---
title: Comment ajouter des valeurs de retour à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: a5618b72827d8ef70201437c4a99ea8bf68cdfd3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565541"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section OUTPUTs à une rubrique d’aide de l’applet de commande® Windows PowerShell. La section OUTPUTs répertorie les classes .NET des objets que l’applet de commande retourne ou transmet le pipeline.

Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section OUTPUTs. Les types de retour d’une applet de commande sont placés dans une \< commande : returnvalues> nœud, avec chaque classe placée dans un \< élément Command : returnValue>.

Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’y a pas de sortie. Par exemple, à la place du nom de la classe, écrivez « None » et fournissez une brève explication. Si l’applet de commande génère une sortie conditionnelle, utilisez ce nœud pour expliquer les conditions et décrire la sortie conditionnelle.

Le schéma comprend deux \< éléments MAML : description> dans chaque \< commande : returnValue> élément. Toutefois, l' `Get-Help` applet de commande affiche uniquement le contenu de l' \< élément Command : returnValue>/ \< maml : description>.

À compter de Windows PowerShell 3,0, l' `Get-Help` applet de commande affiche le contenu de l' \< élément MAML : URI>. Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.

Le code XML suivant montre le \< nœud MAML : returnvalues>.

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

Le code XML suivant montre un exemple d’utilisation du \< nœud MAML : returnvalues> pour documenter un type de sortie.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
