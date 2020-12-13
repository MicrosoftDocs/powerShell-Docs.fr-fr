---
ms.date: 09/13/2016
ms.topic: reference
title: Modules et composants logiciels enfichables
description: Modules et composants logiciels enfichables
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658677"
---
# <a name="modules-and-snap-ins"></a>Modules et composants logiciels enfichables

Des applets de commande peuvent être ajoutées à une session à l’aide de modules (introduits par Windows PowerShell 2,0) ou de composants logiciels enfichables. Une fois l’applet de commande ajoutée à la session, elle peut être exécutée par programme par une application hôte ou de manière interactive à partir de la ligne de commande.

Nous vous recommandons d’utiliser les modules comme méthode de remise pour ajouter des applets de commande à une session pour les raisons suivantes :

- Les modules vous permettent d’ajouter des applets de commande en chargeant l’assembly dans lequel l’applet de commande est définie. Il n’est pas nécessaire d’implémenter une classe de composant logiciel enfichable.

- Les modules vous permettent d’ajouter d’autres ressources, telles que des variables, des fonctions, des scripts, des types et des fichiers de mise en forme, et bien plus encore.

- Les composants logiciels enfichables ne peuvent être utilisés que pour ajouter des applets de commande et des fournisseurs à la session.

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](writing-a-windows-powershell-module.md)

[Écriture d’une applet de commande Windows PowerShell](../cmdlet/cmdlet-overview.md)
