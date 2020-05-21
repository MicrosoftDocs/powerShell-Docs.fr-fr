---
title: Syntaxe de l’aide basée sur les commentaires | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: da74c674c704794d8648dcdf9ba0a1617decba9b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560608"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="eedfe-102">Syntaxe de l’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="eedfe-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="eedfe-103">Cette section décrit la syntaxe de l’aide basée sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="eedfe-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="eedfe-104">Diagramme de syntaxe</span><span class="sxs-lookup"><span data-stu-id="eedfe-104">Syntax Diagram</span></span>

 <span data-ttu-id="eedfe-105">La syntaxe de l’aide basée sur les commentaires est la suivante :</span><span class="sxs-lookup"><span data-stu-id="eedfe-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="eedfe-106">Description de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="eedfe-106">Syntax Description</span></span>

 <span data-ttu-id="eedfe-107">L’aide basée sur les commentaires est écrite sous la forme d’une série de commentaires.</span><span class="sxs-lookup"><span data-stu-id="eedfe-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="eedfe-108">Vous pouvez taper un symbole de commentaire (#) avant chaque ligne de commentaires, ou vous pouvez utiliser les \< symboles « # » et « # > » pour créer un bloc de commentaires.</span><span class="sxs-lookup"><span data-stu-id="eedfe-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="eedfe-109">Toutes les lignes dans le bloc de commentaires sont interprétées comme des commentaires.</span><span class="sxs-lookup"><span data-stu-id="eedfe-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="eedfe-110">Chaque section de l’aide basée sur des commentaires est définie par un mot clé et chaque mot clé est précédé d’un point (.).</span><span class="sxs-lookup"><span data-stu-id="eedfe-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="eedfe-111">Les mots clés peuvent apparaître dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="eedfe-111">The keywords can appear in any order.</span></span> <span data-ttu-id="eedfe-112">Les noms de mots clés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="eedfe-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="eedfe-113">Un bloc de commentaires doit contenir au moins un mot clé d’aide.</span><span class="sxs-lookup"><span data-stu-id="eedfe-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="eedfe-114">Certains mots clés, tels que EXAMPLE, peuvent apparaître plusieurs fois dans le même bloc de commentaires.</span><span class="sxs-lookup"><span data-stu-id="eedfe-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="eedfe-115">Le contenu de l’aide pour chaque mot clé commence sur la ligne qui suit le mot clé et peut s’étendre sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="eedfe-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="eedfe-116">Toutes les lignes d’une rubrique d’aide basée sur des commentaires doivent être contiguës.</span><span class="sxs-lookup"><span data-stu-id="eedfe-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="eedfe-117">Si une rubrique d’aide basée sur des commentaires suit un commentaire qui ne fait pas partie de la rubrique d’aide, il doit y avoir au moins une ligne vide entre la dernière ligne de commentaire non-aide et le début de l’aide basée sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="eedfe-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="eedfe-118">Par exemple, la rubrique d’aide sur les commentaires suivante contient le. Mot clé Description et sa valeur, qui est une description d’une fonction ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="eedfe-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
