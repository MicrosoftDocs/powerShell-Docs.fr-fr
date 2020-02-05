---
title: Guide pratique pour ajouter des types d’entrée à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: 37af16d0279b6487c78f90eb19bcfe5c152ed9e7
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996055"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section d’entrées à une rubrique d’aide de l’applet de commande® Windows PowerShell. La section des entrées répertorie les classes .NET d’objets que l’applet de commande accepte comme entrée du pipeline, par valeur ou par nom de propriété.

Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à une section d’entrées. Les types d’entrée sont placés dans un \<commande : inputTypes > nœud, avec chaque classe placée dans une commande \<: inputType > élément.

Le schéma comprend deux \<MAML : Description > éléments dans chaque \<commande : inputType > élément. Toutefois, l’applet de commande `Get-Help` affiche uniquement le contenu de l’élément Command \<: inputType >/\<MAML : Description >).

À compter de Windows PowerShell 3,0, l’applet de commande `Get-Help` affiche le contenu de l’élément \<MAML : URI >. Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.

Le code XML suivant montre le nœud \<MAML : inputTypes >.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Le code XML suivant montre un exemple d’utilisation du nœud \<MAML : inputTypes > pour documenter un type d’entrée.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```