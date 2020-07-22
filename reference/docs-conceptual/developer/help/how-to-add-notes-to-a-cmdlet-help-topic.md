---
title: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893405"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section **Remarques** à une rubrique d’aide sur une applet de commande PowerShell. La section **Remarques** est utilisée pour expliquer des détails qui ne tiennent pas facilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre. Ce contenu peut inclure des commentaires sur le fonctionnement de l’applet de commande avec un fournisseur spécifique, des utilisations uniques, mais importantes, de l’applet de commande ou des moyens d’éviter des conditions d’erreur possibles.

Il n’existe aucune limite quant au nombre de notes que vous pouvez ajouter à une section Remarques. Pour chaque note, ajoutez une paire de `<maml:alert>` balises au `<maml:alertset>` nœud. Le contenu de chaque note est ajouté dans un ensemble de `<maml:para>` balises. Utilisez `<maml:para>` des balises vides pour l’espacement.

Le code XML suivant montre un `<maml:alertset>` nœud avec deux notes. Notez que chaque note a une `<maml:title>` balise facultative (les titres peuvent être utilisés pour regrouper n’importe quel ensemble de `<maml:alert>` balises), et que chaque note contient une ligne vide qui suit le contenu pour l’espacement.

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
