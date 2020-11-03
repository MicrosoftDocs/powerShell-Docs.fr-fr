---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 315965d3103fc7064f522ca84c8aae77e90ceeb0
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200926"
---
# <span data-ttu-id="5b582-103">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="5b582-103">Get-PSCallStack</span></span>

## <span data-ttu-id="5b582-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5b582-104">SYNOPSIS</span></span>
<span data-ttu-id="5b582-105">Affiche la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="5b582-105">Displays the current call stack.</span></span>

## <span data-ttu-id="5b582-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b582-106">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="5b582-107">Description</span><span class="sxs-lookup"><span data-stu-id="5b582-107">DESCRIPTION</span></span>

<span data-ttu-id="5b582-108">L’applet de commande **PsCallStack** affiche la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="5b582-108">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="5b582-109">Bien qu’elle soit conçue pour être utilisée avec le débogueur PowerShell, vous pouvez utiliser cette applet de commande pour afficher la pile des appels dans un script ou une fonction en dehors du débogueur.</span><span class="sxs-lookup"><span data-stu-id="5b582-109">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="5b582-110">Pour exécuter une commande **obtenir-PsCallStack** dans le débogueur, tapez `k` ou `Get-PSCallStack` .</span><span class="sxs-lookup"><span data-stu-id="5b582-110">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="5b582-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5b582-111">EXAMPLES</span></span>

### <span data-ttu-id="5b582-112">Exemple 1 : obtenir la pile des appels d’une fonction</span><span class="sxs-lookup"><span data-stu-id="5b582-112">Example 1: Get the call stack for a function</span></span>

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

<span data-ttu-id="5b582-113">Cette commande utilise l’applet de commande **PsCallStack** pour afficher la pile des appels pour My-alias, une fonction simple qui obtient les alias d’un nom d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5b582-113">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="5b582-114">La première commande entre la fonction à l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b582-114">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="5b582-115">La deuxième commande utilise l'applet de commande Set-PSBreakpoint pour définir un point d'arrêt sur la fonction My-Alias.</span><span class="sxs-lookup"><span data-stu-id="5b582-115">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="5b582-116">La troisième commande utilise la fonction My-Alias pour obtenir tous les alias dans la session active de l'applet de commande Get-Content.</span><span class="sxs-lookup"><span data-stu-id="5b582-116">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="5b582-117">Le débogueur s'arrête à l'appel de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5b582-117">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="5b582-118">Deux commandes (s) pas à pas d'entrée consécutives commencent à exécuter la fonction ligne par ligne.</span><span class="sxs-lookup"><span data-stu-id="5b582-118">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="5b582-119">Ensuite, une commande **PsCallStack** est utilisée pour récupérer la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="5b582-119">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="5b582-120">La dernière commande est une commande pas à pas de sortie (o) qui quitte le débogueur et continue d'exécuter le script jusqu'à la fin.</span><span class="sxs-lookup"><span data-stu-id="5b582-120">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="5b582-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5b582-121">PARAMETERS</span></span>

### <span data-ttu-id="5b582-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b582-122">CommonParameters</span></span>

<span data-ttu-id="5b582-123">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b582-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b582-124">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b582-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b582-125">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5b582-125">INPUTS</span></span>

### <span data-ttu-id="5b582-126">Aucun</span><span class="sxs-lookup"><span data-stu-id="5b582-126">None</span></span>

<span data-ttu-id="5b582-127">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5b582-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5b582-128">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5b582-128">OUTPUTS</span></span>

### <span data-ttu-id="5b582-129">System. Management. Automation. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="5b582-129">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="5b582-130">La méthode **obtient-PsCallStack** retourne un objet qui représente les éléments de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="5b582-130">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="5b582-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5b582-131">NOTES</span></span>

## <span data-ttu-id="5b582-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5b582-132">RELATED LINKS</span></span>

[<span data-ttu-id="5b582-133">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="5b582-133">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="5b582-134">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="5b582-134">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="5b582-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="5b582-135">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="5b582-136">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="5b582-136">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="5b582-137">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="5b582-137">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="5b582-138">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="5b582-138">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
