---
title: Types d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364578"
---
# <a name="attribute-types"></a>Types d’attributs

Les attributs d’applet de commande peuvent être regroupés par fonctionnalité.
Les sections suivantes décrivent les attributs disponibles et décrivent ce que fait le runtime lorsque l’attribut est appelé.

## <a name="cmdlet-attributes"></a>Attributs des applets de commande

### <a name="cmdlet"></a>Applet de commande

Identifie une classe .NET Framework en tant qu’applet de commande.
Il s’agit de l’attribut de base requis.
Pour plus d’informations, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.

## <a name="parameter-attributes"></a>Attributs de paramètres

### <a name="parameter"></a>Paramètre

Identifie une propriété publique dans la classe d’applet de commande en tant que paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Spécifie un ou plusieurs alias pour un paramètre.
Pour plus d’informations, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Attributs de validation d’argument

### <a name="validatecount"></a>ValidateCount

Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Spécifie un nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Spécifie un modèle d’expression régulière auquel l’argument du paramètre de l’applet de commande doit correspondre.
Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Spécifie les valeurs minimale et maximale d’un argument de paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Spécifie un ensemble de valeurs valides pour l’argument du paramètre de l’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
