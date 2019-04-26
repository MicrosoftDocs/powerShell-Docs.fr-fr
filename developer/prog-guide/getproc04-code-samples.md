---
title: Exemples de Code GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081663"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="aa24d-102">Exemples de code GetProc04</span><span class="sxs-lookup"><span data-stu-id="aa24d-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="aa24d-103">Voici les exemples de code pour l’applet de commande GetProc04 exemple.</span><span class="sxs-lookup"><span data-stu-id="aa24d-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="aa24d-104">Il s’agit du `Get-Process` exemple d’applet de commande décrites dans [ajoutant les rapports d’erreurs à votre applet de commande](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="aa24d-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="aa24d-105">Cela `Get-Process` applet de commande appelle le [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode chaque fois qu’une exception d’opération non valide est levée lors de la récupération des informations de processus.</span><span class="sxs-lookup"><span data-stu-id="aa24d-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="aa24d-106">Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="aa24d-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="aa24d-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="aa24d-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="aa24d-108">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="aa24d-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="aa24d-109">Pour l’exemple de code complet, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="aa24d-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="aa24d-110">Language</span><span class="sxs-lookup"><span data-stu-id="aa24d-110">Language</span></span>|<span data-ttu-id="aa24d-111">Rubrique</span><span class="sxs-lookup"><span data-stu-id="aa24d-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="aa24d-112">C#</span><span class="sxs-lookup"><span data-stu-id="aa24d-112">C#</span></span>|[<span data-ttu-id="aa24d-113">GetProc04 (C#) exemple de Code</span><span class="sxs-lookup"><span data-stu-id="aa24d-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="aa24d-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="aa24d-114">VB.NET</span></span>|[<span data-ttu-id="aa24d-115">GetProc04 exemple de Code (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="aa24d-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="aa24d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa24d-116">See Also</span></span>

[<span data-ttu-id="aa24d-117">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa24d-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="aa24d-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="aa24d-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)