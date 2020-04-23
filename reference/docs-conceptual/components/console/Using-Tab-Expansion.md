---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation du développement par tabulation
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67031008"
---
# <a name="using-tab-expansion"></a>Utilisation du développement par tabulation

Les interpréteurs de ligne de commande offrent souvent une manière de compléter automatiquement les noms de fichiers ou commandes longs, en accélérant la saisie de commandes et en fournissant des indications. PowerShell permet de renseigner des noms de fichiers et des noms de d’applet de commande en appuyant sur la touche <kbd>Tab</kbd>.

> [!NOTE]
> Le développement par tabulation est contrôlé par la fonction interne TabExpansion ou TabExpansion2. Étant donné que cette fonction peut être modifiée ou remplacée, cette explication a trait au comportement de la configuration PowerShell par défaut.

Pour renseigner automatiquement un nom de fichier ou un chemin d’accès à partir des choix disponibles, tapez une partie du nom, puis appuyez sur la touche <kbd>Tab</kbd>. PowerShell développe automatiquement le nom sur la base de la première correspondance trouvée. Des appuis répétés sur la touche <kbd>Tab</kbd> permettent de passer en revue tous les choix disponibles.

Le développement par tabulation des noms d’applet de commande est légèrement différent. Pour développer par tabulation un nom d’applet de commande, tapez la première partie entière du nom (verbe) et le trait d’union qui suit. Vous pouvez entrer davantage de caractères du nom pour une correspondance partielle. Par exemple, si vous tapez `get-co`, puis appuyez sur la touche <kbd>Tab</kbd>, PowerShell développe automatiquement le nom de l’applet de commande `Get-Command` (notez qu’il modifie également la casse des lettres pour leur attribuer leur format standard). Si vous appuyez de nouveau sur la touche <kbd>Tab</kbd>, PowerShell remplace ce nom par le seul autre nom d’applet de commande correspondant, `Get-Content`.

Vous pouvez utiliser le développement par tabulation à plusieurs reprises sur la même ligne. Par exemple, vous pouvez l’utiliser sur le nom de l’applet de commande `Get-Content` en entrant ce qui suit :

```
PS> Get-Con<Tab>
```

Lorsque vous appuyez sur la touche <kbd>Tab</kbd>, la commande est développée en :

```
PS> Get-Content
```

Vous pouvez ensuite partiellement spécifier le chemin d’accès au fichier journal Active Setup, puis utiliser à nouveau le développement par tabulation :

```
PS> Get-Content c:\windows\acts<Tab>
```

Lorsque vous appuyez sur la touche <kbd>Tab</kbd>, la commande est développée en :

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Une limitation du processus de développement par tabulation est que les tabulations sont toujours interprétées comme des tentatives de compléter un mot. Si vous copiez et collez des exemples de commandes dans une console PowerShell, vérifiez qu’ils ne contiennent pas de tabulations. Autrement, les résultats seront imprévisibles et presque certainement différents de ce que vous attendez.
