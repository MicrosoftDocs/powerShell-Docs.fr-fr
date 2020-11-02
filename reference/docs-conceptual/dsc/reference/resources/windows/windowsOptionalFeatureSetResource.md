---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource WindowsOptionalFeatureSet dans DSC
description: Ressource WindowsOptionalFeatureSet dans DSC
ms.openlocfilehash: f72cc27bfc8847d2c87cfb289f3e2c729a21d1f4
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143039"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="4fe51-103">Ressource WindowsOptionalFeatureSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="4fe51-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="4fe51-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="4fe51-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="4fe51-105">La ressource **WindowsOptionalFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="4fe51-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="4fe51-106">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource WindowsOptionalFeature](windowsOptionalFeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété **Name** .</span><span class="sxs-lookup"><span data-stu-id="4fe51-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="4fe51-107">Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités facultatives de Windows au même état.</span><span class="sxs-lookup"><span data-stu-id="4fe51-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="4fe51-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe51-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4fe51-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4fe51-109">Properties</span></span>

|<span data-ttu-id="4fe51-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="4fe51-110">Property</span></span> |<span data-ttu-id="4fe51-111">Description</span><span class="sxs-lookup"><span data-stu-id="4fe51-111">Description</span></span> |
|---|---|
|<span data-ttu-id="4fe51-112">Nom</span><span class="sxs-lookup"><span data-stu-id="4fe51-112">Name</span></span> |<span data-ttu-id="4fe51-113">Indique le nom des fonctionnalités que vous souhaitez voir activées ou désactivées.</span><span class="sxs-lookup"><span data-stu-id="4fe51-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="4fe51-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="4fe51-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="4fe51-115">Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="4fe51-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="4fe51-116">Si la valeur est `$true`, DISM ne contacte pas Windows Update.</span><span class="sxs-lookup"><span data-stu-id="4fe51-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="4fe51-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="4fe51-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="4fe51-118">Affectez la valeur `$true` pour supprimer tous les fichiers associés aux fonctionnalités quand **Ensure** est défini sur **Absent** .</span><span class="sxs-lookup"><span data-stu-id="4fe51-118">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent** .</span></span> |
|<span data-ttu-id="4fe51-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="4fe51-119">LogLevel</span></span> |<span data-ttu-id="4fe51-120">Niveau de sortie maximal affiché dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="4fe51-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="4fe51-121">Les valeurs acceptées sont les suivantes : **ErrorsOnly** , **ErrorsAndWarning** et **ErrorsAndWarningAndInformation** .</span><span class="sxs-lookup"><span data-stu-id="4fe51-121">The accepted values are: **ErrorsOnly** , **ErrorsAndWarning** , and **ErrorsAndWarningAndInformation** .</span></span> |
|<span data-ttu-id="4fe51-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="4fe51-122">LogPath</span></span> |<span data-ttu-id="4fe51-123">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="4fe51-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4fe51-124">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="4fe51-124">Common properties</span></span>

|<span data-ttu-id="4fe51-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="4fe51-125">Property</span></span> |<span data-ttu-id="4fe51-126">Description</span><span class="sxs-lookup"><span data-stu-id="4fe51-126">Description</span></span> |
|---|---|
|<span data-ttu-id="4fe51-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4fe51-127">DependsOn</span></span> |<span data-ttu-id="4fe51-128">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="4fe51-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4fe51-129">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4fe51-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4fe51-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="4fe51-130">Ensure</span></span> |<span data-ttu-id="4fe51-131">Spécifie si les fonctionnalités sont activées.</span><span class="sxs-lookup"><span data-stu-id="4fe51-131">Specifies whether the features are enabled.</span></span> <span data-ttu-id="4fe51-132">Pour faire en sorte que les fonctionnalités soient activées, affectez à cette propriété la valeur **Enable** .</span><span class="sxs-lookup"><span data-stu-id="4fe51-132">To ensure that the features are enabled, set this property to **Enable** .</span></span> <span data-ttu-id="4fe51-133">Pour faire en sorte que les fonctionnalités soient désactivées, affectez à cette propriété la valeur **Disable** .</span><span class="sxs-lookup"><span data-stu-id="4fe51-133">To ensure that the features are disabled, set the property to **Disable** .</span></span> <span data-ttu-id="4fe51-134">La valeur par défaut est **Enable** .</span><span class="sxs-lookup"><span data-stu-id="4fe51-134">The default value is **Enable** .</span></span> |
|<span data-ttu-id="4fe51-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4fe51-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="4fe51-136">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="4fe51-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4fe51-137">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="4fe51-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4fe51-138">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="4fe51-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
