---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Audit et création de rapports sur JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017790"
---
# <a name="auditing-and-reporting-on-jea"></a>Audit et création de rapports sur JEA

Une fois que vous avez déployé JEA, vous devez auditer régulièrement la configuration JEA. L’audit vous aide à évaluer si les personnes adéquates ont accès au point de terminaison JEA et si leurs rôles sont toujours appropriés.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Rechercher des sessions JEA inscrites sur une machine

Pour vérifier les sessions JEA inscrites sur une machine, utilisez l’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Les droits effectifs pour le point de terminaison sont listés dans la propriété **Permission**. Ces utilisateurs ont le droit de se connecter au point de terminaison JEA. Cependant, les rôles et les commandes auxquels ils ont accès sont déterminés par la propriété **RoleDefinitions** dans le [fichier de configuration de session](session-configurations.md) qui a été utilisé pour inscrire le point de terminaison. Développez la propriété **RoleDefinitions** pour évaluer les correspondances de rôles dans un point de terminaison JEA inscrit.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Trouver des fonctionnalités de rôle disponibles sur la machine

JEA obtient les capacités de rôle auprès des fichiers `.psrc` stockés dans le dossier **RoleCapabilities** au sein d’un module PowerShell. La fonction suivante recherche toutes les capacités de rôle disponibles sur un ordinateur.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> L’ordre des résultats de cette fonction n’est pas nécessairement l’ordre dans lequel les fonctionnalités de rôle sont sélectionnées si plusieurs fonctionnalités des rôles partagent le même nom.

## <a name="check-effective-rights-for-a-specific-user"></a>Vérifiez les droits effectifs pour un utilisateur spécifique

L’applet de commande [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) énumère toutes les commandes disponibles sur un point de terminaison JEA en fonction des appartenances aux groupes d’un utilisateur.
La sortie de `Get-PSSessionCapability` est identique à celle de l’utilisateur spécifié exécutant `Get-Command -CommandType All` dans une session JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Si vos utilisateurs ne sont pas des membres permanents de groupes qui leur accordent des droits JEA supplémentaires, cette applet de commande peut ne pas refléter ces autres autorisations. Ceci se produit lors de l’utilisation de systèmes de gestion à accès privilégié de type juste-à-temps pour permettre aux utilisateurs d’appartenir temporairement à un groupe de sécurité. Évaluez soigneusement la mise en correspondance des utilisateurs aux rôles et aux capacités pour garantir que les utilisateurs obtiennent seulement le niveau d’accès nécessaire pour faire leur travail.

## <a name="powershell-event-logs"></a>Journaux des événements PowerShell

Si vous avez activé la journalisation de module ou de bloc de script sur le système, vous pouvez voir des événements dans les journaux des événements Windows pour chaque commande exécutée par un utilisateur dans une session JEA. Pour trouver ces événements, ouvrez le journal des événements **Microsoft-Windows-PowerShell/Operational** et recherchez des événements avec l’ID **4104**.

Chaque entrée du journal des événements comprend des informations sur la session dans laquelle la commande a été exécutée. Pour les sessions JEA, l’événement contient des informations sur **ConnectedUser** et **RunAsUser**. **ConnectedUser** est l’utilisateur réel qui a créé la session JEA. **RunAsUser** est le compte JEA utilisé pour exécuter la commande.

Les journaux des événements d’applications montrent les changements effectués par **RunAsUser**. L’activation de la journalisation des modules et des scripts est donc nécessaire pour retracer l’appel d’une commande spécifique jusqu’à **ConnectedUser**.

## <a name="application-event-logs"></a>Journaux des événements de l’application

Les commandes exécutées dans une session JEA qui interagissent avec des applications ou des services externes peuvent consigner des événements dans leurs propres journaux des événements. Contrairement aux journaux et aux transcriptions PowerShell, les autres mécanismes de journalisation ne capturent pas l’utilisateur connecté de la session JEA. Au lieu de cela, ces applications consignent seulement l’utilisateur d’identification virtuel.
Pour déterminer qui a exécuté la commande, vous devez consulter une [transcription de session](#session-transcripts), ou mettre en corrélation des journaux des événements de PowerShell avec le moment et l’utilisateur indiqués dans le journal des événements d’une application.

Le journal WinRM peut également vous aider à mettre en corrélation les utilisateurs d’identification avec l’utilisateur qui se connecte dans un journal des événements d’une application. L’ID d’événement **193** dans le journal **Microsoft-Windows-Windows Remote Management/Operational** enregistre l’identificateur de sécurité (SID) et le nom du compte de l’utilisateur d’identification et de l’utilisateur qui se connecte pour chaque nouvelle session JEA.

## <a name="session-transcripts"></a>Transcription de sessions

Si vous avez configuré JEA pour créer une transcription pour chaque session utilisateur, une copie texte des actions de chaque utilisateur est stockée dans le dossier spécifié.

La commande suivante (exécutée en tant qu’administrateur) trouve tous les répertoires de transcription.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Chaque transcription démarre avec des informations sur l’heure de début de la session, l’heure de la connexion de l’utilisateur à la session, et l’identité JEA qui lui a été attribuée.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Le corps de la transcription contient des informations sur chaque commande que l’utilisateur a appelée. La syntaxe exacte de la commande utilisée n’est pas disponible dans les sessions JEA en raison de la façon dont les commandes sont transformées pour la communication à distance de PowerShell. Cependant, vous pouvez toujours déterminer la commande effective qui a été exécutée. Voici un exemple d’extrait de code de transcription d’un utilisateur exécutant `Get-Service Dns` dans une session JEA :

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Une ligne **CommandInvocation** est écrite pour chaque commande exécutée par un utilisateur. **ParameterBindings** enregistre chaque paramètre et chaque valeur fournis avec la commande. Dans l’exemple précédent, vous pouvez voir que le paramètre **Name** a été fourni avec la valeur **Dns** pour l’applet de commande `Get-Service`.

Le résultat de chaque commande déclenche également une **CommandInvocation**, généralement pour `Out-Default`. Le **InputObject** de `Out-Default` est l’objet PowerShell retourné par la commande. Les détails de cet objet sont indiqués ci-dessous. Ils imitent étroitement ce que l’utilisateur a pu observer.

## <a name="see-also"></a>Voir aussi

[*PowerShell ♥ the Blue Team*, billet de blog sur la sécurité](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
