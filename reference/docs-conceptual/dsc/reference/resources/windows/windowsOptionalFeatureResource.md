---
ms.date: 08/28/2020
keywords: dsc,powershell,configuration,installation
title: Ressource WindowsOptionalFeature dans DSC
ms.openlocfilehash: f24173c1a9ed605bac43767a9da2d4dbded78883
ms.sourcegitcommit: 06b6f4012e4eca71d414733cdba23ef75535223c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "89093248"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="a8abb-103">Ressource WindowsOptionalFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="a8abb-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="a8abb-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a8abb-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="a8abb-105">La ressource **WindowsOptionalFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="a8abb-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="a8abb-106">**WindowsOptionalFeature** fonctionne uniquement sur les ordinateurs clients Windows, comme Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a8abb-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8abb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8abb-107">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="a8abb-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a8abb-108">Properties</span></span>

|<span data-ttu-id="a8abb-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="a8abb-109">Property</span></span> |<span data-ttu-id="a8abb-110">Description</span><span class="sxs-lookup"><span data-stu-id="a8abb-110">Description</span></span> |
|---|---|
|<span data-ttu-id="a8abb-111">Name</span><span class="sxs-lookup"><span data-stu-id="a8abb-111">Name</span></span> |<span data-ttu-id="a8abb-112">Indique le nom de la fonctionnalité que vous souhaitez voir activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="a8abb-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="a8abb-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="a8abb-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="a8abb-114">Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="a8abb-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="a8abb-115">Si la valeur est `$true`, DISM ne contacte pas Windows Update.</span><span class="sxs-lookup"><span data-stu-id="a8abb-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="a8abb-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="a8abb-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="a8abb-117">Affectez la valeur `$true` pour supprimer tous les fichiers associés à la fonctionnalité quand **Ensure** est défini sur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="a8abb-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="a8abb-118">LogLevel</span><span class="sxs-lookup"><span data-stu-id="a8abb-118">LogLevel</span></span> |<span data-ttu-id="a8abb-119">Niveau de sortie maximal affiché dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="a8abb-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="a8abb-120">Les valeurs acceptées sont les suivantes : **ErrorsOnly**, **ErrorsAndWarning** et **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="a8abb-120">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="a8abb-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="a8abb-121">LogPath</span></span> |<span data-ttu-id="a8abb-122">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="a8abb-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a8abb-123">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="a8abb-123">Common properties</span></span>

|<span data-ttu-id="a8abb-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="a8abb-124">Property</span></span> |<span data-ttu-id="a8abb-125">Description</span><span class="sxs-lookup"><span data-stu-id="a8abb-125">Description</span></span> |
|---|---|
|<span data-ttu-id="a8abb-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a8abb-126">DependsOn</span></span> |<span data-ttu-id="a8abb-127">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="a8abb-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a8abb-128">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a8abb-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a8abb-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="a8abb-129">Ensure</span></span> |<span data-ttu-id="a8abb-130">Indique si la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="a8abb-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="a8abb-131">Pour faire en sorte que la fonctionnalité soit activée, affectez à cette propriété la valeur _Enable_.</span><span class="sxs-lookup"><span data-stu-id="a8abb-131">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="a8abb-132">Pour faire en sorte que la fonctionnalité soit désactivée, affectez à cette propriété la valeur _Disable_.</span><span class="sxs-lookup"><span data-stu-id="a8abb-132">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="a8abb-133">La valeur par défaut est _Enable_.</span><span class="sxs-lookup"><span data-stu-id="a8abb-133">The default value is _Enable_.</span></span> |
|<span data-ttu-id="a8abb-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a8abb-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="a8abb-135">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a8abb-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="a8abb-136">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a8abb-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a8abb-137">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="a8abb-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
