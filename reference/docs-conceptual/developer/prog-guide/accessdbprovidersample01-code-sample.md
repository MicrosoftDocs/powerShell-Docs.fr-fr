---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code AccessDbProviderSample01
description: Exemple de code AccessDbProviderSample01
ms.openlocfilehash: 5be593b9e86347b2f55de156fe4d9b44cfab5b78
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659419"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="206eb-103">Exemple de code AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="206eb-103">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="206eb-104">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="206eb-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="206eb-105">Cette implémentation fournit des méthodes pour démarrer et arrêter le fournisseur et, bien qu’elle ne fournisse pas de moyen d’accéder à un magasin de données ou d’obtenir ou de définir les données dans le magasin de données, elle fournit les fonctionnalités de base requises par tous les fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="206eb-105">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="206eb-106">Vous pouvez télécharger le fichier source C# (AccessDBSampleProvider01.cs) pour ce fournisseur à l’aide du kit de développement logiciel Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="206eb-106">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="206eb-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="206eb-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="206eb-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="206eb-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="206eb-109">Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="206eb-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="206eb-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="206eb-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="206eb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="206eb-111">See Also</span></span>

[<span data-ttu-id="206eb-112">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="206eb-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="206eb-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="206eb-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
