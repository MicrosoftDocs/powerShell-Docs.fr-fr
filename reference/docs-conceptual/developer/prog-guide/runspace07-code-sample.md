---
title: Exemple de code RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: ab68f96372f20a435217702c7f3ebde3de633919
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360148"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="f2024-102">Exemple de code RunSpace07</span><span class="sxs-lookup"><span data-stu-id="f2024-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="f2024-103">Voici le code source de l’exemple Runspace07 décrit dans [création d’une application console qui ajoute des commandes à un pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="f2024-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="f2024-104">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f2024-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="f2024-105">Les commandes ajoutées au pipeline sont les applets de commande `Get-Process` et `Measure-Object`.</span><span class="sxs-lookup"><span data-stu-id="f2024-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="f2024-106">Vous pouvez télécharger le C# fichier source (runspace07.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2024-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f2024-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f2024-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f2024-108">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="f2024-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f2024-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="f2024-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="f2024-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2024-110">See Also</span></span>

[<span data-ttu-id="f2024-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2024-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f2024-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f2024-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
