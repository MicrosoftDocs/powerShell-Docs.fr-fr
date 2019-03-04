---
title: Exemple de Code RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857925"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="5cfb8-102">Exemple de code RunSpace07</span><span class="sxs-lookup"><span data-stu-id="5cfb8-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="5cfb8-103">Voici le code source pour l’exemple Runspace07 décrit dans [création d’une Application qu’ajoute des commandes de la Console à un Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="5cfb8-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="5cfb8-104">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute les deux commandes au pipeline, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5cfb8-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="5cfb8-105">Les commandes ajoutées au pipeline sont le `Get-Process` et `Measure-Object` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="5cfb8-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="5cfb8-106">Vous pouvez télécharger le C# le fichier source (runspace07.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants de Microsoft .NET Framework 3.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="5cfb8-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5cfb8-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5cfb8-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5cfb8-108">Vous pouvez télécharger le C# le fichier source (runspace07.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants de Microsoft .NET Framework 3.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="5cfb8-108">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5cfb8-109">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5cfb8-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5cfb8-110">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="5cfb8-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5cfb8-111">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="5cfb8-111">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="5cfb8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cfb8-112">See Also</span></span>

[<span data-ttu-id="5cfb8-113">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cfb8-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5cfb8-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5cfb8-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)