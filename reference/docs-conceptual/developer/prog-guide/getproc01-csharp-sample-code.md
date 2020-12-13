---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code GetProc01 (C#)
description: Exemple de code GetProc01 (C#)
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654475"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="7aa4b-103">Exemple de code GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="7aa4b-103">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="7aa4b-104">Le code suivant illustre l’implémentation de l’applet de commande GetProc01 Sample.</span><span class="sxs-lookup"><span data-stu-id="7aa4b-104">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="7aa4b-105">Notez que l’applet de commande est simplifiée en laissant le travail réel de récupération du processus à la méthode [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="7aa4b-105">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="7aa4b-106">Vous pouvez télécharger le fichier source C# (getproc01.cs) pour cette Get-Proc applet de commande à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0.</span><span class="sxs-lookup"><span data-stu-id="7aa4b-106">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7aa4b-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7aa4b-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="7aa4b-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="7aa4b-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7aa4b-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="7aa4b-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="7aa4b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aa4b-110">See Also</span></span>

[<span data-ttu-id="7aa4b-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7aa4b-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7aa4b-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7aa4b-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
