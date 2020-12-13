---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour créer un fichier de mise en forme (.format.ps1xml)
description: Guide pratique pour créer un fichier de mise en forme (.format.ps1xml)
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652000"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="6665f-103">Guide pratique pour créer un fichier de mise en forme (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="6665f-103">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="6665f-104">Cette rubrique explique comment créer un fichier de mise en forme (.format.ps1XML).</span><span class="sxs-lookup"><span data-stu-id="6665f-104">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="6665f-105">Vous pouvez également créer un fichier de mise en forme en effectuant une copie de l’un des fichiers fournis par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6665f-105">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="6665f-106">Si vous effectuez une copie d’un fichier existant, supprimez la signature numérique existante et ajoutez votre propre signature au nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="6665f-106">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="6665f-107">Pour créer un fichier .format.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="6665f-107">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="6665f-108">Créez un fichier texte (. txt) à l’aide d’un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="6665f-108">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="6665f-109">Copiez les lignes suivantes dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="6665f-109">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="6665f-110">Les `<Configuration></Configuration>` balises définissent le `Configuration` nœud racine.</span><span class="sxs-lookup"><span data-stu-id="6665f-110">The `<Configuration></Configuration>` tags define the root `Configuration` node.</span></span> <span data-ttu-id="6665f-111">Toutes les balises XML supplémentaires seront incluses dans ce nœud.</span><span class="sxs-lookup"><span data-stu-id="6665f-111">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="6665f-112">Les `<ViewDefinitions></ViewDefinitions>` balises définissent le `ViewDefinitions` nœud.</span><span class="sxs-lookup"><span data-stu-id="6665f-112">The `<ViewDefinitions></ViewDefinitions>` tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="6665f-113">Tous les affichages sont définis dans ce nœud.</span><span class="sxs-lookup"><span data-stu-id="6665f-113">All views are defined within this node.</span></span>

3. <span data-ttu-id="6665f-114">Enregistrez le fichier dans le dossier d’installation de Windows PowerShell, dans le dossier de votre module ou dans un sous-dossier du dossier du module.</span><span class="sxs-lookup"><span data-stu-id="6665f-114">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="6665f-115">Lorsque vous enregistrez le fichier, utilisez le format de nom suivant :  `MyFile.format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="6665f-115">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="6665f-116">La mise en forme des fichiers doit utiliser l' `.format.ps1xml` extension.</span><span class="sxs-lookup"><span data-stu-id="6665f-116">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="6665f-117">Vous êtes maintenant prêt à ajouter des vues au fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="6665f-117">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="6665f-118">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="6665f-118">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="6665f-119">Vous pouvez ajouter une vue unique pour chaque objet, plusieurs vues pour le même objet ou une vue unique utilisée par plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="6665f-119">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="6665f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6665f-120">See Also</span></span>

[<span data-ttu-id="6665f-121">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6665f-121">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
