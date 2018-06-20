---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Inscription de configurations JEA
ms.openlocfilehash: cda899b20378b0183a3d88ecfd593aaf7356e967
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188511"
---
# <a name="registering-jea-configurations"></a>Inscription de configurations JEA

> S’applique à : Windows PowerShell 5.0

La dernière étape avant de pouvoir utiliser JEA une fois les [fonctionnalités de rôles](role-capabilities.md) et le [fichier de configuration de session](session-configurations.md) créés consiste à inscrire le point de terminaison JEA.
Ce processus applique les informations de configuration de session au système et rend le point de terminaison disponible pour une utilisation par des utilisateurs et des moteurs d’automatisation (Automation).

## <a name="single-machine-configuration"></a>Configuration d’une machine unique

Pour les environnements de petite taille, vous pouvez déployer JEA en inscrivant le fichier de configuration de session à l’aide de l’applet de commande [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).

Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
- Un ou plusieurs rôles ont été créés et placés dans le dossier « RoleCapabilities » d’un module PowerShell valide.
- Un fichier de configuration de session a été créé et testé.
- L’utilisateur qui inscrit la configuration JEA dispose de droits d’administrateur sur les systèmes.

Vous devez également sélectionner un nom pour votre point de terminaison JEA.
Le nom du point de terminaison JEA est nécessaire lorsque les utilisateurs souhaitent se connecter au système à l’aide de JEA.
Vous pouvez utiliser l’applet de commande [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) pour vérifier les noms des points de terminaison qui existent sur le système.
Les points de terminaison qui commencent par « microsoft » sont généralement livrés avec Windows.
Le point de terminaison « microsoft.powershell » est le point de terminaison par défaut utilisé lors de la connexion à un point de terminaison PowerShell distant.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Lorsque vous avez déterminé un nom approprié pour votre point de terminaison JEA, exécutez la commande suivante pour inscrire le point de terminaison.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> La commande ci-dessus redémarre le service WinRM sur le système.
> Cela arrête toutes les sessions de communication à distance PowerShell, ainsi que toute configuration DSC en cours.
> Il est recommandé de mettre toute machine de production hors connexion avant d’exécuter la commande pour éviter d’interrompre les opérations métier.

Si l’inscription a réussi, vous êtes prêt à [utiliser JEA](using-jea.md).
Vous pouvez supprimer le fichier de configuration de session à tout moment. Il n’est pas utilisé après l’inscription.

## <a name="multi-machine-configuration-with-dsc"></a>Configuration sur plusieurs machines avec DSC

Si vous déployez JEA sur plusieurs machines, le modèle de déploiement le plus simple consiste à utiliser la ressource JEA [Configuration d’état souhaité](https://msdn.microsoft.com/en-us/powershell/dsc/overview) pour déployer JEA rapidement et de manière cohérente sur chaque machine.

Pour déployer JEA avec DSC, vous devez garantir que les conditions préalables suivantes sont remplies :
- Une ou plusieurs fonctionnalités de rôles ont été créées et ajoutées à un module PowerShell valide.
- Le module PowerShell contenant les rôles est stocké sur un partage de fichiers (en lecture seule) accessible depuis chaque machine.
- Les paramètres de la configuration de session ont été déterminés. Il est inutile de créer un fichier de configuration de session si la ressource DSC JEA est utilisée.
- Vous disposez des informations d’identification qui vous permettent d’effectuer des actions administratives sur chaque machine, ou d’avoir accès à un serveur collecteur DSC utilisé pour gérer les machines.
- Vous avez téléchargé la [ressource DSC JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Sur une machine cible (ou le serveur collecteur, si vous en utilisez un), créez une configuration DSC pour votre point de terminaison JEA.
Dans cette configuration, vous utilisez la ressource DSC JustEnoughAdministration pour définir le fichier de configuration de session et la ressource Fichier à copier sur les fonctionnalités de rôle à partir du partage de fichiers.

Les propriétés suivantes sont configurables à l’aide de la ressource DSC :
- Définitions de rôle
- Groupes de compte virtuel
- Nom de compte de service administré de groupe
- Répertoire de transcription
- Lecteur utilisateur
- Règles d’accès conditionnel
- Scripts de démarrage de la session JEA

La syntaxe pour chacune de ces propriétés dans une configuration DSC est cohérente avec le fichier de configuration de session PowerShell.

Voici un exemple de configuration DSC pour un module de maintenance générale des serveurs.

Il part du principe qu’un module PowerShell valide contenant des fonctionnalités de rôle dans un sous-dossier « RoleCapabilities » se trouve sur le partage de fichiers « \\\\myfileshare\\JEA ».


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

Cette configuration peut ensuite être appliquée à un système en [appelant directement le Gestionnaire de configuration Local](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) ou en mettant à jour la [configuration du serveur collecteur](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).

La ressource DSC vous permet également de remplacer le point de terminaison de communication à distance Microsoft.PowerShell par défaut.
Si vous procédez ainsi, la ressource inscrit automatiquement un point de terminaison de sauvegarde sans contrainte nommé « Microsoft.PowerShell.Restricted » qui a la valeur par défaut des listes de contrôle d’accès WinRM (permettant aux groupes Utilisateurs de gestion à distance et Administrateurs locaux d’y accéder).

## <a name="unregistering-jea-configurations"></a>Désinscription de configurations JEA

Pour supprimer un point de terminaison JEA sur un système, utilisez l’applet de commande [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).
La désinscription d’un point de terminaison JEA empêche les nouveaux utilisateurs de créer de nouvelles sessions JEA sur le système.
Elle permet également de mettre à jour une configuration JEA en réinscrivant un fichier de configuration de session mis à jour à l’aide du même nom de point de terminaison.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> La désinscription d’un point de terminaison JEA entraîne le redémarrage du service WinRM.
> Elle interrompt la plupart des opérations de gestion à distance en cours, notamment les autres sessions PowerShell, les appels WMI et certains outils de gestion.
> Ne désinscrivez des points de terminaison PowerShell que pendant les fenêtres de maintenance planifiée.

## <a name="next-steps"></a>Étapes suivantes

- [Tester le point de terminaison JEA](using-jea.md)