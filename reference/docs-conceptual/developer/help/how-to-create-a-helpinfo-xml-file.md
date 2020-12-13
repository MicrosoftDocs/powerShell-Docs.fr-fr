---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour créer un fichier XML HelpInfo
description: Guide pratique pour créer un fichier XML HelpInfo
ms.openlocfilehash: d5a24306aa6488fdefad0b7b1ea9e2978a93a7b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647713"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="9429b-103">Guide pratique pour créer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9429b-103">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="9429b-104">Les rubriques de cette section expliquent comment créer et remplir un fichier d’informations d’aide, communément appelé « fichier XML HelpInfo », pour la fonctionnalité d’aide actualisable PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9429b-104">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="9429b-105">Vue d’ensemble du fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9429b-105">HelpInfo XML File Overview</span></span>

<span data-ttu-id="9429b-106">Le fichier XML HelpInfo est la principale source d’informations sur l’aide actualisable du module.</span><span class="sxs-lookup"><span data-stu-id="9429b-106">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="9429b-107">Il inclut l’emplacement des fichiers d’aide pour les modules, les cultures d’interface utilisateur prises en charge et les numéros de version que l’aide actualisable utilise pour déterminer si l’utilisateur dispose des fichiers d’aide les plus récents.</span><span class="sxs-lookup"><span data-stu-id="9429b-107">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="9429b-108">Chaque module a un seul fichier XML HelpInfo, même si le module inclut plusieurs fichiers d’aide pour plusieurs cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9429b-108">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="9429b-109">L’auteur du module crée le fichier XML HelpInfo et le place dans l’emplacement Internet spécifié par la clé **HelpInfoUri** dans le manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="9429b-109">The module author creates the HelpInfo XML file and places it in the internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="9429b-110">Lorsque les fichiers d’aide du module sont mis à jour et téléchargés, le créateur du module met à jour le fichier XML HelpInfo et remplace le fichier XML HelpInfo d’origine par la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="9429b-110">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="9429b-111">Il est essentiel que le fichier XML HelpInfo soit soigneusement géré.</span><span class="sxs-lookup"><span data-stu-id="9429b-111">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="9429b-112">Si vous téléchargez de nouveaux fichiers, mais oubliez d’incrémenter les numéros de version, l’aide actualisable ne téléchargera pas les nouveaux fichiers sur les ordinateurs des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9429b-112">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="9429b-113">Si vous ajoutez des fichiers d’aide pour une nouvelle culture d’interface utilisateur, mais que vous ne mettez pas à jour le fichier XML HelpInfo ou que vous le placez à l’emplacement approprié, l’aide actualisable ne télécharge pas les nouveaux fichiers.</span><span class="sxs-lookup"><span data-stu-id="9429b-113">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9429b-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9429b-114">In this section</span></span>

<span data-ttu-id="9429b-115">Cette section comprend les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="9429b-115">This section includes the following topics.</span></span>

- [<span data-ttu-id="9429b-116">Schéma XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9429b-116">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="9429b-117">Exemple de fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9429b-117">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="9429b-118">Guide pratique pour nommer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9429b-118">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="9429b-119">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9429b-119">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="9429b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9429b-120">See Also</span></span>

[<span data-ttu-id="9429b-121">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="9429b-121">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
