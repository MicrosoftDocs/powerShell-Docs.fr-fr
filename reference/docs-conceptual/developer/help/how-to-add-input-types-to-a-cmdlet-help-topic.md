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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="bac36-103">Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="bac36-103">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="bac36-104">Cette section décrit comment ajouter une section d' **entrées** à une rubrique d’aide d’une applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bac36-104">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="bac36-105">La section des **entrées** répertorie les classes .net d’objets que l’applet de commande accepte comme entrée du pipeline, par valeur ou par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="bac36-105">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="bac36-106">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à une section d' **entrées** .</span><span class="sxs-lookup"><span data-stu-id="bac36-106">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="bac36-107">Les types d’entrée sont placés dans un `<command:inputTypes>` nœud, chaque classe étant placée dans un `<command:inputType>` élément.</span><span class="sxs-lookup"><span data-stu-id="bac36-107">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="bac36-108">Le schéma comprend deux `<maml:description>` éléments dans chaque `<command:inputType>` élément.</span><span class="sxs-lookup"><span data-stu-id="bac36-108">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="bac36-109">Toutefois, l' `Get-Help` applet de commande affiche uniquement le contenu de l' `<command:inputType>/<maml:description>` élément.</span><span class="sxs-lookup"><span data-stu-id="bac36-109">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="bac36-110">À compter de PowerShell 3,0, l' `Get-Help` applet de commande affiche le contenu de l' `<maml:uri>` élément.</span><span class="sxs-lookup"><span data-stu-id="bac36-110">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="bac36-111">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="bac36-111">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="bac36-112">Le code XML suivant montre le `<maml:inputTypes>` nœud.</span><span class="sxs-lookup"><span data-stu-id="bac36-112">The following XML shows the `<maml:inputTypes>` node.</span></span>

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

<span data-ttu-id="bac36-113">Le code XML suivant montre un exemple d’utilisation du `<maml:inputTypes>` nœud pour documenter un type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bac36-113">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

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
