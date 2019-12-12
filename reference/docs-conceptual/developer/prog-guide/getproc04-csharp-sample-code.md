---
title: Exemple deC#code GetProc04 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 0ca2ccc5188f0c1784ec14ac204c1fdd624c2e66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416117"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="0f47c-102">Exemple de code GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="0f47c-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="0f47c-103">Le code suivant illustre l’implémentation d’une applet de commande `Get-Process` qui signale des erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="0f47c-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="0f47c-104">Cette implémentation appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="0f47c-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="0f47c-105">Vous pouvez télécharger le C# fichier source (getprov04.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f47c-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0f47c-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0f47c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0f47c-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="0f47c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0f47c-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="0f47c-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="0f47c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f47c-109">See Also</span></span>

[<span data-ttu-id="0f47c-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f47c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0f47c-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0f47c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
