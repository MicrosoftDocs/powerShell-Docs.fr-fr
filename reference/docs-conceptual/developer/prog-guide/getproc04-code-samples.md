---
title: Exemples de code GetProc04 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771955"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="c4912-102">Exemples de code GetProc04</span><span class="sxs-lookup"><span data-stu-id="c4912-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="c4912-103">Voici les exemples de code pour l’applet de commande GetProc04 Sample.</span><span class="sxs-lookup"><span data-stu-id="c4912-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="c4912-104">Il s’agit de l' `Get-Process` exemple d’applet de commande décrit dans [Ajout de rapports d’erreurs de non-terminaison à votre applet de](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)commande.</span><span class="sxs-lookup"><span data-stu-id="c4912-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="c4912-105">Cette `Get-Process` applet de commande appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) chaque fois qu’une exception d’opération non valide est levée lors de la récupération des informations sur le processus.</span><span class="sxs-lookup"><span data-stu-id="c4912-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="c4912-106">Vous pouvez télécharger le fichier source C# (getprov04.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4912-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c4912-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c4912-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c4912-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="c4912-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="c4912-109">Pour obtenir un exemple de code complet, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="c4912-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="c4912-110">Langage</span><span class="sxs-lookup"><span data-stu-id="c4912-110">Language</span></span>|<span data-ttu-id="c4912-111">Rubrique</span><span class="sxs-lookup"><span data-stu-id="c4912-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="c4912-112">C#</span><span class="sxs-lookup"><span data-stu-id="c4912-112">C#</span></span>|[<span data-ttu-id="c4912-113">Exemple de code GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="c4912-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="c4912-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c4912-114">VB.NET</span></span>|[<span data-ttu-id="c4912-115">Exemple de code GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c4912-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="c4912-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4912-116">See Also</span></span>

[<span data-ttu-id="c4912-117">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4912-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c4912-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c4912-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
