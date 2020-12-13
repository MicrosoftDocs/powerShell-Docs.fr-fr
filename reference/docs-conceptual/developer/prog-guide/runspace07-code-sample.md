---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code RunSpace07
description: Exemple de code RunSpace07
ms.openlocfilehash: 6e8c9f48a6e9c5a642ecf93bca8a85003b3cfbf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647389"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="4fdd0-103">Exemple de code RunSpace07</span><span class="sxs-lookup"><span data-stu-id="4fdd0-103">RunSpace07 Code Sample</span></span>

<span data-ttu-id="4fdd0-104">Voici le code source de l’exemple Runspace07 décrit dans [création d’une application console qui ajoute des commandes à un pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="4fdd0-104">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="4fdd0-105">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="4fdd0-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="4fdd0-106">Les commandes ajoutées au pipeline sont les `Get-Process` applets de commande et `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="4fdd0-106">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="4fdd0-107">Vous pouvez télécharger le fichier source C# (runspace07.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="4fdd0-107">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4fdd0-108">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4fdd0-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4fdd0-109">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="4fdd0-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4fdd0-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="4fdd0-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="4fdd0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fdd0-111">See Also</span></span>

[<span data-ttu-id="4fdd0-112">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4fdd0-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4fdd0-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4fdd0-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
