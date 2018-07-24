---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsProcess dans DSC
ms.openlocfilehash: 3c4e6d8377c3dcbf4f1db87a603d5483b8caafb8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093733"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="30038-103">Ressource WindowsProcess dans DSC</span><span class="sxs-lookup"><span data-stu-id="30038-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="30038-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="30038-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="30038-105">La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="30038-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="30038-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30038-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="30038-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="30038-107">Properties</span></span>

|  <span data-ttu-id="30038-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="30038-108">Property</span></span>  |  <span data-ttu-id="30038-109">Description</span><span class="sxs-lookup"><span data-stu-id="30038-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="30038-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="30038-110">Arguments</span></span>| <span data-ttu-id="30038-111">Indique une chaîne d’arguments à passer au processus en l’état.</span><span class="sxs-lookup"><span data-stu-id="30038-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="30038-112">Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="30038-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="30038-113">Path</span><span class="sxs-lookup"><span data-stu-id="30038-113">Path</span></span>| <span data-ttu-id="30038-114">Chemin de l’exécutable du processus.</span><span class="sxs-lookup"><span data-stu-id="30038-114">The path to the process executable.</span></span> <span data-ttu-id="30038-115">S’il s’agit du nom de fichier de l’exécutable (et non du chemin qualifié complet), la ressource DSC recherche la variable d’environnement **Path** (`$env:Path`) pour rechercher le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="30038-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="30038-116">Si la valeur de cette propriété est un chemin qualifié complet, DSC n’utilise pas la variable d’environnement **Path** pour rechercher le fichier et génère une erreur si le chemin n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="30038-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="30038-117">Les chemins relatifs ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="30038-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="30038-118">Credential</span><span class="sxs-lookup"><span data-stu-id="30038-118">Credential</span></span>| <span data-ttu-id="30038-119">Indique les informations d’identification pour démarrer le processus.</span><span class="sxs-lookup"><span data-stu-id="30038-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="30038-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="30038-120">Ensure</span></span>| <span data-ttu-id="30038-121">Indique si le processus existe.</span><span class="sxs-lookup"><span data-stu-id="30038-121">Indicates if the process exists.</span></span> <span data-ttu-id="30038-122">Définissez cette propriété sur « Present » pour vous assurer que le package existe.</span><span class="sxs-lookup"><span data-stu-id="30038-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="30038-123">Sinon, donnez-lui la valeur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="30038-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="30038-124">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="30038-124">The default is "Present".</span></span>|
| <span data-ttu-id="30038-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="30038-125">DependsOn</span></span> | <span data-ttu-id="30038-126">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="30038-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="30038-127">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est « DependsOn = "[ResourceType]ResourceName" ».</span><span class="sxs-lookup"><span data-stu-id="30038-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="30038-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="30038-128">StandardErrorPath</span></span>| <span data-ttu-id="30038-129">Indique le chemin du répertoire dans lequel écrire l’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="30038-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="30038-130">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="30038-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="30038-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="30038-131">StandardInputPath</span></span>| <span data-ttu-id="30038-132">Indique l’emplacement d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="30038-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="30038-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="30038-133">StandardOutputPath</span></span>| <span data-ttu-id="30038-134">Indique l’emplacement où écrire la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="30038-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="30038-135">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="30038-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="30038-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="30038-136">WorkingDirectory</span></span>| <span data-ttu-id="30038-137">Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus.</span><span class="sxs-lookup"><span data-stu-id="30038-137">Indicates the location that will be used as the current working directory for the process.</span></span>|