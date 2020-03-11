---
ms.date: 10/20/2019
keywords: powershell,applet de commande
title: Guide pratique pour utiliser la documentation PowerShell
ms.openlocfilehash: 7b73bc82f32e3ce1e6015822e0cc82078183931b
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279302"
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

![sélecteur de version](media/how-to-use-docs/version-search.gif)

Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`. L’exemple suivant montre la sortie pour Windows PowerShell 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
