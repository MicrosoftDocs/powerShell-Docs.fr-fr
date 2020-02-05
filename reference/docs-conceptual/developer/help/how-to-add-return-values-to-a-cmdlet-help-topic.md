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
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995928"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="ebf31-102">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="ebf31-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="ebf31-103">Cette section décrit comment ajouter une section OUTPUTs à une rubrique d’aide de l’applet de commande® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebf31-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="ebf31-104">La section OUTPUTs répertorie les classes .NET des objets que l’applet de commande retourne ou transmet le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebf31-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="ebf31-105">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section OUTPUTs.</span><span class="sxs-lookup"><span data-stu-id="ebf31-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="ebf31-106">Les types de retour d’une applet de commande sont placés dans une commande \<: returnValues > nœud, chaque classe comprise dans une commande \<: returnValue > élément.</span><span class="sxs-lookup"><span data-stu-id="ebf31-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="ebf31-107">Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="ebf31-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="ebf31-108">Par exemple, à la place du nom de la classe, écrivez « None » et fournissez une brève explication.</span><span class="sxs-lookup"><span data-stu-id="ebf31-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="ebf31-109">Si l’applet de commande génère une sortie conditionnelle, utilisez ce nœud pour expliquer les conditions et décrire la sortie conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="ebf31-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="ebf31-110">Le schéma comprend deux \<MAML : Description > éléments dans chaque \<commande : returnValue > élément.</span><span class="sxs-lookup"><span data-stu-id="ebf31-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="ebf31-111">Toutefois, l’applet de commande `Get-Help` affiche uniquement le contenu de l’élément Command \<: returnValue >/\<MAML : Description >.</span><span class="sxs-lookup"><span data-stu-id="ebf31-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="ebf31-112">À compter de Windows PowerShell 3,0, l’applet de commande `Get-Help` affiche le contenu de l’élément \<MAML : URI >.</span><span class="sxs-lookup"><span data-stu-id="ebf31-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="ebf31-113">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="ebf31-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="ebf31-114">Le code XML suivant montre le nœud \<MAML : returnValues >.</span><span class="sxs-lookup"><span data-stu-id="ebf31-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="ebf31-115">Le code XML suivant montre un exemple d’utilisation du nœud \<MAML : returnValues > pour documenter un type de sortie.</span><span class="sxs-lookup"><span data-stu-id="ebf31-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



