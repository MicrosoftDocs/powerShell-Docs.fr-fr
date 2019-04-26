---
title: Modules et composants logiciel enfichables | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067618"
---
# <a name="modules-and-snap-ins"></a>Modules et composants logiciels enfichables

Applets de commande peuvent être ajoutés à une session à l’aide de modules (introduites par Windows PowerShell 2.0) ou des composants logiciel enfichables. Une fois que l’applet de commande est ajoutée à la session, qu'il peut être exécuté par programme par une application hôte ou de manière interactive en ligne de commande.

Nous vous recommandons d’utiliser les modules en tant que la méthode de remise pour l’ajout d’applets de commande à une session pour les raisons suivantes :

- Modules permettent d’ajouter des applets de commande en chargeant l’assembly dans lequel l’applet de commande est défini. Il est inutile d’implémenter une classe snap-in.

- Modules permettent d’ajouter d’autres ressources, telles que les variables, fonctions, scripts, types et mise en forme les fichiers et bien plus encore.

- Composants logiciel enfichables peuvent être utilisés uniquement pour ajouter des fournisseurs et applets de commande à la session.

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](../module/writing-a-windows-powershell-module.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
