---
title: Exemple de code AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 32abcfafb207ada23667cc6f0f03d382c6868ccb
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978606"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="d1dc9-102">Exemple de code AccessDbProviderSample02</span><span class="sxs-lookup"><span data-stu-id="d1dc9-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="d1dc9-103">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d1dc9-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="d1dc9-104">Cette implémentation crée un chemin d’accès, établit une connexion à une base de données Access, puis supprime le lecteur.</span><span class="sxs-lookup"><span data-stu-id="d1dc9-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="d1dc9-105">Vous pouvez télécharger le C# fichier source (AccessDBSampleProvider02.cs) pour ce fournisseur à l’aide du kit de développement logiciel Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="d1dc9-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d1dc9-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d1dc9-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="d1dc9-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="d1dc9-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="d1dc9-108">Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d1dc9-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="d1dc9-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="d1dc9-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="d1dc9-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1dc9-110">See Also</span></span>

[<span data-ttu-id="d1dc9-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1dc9-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d1dc9-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d1dc9-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
