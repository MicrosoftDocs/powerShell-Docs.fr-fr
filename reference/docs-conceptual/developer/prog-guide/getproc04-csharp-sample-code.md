---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code GetProc04 (C#)
description: Exemple de code GetProc04 (C#)
ms.openlocfilehash: 80020b60a7ab34caec0c856b9b7d12021f4276b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654378"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="32c73-103">Exemple de code GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="32c73-103">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="32c73-104">Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui signale des erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="32c73-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="32c73-105">Cette implémentation appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="32c73-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="32c73-106">Vous pouvez télécharger le fichier source C# (getprov04.cs) pour cette Get-Proc applet de commande à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0.</span><span class="sxs-lookup"><span data-stu-id="32c73-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="32c73-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="32c73-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="32c73-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="32c73-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="32c73-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="32c73-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a><span data-ttu-id="32c73-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32c73-110">See Also</span></span>

[<span data-ttu-id="32c73-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="32c73-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="32c73-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="32c73-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
