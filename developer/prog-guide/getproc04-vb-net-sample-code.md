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
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055459"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="6084e-102">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6084e-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="6084e-103">Le code suivant illustre l’implémentation d’un `Get-Process` applet de commande qui signale les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6084e-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="6084e-104">Cette implémentation appelle le [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode pour signaler des erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6084e-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="6084e-105">Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6084e-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6084e-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6084e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6084e-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="6084e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6084e-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="6084e-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="6084e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6084e-109">See Also</span></span>

[<span data-ttu-id="6084e-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6084e-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6084e-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6084e-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)