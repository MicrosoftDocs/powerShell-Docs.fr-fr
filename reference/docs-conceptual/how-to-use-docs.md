---
ms.date: 07/29/2020
keywords: powershell,applet de commande
title: Guide pratique pour utiliser la documentation PowerShell
ms.openlocfilehash: 1cfeb9eea564e7618062e1b8ada4948bd9e22969
ms.sourcegitcommit: 9f9eb95bc859e9e0fed48101327a602b2ced351d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87821527"
---
# <a name="how-to-use-the-powershell-documentation"></a>Guide pratique pour utiliser la documentation PowerShell

Bienvenue dans la documentation en ligne de PowerShell. Ce site contient des informations de référence sur les applets de commande des versions suivantes de PowerShell :

- PowerShell 7
- PowerShell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Recherche d’articles et sélection de version

Il existe deux façons de rechercher du contenu dans la documentation. Le plus simple est d’utiliser la zone de filtre située en dessous du sélecteur de version. Il vous suffit d’entrer un mot qui figure dans le titre d’un article. La page affiche une liste d’articles correspondants. Vous pouvez aussi sélectionner l’option permettant d’effectuer une recherche sur tout le site à partir de cette liste.

Par défaut, ce site affiche la documentation de la dernière version publiée de PowerShell. Certaines applets de commande fonctionnent différemment d’une version de PowerShell à l’autre. Veillez à consulter la documentation de la version de PowerShell que vous utilisez.

Utilisez le sélecteur de version en haut de la page pour sélectionner la version souhaitée de PowerShell.

![Utilisation du sélecteur de version](media/how-to-use-docs/version-search.gif)

Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`. L’exemple suivant montre la sortie pour Windows PowerShell 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

Si vous débutez avec PowerShell et avez besoin d’aide pour comprendre la syntaxe des commandes, consultez [À propos de la syntaxe des commandes](/powershell/module/microsoft.powershell.core/about/about_command_syntax).

## <a name="finding-articles-for-previous-versions"></a>Recherche d’articles pour les versions précédentes

La documentation des versions antérieures de PowerShell a été archivée dans notre site [Versions précédentes](https://aka.ms/PSLegacyDocs).

Ce site contient la documentation pour les rubriques suivantes :

- PowerShell 3.0
- PowerShell 4.0
- PowerShell 5.0
- Flux de travail PowerShell
- Accès web PowerShell
