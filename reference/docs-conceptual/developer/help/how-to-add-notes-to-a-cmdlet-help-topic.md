---
ms.date: 10/20/2020
ms.topic: reference
title: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
ms.openlocfilehash: 61363c26ab0172277d1332ed1e9de080d8da200c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659559"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande

Cette section explique comment ajouter une section **NOTES** à la rubrique d’aide d’une cmdlet PowerShell. La section **NOTES** permet de donner des détails qui entrent difficilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre. Ce contenu peut comporter des commentaires sur le fonctionnement de la cmdlet avec un fournisseur spécifique, des utilisations uniques mais importantes de la cmdlet ou encore des moyens d’éviter des situations d’erreur potentielles.

La section **NOTES** est définie à l’aide d’un seul nœud `<maml:alertset>`. Le nombre de notes que l’on peut ajouter à une section NOTES n’est pas limité. Pour chaque note, ajoutez une paire de balises `<maml:alert>` au nœud `<maml:alertset>`. Le contenu de chaque note est ajouté au sein d’un ensemble de balises `<maml:para>`. Utilisez des balises `<maml:para>` vides pour l’espacement.

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
