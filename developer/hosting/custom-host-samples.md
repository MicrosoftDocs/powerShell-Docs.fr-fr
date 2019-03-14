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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794142"
---
# <a name="custom-host-samples"></a>Exemples d’hôtes personnalisés

Cette section inclut des exemples de code pour l’écriture d’un hôte personnalisé. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console puis copier le code dans les rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

 [Exemple de Host01](./host01-sample.md) cet exemple montre comment implémenter une application hôte qui utilise une base de l’hôte personnalisé.

 [Exemple de Host02](./host02-sample.md) cet exemple montre comment écrire une application hôte qui utilise le runtime de Windows PowerShell avec une implémentation d’hôte personnalisé. L’application hôte définit la culture de l’hôte pour l’allemand, exécute le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande et affiche les résultats que vous les verriez avec pwrsh.exe pour ensuite imprimer la date et l’heure actuelle en allemand.

 [Exemple de Host03](./host03-sample.md) cet exemple montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.

 [Exemple de Host04](./host04-sample.md) cet exemple montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.

 [Exemple de hôte05](./host05-sample.md) cet exemple montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend également en charge les appels à des ordinateurs distants à l’aide de la [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) et [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) applets de commande

 [Exemple de Host06](./host06-sample.md) cet exemple montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.

## <a name="see-also"></a>Voir aussi
