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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057618"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="f616e-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="f616e-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="f616e-103">Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels à la `Copy-Item`, `Get-ChildItem`, `New-Item`, et `Remove-Item` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="f616e-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="f616e-104">Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur.</span><span class="sxs-lookup"><span data-stu-id="f616e-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="f616e-105">Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent.</span><span class="sxs-lookup"><span data-stu-id="f616e-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="f616e-106">La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="f616e-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f616e-107">Montre</span><span class="sxs-lookup"><span data-stu-id="f616e-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f616e-108">Votre classe de fournisseur dérivent très probablement le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="f616e-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="f616e-109">Cet exemple montre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f616e-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f616e-110">Déclarer la `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="f616e-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="f616e-111">Définition d’une classe de fournisseur qui dérive de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="f616e-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="f616e-112">En remplaçant le [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) méthode pour modifier le comportement de la `Copy-Item` applet de commande qui permet à l’utilisateur copier des éléments d’un emplacement vers un autre.</span><span class="sxs-lookup"><span data-stu-id="f616e-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="f616e-113">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Copy-Item` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="f616e-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="f616e-114">En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour modifier le comportement de l’applet de commande Get-ChildItems, ce qui permet à l’utilisateur récupérer les éléments enfants de l’élément parent (méthode) .</span><span class="sxs-lookup"><span data-stu-id="f616e-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="f616e-115">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à l’applet de commande Get-ChildItems.)</span><span class="sxs-lookup"><span data-stu-id="f616e-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="f616e-116">En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) méthode pour modifier le comportement de l’applet de commande Get-ChildItems lorsque le `Name` de l’applet de commande est précisé.</span><span class="sxs-lookup"><span data-stu-id="f616e-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="f616e-117">En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode pour modifier le comportement de la `New-Item` applet de commande, qui permet à l’utilisateur d’ajouter des éléments au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="f616e-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="f616e-118">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `New-Item` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="f616e-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="f616e-119">En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) méthode pour modifier le comportement de la `Remove-Item` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f616e-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="f616e-120">(Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Remove-Item` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="f616e-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="f616e-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="f616e-121">Example</span></span>

<span data-ttu-id="f616e-122">Cet exemple montre comment remplacer les méthodes nécessaires pour copier, créer et supprimer des éléments, ainsi que des méthodes pour obtenir des éléments d’un élément parent de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="f616e-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="f616e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f616e-123">See Also</span></span>

[<span data-ttu-id="f616e-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f616e-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="f616e-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f616e-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="f616e-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f616e-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="f616e-127">Conception de votre fournisseur de PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="f616e-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)