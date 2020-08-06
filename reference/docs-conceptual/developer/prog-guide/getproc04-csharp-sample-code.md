---
title: Exemple de code GetProc04 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: dd3965ee504641b1b629ba203090ee14c670da43
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771887"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="61b33-102">Exemple de code GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="61b33-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="61b33-103">Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui signale des erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="61b33-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="61b33-104">Cette implémentation appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs qui ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="61b33-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="61b33-105">Vous pouvez télécharger le fichier source C# (getprov04.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="61b33-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="61b33-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="61b33-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="61b33-107">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="61b33-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="61b33-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="61b33-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a><span data-ttu-id="61b33-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61b33-109">See Also</span></span>

[<span data-ttu-id="61b33-110">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="61b33-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="61b33-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="61b33-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
