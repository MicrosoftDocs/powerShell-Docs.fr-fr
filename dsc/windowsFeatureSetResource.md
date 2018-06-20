---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources WindowsFeatureSet dans DSC
ms.openlocfilehash: 582f9b1f439056118680f6f814d2c202d0e823be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186726"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="8d0b4-103">Ressources WindowsFeatureSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="8d0b4-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="8d0b4-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8d0b4-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8d0b4-105">La ressource **WindowsFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="8d0b4-106">Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [WindowsFeature](windowsfeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="8d0b4-107">Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités de Windows au même état.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d0b4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d0b4-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="8d0b4-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8d0b4-109">Properties</span></span>

|  <span data-ttu-id="8d0b4-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="8d0b4-110">Property</span></span>  |  <span data-ttu-id="8d0b4-111">Description</span><span class="sxs-lookup"><span data-stu-id="8d0b4-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="8d0b4-112">Name</span><span class="sxs-lookup"><span data-stu-id="8d0b4-112">Name</span></span>| <span data-ttu-id="8d0b4-113">Nom des rôles ou fonctionnalités dont vous voulez garantir l’ajout ou la suppression.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="8d0b4-114">Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx), et non du nom d’affichage des rôles ou des fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="8d0b4-115">Credential</span><span class="sxs-lookup"><span data-stu-id="8d0b4-115">Credential</span></span>| <span data-ttu-id="8d0b4-116">Informations d’identification à utiliser pour ajouter ou supprimer les rôles ou les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="8d0b4-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="8d0b4-117">Ensure</span></span>| <span data-ttu-id="8d0b4-118">Indique si les rôles ou fonctionnalités sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="8d0b4-119">Pour vous assurer que les rôles ou fonctionnalités sont ajoutés, affectez la valeur « Present » à cette propriété. Pour vous assurer que les rôles ou fonctionnalités sont supprimés, affectez la valeur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="8d0b4-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="8d0b4-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="8d0b4-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="8d0b4-121">Affectez la valeur **$true** à cette propriété pour inclure toutes les sous-fonctionnalités requises avec la fonctionnalité que vous spécifiez avec la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="8d0b4-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="8d0b4-122">LogPath</span></span>| <span data-ttu-id="8d0b4-123">Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="8d0b4-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8d0b4-124">DependsOn</span></span>| <span data-ttu-id="8d0b4-125">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8d0b4-126">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="8d0b4-127">Source</span><span class="sxs-lookup"><span data-stu-id="8d0b4-127">Source</span></span>| <span data-ttu-id="8d0b4-128">Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="8d0b4-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d0b4-129">Example</span></span>

<span data-ttu-id="8d0b4-130">La configuration suivante garantit que les fonctionnalités **Serveur Web** (IIS) et **Serveur SMTP**, et toutes leurs sous-fonctionnalités, sont installées.</span><span class="sxs-lookup"><span data-stu-id="8d0b4-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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