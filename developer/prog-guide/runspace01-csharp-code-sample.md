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
ms.openlocfilehash: 2f1839d1ba578cdfe97f60c741c84b0a57f1d8f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854215"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="962a9-102">Exemple de code Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="962a9-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="962a9-103">Voici les exemples de code pour l’instance d’exécution décrit dans [création d’une Console Application qui s’exécute une commande spécifiée](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="962a9-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="962a9-104">Pour ce faire, l’application appelle une instance d’exécution et appelle ensuite une commande.</span><span class="sxs-lookup"><span data-stu-id="962a9-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="962a9-105">(Notez que cette application ne spécifie pas les informations de configuration d’instance d’exécution, ni il crée explicitement un pipeline).</span><span class="sxs-lookup"><span data-stu-id="962a9-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="962a9-106">La commande est appelée est la `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="962a9-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>
<span data-ttu-id="962a9-107">Voici les exemples de code pour l’instance d’exécution décrit dans [création d’une Console Application qui s’exécute une commande spécifiée](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="962a9-107">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="962a9-108">Pour ce faire, l’application appelle une instance d’exécution et appelle ensuite une commande.</span><span class="sxs-lookup"><span data-stu-id="962a9-108">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="962a9-109">(Notez que cette application ne spécifie pas les informations de configuration d’instance d’exécution, ni il crée explicitement un pipeline).</span><span class="sxs-lookup"><span data-stu-id="962a9-109">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="962a9-110">La commande est appelée est la `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="962a9-110">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="962a9-111">Vous pouvez télécharger le C# le fichier source (runspace01.cs) pour cette instance d’exécution à l’aide du Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="962a9-111">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="962a9-112">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="962a9-112">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="962a9-113">Vous pouvez télécharger le C# le fichier source (runspace01.cs) pour cette instance d’exécution à l’aide du Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="962a9-113">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="962a9-114">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="962a9-114">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="962a9-115">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="962a9-115">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="962a9-116">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="962a9-116">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="962a9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="962a9-117">See Also</span></span>

[<span data-ttu-id="962a9-118">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="962a9-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="962a9-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="962a9-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)