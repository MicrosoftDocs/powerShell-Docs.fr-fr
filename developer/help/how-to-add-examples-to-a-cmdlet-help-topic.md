---
title: Comment ajouter des exemples à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855128"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Choses à savoir à propos des exemples dans l’aide de l’applet de commande

- Répertorier tous les noms de paramètres dans la commande, même lorsque les noms de paramètres sont facultatifs. Cela permet à l’utilisateur à interpréter facilement de la commande.

- Évitez les alias et les noms de paramètre partiel, même si elles fonctionnent dans Windows PowerShell®.

- Dans la description de l’exemple, expliquez le raisonnement sous-tendant la construction de la commande. Expliquer pourquoi vous avez choisi de paramètres bien particuliers et les valeurs, et comment utiliser des variables.

- Si la commande utilise des expressions, les expliquer en détail.

- Si la commande utilise les propriétés et méthodes des objets, en particulier les propriétés qui n’apparaissent pas dans l’affichage par défaut, utilisez l’exemple comme une opportunité indiquer à l’utilisateur sur l’objet.

## <a name="help-views-that-display-examples"></a>Aide des affichages qui présentent des exemples

Exemples apparaissent uniquement dans les vues détaillé et complet de l’aide de l’applet de commande.

## <a name="adding-an-examples-node"></a>Ajout d’un nœud d’exemples

Le code XML suivant montre comment ajouter un nœud d’exemples qui contient un seul nœud de l’exemple. Ajouter des nœuds d’exemple supplémentaire pour chaque exemples que vous souhaitez inclure dans la rubrique.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Ajout d’un titre d’exemple

Le code XML suivant montre comment ajouter un titre pour l’exemple. Le titre est utilisé pour définir l’exemple en dehors d’autres exemples. Windows PowerShell® utilise un en-tête standard qui inclut un numéro séquentiel d’exemple.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Ajout de précédant caractères

Le code XML suivant montre comment ajouter des caractères, tels que l’invite Windows PowerShell, qui sont affichés immédiatement avant l’exemple de commande (sans espaces insérés). Windows PowerShell® utilise l’invite Windows PowerShell : C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Ajout de la commande

Le code XML suivant montre comment ajouter la commande de l’exemple. Lorsque vous ajoutez la commande, tapez le nom entier (n’utilisez pas d’alias) des applets de commande et des paramètres. En outre, utiliser des minuscules autant que possible.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Ajout d’une Description

Le code XML suivant montre comment ajouter une description pour l’exemple. Windows PowerShell® utilise un ensemble unique de \<maml : para > balises pour la description, même si plusieurs \<maml : para > balises peuvent être utilisées.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Ajout d’exemple de sortie

Le code XML suivant montre comment ajouter la sortie de la commande. Les informations de résultats de la commande sont facultatives, mais dans certains cas, il est utile pour illustrer l’effet de l’utilisation de paramètres spécifiques. Windows PowerShell® utilise deux ensembles de vide \<maml : para > balises pour séparer la sortie de commande à partir de la commande.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```