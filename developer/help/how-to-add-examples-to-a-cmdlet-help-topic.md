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
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855128"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="d5462-102">Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d5462-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="d5462-103">Choses à savoir à propos des exemples dans l’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d5462-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="d5462-104">Répertorier tous les noms de paramètres dans la commande, même lorsque les noms de paramètres sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="d5462-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="d5462-105">Cela permet à l’utilisateur à interpréter facilement de la commande.</span><span class="sxs-lookup"><span data-stu-id="d5462-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="d5462-106">Évitez les alias et les noms de paramètre partiel, même si elles fonctionnent dans Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="d5462-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="d5462-107">Dans la description de l’exemple, expliquez le raisonnement sous-tendant la construction de la commande.</span><span class="sxs-lookup"><span data-stu-id="d5462-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="d5462-108">Expliquer pourquoi vous avez choisi de paramètres bien particuliers et les valeurs, et comment utiliser des variables.</span><span class="sxs-lookup"><span data-stu-id="d5462-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="d5462-109">Si la commande utilise des expressions, les expliquer en détail.</span><span class="sxs-lookup"><span data-stu-id="d5462-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="d5462-110">Si la commande utilise les propriétés et méthodes des objets, en particulier les propriétés qui n’apparaissent pas dans l’affichage par défaut, utilisez l’exemple comme une opportunité indiquer à l’utilisateur sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="d5462-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="d5462-111">Aide des affichages qui présentent des exemples</span><span class="sxs-lookup"><span data-stu-id="d5462-111">Help Views that Display Examples</span></span>

<span data-ttu-id="d5462-112">Exemples apparaissent uniquement dans les vues détaillé et complet de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d5462-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="d5462-113">Ajout d’un nœud d’exemples</span><span class="sxs-lookup"><span data-stu-id="d5462-113">Adding an Examples Node</span></span>

<span data-ttu-id="d5462-114">Le code XML suivant montre comment ajouter un nœud d’exemples qui contient un seul nœud de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d5462-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="d5462-115">Ajouter des nœuds d’exemple supplémentaire pour chaque exemples que vous souhaitez inclure dans la rubrique.</span><span class="sxs-lookup"><span data-stu-id="d5462-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="d5462-116">Ajout d’un titre d’exemple</span><span class="sxs-lookup"><span data-stu-id="d5462-116">Adding an Example Title</span></span>

<span data-ttu-id="d5462-117">Le code XML suivant montre comment ajouter un titre pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d5462-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="d5462-118">Le titre est utilisé pour définir l’exemple en dehors d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="d5462-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="d5462-119">Windows PowerShell® utilise un en-tête standard qui inclut un numéro séquentiel d’exemple.</span><span class="sxs-lookup"><span data-stu-id="d5462-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="d5462-120">Ajout de précédant caractères</span><span class="sxs-lookup"><span data-stu-id="d5462-120">Adding Preceding Characters</span></span>

<span data-ttu-id="d5462-121">Le code XML suivant montre comment ajouter des caractères, tels que l’invite Windows PowerShell, qui sont affichés immédiatement avant l’exemple de commande (sans espaces insérés).</span><span class="sxs-lookup"><span data-stu-id="d5462-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="d5462-122">Windows PowerShell® utilise l’invite Windows PowerShell : C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="d5462-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="d5462-123">Ajout de la commande</span><span class="sxs-lookup"><span data-stu-id="d5462-123">Adding the Command</span></span>

<span data-ttu-id="d5462-124">Le code XML suivant montre comment ajouter la commande de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d5462-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="d5462-125">Lorsque vous ajoutez la commande, tapez le nom entier (n’utilisez pas d’alias) des applets de commande et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="d5462-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="d5462-126">En outre, utiliser des minuscules autant que possible.</span><span class="sxs-lookup"><span data-stu-id="d5462-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="d5462-127">Ajout d’une Description</span><span class="sxs-lookup"><span data-stu-id="d5462-127">Adding a Description</span></span>

<span data-ttu-id="d5462-128">Le code XML suivant montre comment ajouter une description pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d5462-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="d5462-129">Windows PowerShell® utilise un ensemble unique de \<maml : para > balises pour la description, même si plusieurs \<maml : para > balises peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="d5462-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="d5462-130">Ajout d’exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="d5462-130">Adding Example Output</span></span>

<span data-ttu-id="d5462-131">Le code XML suivant montre comment ajouter la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="d5462-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="d5462-132">Les informations de résultats de la commande sont facultatives, mais dans certains cas, il est utile pour illustrer l’effet de l’utilisation de paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d5462-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="d5462-133">Windows PowerShell® utilise deux ensembles de vide \<maml : para > balises pour séparer la sortie de commande à partir de la commande.</span><span class="sxs-lookup"><span data-stu-id="d5462-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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