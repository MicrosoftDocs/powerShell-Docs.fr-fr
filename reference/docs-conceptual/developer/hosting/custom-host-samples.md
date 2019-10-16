---
title: Exemples d’hôtes personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367508"
---
# <a name="custom-host-samples"></a>Exemples d’hôtes personnalisés

Cette section comprend un exemple de code pour l’écriture d’un hôte personnalisé. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console, puis copier le code à partir des rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

 [Exemple host01](./host01-sample.md) Cet exemple montre comment implémenter une application hôte qui utilise un hôte personnalisé de base.

 [Exemple Host02](./host02-sample.md) Cet exemple montre comment écrire une application hôte qui utilise le runtime Windows PowerShell avec une implémentation d’hôte personnalisée. L’application hôte définit la culture de l’hôte sur l’allemand, exécute l’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et affiche les résultats comme vous le feriez à l’aide de pwrsh. exe, puis imprime les données actuelles et l’heure en allemand.

 [Exemple Host03](./host03-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.

 [Exemple Host04](./host04-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.

 [Exemple Host05](./host05-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend également en charge les appels à des ordinateurs distants à l’aide des applets de commande [Enter-PSSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) et [Exit-PSSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) .

 [Exemple Host06](./host06-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.

## <a name="see-also"></a>Voir aussi
