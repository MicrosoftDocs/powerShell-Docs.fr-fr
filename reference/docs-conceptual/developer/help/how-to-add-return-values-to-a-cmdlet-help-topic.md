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
ms.openlocfilehash: a5618b72827d8ef70201437c4a99ea8bf68cdfd3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565541"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="5fca6-102">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="5fca6-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="5fca6-103">Cette section décrit comment ajouter une section OUTPUTs à une rubrique d’aide de l’applet de commande® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fca6-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="5fca6-104">La section OUTPUTs répertorie les classes .NET des objets que l’applet de commande retourne ou transmet le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5fca6-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="5fca6-105">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section OUTPUTs.</span><span class="sxs-lookup"><span data-stu-id="5fca6-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="5fca6-106">Les types de retour d’une applet de commande sont placés dans une \< commande : returnvalues> nœud, avec chaque classe placée dans un \< élément Command : returnValue>.</span><span class="sxs-lookup"><span data-stu-id="5fca6-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="5fca6-107">Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="5fca6-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="5fca6-108">Par exemple, à la place du nom de la classe, écrivez « None » et fournissez une brève explication.</span><span class="sxs-lookup"><span data-stu-id="5fca6-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="5fca6-109">Si l’applet de commande génère une sortie conditionnelle, utilisez ce nœud pour expliquer les conditions et décrire la sortie conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="5fca6-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="5fca6-110">Le schéma comprend deux \< éléments MAML : description> dans chaque \< commande : returnValue> élément.</span><span class="sxs-lookup"><span data-stu-id="5fca6-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="5fca6-111">Toutefois, l' `Get-Help` applet de commande affiche uniquement le contenu de l' \< élément Command : returnValue>/ \< maml : description>.</span><span class="sxs-lookup"><span data-stu-id="5fca6-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="5fca6-112">À compter de Windows PowerShell 3,0, l' `Get-Help` applet de commande affiche le contenu de l' \< élément MAML : URI>.</span><span class="sxs-lookup"><span data-stu-id="5fca6-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="5fca6-113">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="5fca6-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="5fca6-114">Le code XML suivant montre le \< nœud MAML : returnvalues>.</span><span class="sxs-lookup"><span data-stu-id="5fca6-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="5fca6-115">Le code XML suivant montre un exemple d’utilisation du \< nœud MAML : returnvalues> pour documenter un type de sortie.</span><span class="sxs-lookup"><span data-stu-id="5fca6-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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
