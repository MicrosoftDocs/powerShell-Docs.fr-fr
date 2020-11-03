---
description: Décrit comment récupérer et exécuter des commandes dans l’historique des commandes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 64a8fac4f25ac60be58aca8549748b9e4dde6c3b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208014"
---
# <a name="about-history"></a>À propos de l’historique

## <a name="short-description"></a>Description courte
Décrit comment récupérer et exécuter des commandes dans l’historique des commandes.

## <a name="long-description"></a>Description longue

Lorsque vous entrez une commande à l’invite de commandes, PowerShell enregistre la commande dans l’historique des commandes. Vous pouvez utiliser les commandes de l’historique comme enregistrement de votre travail. Vous pouvez rappeler et exécuter les commandes à partir de l’historique des commandes.

PowerShell a deux fournisseurs d’historique différents : l’historique intégré et l’historique géré par le module **PSReadLine** . Les historiques sont gérés séparément, mais les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.

## <a name="using-the-psreadline-history"></a>Utilisation de l’historique PSReadLine

L’historique PSReadLine effectue le suivi des commandes utilisées dans toutes les sessions PowerShell.
L’historique est écrit dans un fichier central par hôte. Ce fichier d’historique est disponible pour toutes les sessions et contient tous les historiques précédents. L’historique n’est pas supprimé à la fin de la session. En outre, cet historique ne peut pas être géré par les `*-History` applets de commande. Pour plus d’informations, consultez [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).

## <a name="using-the-built-in-session-history"></a>Utilisation de l’historique de session intégré

L’historique intégré effectue uniquement le suivi des commandes utilisées dans la session active. L’historique n’est pas disponible pour les autres sessions et est supprimé à la fin de la session.

### <a name="history-cmdlets"></a>Applets de commande d’historique

PowerShell possède un ensemble d’applets de commande qui gèrent l’historique des commandes.

| Applet de commande           | Alias  | Description                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | Obtient l’historique de la commande.                  |
| `Invoke-History` | `r`    | Exécute une commande de l'historique.     |
| `Add-History`    |        | Ajoute une commande à l’historique de commande.     |
| `Clear-History`  | `clhy` | Supprime les commandes de l’historique de commande. |

### <a name="keyboard-shortcuts-for-managing-history"></a>Raccourcis clavier pour la gestion de l’historique

Dans la console PowerShell, vous pouvez utiliser les raccourcis suivants pour gérer l’historique des commandes.

- <kbd>Flèche vers le haut</kbd> : affiche la commande précédente.
- <kbd>Flèche</kbd> vers le bas-affiche la commande suivante.
- <kbd>F7</kbd> -affiche l’historique des commandes.
- <kbd>Echap</kbd> : pour masquer l’historique.
- <kbd>F8</kbd> -recherche une commande. Tapez un ou plusieurs caractères, puis appuyez sur <kbd>F8</kbd>. Appuyez de nouveau sur <kbd>F8</kbd> pour l’instance suivante.
- <kbd>F9</kbd> -Rechercher une commande par ID d’historique. Tapez l’ID de l’historique, puis appuyez sur <kbd>F9</kbd>. Appuyez sur <kbd>F7</kbd> pour Rechercher l’ID.
- <kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> : recherchez `*<string>*` et retourne la correspondance la plus récente dans l’historique. Si vous appuyez sur <kbd>Tab</kbd> à plusieurs reprises, il parcourt les éléments correspondants dans votre historique.

> [!NOTE]
> Ces combinaisons de touches sont implémentées par l’application hôte de la console. D’autres applications, telles que Visual Studio Code ou Windows Terminal, peuvent avoir des combinaisons de touches différentes. Les liaisons peuvent être substituées par le module PSReadLine. PSReadLine se charge automatiquement quand vous démarrez une session PowerShell.
> Avec PSReadLine chargé, les fonctions <kbd>F7</kbd> et <kbd>F9</kbd> ne sont liées à aucune fonction. PSReadLine ne fournit pas de fonctionnalité équivalente. Pour plus d’informations, consultez [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).

### <a name="maximumhistorycount"></a>MaximumHistoryCount

La `$MaximumHistoryCount` variable de préférence détermine le nombre maximal de commandes que PowerShell enregistre dans l’historique des commandes. La valeur par défaut est
4096.

Par exemple, la commande suivante réduit les `$MaximumHistoryCount` commandes à 100 :

```powershell
$MaximumHistoryCount = 100
```

Pour appliquer le paramètre, redémarrez PowerShell.

Pour enregistrer la nouvelle valeur de la variable pour toutes vos sessions PowerShell, ajoutez l’instruction d’assignation à un profil PowerShell. Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).

Pour plus d’informations sur la `$MaximumHistoryCount` variable de préférence, consultez [about_Preference_Variables](about_Preference_Variables.md).

### <a name="order-of-commands-in-the-history"></a>Ordre des commandes dans l’historique

Les commandes sont ajoutées à l’historique à la fin de l’exécution de la commande, et non lors de l’entrée de la commande. Si les commandes prennent un certain temps, ou si les commandes s’exécutent dans une invite imbriquée, les commandes peuvent sembler être désordonnées dans l’historique. Les commandes qui s’exécutent dans une invite imbriquée sont exécutées uniquement lorsque vous quittez le niveau d’invite.

## <a name="see-also"></a>Voir aussi

- [about_Line_Editing](about_Line_Editing.md)
- [about_Preference_Variables](about_Preference_Variables.md)
- [about_Profiles](about_Profiles.md)
- [about_Variables](about_Variables.md)
- [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)
