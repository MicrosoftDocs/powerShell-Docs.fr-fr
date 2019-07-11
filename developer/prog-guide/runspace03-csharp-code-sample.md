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
ms.openlocfilehash: e1fc91174a959d6acc306330afb8d5c2e7a9a860
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735006"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="94a2f-102">Exemple de code RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="94a2f-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="94a2f-103">Voici le C# code source pour l’application de console décrite dans [création d’une Console Application qui s’exécute un Script spécifié](fd).</span><span class="sxs-lookup"><span data-stu-id="94a2f-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](fd).</span></span> <span data-ttu-id="94a2f-104">Cet exemple utilise le [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe pour exécuter un script qui Récupère traite les informations à l’aide de la liste des noms de processus passés dans le script.</span><span class="sxs-lookup"><span data-stu-id="94a2f-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="94a2f-105">Il montre comment passer des objets d’entrée à un script et comment récupérer des objets d’erreur, ainsi que les objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="94a2f-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="94a2f-106">Vous pouvez télécharger le C# le fichier source (runspace03.cs) pour cet exemple en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="94a2f-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="94a2f-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="94a2f-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="94a2f-108">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="94a2f-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="94a2f-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="94a2f-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="94a2f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94a2f-110">See Also</span></span>

[<span data-ttu-id="94a2f-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94a2f-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="94a2f-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="94a2f-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)