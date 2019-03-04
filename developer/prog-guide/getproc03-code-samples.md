---
title: Exemples de Code GetProc03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857305"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="3ba6c-102">Exemples de code GetProc03</span><span class="sxs-lookup"><span data-stu-id="3ba6c-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="3ba6c-103">Voici les exemples de code pour l’applet de commande GetProc03 exemple.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="3ba6c-104">Il s’agit du `Get-Process` exemple d’applet de commande décrites dans [ajoutant des paramètres de cette entrée de Pipeline de processus](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="3ba6c-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="3ba6c-105">Cela `Get-Process` applet de commande utilise un `Name` paramètre qui accepte les entrées à partir d’un objet de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis, puis affiche des informations sur les processus à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba6c-106">Vous pouvez télécharger le C# le fichier source (getprov03.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3ba6c-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3ba6c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="3ba6c-108">Vous pouvez télécharger le C# le fichier source (getprov03.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3ba6c-109">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3ba6c-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3ba6c-110">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="3ba6c-111">Pour l’exemple de code complet, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="3ba6c-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="3ba6c-112">Langue</span><span class="sxs-lookup"><span data-stu-id="3ba6c-112">Language</span></span>|<span data-ttu-id="3ba6c-113">Rubrique</span><span class="sxs-lookup"><span data-stu-id="3ba6c-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="3ba6c-114">C#</span><span class="sxs-lookup"><span data-stu-id="3ba6c-114">C#</span></span>|[<span data-ttu-id="3ba6c-115">GetProc03 (C#) exemple de Code</span><span class="sxs-lookup"><span data-stu-id="3ba6c-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="3ba6c-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="3ba6c-116">VB.NET</span></span>|[<span data-ttu-id="3ba6c-117">GetProc03 exemple de Code (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="3ba6c-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="3ba6c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ba6c-118">See Also</span></span>

[<span data-ttu-id="3ba6c-119">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ba6c-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3ba6c-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3ba6c-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)