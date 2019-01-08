---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Archive DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047313"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="38d0f-103">Ressource Archive DSC</span><span class="sxs-lookup"><span data-stu-id="38d0f-103">DSC Archive Resource</span></span>

> <span data-ttu-id="38d0f-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="38d0f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="38d0f-105">La ressource Archive de la configuration d’état souhaité (DSC) de Windows PowerShell fournit un mécanisme permettant de décompresser les fichiers d’archive (.zip) à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="38d0f-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="38d0f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38d0f-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="38d0f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="38d0f-107">Properties</span></span>

|  <span data-ttu-id="38d0f-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="38d0f-108">Property</span></span>  |  <span data-ttu-id="38d0f-109">Description</span><span class="sxs-lookup"><span data-stu-id="38d0f-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="38d0f-110">Destination</span><span class="sxs-lookup"><span data-stu-id="38d0f-110">Destination</span></span>| <span data-ttu-id="38d0f-111">Spécifie l’emplacement où le contenu de l’archive doit être extrait.</span><span class="sxs-lookup"><span data-stu-id="38d0f-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="38d0f-112">Path</span><span class="sxs-lookup"><span data-stu-id="38d0f-112">Path</span></span>| <span data-ttu-id="38d0f-113">Spécifie le chemin source du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="38d0f-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="38d0f-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="38d0f-114">__Checksum__</span></span>| <span data-ttu-id="38d0f-115">Définit le type à utiliser pour déterminer si deux fichiers sont identiques.</span><span class="sxs-lookup"><span data-stu-id="38d0f-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="38d0f-116">Si __Checksum__ n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="38d0f-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="38d0f-117">Les valeurs valides sont les suivantes : SHA-1, SHA-256, SHA-512, createdDate, modifiedDate et none (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="38d0f-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="38d0f-118">Si vous spécifiez __Checksum__ sans __Validate__, la configuration échoue.</span><span class="sxs-lookup"><span data-stu-id="38d0f-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="38d0f-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="38d0f-119">Ensure</span></span>| <span data-ttu-id="38d0f-120">Détermine s’il faut vérifier que le contenu de l’archive se trouve à la __Destination__ donnée.</span><span class="sxs-lookup"><span data-stu-id="38d0f-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="38d0f-121">Définissez cette propriété sur __Present__ pour vous assurer que le contenu se trouve à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="38d0f-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="38d0f-122">Définissez la propriété sur __Absent__ pour vous assurer que le contenu ne se trouve pas à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="38d0f-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="38d0f-123">La valeur par défaut est __Present__.</span><span class="sxs-lookup"><span data-stu-id="38d0f-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="38d0f-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="38d0f-124">DependsOn</span></span> | <span data-ttu-id="38d0f-125">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="38d0f-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="38d0f-126">Par exemple, si l’ID du bloc de script de configuration de ressource que vous voulez exécuter en premier est ResourceName et son type est __ResourceType__, la syntaxe de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="38d0f-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="38d0f-127">Validate</span><span class="sxs-lookup"><span data-stu-id="38d0f-127">Validate</span></span>| <span data-ttu-id="38d0f-128">Utilise la propriété Checksum pour déterminer si l’archive correspond à la signature.</span><span class="sxs-lookup"><span data-stu-id="38d0f-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="38d0f-129">Si vous spécifiez Checksum sans Validate, la configuration échoue.</span><span class="sxs-lookup"><span data-stu-id="38d0f-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="38d0f-130">Si vous spécifiez Validate sans Checksum, une somme de contrôle SHA-256 est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="38d0f-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="38d0f-131">Force</span><span class="sxs-lookup"><span data-stu-id="38d0f-131">Force</span></span>| <span data-ttu-id="38d0f-132">Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur.</span><span class="sxs-lookup"><span data-stu-id="38d0f-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="38d0f-133">La propriété Force permet d’ignorer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="38d0f-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="38d0f-134">La valeur par défaut est False.</span><span class="sxs-lookup"><span data-stu-id="38d0f-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="38d0f-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="38d0f-135">Example</span></span>

<span data-ttu-id="38d0f-136">L’exemple suivant montre comment utiliser la ressource Archive pour vous assurer que le contenu d’un fichier d’archive appelé Test.zip existe et qu’il est extrait à une destination donnée.</span><span class="sxs-lookup"><span data-stu-id="38d0f-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```