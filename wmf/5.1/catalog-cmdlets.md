---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
title: Applets de commande de catalogue
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="65432-103">Applets de commande de catalogue</span><span class="sxs-lookup"><span data-stu-id="65432-103">Catalog Cmdlets</span></span>  

<span data-ttu-id="65432-104">Nous avons ajouté deux nouvelles applets de commande au module [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) pour générer et valider des fichiers catalogue Windows.</span><span class="sxs-lookup"><span data-stu-id="65432-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>  

## <a name="new-filecatalog"></a><span data-ttu-id="65432-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="65432-105">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="65432-106">`New-FileCatalog` crée un fichier catalogue Windows pour un ensemble de dossiers et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="65432-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="65432-107">Un fichier catalogue contient des hachages pour tous les fichiers dans les chemins spécifiés.</span><span class="sxs-lookup"><span data-stu-id="65432-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="65432-108">Les utilisateurs peuvent distribuer l’ensemble des dossiers ainsi que le fichier catalogue correspondant qui représente ces dossiers.</span><span class="sxs-lookup"><span data-stu-id="65432-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="65432-109">Un fichier catalogue peut être utilisé par le destinataire du contenu pour valider si des modifications ont été apportées aux dossiers après la création du catalogue.</span><span class="sxs-lookup"><span data-stu-id="65432-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="65432-110">Nous prenons en charge la création des versions de catalogues 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="65432-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="65432-111">La version 1 utilise l’algorithme de hachage SHA1 pour créer des fichiers à hacher et la version 2 utilise SHA256.</span><span class="sxs-lookup"><span data-stu-id="65432-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="65432-112">La version de catalogue 2 n’est pas prise en charge sur *Windows Server 2008 R2* ni *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="65432-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="65432-113">Il est recommandé d’utiliser la version de catalogue 2 si vous utilisez les plateformes *Windows 8*, *Windows Server 2012* et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="65432-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>  

<span data-ttu-id="65432-114">Pour utiliser cette commande sur un module existant, spécifiez les variables CatalogFilePath et Path de façon à ce qu’elles correspondent à l’emplacement du manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="65432-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="65432-115">Dans l’exemple ci-dessous, le manifeste du module se trouve dans C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="65432-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span> 

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="65432-116">Le fichier catalogue est ainsi créé.</span><span class="sxs-lookup"><span data-stu-id="65432-116">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="65432-117">Pour vérifier l’intégrité d’un fichier catalogue (Pester.cat dans l’exemple ci-dessus), il doit être signé à l’aide de l’applet de commande [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).</span><span class="sxs-lookup"><span data-stu-id="65432-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


## <a name="test-filecatalog"></a><span data-ttu-id="65432-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="65432-118">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="65432-119">`Test-FileCatalog` valide le catalogue représentant un ensemble de dossiers.</span><span class="sxs-lookup"><span data-stu-id="65432-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="65432-120">Cette applet de commande compare les hachages de tous les fichiers et leurs chemins relatifs qui figurent dans le fichier catalogue à ceux enregistrés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="65432-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="65432-121">Si elle détecte une incompatibilité entre les hachages de fichier et les chemins, elle retourne le statut `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="65432-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span> <span data-ttu-id="65432-122">Les utilisateurs peuvent récupérer toutes ces informations à l’aide de l’indicateur `Detailed`.</span><span class="sxs-lookup"><span data-stu-id="65432-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="65432-123">Le statut de signature du catalogue est affiché dans le champ `Signature`, ce qui revient à appeler l’applet de commande [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) sur le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="65432-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="65432-124">Les utilisateurs peuvent également ignorer des fichiers pendant la validation à l’aide du paramètre `FilesToSkip`.</span><span class="sxs-lookup"><span data-stu-id="65432-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span> 

