---
title: Exemple de Code AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081986"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="b76a2-102">Exemple de code AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="b76a2-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="b76a2-103">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de PowerShell Windows base](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b76a2-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="b76a2-104">Cette implémentation fournit des méthodes pour démarrer et arrêter le fournisseur, et bien qu’il ne fournit pas un moyen pour accéder à un magasin de données ou à obtenir ou définir les données dans le magasin de données, il vous offre les fonctionnalités de base requises par tous les fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="b76a2-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="b76a2-105">Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider01.cs) pour ce fournisseur en utilisant le Kit du développement de logiciel Windows pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="b76a2-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b76a2-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="b76a2-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="b76a2-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="b76a2-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="b76a2-108">Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b76a2-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="b76a2-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b76a2-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="b76a2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b76a2-110">See Also</span></span>

[<span data-ttu-id="b76a2-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b76a2-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b76a2-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b76a2-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)