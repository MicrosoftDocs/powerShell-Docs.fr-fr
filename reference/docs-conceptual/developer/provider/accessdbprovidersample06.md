---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366328"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="9c9d2-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="9c9d2-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="9c9d2-103">Cet exemple montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux applets de commande `Clear-Content`, `Get-Content` et `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="9c9d2-104">Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="9c9d2-105">La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et implémente l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9c9d2-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9c9d2-106">Illustré</span><span class="sxs-lookup"><span data-stu-id="9c9d2-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c9d2-107">Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="9c9d2-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="9c9d2-108">Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9c9d2-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="9c9d2-109">Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="9c9d2-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="9c9d2-110">Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9c9d2-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="9c9d2-111">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="9c9d2-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="9c9d2-112">Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9c9d2-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="9c9d2-113">Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c9d2-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="9c9d2-114">Cet exemple illustre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9c9d2-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="9c9d2-115">Déclaration de l’attribut `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="9c9d2-116">Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et qui déclare l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9c9d2-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="9c9d2-117">Remplacement de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) pour modifier le comportement de l’applet de commande `Clear-Content`, ce qui permet à l’utilisateur de supprimer le contenu d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="9c9d2-118">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande `Clear-Content`.)</span><span class="sxs-lookup"><span data-stu-id="9c9d2-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="9c9d2-119">Remplacement de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) pour modifier le comportement de l’applet de commande `Get-Content`, ce qui permet à l’utilisateur de récupérer le contenu d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="9c9d2-120">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande `Get-Content`.).</span><span class="sxs-lookup"><span data-stu-id="9c9d2-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="9c9d2-121">Remplacement de la méthode [Microsoft. PowerShell. Commands. FileSystemProvider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) pour modifier le comportement de l’applet de commande `Set-Content`, ce qui permet à l’utilisateur de mettre à jour le contenu d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="9c9d2-122">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande `Set-Content`.)</span><span class="sxs-lookup"><span data-stu-id="9c9d2-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="9c9d2-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c9d2-123">Example</span></span>

<span data-ttu-id="9c9d2-124">Cet exemple montre comment remplacer les méthodes nécessaires pour effacer, obtenir et définir le contenu des éléments dans une base de données Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="9c9d2-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="9c9d2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c9d2-125">See Also</span></span>

[<span data-ttu-id="9c9d2-126">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="9c9d2-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="9c9d2-127">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="9c9d2-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="9c9d2-128">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="9c9d2-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="9c9d2-129">Conception de votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c9d2-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)