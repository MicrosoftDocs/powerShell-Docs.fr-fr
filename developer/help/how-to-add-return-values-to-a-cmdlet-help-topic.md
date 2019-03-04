---
title: Comment ajouter le retour des valeurs à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859435"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section des sorties à une rubrique d’aide Windows PowerShell® applet de commande. La section des sorties répertorie les classes .NET d’objets que l’applet de commande renvoie ou transmet dans le pipeline.

Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section des sorties. Les types de retour d’une applet de commande sont placés entre un \<commande : returnValues > nœud, avec chaque classe placée entre dans un \<commande : returnValue > élément.

Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’existe aucune sortie. Par exemple, à la place le nom de classe, écrire « None » et fournissent une brève explication. Si l’applet de commande génère une sortie de manière conditionnelle, utilisez ce nœud pour expliquer les conditions et de décrire la sortie conditionnelle.

Le schéma inclut deux \<maml:description > éléments de chaque \<commande : returnValue > élément. Toutefois, le `Get-Help` applet de commande affiche uniquement le contenu de la \<commande : returnValue > /\<maml:description > élément.

À compter de Windows PowerShell 3.0, le `Get-Help` applet de commande affiche le contenu de la \<maml : URI > élément. Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.

Le code XML suivant montre la \<maml:returnValues > nœud.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

Le code XML suivant montre un exemple d’utilisation le \<maml:returnValues > nœud pour documenter un type de sortie.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



