---
title: Élément PropertyName pour WideItem pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064643"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName, élément pour WideItem pour WideControl (Format)

Spécifie la propriété de l’objet dont la valeur est affichée dans l’affichage plus large.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) élément WideEntries (Format) WideEntry, élément (Format) WideItem, élément (Format) PropertyName élément de configuration pour WideItem (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans l’affichage plus large.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un affichage plus large qui affiche la valeur de la propriété ProcessName de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Voir aussi

[Élément WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
