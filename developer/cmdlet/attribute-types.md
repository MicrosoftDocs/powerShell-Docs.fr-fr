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
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863805"
---
# <a name="attribute-types"></a>Types d’attributs

Attributs de l’applet de commande peuvent être regroupées par fonctionnalité.
Les sections suivantes décrivent les attributs disponibles et décrivent ce que fait le runtime lorsque l’attribut est appelé.

## <a name="cmdlet-attributes"></a>Attributs des applets de commande

### <a name="cmdlet"></a>Applet de commande

Identifie une classe .NET Framework comme une applet de commande.
Il s’agit de l’attribut de base requis.
Pour plus d’informations, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Attributs de paramètre

### <a name="parameter"></a>Paramètre

Identifie une propriété publique dans la classe de l’applet de commande comme un paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Spécifie un ou plusieurs alias pour un paramètre.
Pour plus d’informations, consultez [déclaration d’attribut Alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Attributs de Validation d’argument

### <a name="validatecount"></a>ValidateCount

Spécifie le nombre minimal et maximal d’arguments qui sont autorisés pour un paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Spécifie un nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Spécifie que l’argument de paramètre d’applet de commande doit correspondre à un modèle d’expression régulière.
Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Spécifie les valeurs minimales et maximales pour un argument de paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Spécifie un ensemble de valeurs valides pour l’argument de paramètre d’applet de commande.
Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
