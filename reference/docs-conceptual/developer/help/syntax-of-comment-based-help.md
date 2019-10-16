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
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367758"
---
# <a name="syntax-of-comment-based-help"></a>Syntaxe de l’aide basée sur les commentaires

Cette section décrit la syntaxe de l’aide basée sur les commentaires.

## <a name="syntax-diagram"></a>Diagramme de syntaxe

 La syntaxe de l’aide basée sur les commentaires est la suivante :

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Description de la syntaxe

 L’aide basée sur les commentaires est écrite sous la forme d’une série de commentaires. Vous pouvez taper un symbole de commentaire (#) avant chaque ligne de commentaires, ou vous pouvez utiliser les symboles « \< # » et « # > » pour créer un bloc de commentaires. Toutes les lignes dans le bloc de commentaires sont interprétées comme des commentaires.

 Chaque section de l’aide basée sur des commentaires est définie par un mot clé et chaque mot clé est précédé d’un point (.). Les mots clés peuvent apparaître dans n’importe quel ordre. Les noms de mots clés ne respectent pas la casse.

 Un bloc de commentaires doit contenir au moins un mot clé d’aide. Certains mots clés, tels que EXAMPLE, peuvent apparaître plusieurs fois dans le même bloc de commentaires. Le contenu de l’aide pour chaque mot clé commence sur la ligne qui suit le mot clé et peut s’étendre sur plusieurs lignes.

 Toutes les lignes d’une rubrique d’aide basée sur des commentaires doivent être contiguës. Si une rubrique d’aide basée sur des commentaires suit un commentaire qui ne fait pas partie de la rubrique d’aide, il doit y avoir au moins une ligne vide entre la dernière ligne de commentaire non-aide et le début de l’aide basée sur les commentaires.

 Par exemple, la rubrique d’aide sur les commentaires suivante contient le. Mot clé Description et sa valeur, qui est une description d’une fonction ou d’un script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```