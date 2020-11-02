---
ms.date: 07/17/2020
ms.topic: reference
title: Ressource nxEnvironment dans DSC pour Linux
description: Ressource nxEnvironment dans DSC pour Linux
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644678"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="8f7f9-103">Ressource nxEnvironment dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="8f7f9-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="8f7f9-104">La ressource **nxEnvironment** de DSC (Desired State Configuration) PowerShell offre un mécanisme permettant de gérer les variables d’environnement système sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f7f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f7f9-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="8f7f9-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8f7f9-106">Properties</span></span>

|<span data-ttu-id="8f7f9-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="8f7f9-107">Property</span></span> |<span data-ttu-id="8f7f9-108">Description</span><span class="sxs-lookup"><span data-stu-id="8f7f9-108">Description</span></span> |
|---|---|
|<span data-ttu-id="8f7f9-109">Name</span><span class="sxs-lookup"><span data-stu-id="8f7f9-109">Name</span></span> |<span data-ttu-id="8f7f9-110">Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="8f7f9-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="8f7f9-111">Value</span></span> |<span data-ttu-id="8f7f9-112">Valeur à attribuer à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="8f7f9-113">Path</span><span class="sxs-lookup"><span data-stu-id="8f7f9-113">Path</span></span> |<span data-ttu-id="8f7f9-114">Définit la variable d’environnement actuellement configurée.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="8f7f9-115">Définissez cette propriété sur `$true` si la variable est une variable **Path**  ; sinon, affectez-lui la valeur `$false`.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="8f7f9-116">Par défaut, il s’agit de `$false`.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-116">The default is `$false`.</span></span> <span data-ttu-id="8f7f9-117">Si la variable actuellement configurée est une variable **Path** , la valeur fournie par la propriété **Value** est adjointe à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8f7f9-118">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="8f7f9-118">Common properties</span></span>

|<span data-ttu-id="8f7f9-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="8f7f9-119">Property</span></span> |<span data-ttu-id="8f7f9-120">Description</span><span class="sxs-lookup"><span data-stu-id="8f7f9-120">Description</span></span> |
|---|---|
|<span data-ttu-id="8f7f9-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8f7f9-121">DependsOn</span></span> |<span data-ttu-id="8f7f9-122">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8f7f9-123">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="8f7f9-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="8f7f9-124">Ensure</span></span> |<span data-ttu-id="8f7f9-125">Détermine si l’existence de la variable doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="8f7f9-126">Définissez cette propriété sur **Present** pour vous assurer que la variable existe.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="8f7f9-127">Définissez la propriété sur **Absent** pour vous assurer que la variable n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="8f7f9-128">La valeur par défaut est **Present** .</span><span class="sxs-lookup"><span data-stu-id="8f7f9-128">The default value is **Present** .</span></span> |

## <a name="additional-information"></a><span data-ttu-id="8f7f9-129">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8f7f9-129">Additional Information</span></span>

- <span data-ttu-id="8f7f9-130">Si **Path** est absent ou a la valeur `$false`, les variables d’environnement sont gérées dans `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="8f7f9-131">Vos programmes ou vos scripts peuvent nécessiter que la configuration « source » le fichier `/etc/environment` pour accéder aux variables d’environnement gérées.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="8f7f9-132">Si **Path** est défini sur `$true`, la variable d’environnement est gérée dans le fichier `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="8f7f9-133">Ce fichier est créé s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="8f7f9-134">Si **Ensure** est défini sur **Absent** et **Path** sur `$true`, une variable d’environnement existante est supprimée de `/etc/profile.d/DSCenvironment.sh`, mais pas des autres fichiers.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="8f7f9-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f7f9-135">Example</span></span>

<span data-ttu-id="8f7f9-136">L’exemple suivant montre comment utiliser la ressource **nxEnvironment** pour s’assurer que **TestEnvironmentVariable** est présent et a la valeur Test-Value.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="8f7f9-137">Si **TestEnvironmentVariable** est absent, il est créé.</span><span class="sxs-lookup"><span data-stu-id="8f7f9-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
