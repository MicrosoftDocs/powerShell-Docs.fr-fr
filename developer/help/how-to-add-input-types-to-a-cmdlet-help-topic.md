---
title: Comment ajouter des Types d’entrée à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860805"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section d’entrées à une rubrique d’aide Windows PowerShell® applet de commande. La section entrées répertorie les classes .NET des objets que l’applet de commande accepte comme entrée du pipeline, par valeur ou par nom de propriété.

Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à une section d’entrées. Les types d’entrée sont placés entre un \<commande : inputTypes > nœud, avec chaque classe placée entre dans un \<commande : inputType > élément.

Le schéma inclut deux \<maml:description > éléments de chaque \<commande : inputType > élément. Toutefois, le `Get-Help` applet de commande affiche uniquement le contenu de la \<commande : inputType > /\<maml:description >) élément.

À compter de Windows PowerShell 3.0, le `Get-Help` applet de commande affiche le contenu de la \<maml : URI > élément. Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.

Le code XML suivant montre la \<maml:inputTypes > nœud.

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

Le code XML suivant montre un exemple d’utilisation le \<maml:inputTypes > nœud pour documenter un type d’entrée.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```