---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Inscription de configurations JEA
ms.openlocfilehash: dbed5c7dd71f2f7a09d97416be56dff675799548
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417601"
---
# <a name="registering-jea-configurations"></a>Inscription de configurations JEA

Une fois les [capacités des rôles](role-capabilities.md) et le [fichier de configuration de session](session-configurations.md) créés, la dernière étape consiste à inscrire le point de terminaison JEA. Cette inscription auprès du système a pour effet de mettre le point de terminaison à la disposition des utilisateurs et des moteurs d’automatisation.

## <a name="single-machine-configuration"></a>Configuration d’une machine unique

Pour les environnements de petite taille, vous pouvez déployer JEA en inscrivant le fichier de configuration de session à l’aide de l’applet de commande [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).

Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :

- Un ou plusieurs rôles ont été créés et placés dans le dossier **RoleCapabilities** d’un module PowerShell.
- Un fichier de configuration de session a été créé et testé.
- L’utilisateur qui inscrit la configuration JEA dispose de droits d’administrateur sur le système.
- Vous avez sélectionné un nom pour votre point de terminaison JEA.

Le nom du point de terminaison JEA est nécessaire quand les utilisateurs se connectent au système avec JEA. L’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) liste les noms des points de terminaison sur un système. Les points de terminaison qui commencent par `microsoft` sont généralement livrés avec Windows. Le point de terminaison `microsoft.powershell` est le point de terminaison par défaut utilisé lors de la connexion à un point de terminaison PowerShell distant.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Exécutez la commande suivante pour inscrire le point de terminaison.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> La commande précédente redémarre le service WinRM sur le système. Ceci arrête toutes les sessions de communication à distance PowerShell ainsi que les éventuelles configurations DSC en cours. Nous vous recommandons de mettre les machines de production hors connexion avant d’exécuter la commande, de façon à éviter d’interrompre les opérations dans l’entreprise.

Après l’inscription, vous êtes prêt à [utiliser JEA](using-jea.md). Vous pouvez supprimer le fichier de configuration de session à tout moment. Le fichier de configuration n’est plus utilisé après l’inscription du point de terminaison.

## <a name="multi-machine-configuration-with-dsc"></a>Configuration sur plusieurs machines avec DSC

Pour le déploiement de JEA sur plusieurs machines, le modèle de déploiement le plus simple utilise la ressource JEA [Configuration d’état souhaité](/powershell/scripting/dsc/overview) (DSC, Desired State Configuration) pour déployer JEA de façon rapide et cohérente sur chaque machine.

Voici les prérequis à respecter pour pouvoir déployer JEA avec DSC :

- Une ou plusieurs capacités de rôle ont été créées et ajoutées dans un module PowerShell valide.
- Le module PowerShell contenant les rôles est stocké sur un partage de fichiers (en lecture seule) accessible depuis chaque machine.
- Les paramètres de la configuration de session ont été déterminés. Vous n’avez pas besoin de créer un fichier de configuration de session quand vous utilisez la ressource DSC JEA.
- Vous disposez d’informations d’identification permettant des actions d’administration sur chaque machine ou l’accès au serveur Pull DSC utilisé pour gérer les machines.
- Vous avez téléchargé la [ressource DSC JEA](https://github.com/powershell/JEA/tree/master/DSC%20Resource).

Créez une configuration DSC pour votre point de terminaison JEA sur une machine ou un serveur Pull cible. Dans cette configuration, la ressource DSC **JustEnoughAdministration** définit le fichier de configuration de session et la ressource **File** copie les capacités de rôle depuis le partage de fichiers.

Les propriétés suivantes sont configurables à l’aide de la ressource DSC :

- Définitions de rôle
- Groupes de comptes virtuels
- Nom du compte de service géré de groupe
- Répertoire de transcription
- Lecteur utilisateur
- Règles d’accès conditionnel
- Scripts de démarrage de la session JEA

La syntaxe pour chacune de ces propriétés dans une configuration DSC est cohérente avec le fichier de configuration de session PowerShell.

Voici un exemple de configuration DSC pour un module de maintenance générale des serveurs. Il suppose qu’un module PowerShell valide contenant les capacités de rôle se trouve sur le partage de fichiers `\\myfileshare\JEA`.

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Ensuite, cette configuration est appliquée à un système en appelant directement le [Gestionnaire de configuration local](/powershell/scripting/dsc/managing-nodes/metaConfig) ou en mettant à jour la [configuration du serveur Pull](/powershell/scripting/dsc/pull-server/pullServer).

La ressource DSC vous permet également de remplacer le point de terminaison **Microsoft.PowerShell** par défaut. Après le remplacement, la ressource inscrit automatiquement un point de terminaison de sauvegarde nommé **Microsoft.PowerShell.Restricted**. Le point de terminaison de sauvegarde a la liste de contrôle d’accès WinRM par défaut, qui permet aux utilisateurs de la gestion à distance et aux membres du groupe Administrateurs locaux d’y accéder.

## <a name="unregistering-jea-configurations"></a>Désinscription de configurations JEA

L’applet de commande [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) supprime un point de terminaison JEA. Le fait de désinscrire un point de terminaison JEA empêche les nouveaux utilisateurs de créer des sessions JEA sur le système. Elle permet également de mettre à jour une configuration JEA en réinscrivant un fichier de configuration de session mis à jour à l’aide du même nom de point de terminaison.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Le fait de désinscrire un point de terminaison JEA entraîne le redémarrage du service WinRM, ce qui interrompt la plupart des opérations de gestion à distance en cours, notamment les autres sessions PowerShell, les appels WMI et certains outils de gestion. Ne désinscrivez des points de terminaison PowerShell que pendant les fenêtres de maintenance planifiée.

## <a name="next-steps"></a>Étapes suivantes

[Tester le point de terminaison JEA](using-jea.md)
