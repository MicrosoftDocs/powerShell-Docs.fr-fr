---
title: Guide pratique pour ajouter des exemples à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368108"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="15209-102">Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="15209-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="15209-103">Éléments à connaître sur les exemples de l’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="15209-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="15209-104">Répertorie tous les noms de paramètres dans la commande, même si les noms de paramètres sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="15209-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="15209-105">Cela permet à l’utilisateur d’interpréter facilement la commande.</span><span class="sxs-lookup"><span data-stu-id="15209-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="15209-106">Évitez les alias et les noms de paramètres partiels, même s’ils fonctionnent dans Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="15209-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="15209-107">Dans l’exemple de description, expliquez le raisonnement pour la construction de la commande.</span><span class="sxs-lookup"><span data-stu-id="15209-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="15209-108">Expliquez pourquoi vous avez choisi des paramètres et des valeurs particuliers et comment utiliser des variables.</span><span class="sxs-lookup"><span data-stu-id="15209-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="15209-109">Si la commande utilise des expressions, expliquez-les en détail.</span><span class="sxs-lookup"><span data-stu-id="15209-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="15209-110">Si la commande utilise des propriétés et des méthodes d’objets, en particulier les propriétés qui n’apparaissent pas dans l’affichage par défaut, utilisez l’exemple comme une opportunité pour indiquer à l’utilisateur l’objet.</span><span class="sxs-lookup"><span data-stu-id="15209-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="15209-111">Vues d’aide qui affichent des exemples</span><span class="sxs-lookup"><span data-stu-id="15209-111">Help Views that Display Examples</span></span>

<span data-ttu-id="15209-112">Les exemples apparaissent uniquement dans les vues détaillées et complètes de l’aide sur les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="15209-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="15209-113">Ajout d’un nœud exemples</span><span class="sxs-lookup"><span data-stu-id="15209-113">Adding an Examples Node</span></span>

<span data-ttu-id="15209-114">Le code XML suivant montre comment ajouter un nœud exemples qui contient un seul nœud exemple.</span><span class="sxs-lookup"><span data-stu-id="15209-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="15209-115">Ajoutez des exemples de nœuds supplémentaires pour chaque exemple que vous souhaitez inclure dans la rubrique.</span><span class="sxs-lookup"><span data-stu-id="15209-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="15209-116">Ajout d’un titre d’exemple</span><span class="sxs-lookup"><span data-stu-id="15209-116">Adding an Example Title</span></span>

<span data-ttu-id="15209-117">Le code XML suivant montre comment ajouter un titre pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="15209-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="15209-118">Le titre est utilisé pour définir l’exemple, à l’exception des autres exemples.</span><span class="sxs-lookup"><span data-stu-id="15209-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="15209-119">Windows PowerShell® utilise un en-tête standard qui comprend un numéro d’exemple séquentiel.</span><span class="sxs-lookup"><span data-stu-id="15209-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="15209-120">Ajout de caractères précédents</span><span class="sxs-lookup"><span data-stu-id="15209-120">Adding Preceding Characters</span></span>

<span data-ttu-id="15209-121">Le code XML suivant montre comment ajouter des caractères, tels que l’invite de commandes Windows PowerShell, qui sont affichés immédiatement avant l’exemple de commande (sans espaces intermédiaires).</span><span class="sxs-lookup"><span data-stu-id="15209-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="15209-122">Windows PowerShell® utilise l’invite de commandes Windows PowerShell : C:\PS >.</span><span class="sxs-lookup"><span data-stu-id="15209-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="15209-123">Ajout de la commande</span><span class="sxs-lookup"><span data-stu-id="15209-123">Adding the Command</span></span>

<span data-ttu-id="15209-124">Le code XML suivant montre comment ajouter la commande réelle de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="15209-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="15209-125">Lorsque vous ajoutez la commande, tapez le nom complet (n’utilisez pas d’alias) des applets de commande et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="15209-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="15209-126">En outre, utilisez des caractères minuscules dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="15209-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="15209-127">Ajout d’une description</span><span class="sxs-lookup"><span data-stu-id="15209-127">Adding a Description</span></span>

<span data-ttu-id="15209-128">Le code XML suivant montre comment ajouter une description pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="15209-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="15209-129">Windows PowerShell® utilise un ensemble unique de balises \<maml : para > pour la description, même si plusieurs balises \<maml : para > peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="15209-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="15209-130">Ajout d’un exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="15209-130">Adding Example Output</span></span>

<span data-ttu-id="15209-131">Le code XML suivant montre comment ajouter la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="15209-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="15209-132">Les informations sur les résultats de la commande sont facultatives, mais dans certains cas, il est utile d’illustrer l’effet de l’utilisation de paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="15209-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="15209-133">Windows PowerShell® utilise deux ensembles de balises \<maml : para > vides pour séparer la sortie de commande de la commande.</span><span class="sxs-lookup"><span data-stu-id="15209-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```