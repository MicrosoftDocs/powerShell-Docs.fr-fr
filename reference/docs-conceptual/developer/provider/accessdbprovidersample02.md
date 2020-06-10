---
title: AccessDBProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: 219f8c2367939d16da928ede789843669b4451c6
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633411"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="a4dd0-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="a4dd0-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="a4dd0-103">Cet exemple montre comment remplacer les méthodes [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour prendre en charge les appels aux `New-PSDrive` applets de commande et `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="a4dd0-104">La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a4dd0-105">Illustre</span><span class="sxs-lookup"><span data-stu-id="a4dd0-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4dd0-106">Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="a4dd0-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="a4dd0-107">Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="a4dd0-108">Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="a4dd0-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="a4dd0-109">Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a4dd0-110">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a4dd0-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="a4dd0-111">Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="a4dd0-112">Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="a4dd0-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="a4dd0-113">Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="a4dd0-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a4dd0-114">Cet exemple indique :</span><span class="sxs-lookup"><span data-stu-id="a4dd0-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a4dd0-115">Déclaration de l' `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="a4dd0-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a4dd0-116">Définition d’une classe de fournisseur qui pilote à partir de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="a4dd0-117">Remplacement de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) pour prendre en charge la création de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="a4dd0-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="a4dd0-118">(Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `New-PSDrive` applet de commande.)</span><span class="sxs-lookup"><span data-stu-id="a4dd0-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="a4dd0-119">Remplacement de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour prendre en charge la suppression des lecteurs existants.</span><span class="sxs-lookup"><span data-stu-id="a4dd0-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="a4dd0-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4dd0-120">Example</span></span>

<span data-ttu-id="a4dd0-121">Cet exemple montre comment remplacer les méthodes [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .</span><span class="sxs-lookup"><span data-stu-id="a4dd0-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="a4dd0-122">Pour cet exemple de fournisseur, lorsqu’un lecteur est créé, ses informations de connexion sont stockées dans un `AccessDBPsDriveInfo` objet.</span><span class="sxs-lookup"><span data-stu-id="a4dd0-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="a4dd0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4dd0-123">See Also</span></span>

[<span data-ttu-id="a4dd0-124">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a4dd0-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a4dd0-125">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a4dd0-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a4dd0-126">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a4dd0-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a4dd0-127">Conception de votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4dd0-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
