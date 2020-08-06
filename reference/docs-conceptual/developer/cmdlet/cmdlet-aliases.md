---
title: Alias d’applet de commande | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fed4055f09e01c5f3fa87584d48551918606f4eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784535"
---
# <a name="cmdlet-aliases"></a>Alias des applets de commande

Vous pouvez utiliser des alias d’applet de commande pour améliorer l’expérience utilisateur de l’applet de commande. Vous pouvez ajouter des alias aux cmdlets fréquemment utilisées pour réduire la saisie et faciliter l’exécution rapide des tâches. Vous pouvez inclure des alias intégrés dans vos applets de commande ou les utilisateurs peuvent définir leurs propres alias personnalisés.

Par exemple, l’applet de [commande obtenir-Command](/powershell/module/microsoft.powershell.core/get-command) a un `gcm` alias intégré. Vous pouvez également utiliser des alias pour ajouter des noms de commande d’autres langues afin que les utilisateurs n’aient pas à apprendre de nouvelles commandes.

## <a name="alias-guidelines"></a>Instructions relatives aux alias

Suivez ces instructions lorsque vous créez des alias intégrés pour vos applets de commande :

- Avant d’assigner des alias, démarrez Windows PowerShell, puis exécutez l’applet de commande [obtenir-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) pour voir les alias déjà utilisés.

- Incluez un préfixe d’alias qui référence le verbe du nom de l’applet de commande et un suffixe d’alias qui référence le nom du nom de l’applet de commande. Par exemple, l’alias de l' `Import-Module` applet de commande est « Bureau à pas ». Pour obtenir la liste de tous les verbes et leurs alias, consultez [verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

- Pour les applets de commande qui ont le même verbe, incluez le même préfixe d’alias. Par exemple, les alias de toutes les applets de commande Windows PowerShell dont le nom contient le verbe « obtenir » utilisent le préfixe « g ».

- Pour les applets de commande qui ont le même nom, incluez le même suffixe d’alias. Par exemple, les alias de toutes les applets de commande Windows PowerShell qui ont le nom « session » dans leur nom utilisent le suffixe « SN ».

- Pour les applets de commande équivalentes aux commandes dans d’autres langues, utilisez le nom de la commande.

- En général, rendez les alias aussi courts que possible. Assurez-vous que l’alias a au moins un caractère distinct pour le verbe et un caractère distinct pour le nom. Ajoutez autant de caractères que nécessaire pour rendre l’alias unique.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
