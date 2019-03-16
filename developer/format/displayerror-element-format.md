---
title: Élément DisplayError (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056479"
---
# <a name="displayerror-element-format"></a>DisplayError, élément (Format)

Spécifie que la chaîne #ERR est affichée lorsqu’une erreur se produit à afficher un élément de données.

Configuration élément (Format) DefaultSettings (Format) DisplayError élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `DisplayError` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément DefaultSettings (Format)](./defaultsettings-element-format.md)|Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|

## <a name="remarks"></a>Remarques

Par défaut, lorsqu’une erreur se produit en essayant d’afficher un élément de données, l’emplacement des données est vide. Lorsque cet élément est défini sur true, la chaîne #ERR s’affichera.

## <a name="see-also"></a>Voir aussi

[Élément DefaultSettings (Format)](./defaultsettings-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
