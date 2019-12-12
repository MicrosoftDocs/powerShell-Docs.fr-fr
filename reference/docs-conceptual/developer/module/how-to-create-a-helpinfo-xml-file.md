---
title: Comment créer un fichier XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367318"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="ec659-102">Guide pratique pour créer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ec659-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="ec659-103">Les rubriques de cette section expliquent comment créer et remplir un fichier d’informations d’aide, communément appelé « fichier XML HelpInfo », pour la fonctionnalité d’aide actualisable de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec659-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="ec659-104">Vue d’ensemble du fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ec659-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="ec659-105">Le fichier XML HelpInfo est la principale source d’informations sur l’aide actualisable du module.</span><span class="sxs-lookup"><span data-stu-id="ec659-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="ec659-106">Il inclut l’emplacement des fichiers d’aide pour les modules, les cultures d’interface utilisateur prises en charge et les numéros de version que l’aide actualisable utilise pour déterminer si l’utilisateur dispose des fichiers d’aide les plus récents.</span><span class="sxs-lookup"><span data-stu-id="ec659-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="ec659-107">Chaque module a un seul fichier XML HelpInfo, même si le module inclut plusieurs fichiers d’aide pour plusieurs cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec659-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="ec659-108">L’auteur du module crée le fichier XML HelpInfo et le place dans l’emplacement Internet spécifié par la clé **HelpInfoUri** dans le manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="ec659-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="ec659-109">Lorsque les fichiers d’aide du module sont mis à jour et téléchargés, le créateur du module met à jour le fichier XML HelpInfo et remplace le fichier XML HelpInfo d’origine par la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="ec659-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="ec659-110">Il est essentiel que le fichier XML HelpInfo soit soigneusement géré.</span><span class="sxs-lookup"><span data-stu-id="ec659-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="ec659-111">Si vous téléchargez de nouveaux fichiers, mais oubliez d’incrémenter les numéros de version, l’aide actualisable ne téléchargera pas les nouveaux fichiers sur les ordinateurs des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ec659-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="ec659-112">Si vous ajoutez des fichiers d’aide pour une nouvelle culture d’interface utilisateur, mais que vous ne mettez pas à jour le fichier XML HelpInfo ou que vous le placez à l’emplacement approprié, l’aide actualisable ne télécharge pas les nouveaux fichiers.</span><span class="sxs-lookup"><span data-stu-id="ec659-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ec659-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ec659-113">In this section</span></span>

<span data-ttu-id="ec659-114">Cette section comprend les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="ec659-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="ec659-115">Schéma XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ec659-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="ec659-116">Exemple de fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ec659-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="ec659-117">Comment nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ec659-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="ec659-118">Définition des numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ec659-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="ec659-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec659-119">See Also</span></span>

[<span data-ttu-id="ec659-120">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="ec659-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)