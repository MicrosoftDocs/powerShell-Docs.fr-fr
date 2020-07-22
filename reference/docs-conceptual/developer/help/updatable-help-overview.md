---
title: Vue d’ensemble de l’aide actualisable
ms.date: 03/22/2012
ms.openlocfilehash: 142bac764c93728d302707504d6d3fb2d50a3a7b
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892317"
---
# <a name="updatable-help-overview"></a>Vue d’ensemble de l’aide actualisable

Ce document fournit une introduction à la conception et au fonctionnement de la fonctionnalité d’aide actualisable PowerShell. Il est conçu pour les auteurs de modules et d’autres qui fournissent des rubriques d’aide Windows PowerShell aux utilisateurs.

## <a name="introduction"></a>Introduction

Les rubriques d’aide PowerShell font partie intégrante de l’expérience PowerShell. À l’instar des modules PowerShell, les rubriques d’aide sont continuellement mises à jour et améliorées par les auteurs et par les contributions de la communauté des utilisateurs de PowerShell.

La fonctionnalité *d’aide actualisable* , introduite dans Windows PowerShell 3,0, garantit que les utilisateurs disposent des dernières versions des rubriques d’aide à l’invite de commandes, même pour les commandes PowerShell intégrées, sans télécharger de nouveaux modules ni exécuter Windows Update. L’aide actualisable facilite la mise à jour en fournissant des applets de commande qui téléchargent les versions les plus récentes des rubriques d’aide à partir d’Internet et les installent dans les sous-répertoires appropriés sur l’ordinateur local de l’utilisateur. Même les utilisateurs qui se trouvent derrière des pare-feu peuvent utiliser les nouvelles applets de commande pour obtenir une aide mise à jour à partir d’un partage de fichiers interne.

L’aide actualisable est entièrement prise en charge par tous les modules Windows PowerShell dans Windows 8 et Windows Server 2012, et ses fonctionnalités sont disponibles pour tous les auteurs de modules Windows PowerShell. L’aide actualisable prend en charge uniquement les fichiers d’aide basés sur XML. Elle ne prend pas en charge l’aide basée sur les commentaires.

L’aide actualisable comprend les fonctionnalités suivantes.

- L’applet de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , qui détermine si les utilisateurs disposent des fichiers d’aide les plus récents pour un module et, si ce n’est pas le cas, télécharge les fichiers d’aide les plus récents à partir d’Internet, les décompresse et les installe dans les sous-répertoires appropriés du module sur l’ordinateur de l’utilisateur. Les utilisateurs peuvent utiliser l’applet de commande [obtenir-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) pour afficher immédiatement les rubriques d’aide récemment installées. Ils n’ont pas besoin de redémarrer PowerShell.

- L’applet de commande [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) , qui télécharge les fichiers d’aide les plus récents à partir d’Internet et les enregistre dans un répertoire du système de fichiers. Les utilisateurs peuvent utiliser l' `Update-Help` applet de commande pour obtenir les fichiers d’aide à partir du répertoire du système de fichiers, et les décompresser et les installer dans les sous-répertoires du module sur l’ordinateur de l’utilisateur. L' `Save-Help` applet de commande est conçue pour les utilisateurs qui ont un accès limité ou non à Internet et pour les entreprises qui préfèrent limiter l’accès à Internet.

- **Aide pour un module**. Les fichiers d’aide d’un module sont gérés et remis en tant qu’unité, afin que les utilisateurs puissent obtenir tous les fichiers d’aide pour les modules qu’ils utilisent. L’aide actualisable est prise en charge uniquement pour les modules, et non pour les composants logiciels enfichables Windows PowerShell.

- **Prise en charge des versions**. L’aide actualisable utilise standard à quatre positions (N1. N2. N3. N4).
  L’aide actualisable télécharge les fichiers d’aide lorsque le numéro de version des fichiers d’aide sur l’ordinateur de l’utilisateur (ou dans le `Save-Help` Répertoire) est inférieur au numéro de version des fichiers d’aide à l’emplacement Internet.

- **Prise en charge de plusieurs langues**. L’aide actualisable prend en charge les fichiers d’aide de module dans plusieurs cultures d’interface utilisateur.
  Les noms de fichiers d’aide pouvant être mis à jour incluent des codes de langue standard, tels que « en-US » et « ja-JP », et les `Update-Help` applets de commande et `Save-Help` placent les fichiers d’aide dans des sous-répertoires spécifiques au langage du répertoire du module.

- **Aide générée automatiquement**. L’applet de commande [obtenir-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) affiche l’aide de base pour les commandes qui n’ont pas de fichiers d’aide. L’aide générée automatiquement contient la syntaxe de commande et les alias, ainsi que des instructions pour l’utilisation de l’aide en ligne et de l’aide actualisable.

- **Aide en ligne améliorée**. Un accès facile à l’aide en ligne ne nécessite plus de fichiers d’aide. Le paramètre **Online** de l' `Get-Help` applet de commande obtient à présent l’URL d’une rubrique d’aide en ligne à partir de la valeur de la propriété **HelpUri** d’une commande, si elle ne trouve pas l’URL de l’aide en ligne dans un fichier d’aide. Vous pouvez remplir la propriété **HelpUri** en ajoutant un attribut **HelpUri** au code des applets de commande, des fonctions et des commandes CIM, ou en utilisant le **. Lier** la directive d’aide basée sur des commentaires dans les flux de travail et les scripts.

  Pour mettre à jour nos fichiers d’aide, les modules Windows PowerShell dans Windows 8 et Windows Server vNext ne sont pas fournis avec les fichiers d’aide. Les utilisateurs peuvent utiliser l’aide actualisable pour installer les fichiers d’aide et les mettre à jour. Les auteurs d’autres modules peuvent inclure des fichiers d’aide dans des modules ou les omettre. La prise en charge de l’aide actualisable est facultative, mais recommandée.
