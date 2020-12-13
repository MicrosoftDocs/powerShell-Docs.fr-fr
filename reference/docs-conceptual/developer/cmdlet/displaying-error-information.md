---
ms.date: 09/13/2016
ms.topic: reference
title: Affichage des informations sur les erreurs
description: Affichage des informations sur les erreurs
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653053"
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
