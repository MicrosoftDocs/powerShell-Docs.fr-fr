---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsProcess dans DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047344"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="4ad6a-103">Ressource WindowsProcess dans DSC</span><span class="sxs-lookup"><span data-stu-id="4ad6a-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="4ad6a-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="4ad6a-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="4ad6a-105">La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ad6a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ad6a-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="4ad6a-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4ad6a-107">Properties</span></span>

| <span data-ttu-id="4ad6a-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="4ad6a-108">Property</span></span> | <span data-ttu-id="4ad6a-109">Description</span><span class="sxs-lookup"><span data-stu-id="4ad6a-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="4ad6a-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="4ad6a-110">Arguments</span></span>| <span data-ttu-id="4ad6a-111">Indique une chaîne d’arguments à passer au processus en l’état.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="4ad6a-112">Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="4ad6a-113">Path</span><span class="sxs-lookup"><span data-stu-id="4ad6a-113">Path</span></span>| <span data-ttu-id="4ad6a-114">Chemin de l’exécutable du processus.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-114">The path to the process executable.</span></span> <span data-ttu-id="4ad6a-115">S’il s’agit du nom de fichier de l’exécutable (et non du chemin qualifié complet), la ressource DSC recherche la variable d’environnement **Path** (`$env:Path`) pour rechercher le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="4ad6a-116">Si la valeur de cette propriété est un chemin qualifié complet, DSC n’utilise pas la variable d’environnement **Path** pour rechercher le fichier et génère une erreur si le chemin n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="4ad6a-117">Les chemins relatifs ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="4ad6a-118">Credential</span><span class="sxs-lookup"><span data-stu-id="4ad6a-118">Credential</span></span>| <span data-ttu-id="4ad6a-119">Indique les informations d’identification pour démarrer le processus.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="4ad6a-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="4ad6a-120">Ensure</span></span>| <span data-ttu-id="4ad6a-121">Indique si le processus existe.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-121">Indicates if the process exists.</span></span> <span data-ttu-id="4ad6a-122">Définissez cette propriété sur « Present » pour vous assurer que le package existe.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="4ad6a-123">Sinon, donnez-lui la valeur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="4ad6a-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="4ad6a-124">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="4ad6a-124">The default is "Present".</span></span>|
| <span data-ttu-id="4ad6a-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4ad6a-125">DependsOn</span></span> | <span data-ttu-id="4ad6a-126">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4ad6a-127">Par exemple, si vous souhaitez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **ResourceType**, la syntaxe à utiliser pour cette propriété est la suivante : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="4ad6a-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="4ad6a-128">StandardErrorPath</span></span>| <span data-ttu-id="4ad6a-129">Indique le chemin du répertoire dans lequel écrire l’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="4ad6a-130">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="4ad6a-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="4ad6a-131">StandardInputPath</span></span>| <span data-ttu-id="4ad6a-132">Indique l’emplacement d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="4ad6a-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="4ad6a-133">StandardOutputPath</span></span>| <span data-ttu-id="4ad6a-134">Indique l’emplacement où écrire la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="4ad6a-135">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="4ad6a-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="4ad6a-136">WorkingDirectory</span></span>| <span data-ttu-id="4ad6a-137">Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus.</span><span class="sxs-lookup"><span data-stu-id="4ad6a-137">Indicates the location that will be used as the current working directory for the process.</span></span>|