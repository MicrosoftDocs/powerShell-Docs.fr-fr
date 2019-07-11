---
title: Runspace01 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735059"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="312d0-102">Exemple de code Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="312d0-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="312d0-103">Voici les exemples de code pour l’instance d’exécution décrit dans [création d’une Console Application qui s’exécute une commande spécifiée](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="312d0-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="312d0-104">Pour ce faire, l’application appelle une instance d’exécution et appelle ensuite une commande.</span><span class="sxs-lookup"><span data-stu-id="312d0-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="312d0-105">(Notez que cette application ne spécifie pas les informations de configuration d’instance d’exécution, ni il crée explicitement un pipeline).</span><span class="sxs-lookup"><span data-stu-id="312d0-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="312d0-106">La commande est appelée est la `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="312d0-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="312d0-107">Vous pouvez télécharger le C# le fichier source (runspace01.cs) pour cette instance d’exécution à l’aide du Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="312d0-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="312d0-108">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="312d0-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="312d0-109">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="312d0-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="312d0-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="312d0-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="312d0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="312d0-111">See Also</span></span>

[<span data-ttu-id="312d0-112">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="312d0-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="312d0-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="312d0-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)