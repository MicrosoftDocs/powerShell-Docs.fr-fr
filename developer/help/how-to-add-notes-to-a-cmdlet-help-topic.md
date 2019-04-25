---
title: Comment ajouter des remarques à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083414"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section de Notes à une rubrique d’aide Windows PowerShell® applet de commande. La section Notes de publication est utilisée pour expliquer les détails qui ne tiennent pas facilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre. Ce contenu peut inclure des commentaires sur le fonctionne de l’applet de commande avec un fournisseur spécifique, certaines utilisations uniques, mais il est importantes, de l’applet de commande ou les moyens d’éviter les conditions d’erreur possibles.

Il n’existe aucune limite au nombre de notes que vous pouvez ajouter à la section Notes. Pour chaque note, ajoutez une paire de \<maml:alert > balises à la \<maml:alertset > nœud. Le contenu de chaque note est ajouté au sein d’un ensemble de \<maml : para > balises. Utilisez vide \<maml : para > balises pour l’espacement.

Le code XML suivant montre un \<maml:alertset > nœud avec deux notes. Notez que chaque note a facultative \<maml : Title > balise (titres peuvent être utilisées pour regrouper un ensemble de \<maml:alert > balises), et que chaque note a une ligne vierge suivant le contenu pour l’espacement.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



