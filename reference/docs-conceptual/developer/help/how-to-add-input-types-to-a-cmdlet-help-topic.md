---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande
ms.openlocfilehash: f2ad87c54230bcdd7e0ea708e9a1869daef7495f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391100"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter une section d' **entrées** à une rubrique d’aide d’une applet de commande PowerShell. La section des **entrées** répertorie les classes .net d’objets que l’applet de commande accepte comme entrée du pipeline, par valeur ou par nom de propriété.

Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à une section d' **entrées** . Les types d’entrée sont placés dans un `<command:inputTypes>` nœud, chaque classe étant placée dans un `<command:inputType>` élément.

Le schéma comprend deux `<maml:description>` éléments dans chaque `<command:inputType>` élément.
Toutefois, l' `Get-Help` applet de commande affiche uniquement le contenu de l' `<command:inputType>/<maml:description>` élément.

À compter de PowerShell 3,0, l' `Get-Help` applet de commande affiche le contenu de l' `<maml:uri>` élément.
Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.

Le code XML suivant montre le `<maml:inputTypes>` nœud.

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

Le code XML suivant montre un exemple d’utilisation du `<maml:inputTypes>` nœud pour documenter un type d’entrée.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name>System.DateTime</maml:name>
      <maml:uri>https://docs.microsoft.com/dotnet/api/system.datetime</maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
