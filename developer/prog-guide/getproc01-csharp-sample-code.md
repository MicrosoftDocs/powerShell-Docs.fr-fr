---
title: GetProc01 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081731"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="ccdd3-102">Exemple de code GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="ccdd3-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="ccdd3-103">Le code suivant illustre l’implémentation de l’applet de commande GetProc01 exemple.</span><span class="sxs-lookup"><span data-stu-id="ccdd3-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="ccdd3-104">Notez que l’applet de commande est simplifiée en laissant le travail réel de la récupération des processus à le [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ccdd3-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="ccdd3-105">Vous pouvez télécharger le C# le fichier source (getproc01.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="ccdd3-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ccdd3-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ccdd3-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ccdd3-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="ccdd3-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ccdd3-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="ccdd3-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="ccdd3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccdd3-109">See Also</span></span>

[<span data-ttu-id="ccdd3-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccdd3-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ccdd3-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ccdd3-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)