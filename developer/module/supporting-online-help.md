---
title: Prise en charge de l’aide en ligne | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082139"
---
# <a name="supporting-online-help"></a><span data-ttu-id="6d348-102">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="6d348-102">Supporting Online Help</span></span>

<span data-ttu-id="6d348-103">À compter de Windows PowerShell 3.0, il existe deux façons pour prendre en charge la `Get-Help` fonctionnalité en ligne pour les commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d348-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="6d348-104">Cette rubrique explique comment implémenter cette fonctionnalité pour différents types de commandes.</span><span class="sxs-lookup"><span data-stu-id="6d348-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="6d348-105">À propos de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="6d348-105">About Online Help</span></span>

<span data-ttu-id="6d348-106">Aide en ligne a toujours été un élément essentiel de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d348-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="6d348-107">Bien que le `Get-Help` applet de commande affiche les rubriques d’aide à l’invite de commandes, de nombreux utilisateurs préfèrent l’expérience de lecture en ligne, y compris les codes de couleur des liens hypertexte et partage des idées dans le contenu de la Communauté et des documents basés sur le wiki.</span><span class="sxs-lookup"><span data-stu-id="6d348-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="6d348-108">Plus important encore, avant l’arrivée de l’aide actualisable, aide en ligne fournie de la version la plus récente des fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="6d348-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="6d348-109">Avec l’avènement de l’aide actualisable dans Windows PowerShell 3.0, aide en ligne joue un rôle essentiel.</span><span class="sxs-lookup"><span data-stu-id="6d348-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="6d348-110">En plus de l’expérience utilisateur flexible, aide en ligne fournit une aide aux utilisateurs qui ne le faites pas ou ne peut pas utiliser l’aide actualisable pour télécharger les rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="6d348-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="6d348-111">Comment Get-Help-Online-travaux</span><span class="sxs-lookup"><span data-stu-id="6d348-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="6d348-112">Pour aider les utilisateurs à trouver les rubriques d’aide en ligne pour les commandes, le `Get-Help` commande possède un paramètre en ligne qui ouvre la version en ligne de la rubrique d’aide pour une commande dans le navigateur Internet de l’utilisateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6d348-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="6d348-113">Par exemple, la commande suivante ouvre la rubrique d’aide en ligne pour le `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="6d348-114">Pour implémenter `Get-Help` -en ligne, le `Get-Help` applet de commande recherche pour un identificateur URI (Uniform Resource) pour la rubrique d’aide en ligne de version dans les emplacements suivants.</span><span class="sxs-lookup"><span data-stu-id="6d348-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="6d348-115">Le premier lien dans la section liens connexes de la rubrique d’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="6d348-116">La rubrique d’aide doit être installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d348-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="6d348-117">Cette fonctionnalité a été introduite dans Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="6d348-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="6d348-118">La propriété HelpUri de n’importe quelle commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-118">The HelpUri property of any command.</span></span> <span data-ttu-id="6d348-119">La propriété HelpUri est accessible, même lorsque la rubrique d’aide pour la commande n’est pas installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d348-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="6d348-120">Cette fonctionnalité a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="6d348-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="6d348-121">`Get-Help` recherche d’un URI dans la première entrée dans la section liens connexes avant d’obtenir la valeur de la propriété HelpUri.</span><span class="sxs-lookup"><span data-stu-id="6d348-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="6d348-122">Si la valeur de propriété est incorrecte ou a changé, vous pouvez le remplacer en entrant une valeur différente dans le premier lien associé.</span><span class="sxs-lookup"><span data-stu-id="6d348-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="6d348-123">Toutefois, le premier lien associé fonctionne uniquement lorsque les rubriques d’aide sont installés sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d348-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="6d348-124">Ajout d’un URI pour le premier lien associé d’une rubrique d’aide de commande</span><span class="sxs-lookup"><span data-stu-id="6d348-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="6d348-125">Vous pouvez prendre en charge `Get-Help` -Online pour n’importe quelle commande en ajoutant un URI valide à la première entrée dans la section liens connexes de la rubrique d’aide basé sur XML pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="6d348-126">Cette option est valide uniquement dans les rubriques d’aide basé sur XML et ne fonctionne que si la rubrique d’aide est installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d348-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="6d348-127">Lors de la rubrique d’aide est installée et l’URI est remplie, cette valeur est prioritaire sur la **HelpUri** propriété de la commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="6d348-128">Pour plus d’informations sur les rubriques d’aide basé sur XML pour les commandes, consultez [Writing XML-Based rubriques d’aide pour les commandes](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="6d348-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="6d348-129">Pour prendre en charge cette fonctionnalité, l’URI doit apparaître dans le `maml:uri` élément sous le premier `maml:relatedLinks/maml:navigationLink` élément dans le `maml:relatedLinks` élément.</span><span class="sxs-lookup"><span data-stu-id="6d348-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="6d348-130">Le code XML suivant indique le positionnement correct de l’URI.</span><span class="sxs-lookup"><span data-stu-id="6d348-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="6d348-131">La « version en ligne : « texte dans la `maml:linkText` élément est une bonne pratique, mais il n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6d348-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="6d348-132">Ajout de la propriété HelpUri à une commande</span><span class="sxs-lookup"><span data-stu-id="6d348-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="6d348-133">Cette section montre comment ajouter la propriété HelpUri aux commandes de types différents.</span><span class="sxs-lookup"><span data-stu-id="6d348-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="6d348-134">Ajout d’une propriété HelpUri à une applet de commande</span><span class="sxs-lookup"><span data-stu-id="6d348-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="6d348-135">Pour les applets de commande écrite C#, ajoutez un **HelpUri** d’attribut à la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="6d348-136">La valeur de l’attribut doit être un URI qui commence par « http » ou « https ».</span><span class="sxs-lookup"><span data-stu-id="6d348-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="6d348-137">Le code suivant illustre l’attribut HelpUri de la `Get-History` classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6d348-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="6d348-138">Ajout d’une propriété HelpUri à une fonction avancée</span><span class="sxs-lookup"><span data-stu-id="6d348-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="6d348-139">Pour des fonctions avancées, ajoutez un **HelpUri** propriété le **CmdletBinding** attribut.</span><span class="sxs-lookup"><span data-stu-id="6d348-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="6d348-140">La valeur de la propriété doit être un URI qui commence par « http » ou « https ».</span><span class="sxs-lookup"><span data-stu-id="6d348-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="6d348-141">Le code suivant illustre l’attribut HelpUri de la fonction New-calendrier</span><span class="sxs-lookup"><span data-stu-id="6d348-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="6d348-142">Ajout d’un attribut HelpUri à une commande CIM</span><span class="sxs-lookup"><span data-stu-id="6d348-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="6d348-143">Pour les commandes CIM, ajoutez un **HelpUri** attribut le **CmdletMetadata** élément dans le fichier CDXML.</span><span class="sxs-lookup"><span data-stu-id="6d348-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="6d348-144">La valeur de l’attribut doit être un URI qui commence par « http » ou « https ».</span><span class="sxs-lookup"><span data-stu-id="6d348-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="6d348-145">Le code suivant illustre l’attribut HelpUri de la commande Start-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="6d348-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="6d348-146">Ajout d’un attribut HelpUri à un flux de travail</span><span class="sxs-lookup"><span data-stu-id="6d348-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="6d348-147">Pour les workflows qui sont écrits dans le langage Windows PowerShell, ajoutez un **. ExternalHelp** directive de commentaire pour le code de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6d348-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="6d348-148">La valeur de la directive doit être un URI qui commence par « http » ou « https ».</span><span class="sxs-lookup"><span data-stu-id="6d348-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="6d348-149">La propriété HelpUri n’est pas pris en charge pour les flux de travail basé sur XAML dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d348-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="6d348-150">Le code suivant montre le. Directive ExternalHelp dans un fichier de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6d348-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```