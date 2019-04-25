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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083431"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="c4c14-102">Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c4c14-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c4c14-103">Cette section décrit comment ajouter une section d’entrées à une rubrique d’aide Windows PowerShell® applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c14-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="c4c14-104">La section entrées répertorie les classes .NET des objets que l’applet de commande accepte comme entrée du pipeline, par valeur ou par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="c4c14-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="c4c14-105">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à une section d’entrées.</span><span class="sxs-lookup"><span data-stu-id="c4c14-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="c4c14-106">Les types d’entrée sont placés entre un \<commande : inputTypes > nœud, avec chaque classe placée entre dans un \<commande : inputType > élément.</span><span class="sxs-lookup"><span data-stu-id="c4c14-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="c4c14-107">Le schéma inclut deux \<maml:description > éléments de chaque \<commande : inputType > élément.</span><span class="sxs-lookup"><span data-stu-id="c4c14-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="c4c14-108">Toutefois, le `Get-Help` applet de commande affiche uniquement le contenu de la \<commande : inputType > /\<maml:description >) élément.</span><span class="sxs-lookup"><span data-stu-id="c4c14-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="c4c14-109">À compter de Windows PowerShell 3.0, le `Get-Help` applet de commande affiche le contenu de la \<maml : URI > élément.</span><span class="sxs-lookup"><span data-stu-id="c4c14-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="c4c14-110">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="c4c14-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="c4c14-111">Le code XML suivant montre la \<maml:inputTypes > nœud.</span><span class="sxs-lookup"><span data-stu-id="c4c14-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="c4c14-112">Le code XML suivant montre un exemple d’utilisation le \<maml:inputTypes > nœud pour documenter un type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c4c14-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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