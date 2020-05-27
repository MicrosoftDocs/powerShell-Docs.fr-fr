---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource WindowsOptionalFeature dans DSC
ms.openlocfilehash: bca6294db74c92a2c1940cfbe00305542a1c5d19
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565364"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="dd5e0-103">Ressource WindowsOptionalFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="dd5e0-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="dd5e0-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="dd5e0-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="dd5e0-105">La ressource **WindowsOptionalFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd5e0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd5e0-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="dd5e0-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="dd5e0-107">Properties</span></span>

|<span data-ttu-id="dd5e0-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="dd5e0-108">Property</span></span> |<span data-ttu-id="dd5e0-109">Description</span><span class="sxs-lookup"><span data-stu-id="dd5e0-109">Description</span></span> |
|---|---|
|<span data-ttu-id="dd5e0-110">Nom</span><span class="sxs-lookup"><span data-stu-id="dd5e0-110">Name</span></span> |<span data-ttu-id="dd5e0-111">Indique le nom de la fonctionnalité que vous souhaitez voir activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="dd5e0-112">Source</span><span class="sxs-lookup"><span data-stu-id="dd5e0-112">Source</span></span> |<span data-ttu-id="dd5e0-113">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-113">Not implemented.</span></span> |
|<span data-ttu-id="dd5e0-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="dd5e0-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="dd5e0-115">Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="dd5e0-116">Si la valeur est `$true`, DISM ne contacte pas Windows Update.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="dd5e0-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="dd5e0-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="dd5e0-118">Affectez la valeur `$true` pour supprimer tous les fichiers associés à la fonctionnalité quand **Ensure** est défini sur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="dd5e0-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="dd5e0-119">LogLevel</span></span> |<span data-ttu-id="dd5e0-120">Niveau de sortie maximal affiché dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="dd5e0-121">Les valeurs acceptées sont les suivantes : **ErrorsOnly**, **ErrorsAndWarning** et **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="dd5e0-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="dd5e0-122">LogPath</span></span> |<span data-ttu-id="dd5e0-123">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="dd5e0-124">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="dd5e0-124">Common properties</span></span>

|<span data-ttu-id="dd5e0-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="dd5e0-125">Property</span></span> |<span data-ttu-id="dd5e0-126">Description</span><span class="sxs-lookup"><span data-stu-id="dd5e0-126">Description</span></span> |
|---|---|
|<span data-ttu-id="dd5e0-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dd5e0-127">DependsOn</span></span> |<span data-ttu-id="dd5e0-128">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dd5e0-129">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="dd5e0-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="dd5e0-130">Ensure</span></span> |<span data-ttu-id="dd5e0-131">Indique si la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="dd5e0-132">Pour faire en sorte que la fonctionnalité soit activée, affectez à cette propriété la valeur _Enable_.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="dd5e0-133">Pour faire en sorte que la fonctionnalité soit désactivée, affectez à cette propriété la valeur _Disable_.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="dd5e0-134">La valeur par défaut est _Enable_.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="dd5e0-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dd5e0-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="dd5e0-136">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="dd5e0-137">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="dd5e0-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="dd5e0-138">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="dd5e0-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
