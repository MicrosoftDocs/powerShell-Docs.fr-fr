---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressources WindowsFeatureSet dans DSC
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952956"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="c8690-103">Ressources WindowsFeatureSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="c8690-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="c8690-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c8690-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="c8690-105">La ressource **WindowsFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="c8690-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="c8690-106">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource WindowsFeature](windowsfeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="c8690-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="c8690-107">Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités de Windows au même état.</span><span class="sxs-lookup"><span data-stu-id="c8690-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8690-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8690-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c8690-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c8690-109">Properties</span></span>

|  <span data-ttu-id="c8690-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="c8690-110">Property</span></span>  |  <span data-ttu-id="c8690-111">Description</span><span class="sxs-lookup"><span data-stu-id="c8690-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="c8690-112">Name</span><span class="sxs-lookup"><span data-stu-id="c8690-112">Name</span></span> |<span data-ttu-id="c8690-113">Nom des rôles ou fonctionnalités dont vous voulez garantir l’ajout ou la suppression.</span><span class="sxs-lookup"><span data-stu-id="c8690-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="c8690-114">Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps), et non du nom d’affichage des rôles ou des fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="c8690-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="c8690-115">Source</span><span class="sxs-lookup"><span data-stu-id="c8690-115">Source</span></span> |<span data-ttu-id="c8690-116">Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c8690-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="c8690-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="c8690-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="c8690-118">Affectez la valeur `$true` à cette propriété pour inclure toutes les sous-fonctionnalités requises avec les fonctionnalités que vous spécifiez avec la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="c8690-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="c8690-119">Credential</span><span class="sxs-lookup"><span data-stu-id="c8690-119">Credential</span></span> |<span data-ttu-id="c8690-120">Informations d’identification à utiliser pour ajouter ou supprimer les rôles ou les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c8690-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="c8690-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="c8690-121">LogPath</span></span> |<span data-ttu-id="c8690-122">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="c8690-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c8690-123">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="c8690-123">Common properties</span></span>

|<span data-ttu-id="c8690-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="c8690-124">Property</span></span> |<span data-ttu-id="c8690-125">Description</span><span class="sxs-lookup"><span data-stu-id="c8690-125">Description</span></span> |
|---|---|
|<span data-ttu-id="c8690-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c8690-126">DependsOn</span></span> |<span data-ttu-id="c8690-127">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="c8690-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c8690-128">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c8690-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c8690-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="c8690-129">Ensure</span></span> |<span data-ttu-id="c8690-130">Indique si les rôles ou fonctionnalités sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="c8690-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="c8690-131">Pour faire en sorte que les rôles ou les fonctionnalités soient ajoutés, définissez cette propriété sur **Present**.</span><span class="sxs-lookup"><span data-stu-id="c8690-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="c8690-132">Pour faire en sorte que les rôles ou les fonctionnalités soient supprimés, définissez cette propriété sur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="c8690-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="c8690-133">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="c8690-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="c8690-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c8690-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="c8690-135">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="c8690-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c8690-136">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="c8690-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c8690-137">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="c8690-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c8690-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8690-138">Example</span></span>

<span data-ttu-id="c8690-139">La configuration suivante garantit que les fonctionnalités **Serveur Web** (IIS) et **Serveur SMTP**, et toutes leurs sous-fonctionnalités, sont installées.</span><span class="sxs-lookup"><span data-stu-id="c8690-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```