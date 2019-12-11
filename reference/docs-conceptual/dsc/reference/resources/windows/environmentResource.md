---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource Environment DSC
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954716"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="bf853-103">Ressource Environment DSC</span><span class="sxs-lookup"><span data-stu-id="bf853-103">DSC Environment Resource</span></span>

> <span data-ttu-id="bf853-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="bf853-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="bf853-105">La ressource **Environment** dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système.</span><span class="sxs-lookup"><span data-stu-id="bf853-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf853-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf853-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="bf853-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bf853-107">Properties</span></span>

|<span data-ttu-id="bf853-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="bf853-108">Property</span></span> |<span data-ttu-id="bf853-109">Description</span><span class="sxs-lookup"><span data-stu-id="bf853-109">Description</span></span> |
|---|---|
|<span data-ttu-id="bf853-110">Name</span><span class="sxs-lookup"><span data-stu-id="bf853-110">Name</span></span> |<span data-ttu-id="bf853-111">Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="bf853-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="bf853-112">Path</span><span class="sxs-lookup"><span data-stu-id="bf853-112">Path</span></span> |<span data-ttu-id="bf853-113">Définit la variable d’environnement actuellement configurée.</span><span class="sxs-lookup"><span data-stu-id="bf853-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="bf853-114">Définissez cette propriété sur `$true` si la variable est une variable **Path** ; sinon, affectez-lui la valeur `$false`.</span><span class="sxs-lookup"><span data-stu-id="bf853-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="bf853-115">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="bf853-115">The default is `$false`.</span></span> <span data-ttu-id="bf853-116">Si la variable actuellement configurée est une variable **Path**, la valeur fournie par la propriété **Value** est adjointe à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="bf853-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="bf853-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="bf853-117">Value</span></span> |<span data-ttu-id="bf853-118">Valeur à attribuer à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="bf853-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="bf853-119">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="bf853-119">Common properties</span></span>

|<span data-ttu-id="bf853-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="bf853-120">Property</span></span> |<span data-ttu-id="bf853-121">Description</span><span class="sxs-lookup"><span data-stu-id="bf853-121">Description</span></span> |
|---|---|
|<span data-ttu-id="bf853-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bf853-122">DependsOn</span></span> |<span data-ttu-id="bf853-123">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="bf853-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bf853-124">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bf853-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="bf853-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="bf853-125">Ensure</span></span> |<span data-ttu-id="bf853-126">Indique si une variable existe.</span><span class="sxs-lookup"><span data-stu-id="bf853-126">Indicates if a variable exists.</span></span> <span data-ttu-id="bf853-127">Définissez cette propriété sur **Present** pour créer la variable d’environnement s’il n’en existe pas ou pour vérifier que sa valeur correspond à celle fournie par la propriété **Value** si la variable existe déjà.</span><span class="sxs-lookup"><span data-stu-id="bf853-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="bf853-128">Affectez-lui la valeur **Absent** pour supprimer la variable, si elle existe.</span><span class="sxs-lookup"><span data-stu-id="bf853-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="bf853-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bf853-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="bf853-130">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="bf853-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="bf853-131">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="bf853-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="bf853-132">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="bf853-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="bf853-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf853-133">Example</span></span>

<span data-ttu-id="bf853-134">L’exemple suivant vérifie que TestEnvironmentVariable est présent et que sa valeur est _TestValue_.</span><span class="sxs-lookup"><span data-stu-id="bf853-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="bf853-135">S’il n’est pas présent, il le crée.</span><span class="sxs-lookup"><span data-stu-id="bf853-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```