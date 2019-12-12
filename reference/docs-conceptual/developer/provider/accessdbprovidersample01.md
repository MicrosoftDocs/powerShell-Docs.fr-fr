---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359998"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="85d48-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="85d48-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="85d48-103">Cet exemple montre comment déclarer une classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="85d48-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="85d48-104">Il est indiqué ici uniquement par souci de citer tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="85d48-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="85d48-105">Démontre</span><span class="sxs-lookup"><span data-stu-id="85d48-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85d48-106">Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :</span><span class="sxs-lookup"><span data-stu-id="85d48-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="85d48-107">Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="85d48-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="85d48-108">Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="85d48-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="85d48-109">Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="85d48-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="85d48-110">Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="85d48-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="85d48-111">Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="85d48-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="85d48-112">Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="85d48-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="85d48-113">Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="85d48-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="85d48-114">Cet exemple illustre les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="85d48-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="85d48-115">Déclaration de l’attribut `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="85d48-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="85d48-116">Définition d’une classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="85d48-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="85d48-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="85d48-117">Example</span></span>

<span data-ttu-id="85d48-118">Cet exemple montre comment définir une classe de fournisseur et comment déclarer l’attribut `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="85d48-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="85d48-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85d48-119">See Also</span></span>

[<span data-ttu-id="85d48-120">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="85d48-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="85d48-121">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="85d48-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="85d48-122">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="85d48-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="85d48-123">Conception de votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="85d48-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)