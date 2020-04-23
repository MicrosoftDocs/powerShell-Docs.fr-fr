---
ms.date: 07/09/2019
keywords: DSC,gpo,powershell,configuration,installation
title: Démarrage rapide - Convertir la stratégie de groupe en DSC
ms.openlocfilehash: 5e6b86be5127332fe4fd400980c8e147b735247b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500653"
---
> <span data-ttu-id="9e917-103">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9e917-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="9e917-104">Démarrage rapide : Convertir la stratégie de groupe en DSC</span><span class="sxs-lookup"><span data-stu-id="9e917-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="9e917-105">Vous pouvez générer une configuration DSC à partir d’une base de référence de stratégie de groupe ou Azure Security Center.</span><span class="sxs-lookup"><span data-stu-id="9e917-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="9e917-106">Le module [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) inclut les commandes suivantes pour accomplir cette tâche.</span><span class="sxs-lookup"><span data-stu-id="9e917-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="9e917-107">`ConvertFrom-GPO` - Convertit des stratégies de groupe stockées sous forme de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9e917-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="9e917-108">Vous pouvez également spécifier un répertoire contenant plusieurs stratégies qui seront combinées en une seule configuration.</span><span class="sxs-lookup"><span data-stu-id="9e917-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="9e917-109">Pour exporter des stratégies de groupe dans votre environnement, utilisez l’applet de commande [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) ou suivez les instructions dans [Exporter un objet de stratégie de groupe dans un fichier](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="9e917-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="9e917-110">`ConvertFrom-SCM` - Convertit les bases de référence du gestionnaire de conformité de la sécurité, stockées sous forme de fichiers `.xml`.</span><span class="sxs-lookup"><span data-stu-id="9e917-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="9e917-111">`ConvertFrom-ASC` - Convertit les bases de référence d’Azure Security Center, stockées sous forme de fichiers `.json`.</span><span class="sxs-lookup"><span data-stu-id="9e917-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="9e917-112">`Merge-GPOs` - Convertit des stratégies de groupe appliquées à un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="9e917-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="9e917-113">Les applets de commande listées ci-dessus convertissent une base de référence en un fichier DSC `.mof`.</span><span class="sxs-lookup"><span data-stu-id="9e917-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="9e917-114">Vous pouvez également choisir de générer un script de configuration (`.ps1`), que vous pouvez modifier et recompiler.</span><span class="sxs-lookup"><span data-stu-id="9e917-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="9e917-115">Les applets de commande détectent les erreurs de compilation pour les ressources manquantes ou les blocs de ressources en double.</span><span class="sxs-lookup"><span data-stu-id="9e917-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="9e917-116">Les blocs de ressources qui entraînent des erreurs de compilation sont placés en commentaire.</span><span class="sxs-lookup"><span data-stu-id="9e917-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="9e917-117">L’exemple suivant convertit une [base de référence de sécurité Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=55319) en script de configuration DSC (`.ps1`) et en fichier `.mof`.</span><span class="sxs-lookup"><span data-stu-id="9e917-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="9e917-118">Après avoir exécuté les commandes, vous voyez deux fichiers dans le répertoire « Output » par défaut créé sous votre chemin actuel.</span><span class="sxs-lookup"><span data-stu-id="9e917-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="9e917-119">Chaque nœud géré a également besoin des deux modules suivants :</span><span class="sxs-lookup"><span data-stu-id="9e917-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="9e917-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="9e917-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="9e917-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="9e917-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="9e917-122">**BaselineManagement** est une solution développée par la communauté pour rendre DSC plus découvrable dans le cadre du support technique des solutions de la communauté provenant des personnes chargées de la maintenance du projet et non pas de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9e917-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="9e917-123">Vous pouvez ouvrir un nouveau problème pour **BaselineManagement** sur [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="9e917-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e917-124">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9e917-124">Next steps</span></span>

- <span data-ttu-id="9e917-125">Pour charger votre script de configuration dans Configuration d’état Azure Automation, consultez [Bien démarrer](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="9e917-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="9e917-126">Ajoutez les modules **SecurityPolicyDSC** et **AuditPolicyDSC** à votre [compte Automation](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="9e917-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="9e917-127">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="9e917-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
