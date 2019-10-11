---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsProcess dans DSC
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952836"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="e633b-103">Ressource WindowsProcess dans DSC</span><span class="sxs-lookup"><span data-stu-id="e633b-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="e633b-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="e633b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="e633b-105">La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="e633b-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e633b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e633b-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e633b-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e633b-107">Properties</span></span>

|<span data-ttu-id="e633b-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="e633b-108">Property</span></span> |<span data-ttu-id="e633b-109">Description</span><span class="sxs-lookup"><span data-stu-id="e633b-109">Description</span></span> |
|---|---|
|<span data-ttu-id="e633b-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="e633b-110">Arguments</span></span> |<span data-ttu-id="e633b-111">Indique une chaîne d’arguments à passer au processus en l’état.</span><span class="sxs-lookup"><span data-stu-id="e633b-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="e633b-112">Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="e633b-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="e633b-113">Path</span><span class="sxs-lookup"><span data-stu-id="e633b-113">Path</span></span> |<span data-ttu-id="e633b-114">Chemin de l’exécutable du processus.</span><span class="sxs-lookup"><span data-stu-id="e633b-114">The path to the process executable.</span></span> <span data-ttu-id="e633b-115">S’il s’agit du nom de fichier de l’exécutable (et non du chemin d’accès complet), la ressource DSC recherche la variable d’environnement `$env:Path` pour rechercher le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="e633b-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="e633b-116">Si la valeur de cette propriété est un chemin d’accès complet, DSC n’utilise pas la variable `$env:Path` pour rechercher le fichier et lève une erreur si le chemin n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="e633b-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="e633b-117">Les chemins relatifs ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="e633b-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="e633b-118">Credential</span><span class="sxs-lookup"><span data-stu-id="e633b-118">Credential</span></span> |<span data-ttu-id="e633b-119">Indique les informations d’identification pour démarrer le processus.</span><span class="sxs-lookup"><span data-stu-id="e633b-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="e633b-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="e633b-120">StandardErrorPath</span></span> |<span data-ttu-id="e633b-121">Indique le chemin du répertoire dans lequel écrire l’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="e633b-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="e633b-122">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="e633b-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="e633b-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="e633b-123">StandardInputPath</span></span> |<span data-ttu-id="e633b-124">Indique l’emplacement d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="e633b-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="e633b-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="e633b-125">StandardOutputPath</span></span> |<span data-ttu-id="e633b-126">Indique l’emplacement où écrire la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="e633b-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="e633b-127">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="e633b-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="e633b-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="e633b-128">WorkingDirectory</span></span> |<span data-ttu-id="e633b-129">Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus.</span><span class="sxs-lookup"><span data-stu-id="e633b-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e633b-130">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="e633b-130">Common properties</span></span>

|<span data-ttu-id="e633b-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="e633b-131">Property</span></span> |<span data-ttu-id="e633b-132">Description</span><span class="sxs-lookup"><span data-stu-id="e633b-132">Description</span></span> |
|---|---|
|<span data-ttu-id="e633b-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e633b-133">DependsOn</span></span> |<span data-ttu-id="e633b-134">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e633b-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e633b-135">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e633b-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e633b-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="e633b-136">Ensure</span></span> |<span data-ttu-id="e633b-137">Indique si le processus existe.</span><span class="sxs-lookup"><span data-stu-id="e633b-137">Indicates if the process exists.</span></span> <span data-ttu-id="e633b-138">Définissez cette propriété sur **Present** pour faire en sorte que le processus existe.</span><span class="sxs-lookup"><span data-stu-id="e633b-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="e633b-139">Sinon, donnez-lui la valeur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="e633b-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="e633b-140">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="e633b-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="e633b-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e633b-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="e633b-142">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e633b-142">Sets the credential for running the entire resource as.</span></span> |