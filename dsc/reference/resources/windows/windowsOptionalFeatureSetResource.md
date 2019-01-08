---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsOptionalFeatureSet dans DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047293"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="fc58d-103">Ressource WindowsOptionalFeatureSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="fc58d-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="fc58d-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fc58d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fc58d-105">La ressource **WindowsOptionalFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="fc58d-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="fc58d-106">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la ressource [WindowsOptionalFeature](windowsOptionalFeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="fc58d-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="fc58d-107">Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités facultatives de Windows au même état.</span><span class="sxs-lookup"><span data-stu-id="fc58d-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc58d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc58d-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="fc58d-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fc58d-109">Properties</span></span>

|  <span data-ttu-id="fc58d-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="fc58d-110">Property</span></span>  |  <span data-ttu-id="fc58d-111">Description</span><span class="sxs-lookup"><span data-stu-id="fc58d-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="fc58d-112">Name</span><span class="sxs-lookup"><span data-stu-id="fc58d-112">Name</span></span>| <span data-ttu-id="fc58d-113">Indique le nom des fonctionnalités que vous souhaitez voir activées ou désactivées.</span><span class="sxs-lookup"><span data-stu-id="fc58d-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="fc58d-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="fc58d-114">Ensure</span></span>| <span data-ttu-id="fc58d-115">Spécifie si les fonctionnalités sont activées.</span><span class="sxs-lookup"><span data-stu-id="fc58d-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="fc58d-116">Pour vous assurer que les fonctionnalités sont activées, affectez la valeur « Enable » à cette propriété. Pour vous assurer que les fonctionnalités sont désactivées, affectez la valeur «Disable ».</span><span class="sxs-lookup"><span data-stu-id="fc58d-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="fc58d-117">Source</span><span class="sxs-lookup"><span data-stu-id="fc58d-117">Source</span></span>| <span data-ttu-id="fc58d-118">Non implémentée.</span><span class="sxs-lookup"><span data-stu-id="fc58d-118">Not implemented.</span></span>|
| <span data-ttu-id="fc58d-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="fc58d-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="fc58d-120">Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="fc58d-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="fc58d-121">Si la valeur est $true, DISM ne contacte pas Windows Update.</span><span class="sxs-lookup"><span data-stu-id="fc58d-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="fc58d-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="fc58d-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="fc58d-123">Affectez la valeur **$true** pour supprimer tous les fichiers associés aux fonctionnalités quand elles sont désactivées (autrement dit, quand **Ensure** a la valeur « Absent »).</span><span class="sxs-lookup"><span data-stu-id="fc58d-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="fc58d-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="fc58d-124">LogLevel</span></span>| <span data-ttu-id="fc58d-125">Niveau de sortie maximal affiché dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="fc58d-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="fc58d-126">Les valeurs acceptées sont : « ErrorsOnly » (seules les erreurs sont enregistrées), « ErrorsAndWarning » (erreurs et avertissements sont enregistrés) et « ErrorsAndWarningAndInformation » (erreurs, avertissements et informations de débogage sont enregistrées).</span><span class="sxs-lookup"><span data-stu-id="fc58d-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="fc58d-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="fc58d-127">LogPath</span></span>| <span data-ttu-id="fc58d-128">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="fc58d-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="fc58d-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fc58d-129">DependsOn</span></span>| <span data-ttu-id="fc58d-130">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="fc58d-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fc58d-131">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fc58d-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
