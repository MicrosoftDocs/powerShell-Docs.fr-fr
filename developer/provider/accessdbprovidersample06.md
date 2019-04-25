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
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080983"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="80ca7-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="80ca7-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="80ca7-103">Cet exemple montre comment remplacer les méthodes de contenu pour prendre en charge les appels à la `Clear-Content`, `Get-Content`, et `Set-Content` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="80ca7-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="80ca7-104">Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="80ca7-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="80ca7-105">La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe, qui implémente le [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="80ca7-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="80ca7-106">Montre</span><span class="sxs-lookup"><span data-stu-id="80ca7-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80ca7-107">Votre classe de fournisseur sera très probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="80ca7-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="80ca7-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="80ca7-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="80ca7-109">Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="80ca7-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="80ca7-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="80ca7-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="80ca7-111">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="80ca7-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="80ca7-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="80ca7-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="80ca7-113">Pour plus d’informations sur le choix de la classe de fournisseur à dérivent selon les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="80ca7-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="80ca7-114">Cet exemple montre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="80ca7-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="80ca7-115">Déclarer la `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="80ca7-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="80ca7-116">Définition d’une classe de fournisseur qui dérive de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et qui déclare le [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="80ca7-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="80ca7-117">En remplaçant le [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode pour modifier le comportement de la `Clear-Content` applet de commande, permettant à l’utilisateur à supprimer le contenu d’un élément.</span><span class="sxs-lookup"><span data-stu-id="80ca7-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="80ca7-118">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Clear-Content` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="80ca7-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="80ca7-119">En remplaçant le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) méthode pour modifier le comportement de la `Get-Content` applet de commande, permettant à l’utilisateur récupérer le contenu d’un élément.</span><span class="sxs-lookup"><span data-stu-id="80ca7-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="80ca7-120">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Get-Content` applet de commande.).</span><span class="sxs-lookup"><span data-stu-id="80ca7-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="80ca7-121">En remplaçant le [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) méthode pour modifier le comportement de la `Set-Content` applet de commande, permettant à l’utilisateur à mettre à jour le contenu d’un élément.</span><span class="sxs-lookup"><span data-stu-id="80ca7-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="80ca7-122">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Set-Content` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="80ca7-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="80ca7-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="80ca7-123">Example</span></span>

<span data-ttu-id="80ca7-124">Cet exemple montre comment remplacer les méthodes nécessaires pour effacer, obtenir et définir le contenu des éléments de données Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="80ca7-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="80ca7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80ca7-125">See Also</span></span>

[<span data-ttu-id="80ca7-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="80ca7-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="80ca7-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="80ca7-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="80ca7-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="80ca7-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="80ca7-129">Conception de votre fournisseur de PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="80ca7-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)