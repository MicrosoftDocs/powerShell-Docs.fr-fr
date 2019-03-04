---
title: GetProc01 (VB.NET) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856065"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="60c3d-102">Exemple de code GetProc01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="60c3d-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="60c3d-103">Le code suivant illustre l’implémentation de l’applet de commande GetProc01 exemple.</span><span class="sxs-lookup"><span data-stu-id="60c3d-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="60c3d-104">Notez que l’applet de commande est simplifiée en laissant le travail réel de la récupération des processus à le [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) (méthode).</span><span class="sxs-lookup"><span data-stu-id="60c3d-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="60c3d-105">Vous pouvez télécharger le C# le fichier source (getproc01.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="60c3d-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="60c3d-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="60c3d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="60c3d-107">Vous pouvez télécharger le C# le fichier source (getproc01.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="60c3d-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="60c3d-108">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="60c3d-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="60c3d-109">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="60c3d-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="60c3d-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="60c3d-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="60c3d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60c3d-111">See Also</span></span>

[<span data-ttu-id="60c3d-112">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="60c3d-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="60c3d-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="60c3d-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)