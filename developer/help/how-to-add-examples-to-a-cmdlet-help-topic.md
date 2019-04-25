---
title: Comment ajouter des exemples à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083465"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="dd2e8-102">Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dd2e8-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="dd2e8-103">Choses à savoir à propos des exemples dans l’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dd2e8-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="dd2e8-104">Aide des affichages qui présentent des exemples</span><span class="sxs-lookup"><span data-stu-id="dd2e8-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="dd2e8-105">Ajout d’un nœud d’exemples</span><span class="sxs-lookup"><span data-stu-id="dd2e8-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="dd2e8-106">Ajout de précédant caractères</span><span class="sxs-lookup"><span data-stu-id="dd2e8-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="dd2e8-107">Ajout de la commande</span><span class="sxs-lookup"><span data-stu-id="dd2e8-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="dd2e8-108">Ajout d’une Description</span><span class="sxs-lookup"><span data-stu-id="dd2e8-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="dd2e8-109">Ajout d’exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="dd2e8-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="dd2e8-110">Choses à savoir à propos des exemples dans l’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dd2e8-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="dd2e8-111">Répertorier tous les noms de paramètres dans la commande, même lorsque les noms de paramètres sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="dd2e8-112">Cela permet à l’utilisateur à interpréter facilement de la commande.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="dd2e8-113">Évitez les alias et les noms de paramètre partiel, même si elles fonctionnent dans Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="dd2e8-114">Dans la description de l’exemple, expliquez le raisonnement sous-tendant la construction de la commande.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="dd2e8-115">Expliquer pourquoi vous avez choisi de paramètres bien particuliers et les valeurs, et comment utiliser des variables.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="dd2e8-116">Si la commande utilise des expressions, les expliquer en détail.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="dd2e8-117">Si la commande utilise les propriétés et méthodes des objets, en particulier les propriétés qui n’apparaissent pas dans l’affichage par défaut, utilisez l’exemple comme une opportunité indiquer à l’utilisateur sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="dd2e8-118">Aide des affichages qui présentent des exemples</span><span class="sxs-lookup"><span data-stu-id="dd2e8-118">Help Views that Display Examples</span></span>

<span data-ttu-id="dd2e8-119">Exemples apparaissent uniquement dans les vues détaillé et complet de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="dd2e8-120">Ajout d’un nœud d’exemples</span><span class="sxs-lookup"><span data-stu-id="dd2e8-120">Adding an Examples Node</span></span>

<span data-ttu-id="dd2e8-121">Le code XML suivant montre comment ajouter un nœud d’exemples qui contient un seul nœud de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="dd2e8-122">Ajouter des nœuds d’exemple supplémentaire pour chaque exemples que vous souhaitez inclure dans la rubrique.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="dd2e8-123">Ajout d’un titre d’exemple</span><span class="sxs-lookup"><span data-stu-id="dd2e8-123">Adding an Example Title</span></span>

<span data-ttu-id="dd2e8-124">Le code XML suivant montre comment ajouter un titre pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="dd2e8-125">Le titre est utilisé pour définir l’exemple en dehors d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="dd2e8-126">Windows PowerShell® utilise un en-tête standard qui inclut un numéro séquentiel d’exemple.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="dd2e8-127">Ajout de précédant caractères</span><span class="sxs-lookup"><span data-stu-id="dd2e8-127">Adding Preceding Characters</span></span>

<span data-ttu-id="dd2e8-128">Le code XML suivant montre comment ajouter des caractères, tels que l’invite Windows PowerShell, qui sont affichés immédiatement avant l’exemple de commande (sans espaces insérés).</span><span class="sxs-lookup"><span data-stu-id="dd2e8-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="dd2e8-129">Windows PowerShell® utilise l’invite Windows PowerShell : C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="dd2e8-130">Ajout de la commande</span><span class="sxs-lookup"><span data-stu-id="dd2e8-130">Adding the Command</span></span>

<span data-ttu-id="dd2e8-131">Le code XML suivant montre comment ajouter la commande de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="dd2e8-132">Lorsque vous ajoutez la commande, tapez le nom entier (n’utilisez pas d’alias) des applets de commande et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="dd2e8-133">En outre, utiliser des minuscules autant que possible.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-133">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="dd2e8-134">Ajout d’une Description</span><span class="sxs-lookup"><span data-stu-id="dd2e8-134">Adding a Description</span></span>

<span data-ttu-id="dd2e8-135">Le code XML suivant montre comment ajouter une description pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="dd2e8-136">Windows PowerShell® utilise un ensemble unique de \<maml : para > balises pour la description, même si plusieurs \<maml : para > balises peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="dd2e8-137">Ajout d’exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="dd2e8-137">Adding Example Output</span></span>

<span data-ttu-id="dd2e8-138">Le code XML suivant montre comment ajouter la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="dd2e8-139">Les informations de résultats de la commande sont facultatives, mais dans certains cas, il est utile pour illustrer l’effet de l’utilisation de paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="dd2e8-140">Windows PowerShell® utilise deux ensembles de vide \<maml : para > balises pour séparer la sortie de commande à partir de la commande.</span><span class="sxs-lookup"><span data-stu-id="dd2e8-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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