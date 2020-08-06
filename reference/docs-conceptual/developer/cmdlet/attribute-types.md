---
title: Types d’attributs | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 96fdd38ba10eb748ab0762f0c910463dd472494d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782376"
---
# <a name="attribute-types"></a>Types d’attributs

Les attributs d’applet de commande peuvent être regroupés par fonctionnalité.
Les sections suivantes décrivent les attributs disponibles et décrivent ce que fait le runtime lorsque l’attribut est appelé.

## <a name="cmdlet-attributes"></a>Attributs des applets de commande

### <a name="cmdlet"></a>Applet de commande

Identifie une classe .NET Framework en tant qu’applet de commande.
Il s’agit de l’attribut de base requis.
Pour plus d’informations, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.

## <a name="parameter-attributes"></a>Attributs de paramètre

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
