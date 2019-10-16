---
title: Exemple de code GetProc01 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360438"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="7697c-102">Exemple de code GetProc01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="7697c-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="7697c-103">Le code suivant illustre l’implémentation de l’applet de commande GetProc01 Sample.</span><span class="sxs-lookup"><span data-stu-id="7697c-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="7697c-104">Notez que l’applet de commande est simplifiée en laissant le travail réel de récupération du processus à la méthode [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="7697c-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="7697c-105">Vous pouvez télécharger le C# fichier source (getproc01.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="7697c-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7697c-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7697c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7697c-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="7697c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7697c-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="7697c-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="7697c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7697c-109">See Also</span></span>

[<span data-ttu-id="7697c-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7697c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7697c-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7697c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)