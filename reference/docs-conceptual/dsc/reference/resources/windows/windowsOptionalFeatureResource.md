---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsOptionalFeature dans DSC
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954646"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="80376-103">Ressource WindowsOptionalFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="80376-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="80376-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="80376-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="80376-105">La ressource **WindowsOptionalFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="80376-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="80376-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80376-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="80376-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="80376-107">Properties</span></span>

|<span data-ttu-id="80376-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="80376-108">Property</span></span> |<span data-ttu-id="80376-109">Description</span><span class="sxs-lookup"><span data-stu-id="80376-109">Description</span></span> |
|---|---|
|<span data-ttu-id="80376-110">Name</span><span class="sxs-lookup"><span data-stu-id="80376-110">Name</span></span> |<span data-ttu-id="80376-111">Indique le nom de la fonctionnalité que vous souhaitez voir activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="80376-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="80376-112">Source</span><span class="sxs-lookup"><span data-stu-id="80376-112">Source</span></span> |<span data-ttu-id="80376-113">Non implémentée.</span><span class="sxs-lookup"><span data-stu-id="80376-113">Not implemented.</span></span> |
|<span data-ttu-id="80376-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="80376-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="80376-115">Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="80376-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="80376-116">Si la valeur est `$true`, DISM ne contacte pas Windows Update.</span><span class="sxs-lookup"><span data-stu-id="80376-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="80376-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="80376-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="80376-118">Affectez la valeur `$true` pour supprimer tous les fichiers associés à la fonctionnalité quand **Ensure** est défini sur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="80376-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="80376-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="80376-119">LogLevel</span></span> |<span data-ttu-id="80376-120">Niveau de sortie maximal affiché dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="80376-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="80376-121">Les valeurs acceptées sont les suivantes : **ErrorsOnly**, **ErrorsAndWarning** et **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="80376-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="80376-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="80376-122">LogPath</span></span> |<span data-ttu-id="80376-123">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="80376-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="80376-124">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="80376-124">Common properties</span></span>

|<span data-ttu-id="80376-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="80376-125">Property</span></span> |<span data-ttu-id="80376-126">Description</span><span class="sxs-lookup"><span data-stu-id="80376-126">Description</span></span> |
|---|---|
|<span data-ttu-id="80376-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="80376-127">DependsOn</span></span> |<span data-ttu-id="80376-128">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="80376-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="80376-129">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="80376-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="80376-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="80376-130">Ensure</span></span> |<span data-ttu-id="80376-131">Spécifie si la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="80376-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="80376-132">Pour faire en sorte que la fonctionnalité soit activée, affectez à cette propriété la valeur _Enable_.</span><span class="sxs-lookup"><span data-stu-id="80376-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="80376-133">Pour faire en sorte que la fonctionnalité soit désactivée, affectez à cette propriété la valeur _Disable_.</span><span class="sxs-lookup"><span data-stu-id="80376-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="80376-134">La valeur par défaut est _Enable_.</span><span class="sxs-lookup"><span data-stu-id="80376-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="80376-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="80376-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="80376-136">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="80376-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="80376-137">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="80376-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="80376-138">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="80376-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>