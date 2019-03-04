---
title: Écriture d’un fichier de mise en forme de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857045"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="67fd1-102">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="67fd1-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="67fd1-103">« Écriture d’un fichier de mise en forme de PowerShell » est pour les développeurs de commande qui écrivent des applets de commande ou des fonctions que les objets à la ligne de commande de sortie.</span><span class="sxs-lookup"><span data-stu-id="67fd1-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="67fd1-104">Fichiers de mise en forme définissent comment PowerShell affiche ces objets à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="67fd1-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="67fd1-105">Cette documentation fournit une vue d’ensemble de la mise en forme de fichiers, une explication des concepts que vous devez connaître lors de l’écriture de ces fichiers, les exemples de code XML utilisé dans ces fichiers et une section de référence pour les éléments XML.</span><span class="sxs-lookup"><span data-stu-id="67fd1-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="67fd1-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="67fd1-106">In This Section</span></span>

<span data-ttu-id="67fd1-107">[Vue d’ensemble du fichier de mise en forme](./formatting-file-overview.md) décrit quelles un fichier de format est et les composants généraux d’un fichier de mise en forme, y compris les fonctionnalités courantes qui peuvent être définies dans le fichier, les différents types de vues de format qui peuvent être définis pour les objets .NET et un exemple simplifié du XML utilisé pour définir une vue de table.</span><span class="sxs-lookup"><span data-stu-id="67fd1-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="67fd1-108">[Concepts liés au fichier de mise en forme](./formatting-file-concepts.md) inclut des informations que vous devrez peut-être savoir quand créer votre propre mise en forme de fichiers, tels que les différents types de vues que vous pouvez définir et des composants particuliers de ces vues.</span><span class="sxs-lookup"><span data-stu-id="67fd1-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="67fd1-109">[Exemples de fichiers de mise en forme](./examples-of-formatting-files.md) exemples XML fournit plusieurs fichiers de mise en forme, y compris des exemples de vue d’une table, une vue de liste et un affichage plus large, ainsi que des exemples qui montrent comment définir des fonctionnalités telles que des jeux de sélection, les conditions de sélection, et contrôles communs.</span><span class="sxs-lookup"><span data-stu-id="67fd1-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="67fd1-110">[Format de référence XML](./format-schema-xml-reference.md) contient des rubriques de référence pour les éléments XML utilisés dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="67fd1-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
