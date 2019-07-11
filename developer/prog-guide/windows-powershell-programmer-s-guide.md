---
title: Windows PowerShell programmeur&#39;s Guide | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 44a9c970d32dc6f98456227f8b02101280541dd9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734878"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell programmeur&#39;s Guide

Ce guide du programmeur est destiné aux développeurs qui souhaitent fournir un environnement de gestion de ligne de commande pour les administrateurs système. Windows PowerShell fournit un moyen simple de générer des commandes de gestion qui exposent des objets .NET, tout en permettant aux PowerShell de Windows pour faire l’essentiel du travail pour vous.

Dans le développement de commande traditionnelles, vous devez écrire un analyseur de paramètre, un classeur de paramètre, filtres et toutes les autres fonctionnalités exposées par chaque commande. Windows PowerShell fournit la commande suivante pour le rendre facile à écrire des commandes :

- Un puissant PowerShell de Windows runtime (moteur d’exécution) avec son propre analyseur et un mécanisme de liaison automatiquement les paramètres de commande.

- Utilitaires de mise en forme et d’affichage des résultats de la commande à l’aide d’un interpréteur de ligne de commande (CLI).

- Prise en charge des niveaux élevés de la fonctionnalité (via les fournisseurs Windows PowerShell) qui facilitent l’accès aux données stockées.

  Un coût minimal, vous pouvez représenter un objet .NET par une commande enrichi ou un ensemble de commandes qui offrira une expérience de ligne de commande complète à l’administrateur.

  La section suivante couvre les concepts clés de Windows PowerShell et les termes du contrat. Vous devez vous familiariser avec ces concepts et les termes avant de commencer le développement.

## <a name="about-windows-powershell"></a>À propos de Windows PowerShell

Windows PowerShell définit plusieurs types de commandes que vous pouvez utiliser dans le développement. Ces commandes incluent : fonctions, les filtres, les scripts, les alias et les exécutables (applications). Le type de commande principal abordé dans ce guide est une commande simple, petite appelée un « cmdlet ». Windows PowerShell fournit un ensemble d’applets de commande et prend entièrement en charge la personnalisation de l’applet de commande pour l’adapter à votre environnement. Le runtime Windows PowerShell traite tous les types de commande comme il le fait applets de commande, à l’aide de pipelines.

Outre les commandes, Windows PowerShell prend en charge les divers fournisseurs Windows PowerShell personnalisables qui rendent des ensembles spécifiques d’applets de commande disponibles. L’interpréteur de commandes opère au sein de l’application hôte fournis par Windows PowerShell (PowerShell.exe Windows), mais il est également accessible à partir d’une application hôte personnalisé que vous pouvez développer pour répondre aux besoins spécifiques. Pour plus d’informations, consultez [Windows PowerShell fonctionnement](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Applets de commande Windows PowerShell

Une applet de commande est une commande légère utilisée dans l’environnement Windows PowerShell. Le runtime de Windows PowerShell appelle ces applets de commande dans le contexte des scripts d’automatisation qui sont fournies à la ligne de commande, et le runtime Windows PowerShell également les appelle par programme via Windows APIs PowerShell.

Pour plus d’informations sur les applets de commande, consultez [écrire une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Fournisseurs Windows PowerShell

Dans la réalisation des tâches d’administration, l’utilisateur peut-être examiner les données stockées dans un magasin de données (par exemple, le système de fichiers, le Registre Windows ou un magasin de certificats). Pour faciliter ces opérations, Windows PowerShell définit un module appelé un fournisseur Windows PowerShell qui peut être utilisé pour accéder à un magasin de données spécifique, par exemple le Registre Windows. Chaque fournisseur prend en charge un ensemble d’applets de commande associées à l’utilisateur une vue symétrique des données dans le magasin.

Windows PowerShell fournit par défaut plusieurs fournisseurs Windows PowerShell. Par exemple, le fournisseur Registry prend en charge la navigation et la manipulation du Registre Windows. Les clés de Registre sont représentées en tant qu’éléments et valeurs de Registre sont traités en tant que propriétés.

Si vous exposez un magasin de données que vous devez accéder à l’utilisateur, vous devrez peut-être écrire votre propre fournisseur Windows PowerShell, comme décrit dans [créant les fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Pour plus d’informations aboutWindows une fournisseurs PowerShell, consultez [Windows PowerShell fonctionnement](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Application hôte

Windows PowerShell inclut la valeur par défaut hôte application powershell.exe, qui est une application console qui interagit avec l’utilisateur et héberge le runtime de Windows PowerShell à l’aide d’une fenêtre de console.

Rarement vous devez écrire votre propre application hôte pour Windows PowerShell, bien que la personnalisation est prise en charge. Un cas dans lesquels vous devrez peut-être votre propre application est lorsque vous avez besoin d’une interface utilisateur graphique est plus riche que l’interface fournie par l’application d’hôte par défaut. Vous pourriez également une application personnalisée lorsque vous basez votre GUI sur la ligne de commande. Pour plus d’informations, consultez [comment créer une Application hôte de Windows PowerShell](/powershell/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Service d’exécution Windows PowerShell

Le runtime de Windows PowerShell est le moteur d’exécution qui implémente le traitement des commandes. Il inclut les classes qui fournissent l’interface entre l’application hôte et les commandes Windows PowerShell et les fournisseurs. Le runtime de Windows PowerShell est implémenté comme un objet d’instance d’exécution pour la session Windows PowerShell actuelle, qui est l’environnement d’exploitation dans lequel l’interpréteur de commandes et les commandes s’exécutent. Pour obtenir des détails opérationnels, consultez [Windows PowerShell fonctionnement](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Langage de Windows PowerShell

Le langage Windows PowerShell fournit le script des fonctions et des mécanismes pour appeler des commandes. Pour obtenir des informations de script complètes, consultez que la référence du langage Windows PowerShell fournis avec Windows PowerShell.

### <a name="extended-type-system-ets"></a>Système de Type étendu (ETS)

Windows PowerShell fournit un accès à une variété de différents objets, tels que .NET et objets XML. Par conséquent, pour présenter une abstraction commune pour tous les types d’objets, l’interpréteur de commandes utilise son système de type étendu (ETS). La plupart des fonctionnalités ETS est transparent pour l’utilisateur, mais le script ou un développeur .NET utilise aux fins suivantes :

- Afficher un sous-ensemble des membres d’objets spécifiques. Windows PowerShell fournit une vue « adaptée » plusieurs types d’objets spécifiques.

- Ajout de membres aux objets existants.

- L’accès aux objets sérialisés.

- Écriture des objets personnalisés.

  À l’aide de ETS, vous pouvez créer nouveau flexibles « types » qui sont compatibles avec le langage Windows PowerShell. Si vous êtes un développeur .NET, vous êtes en mesure d’utiliser des objets à l’aide de la même sémantique que le langage Windows PowerShell s’applique aux scripts, par exemple, pour déterminer si un objet a la valeur `true`.

  Pour plus d’informations sur ETS et comment Windows PowerShell utilise des objets, consultez [Concepts d’objet Windows PowerShell](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programmation pour Windows PowerShell

Windows PowerShell définit son code des commandes, les fournisseurs et les autres modules de programme à l’aide de .NET Framework. Vous n'êtes pas limité à l’utilisation de Microsoft Visual Studio lors de la création de modules personnalisés pour Windows PowerShell, bien que les exemples fournis dans ce guide sont connus pour s’exécuter dans cet outil. Vous pouvez utiliser n’importe quel langage .NET qui prend en charge l’héritage de classe et l’utilisation d’attributs. Dans certains cas, Windows APIs PowerShell nécessitent le langage de programmation pour être en mesure d’accéder aux types génériques.

## <a name="programmers-reference"></a>Référence du programmeur

Pour référence lors du développement pour Windows PowerShell, consultez le [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Mise en route à l’aide de Windows PowerShell

Pour plus d’informations sur le démarrage à utiliser l’interpréteur de commandes Windows PowerShell, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) livrés avec Windows PowerShell. Un document de pliage en trois aide-mémoire est également fourni un manuel de démarrage pour une utilisation de l’applet de commande.

## <a name="contents-of-this-guide"></a>Contenu de ce Guide

|Rubrique|Définition|
|-----------|----------------|
|[Comment créer un fournisseur PowerShell de Windows](./how-to-create-a-windows-powershell-provider.md)|Cette section décrit comment générer un fournisseur Windows PowerShell pour Windows PowerShell.|
|[Comment créer une Application hôte PowerShell de Windows](/powershell/developer/hosting/writing-a-windows-powershell-host-application)|Cette section décrit comment écrire une application hôte qui manipule une instance d’exécution et comment écrire une application hôte qui implémente son propre hôte personnalisé.|
|[Comment créer un composant logiciel enfichable PowerShell Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Cette section décrit comment créer un composant logiciel enfichable qui est utilisé pour inscrire tous les fournisseurs et applets de commande dans un assembly et la création d’un composant logiciel enfichable personnalisé.|
|[Comment créer un interpréteur de commandes de Console](./how-to-create-a-console-shell.md)|Cette section décrit comment créer un interpréteur de commandes de console qui n’est pas extensible.|
|[Concepts de Windows PowerShell](./windows-powershell-concepts.md)|Cette section contient des informations conceptuelles qui vous aideront à comprendre Windows PowerShell à partir du point de vue d’un développeur.|

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
