---
title: Exemple de code GetProc01 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778886"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="04f35-102">Exemple de code GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="04f35-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="04f35-103">Le code suivant illustre l’implémentation de l’applet de commande GetProc01 Sample.</span><span class="sxs-lookup"><span data-stu-id="04f35-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="04f35-104">Notez que l’applet de commande est simplifiée en laissant le travail réel de récupération du processus à la méthode [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="04f35-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="04f35-105">Vous pouvez télécharger le fichier source C# (getproc01.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="04f35-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="04f35-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="04f35-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="04f35-107">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="04f35-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="04f35-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="04f35-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="04f35-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04f35-109">See Also</span></span>

[<span data-ttu-id="04f35-110">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="04f35-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="04f35-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="04f35-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
