---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande
ms.openlocfilehash: 8c556821a257451a320916231cb20fc82e75ebb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94389740"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="4f951-103">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="4f951-103">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="4f951-104">Cette section décrit comment ajouter une section OUTPUTs à une rubrique d’aide sur une applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f951-104">This section describes how to add an OUTPUTS section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="4f951-105">La section **Outputs** répertorie les classes .net des objets que l’applet de commande retourne ou transmet le pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f951-105">The **OUTPUTS** section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="4f951-106">Il n’existe aucune limite au nombre de classes que vous pouvez ajouter à la section **Outputs** .</span><span class="sxs-lookup"><span data-stu-id="4f951-106">There is no limit to the number of classes that you can add to the **OUTPUTS** section.</span></span> <span data-ttu-id="4f951-107">Les types de retour d’une applet de commande sont placés dans un `<command:returnValues>` nœud, chaque classe étant placée dans un `<command:returnValue>` élément.</span><span class="sxs-lookup"><span data-stu-id="4f951-107">The return types of a cmdlet are enclosed in a `<command:returnValues>` node, with each class enclosed in a `<command:returnValue>` element.</span></span>

<span data-ttu-id="4f951-108">Si une applet de commande ne génère pas de sortie, utilisez cette section pour indiquer qu’il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="4f951-108">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="4f951-109">Par exemple, à la place du nom de la classe, écrivez **aucun** et fournissez une brève explication.</span><span class="sxs-lookup"><span data-stu-id="4f951-109">For example, in place of the class name, write **None** and provide a brief explanation.</span></span> <span data-ttu-id="4f951-110">Si l’applet de commande génère une sortie conditionnelle, utilisez ce nœud pour expliquer les conditions et décrire la sortie conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="4f951-110">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="4f951-111">Le schéma comprend deux `<maml:description>` éléments dans chaque `<command:returnValue>` élément.</span><span class="sxs-lookup"><span data-stu-id="4f951-111">The schema includes two `<maml:description>` elements in each `<command:returnValue>` element.</span></span>
<span data-ttu-id="4f951-112">Toutefois, l' `Get-Help` applet de commande affiche uniquement le contenu de l' `<command:returnValue>/<maml:description>` élément.</span><span class="sxs-lookup"><span data-stu-id="4f951-112">However, the `Get-Help` cmdlet displays only the content of the `<command:returnValue>/<maml:description>` element.</span></span>

<span data-ttu-id="4f951-113">À compter de PowerShell 3,0, l' `Get-Help` applet de commande affiche le contenu de l' `<maml:uri>` élément.</span><span class="sxs-lookup"><span data-stu-id="4f951-113">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="4f951-114">Cet élément vous permet de diriger les utilisateurs vers des rubriques qui décrivent la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="4f951-114">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="4f951-115">Le code XML suivant montre le `<maml:returnValues>` nœud.</span><span class="sxs-lookup"><span data-stu-id="4f951-115">The following XML shows the `<maml:returnValues>` node.</span></span>

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

<span data-ttu-id="4f951-116">Le code XML suivant montre un exemple d’utilisation du `<maml:returnValues>` nœud pour documenter un type de sortie.</span><span class="sxs-lookup"><span data-stu-id="4f951-116">The following XML shows an example of using the `<maml:returnValues>` node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://docs.microsoft.com/dotnet/api/system.datetime </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
