---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxPackage dans DSC pour Linux
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="f1f81-103">Ressource nxPackage dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="f1f81-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="f1f81-104">La ressource **nxPackage** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des packages sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="f1f81-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1f81-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1f81-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a><span data-ttu-id="f1f81-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f1f81-106">Properties</span></span>

|  <span data-ttu-id="f1f81-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="f1f81-107">Property</span></span> |  <span data-ttu-id="f1f81-108">Description</span><span class="sxs-lookup"><span data-stu-id="f1f81-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="f1f81-109">Name</span><span class="sxs-lookup"><span data-stu-id="f1f81-109">Name</span></span>| <span data-ttu-id="f1f81-110">Nom du package pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="f1f81-110">The name of the package for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="f1f81-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="f1f81-111">Ensure</span></span>| <span data-ttu-id="f1f81-112">Détermine si l’existence du package doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="f1f81-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="f1f81-113">Définissez cette propriété sur « Present » pour vous assurer que le package existe.</span><span class="sxs-lookup"><span data-stu-id="f1f81-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="f1f81-114">Définissez la propriété sur « Absent » pour vous assurer que le package n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="f1f81-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="f1f81-115">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="f1f81-115">The default value is "Present".</span></span>|  
| <span data-ttu-id="f1f81-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="f1f81-116">PackageManager</span></span>| <span data-ttu-id="f1f81-117">Les valeurs prises en charge sont « yum », « apt » et « zypper ».</span><span class="sxs-lookup"><span data-stu-id="f1f81-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="f1f81-118">Spécifie le gestionnaire de package à utiliser lors de l’installation de packages.</span><span class="sxs-lookup"><span data-stu-id="f1f81-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="f1f81-119">Si **FilePath** est spécifié, le chemin fourni est utilisé pour installer le package.</span><span class="sxs-lookup"><span data-stu-id="f1f81-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="f1f81-120">Sinon, un gestionnaire de package est utilisé pour installer le package à partir d’un référentiel préconfiguré.</span><span class="sxs-lookup"><span data-stu-id="f1f81-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="f1f81-121">Si ni **PackageManager** ni **FilePath** ne sont spécifiés, le gestionnaire de package par défaut pour le système est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f1f81-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>| 
| <span data-ttu-id="f1f81-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="f1f81-122">FilePath</span></span>| <span data-ttu-id="f1f81-123">Chemin du fichier contenant le package.</span><span class="sxs-lookup"><span data-stu-id="f1f81-123">The file path where the package resides</span></span>| 
| <span data-ttu-id="f1f81-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="f1f81-124">PackageGroup</span></span>| <span data-ttu-id="f1f81-125">Si sa valeur est **$true**, **Name** doit correspondre au nom d’un groupe de package à utiliser avec **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="f1f81-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="f1f81-126">**PackageGroup** n’est pas valide si **FilePath** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="f1f81-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>| 
| <span data-ttu-id="f1f81-127">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1f81-127">Arguments</span></span>| <span data-ttu-id="f1f81-128">Chaîne d’arguments transmise telle quelle au package.</span><span class="sxs-lookup"><span data-stu-id="f1f81-128">A string of arguments that will be passed to the package exactly as provided.</span></span>| 
| <span data-ttu-id="f1f81-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="f1f81-129">ReturnCode</span></span>| <span data-ttu-id="f1f81-130">Code de retour attendu.</span><span class="sxs-lookup"><span data-stu-id="f1f81-130">The expected return code.</span></span> <span data-ttu-id="f1f81-131">Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="f1f81-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>| 
| <span data-ttu-id="f1f81-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f1f81-132">DependsOn</span></span> | <span data-ttu-id="f1f81-133">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="f1f81-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f1f81-134">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f1f81-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="f1f81-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="f1f81-135">Example</span></span>

<span data-ttu-id="f1f81-136">L’exemple suivant vérifie que le package nommé « httpd » a été installé sur un ordinateur Linux, à l’aide du gestionnaire de package « Yum ».</span><span class="sxs-lookup"><span data-stu-id="f1f81-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

