---
title: Comment créer un fichier de mise en forme (. format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363618"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="cc7f0-102">Guide pratique pour créer un fichier de mise en forme (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="cc7f0-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="cc7f0-103">Cette rubrique explique comment créer un fichier de mise en forme (. format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="cc7f0-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="cc7f0-104">Vous pouvez également créer un fichier de mise en forme en effectuant une copie de l’un des fichiers fournis par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="cc7f0-105">Si vous effectuez une copie d’un fichier existant, supprimez la signature numérique existante et ajoutez votre propre signature au nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="cc7f0-106">Pour créer un fichier. format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="cc7f0-107">Créez un fichier texte (. txt) à l’aide d’un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="cc7f0-108">Copiez les lignes suivantes dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="cc7f0-109">Les balises \<Configuration > \</Configuration > définissent le nœud `Configuration` racine.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="cc7f0-110">Toutes les balises XML supplémentaires seront incluses dans ce nœud.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="cc7f0-111">Les <ViewDefinitions></ViewDefinitions> balises définissent le nœud `ViewDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="cc7f0-112">Tous les affichages sont définis dans ce nœud.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="cc7f0-113">Enregistrez le fichier dans le dossier d’installation de Windows PowerShell, dans le dossier de votre module ou dans un sous-dossier du dossier du module.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="cc7f0-114">Lorsque vous enregistrez le fichier, utilisez le format de nom suivant : `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="cc7f0-115">La mise en forme des fichiers doit utiliser l’extension `.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="cc7f0-116">Vous êtes maintenant prêt à ajouter des vues au fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="cc7f0-117">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="cc7f0-118">Vous pouvez ajouter une vue unique pour chaque objet, plusieurs vues pour le même objet ou une vue unique utilisée par plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="cc7f0-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc7f0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc7f0-119">See Also</span></span>

[<span data-ttu-id="cc7f0-120">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc7f0-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
