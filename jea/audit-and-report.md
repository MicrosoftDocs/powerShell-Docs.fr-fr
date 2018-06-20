---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Audit et création de rapports sur JEA
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188850"
---
# <a name="auditing-and-reporting-on-jea"></a>Audit et création de rapports sur JEA

> S’applique à : Windows PowerShell 5.0

Une fois que vous avez déployé JEA, vous devez auditer régulièrement la configuration JEA.
Cela vous aide à évaluer si les personnes adéquates ont accès au point de terminaison JEA et si leurs rôles sont toujours appropriés.

Cette rubrique décrit les différentes manières d’auditer un point de terminaison JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Rechercher des sessions JEA inscrites sur une machine

Pour vérifier les sessions JEA inscrites sur une machine, utilisez l’applet de commande [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Les droits effectifs pour le point de terminaison sont répertoriés dans la propriété « Permission » (Autorisation).
Ces utilisateurs ont le droit de se connecter au point de terminaison JEA, mais les rôles (et, par extension, les commandes) auxquels ils ont accès sont déterminés par le champ « RoleDefinitions » dans le [fichier de configuration de session](session-configurations.md) qui a été utilisé pour inscrire le point de terminaison.

Vous pouvez évaluer les mappages de rôles dans un point de terminaison JEA inscrit en développant les données de la propriété « RoleDefinitions ».

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Trouver des fonctionnalités de rôle disponibles sur la machine

Les fichiers de fonctionnalité de rôle sont uniquement utilisés par JEA s’ils sont stockés dans un dossier « RoleCapabilities » à l’intérieur d’un module PowerShell valide.
Vous pouvez trouver toutes les fonctionnalités de rôle disponibles sur un ordinateur en recherchant la liste des modules disponibles.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> L’ordre des résultats de cette fonction n’est pas nécessairement l’ordre dans lequel les fonctionnalités de rôle sont sélectionnées si plusieurs fonctionnalités des rôles partagent le même nom.

## <a name="check-effective-rights-for-a-specific-user"></a>Vérifiez les droits effectifs pour un utilisateur spécifique

Une fois que vous avez configuré un point de terminaison JEA, vous pourrez peut-être vérifier les commandes disponibles pour un utilisateur spécifique dans une session JEA.
Vous pouvez utiliser [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) pour énumérer toutes les commandes applicables à un utilisateur s’il s’agit de démarrer une session JEA avec leur appartenance à un groupe actuelle.
La sortie de `Get-PSSessionCapability` est identique à celle de l’utilisateur spécifié exécutant `Get-Command -CommandType All` dans une session JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Si vos utilisateurs ne sont pas des membres permanents de groupes qui accorderaient des droits JEA supplémentaires, cette applet de commande ne reflète pas ces autorisations.
C’est généralement le cas lors de l’utilisation de systèmes de gestion à accès privilégié de type just-in-time pour permettre aux utilisateurs d’appartenir temporairement à un groupe de sécurité.
Évaluez toujours attentivement le mappage des utilisateurs sur les rôles et les contenus de chaque rôle pour vous assurer que les utilisateurs ont accès uniquement à la quantité de commandes nécessaires pour mener leurs tâches à bien.

## <a name="powershell-event-logs"></a>Journaux des événements PowerShell

Si vous avez activé la journalisation de module et/ou de bloc de script sur le système, vous serez en mesure de rechercher des événements dans les journaux des événements Windows pour chaque commande exécutée par un utilisateur dans ses sessions JEA.
Pour rechercher ces événements, ouvrez l’Observateur d’événements Windows, accédez au journal des événements **Microsoft-Windows-PowerShell/Operational** et recherchez des événements avec l’ID **4104**.

Chaque entrée de journal des événements comprend des informations sur la session dans laquelle la commande a été exécutée.
Pour les sessions JEA, il s’agit d’informations importantes sur le **ConnectedUser**, qui est l’utilisateur réel qui a créé la session JEA, ainsi que le **RunAsUser**, qui identifie le compte JEA utilisé pour exécuter la commande.
Les journaux des événements de l’application indiquent les modifications effectuées par le RunAsUser. Il est donc important de disposer de transcriptions ou d’activer la journalisation du module / des scripts pour pouvoir tracer un appel de commande spécifique jusqu’à un utilisateur.

## <a name="application-event-logs"></a>Journaux des événements de l’application

Lorsque vous exécutez une commande dans une session JEA qui interagit avec une application ou un service externe, ces applications peuvent éventuellement journaliser des événements dans leurs propres journaux des événements.
Contrairement aux journaux PowerShell et aux transcriptions, d’autres mécanismes de journalisation ne capturent pas l’utilisateur connecté de la session JEA et journalisent uniquement le run-as user virtuel ou le compte de service administré de groupe.
Afin de déterminer qui a exécuté la commande, vous devez consulter un [transcript de session](#session-transcripts) ou mettre en corrélation des journaux des événements de PowerShell avec l’heure et l’utilisateur indiqués dans le journal des événements de l’application.

Le journal WinRM peut également vous aider à mettre en corrélation les run as users dans un journal des événements de l’application avec l’utilisateur connecté.
L’ID d’événement **193** dans le journal **Microsoft-Windows-Windows Remote Management/Operational** enregistre l’identificateur de sécurité (SID) et le nom du compte de l’utilisateur qui se connecte et le run as user chaque fois qu’une session JEA est créée.

## <a name="session-transcripts"></a>Transcriptions de session

Si vous avez configuré JEA afin de créer une transcription pour chaque session utilisateur, une copie de texte des actions de chaque utilisateur est stockée dans le dossier spécifié.

Pour rechercher tous les répertoires de transcription, exécutez la commande suivante en tant qu’administrateur sur l’ordinateur configuré avec JEA :

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

Dans le texte de la transcription, les informations concernant chaque commande que l’utilisateur a appelée sont journalisées.
La syntaxe exacte de la commande exécutée par l’utilisateur n’est pas disponible dans les sessions JEA en raison de la manière dont les commandes sont transformées pour l’accès distant PowerShell. Cependant, vous pouvez toujours déterminer la commande effective qui a été exécutée.
Voici un exemple d’extrait de code de transcription d’un utilisateur exécutant `Get-Service Dns` dans une session JEA :

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Une ligne « CommandInvocation » est écrite pour chaque commande qu'un utilisateur exécute, qui décrit l’applet de commande ou la fonction appelée par l’utilisateur.
Les liaisons de paramètres (ParameterBindings) suivent chaque appel de commande (CommandInvocation) pour vous donner des informations sur chaque paramètre et leurs valeurs.
Dans l’exemple ci-dessus, vous pouvez voir que le paramètre « Name » a reçu la valeur « Dns » pour l’applet de commande « Get-Service ».

Le résultat de chaque commande déclenche également une CommandInvocation, généralement pour Out-Default.
L’objet d’entrée (InputObject) d’Out-Default est l’objet PowerShell retourné par la commande.
Les détails de cet objet sont indiqués ci-dessous. Ils imitent étroitement ce que l’utilisateur a pu observer.

## <a name="see-also"></a>Voir aussi

- [Audit des actions de l’utilisateur dans une session JEA](audit-and-report.md)
- [*PowerShell ♥ the Blue Team*, billet de blog sur la sécurité](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)