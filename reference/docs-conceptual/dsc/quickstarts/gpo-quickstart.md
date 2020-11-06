---
ms.date: 07/09/2019
keywords: DSC,gpo,powershell,configuration,installation
title: Démarrage rapide - Convertir la stratégie de groupe en DSC
description: Ce guide de démarrage rapide montre les étapes nécessaires pour convertir une stratégie de groupe Windows en une configuration DSC.
ms.openlocfilehash: b67f6dd2cf6c91d90fa6ac5b6367f9efc7f40ee0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644706"
---
# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="62cb3-104">Démarrage rapide : Convertir la stratégie de groupe en DSC</span><span class="sxs-lookup"><span data-stu-id="62cb3-104">Quickstart: Convert Group Policy into DSC</span></span>

> <span data-ttu-id="62cb3-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="62cb3-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="62cb3-106">Vous pouvez générer une configuration DSC à partir d’une base de référence de stratégie de groupe ou Azure Security Center.</span><span class="sxs-lookup"><span data-stu-id="62cb3-106">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="62cb3-107">Le module [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) inclut les commandes suivantes pour accomplir cette tâche.</span><span class="sxs-lookup"><span data-stu-id="62cb3-107">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="62cb3-108">`ConvertFrom-GPO` - Convertit des stratégies de groupe stockées sous forme de fichiers.</span><span class="sxs-lookup"><span data-stu-id="62cb3-108">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="62cb3-109">Vous pouvez également spécifier un répertoire contenant plusieurs stratégies qui seront combinées en une seule configuration.</span><span class="sxs-lookup"><span data-stu-id="62cb3-109">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="62cb3-110">Pour exporter des stratégies de groupe dans votre environnement, utilisez l’applet de commande [Backup-GPO](/powershell/module/grouppolicy/backup-gpo) ou suivez les instructions dans [Exporter un objet de stratégie de groupe dans un fichier](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="62cb3-110">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="62cb3-111">`ConvertFrom-SCM` - Convertit les bases de référence du gestionnaire de conformité de la sécurité, stockées sous forme de fichiers `.xml`.</span><span class="sxs-lookup"><span data-stu-id="62cb3-111">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="62cb3-112">`ConvertFrom-ASC` - Convertit les bases de référence d’Azure Security Center, stockées sous forme de fichiers `.json`.</span><span class="sxs-lookup"><span data-stu-id="62cb3-112">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="62cb3-113">`Merge-GPOs` - Convertit des stratégies de groupe appliquées à un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="62cb3-113">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="62cb3-114">Les applets de commande listées ci-dessus convertissent une base de référence en un fichier DSC `.mof`.</span><span class="sxs-lookup"><span data-stu-id="62cb3-114">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="62cb3-115">Vous pouvez également choisir de générer un script de configuration (`.ps1`), que vous pouvez modifier et recompiler.</span><span class="sxs-lookup"><span data-stu-id="62cb3-115">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="62cb3-116">Les applets de commande détectent les erreurs de compilation pour les ressources manquantes ou les blocs de ressources en double.</span><span class="sxs-lookup"><span data-stu-id="62cb3-116">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="62cb3-117">Les blocs de ressources qui entraînent des erreurs de compilation sont placés en commentaire.</span><span class="sxs-lookup"><span data-stu-id="62cb3-117">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="62cb3-118">L’exemple suivant convertit une [base de référence de sécurité Microsoft](https://www.microsoft.com/download/details.aspx?id=55319) en script de configuration DSC (`.ps1`) et en fichier `.mof`.</span><span class="sxs-lookup"><span data-stu-id="62cb3-118">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="62cb3-119">Après avoir exécuté les commandes, vous voyez deux fichiers dans le répertoire « Output » par défaut créé sous votre chemin actuel.</span><span class="sxs-lookup"><span data-stu-id="62cb3-119">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="62cb3-120">Chaque nœud géré a également besoin des deux modules suivants :</span><span class="sxs-lookup"><span data-stu-id="62cb3-120">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="62cb3-121">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="62cb3-121">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="62cb3-122">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="62cb3-122">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="62cb3-123">**BaselineManagement** est une solution développée par la communauté pour rendre DSC plus découvrable dans le cadre du support technique des solutions de la communauté provenant des personnes chargées de la maintenance du projet et non pas de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="62cb3-123">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="62cb3-124">Vous pouvez ouvrir un nouveau problème pour **BaselineManagement** sur [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="62cb3-124">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="62cb3-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="62cb3-125">Next steps</span></span>

- <span data-ttu-id="62cb3-126">Pour charger votre script de configuration dans Configuration d’état Azure Automation, consultez [Bien démarrer](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="62cb3-126">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="62cb3-127">Ajoutez les modules **SecurityPolicyDSC** et **AuditPolicyDSC** à votre [compte Automation](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="62cb3-127">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="62cb3-128">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="62cb3-128">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
