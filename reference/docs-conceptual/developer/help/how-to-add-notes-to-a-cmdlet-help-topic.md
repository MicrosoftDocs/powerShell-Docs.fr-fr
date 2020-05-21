---
title: Guide pratique pour ajouter des notes à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 1a365a167c245006bb882a542aedb5c43cfc4c96
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557105"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section Remarques à une rubrique d’aide de l’applet de commande® Windows PowerShell. La section Remarques est utilisée pour expliquer des détails qui ne tiennent pas facilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre. Ce contenu peut inclure des commentaires sur le fonctionnement de l’applet de commande avec un fournisseur spécifique, des utilisations uniques, mais importantes, de l’applet de commande ou des moyens d’éviter des conditions d’erreur possibles.

Il n’existe aucune limite quant au nombre de notes que vous pouvez ajouter à une section Remarques. Pour chaque note, ajoutez une paire de \< balises de MAML : alert> au \< nœud MAML : alertSet>. Le contenu de chaque note est ajouté au sein d’un ensemble de \< balises MAML : para>. Utilisez \< MAML vide : para> balises pour l’espacement.

Le code XML suivant montre un \< nœud MAML : alertset> avec deux notes. Notez que chaque note a une \< balise MAML : title> facultative (les titres peuvent être utilisés pour regrouper n’importe quel ensemble de \< balises MAML : Alert>), et que chaque note contient une ligne vide suivant le contenu pour l’espacement.

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
