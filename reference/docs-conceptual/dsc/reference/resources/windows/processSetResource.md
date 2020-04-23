---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressources ProcessSet dans DSC
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953126"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="275ae-103">Ressources ProcessSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="275ae-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="275ae-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="275ae-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="275ae-105">La ressource **ProcessSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="275ae-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="275ae-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="275ae-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="275ae-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="275ae-107">Properties</span></span>

|<span data-ttu-id="275ae-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="275ae-108">Property</span></span> |<span data-ttu-id="275ae-109">Description</span><span class="sxs-lookup"><span data-stu-id="275ae-109">Description</span></span> |
|---|---|
|<span data-ttu-id="275ae-110">Path</span><span class="sxs-lookup"><span data-stu-id="275ae-110">Path</span></span> |<span data-ttu-id="275ae-111">Chemin de l’exécutable du processus.</span><span class="sxs-lookup"><span data-stu-id="275ae-111">The path to the process executable.</span></span> <span data-ttu-id="275ae-112">S’il s’agit des noms des fichiers exécutables (et non des chemins d’accès complets), la ressource DSC recherche la variable d’environnement `$env:Path` pour rechercher les fichiers.</span><span class="sxs-lookup"><span data-stu-id="275ae-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="275ae-113">Si les valeurs de cette propriété sont des chemins d’accès complets, DSC n’utilise pas la variable d’environnement `$env:Path` pour rechercher les fichiers et lève une erreur si l’un des chemins n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="275ae-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="275ae-114">Les chemins relatifs ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="275ae-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="275ae-115">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="275ae-115">Credential</span></span> |<span data-ttu-id="275ae-116">Indique les informations d’identification pour démarrer le processus.</span><span class="sxs-lookup"><span data-stu-id="275ae-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="275ae-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="275ae-117">StandardErrorPath</span></span> |<span data-ttu-id="275ae-118">Chemin où les processus écrivent l’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="275ae-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="275ae-119">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="275ae-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="275ae-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="275ae-120">StandardInputPath</span></span> |<span data-ttu-id="275ae-121">Flux à partir duquel le processus reçoit l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="275ae-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="275ae-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="275ae-122">StandardOutputPath</span></span> |<span data-ttu-id="275ae-123">Chemin du fichier où les processus écrivent la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="275ae-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="275ae-124">Tout fichier existant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="275ae-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="275ae-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="275ae-125">WorkingDirectory</span></span> |<span data-ttu-id="275ae-126">Emplacement utilisé comme répertoire de travail actuel pour les processus.</span><span class="sxs-lookup"><span data-stu-id="275ae-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="275ae-127">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="275ae-127">Common properties</span></span>

|<span data-ttu-id="275ae-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="275ae-128">Property</span></span> |<span data-ttu-id="275ae-129">Description</span><span class="sxs-lookup"><span data-stu-id="275ae-129">Description</span></span> |
|---|---|
|<span data-ttu-id="275ae-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="275ae-130">DependsOn</span></span> |<span data-ttu-id="275ae-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="275ae-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="275ae-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="275ae-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="275ae-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="275ae-133">Ensure</span></span> |<span data-ttu-id="275ae-134">Spécifie si les processus existent.</span><span class="sxs-lookup"><span data-stu-id="275ae-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="275ae-135">Définissez cette propriété sur **Present** pour faire en sorte que le processus existe.</span><span class="sxs-lookup"><span data-stu-id="275ae-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="275ae-136">Sinon, donnez-lui la valeur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="275ae-136">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="275ae-137">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="275ae-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="275ae-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="275ae-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="275ae-139">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="275ae-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="275ae-140">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="275ae-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="275ae-141">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="275ae-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>