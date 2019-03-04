---
title: Alias d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860505"
---
# <a name="cmdlet-aliases"></a>Alias des applets de commande

Vous pouvez utiliser des alias d’applet de commande pour améliorer l’expérience utilisateur de l’applet de commande. Vous pouvez ajouter des alias pour les applets de commande fréquemment utilisées pour réduire la frappe et pour le rendre plus facile à effectuer des tâches rapidement. Vous pouvez inclure les alias intégrés dans vos applets de commande, ou les utilisateurs peuvent définir leurs propres alias personnalisés.

Par exemple, le [Get-Command](/powershell/module/microsoft.powershell.core/get-command) applet de commande intègre `gcm` alias. Vous pouvez également utiliser des alias pour ajouter des noms de commande à partir d’autres langages afin que les utilisateurs n’ont pas à apprendre de nouvelles commandes.

## <a name="alias-guidelines"></a>Instructions d’alias

Suivez ces instructions lorsque vous créez des alias intégrés pour vos applets de commande :

- Avant de vous attribuez les alias, démarrez Windows PowerShell et exécutez le [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) applet de commande pour afficher les alias qui sont déjà utilisés.

- Inclure un préfixe d’alias qui référence le verbe du nom d’applet de commande et un suffixe d’alias qui référence le substantif du nom de l’applet de commande. Par exemple, l’alias pour le `Import-Module` applet de commande est « ipmo ». Pour obtenir la liste de tous les verbes et de leurs alias, consultez [verbes d’applet de commande](./approved-verbs-for-windows-powershell-commands.md).

- Pour les applets de commande qui ont le même verbe incluent le même préfixe de l’alias. Par exemple, les alias de toutes les cmdlets Windows PowerShell qui ont le verbe « Get » dans leur nom utilisent le préfixe « g ».

- Pour les applets de commande qui ont le même nom, inclure le même suffixe de l’alias. Par exemple, les alias de toutes les cmdlets Windows PowerShell qui comportent le mot « Session » dans leur nom utilisent le suffixe « sn ».

- Pour les applets de commande qui sont équivalentes aux commandes dans d’autres langages, utilisez le nom de la commande.

- En général, rendre aussi courte que possible. Vérifiez que l’alias a au moins un caractère distinct pour le verbe et un caractère distinct pour le substantif. Ajouter plus de caractères que nécessaire pour rendre l’alias unique.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
