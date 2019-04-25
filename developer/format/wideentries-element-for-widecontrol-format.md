---
title: Élément WideEntries pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083686"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries, élément pour WideControl (Format)

Fournit les définitions de l’affichage plus large. L’affichage large doit spécifier une ou plusieurs définitions.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) WideEntries élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `WideEntries` élément. Au moins un élément enfant doit être spécifié.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de l’affichage plus large.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideControl (Format)](./widecontrol-element-format.md)|Définit un (valeur unique) à l’échelle du format de liste pour la vue.|

## <a name="remarks"></a>Remarques

Un affichage plus large est un format de liste qui affiche une valeur de propriété unique ou une valeur de script pour chaque objet. Pour plus d’informations sur les composants d’un affichage plus large, consultez [les composants de vue large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideEntries` élément qui définit un seul `WideEntry` élément. Le `WideEntry` élément contienne un seul `WideItem` élément qui définit quelle valeur de propriété ou un script s’affiche dans la vue.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Élément WideControl (Format)](./widecontrol-element-format.md)

[Élément WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
