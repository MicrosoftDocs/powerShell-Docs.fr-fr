---
title: Écriture d’un fichier de mise en forme PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361408"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="0a4d1-102">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a4d1-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="0a4d1-103">« L’écriture d’un fichier de mise en forme PowerShell » est destinée aux développeurs de commandes qui écrivent des applets de commande ou des fonctions qui génèrent des objets sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="0a4d1-104">Les fichiers de mise en forme définissent la façon dont PowerShell affiche ces objets sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="0a4d1-105">Cette documentation fournit une vue d’ensemble des fichiers de mise en forme, une explication des concepts que vous devez comprendre lors de l’écriture de ces fichiers, des exemples de code XML utilisé dans ces fichiers et une section de référence pour les éléments XML.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0a4d1-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0a4d1-106">In This Section</span></span>

<span data-ttu-id="0a4d1-107">[Présentation de la mise en forme du fichier](./formatting-file-overview.md) Décrit ce qu’est un fichier de format et les composants généraux d’un fichier de mise en forme, y compris les fonctionnalités communes qui peuvent être définies dans le fichier, les différents types de vues de format qui peuvent être définis pour les objets .NET et un exemple simplifié du code XML utilisé pour définir une table v icher.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="0a4d1-108">[Mise en forme des concepts de fichier](./formatting-file-concepts.md) Contient des informations que vous devrez peut-être connaître lors de la création de vos propres fichiers de mise en forme, tels que les différents types d’affichages que vous pouvez définir et les composants spéciaux de ces vues.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="0a4d1-109">[Exemples de mise en forme de fichiers](./examples-of-formatting-files.md) Fournit des exemples XML de plusieurs fichiers de mise en forme, y compris des exemples de vue de table, une vue liste et une vue étendue, ainsi que des exemples qui montrent comment définir des fonctionnalités telles que les jeux de sélection, les conditions de sélection et les contrôles communs.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="0a4d1-110">[Mettre en forme la référence XML](./format-schema-xml-reference.md) Contient des rubriques de référence pour les éléments XML utilisés dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0a4d1-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
