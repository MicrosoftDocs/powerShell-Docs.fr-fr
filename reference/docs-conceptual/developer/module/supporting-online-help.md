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
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360658"
---
# <a name="supporting-online-help"></a><span data-ttu-id="0d0df-102">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="0d0df-102">Supporting Online Help</span></span>

<span data-ttu-id="0d0df-103">À compter de Windows PowerShell 3,0, il existe deux façons de prendre en charge la fonctionnalité en ligne `Get-Help` pour les commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d0df-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="0d0df-104">Cette rubrique explique comment implémenter cette fonctionnalité pour différents types de commande.</span><span class="sxs-lookup"><span data-stu-id="0d0df-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="0d0df-105">À propos de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="0d0df-105">About Online Help</span></span>

<span data-ttu-id="0d0df-106">L’aide en ligne a toujours été une partie essentielle de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d0df-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="0d0df-107">Bien que l’applet de commande `Get-Help` affiche des rubriques d’aide à l’invite de commandes, de nombreux utilisateurs préfèrent l’expérience de lecture en ligne, notamment le codage de couleurs, les liens hypertexte et le partage d’idées dans le contenu de la communauté et les documents basés sur le wiki.</span><span class="sxs-lookup"><span data-stu-id="0d0df-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="0d0df-108">Plus important encore, avant l’avènement de l’aide actualisable, l’aide en ligne offrait la version la plus récente des fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="0d0df-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="0d0df-109">Avec l’avènement de l’aide actualisable dans Windows PowerShell 3,0, l’aide en ligne joue toujours un rôle vital.</span><span class="sxs-lookup"><span data-stu-id="0d0df-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="0d0df-110">En plus de l’expérience utilisateur flexible, l’aide en ligne fournit de l’aide aux utilisateurs qui ne peuvent pas ou ne peuvent pas utiliser l’aide actualisable pour télécharger des rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="0d0df-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="0d0df-111">Comment obtenir-Help-Online fonctionne</span><span class="sxs-lookup"><span data-stu-id="0d0df-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="0d0df-112">Pour aider les utilisateurs à trouver les rubriques d’aide en ligne pour les commandes, la commande `Get-Help` a un paramètre en ligne qui ouvre la version en ligne de la rubrique d’aide pour une commande dans le navigateur Internet par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d0df-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="0d0df-113">Par exemple, la commande suivante ouvre la rubrique d’aide en ligne de l’applet de commande `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="0d0df-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="0d0df-114">Pour implémenter `Get-Help`-Online, l’applet de commande `Get-Help` recherche une Uniform Resource Identifier (URI) pour la rubrique d’aide de la version en ligne aux emplacements suivants.</span><span class="sxs-lookup"><span data-stu-id="0d0df-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="0d0df-115">Premier lien de la section Liens connexes de la rubrique d’aide de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d0df-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="0d0df-116">La rubrique d’aide doit être installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d0df-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="0d0df-117">Cette fonctionnalité a été introduite dans Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="0d0df-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="0d0df-118">Propriété HelpUri de toute commande.</span><span class="sxs-lookup"><span data-stu-id="0d0df-118">The HelpUri property of any command.</span></span> <span data-ttu-id="0d0df-119">La propriété HelpUri est accessible même lorsque la rubrique d’aide de la commande n’est pas installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d0df-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="0d0df-120">Cette fonctionnalité a été introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0d0df-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="0d0df-121">`Get-Help` recherche un URI dans la première entrée de la section Liens connexes avant d’obtenir la valeur de la propriété HelpUri.</span><span class="sxs-lookup"><span data-stu-id="0d0df-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="0d0df-122">Si la valeur de la propriété est incorrecte ou a changé, vous pouvez la remplacer en entrant une valeur différente dans le premier lien associé.</span><span class="sxs-lookup"><span data-stu-id="0d0df-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="0d0df-123">Toutefois, le premier lien associé fonctionne uniquement lorsque les rubriques d’aide sont installées sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d0df-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="0d0df-124">Ajout d’un URI au premier lien associé d’une rubrique d’aide sur une commande</span><span class="sxs-lookup"><span data-stu-id="0d0df-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="0d0df-125">Vous pouvez prendre en charge `Get-Help`-Online pour n’importe quelle commande en ajoutant un URI valide à la première entrée de la section Liens connexes de la rubrique d’aide XML de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d0df-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="0d0df-126">Cette option est valide uniquement dans les rubriques d’aide XML et fonctionne uniquement lorsque la rubrique d’aide est installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d0df-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="0d0df-127">Lorsque la rubrique d’aide est installée et que l’URI est rempli, cette valeur est prioritaire par rapport à la propriété **HelpUri** de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d0df-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="0d0df-128">Pour prendre en charge cette fonctionnalité, l’URI doit apparaître dans l’élément `maml:uri` sous le premier élément `maml:relatedLinks/maml:navigationLink` dans l’élément `maml:relatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="0d0df-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="0d0df-129">Le code XML suivant montre le positionnement correct de l’URI.</span><span class="sxs-lookup"><span data-stu-id="0d0df-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="0d0df-130">Le texte « version en ligne : » dans l’élément `maml:linkText` est une meilleure pratique, mais il n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0d0df-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="0d0df-131">Ajout de la propriété HelpUri à une commande</span><span class="sxs-lookup"><span data-stu-id="0d0df-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="0d0df-132">Cette section montre comment ajouter la propriété HelpUri à des commandes de types différents.</span><span class="sxs-lookup"><span data-stu-id="0d0df-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="0d0df-133">Ajout d’une propriété HelpUri à une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0d0df-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="0d0df-134">Pour les applets de C#commande écrites dans, ajoutez un attribut **HelpUri** à la classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d0df-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="0d0df-135">La valeur de l’attribut doit être un URI qui commence par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="0d0df-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="0d0df-136">Le code suivant illustre l’attribut HelpUri de la classe d’applet de commande `Get-History`.</span><span class="sxs-lookup"><span data-stu-id="0d0df-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="0d0df-137">Ajout d’une propriété HelpUri à une fonction avancée</span><span class="sxs-lookup"><span data-stu-id="0d0df-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="0d0df-138">Pour fonctions avancées, ajoutez une propriété **HelpUri** à l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="0d0df-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="0d0df-139">La valeur de la propriété doit être un URI qui commence par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="0d0df-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="0d0df-140">Le code suivant illustre l’attribut HelpUri de la fonction New-Calendar</span><span class="sxs-lookup"><span data-stu-id="0d0df-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="0d0df-141">Ajout d’un attribut HelpUri à une commande CIM</span><span class="sxs-lookup"><span data-stu-id="0d0df-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="0d0df-142">Pour les commandes CIM, ajoutez un attribut **HelpUri** à l’élément **CmdletMetadata** dans le fichier CDXML.</span><span class="sxs-lookup"><span data-stu-id="0d0df-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="0d0df-143">La valeur de l’attribut doit être un URI qui commence par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="0d0df-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="0d0df-144">Le code suivant illustre l’attribut HelpUri de la commande CIM Start-Debug.</span><span class="sxs-lookup"><span data-stu-id="0d0df-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="0d0df-145">Ajout d’un attribut HelpUri à un Workflow</span><span class="sxs-lookup"><span data-stu-id="0d0df-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="0d0df-146">Pour les flux de travail écrits dans le langage Windows PowerShell, ajoutez un **. Commentaire ExternalHelp** directive de commentaire au code de Workflow.</span><span class="sxs-lookup"><span data-stu-id="0d0df-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="0d0df-147">La valeur de la directive doit être un URI qui commence par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="0d0df-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="0d0df-148">La propriété HelpUri n’est pas prise en charge pour les flux de travail XAML dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d0df-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="0d0df-149">Le code suivant illustre. Directive commentaire ExternalHelp dans un fichier de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="0d0df-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```