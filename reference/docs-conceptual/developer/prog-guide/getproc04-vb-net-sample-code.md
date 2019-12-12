---
title: Exemple de code GetProc04 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416088"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="7b625-102">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="7b625-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="7b625-103">Le code suivant illustre l’implémentation d’une applet de commande `Get-Process` qui signale des erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="7b625-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="7b625-104">Cette implémentation appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="7b625-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="7b625-105">Vous pouvez télécharger le C# fichier source (getprov04.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="7b625-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7b625-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7b625-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7b625-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="7b625-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7b625-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="7b625-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="7b625-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b625-109">See Also</span></span>

[<span data-ttu-id="7b625-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b625-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7b625-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7b625-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
