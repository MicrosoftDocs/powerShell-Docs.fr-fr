---
title: Exemples de code GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417457"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="9ff27-102">Exemples de code GetProc04</span><span class="sxs-lookup"><span data-stu-id="9ff27-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="9ff27-103">Voici les exemples de code pour l’applet de commande GetProc04 Sample.</span><span class="sxs-lookup"><span data-stu-id="9ff27-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="9ff27-104">Il s’agit de l’exemple d’applet de commande `Get-Process` décrit dans [Ajout de rapports d’erreurs de non-terminaison à votre applet de](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)commande.</span><span class="sxs-lookup"><span data-stu-id="9ff27-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="9ff27-105">Cette applet de `Get-Process` appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) chaque fois qu’une exception d’opération non valide est levée lors de la récupération des informations sur le processus.</span><span class="sxs-lookup"><span data-stu-id="9ff27-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="9ff27-106">Vous pouvez télécharger le C# fichier source (getprov04.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="9ff27-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9ff27-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9ff27-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9ff27-108">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="9ff27-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="9ff27-109">Pour obtenir un exemple de code complet, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="9ff27-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="9ff27-110">Language</span><span class="sxs-lookup"><span data-stu-id="9ff27-110">Language</span></span>|<span data-ttu-id="9ff27-111">Rubrique</span><span class="sxs-lookup"><span data-stu-id="9ff27-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="9ff27-112">C#</span><span class="sxs-lookup"><span data-stu-id="9ff27-112">C#</span></span>|[<span data-ttu-id="9ff27-113">Exemple deC#code GetProc04 ()</span><span class="sxs-lookup"><span data-stu-id="9ff27-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="9ff27-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="9ff27-114">VB.NET</span></span>|[<span data-ttu-id="9ff27-115">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="9ff27-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="9ff27-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ff27-116">See Also</span></span>

[<span data-ttu-id="9ff27-117">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ff27-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9ff27-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9ff27-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
