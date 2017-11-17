---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource Environment DSC
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="120ba-103">Ressource Environment DSC</span><span class="sxs-lookup"><span data-stu-id="120ba-103">DSC Environment Resource</span></span>

> <span data-ttu-id="120ba-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="120ba-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="120ba-105">La ressource __Environment__ dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système.</span><span class="sxs-lookup"><span data-stu-id="120ba-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="120ba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="120ba-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="120ba-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="120ba-107">Properties</span></span>

|  <span data-ttu-id="120ba-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="120ba-108">Property</span></span>  |  <span data-ttu-id="120ba-109">Description</span><span class="sxs-lookup"><span data-stu-id="120ba-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="120ba-110">Nom</span><span class="sxs-lookup"><span data-stu-id="120ba-110">Name</span></span>| <span data-ttu-id="120ba-111">Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="120ba-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="120ba-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="120ba-112">Ensure</span></span>| <span data-ttu-id="120ba-113">Indique si une variable existe.</span><span class="sxs-lookup"><span data-stu-id="120ba-113">Indicates if a variable exists.</span></span> <span data-ttu-id="120ba-114">Définissez cette propriété sur __Present__ pour créer la variable d’environnement s’il n’en existe pas ou pour vérifier que sa valeur correspond à celle fournie par la propriété __Value__ si la variable existe déjà.</span><span class="sxs-lookup"><span data-stu-id="120ba-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="120ba-115">Affectez-lui la valeur __Absent__ pour supprimer la variable, si elle existe.</span><span class="sxs-lookup"><span data-stu-id="120ba-115">Set it to __Absent__ to delete the variable if it exists.</span></span>| 
| <span data-ttu-id="120ba-116">Path</span><span class="sxs-lookup"><span data-stu-id="120ba-116">Path</span></span>| <span data-ttu-id="120ba-117">Définit la variable d’environnement actuellement configurée.</span><span class="sxs-lookup"><span data-stu-id="120ba-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="120ba-118">Définissez cette propriété sur __$true__ si la variable est une variable __Path__ ; sinon, affectez-lui la valeur __$false__.</span><span class="sxs-lookup"><span data-stu-id="120ba-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="120ba-119">La valeur par défaut est __$false__.</span><span class="sxs-lookup"><span data-stu-id="120ba-119">The default is __$false__.</span></span> <span data-ttu-id="120ba-120">Si la variable actuellement configurée est une variable __Path__, la valeur fournie par la propriété __Value__ est adjointe à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="120ba-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>| 
| <span data-ttu-id="120ba-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="120ba-121">DependsOn</span></span> | <span data-ttu-id="120ba-122">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="120ba-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="120ba-123">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="120ba-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="120ba-124">Value</span><span class="sxs-lookup"><span data-stu-id="120ba-124">Value</span></span>| <span data-ttu-id="120ba-125">Valeur à attribuer à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="120ba-125">The value to assign to the environment variable.</span></span>| 

## <a name="example"></a><span data-ttu-id="120ba-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="120ba-126">Example</span></span>

<span data-ttu-id="120ba-127">L’exemple suivant vérifie que __TestEnvironmentVariable__ est présent et que sa valeur est __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="120ba-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="120ba-128">S’il n’est pas présent, il le crée.</span><span class="sxs-lookup"><span data-stu-id="120ba-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

