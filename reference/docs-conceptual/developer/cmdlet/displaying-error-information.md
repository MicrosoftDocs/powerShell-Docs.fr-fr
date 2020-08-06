---
title: Affichage des informations sur les erreurs | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774573"
---
# <a name="displaying-error-information"></a>Affichage des informations sur les erreurs

Cette rubrique explique comment les utilisateurs peuvent afficher des informations sur les erreurs.

Lorsque votre applet de commande rencontre une erreur, la présentation des informations sur l’erreur sera, par défaut, similaire à la sortie d’erreur suivante.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Toutefois, les utilisateurs peuvent afficher les erreurs par catégorie en affectant à la variable la valeur `$ErrorView` `"CategoryView"` . Affichage des catégories affiche des informations spécifiques à partir de l’enregistrement d’erreur plutôt qu’une description de l’erreur en texte libre. Cette vue peut être utile si vous avez une longue liste d’erreurs à analyser. Dans l’affichage des catégories, le message d’erreur précédent s’affiche comme suit.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Pour plus d’informations sur les catégories d’erreurs, consultez [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Voir aussi

[Enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
