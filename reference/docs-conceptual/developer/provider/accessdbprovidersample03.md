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
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359988"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="b4d03-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="b4d03-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="b4d03-103">Cet exemple montre comment remplacer les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) pour prendre en charge les appels aux applets de commande `Get-Item` et `Set-Item`.</span><span class="sxs-lookup"><span data-stu-id="b4d03-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="b4d03-104">La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b4d03-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b4d03-105">Démontre</span><span class="sxs-lookup"><span data-stu-id="b4d03-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4d03-106">Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="b4d03-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="b4d03-107">Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b4d03-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="b4d03-108">Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b4d03-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="b4d03-109">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="b4d03-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="b4d03-110">Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b4d03-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="b4d03-111">Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="b4d03-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="b4d03-112">Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4d03-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="b4d03-113">Cet exemple illustre les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4d03-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b4d03-114">Déclaration de l’attribut `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="b4d03-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="b4d03-115">Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b4d03-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="b4d03-116">Remplacement de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) pour modifier le comportement de l’applet de commande `New-PSDrive`, permettant à l’utilisateur de créer des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="b4d03-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="b4d03-117">(Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `New-PSDrive`.)</span><span class="sxs-lookup"><span data-stu-id="b4d03-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="b4d03-118">Remplacement de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour prendre en charge la suppression des lecteurs existants.</span><span class="sxs-lookup"><span data-stu-id="b4d03-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="b4d03-119">Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pour modifier le comportement de l’applet de commande `Get-Item`, permettant à l’utilisateur de récupérer des éléments de la Banque de données.</span><span class="sxs-lookup"><span data-stu-id="b4d03-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="b4d03-120">(Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `Get-Item`.)</span><span class="sxs-lookup"><span data-stu-id="b4d03-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="b4d03-121">Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) pour modifier le comportement de l’applet de commande `Set-Item`, permettant à l’utilisateur de mettre à jour les éléments dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="b4d03-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="b4d03-122">(Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `Get-Item`.)</span><span class="sxs-lookup"><span data-stu-id="b4d03-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="b4d03-123">Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) pour modifier le comportement de l’applet de commande `Test-Path`.</span><span class="sxs-lookup"><span data-stu-id="b4d03-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="b4d03-124">(Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `Test-Path`.)</span><span class="sxs-lookup"><span data-stu-id="b4d03-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="b4d03-125">Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) pour déterminer si le chemin d’accès fourni est valide.</span><span class="sxs-lookup"><span data-stu-id="b4d03-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="b4d03-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4d03-126">Example</span></span>

<span data-ttu-id="b4d03-127">Cet exemple montre comment remplacer les méthodes nécessaires pour obtenir et définir des éléments dans une base de données Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="b4d03-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="b4d03-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4d03-128">See Also</span></span>

[<span data-ttu-id="b4d03-129">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b4d03-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="b4d03-130">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b4d03-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="b4d03-131">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b4d03-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="b4d03-132">Conception de votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4d03-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
