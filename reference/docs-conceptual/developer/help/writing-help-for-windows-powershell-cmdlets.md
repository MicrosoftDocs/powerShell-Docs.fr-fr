---
title: Écriture de l’aide pour les applets de commande PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361068"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="dfc23-102">Écriture de l’aide pour les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfc23-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="dfc23-103">Les applets de commande PowerShell peuvent être utiles, mais à moins que vos rubriques d’aide n’expliquent clairement ce que fait l’applet de commande et comment l’utiliser, l’applet de commande peut ne pas être utilisée ou, pire encore, elle risque de nuire aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dfc23-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="dfc23-104">Le format de fichier d’aide sur les applets de commande XML améliore la cohérence, mais une grande partie de l’aide est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dfc23-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="dfc23-105">Si vous n’avez jamais écrit l’aide sur les applets de commande, passez en revue les instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="dfc23-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="dfc23-106">Le schéma XML requis pour créer la rubrique d’aide de l’applet de commande est décrit dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="dfc23-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="dfc23-107">Commencez par [créer le fichier d’aide de l’applet](./how-to-create-the-cmdlet-help-file.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="dfc23-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="dfc23-108">Cette rubrique contient une description des nœuds XML de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="dfc23-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="dfc23-109">Écriture des instructions pour l’aide sur les applets de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="dfc23-110">Écrire correctement</span><span class="sxs-lookup"><span data-stu-id="dfc23-110">Write well</span></span>
<span data-ttu-id="dfc23-111">Rien ne remplace un sujet bien écrit.</span><span class="sxs-lookup"><span data-stu-id="dfc23-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="dfc23-112">Si vous n’êtes pas un éditeur professionnel, recherchez un enregistreur ou un éditeur pour vous aider.</span><span class="sxs-lookup"><span data-stu-id="dfc23-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="dfc23-113">Une autre solution consiste à copier votre texte d’aide dans Microsoft Word et à utiliser la grammaire et l’orthographe pour améliorer votre travail.</span><span class="sxs-lookup"><span data-stu-id="dfc23-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="dfc23-114">Écrire simplement</span><span class="sxs-lookup"><span data-stu-id="dfc23-114">Write simply</span></span>
<span data-ttu-id="dfc23-115">Utilisez des mots et des expressions simples.</span><span class="sxs-lookup"><span data-stu-id="dfc23-115">Use simple words and phrases.</span></span>
<span data-ttu-id="dfc23-116">Évitez le jargon.</span><span class="sxs-lookup"><span data-stu-id="dfc23-116">Avoid jargon.</span></span>
<span data-ttu-id="dfc23-117">Supposons que de nombreux lecteurs disposent uniquement d’un dictionnaire de langue étrangère et de votre rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="dfc23-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="dfc23-118">Écrire de manière cohérente</span><span class="sxs-lookup"><span data-stu-id="dfc23-118">Write consistently</span></span>
<span data-ttu-id="dfc23-119">L’aide sur les applets de commande associées doit être similaire (par exemple, obtenir-x et Set-x).</span><span class="sxs-lookup"><span data-stu-id="dfc23-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="dfc23-120">Utilisez les descriptions standard pour les paramètres standard, par exemple **force** et **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="dfc23-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="dfc23-121">(Copiez-les à partir de l’aide pour les applets de commande de base.) Utilisez les termes standard.</span><span class="sxs-lookup"><span data-stu-id="dfc23-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="dfc23-122">Par exemple, utilisez « Parameter », et non « argument », et utilisez « applet de commande » et non « Command » ou « Command-Let ».</span><span class="sxs-lookup"><span data-stu-id="dfc23-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="dfc23-123">Démarrer le synopsis avec un verbe</span><span class="sxs-lookup"><span data-stu-id="dfc23-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="dfc23-124">Le champ Synopsis informe l’utilisateur de ce que fait l’applet de commande, et non de son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="dfc23-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="dfc23-125">Les verbes créent une instruction basée sur les tâches qui informe les utilisateurs si cette applet de commande répond à leurs exigences.</span><span class="sxs-lookup"><span data-stu-id="dfc23-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="dfc23-126">Utilisez des verbes simples tels que « obten », « Create » et « change ».</span><span class="sxs-lookup"><span data-stu-id="dfc23-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="dfc23-127">Évitez « Set », qui peut être vague et fantaisie comme « Modify ».</span><span class="sxs-lookup"><span data-stu-id="dfc23-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="dfc23-128">Focus sur les objets</span><span class="sxs-lookup"><span data-stu-id="dfc23-128">Focus on objects</span></span>
<span data-ttu-id="dfc23-129">La plupart des applets de commande « obtenir » affichent un objet, mais leur fonction principale consiste à obtenir un objet.</span><span class="sxs-lookup"><span data-stu-id="dfc23-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="dfc23-130">Dans votre aide, concentrez-vous sur l’objet afin que les utilisateurs sachent que l’affichage par défaut est l’un des nombreux et qu’ils peuvent utiliser les méthodes et propriétés de l’objet que vous avez récupéré pour eux de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="dfc23-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="dfc23-131">Écrire des descriptions détaillées</span><span class="sxs-lookup"><span data-stu-id="dfc23-131">Write detailed descriptions</span></span>
<span data-ttu-id="dfc23-132">Répertoriez brièvement tout ce que l’applet de commande peut faire dans la description détaillée.</span><span class="sxs-lookup"><span data-stu-id="dfc23-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="dfc23-133">Si la fonction principale consiste à modifier une propriété, mais que l’applet de commande peut modifier toutes les propriétés, répertoriez-la dans la description détaillée.</span><span class="sxs-lookup"><span data-stu-id="dfc23-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="dfc23-134">Utiliser la syntaxe conventionnelle</span><span class="sxs-lookup"><span data-stu-id="dfc23-134">Use conventional syntax</span></span>
<span data-ttu-id="dfc23-135">Utilisez le format Backus-Naur standard qui est courant pour l’aide de la ligne de commande Windows et UNIX.</span><span class="sxs-lookup"><span data-stu-id="dfc23-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="dfc23-136">Utiliser des types de Microsoft .NET Framework pour les valeurs de paramètres</span><span class="sxs-lookup"><span data-stu-id="dfc23-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="dfc23-137">Les espaces réservés pour les valeurs de paramètres (dans la syntaxe et les descriptions de paramètres) affichent les types de .NET Framework des objets que le paramètre acceptera.</span><span class="sxs-lookup"><span data-stu-id="dfc23-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="dfc23-138">L’équipe PowerShell a développé cette Convention pour aider les utilisateurs à se familiariser avec les .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dfc23-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="dfc23-139">Écrire les descriptions des paramètres complets</span><span class="sxs-lookup"><span data-stu-id="dfc23-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="dfc23-140">Les descriptions des paramètres doivent informer les utilisateurs de deux choses : ce que fait le paramètre (son effet) et ce qu’il doit taper pour les valeurs de paramètres.</span><span class="sxs-lookup"><span data-stu-id="dfc23-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="dfc23-141">Écrire des exemples pratiques</span><span class="sxs-lookup"><span data-stu-id="dfc23-141">Write practical examples</span></span>
<span data-ttu-id="dfc23-142">Les exemples doivent montrer comment utiliser tous les paramètres, mais l’élément le plus important consiste à montrer comment utiliser l’applet de commande dans des tâches réelles.</span><span class="sxs-lookup"><span data-stu-id="dfc23-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="dfc23-143">Commencez par un exemple simple et écrivez des exemples de plus en plus complexes.</span><span class="sxs-lookup"><span data-stu-id="dfc23-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="dfc23-144">Dans l’exemple final, montrez comment utiliser l’applet de commande dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="dfc23-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="dfc23-145">Utiliser le champ Remarques</span><span class="sxs-lookup"><span data-stu-id="dfc23-145">Use the Notes field</span></span>
<span data-ttu-id="dfc23-146">Utilisez le champ Remarques pour expliquer les concepts dont les utilisateurs ont besoin pour comprendre l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dfc23-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="dfc23-147">Vous pouvez également utiliser des notes pour aider les utilisateurs à éviter les erreurs courantes.</span><span class="sxs-lookup"><span data-stu-id="dfc23-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="dfc23-148">Évitez les URL au fur et à mesure qu’elles changent.</span><span class="sxs-lookup"><span data-stu-id="dfc23-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="dfc23-149">Au lieu de cela, indiquez aux utilisateurs les termes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="dfc23-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="dfc23-150">Tester votre aide</span><span class="sxs-lookup"><span data-stu-id="dfc23-150">Test your Help</span></span>
<span data-ttu-id="dfc23-151">Testez l’aide de la même façon que vous testez votre code.</span><span class="sxs-lookup"><span data-stu-id="dfc23-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="dfc23-152">Demander aux amis et collègues de lire le contenu de l’aide et de fournir des commentaires.</span><span class="sxs-lookup"><span data-stu-id="dfc23-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="dfc23-153">Vous pouvez également solliciter des commentaires à partir de groupes de discussion.</span><span class="sxs-lookup"><span data-stu-id="dfc23-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfc23-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfc23-154">See Also</span></span>

 [<span data-ttu-id="dfc23-155">Comment créer le fichier d’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="dfc23-156">Comment ajouter le nom de l’applet de commande et synopsis à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-157">Comment ajouter la description détaillée à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="dfc23-158">Guide pratique pour ajouter une syntaxe à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-159">Comment ajouter des paramètres à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="dfc23-160">Comment ajouter des types d’entrée à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-161">Comment ajouter des valeurs de retour à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-162">Comment ajouter des notes à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-163">Comment ajouter des exemples à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-164">Comment ajouter des liens connexes à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dfc23-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dfc23-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dfc23-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)