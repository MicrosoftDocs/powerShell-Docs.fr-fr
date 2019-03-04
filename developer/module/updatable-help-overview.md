---
title: Vue d’ensemble de l’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: 4e962890fa1d5c282a02a89f0ae2e263844c635e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856965"
---
# <a name="updatable-help-overview"></a>Vue d’ensemble de l’aide actualisable

Ce document fournit une présentation générale de la conception et le fonctionnement de la fonctionnalité de Windows PowerShell de l’aide actualisable. Il est conçu pour les auteurs de modules et d’autres rubriques d’aide Windows PowerShell de remettre aux utilisateurs.

## <a name="introduction"></a>Introduction

Rubriques d’aide Windows PowerShell font partie intégrante de l’expérience de Windows PowerShell. Comme les modules Windows PowerShell, les rubriques d’aide sont continuellement mis à jour et améliorés par les auteurs et les contributions de la Communauté d’utilisateurs de Windows PowerShell.

Le *aide actualisable* fonctionnalité, introduite dans Windows PowerShell 3.0, garantit que les utilisateurs ont les dernières versions des rubriques d’aide à l’invite de commande, même pour les commandes Windows PowerShell intégrées, sans télécharger de nouveaux modules ou mise à jour de Windows en cours d’exécution. Aide actualisable facilite la mise à jour en fournissant des applets de commande télécharger les dernières versions des rubriques d’aide à partir d’Internet et les installer dans les sous-répertoires corrects sur l’ordinateur local de l’utilisateur. Même les utilisateurs qui sont trouvent derrière des pare-feux peuvent utiliser les nouvelles applets de commande pour obtenir de l’aide de mises à jour à partir d’un partage de fichiers interne.

Aide actualisable est entièrement pris en charge par tous les modules Windows PowerShell dans Windows® 8 et Windows Server® 2012, et ses fonctionnalités sont disponibles pour tous les auteurs de module Windows PowerShell. Aide actualisable prend en charge uniquement les fichiers d’aide basé sur XML. Il ne prend pas en charge aide basée sur le commentaire.

Aide actualisable inclut les fonctionnalités suivantes.

- Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applet de commande, qui détermine si les utilisateurs ont l’aide les plus récents des fichiers pour un module et, dans le cas contraire, télécharge les fichiers d’aide plus récents à partir d’Internet, les décompresse et les installe dans les sous-répertoires de module approprié sur le ordinateur de l’utilisateur. Les utilisateurs peuvent utiliser le [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applet de commande pour afficher les rubriques d’aide qui vient d’être installé immédiatement. Il est inutile de redémarrer Windows PowerShell.

- Le [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applet de commande, qui télécharge l’aide la plus récente des fichiers à partir d’Internet et les enregistre dans un répertoire de système de fichiers. Les utilisateurs peuvent utiliser le `Update-Help` applet de commande pour obtenir les fichiers d’aide à partir du répertoire de système de fichier et de décompresser et de les installer dans les sous-répertoires de module sur l’ordinateur de l’utilisateur. Le `Save-Help` applet de commande est conçue pour les utilisateurs qui ont une limitée ou sans accès à Internet et pour les entreprises qui préfèrent limiter l’accès à Internet.

- **Aide pour un Module**. Fichiers d’aide pour un module sont gérés et stockés en tant qu’unité, afin que les utilisateurs peuvent obtenir tous les fichiers d’aide pour les modules qu’ils utilisent. Aide actualisable est pris en charge uniquement pour les modules, pas pour les composants logiciels enfichables Windows PowerShell.

- **Prise en charge de la version**. Aide actualisable utilise standard quatre positions (N1. N2. N3. Numéros de version N4). Aide actualisable télécharge les fichiers d’aide lorsque le numéro de version de l’aide de fichiers sur l’ordinateur de l’utilisateur (ou dans le `Save-Help` directory) est inférieur au numéro de version des fichiers d’aide à l’emplacement Internet.

- **Prise en charge multilingue**. Aide actualisable prend en charge les fichiers d’aide de module dans plusieurs cultures d’interface utilisateur. Aide actualisable noms de fichiers incluent les codes de langue standard, tels que « en-US » et « ja-JP » et le `Update-Help` et `Save-Help` applets de commande placer les fichiers d’aide dans les sous-répertoires spécifiques au langage du répertoire du module.

- **Aide générée automatiquement**. Le [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) applet de commande affiche l’aide de base pour les commandes qui n’ont pas de fichiers d’aide. L’aide générée automatiquement contient la syntaxe de commande et les alias et les instructions sur l’utilisation de l’aide en ligne et l’aide actualisable.

- **Amélioré d’aide en ligne**. Accès facile à l’aide en ligne n’a plus besoin des fichiers d’aide. Le **Online** paramètre de la `Get-Help` applet de commande obtient désormais l’URL d’une rubrique d’aide en ligne à partir de la valeur de la **HelpUri** propriété de n’importe quelle commande, si elle ne peut pas trouver l’URL de l’aide en ligne dans un fichier d’aide. Vous pouvez remplir le **HelpUri** propriété en ajoutant un **HelpUri** le code des applets de commande, fonctions et commandes CIM, ou à l’aide de l’attribut le **. Lien** directive aide basée sur un commentaire dans les workflows et les scripts.

  Pour rendre les fichiers d’aide actualisable, les modules Windows PowerShell dans Windows 8 et Windows Server vNext ne sont pas fournies avec les fichiers d’aide. Les utilisateurs peuvent utiliser l’aide actualisable pour installer les fichiers d’aide et les mettre à jour. Les auteurs des autres modules peuvent inclure des fichiers d’aide dans les modules ou les omettre. Prise en charge de l’aide actualisable est facultatif mais recommandé.
