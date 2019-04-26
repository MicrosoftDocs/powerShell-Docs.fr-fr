---
title: Affichage des informations d’erreur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068281"
---
# <a name="displaying-error-information"></a>Affichage des informations sur les erreurs

Cette rubrique décrit les façons dans lequel les utilisateurs peuvent afficher des informations sur l’erreur.

Lorsque votre applet de commande rencontre une erreur, la présentation des informations d’erreur, par défaut, ressemble à la sortie d’erreur suivant.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Toutefois, les utilisateurs peuvent afficher les erreurs par catégorie en définissant le `$ErrorView` à la variable `"CategoryView"`. Affichage des catégories affiche des informations spécifiques à partir de l’enregistrement d’erreur plutôt qu’une description de texte libre de l’erreur. Cette vue peut être utile si vous avez une longue liste d’erreurs à analyser. Dans l’affichage des catégories, le message d’erreur précédent s’affiche comme suit.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Pour plus d’informations sur les catégories d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Voir aussi

[Windows PowerShell erreur enregistrements](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
