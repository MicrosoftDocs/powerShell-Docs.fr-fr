---
title: PropertyName, élément de WideItem pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7728f960a67faa99eaafb4a4934674e119b8af27
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780472"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName, élément pour WideItem pour WideControl (Format)

Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem élément (format) NomPropriété, élément pour WideItem (format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans la vue étendue.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

Cet exemple montre une vue étendue qui affiche la valeur de la propriété ProcessName de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
