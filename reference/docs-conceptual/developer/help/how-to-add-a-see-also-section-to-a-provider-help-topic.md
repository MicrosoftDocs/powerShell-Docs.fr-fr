---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur
description: Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur
ms.openlocfilehash: df0b14ba84e04baf404081944ef62ef6745d74b2
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667655"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="bc7a7-103">Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur</span><span class="sxs-lookup"><span data-stu-id="bc7a7-103">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="bc7a7-104">Cette section explique comment remplir la section **Voir aussi** d’une rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-104">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="bc7a7-105">La section **Voir aussi** est constituée d’une liste de rubriques relatives au fournisseur ou qui peut aider l’utilisateur à mieux comprendre et à utiliser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-105">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="bc7a7-106">La liste de rubriques peut inclure des rubriques d’aide sur les applets de commande, aide du fournisseur et concepts (« à propos de ») dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-106">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="bc7a7-107">Il peut également inclure des références à des livres, des documents et des rubriques en ligne, notamment une version en ligne de la rubrique d’aide actuelle du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-107">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="bc7a7-108">Lorsque vous faites référence à des rubriques en ligne, fournissez l’URI ou un terme de recherche en texte brut.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-108">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="bc7a7-109">L' `Get-Help` applet de commande n’effectue pas de liaison ou de redirection vers l’une des rubriques de la liste.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-109">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="bc7a7-110">En outre, le `Online` paramètre de l’applet de commande `Get-Help` ne fonctionne pas avec l’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-110">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="bc7a7-111">La section **Voir aussi** est créée à partir de l' `RelatedLinks` élément et des balises qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-111">The **See Also** section is created from the `RelatedLinks` element and the tags that it contains.</span></span>
<span data-ttu-id="bc7a7-112">Le code XML suivant montre comment ajouter les balises.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-112">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="bc7a7-113">Pour ajouter des rubriques Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc7a7-113">To Add SEE ALSO Topics</span></span>

1. <span data-ttu-id="bc7a7-114">Dans le `<AssemblyName>.dll-help.xml` fichier, dans l' `providerHelp` élément, ajoutez un `RelatedLinks` élément.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-114">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="bc7a7-115">L' `RelatedLinks` élément doit être le dernier élément de l' `providerHelp` élément.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-115">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="bc7a7-116">Un seul `RelatedLinks` élément est autorisé dans chaque rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-116">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="bc7a7-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bc7a7-117">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. <span data-ttu-id="bc7a7-118">Pour chaque rubrique de la section **Voir aussi** , dans l' `RelatedLinks` élément, ajoutez un `navigationLink` élément.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-118">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="bc7a7-119">Ensuite, dans chaque `navigationLink` élément, ajoutez un `linkText` élément et un `uri` élément.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-119">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="bc7a7-120">Si vous n’utilisez pas l' `uri` élément, vous pouvez l’ajouter en tant qu’élément vide ( \<uri/> ).</span><span class="sxs-lookup"><span data-stu-id="bc7a7-120">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="bc7a7-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bc7a7-121">For example:</span></span>

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

1. <span data-ttu-id="bc7a7-122">Tapez le nom de la rubrique entre les `linkText` balises.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-122">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="bc7a7-123">Si vous fournissez un URI, tapez-le entre les `uri` balises.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-123">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="bc7a7-124">Pour indiquer la version en ligne de la rubrique d’aide actuelle du fournisseur, entre les `linkText` balises, tapez « version en ligne : » à la place du nom de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-124">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="bc7a7-125">En règle générale, le lien « version en ligne : » est la première rubrique de la liste de rubriques Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-125">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="bc7a7-126">L’exemple suivant inclut trois rubriques Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-126">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="bc7a7-127">La première référence à la version en ligne de la rubrique active.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-127">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="bc7a7-128">Le deuxième fait référence à une rubrique d’aide sur les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-128">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="bc7a7-129">Le troisième fait référence à une autre rubrique en ligne.</span><span class="sxs-lookup"><span data-stu-id="bc7a7-129">The third refers to another online topic.</span></span>

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
