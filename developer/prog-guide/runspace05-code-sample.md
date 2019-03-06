---
title: Exemple de Code RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429565"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="1bdc2-102">Exemple de code RunSpace05</span><span class="sxs-lookup"><span data-stu-id="1bdc2-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="1bdc2-103">Voici le code source pour l’exemple Runspace05 qui est décrite dans [configuration un RunspaceConfiguration à l’aide d’instance d’exécution](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="1bdc2-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="1bdc2-104">Cet exemple montre comment créer les informations de configuration d’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une seule commande et puis exécuter le pipeline.</span><span class="sxs-lookup"><span data-stu-id="1bdc2-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="1bdc2-105">La commande est exécutée est la `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1bdc2-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="1bdc2-106">Vous pouvez télécharger le C# le fichier source (runspace05.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="1bdc2-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1bdc2-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1bdc2-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1bdc2-108">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="1bdc2-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1bdc2-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="1bdc2-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="1bdc2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bdc2-110">See Also</span></span>

[<span data-ttu-id="1bdc2-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bdc2-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1bdc2-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1bdc2-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)