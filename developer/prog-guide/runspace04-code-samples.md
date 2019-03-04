---
title: Exemples de Code RunSpace04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: 10f236b201920d2d456af41328c7a62a9e14b571
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861095"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="6795a-102">Exemples de code RunSpace04</span><span class="sxs-lookup"><span data-stu-id="6795a-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="6795a-103">Voici un exemple de code pour une instance d’exécution qui utilise le [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe pour exécuter un script qui génère une erreur avec fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6795a-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="6795a-104">L’application hôte est responsable de l’interception de l’erreur et l’interprétation de l’enregistrement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6795a-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="6795a-105">Vous pouvez télécharger le fichier de source VB.NET (Runspace04.vb) pour cette instance d’exécution à l’aide du Kit du développement de logiciel Windows pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6795a-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6795a-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6795a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6795a-107">Vous pouvez télécharger le fichier de source VB.NET (Runspace04.vb) pour cette instance d’exécution à l’aide du Kit du développement de logiciel Windows pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6795a-107">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6795a-108">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6795a-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6795a-109">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="6795a-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="6795a-110">Pour l’exemple de code complet, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="6795a-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="6795a-111">Langue</span><span class="sxs-lookup"><span data-stu-id="6795a-111">Language</span></span>|<span data-ttu-id="6795a-112">Rubrique</span><span class="sxs-lookup"><span data-stu-id="6795a-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="6795a-113">VB.NET</span><span class="sxs-lookup"><span data-stu-id="6795a-113">VB.NET</span></span>|[<span data-ttu-id="6795a-114">Runspace01 exemple de Code (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6795a-114">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="6795a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6795a-115">See Also</span></span>

[<span data-ttu-id="6795a-116">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6795a-116">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6795a-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6795a-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)