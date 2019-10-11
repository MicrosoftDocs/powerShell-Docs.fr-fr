---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxPackage dans DSC pour Linux
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954816"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="56353-103">Ressource nxPackage dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="56353-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="56353-104">La ressource **nxPackage** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des packages sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="56353-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="56353-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56353-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="56353-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="56353-106">Properties</span></span>

|<span data-ttu-id="56353-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="56353-107">Property</span></span> |<span data-ttu-id="56353-108">Description</span><span class="sxs-lookup"><span data-stu-id="56353-108">Description</span></span> |
|---|---|
|<span data-ttu-id="56353-109">Name</span><span class="sxs-lookup"><span data-stu-id="56353-109">Name</span></span> |<span data-ttu-id="56353-110">Nom du package pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="56353-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="56353-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="56353-111">PackageManager</span></span> |<span data-ttu-id="56353-112">Les valeurs prises en charge sont **yum**, **apt** et **zypper**.</span><span class="sxs-lookup"><span data-stu-id="56353-112">Supported values are **yum**, **apt**, and **zypper**.</span></span> <span data-ttu-id="56353-113">Spécifie le gestionnaire de package à utiliser lors de l’installation de packages.</span><span class="sxs-lookup"><span data-stu-id="56353-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="56353-114">Si **FilePath** est spécifié, le chemin fourni est utilisé pour installer le package.</span><span class="sxs-lookup"><span data-stu-id="56353-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="56353-115">Sinon, un gestionnaire de package est utilisé pour installer le package à partir d’un référentiel préconfiguré.</span><span class="sxs-lookup"><span data-stu-id="56353-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="56353-116">Si ni **PackageManager** ni **FilePath** ne sont spécifiés, le gestionnaire de package par défaut pour le système est utilisé.</span><span class="sxs-lookup"><span data-stu-id="56353-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="56353-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="56353-117">PackageGroup</span></span> |<span data-ttu-id="56353-118">Si sa valeur est `$true`, **Name** doit correspondre au nom d’un groupe de package à utiliser avec **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="56353-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="56353-119">**PackageGroup** n’est pas valide si **FilePath** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="56353-119">**PackageGroup** is not valid when providing a **FilePath**.</span></span> |
|<span data-ttu-id="56353-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="56353-120">Arguments</span></span> |<span data-ttu-id="56353-121">Chaîne d’arguments transmise telle quelle au package.</span><span class="sxs-lookup"><span data-stu-id="56353-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="56353-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="56353-122">ReturnCode</span></span> |<span data-ttu-id="56353-123">Code de retour attendu.</span><span class="sxs-lookup"><span data-stu-id="56353-123">The expected return code.</span></span> <span data-ttu-id="56353-124">Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="56353-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="56353-125">FilePath</span><span class="sxs-lookup"><span data-stu-id="56353-125">FilePath</span></span> |<span data-ttu-id="56353-126">Chemin du fichier contenant le package.</span><span class="sxs-lookup"><span data-stu-id="56353-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="56353-127">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="56353-127">Common properties</span></span>

|<span data-ttu-id="56353-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="56353-128">Property</span></span> |<span data-ttu-id="56353-129">Description</span><span class="sxs-lookup"><span data-stu-id="56353-129">Description</span></span> |
|---|---|
|<span data-ttu-id="56353-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="56353-130">DependsOn</span></span> |<span data-ttu-id="56353-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="56353-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="56353-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="56353-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="56353-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="56353-133">Ensure</span></span> |<span data-ttu-id="56353-134">Détermine si l’existence du package doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="56353-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="56353-135">Définissez cette propriété sur **Present** pour vous assurer que le package existe.</span><span class="sxs-lookup"><span data-stu-id="56353-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="56353-136">Définissez la propriété sur **Absent** pour vous assurer que le package n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="56353-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="56353-137">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="56353-137">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="56353-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="56353-138">Example</span></span>

<span data-ttu-id="56353-139">L’exemple suivant vérifie que le package nommé « httpd » a été installé sur un ordinateur Linux, à l’aide du gestionnaire de package « Yum ».</span><span class="sxs-lookup"><span data-stu-id="56353-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```