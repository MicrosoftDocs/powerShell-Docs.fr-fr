---
title: Exemple deC#code Runspace01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 39e7d49b51942da51a581ab33dbe46ab848ca1c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366638"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="07bf4-102">Exemple de code Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="07bf4-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="07bf4-103">Voici les exemples de code pour l’instance d’exécution décrite dans [création d’une application console qui exécute une commande spécifiée](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="07bf4-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="07bf4-104">Pour ce faire, l’application appelle une instance d’exécution, puis appelle une commande.</span><span class="sxs-lookup"><span data-stu-id="07bf4-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="07bf4-105">(Notez que cette application ne spécifie pas d’informations de configuration d’instance d’exécution et ne crée pas de pipeline de manière explicite).</span><span class="sxs-lookup"><span data-stu-id="07bf4-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="07bf4-106">La commande appelée est l’applet de commande `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="07bf4-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="07bf4-107">Vous pouvez télécharger le C# fichier source (runspace01.cs) pour cette instance d’exécution à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0 Framework.</span><span class="sxs-lookup"><span data-stu-id="07bf4-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="07bf4-108">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="07bf4-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="07bf4-109">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="07bf4-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="07bf4-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="07bf4-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="07bf4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07bf4-111">See Also</span></span>

[<span data-ttu-id="07bf4-112">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07bf4-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="07bf4-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="07bf4-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
