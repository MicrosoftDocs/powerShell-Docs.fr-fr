---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsProcess dans DSC
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="61aaa-103">Ressource WindowsProcess dans DSC</span><span class="sxs-lookup"><span data-stu-id="61aaa-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="61aaa-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="61aaa-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="61aaa-105">La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="61aaa-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="61aaa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61aaa-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="61aaa-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="61aaa-107">Properties</span></span>
|  <span data-ttu-id="61aaa-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="61aaa-108">Property</span></span>  |  <span data-ttu-id="61aaa-109">Description</span><span class="sxs-lookup"><span data-stu-id="61aaa-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="61aaa-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="61aaa-110">Arguments</span></span>| <span data-ttu-id="61aaa-111">Indique une chaîne d’arguments à passer au processus en l’état.</span><span class="sxs-lookup"><span data-stu-id="61aaa-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="61aaa-112">Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="61aaa-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="61aaa-113">Path</span><span class="sxs-lookup"><span data-stu-id="61aaa-113">Path</span></span>| <span data-ttu-id="61aaa-114">Chemin de l’exécutable du processus.</span><span class="sxs-lookup"><span data-stu-id="61aaa-114">The path to the process executable.</span></span> <span data-ttu-id="61aaa-115">S’il s’agit du nom de fichier de l’exécutable (et non du chemin qualifié complet), la ressource DSC recherche la variable d’environnement **Path** (`$env:Path`) pour rechercher le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="61aaa-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="61aaa-116">Si la valeur de cette propriété est un chemin qualifié complet, DSC n’utilise pas la variable d’environnement **Path** pour rechercher le fichier et génère une erreur si le chemin n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="61aaa-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="61aaa-117">Les chemins relatifs ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="61aaa-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="61aaa-118">Credential</span><span class="sxs-lookup"><span data-stu-id="61aaa-118">Credential</span></span>| <span data-ttu-id="61aaa-119">Indique les informations d’identification pour démarrer le processus.</span><span class="sxs-lookup"><span data-stu-id="61aaa-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="61aaa-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="61aaa-120">Ensure</span></span>| <span data-ttu-id="61aaa-121">Indique si le processus existe.</span><span class="sxs-lookup"><span data-stu-id="61aaa-121">Indicates if the process exists.</span></span> <span data-ttu-id="61aaa-122">Définissez cette propriété sur « Present » pour vous assurer que le package existe.</span><span class="sxs-lookup"><span data-stu-id="61aaa-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="61aaa-123">Sinon, donnez-lui la valeur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="61aaa-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="61aaa-124">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="61aaa-124">The default is "Present".</span></span>|
| <span data-ttu-id="61aaa-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="61aaa-125">DependsOn</span></span> | <span data-ttu-id="61aaa-126">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="61aaa-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="61aaa-127">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est « DependsOn = "[ResourceType]ResourceName" ».</span><span class="sxs-lookup"><span data-stu-id="61aaa-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="61aaa-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="61aaa-128">StandardErrorPath</span></span>| <span data-ttu-id="61aaa-129">Indique le chemin du répertoire dans lequel écrire l’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="61aaa-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="61aaa-130">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="61aaa-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="61aaa-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="61aaa-131">StandardInputPath</span></span>| <span data-ttu-id="61aaa-132">Indique l’emplacement d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="61aaa-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="61aaa-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="61aaa-133">StandardOutputPath</span></span>| <span data-ttu-id="61aaa-134">Indique l’emplacement où écrire la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="61aaa-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="61aaa-135">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="61aaa-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="61aaa-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="61aaa-136">WorkingDirectory</span></span>| <span data-ttu-id="61aaa-137">Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus.</span><span class="sxs-lookup"><span data-stu-id="61aaa-137">Indicates the location that will be used as the current working directory for the process.</span></span>|