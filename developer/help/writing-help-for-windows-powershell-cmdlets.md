---
title: Écriture de l’aide des applets de commande PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083159"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="c6b30-102">Aide d’écriture pour les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6b30-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="c6b30-103">Applets de commande PowerShell peut être utile, mais à moins que vos rubriques d’aide expliquer clairement ce que fait l’applet de commande et comment l’utiliser, l’applet de commande ne peut pas utilisé ou, pire encore, il peut nuire aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c6b30-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="c6b30-104">Le format de fichier d’aide applet de commande basé sur XML améliore la cohérence, mais une aide précieuse nécessite beaucoup plus.</span><span class="sxs-lookup"><span data-stu-id="c6b30-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="c6b30-105">Si vous n’avez jamais écrit aide de l’applet de commande, passez en revue les instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="c6b30-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="c6b30-106">Le schéma XML requis pour créer la rubrique d’aide de l’applet de commande est décrite dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="c6b30-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="c6b30-107">Démarrer avec [création du fichier d’aide de l’applet de commande](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="c6b30-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="c6b30-108">Cette rubrique inclut une description des nœuds XML de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="c6b30-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="c6b30-109">Guides de l’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="c6b30-110">Écrire</span><span class="sxs-lookup"><span data-stu-id="c6b30-110">Write well</span></span>
<span data-ttu-id="c6b30-111">Rien ne remplace une rubrique bien écrite.</span><span class="sxs-lookup"><span data-stu-id="c6b30-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="c6b30-112">Si vous n’êtes pas un rédacteur professionnel, trouver un enregistreur ou un éditeur pour vous aider à.</span><span class="sxs-lookup"><span data-stu-id="c6b30-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="c6b30-113">Une autre solution consiste à copier votre texte d’aide dans Microsoft Word et à utiliser la grammaire et orthographe vérifie pour améliorer votre travail.</span><span class="sxs-lookup"><span data-stu-id="c6b30-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="c6b30-114">Écrire simplement</span><span class="sxs-lookup"><span data-stu-id="c6b30-114">Write simply</span></span>
<span data-ttu-id="c6b30-115">Utiliser des expressions et les mots simples.</span><span class="sxs-lookup"><span data-stu-id="c6b30-115">Use simple words and phrases.</span></span>
<span data-ttu-id="c6b30-116">Éviter le jargon.</span><span class="sxs-lookup"><span data-stu-id="c6b30-116">Avoid jargon.</span></span>
<span data-ttu-id="c6b30-117">Prendre en compte que de nombreux lecteurs sont équipés uniquement un dictionnaire de langue étrangère et votre rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="c6b30-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="c6b30-118">Écrire de manière cohérente</span><span class="sxs-lookup"><span data-stu-id="c6b30-118">Write consistently</span></span>
<span data-ttu-id="c6b30-119">L’aide d’applets de commande associées doivent être similaires (par exemple, x-get et set-x).</span><span class="sxs-lookup"><span data-stu-id="c6b30-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="c6b30-120">Utiliser les descriptions standards pour les paramètres standard, comme **Force** et **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="c6b30-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="c6b30-121">(Les copier à partir de l’aide pour les applets de commande core.) Utilisez des termes standards.</span><span class="sxs-lookup"><span data-stu-id="c6b30-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="c6b30-122">Par exemple, utilisez « paramètre », pas « argument », utilisez « cmdlet » pas « commande » ou « applet de commande. »</span><span class="sxs-lookup"><span data-stu-id="c6b30-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="c6b30-123">Démarrer le synopsis avec un verbe</span><span class="sxs-lookup"><span data-stu-id="c6b30-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="c6b30-124">Le champ synopsis informe l’utilisateur quel l’applet de commande ne, il est ni son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="c6b30-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="c6b30-125">Verbes créez une instruction basé sur des tâches qui informe les utilisateurs si cette applet de commande répond à leurs besoins.</span><span class="sxs-lookup"><span data-stu-id="c6b30-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="c6b30-126">Utiliser des verbes simples comme « get », « créer » et « modifier ».</span><span class="sxs-lookup"><span data-stu-id="c6b30-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="c6b30-127">Évitez de « set », ce qui peut être vagues et fantaisistes mots comme « modifier ».</span><span class="sxs-lookup"><span data-stu-id="c6b30-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="c6b30-128">Vous concentrer sur des objets</span><span class="sxs-lookup"><span data-stu-id="c6b30-128">Focus on objects</span></span>
<span data-ttu-id="c6b30-129">La plupart « get » complet d’applets de commande quelque chose, mais leur fonction principale consiste à obtenir un objet.</span><span class="sxs-lookup"><span data-stu-id="c6b30-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="c6b30-130">Dans votre aide, de vous concentrer sur l’objet, afin que les utilisateurs comprennent que l’affichage par défaut est un des nombreux et qu’ils peuvent utiliser les méthodes et propriétés de l’objet que vous avez récupérées pour eux de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="c6b30-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="c6b30-131">Écrire une description détaillée</span><span class="sxs-lookup"><span data-stu-id="c6b30-131">Write detailed descriptions</span></span>
<span data-ttu-id="c6b30-132">Mentionner rapidement tout ce que l’applet de commande peut faire dans la description détaillée.</span><span class="sxs-lookup"><span data-stu-id="c6b30-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="c6b30-133">Si la fonction principale consiste à modifier une propriété, mais l’applet de commande peut modifier toutes les propriétés, liste cela dans la description détaillée.</span><span class="sxs-lookup"><span data-stu-id="c6b30-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="c6b30-134">Utilisez la syntaxe classique</span><span class="sxs-lookup"><span data-stu-id="c6b30-134">Use conventional syntax</span></span>
<span data-ttu-id="c6b30-135">Utilisez le format Backus-Naur standard, ce qui est courant pour Windows et de l’aide en ligne de commande UNIX.</span><span class="sxs-lookup"><span data-stu-id="c6b30-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="c6b30-136">Utiliser des types Microsoft .NET Framework pour les valeurs de paramètre</span><span class="sxs-lookup"><span data-stu-id="c6b30-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="c6b30-137">Les espaces réservés pour les valeurs de paramètre (dans les descriptions de syntaxe et les paramètres) affichent les types .NET Framework des objets qui accepte le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c6b30-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="c6b30-138">L’équipe PowerShell développé cette convention pour aider à apprendre aux utilisateurs sur le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6b30-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="c6b30-139">Écrire des descriptions de paramètre complet</span><span class="sxs-lookup"><span data-stu-id="c6b30-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="c6b30-140">Descriptions de paramètres doivent informer les utilisateurs de deux choses : le paramètre ne (son effet) et ils doivent taper les valeurs des paramètres.</span><span class="sxs-lookup"><span data-stu-id="c6b30-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="c6b30-141">Écrire des exemples concrets</span><span class="sxs-lookup"><span data-stu-id="c6b30-141">Write practical examples</span></span>
<span data-ttu-id="c6b30-142">Les exemples doivent afficher l’utilisation de tous les paramètres, mais le plus important est de montrer comment utiliser l’applet de commande dans les tâches réelles.</span><span class="sxs-lookup"><span data-stu-id="c6b30-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="c6b30-143">Démarrez avec un exemple simple et écrire des exemples de plus en plus complexes.</span><span class="sxs-lookup"><span data-stu-id="c6b30-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="c6b30-144">Dans l’exemple final, montrent comment utiliser l’applet de commande dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="c6b30-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="c6b30-145">Utilisez le champ Notes</span><span class="sxs-lookup"><span data-stu-id="c6b30-145">Use the Notes field</span></span>
<span data-ttu-id="c6b30-146">Utilisez le champ Notes pour expliquer les concepts que les utilisateurs doivent comprendre l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c6b30-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="c6b30-147">Vous pouvez également utiliser des notes pour aider les utilisateurs à éviter les erreurs courantes.</span><span class="sxs-lookup"><span data-stu-id="c6b30-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="c6b30-148">Évitez d’URL comme elles changent.</span><span class="sxs-lookup"><span data-stu-id="c6b30-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="c6b30-149">Au lieu de cela, fournissez de termes à rechercher les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c6b30-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="c6b30-150">Tester votre aide</span><span class="sxs-lookup"><span data-stu-id="c6b30-150">Test your Help</span></span>
<span data-ttu-id="c6b30-151">L’aide de test comme vous tester votre code.</span><span class="sxs-lookup"><span data-stu-id="c6b30-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="c6b30-152">Avez des amis et collègues lire votre contenu d’aide et de fournissent des commentaires.</span><span class="sxs-lookup"><span data-stu-id="c6b30-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="c6b30-153">Vous pouvez également recueillir les commentaires des groupes de discussion.</span><span class="sxs-lookup"><span data-stu-id="c6b30-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6b30-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6b30-154">See Also</span></span>

 [<span data-ttu-id="c6b30-155">Comment créer le fichier d’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="c6b30-156">Comment ajouter le nom de l’applet de commande et le Synopsis à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-157">Comment ajouter la Description détaillée à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="c6b30-158">Comment ajouter la syntaxe pour une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-159">Comment ajouter des paramètres à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="c6b30-160">Comment ajouter des Types d’entrée à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-161">Comment ajouter des valeurs de retour à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-162">Comment ajouter des Notes à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-163">Comment ajouter des exemples à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-164">Comment ajouter des liens connexes à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6b30-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c6b30-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c6b30-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)