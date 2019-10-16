---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366338"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="d2b86-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="d2b86-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="d2b86-103">Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande `Copy-Item`, `Get-ChildItem`, `New-Item` et `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="d2b86-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="d2b86-104">Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur.</span><span class="sxs-lookup"><span data-stu-id="d2b86-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="d2b86-105">Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent.</span><span class="sxs-lookup"><span data-stu-id="d2b86-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="d2b86-106">La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="d2b86-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d2b86-107">Illustré</span><span class="sxs-lookup"><span data-stu-id="d2b86-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2b86-108">Votre classe de fournisseur sera probablement dérivée de [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="d2b86-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="d2b86-109">Cet exemple illustre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d2b86-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="d2b86-110">Déclaration de l’attribut `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="d2b86-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="d2b86-111">Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="d2b86-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="d2b86-112">Remplacement de la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) pour modifier le comportement de l’applet de commande `Copy-Item` qui permet à l’utilisateur de copier des éléments d’un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="d2b86-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="d2b86-113">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande `Copy-Item`.)</span><span class="sxs-lookup"><span data-stu-id="d2b86-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="d2b86-114">Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour modifier le comportement de l’applet de commande « obtenir-ChildItems », qui permet à l’utilisateur de récupérer les éléments enfants de l’élément parent.</span><span class="sxs-lookup"><span data-stu-id="d2b86-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="d2b86-115">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande ChildItems.)</span><span class="sxs-lookup"><span data-stu-id="d2b86-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="d2b86-116">Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) pour modifier le comportement de l’applet de commande ChildItems-1 lorsque le paramètre `Name` de l’applet de commande est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d2b86-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="d2b86-117">Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) pour modifier le comportement de l’applet de commande `New-Item`, ce qui permet à l’utilisateur d’ajouter des éléments au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="d2b86-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="d2b86-118">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande `New-Item`.)</span><span class="sxs-lookup"><span data-stu-id="d2b86-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="d2b86-119">Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) pour modifier le comportement de l’applet de commande `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="d2b86-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="d2b86-120">(Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande `Remove-Item`.)</span><span class="sxs-lookup"><span data-stu-id="d2b86-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="d2b86-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2b86-121">Example</span></span>

<span data-ttu-id="d2b86-122">Cet exemple montre comment remplacer les méthodes nécessaires pour copier, créer et supprimer des éléments, ainsi que les méthodes permettant d’obtenir les éléments enfants d’un élément parent.</span><span class="sxs-lookup"><span data-stu-id="d2b86-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="d2b86-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2b86-123">See Also</span></span>

[<span data-ttu-id="d2b86-124">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d2b86-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="d2b86-125">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d2b86-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="d2b86-126">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d2b86-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="d2b86-127">Conception de votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2b86-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
