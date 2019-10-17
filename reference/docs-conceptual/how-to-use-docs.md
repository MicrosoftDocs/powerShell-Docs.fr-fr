---
ms.date: 09/25/2019
keywords: powershell,applet de commande
title: Guide pratique pour utiliser la documentation PowerShell
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281655"
---
# <a name="how-to-use-the-powershell-documentation"></a>Guide pratique pour utiliser la documentation PowerShell

Bienvenue dans la documentation en ligne de PowerShell. Ce site contient des informations de référence sur les applets de commande des versions suivantes de PowerShell :

- PowerShell 7 (préversion)
- PowerShell 6
- PowerShell 5.1
- PowerShell 5.0
- PowerShell 4.0
- PowerShell 3.0

## <a name="selecting-your-version"></a>Sélection de votre version

Par défaut, ce site affiche la documentation de la dernière version publiée de PowerShell. Certaines applets de commande fonctionnent différemment d’une version de PowerShell à l’autre. Veillez à consulter la documentation de la version de PowerShell que vous utilisez.

Utilisez le sélecteur de version en haut de la page pour sélectionner la version souhaitée de PowerShell.

![sélecteur de version](images/how-to-use-docs/picker-vall.gif)

Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`. L’exemple suivant montre la sortie pour Windows PowerShell 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>Recherche d’articles

Il existe deux façons de rechercher du contenu dans la documentation. Le plus simple est d’utiliser la zone de filtre située en dessous du sélecteur de version. Il vous suffit d’entrer un mot qui figure dans le titre d’un article. La page affiche une liste d’articles correspondants. Vous pouvez aussi sélectionner l’option permettant d’effectuer une recherche sur tout le site à partir de cette liste.

![zone de filtre](images/how-to-use-docs/filter-search.gif)
