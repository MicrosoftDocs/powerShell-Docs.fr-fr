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
# <a name="syntax-of-comment-based-help"></a>Syntaxe de l’aide basée sur les commentaires

Cette section décrit la syntaxe de l’aide en fonction du commentaire.

## <a name="syntax-diagram"></a>Diagramme de syntaxe

 La syntaxe de l’aide basée sur le commentaire est comme suit :

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

 Aide basée sur le commentaire est écrit en tant que série de commentaires. Vous pouvez taper un symbole de commentaire (#) devant chaque ligne de commentaires, ou vous pouvez utiliser le «\<# » et « #> « symboles pour créer un bloc de commentaire. Toutes les lignes dans le bloc de commentaire sont interprétés en tant que commentaires.

 Chaque section de l’aide basée sur le commentaire est définie par un mot clé et chaque mot clé est précédé par un point (.). Les mots clés peuvent apparaître dans n’importe quel ordre. Les noms des mots clés ne respectent pas la casse.

 Un bloc de commentaire doit contenir au moins un mot clé d’aide. Certains des mots clés, comme dans l’exemple, peuvent apparaître plusieurs fois dans le même bloc de commentaire. Le contenu d’aide pour chaque mot clé commence sur la ligne après le mot clé et peut couvrir plusieurs lignes.

 Toutes les lignes dans une rubrique d’aide en fonction des commentaires doivent être contiguës. Si une rubrique d’aide en fonction du commentaire suit un commentaire qui ne fait pas partie de la rubrique d’aide, il doit être d’au moins une ligne vide entre la dernière ligne de commentaire de non-Help et le début de l’aide en fonction du commentaire.

 Par exemple, la rubrique d’aide en fonction du commentaire suivante contient la. Mot clé de description et sa valeur, qui est une description d’une fonction ou un script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```