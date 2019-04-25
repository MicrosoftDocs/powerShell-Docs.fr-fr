---
title: Syntaxe de commentaire aide | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083210"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="3c4e7-102">Syntaxe de l’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="3c4e7-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="3c4e7-103">Cette section décrit la syntaxe de l’aide en fonction du commentaire.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="3c4e7-104">Diagramme de syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c4e7-104">Syntax Diagram</span></span>

 <span data-ttu-id="3c4e7-105">La syntaxe de l’aide basée sur le commentaire est comme suit :</span><span class="sxs-lookup"><span data-stu-id="3c4e7-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="3c4e7-106">Description de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c4e7-106">Syntax Description</span></span>

 <span data-ttu-id="3c4e7-107">Aide basée sur le commentaire est écrit en tant que série de commentaires.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="3c4e7-108">Vous pouvez taper un symbole de commentaire (#) devant chaque ligne de commentaires, ou vous pouvez utiliser le «\<# » et « #> « symboles pour créer un bloc de commentaire.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="3c4e7-109">Toutes les lignes dans le bloc de commentaire sont interprétés en tant que commentaires.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="3c4e7-110">Chaque section de l’aide basée sur le commentaire est définie par un mot clé et chaque mot clé est précédé par un point (.).</span><span class="sxs-lookup"><span data-stu-id="3c4e7-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="3c4e7-111">Les mots clés peuvent apparaître dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-111">The keywords can appear in any order.</span></span> <span data-ttu-id="3c4e7-112">Les noms des mots clés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="3c4e7-113">Un bloc de commentaire doit contenir au moins un mot clé d’aide.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="3c4e7-114">Certains des mots clés, comme dans l’exemple, peuvent apparaître plusieurs fois dans le même bloc de commentaire.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="3c4e7-115">Le contenu d’aide pour chaque mot clé commence sur la ligne après le mot clé et peut couvrir plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="3c4e7-116">Toutes les lignes dans une rubrique d’aide en fonction des commentaires doivent être contiguës.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="3c4e7-117">Si une rubrique d’aide en fonction du commentaire suit un commentaire qui ne fait pas partie de la rubrique d’aide, il doit être d’au moins une ligne vide entre la dernière ligne de commentaire de non-Help et le début de l’aide en fonction du commentaire.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="3c4e7-118">Par exemple, la rubrique d’aide en fonction du commentaire suivante contient la. Mot clé de description et sa valeur, qui est une description d’une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="3c4e7-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```