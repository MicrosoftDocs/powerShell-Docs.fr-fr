---
title: GetProc04 (VB.NET) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 18f9e7a23f8b8c94aae2807a4058cb3a6f18615c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861015"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="cfdec-102">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="cfdec-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="cfdec-103">Le code suivant illustre l’implémentation d’un `Get-Process` applet de commande qui signale les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cfdec-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="cfdec-104">Cette implémentation appelle le [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode pour signaler des erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cfdec-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="cfdec-105">Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="cfdec-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="cfdec-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="cfdec-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="cfdec-107">Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="cfdec-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="cfdec-108">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="cfdec-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="cfdec-109">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="cfdec-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cfdec-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="cfdec-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="cfdec-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfdec-111">See Also</span></span>

[<span data-ttu-id="cfdec-112">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfdec-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="cfdec-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cfdec-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)