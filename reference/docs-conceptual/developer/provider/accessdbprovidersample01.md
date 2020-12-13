---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample01
description: AccessDBProviderSample01
ms.openlocfilehash: 8bdfa3ad492935a22ce06846294c02961cab2c65
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653753"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="790d0-103">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="790d0-103">AccessDBProviderSample01</span></span>

<span data-ttu-id="790d0-104">Cet exemple montre comment déclarer une classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="790d0-104">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="790d0-105">Il est indiqué ici uniquement par souci de citer tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="790d0-105">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="790d0-106">Illustre le</span><span class="sxs-lookup"><span data-stu-id="790d0-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="790d0-107">Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="790d0-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="790d0-108">Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="790d0-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="790d0-109">Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="790d0-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="790d0-110">Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="790d0-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="790d0-111">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="790d0-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="790d0-112">Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="790d0-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="790d0-113">Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="790d0-113">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="790d0-114">Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="790d0-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="790d0-115">Cet exemple indique :</span><span class="sxs-lookup"><span data-stu-id="790d0-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="790d0-116">Déclaration de l' `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="790d0-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="790d0-117">Définition d’une classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="790d0-117">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="790d0-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="790d0-118">Example</span></span>

<span data-ttu-id="790d0-119">Cet exemple montre comment définir une classe de fournisseur et comment déclarer l' `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="790d0-119">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="790d0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="790d0-120">See Also</span></span>

[<span data-ttu-id="790d0-121">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="790d0-121">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="790d0-122">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="790d0-122">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="790d0-123">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="790d0-123">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="790d0-124">Conception de votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="790d0-124">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
