---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,installation
title: Ressource Environment DSC
ms.openlocfilehash: d8519a66d457767dcbc0e08b01a69a9264997479
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464415"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="807f1-103">Ressource Environment DSC</span><span class="sxs-lookup"><span data-stu-id="807f1-103">DSC Environment Resource</span></span>

> <span data-ttu-id="807f1-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="807f1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="807f1-105">La ressource **Environment** dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système.</span><span class="sxs-lookup"><span data-stu-id="807f1-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="807f1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="807f1-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="807f1-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="807f1-107">Properties</span></span>

|<span data-ttu-id="807f1-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="807f1-108">Property</span></span> |<span data-ttu-id="807f1-109">Description</span><span class="sxs-lookup"><span data-stu-id="807f1-109">Description</span></span> |
|---|---|
|<span data-ttu-id="807f1-110">Name</span><span class="sxs-lookup"><span data-stu-id="807f1-110">Name</span></span> |<span data-ttu-id="807f1-111">Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="807f1-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="807f1-112">Path</span><span class="sxs-lookup"><span data-stu-id="807f1-112">Path</span></span> |<span data-ttu-id="807f1-113">Définit la variable d’environnement actuellement configurée.</span><span class="sxs-lookup"><span data-stu-id="807f1-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="807f1-114">Définissez cette propriété sur `$true` si la variable est une variable **Path** ; sinon, affectez-lui la valeur `$false`.</span><span class="sxs-lookup"><span data-stu-id="807f1-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="807f1-115">Par défaut, il s’agit de `$false`.</span><span class="sxs-lookup"><span data-stu-id="807f1-115">The default is `$false`.</span></span> <span data-ttu-id="807f1-116">Si la variable actuellement configurée est une variable **Path**, la valeur fournie par la propriété **Value** est adjointe à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="807f1-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="807f1-117">Cible</span><span class="sxs-lookup"><span data-stu-id="807f1-117">Target</span></span>| <span data-ttu-id="807f1-118">Indique où récupérer la variable : Sur l’ordinateur ou le processus.</span><span class="sxs-lookup"><span data-stu-id="807f1-118">Indicates where to retrieve the variable: The machine or the process.</span></span> <span data-ttu-id="807f1-119">Si les deux sont indiqués, seule la valeur de l’ordinateur est retournée.</span><span class="sxs-lookup"><span data-stu-id="807f1-119">If both are indicated then only the value from the machine is returned.</span></span> <span data-ttu-id="807f1-120">La valeur par défaut correspond aux deux, car il s’agit de la valeur par défaut du reste de la ressource.</span><span class="sxs-lookup"><span data-stu-id="807f1-120">The default is both since that is the default for the rest of the resource.</span></span> |
|<span data-ttu-id="807f1-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="807f1-121">Value</span></span> |<span data-ttu-id="807f1-122">Valeur à attribuer à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="807f1-122">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="807f1-123">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="807f1-123">Common properties</span></span>

|<span data-ttu-id="807f1-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="807f1-124">Property</span></span> |<span data-ttu-id="807f1-125">Description</span><span class="sxs-lookup"><span data-stu-id="807f1-125">Description</span></span> |
|---|---|
|<span data-ttu-id="807f1-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="807f1-126">DependsOn</span></span> |<span data-ttu-id="807f1-127">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="807f1-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="807f1-128">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="807f1-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="807f1-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="807f1-129">Ensure</span></span> |<span data-ttu-id="807f1-130">Indique si une variable existe.</span><span class="sxs-lookup"><span data-stu-id="807f1-130">Indicates if a variable exists.</span></span> <span data-ttu-id="807f1-131">Définissez cette propriété sur **Present** pour créer la variable d’environnement s’il n’en existe pas ou pour vérifier que sa valeur correspond à celle fournie par la propriété **Value** si la variable existe déjà.</span><span class="sxs-lookup"><span data-stu-id="807f1-131">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="807f1-132">Affectez-lui la valeur **Absent** pour supprimer la variable, si elle existe.</span><span class="sxs-lookup"><span data-stu-id="807f1-132">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="807f1-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="807f1-133">PsDscRunAsCredential</span></span> |<span data-ttu-id="807f1-134">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="807f1-134">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="807f1-135">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="807f1-135">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="807f1-136">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="807f1-136">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="807f1-137"> Exemple</span><span class="sxs-lookup"><span data-stu-id="807f1-137">Example</span></span>

<span data-ttu-id="807f1-138">L’exemple suivant vérifie que TestEnvironmentVariable est présent et que sa valeur est _TestValue_.</span><span class="sxs-lookup"><span data-stu-id="807f1-138">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="807f1-139">S’il n’est pas présent, il le crée.</span><span class="sxs-lookup"><span data-stu-id="807f1-139">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
