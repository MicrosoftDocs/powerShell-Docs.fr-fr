---
title: Validation de l’entrée de paramètre | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783991"
---
# <a name="validating-parameter-input"></a>Validation des entrées de paramètre

PowerShell peut valider les arguments passés aux paramètres de l’applet de commande de plusieurs façons.
PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument.
Il peut valider le nombre d’arguments disponibles (le nombre).
Ces règles de validation sont définies par des attributs de validation qui sont déclarés avec l’attribut de paramètre sur les propriétés publiques de la classe d’applet de commande.

Pour valider un argument de paramètre, le runtime PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande.
Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur.
Chaque paramètre de validation définit une règle de validation appliquée par PowerShell.

PowerShell applique les règles de validation en fonction des attributs suivants.

### <a name="validatecount"></a>ValidateCount

Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter.
Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Spécifie le nombre minimal et maximal de caractères dans l’argument du paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Spécifie une expression régulière qui valide l’argument du paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Spécifie les valeurs minimale et maximale de l’argument du paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Spécifie les valeurs valides pour l’argument de paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Guide pratique pour valider l’entrée des paramètres](./how-to-validate-parameter-input.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
