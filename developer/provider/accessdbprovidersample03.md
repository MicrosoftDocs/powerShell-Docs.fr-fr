---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859405"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="83277-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="83277-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="83277-103">Cet exemple montre comment remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthodes pour prendre en charge les appels à la `Get-Item` et `Set-Item` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="83277-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="83277-104">La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="83277-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="83277-105">Montre</span><span class="sxs-lookup"><span data-stu-id="83277-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83277-106">Votre classe de fournisseur sera très probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="83277-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="83277-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="83277-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="83277-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="83277-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="83277-109">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="83277-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="83277-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="83277-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="83277-111">Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="83277-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="83277-112">Pour plus d’informations sur le choix de la classe de fournisseur à dérivent selon les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="83277-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="83277-113">Cet exemple montre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="83277-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="83277-114">Déclarer la `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="83277-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="83277-115">Définition d’une classe de fournisseur qui dérive de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="83277-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="83277-116">En remplaçant le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) méthode pour modifier le comportement de la `New-PSDrive` applet de commande, permettant à l’utilisateur à créer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="83277-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="83277-117">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `New-PSDrive` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="83277-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="83277-118">En remplaçant le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthode pour prendre en charge la suppression de lecteurs existants.</span><span class="sxs-lookup"><span data-stu-id="83277-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="83277-119">En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode pour modifier le comportement de la `Get-Item` applet de commande, permettant à l’utilisateur récupérer des éléments à partir du magasin de données.</span><span class="sxs-lookup"><span data-stu-id="83277-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="83277-120">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Get-Item` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="83277-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="83277-121">En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthode pour modifier le comportement de la `Set-Item` applet de commande, permettant à l’utilisateur à mettre à jour les éléments dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="83277-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="83277-122">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Get-Item` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="83277-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="83277-123">En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) méthode pour modifier le comportement de la `Test-Path` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="83277-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="83277-124">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Test-Path` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="83277-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="83277-125">En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) méthode pour déterminer si le chemin d’accès fourni est valide.</span><span class="sxs-lookup"><span data-stu-id="83277-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="83277-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="83277-126">Example</span></span>

<span data-ttu-id="83277-127">Cet exemple montre comment remplacer les méthodes nécessaires pour obtenir et définir les éléments de données Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="83277-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="83277-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83277-128">See Also</span></span>

[<span data-ttu-id="83277-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="83277-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="83277-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="83277-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="83277-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="83277-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="83277-132">Conception de votre fournisseur de PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="83277-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)