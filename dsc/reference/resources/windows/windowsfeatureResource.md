---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsFeature dans DSC
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047349"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="96e85-103">Ressource WindowsFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="96e85-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="96e85-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="96e85-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="96e85-105">La ressource **WindowsFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="96e85-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="96e85-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96e85-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="96e85-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="96e85-107">Properties</span></span>

|  <span data-ttu-id="96e85-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="96e85-108">Property</span></span>  |  <span data-ttu-id="96e85-109">Description</span><span class="sxs-lookup"><span data-stu-id="96e85-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="96e85-110">Name</span><span class="sxs-lookup"><span data-stu-id="96e85-110">Name</span></span>| <span data-ttu-id="96e85-111">Indique le nom du rôle ou de la fonctionnalité dont vous voulez garantir l’ajout ou la suppression.</span><span class="sxs-lookup"><span data-stu-id="96e85-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="96e85-112">Il s’agit du même nom que celui de la propriété __Name__ de l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) et non du nom d’affichage du rôle ou de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96e85-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="96e85-113">Credential</span><span class="sxs-lookup"><span data-stu-id="96e85-113">Credential</span></span>| <span data-ttu-id="96e85-114">Indique les informations d’identification à utiliser pour ajouter ou supprimer le rôle ou la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96e85-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="96e85-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="96e85-115">Ensure</span></span>| <span data-ttu-id="96e85-116">Indique si le rôle ou la fonctionnalité sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="96e85-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="96e85-117">Pour vous assurer que le rôle ou la fonctionnalité sont ajoutés, définissez cette propriété sur « Present ». Pour que le rôle ou la fonctionnalité soient supprimés, définissez la propriété sur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="96e85-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="96e85-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="96e85-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="96e85-119">Définissez cette propriété sur __$true__ pour garantir que l’état de toutes les sous-fonctionnalités nécessaires est l’état de la fonctionnalité que vous spécifiez avec la propriété __Name__.</span><span class="sxs-lookup"><span data-stu-id="96e85-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="96e85-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="96e85-120">LogPath</span></span>| <span data-ttu-id="96e85-121">Indique le chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="96e85-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="96e85-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="96e85-122">DependsOn</span></span>| <span data-ttu-id="96e85-123">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="96e85-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="96e85-124">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="96e85-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="96e85-125">Source</span><span class="sxs-lookup"><span data-stu-id="96e85-125">Source</span></span>| <span data-ttu-id="96e85-126">Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="96e85-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="96e85-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="96e85-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```