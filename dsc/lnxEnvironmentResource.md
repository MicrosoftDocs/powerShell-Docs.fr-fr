---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxEnvironment dans DSC pour Linux
ms.openlocfilehash: 3c9f39760e0fba7fac060f29f9e808a3a434401f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="d1e2e-103">Ressource nxEnvironment dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="d1e2e-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="d1e2e-104">La ressource **nxEnvironment** dans DSC PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1e2e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1e2e-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="d1e2e-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d1e2e-106">Properties</span></span>

|  <span data-ttu-id="d1e2e-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="d1e2e-107">Property</span></span> |  <span data-ttu-id="d1e2e-108">Description</span><span class="sxs-lookup"><span data-stu-id="d1e2e-108">Description</span></span> |
|---|---|
| <span data-ttu-id="d1e2e-109">Name</span><span class="sxs-lookup"><span data-stu-id="d1e2e-109">Name</span></span>| <span data-ttu-id="d1e2e-110">Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="d1e2e-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="d1e2e-111">Value</span></span>| <span data-ttu-id="d1e2e-112">Valeur à attribuer à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="d1e2e-113">Ensure</span><span class="sxs-lookup"><span data-stu-id="d1e2e-113">Ensure</span></span>| <span data-ttu-id="d1e2e-114">Détermine si l’existence de la variable doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="d1e2e-115">Définissez cette propriété sur « Present » pour vous assurer que la variable existe.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="d1e2e-116">Définissez la propriété sur « Absent » pour vous assurer que la variable n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="d1e2e-117">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="d1e2e-117">The default value is "Present".</span></span>|
| <span data-ttu-id="d1e2e-118">Path</span><span class="sxs-lookup"><span data-stu-id="d1e2e-118">Path</span></span>| <span data-ttu-id="d1e2e-119">Définit la variable d’environnement actuellement configurée.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="d1e2e-120">Définissez cette propriété sur **$true** si la variable est une variable **Path** ; sinon, affectez-lui la valeur **$false**.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="d1e2e-121">La valeur par défaut est **$false**.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-121">The default is **$false**.</span></span> <span data-ttu-id="d1e2e-122">Si la variable actuellement configurée est une variable **Path**, la valeur fournie par la propriété **Value** est adjointe à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="d1e2e-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d1e2e-123">DependsOn</span></span> | <span data-ttu-id="d1e2e-124">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d1e2e-125">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="d1e2e-126">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d1e2e-126">Additional Information</span></span>

* <span data-ttu-id="d1e2e-127">Si **Path** est absent ou a la valeur **$false**, les variables d’environnement sont gérées dans `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="d1e2e-128">Vos programmes ou vos scripts peuvent nécessiter que la configuration « source » le fichier `/etc/environment` pour accéder aux variables d’environnement gérées.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="d1e2e-129">Si **Path** est défini sur **$true**, la variable d’environnement est gérée dans le fichier `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="d1e2e-130">Ce fichier est créé s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="d1e2e-131">Si **Ensure** est défini sur Absent et **Path** sur **$true**, une variable d’environnement existante n’est supprimée que de `/etc/profile.d/DSCenvironment.sh` et pas des autres fichiers.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="d1e2e-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1e2e-132">Example</span></span>

<span data-ttu-id="d1e2e-133">L’exemple suivant montre comment utiliser la ressource **nxEnvironment** pour s’assurer que **TestEnvironmentVariable** est présent et a la valeur Test-Value.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="d1e2e-134">Si **TestEnvironmentVariable** est absent, il est créé.</span><span class="sxs-lookup"><span data-stu-id="d1e2e-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```