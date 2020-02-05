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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="ad43a-102">Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="ad43a-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="ad43a-103">Cette section décrit comment ajouter une section d’entrées à une rubrique d’aide de l’applet de commande® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad43a-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="ad43a-104">La section des entrées répertorie les classes .NET d’objets que l’applet de commande accepte comme entrée du pipeline, par valeur ou par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="ad43a-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="ad43a-105">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à une section d’entrées.</span><span class="sxs-lookup"><span data-stu-id="ad43a-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="ad43a-106">Les types d’entrée sont placés dans un \<commande : inputTypes > nœud, avec chaque classe placée dans une commande \<: inputType > élément.</span><span class="sxs-lookup"><span data-stu-id="ad43a-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="ad43a-107">Le schéma comprend deux \<MAML : Description > éléments dans chaque \<commande : inputType > élément.</span><span class="sxs-lookup"><span data-stu-id="ad43a-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="ad43a-108">Toutefois, l’applet de commande `Get-Help` affiche uniquement le contenu de l’élément Command \<: inputType >/\<MAML : Description >).</span><span class="sxs-lookup"><span data-stu-id="ad43a-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="ad43a-109">À compter de Windows PowerShell 3,0, l’applet de commande `Get-Help` affiche le contenu de l’élément \<MAML : URI >.</span><span class="sxs-lookup"><span data-stu-id="ad43a-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="ad43a-110">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="ad43a-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="ad43a-111">Le code XML suivant montre le nœud \<MAML : inputTypes >.</span><span class="sxs-lookup"><span data-stu-id="ad43a-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="ad43a-112">Le code XML suivant montre un exemple d’utilisation du nœud \<MAML : inputTypes > pour documenter un type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ad43a-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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