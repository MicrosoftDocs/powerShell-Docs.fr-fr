---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxArchive dans DSC pour Linux
ms.openlocfilehash: 77b52ad68344ba791501baeb585a5001cc97a126
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953326"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="978e8-103">Ressource nxArchive dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="978e8-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="978e8-104">La ressource **nxArchive** de la configuration d’état souhaité (DSC) de Windows PowerShell fournit un mécanisme permettant de décompresser les fichiers d’archive (.zip) à un emplacement spécifique d’un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="978e8-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="978e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="978e8-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="978e8-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="978e8-106">Properties</span></span>

|<span data-ttu-id="978e8-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="978e8-107">Property</span></span> |<span data-ttu-id="978e8-108">Description</span><span class="sxs-lookup"><span data-stu-id="978e8-108">Description</span></span> |
|---|---|
|<span data-ttu-id="978e8-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="978e8-109">SourcePath</span></span> |<span data-ttu-id="978e8-110">Spécifie le chemin source du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="978e8-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="978e8-111">Ce fichier doit être au format .tar, .zip ou .tar.gz.</span><span class="sxs-lookup"><span data-stu-id="978e8-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="978e8-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="978e8-112">DestinationPath</span></span> |<span data-ttu-id="978e8-113">Spécifie l’emplacement où le contenu de l’archive doit être extrait.</span><span class="sxs-lookup"><span data-stu-id="978e8-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="978e8-114">Somme de contrôle</span><span class="sxs-lookup"><span data-stu-id="978e8-114">Checksum</span></span> |<span data-ttu-id="978e8-115">Définit le type à utiliser pour déterminer si l’archive source a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="978e8-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="978e8-116">Les valeurs sont **ctime**, **mtime** ou **md5**.</span><span class="sxs-lookup"><span data-stu-id="978e8-116">Values are: **ctime**, **mtime**, or **md5**.</span></span> <span data-ttu-id="978e8-117">La valeur par défaut est **md5**.</span><span class="sxs-lookup"><span data-stu-id="978e8-117">The default value is **md5**.</span></span> |
|<span data-ttu-id="978e8-118">Force</span><span class="sxs-lookup"><span data-stu-id="978e8-118">Force</span></span> |<span data-ttu-id="978e8-119">Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur.</span><span class="sxs-lookup"><span data-stu-id="978e8-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="978e8-120">La propriété **Force** permet d’ignorer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="978e8-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="978e8-121">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="978e8-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="978e8-122">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="978e8-122">Common properties</span></span>

|<span data-ttu-id="978e8-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="978e8-123">Property</span></span> |<span data-ttu-id="978e8-124">Description</span><span class="sxs-lookup"><span data-stu-id="978e8-124">Description</span></span> |
|---|---|
|<span data-ttu-id="978e8-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="978e8-125">DependsOn</span></span> |<span data-ttu-id="978e8-126">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="978e8-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="978e8-127">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="978e8-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="978e8-128">Ensure</span><span class="sxs-lookup"><span data-stu-id="978e8-128">Ensure</span></span> |<span data-ttu-id="978e8-129">Détermine s’il faut vérifier que le contenu de l’archive se trouve à la **Destination** donnée.</span><span class="sxs-lookup"><span data-stu-id="978e8-129">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="978e8-130">Définissez cette propriété sur **Present** pour vous assurer que le contenu se trouve à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="978e8-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="978e8-131">Définissez la propriété sur **Absent** pour vous assurer que le contenu ne se trouve pas à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="978e8-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="978e8-132">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="978e8-132">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="978e8-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="978e8-133">Example</span></span>

<span data-ttu-id="978e8-134">L’exemple suivant montre comment utiliser la ressource **nxArchive** pour vous assurer que le contenu d’un fichier d’archive appelé `website.tar` existe et qu’il est extrait à une destination donnée.</span><span class="sxs-lookup"><span data-stu-id="978e8-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```