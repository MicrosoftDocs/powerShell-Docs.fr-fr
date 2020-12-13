---
ms.date: 07/09/2020
ms.topic: reference
title: Vue d’ensemble du système de type étendu
description: Vue d’ensemble du système de type étendu
ms.openlocfilehash: f4a789f779fa8a52f0fe524abff7ec3311e93b6c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655726"
---
# <a name="extended-type-system-overview"></a>Vue d’ensemble du système de type étendu

PowerShell utilise son objet **PSObject** pour étendre les types d’objets de deux manières. Tout d’abord, l’objet **PSObject** offre un moyen d’afficher différentes vues de types d’objets spécifiques. Cela s’appelle l’affichage d’une vue adaptée d’un objet. Deuxièmement, l’objet **PSObject** offre un moyen d’ajouter des membres à un objet existant. Ensemble, en encapsulant un objet existant, appelé objet de base, l’objet **PSObject** fournit un système de type étendu (ETS) que les développeurs de scripts et d’applets de commande peuvent utiliser pour manipuler des objets .net dans l’interpréteur de commandes.

## <a name="cmdlet-and-script-development-issues"></a>Problèmes de développement des applets de commande et des scripts

ETS résout deux problèmes fondamentaux :

Tout d’abord, certains objets .NET n’ont pas le comportement par défaut nécessaire pour agir en tant que données entre les applets de commande.

- Certains objets .NET sont des objets « méta » (par exemple : objets WMI, objets ADO et objets XML) dont les membres décrivent les données qu’ils contiennent. Toutefois, dans un environnement de script, il s’agit des données contenues qui sont les plus intéressantes, et non pas de la description des données contenues. ETS résout ce problème en introduisant la notion d’adaptateurs qui adaptent l’objet .NET sous-jacent pour avoir la sémantique par défaut attendue.
- Certains membres de l’objet .NET sont nommés de manière incohérente, fournissent un ensemble insuffisant de membres publics ou fournissent une capacité insuffisante. ETS résout ce problème en introduisant la possibilité d’étendre l’objet .NET avec des membres supplémentaires.

Deuxièmement, le langage de script PowerShell est sans _type_ dans le fait qu’une variable n’a pas besoin d’être déclarée d’un type particulier. Autrement dit, les variables créées par un développeur de script sont de nature non _typée_. Toutefois, le système PowerShell est « piloté par type », car il dépend d’un nom de type pour les opérations de base, telles que la génération de résultats ou le tri.

Par conséquent, un développeur de script doit avoir la possibilité d’indiquer le type de l’une de ses variables et de créer son propre jeu d’objets de type dynamique qui contiennent des propriétés et des méthodes et qui peuvent participer au système piloté par type. ETS résout ce problème en fournissant un objet commun pour le langage de script qui a la capacité d’indiquer dynamiquement son type et d’ajouter des membres de manière dynamique.

Fondamentalement, ETS résout le problème mentionné précédemment en fournissant l’objet **PSObject** , qui joue le rôle de base de tous les accès aux objets à partir du langage de script et fournit une abstraction standard pour le développeur d’applets de commande.

### <a name="cmdlet-developers"></a>Développeurs d’applets de commande

Pour les développeurs d’applets de commande, ETS offre la prise en charge suivante :

- Les abstractions pour travailler sur des objets de façon générique à l’aide de l’objet **PSObject** . ETS offre également la possibilité d’effectuer des recherches au-delà de ces abstractions si nécessaire.
- Mécanismes permettant de créer un comportement par défaut pour la mise en forme, le tri, la sérialisation et d’autres manipulations système de leur type d’objet à l’aide d’un ensemble bien connu de membres étendus.
- Le moyen de faire face à n’importe quel objet utilisant la même sémantique que le langage de script à l’aide d’un objet LanguagePrimitives.
- La méthode consiste à « taper » de manière dynamique une table de hachage afin que le reste du système puisse agir efficacement.

### <a name="script-developers"></a>Développeurs de scripts

Pour les développeurs de script, ETS offre la prise en charge suivante :

- La possibilité de référencer n’importe quel type d’objet sous-jacent à l’aide de la même syntaxe ( `$a.x` ).
- La possibilité d’accéder au-delà de l’abstraction fournie par l’objet **PSObject** (comme l’accès aux seuls membres adaptés, ou l’accès à l’objet de base lui-même).
- Possibilité de définir des membres connus qui contrôlent la mise en forme, le tri, la sérialisation et d’autres manipulations d’une instance d’objet ou d’un type.
- Le signifie que vous nommez un objet en tant que type spécifique et que vous contrôlez ainsi l’héritage de ses membres basés sur le type.
- La possibilité d’ajouter, de supprimer et de modifier des membres étendus.
- La possibilité de manipuler l’objet **PSObject** lui-même, si nécessaire.

## <a name="the-psobject-class"></a>Classe PSObject

L’objet **PSObject** est la base de tous les accès aux objets à partir du langage de script et fournit une abstraction standard pour le développeur d’applets de commande. Elle contient un objet de base (un objet .NET) et tous les membres d’instance (membres, plus particulièrement les membres étendus) qui sont présents sur une instance d’objet particulière, mais pas nécessairement sur d’autres objets du même type. Selon le type de l’objet de base, l’objet **PSObject** peut également fournir un accès implicite et explicite aux membres adaptés, ainsi qu’à tous les membres étendus basés sur un type.

L’objet **PSObject** fournit les mécanismes suivants :

- Possibilité de construire un **PSObject** avec ou sans objet de base.
- La possibilité d’accéder à tous les membres de chaque objet **PSObject** construit par le biais d’un algorithme de recherche commun et de la possibilité de substituer cet algorithme quand cela est nécessaire.
- Capacité à récupérer et à définir les noms des objets **PSObject** construits afin que les scripts et les applets de commande puissent faire référence à des objets **PSObject** similaires par le même nom de type, quel que soit le type de leur objet de base.

### <a name="how-to-construct-a-psobject"></a>Comment construire un PSObject

La liste suivante décrit les façons de créer un objet **PSObject** :

- L’appel du constructeur **PSObject** . #ctor crée un nouvel objet **PSObject** avec un objet de base de PSCustomObject. Un objet de base de ce type indique que l’objet **PSObject** n’a aucun objet de base significatif. Toutefois, un objet **PSObject** avec ce type d’objet de base fournit un jeu de propriétés que les développeurs d’applets de commande peuvent trouver utiles en ajoutant des membres étendus.

Les développeurs peuvent également spécifier le nom du type d’objet, ce qui permet à cet objet de partager ses membres étendus avec d’autres objets **PSObject** du même type-nom.

- L’appel du constructeur **PSObject** . #ctor (System. Object) crée un nouvel objet **PSObject** avec un objet de base de type System. Object.

  Dans ce cas, le nom de type de l’objet créé est une collection de la hiérarchie de dérivation de l’objet de base. Par exemple, le nom de type pour le **PSObject** qui contient un objet de base ProcessInfo inclut les noms suivants :

  - System.Diagnostics.Process
  - System. ComponentModel. Component
  - System.MarshalByRefObject
  - System.Object

- Appel du **PSObject** . La méthode AsPSObject (System. Object) crée un nouvel objet **PSObject** basé sur un objet fourni.

  Si l’objet fourni est de type System. Object, l’objet fourni est utilisé comme objet de base pour le nouvel objet **PSObject** . Si l’objet fourni est déjà un objet **PSObject** , l’objet fourni est retourné tel quel.

### <a name="base-adapted-and-extended-members"></a>Membres de base, adaptés et étendu

Conceptuellement, ETS utilise les termes suivants pour afficher la relation entre les membres d’origine de l’objet de base et les membres ajoutés par PowerShell. Pour plus d’informations sur les types de membres spécifiques qui sont utilisés par l’objet **PSObject** , consultez [PSObject, classe](/dotnet/api/system.management.automation.psobject).

#### <a name="base-object-members"></a>Membres de l’objet de base

Si l’objet de base est spécifié lors de la construction des objets **PSObject** , les membres de l’objet de base sont rendus disponibles par le biais de la propriété Members.

#### <a name="adapted-members"></a>Membres adaptés

Lorsqu’un objet de base est un méta-objet, qui contient des données d’une manière générique dont les propriétés décrivent les données qu’ils contiennent, ETS adapte ces objets à une vue qui permet un accès direct aux données via des membres adaptés de l’objet **PSObject** . Les membres adaptés et les membres d’objet de base sont accessibles par le biais de la propriété Members.

#### <a name="extended-members"></a>Membres étendus

En plus des membres rendus disponibles à partir de l’objet de base ou des membres adaptés créés par PowerShell, un **PSObject** peut également définir des membres étendus qui étendent l’objet de base d’origine avec des informations supplémentaires qui sont utiles dans l’environnement de script.

Par exemple, toutes les applets de commande principales fournies par PowerShell, telles que les applets de commande Get-Content et Set-Content, acceptent un paramètre Path. Pour vous assurer que ces applets de commande, et d’autres, peuvent fonctionner sur des objets de types différents, un membre de chemin d’accès peut être ajouté à ces objets afin qu’ils aient tous l’état de leurs informations de manière courante. Ce membre du chemin d’accès étendu garantit que les applets de commande peuvent fonctionner sur tous ces types, même si une classe de base peut ne pas avoir de membre de chemin d’accès.

Les membres étendus, les membres adaptés et les membres d’objet de base sont accessibles via la propriété Members.
