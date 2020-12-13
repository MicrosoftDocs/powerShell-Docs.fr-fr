---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code Runspace01 (C#)
description: Exemple de code Runspace01 (C#)
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657155"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="78b0f-103">Exemple de code Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="78b0f-103">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="78b0f-104">Voici les exemples de code pour l’instance d’exécution décrite dans [création d’une application console qui exécute une commande spécifiée](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="78b0f-104">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="78b0f-105">Pour ce faire, l’application appelle une instance d’exécution, puis appelle une commande.</span><span class="sxs-lookup"><span data-stu-id="78b0f-105">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="78b0f-106">(Notez que cette application ne spécifie pas d’informations de configuration d’instance d’exécution et ne crée pas de pipeline de manière explicite).</span><span class="sxs-lookup"><span data-stu-id="78b0f-106">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="78b0f-107">La commande appelée est l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="78b0f-107">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="78b0f-108">Vous pouvez télécharger le fichier source C# (runspace01.cs) pour cette instance d’exécution à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="78b0f-108">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="78b0f-109">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="78b0f-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="78b0f-110">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="78b0f-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="78b0f-111">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="78b0f-111">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="78b0f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78b0f-112">See Also</span></span>

[<span data-ttu-id="78b0f-113">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78b0f-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="78b0f-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="78b0f-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
