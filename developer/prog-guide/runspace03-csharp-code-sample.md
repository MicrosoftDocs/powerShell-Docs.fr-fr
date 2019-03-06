---
title: RunSpace03 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429905"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="28bf2-102">Exemple de code RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="28bf2-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="28bf2-103">Voici le C# code source pour l’application de console décrite dans [création d’une Console Application qui s’exécute un Script spécifié](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="28bf2-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="28bf2-104">Cet exemple utilise le [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe pour exécuter un script qui Récupère traite les informations à l’aide de la liste des noms de processus passés dans le script.</span><span class="sxs-lookup"><span data-stu-id="28bf2-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="28bf2-105">Il montre comment passer des objets d’entrée à un script et comment récupérer des objets d’erreur, ainsi que les objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="28bf2-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="28bf2-106">Vous pouvez télécharger le C# le fichier source (runspace03.cs) pour cet exemple en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="28bf2-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="28bf2-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="28bf2-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="28bf2-108">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="28bf2-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="28bf2-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="28bf2-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="28bf2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28bf2-110">See Also</span></span>

[<span data-ttu-id="28bf2-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="28bf2-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="28bf2-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="28bf2-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)