---
title: Exemple deC#code RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 28cef037f56f2a101f631d3a234974a8868b4ef9
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978319"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="e2770-102">Exemple de code RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="e2770-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="e2770-103">Voici le C# code source de l’application console décrite dans la section « création d’une application console qui exécute un script spécifié ».</span><span class="sxs-lookup"><span data-stu-id="e2770-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="e2770-104">Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter un script qui récupère les informations de processus à l’aide de la liste des noms de processus passée dans le script.</span><span class="sxs-lookup"><span data-stu-id="e2770-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="e2770-105">Il montre comment passer des objets d’entrée à un script et comment récupérer des objets d’erreur ainsi que les objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="e2770-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="e2770-106">Vous pouvez télécharger le C# fichier source (runspace03.cs) pour cet exemple à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0 Framework.</span><span class="sxs-lookup"><span data-stu-id="e2770-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e2770-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e2770-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e2770-108">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="e2770-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e2770-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="e2770-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="e2770-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2770-110">See Also</span></span>

[<span data-ttu-id="e2770-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2770-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e2770-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e2770-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
