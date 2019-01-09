---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource File DSC
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047402"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="02337-103">Ressource File DSC</span><span class="sxs-lookup"><span data-stu-id="02337-103">DSC File Resource</span></span>

> <span data-ttu-id="02337-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="02337-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="02337-105">La ressource File dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les fichiers et les dossiers sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="02337-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="02337-106">**Remarque :** Si la propriété **MatchSource** est définie sur **$false** (qui est la valeur par défaut), le contenu à copier est mis en cache la première fois que la configuration est appliquée.</span><span class="sxs-lookup"><span data-stu-id="02337-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="02337-107">Les applications suivantes de la configuration ne recherchent pas les fichiers et/ou dossiers mis à jour dans le chemin spécifié par **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="02337-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="02337-108">Si vous voulez rechercher les mises à jour des fichiers et/ou dossiers dans **SourcePath** chaque fois que la configuration est appliquée, affectez à **MatchSource** la valeur **$true**.</span><span class="sxs-lookup"><span data-stu-id="02337-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="02337-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02337-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="02337-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="02337-110">Properties</span></span>

|  <span data-ttu-id="02337-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="02337-111">Property</span></span>  |  <span data-ttu-id="02337-112">Description</span><span class="sxs-lookup"><span data-stu-id="02337-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="02337-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="02337-113">DestinationPath</span></span>| <span data-ttu-id="02337-114">Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.</span><span class="sxs-lookup"><span data-stu-id="02337-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="02337-115">Attributes</span><span class="sxs-lookup"><span data-stu-id="02337-115">Attributes</span></span>| <span data-ttu-id="02337-116">Spécifie l’état souhaité des attributs du fichier ou du répertoire cible.</span><span class="sxs-lookup"><span data-stu-id="02337-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="02337-117">Checksum</span><span class="sxs-lookup"><span data-stu-id="02337-117">Checksum</span></span>| <span data-ttu-id="02337-118">Spécifie le type de somme de contrôle à utiliser pour déterminer si deux fichiers sont identiques.</span><span class="sxs-lookup"><span data-stu-id="02337-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="02337-119">Si __Checksum__ n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="02337-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="02337-120">Les valeurs valides sont les suivantes : SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="02337-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="02337-121">Contenu</span><span class="sxs-lookup"><span data-stu-id="02337-121">Contents</span></span>| <span data-ttu-id="02337-122">Spécifie le contenu d’un fichier, tel qu’une chaîne spécifique.</span><span class="sxs-lookup"><span data-stu-id="02337-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="02337-123">Credential</span><span class="sxs-lookup"><span data-stu-id="02337-123">Credential</span></span>| <span data-ttu-id="02337-124">Indique les informations d’identification qui sont nécessaires pour accéder aux ressources, telles que des fichiers sources, si ce type d’accès est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="02337-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="02337-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="02337-125">Ensure</span></span>| <span data-ttu-id="02337-126">Indique si le fichier ou le répertoire existe.</span><span class="sxs-lookup"><span data-stu-id="02337-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="02337-127">Définissez cette propriété sur Absent pour vous assurer que le fichier ou le répertoire n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="02337-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="02337-128">Définissez cette propriété sur Present pour vous assurer que le fichier ou le répertoire existe.</span><span class="sxs-lookup"><span data-stu-id="02337-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="02337-129">La valeur par défaut est Present.</span><span class="sxs-lookup"><span data-stu-id="02337-129">The default is "Present".</span></span>|
| <span data-ttu-id="02337-130">Force</span><span class="sxs-lookup"><span data-stu-id="02337-130">Force</span></span>| <span data-ttu-id="02337-131">Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur.</span><span class="sxs-lookup"><span data-stu-id="02337-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="02337-132">La propriété Force permet d’ignorer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="02337-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="02337-133">La valeur par défaut est __$false__.</span><span class="sxs-lookup"><span data-stu-id="02337-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="02337-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="02337-134">Recurse</span></span>| <span data-ttu-id="02337-135">Indique si des sous-répertoires sont inclus.</span><span class="sxs-lookup"><span data-stu-id="02337-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="02337-136">Définissez cette propriété sur __$true__ pour indiquer que vous voulez inclure des sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="02337-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="02337-137">La valeur par défaut est __$false__.</span><span class="sxs-lookup"><span data-stu-id="02337-137">The default is __$false__.</span></span> <span data-ttu-id="02337-138">**Remarque** : Cette propriété est valide uniquement lorsque la propriété de Type est définie sur Directory.</span><span class="sxs-lookup"><span data-stu-id="02337-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="02337-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="02337-139">DependsOn</span></span> | <span data-ttu-id="02337-140">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="02337-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="02337-141">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="02337-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="02337-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="02337-142">SourcePath</span></span>| <span data-ttu-id="02337-143">Indique le chemin à partir duquel copier la ressource de fichier ou de dossier.</span><span class="sxs-lookup"><span data-stu-id="02337-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="02337-144">Type</span><span class="sxs-lookup"><span data-stu-id="02337-144">Type</span></span>| <span data-ttu-id="02337-145">Indique si la ressource actuellement configurée est un répertoire ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="02337-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="02337-146">Définissez cette propriété sur Directory pour indiquer que la ressource est un répertoire.</span><span class="sxs-lookup"><span data-stu-id="02337-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="02337-147">Affectez-lui la valeur File pour indiquer que la ressource est un fichier.</span><span class="sxs-lookup"><span data-stu-id="02337-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="02337-148">La valeur par défaut est File.</span><span class="sxs-lookup"><span data-stu-id="02337-148">The default value is “File”.</span></span>|
| <span data-ttu-id="02337-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="02337-149">MatchSource</span></span>| <span data-ttu-id="02337-150">Si la valeur par défaut __$false__ est définie, tous les fichiers de la source (par exemple, les fichiers A, B et C) sont ajoutés à la destination quand la configuration est appliquée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="02337-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="02337-151">Si un nouveau fichier (D) est ajouté à la source, il n’est pas ajouté à la destination, même si la configuration est de nouveau appliquée plus tard.</span><span class="sxs-lookup"><span data-stu-id="02337-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="02337-152">Si la valeur est __$true__, chaque fois que la configuration est appliquée, les nouveaux fichiers détectés par la suite sur la source (comme le fichier D de cet exemple) seront ajoutés à la destination.</span><span class="sxs-lookup"><span data-stu-id="02337-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="02337-153">La valeur par défaut est **$false**.</span><span class="sxs-lookup"><span data-stu-id="02337-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="02337-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="02337-154">Example</span></span>

<span data-ttu-id="02337-155">L’exemple suivant montre comment utiliser la ressource File pour vérifier qu’un répertoire à l’emplacement `C:\Users\Public\Documents\DSCDemo\DemoSource` sur un ordinateur source (tel que le serveur collecteur) est également présent (ainsi que tous ses sous-répertoires) sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="02337-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="02337-156">Il écrit également un message de confirmation dans le journal une fois terminé, et ajoute une instruction pour garantir que l’opération de vérification des fichiers sera exécutée avant l’opération de journalisation.</span><span class="sxs-lookup"><span data-stu-id="02337-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```