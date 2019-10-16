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
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367798"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="9a325-102">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="9a325-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="9a325-103">Cette section décrit comment ajouter une section OUTPUTs à une rubrique d’aide de l’applet de commande® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a325-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="9a325-104">La section OUTPUTs répertorie les classes .NET des objets que l’applet de commande retourne ou transmet le pipeline.</span><span class="sxs-lookup"><span data-stu-id="9a325-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="9a325-105">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section OUTPUTs.</span><span class="sxs-lookup"><span data-stu-id="9a325-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="9a325-106">Les types de retour d’une applet de commande sont placés dans un nœud \<command : returnValues >, chaque classe étant placée dans un élément \<command : returnValue >.</span><span class="sxs-lookup"><span data-stu-id="9a325-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="9a325-107">Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="9a325-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="9a325-108">Par exemple, à la place du nom de la classe, écrivez « None » et fournissez une brève explication.</span><span class="sxs-lookup"><span data-stu-id="9a325-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="9a325-109">Si l’applet de commande génère une sortie conditionnelle, utilisez ce nœud pour expliquer les conditions et décrire la sortie conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="9a325-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="9a325-110">Le schéma comprend deux éléments \<maml : Description > dans chaque élément \<command : returnValue >.</span><span class="sxs-lookup"><span data-stu-id="9a325-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="9a325-111">Toutefois, l’applet de commande `Get-Help` affiche uniquement le contenu de l’élément \<command : returnValue >/\<maml : Description >.</span><span class="sxs-lookup"><span data-stu-id="9a325-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="9a325-112">À compter de Windows PowerShell 3,0, l’applet de commande `Get-Help` affiche le contenu de l’élément \<maml : URI >.</span><span class="sxs-lookup"><span data-stu-id="9a325-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="9a325-113">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="9a325-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="9a325-114">Le code XML suivant montre le nœud \<maml : returnValues >.</span><span class="sxs-lookup"><span data-stu-id="9a325-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="9a325-115">Le code XML suivant montre un exemple d’utilisation du nœud \<maml : returnValues > pour documenter un type de sortie.</span><span class="sxs-lookup"><span data-stu-id="9a325-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



