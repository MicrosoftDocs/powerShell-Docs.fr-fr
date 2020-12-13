---
ms.date: 09/13/2016
ms.topic: reference
title: Exemples de code GetProc04
description: Exemples de code GetProc04
ms.openlocfilehash: db94eda2b3aa5fc88a3054df66f54628e1482f56
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659246"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="13e38-103">Exemples de code GetProc04</span><span class="sxs-lookup"><span data-stu-id="13e38-103">GetProc04 Code Samples</span></span>

<span data-ttu-id="13e38-104">Voici les exemples de code pour l’applet de commande GetProc04 Sample.</span><span class="sxs-lookup"><span data-stu-id="13e38-104">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="13e38-105">Il s’agit de l' `Get-Process` exemple d’applet de commande décrit dans [Ajout de rapports d’erreurs de non-terminaison à votre applet de](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)commande.</span><span class="sxs-lookup"><span data-stu-id="13e38-105">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="13e38-106">Cette `Get-Process` applet de commande appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) chaque fois qu’une exception d’opération non valide est levée lors de la récupération des informations sur le processus.</span><span class="sxs-lookup"><span data-stu-id="13e38-106">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="13e38-107">Vous pouvez télécharger le fichier source C# (getprov04.cs) pour cette Get-Proc applet de commande à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0.</span><span class="sxs-lookup"><span data-stu-id="13e38-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="13e38-108">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="13e38-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="13e38-109">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="13e38-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="13e38-110">Pour obtenir un exemple de code complet, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="13e38-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="13e38-111">Langage</span><span class="sxs-lookup"><span data-stu-id="13e38-111">Language</span></span>|<span data-ttu-id="13e38-112">Rubrique</span><span class="sxs-lookup"><span data-stu-id="13e38-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="13e38-113">C#</span><span class="sxs-lookup"><span data-stu-id="13e38-113">C#</span></span>|[<span data-ttu-id="13e38-114">Exemple de code GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="13e38-114">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="13e38-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="13e38-115">VB.NET</span></span>|[<span data-ttu-id="13e38-116">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="13e38-116">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="13e38-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13e38-117">See Also</span></span>

[<span data-ttu-id="13e38-118">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13e38-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="13e38-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="13e38-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
