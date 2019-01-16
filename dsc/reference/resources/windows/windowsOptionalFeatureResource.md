---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsOptionalFeature dans DSC
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047331"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="0d7d1-103">Ressource WindowsOptionalFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="0d7d1-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="0d7d1-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0d7d1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0d7d1-105">La ressource **WindowsOptionalFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d7d1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d7d1-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="0d7d1-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0d7d1-107">Properties</span></span>

|  <span data-ttu-id="0d7d1-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="0d7d1-108">Property</span></span>  |  <span data-ttu-id="0d7d1-109">Description</span><span class="sxs-lookup"><span data-stu-id="0d7d1-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="0d7d1-110">Name</span><span class="sxs-lookup"><span data-stu-id="0d7d1-110">Name</span></span>| <span data-ttu-id="0d7d1-111">Indique le nom de la fonctionnalité que vous souhaitez voir activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="0d7d1-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="0d7d1-112">Ensure</span></span>| <span data-ttu-id="0d7d1-113">Spécifie si la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="0d7d1-114">Pour vous assurer que la fonctionnalité est activée, affectez la valeur « Enable » à cette propriété. Pour vous assurer que la fonctionnalité est désactivée, affectez la valeur « Disable ».</span><span class="sxs-lookup"><span data-stu-id="0d7d1-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="0d7d1-115">Source</span><span class="sxs-lookup"><span data-stu-id="0d7d1-115">Source</span></span>| <span data-ttu-id="0d7d1-116">Non implémentée.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-116">Not implemented.</span></span>|
| <span data-ttu-id="0d7d1-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="0d7d1-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="0d7d1-118">Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="0d7d1-119">Si la valeur est $true, DISM ne contacte pas Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="0d7d1-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="0d7d1-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="0d7d1-121">Affectez la valeur **$true** pour supprimer tous les fichiers associés à la fonctionnalité quand elle est désactivée (autrement dit, quand **Ensure** a la valeur « Absent »).</span><span class="sxs-lookup"><span data-stu-id="0d7d1-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="0d7d1-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="0d7d1-122">LogLevel</span></span>| <span data-ttu-id="0d7d1-123">Niveau de sortie maximal affiché dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="0d7d1-124">Les valeurs acceptées sont : « ErrorsOnly » (seules les erreurs sont enregistrées), « ErrorsAndWarning » (erreurs et avertissements sont enregistrés) et « ErrorsAndWarningAndInformation » (erreurs, avertissements et informations de débogage sont enregistrées).</span><span class="sxs-lookup"><span data-stu-id="0d7d1-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="0d7d1-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="0d7d1-125">LogPath</span></span>| <span data-ttu-id="0d7d1-126">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="0d7d1-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0d7d1-127">DependsOn</span></span>| <span data-ttu-id="0d7d1-128">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0d7d1-129">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0d7d1-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|