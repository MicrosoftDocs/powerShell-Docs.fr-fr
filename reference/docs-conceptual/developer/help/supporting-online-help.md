---
ms.date: 09/13/2016
ms.topic: reference
title: Prise en charge de l’aide en ligne
description: Prise en charge de l’aide en ligne
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645425"
---
# <a name="supporting-online-help"></a><span data-ttu-id="a22e0-103">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="a22e0-103">Supporting Online Help</span></span>

<span data-ttu-id="a22e0-104">À compter de PowerShell 3,0, il existe deux façons de prendre en charge la `Get-Help` fonctionnalité en ligne pour les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a22e0-104">Beginning in PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for PowerShell commands.</span></span> <span data-ttu-id="a22e0-105">Cette rubrique explique comment implémenter cette fonctionnalité pour différents types de commande.</span><span class="sxs-lookup"><span data-stu-id="a22e0-105">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="a22e0-106">À propos de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="a22e0-106">About Online Help</span></span>

<span data-ttu-id="a22e0-107">L’aide en ligne a toujours été une partie essentielle de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a22e0-107">Online help has always been a vital part of PowerShell.</span></span> <span data-ttu-id="a22e0-108">Bien que l' `Get-Help` applet de commande affiche les rubriques d’aide à l’invite de commandes, de nombreux utilisateurs préfèrent l’expérience de lecture en ligne, notamment le codage de couleurs, les liens hypertexte et le partage d’idées dans le contenu de la communauté et les documents wiki.</span><span class="sxs-lookup"><span data-stu-id="a22e0-108">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="a22e0-109">Plus important encore, avant l’avènement de l’aide actualisable, l’aide en ligne offrait la version la plus récente des fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="a22e0-109">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="a22e0-110">Avec l’avènement de l’aide actualisable dans PowerShell 3,0, l’aide en ligne joue toujours un rôle vital.</span><span class="sxs-lookup"><span data-stu-id="a22e0-110">With the advent of Updatable Help in PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="a22e0-111">En plus de l’expérience utilisateur flexible, l’aide en ligne fournit de l’aide aux utilisateurs qui ne peuvent pas ou ne peuvent pas utiliser l’aide actualisable pour télécharger des rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="a22e0-111">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="a22e0-112">Fonctionnement de Get-Help-Online</span><span class="sxs-lookup"><span data-stu-id="a22e0-112">How Get-Help -Online Works</span></span>

<span data-ttu-id="a22e0-113">Pour aider les utilisateurs à trouver les rubriques d’aide en ligne pour les commandes, la `Get-Help` commande dispose d’un paramètre en ligne qui ouvre la version en ligne de la rubrique d’aide pour une commande dans le navigateur Internet par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a22e0-113">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default internet browser.</span></span>

<span data-ttu-id="a22e0-114">Par exemple, la commande suivante ouvre la rubrique d’aide en ligne de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="a22e0-114">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="a22e0-115">Pour implémenter `Get-Help -Online` , l' `Get-Help` applet de commande recherche une Uniform Resource Identifier (Uri) pour la rubrique d’aide de la version en ligne aux emplacements suivants.</span><span class="sxs-lookup"><span data-stu-id="a22e0-115">To implement `Get-Help -Online`, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="a22e0-116">Premier lien de la section **liens connexes** de la rubrique d’aide de la commande.</span><span class="sxs-lookup"><span data-stu-id="a22e0-116">The first link in the **Related Links** section of the help topic for the command.</span></span> <span data-ttu-id="a22e0-117">La rubrique d’aide doit être installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a22e0-117">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="a22e0-118">Cette fonctionnalité a été introduite dans PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a22e0-118">This feature was introduced in PowerShell 2.0.</span></span>

- <span data-ttu-id="a22e0-119">Propriété **HelpUri** de toute commande.</span><span class="sxs-lookup"><span data-stu-id="a22e0-119">The **HelpUri** property of any command.</span></span> <span data-ttu-id="a22e0-120">La propriété **HelpUri** est accessible même lorsque la rubrique d’aide de la commande n’est pas installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a22e0-120">The **HelpUri** property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="a22e0-121">Cette fonctionnalité a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a22e0-121">This feature was introduced in PowerShell 3.0.</span></span>

  <span data-ttu-id="a22e0-122">`Get-Help` recherche un URI dans la première entrée de la section **liens connexes** avant d’obtenir la valeur de la propriété **HelpUri** .</span><span class="sxs-lookup"><span data-stu-id="a22e0-122">`Get-Help` looks for a URI in the first entry in the **Related Links** section before getting the **HelpUri** property value.</span></span> <span data-ttu-id="a22e0-123">Si la valeur de la propriété est incorrecte ou a changé, vous pouvez la remplacer en entrant une valeur différente dans le premier lien associé.</span><span class="sxs-lookup"><span data-stu-id="a22e0-123">If the property value is incorrect or has changed, you can override it by entering a different value in the first related link.</span></span> <span data-ttu-id="a22e0-124">Toutefois, le premier lien associé fonctionne uniquement lorsque les rubriques d’aide sont installées sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a22e0-124">However, the first related link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="a22e0-125">Ajout d’un URI au premier lien associé d’une rubrique d’aide sur une commande</span><span class="sxs-lookup"><span data-stu-id="a22e0-125">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="a22e0-126">Vous pouvez prendre en charge `Get-Help -Online` n’importe quelle commande en ajoutant un URI valide à la première entrée de la section **liens connexes** de la rubrique d’aide XML de la commande.</span><span class="sxs-lookup"><span data-stu-id="a22e0-126">You can support `Get-Help -Online` for any command by adding a valid URI to the first entry in the **Related Links** section of the XML-based help topic for the command.</span></span> <span data-ttu-id="a22e0-127">Cette option est valide uniquement dans les rubriques d’aide XML et fonctionne uniquement lorsque la rubrique d’aide est installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a22e0-127">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="a22e0-128">Lorsque la rubrique d’aide est installée et que l’URI est rempli, cette valeur est prioritaire par rapport à la propriété **HelpUri** de la commande.</span><span class="sxs-lookup"><span data-stu-id="a22e0-128">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="a22e0-129">Pour prendre en charge cette fonctionnalité, l’URI doit apparaître dans l' `maml:uri` élément sous le premier `maml:relatedLinks/maml:navigationLink` élément de l' `maml:relatedLinks` élément.</span><span class="sxs-lookup"><span data-stu-id="a22e0-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="a22e0-130">Le code XML suivant montre le positionnement correct de l’URI.</span><span class="sxs-lookup"><span data-stu-id="a22e0-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="a22e0-131">Le `Online version:` texte de l' `maml:linkText` élément est une meilleure pratique, mais il n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a22e0-131">The `Online version:` text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml
<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="a22e0-132">Ajout de la propriété HelpUri à une commande</span><span class="sxs-lookup"><span data-stu-id="a22e0-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="a22e0-133">Cette section montre comment ajouter la propriété HelpUri à des commandes de types différents.</span><span class="sxs-lookup"><span data-stu-id="a22e0-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="a22e0-134">Ajout d’une propriété HelpUri à une applet de commande</span><span class="sxs-lookup"><span data-stu-id="a22e0-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="a22e0-135">Pour les applets de commande écrites en C#, ajoutez un attribut **HelpUri** à la classe **cmdlet** .</span><span class="sxs-lookup"><span data-stu-id="a22e0-135">For cmdlets written in C#, add a **HelpUri** attribute to the **Cmdlet** class.</span></span> <span data-ttu-id="a22e0-136">La valeur de l’attribut doit être un URI qui commence par `http` ou `https` .</span><span class="sxs-lookup"><span data-stu-id="a22e0-136">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="a22e0-137">Le code suivant illustre l’attribut **HelpUri** de la `Get-History` classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a22e0-137">The following code shows the **HelpUri** attribute of the `Get-History` cmdlet class.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="a22e0-138">Ajout d’une propriété HelpUri à une fonction avancée</span><span class="sxs-lookup"><span data-stu-id="a22e0-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="a22e0-139">Pour fonctions avancées, ajoutez une propriété **HelpUri** à l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="a22e0-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="a22e0-140">La valeur de la propriété doit être un URI qui commence par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="a22e0-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="a22e0-141">Le code suivant illustre l’attribut **HelpUri** de la `New-Calendar` fonction.</span><span class="sxs-lookup"><span data-stu-id="a22e0-141">The following code shows the **HelpUri** attribute of the `New-Calendar` function</span></span>

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="a22e0-142">Ajout d’un attribut HelpUri à une commande CIM</span><span class="sxs-lookup"><span data-stu-id="a22e0-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="a22e0-143">Pour les commandes CIM, ajoutez un attribut **HelpUri** à l’élément **CmdletMetadata** dans le fichier CDXML.</span><span class="sxs-lookup"><span data-stu-id="a22e0-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span>
<span data-ttu-id="a22e0-144">La valeur de l’attribut doit être un URI qui commence par `http` ou `https` .</span><span class="sxs-lookup"><span data-stu-id="a22e0-144">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="a22e0-145">Le code suivant illustre l’attribut HelpUri de la `Start-Debug` commande CIM.</span><span class="sxs-lookup"><span data-stu-id="a22e0-145">The following code shows the HelpUri attribute of the `Start-Debug` CIM command</span></span>

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="a22e0-146">Ajout d’un attribut HelpUri à un Workflow</span><span class="sxs-lookup"><span data-stu-id="a22e0-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="a22e0-147">Pour les flux de travail écrits dans le langage PowerShell, ajoutez un **. Commentaire ExternalHelp** directive de commentaire au code de Workflow.</span><span class="sxs-lookup"><span data-stu-id="a22e0-147">For workflows that are written in the PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="a22e0-148">La valeur de la directive doit être un URI qui commence par `http` ou `https` .</span><span class="sxs-lookup"><span data-stu-id="a22e0-148">The value of the directive must be a URI that begins with `http` or `https`.</span></span>

> [!NOTE]
> <span data-ttu-id="a22e0-149">La propriété HelpUri n’est pas prise en charge pour les flux de travail XAML dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a22e0-149">The HelpUri property is not supported for XAML-based workflows in PowerShell.</span></span>

<span data-ttu-id="a22e0-150">Le code suivant illustre. Directive commentaire ExternalHelp dans un fichier de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a22e0-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
