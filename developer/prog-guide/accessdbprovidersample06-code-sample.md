---
title: Exemple de Code AccessDbProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 2798e8b542b2f06247955409118e75c5652b644c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860785"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="55cc5-102">Exemple de code AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="55cc5-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="55cc5-103">Le code suivant montre l’implémentation de fournisseur de contenu décrit dans la commande PowerShell Windows [création d’un fournisseur de contenu Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="55cc5-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="55cc5-104">Ce fournisseur permet à l’utilisateur de manipuler le contenu des éléments dans un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="55cc5-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="55cc5-105">Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider06.cs) pour ce fournisseur en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="55cc5-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="55cc5-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="55cc5-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="55cc5-107">Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider06.cs) pour ce fournisseur en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="55cc5-107">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="55cc5-108">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="55cc5-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="55cc5-109">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="55cc5-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="55cc5-110">Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="55cc5-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="55cc5-111">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="55cc5-111">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="55cc5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55cc5-112">See Also</span></span>

[<span data-ttu-id="55cc5-113">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="55cc5-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="55cc5-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="55cc5-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)