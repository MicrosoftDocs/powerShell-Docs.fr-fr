---
title: Validation des entrées de paramètre | Microsoft Docs
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
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429837"
---
# <a name="validating-parameter-input"></a>Validation des entrées de paramètre

PowerShell peut valider les arguments passés aux paramètres d’applet de commande de plusieurs façons.
PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument.
Il peut valider le nombre d’arguments disponibles (nombre).
Ces règles de validation sont définies par les attributs de validation qui sont déclarées avec l’attribut de paramètre sur les propriétés publiques de la classe de l’applet de commande.

Pour valider un argument de paramètre, le runtime PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande.
Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur.
Chaque paramètre de validation définit une règle de validation est appliquée par PowerShell.

PowerShell applique les règles de validation basées sur les attributs suivants.

### <a name="validatecount"></a>ValidateCount

Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter.
Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Spécifie le nombre minimal et maximal de caractères dans l’argument de paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Spécifie une expression régulière qui valide l’argument de paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Spécifie les valeurs minimales et maximales de l’argument de paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Spécifie les valeurs valides pour l’argument de paramètre.
Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Comment valider l’entrée de paramètre](./how-to-validate-parameter-input.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
