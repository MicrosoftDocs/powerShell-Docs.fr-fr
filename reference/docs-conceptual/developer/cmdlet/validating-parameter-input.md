---
title: Validation de l’entrée de paramètre | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363508"
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

[Comment valider une entrée de paramètre](./how-to-validate-parameter-input.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
