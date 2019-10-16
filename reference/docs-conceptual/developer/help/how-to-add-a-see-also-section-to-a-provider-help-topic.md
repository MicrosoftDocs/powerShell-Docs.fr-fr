---
title: Comment ajouter une section Voir aussi à une rubrique d’aide du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367838"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="1d560-102">Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur</span><span class="sxs-lookup"><span data-stu-id="1d560-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="1d560-103">Cette section explique comment remplir la section **Voir aussi** d’une rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1d560-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="1d560-104">La section **Voir aussi** est constituée d’une liste de rubriques relatives au fournisseur ou qui peut aider l’utilisateur à mieux comprendre et à utiliser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1d560-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="1d560-105">La liste de rubriques peut inclure des rubriques d’aide sur les applets de commande, aide du fournisseur et concepts (« à propos de ») dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d560-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="1d560-106">Il peut également inclure des références à des livres, des documents et des rubriques en ligne, notamment une version en ligne de la rubrique d’aide actuelle du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1d560-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="1d560-107">Lorsque vous faites référence à des rubriques en ligne, fournissez l’URI ou un terme de recherche en texte brut.</span><span class="sxs-lookup"><span data-stu-id="1d560-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="1d560-108">L’applet de commande `Get-Help` n’effectue pas de liaison ou de redirection vers l’une des rubriques de la liste.</span><span class="sxs-lookup"><span data-stu-id="1d560-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="1d560-109">En outre, le paramètre `Online` de l’applet de commande `Get-Help` ne fonctionne pas avec l’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1d560-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="1d560-110">La section Voir aussi est créée à partir de l’élément `RelatedLinks` et des balises qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="1d560-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="1d560-111">Le code XML suivant montre comment ajouter les balises.</span><span class="sxs-lookup"><span data-stu-id="1d560-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="1d560-112">Pour ajouter des rubriques « Voir aussi »</span><span class="sxs-lookup"><span data-stu-id="1d560-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="1d560-113">Dans le fichier *AssemblyName*. dll-help. xml, dans l’élément `providerHelp`, ajoutez un élément `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="1d560-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="1d560-114">L’élément `RelatedLinks` doit être le dernier élément de l’élément `providerHelp`.</span><span class="sxs-lookup"><span data-stu-id="1d560-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="1d560-115">Un seul élément `RelatedLinks` est autorisé dans chaque rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1d560-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="1d560-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1d560-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="1d560-117">Pour chaque rubrique de la section **Voir aussi** , dans l’élément `RelatedLinks`, ajoutez un élément `navigationLink`.</span><span class="sxs-lookup"><span data-stu-id="1d560-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="1d560-118">Ensuite, dans chaque élément `navigationLink`, ajoutez un élément `linkText` et un élément `uri`.</span><span class="sxs-lookup"><span data-stu-id="1d560-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="1d560-119">Si vous n’utilisez pas l’élément `uri`, vous pouvez l’ajouter en tant qu’élément vide (\<uri/>).</span><span class="sxs-lookup"><span data-stu-id="1d560-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="1d560-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1d560-120">For example:</span></span>

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

3. <span data-ttu-id="1d560-121">Tapez le nom de la rubrique entre les balises `linkText`.</span><span class="sxs-lookup"><span data-stu-id="1d560-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="1d560-122">Si vous fournissez un URI, tapez-le entre les balises `uri`.</span><span class="sxs-lookup"><span data-stu-id="1d560-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="1d560-123">Pour indiquer la version en ligne de la rubrique d’aide actuelle du fournisseur, entre les balises `linkText`, tapez « version en ligne : » à la place du nom de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="1d560-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="1d560-124">En règle générale, le lien « version en ligne : » est la première rubrique de la liste de rubriques Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="1d560-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="1d560-125">L’exemple suivant inclut trois rubriques Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="1d560-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="1d560-126">La première référence à la version en ligne de la rubrique active.</span><span class="sxs-lookup"><span data-stu-id="1d560-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="1d560-127">Le deuxième fait référence à une rubrique d’aide sur les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d560-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="1d560-128">Le troisième fait référence à une autre rubrique en ligne.</span><span class="sxs-lookup"><span data-stu-id="1d560-128">The third refers to another online topic.</span></span>

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