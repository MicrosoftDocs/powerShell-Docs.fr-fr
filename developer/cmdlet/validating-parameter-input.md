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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858845"
---
# <a name="validating-parameter-input"></a>Validation des entrées de paramètre

Windows PowerShell peut valider les arguments passés aux paramètres d’applet de commande de plusieurs façons. Windows PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument. Il peut valider le nombre d’arguments disponibles (nombre). Ces règles de validation sont définies par les attributs de validation qui sont déclarées avec l’attribut de paramètre sur les propriétés publiques de la classe de l’applet de commande.

Pour valider un argument de paramètre, le runtime Windows PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande. Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur. Chaque paramètre de validation définit une règle de validation est appliquée par Windows PowerShell.

Windows PowerShell applique les règles de validation basées sur les attributs suivants.

ValidateCount Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter. Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).

ValidateLength Spécifie le nombre minimal et maximal de caractères dans l’argument de paramètre. Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).

ValidatePattern spécifie une expression régulière qui valide l’argument de paramètre. Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).

ValidateRange spécifie les valeurs minimales et maximales de l’argument de paramètre. Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).

ValidateSet spécifie les valeurs valides pour l’argument de paramètre. Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Comment valider l’entrée de paramètre](./how-to-validate-parameter-input.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
