---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources ProcessSet dans DSC
ms.openlocfilehash: d18d2c96239abd83cea735e0fbce198d0456cea6
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093988"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="7ada4-103">Ressource WindowsProcess dans DSC</span><span class="sxs-lookup"><span data-stu-id="7ada4-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="7ada4-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7ada4-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7ada4-105">La ressource **ProcessSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="7ada4-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="7ada4-106">Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [WindowsProcess](windowsProcessResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="7ada4-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ada4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ada4-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7ada4-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7ada4-108">Properties</span></span>

|  <span data-ttu-id="7ada4-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="7ada4-109">Property</span></span>  |  <span data-ttu-id="7ada4-110">Description</span><span class="sxs-lookup"><span data-stu-id="7ada4-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="7ada4-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="7ada4-111">Arguments</span></span>| <span data-ttu-id="7ada4-112">Chaîne qui contient les arguments à passer au processus en l’état.</span><span class="sxs-lookup"><span data-stu-id="7ada4-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="7ada4-113">Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="7ada4-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="7ada4-114">Path</span><span class="sxs-lookup"><span data-stu-id="7ada4-114">Path</span></span>| <span data-ttu-id="7ada4-115">Chemins vers les exécutables du processus.</span><span class="sxs-lookup"><span data-stu-id="7ada4-115">The paths to the process executables.</span></span> <span data-ttu-id="7ada4-116">S’il s’agit des noms des fichiers exécutables (et non des chemins qualifiés complets), la ressource DSC recherche la variable d’environnement **Path** (`$env:Path`) pour rechercher les fichiers.</span><span class="sxs-lookup"><span data-stu-id="7ada4-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="7ada4-117">Si les valeurs de cette propriété sont des chemins qualifiés complets, DSC n’utilise pas la variable d’environnement **Path** pour rechercher les fichiers et génère une erreur si l’un des chemins n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="7ada4-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="7ada4-118">Les chemins relatifs ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="7ada4-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="7ada4-119">Credential</span><span class="sxs-lookup"><span data-stu-id="7ada4-119">Credential</span></span>| <span data-ttu-id="7ada4-120">Indique les informations d’identification pour démarrer le processus.</span><span class="sxs-lookup"><span data-stu-id="7ada4-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="7ada4-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="7ada4-121">Ensure</span></span>| <span data-ttu-id="7ada4-122">Spécifie si les processus existent.</span><span class="sxs-lookup"><span data-stu-id="7ada4-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="7ada4-123">Définissez cette propriété sur « Present » pour vous assurer que le package existe.</span><span class="sxs-lookup"><span data-stu-id="7ada4-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="7ada4-124">Sinon, donnez-lui la valeur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="7ada4-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="7ada4-125">La valeur par défaut est Present.</span><span class="sxs-lookup"><span data-stu-id="7ada4-125">The default is "Present".</span></span>|
| <span data-ttu-id="7ada4-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="7ada4-126">StandardErrorPath</span></span>| <span data-ttu-id="7ada4-127">Chemin où les processus écrivent l’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="7ada4-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="7ada4-128">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="7ada4-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="7ada4-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="7ada4-129">StandardInputPath</span></span>| <span data-ttu-id="7ada4-130">Flux à partir duquel le processus reçoit l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="7ada4-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="7ada4-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="7ada4-131">StandardOutputPath</span></span>| <span data-ttu-id="7ada4-132">Chemin du fichier où les processus écrivent la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="7ada4-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="7ada4-133">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="7ada4-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="7ada4-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="7ada4-134">WorkingDirectory</span></span>| <span data-ttu-id="7ada4-135">Emplacement utilisé comme répertoire de travail actuel pour les processus.</span><span class="sxs-lookup"><span data-stu-id="7ada4-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="7ada4-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7ada4-136">DependsOn</span></span> | <span data-ttu-id="7ada4-137">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="7ada4-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7ada4-138">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **_ResourceType**, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"</span><span class="sxs-lookup"><span data-stu-id="7ada4-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|