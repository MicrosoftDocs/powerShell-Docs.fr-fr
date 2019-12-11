---
ms.date: 10/20/2019
keywords: powershell,applet de commande
title: Guide pratique pour utiliser la documentation PowerShell
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72676159"
---
# <a name="how-to-use-the-powershell-documentation"></a>Guide pratique pour utiliser la documentation PowerShell

Bienvenue dans la documentation en ligne de PowerShell. Ce site contient des informations de référence sur les applets de commande des versions suivantes de PowerShell :

- PowerShell 7 (préversion)
- PowerShell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Recherche d’articles et sélection de version

Il existe deux façons de rechercher du contenu dans la documentation. Le plus simple est d’utiliser la zone de filtre située en dessous du sélecteur de version. Il vous suffit d’entrer un mot qui figure dans le titre d’un article. La page affiche une liste d’articles correspondants. Vous pouvez aussi sélectionner l’option permettant d’effectuer une recherche sur tout le site à partir de cette liste.

Par défaut, ce site affiche la documentation de la dernière version publiée de PowerShell. Certaines applets de commande fonctionnent différemment d’une version de PowerShell à l’autre. Veillez à consulter la documentation de la version de PowerShell que vous utilisez.

Utilisez le sélecteur de version en haut de la page pour sélectionner la version souhaitée de PowerShell.

![sélecteur de version](images/how-to-use-docs/version-search.gif)

Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`. L’exemple suivant montre la sortie pour Windows PowerShell 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
