---
title: Guide des programmeurs&#39;Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: f8cbaf464345b8f2b693e72f3dbe781a47605b28
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417778"
---
# <a name="windows-powershell-programmer39s-guide"></a>Guide du programmeur&#39;Windows PowerShell

Ce guide du programmeur est destiné aux développeurs qui souhaitent fournir un environnement de gestion en ligne de commande pour les administrateurs système. Windows PowerShell offre un moyen simple de créer des commandes de gestion qui exposent des objets .NET, tout en permettant à Windows PowerShell d’effectuer la majeure partie du travail pour vous.

Dans le développement de commande traditionnel, vous devez écrire un analyseur de paramètre, un classeur de paramètres, des filtres et toutes les autres fonctionnalités exposées par chaque commande. Windows PowerShell fournit les éléments suivants pour vous permettre d’écrire facilement des commandes :

- Un puissant runtime Windows PowerShell (moteur d’exécution) avec son propre analyseur et un mécanisme de liaison automatique des paramètres de commande.

- Utilitaires pour la mise en forme et l’affichage des résultats des commandes à l’aide d’un interpréteur de ligne de commande (CLI).

- Prise en charge de hauts niveaux de fonctionnalité (via des fournisseurs Windows PowerShell) qui facilitent l’accès aux données stockées.

  À moindre coût, vous pouvez représenter un objet .NET par une commande riche ou un ensemble de commandes qui offrira une expérience de ligne de commande complète à l’administrateur.

  La section suivante présente les principaux concepts et termes de Windows PowerShell. Familiarisez-vous avec ces concepts et termes avant de commencer le développement.

## <a name="about-windows-powershell"></a>À propos de Windows PowerShell

Windows PowerShell définit plusieurs types de commandes que vous pouvez utiliser dans le développement. Ces commandes sont les suivantes : fonctions, filtres, scripts, alias et exécutables (applications). Le type de commande principal abordé dans ce guide est une simple commande simple appelée « cmdlet ». Windows PowerShell fournit un ensemble d’applets de commande et prend entièrement en charge la personnalisation des applets de commande pour les adapter à votre environnement. Le runtime Windows PowerShell traite tous les types de commande comme c’est le cas pour les applets de commande, à l’aide de pipelines.

En plus des commandes, Windows PowerShell prend en charge différents fournisseurs Windows PowerShell personnalisables qui rendent disponibles des ensembles d’applets de commande spécifiques. L’interpréteur de commandes fonctionne dans l’application hôte fournie par Windows PowerShell (Windows PowerShell. exe), mais il est également accessible à partir d’une application hôte personnalisée que vous pouvez développer pour répondre à des exigences spécifiques. Pour plus d’informations, consultez fonctionnement de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Applets de commande Windows PowerShell

Une applet de commande est une commande légère qui est utilisée dans l’environnement Windows PowerShell. Le runtime Windows PowerShell appelle ces applets de commande dans le contexte des scripts d’automatisation fournis sur la ligne de commande, et le runtime Windows PowerShell les appelle également par programme par le biais des API Windows PowerShell.

Pour plus d’informations sur les applets de commande, consultez [écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Fournisseurs Windows PowerShell

Lors de l’exécution de tâches d’administration, l’utilisateur peut avoir besoin d’examiner les données stockées dans un magasin de données (par exemple, le système de fichiers, le Registre Windows ou un magasin de certificats). Pour faciliter ces opérations, Windows PowerShell définit un module appelé fournisseur Windows PowerShell qui peut être utilisé pour accéder à un magasin de données spécifique, tel que le Registre Windows. Chaque fournisseur prend en charge un ensemble d’applets de commande connexes pour fournir à l’utilisateur une vue symétrique des données du magasin.

Windows PowerShell fournit plusieurs fournisseurs Windows PowerShell par défaut. Par exemple, le fournisseur de Registre prend en charge la navigation et la manipulation du Registre Windows. Les clés de Registre sont représentées en tant qu’éléments et les valeurs de Registre sont traitées comme des propriétés.

Si vous exposez un magasin de données auquel l’utilisateur doit accéder, vous devrez peut-être écrire votre propre fournisseur Windows PowerShell, comme décrit dans [création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Pour plus d’informations sur les fournisseurs aboutWindows PowerShell, consultez fonctionnement de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Application hôte

Windows PowerShell comprend l’application hôte par défaut PowerShell. exe, qui est une application console qui interagit avec l’utilisateur et qui héberge le runtime Windows PowerShell à l’aide d’une fenêtre de console.

Il vous suffit rarement d’écrire votre propre application hôte pour Windows PowerShell, bien que la personnalisation soit prise en charge. Si vous avez besoin d’une interface GUI plus riche que l’interface fournie par l’application hôte par défaut, vous pouvez avoir besoin de votre propre application. Vous pouvez également avoir besoin d’une application personnalisée lorsque vous basez votre interface utilisateur graphique sur la ligne de commande. Pour plus d’informations, consultez [comment créer une application hôte Windows PowerShell](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Runtime Windows PowerShell

Le runtime Windows PowerShell est le moteur d’exécution qui implémente le traitement des commandes. Il comprend les classes qui fournissent l’interface entre l’application hôte et les commandes et fournisseurs Windows PowerShell. Le runtime Windows PowerShell est implémenté comme un objet d’instance d’exécution pour la session Windows PowerShell actuelle, qui est l’environnement opérationnel dans lequel l’interpréteur de commandes et les commandes s’exécutent. Pour plus d’informations sur les opérations, consultez fonctionnement de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Langage Windows PowerShell

Le langage Windows PowerShell fournit des fonctions et des mécanismes de script pour appeler des commandes. Pour obtenir des informations complètes sur les scripts, consultez les informations de référence sur le langage Windows PowerShell fournies avec Windows PowerShell.

### <a name="extended-type-system-ets"></a>Système de type étendu (ETS)

Windows PowerShell permet d’accéder à différents objets, tels que les objets .NET et XML. Par conséquent, pour présenter une abstraction commune pour tous les types d’objets, l’interpréteur de commandes utilise son système de type étendu (ETS). La plupart des fonctionnalités ETS sont transparentes pour l’utilisateur, mais le script ou le développeur .NET l’utilise pour les besoins suivants :

- Affichage d’un sous-ensemble des membres d’objets spécifiques. Windows PowerShell fournit une vue « adaptée » de plusieurs types d’objets spécifiques.

- Ajout de membres aux objets existants.

- Accès aux objets sérialisés.

- Écriture d’objets personnalisés.

  À l’aide de ETS, vous pouvez créer de nouveaux « types » flexibles qui sont compatibles avec le langage Windows PowerShell. Si vous êtes un développeur .NET, vous pouvez utiliser des objets à l’aide de la même sémantique que le langage Windows PowerShell s’applique aux scripts, par exemple, pour déterminer si un objet prend la valeur `true`.

  Pour plus d’informations sur ETS et sur la façon dont Windows PowerShell utilise les objets, consultez [concepts relatifs aux objets Windows PowerShell](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programmation pour Windows PowerShell

Windows PowerShell définit son code pour les commandes, les fournisseurs et d’autres modules de programme à l’aide de l' .NET Framework. Vous n’êtes pas limité à l’utilisation de Microsoft Visual Studio lors de la création de modules personnalisés pour Windows PowerShell, bien que les exemples fournis dans ce guide soient connus pour s’exécuter dans cet outil. Vous pouvez utiliser n’importe quel langage .NET qui prend en charge l’héritage de classes et l’utilisation d’attributs. Dans certains cas, les API Windows PowerShell requièrent que le langage de programmation soit en mesure d’accéder aux types génériques.

## <a name="programmers-reference"></a>Guide de référence du programmeur

Pour référence lors du développement pour Windows PowerShell, consultez le [Kit de développement logiciel (SDK) Windows PowerShell](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Prise en main à l’aide de Windows PowerShell

Pour plus d’informations sur le démarrage de l’utilisation de l’interpréteur de commandes Windows PowerShell, consultez la [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) livré avec Windows PowerShell. Un document de référence rapide triple est également fourni comme une introduction à l’utilisation des applets de commande.

## <a name="contents-of-this-guide"></a>Contenu de ce guide

|Rubrique|Définition|
|-----------|----------------|
|[Comment créer un fournisseur Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|Cette section décrit comment créer un fournisseur Windows PowerShell pour Windows PowerShell.|
|[Comment créer une application hôte Windows PowerShell](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)|Cette section décrit comment écrire une application hôte qui manipule une instance d’exécution et comment écrire une application hôte qui implémente son propre hôte personnalisé.|
|[Comment créer un composant logiciel enfichable Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Cette section décrit comment créer un composant logiciel enfichable qui est utilisé pour inscrire toutes les applets de commande et tous les fournisseurs dans un assembly et comment créer un composant logiciel enfichable personnalisé.|
|[Comment créer un interpréteur de commandes de console](./how-to-create-a-console-shell.md)|Cette section décrit comment créer un interpréteur de commandes de console qui n’est pas extensible.|
|[Concepts de Windows PowerShell](./windows-powershell-concepts.md)|Cette section contient des informations conceptuelles qui vous aideront à comprendre Windows PowerShell du point de vue d’un développeur.|

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
