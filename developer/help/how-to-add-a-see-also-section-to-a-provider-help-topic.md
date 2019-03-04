---
title: Comment ajouter un, consultez Section une rubrique d’aide de fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858345"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="c5fb8-102">Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur</span><span class="sxs-lookup"><span data-stu-id="c5fb8-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="c5fb8-103">Cette section explique comment remplir le **Voir aussi** section d’une rubrique d’aide de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="c5fb8-104">Le **Voir aussi** section se compose d’une liste de rubriques qui sont liées au fournisseur ou peut aider l’utilisateur à mieux comprendre et utiliser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="c5fb8-105">La liste de rubriques peut inclure l’aide de l’applet de commande, fournisseur aide et conceptuelles (« about ») des rubriques d’aide dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="c5fb8-106">Il peut également inclure des références à la documentation, papier et rubriques en ligne, y compris une version en ligne de la rubrique d’aide fournisseur actuel.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="c5fb8-107">Lorsque vous faites référence à des rubriques en ligne, indiquez l’URI ou un terme de recherche en texte brut.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="c5fb8-108">Le `Get-Help` applet de commande ne pas lier ou rediriger vers les rubriques dans la liste.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="c5fb8-109">En outre, le `Online` paramètre de la `Get-Help` applet de commande ne fonctionne pas avec l’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="c5fb8-110">La section Voir aussi est créée à partir du `RelatedLinks` élément les balises et qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="c5fb8-111">Le code XML suivant montre comment ajouter des balises.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="c5fb8-112">Pour ajouter des rubriques « Voir aussi »</span><span class="sxs-lookup"><span data-stu-id="c5fb8-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="c5fb8-113">Dans le *AssemblyName*.dll-help.xml de fichiers, dans le `providerHelp` élément, ajoutez un `RelatedLinks` élément.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="c5fb8-114">Le `RelatedLinks` élément doit être le dernier élément dans le `providerHelp` élément.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="c5fb8-115">Seul `RelatedLinks` élément est autorisé dans chaque rubrique d’aide de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="c5fb8-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c5fb8-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="c5fb8-117">Pour chaque rubrique de la **Voir aussi** section dans le `RelatedLinks` élément, ajoutez un `navigationLink` élément.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="c5fb8-118">Ensuite, dans chaque `navigationLink` élément, ajouter un `linkText` et un élément `uri` élément.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="c5fb8-119">Si vous n’utilisez pas le `uri` élément, vous pouvez l’ajouter comme un élément vide (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="c5fb8-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="c5fb8-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c5fb8-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="c5fb8-121">Tapez le nom de rubrique entre le `linkText` balises.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="c5fb8-122">Si vous fournissez un URI, tapez-le entre le `uri` balises.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="c5fb8-123">Pour indiquer la version en ligne de la rubrique d’aide fournisseur actuel, entre le `linkText` balises, tapez « version en ligne : « au lieu du nom de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="c5fb8-124">En règle générale, la « version en ligne : « lien est la première rubrique dans la liste de rubrique Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="c5fb8-125">L’exemple suivant inclut les trois rubriques connexes.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="c5fb8-126">Le premier font référence à la version en ligne de la rubrique active.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="c5fb8-127">Le second fait référence à une rubrique d’aide applet de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="c5fb8-128">Le troisième fait référence à une autre rubrique en ligne.</span><span class="sxs-lookup"><span data-stu-id="c5fb8-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```