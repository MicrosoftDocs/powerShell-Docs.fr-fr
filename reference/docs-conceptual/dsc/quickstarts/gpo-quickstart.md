---
ms.date: 07/09/2019
keywords: DSC,gpo,powershell,configuration,installation
title: Démarrage rapide - Convertir la stratégie de groupe en DSC
ms.openlocfilehash: a9ce9cecd71fe00d2908024a3ee474ec836af3ba
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808246"
---
# <a name="quickstart-convert-group-policy-into-dsc"></a>Démarrage rapide : Convertir la stratégie de groupe en DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Vous pouvez générer une configuration DSC à partir d’une base de référence de stratégie de groupe ou Azure Security Center. Le module [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) inclut les commandes suivantes pour accomplir cette tâche.

- `ConvertFrom-GPO` - Convertit des stratégies de groupe stockées sous forme de fichiers. Vous pouvez également spécifier un répertoire contenant plusieurs stratégies qui seront combinées en une seule configuration.
  - Pour exporter des stratégies de groupe dans votre environnement, utilisez l’applet de commande [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) ou suivez les instructions dans [Exporter un objet de stratégie de groupe dans un fichier](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` - Convertit les bases de référence du gestionnaire de conformité de la sécurité, stockées sous forme de fichiers `.xml`.
- `ConvertFrom-ASC` - Convertit les bases de référence d’Azure Security Center, stockées sous forme de fichiers `.json`.
- `Merge-GPOs` - Convertit des stratégies de groupe appliquées à un ordinateur cible.

Les applets de commande listées ci-dessus convertissent une base de référence en un fichier DSC `.mof`. Vous pouvez également choisir de générer un script de configuration (`.ps1`), que vous pouvez modifier et recompiler. Les applets de commande détectent les erreurs de compilation pour les ressources manquantes ou les blocs de ressources en double. Les blocs de ressources qui entraînent des erreurs de compilation sont placés en commentaire.

L’exemple suivant convertit une [base de référence de sécurité Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=55319) en script de configuration DSC (`.ps1`) et en fichier `.mof`.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Après avoir exécuté les commandes, vous voyez deux fichiers dans le répertoire « Output » par défaut créé sous votre chemin actuel.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Chaque nœud géré a également besoin des deux modules suivants :

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** est une solution développée par la communauté pour rendre DSC plus découvrable dans le cadre du support technique des solutions de la communauté provenant des personnes chargées de la maintenance du projet et non pas de Microsoft. Vous pouvez ouvrir un nouveau problème pour **BaselineManagement** sur [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Étapes suivantes

- Pour charger votre script de configuration dans Configuration d’état Azure Automation, consultez [Bien démarrer](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Ajoutez les modules **SecurityPolicyDSC** et **AuditPolicyDSC** à votre [compte Automation](/azure/automation/shared-resources/modules).
- Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).
