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
ms.openlocfilehash: 8de99247574de130b91eea78b9af81dafbab48eb
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429616"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="d99fd-102">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="d99fd-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="d99fd-103">Le code suivant illustre l’implémentation d’un `Get-Process` applet de commande qui signale les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d99fd-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="d99fd-104">Cette implémentation appelle le [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode pour signaler des erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d99fd-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="d99fd-105">Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="d99fd-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d99fd-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d99fd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d99fd-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="d99fd-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d99fd-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="d99fd-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="d99fd-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d99fd-109">See Also</span></span>

[<span data-ttu-id="d99fd-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d99fd-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d99fd-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d99fd-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)