---
title: Exemple deC#code GetProc01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416156"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="3b32c-102">Exemple de code GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b32c-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="3b32c-103">Le code suivant illustre l’implémentation de l’applet de commande GetProc01 Sample.</span><span class="sxs-lookup"><span data-stu-id="3b32c-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="3b32c-104">Notez que l’applet de commande est simplifiée en laissant le travail réel de récupération du processus à la méthode [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="3b32c-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="3b32c-105">Vous pouvez télécharger le C# fichier source (getproc01.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="3b32c-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3b32c-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3b32c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3b32c-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="3b32c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3b32c-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="3b32c-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="3b32c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b32c-109">See Also</span></span>

[<span data-ttu-id="3b32c-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b32c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3b32c-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3b32c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
