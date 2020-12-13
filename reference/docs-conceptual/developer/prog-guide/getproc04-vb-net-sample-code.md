---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code GetProc04 (VB.NET)
description: Exemple de code GetProc04 (VB.NET)
ms.openlocfilehash: c46a374ab9d77f343b5ac6f45be1711eaec6dd75
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659230"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="14c33-103">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="14c33-103">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="14c33-104">Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui signale des erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="14c33-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="14c33-105">Cette implémentation appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="14c33-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="14c33-106">Vous pouvez télécharger le fichier source C# (getprov04.cs) pour cette Get-Proc applet de commande à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0.</span><span class="sxs-lookup"><span data-stu-id="14c33-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="14c33-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="14c33-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="14c33-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="14c33-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="14c33-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="14c33-109">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="14c33-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14c33-110">See Also</span></span>

[<span data-ttu-id="14c33-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="14c33-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="14c33-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="14c33-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
