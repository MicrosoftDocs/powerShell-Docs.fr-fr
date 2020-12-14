---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande
ms.openlocfilehash: 8c556821a257451a320916231cb20fc82e75ebb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94389740"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section OUTPUTs à une rubrique d’aide sur une applet de commande PowerShell. La section **Outputs** répertorie les classes .net des objets que l’applet de commande retourne ou transmet le pipeline.

Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section **Outputs** . Les types de retour d’une applet de commande sont placés dans un `<command:returnValues>` nœud, chaque classe étant placée dans un `<command:returnValue>` élément.

Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’y a pas de sortie. Par exemple, à la place du nom de la classe, écrivez **aucun** et fournissez une brève explication. Si l’applet de commande génère une sortie conditionnelle, utilisez ce nœud pour expliquer les conditions et décrire la sortie conditionnelle.

Le schéma comprend deux `<maml:description>` éléments dans chaque `<command:returnValue>` élément.
Toutefois, l' `Get-Help` applet de commande affiche uniquement le contenu de l' `<command:returnValue>/<maml:description>` élément.

À compter de PowerShell 3,0, l' `Get-Help` applet de commande affiche le contenu de l' `<maml:uri>` élément.
Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.

Le code XML suivant montre le `<maml:returnValues>` nœud.

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

Le code XML suivant montre un exemple d’utilisation du `<maml:returnValues>` nœud pour documenter un type de sortie.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://docs.microsoft.com/dotnet/api/system.datetime </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
