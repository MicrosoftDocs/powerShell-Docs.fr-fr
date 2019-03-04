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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="07813-102">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="07813-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="07813-103">Cette section décrit comment ajouter une section des sorties à une rubrique d’aide Windows PowerShell® applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07813-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="07813-104">La section des sorties répertorie les classes .NET d’objets que l’applet de commande renvoie ou transmet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="07813-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="07813-105">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section des sorties.</span><span class="sxs-lookup"><span data-stu-id="07813-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="07813-106">Les types de retour d’une applet de commande sont placés entre un \<commande : returnValues > nœud, avec chaque classe placée entre dans un \<commande : returnValue > élément.</span><span class="sxs-lookup"><span data-stu-id="07813-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="07813-107">Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’existe aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="07813-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="07813-108">Par exemple, à la place le nom de classe, écrire « None » et fournissent une brève explication.</span><span class="sxs-lookup"><span data-stu-id="07813-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="07813-109">Si l’applet de commande génère une sortie de manière conditionnelle, utilisez ce nœud pour expliquer les conditions et de décrire la sortie conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="07813-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="07813-110">Le schéma inclut deux \<maml:description > éléments de chaque \<commande : returnValue > élément.</span><span class="sxs-lookup"><span data-stu-id="07813-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="07813-111">Toutefois, le `Get-Help` applet de commande affiche uniquement le contenu de la \<commande : returnValue > /\<maml:description > élément.</span><span class="sxs-lookup"><span data-stu-id="07813-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="07813-112">À compter de Windows PowerShell 3.0, le `Get-Help` applet de commande affiche le contenu de la \<maml : URI > élément.</span><span class="sxs-lookup"><span data-stu-id="07813-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="07813-113">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="07813-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="07813-114">Le code XML suivant montre la \<maml:returnValues > nœud.</span><span class="sxs-lookup"><span data-stu-id="07813-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="07813-115">Le code XML suivant montre un exemple d’utilisation le \<maml:returnValues > nœud pour documenter un type de sortie.</span><span class="sxs-lookup"><span data-stu-id="07813-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



