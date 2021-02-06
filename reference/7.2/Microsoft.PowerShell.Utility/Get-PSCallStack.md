---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 607e3999a1dbe9a4f22a751f11ac93ee3f9d9409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596497"
---
# <span data-ttu-id="cbe96-102">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="cbe96-102">Get-PSCallStack</span></span>

## <span data-ttu-id="cbe96-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cbe96-103">SYNOPSIS</span></span>
<span data-ttu-id="cbe96-104">Affiche la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="cbe96-104">Displays the current call stack.</span></span>

## <span data-ttu-id="cbe96-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="cbe96-105">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="cbe96-106">Description</span><span class="sxs-lookup"><span data-stu-id="cbe96-106">DESCRIPTION</span></span>

<span data-ttu-id="cbe96-107">L’applet de commande **PsCallStack** affiche la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="cbe96-107">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="cbe96-108">Bien qu’elle soit conçue pour être utilisée avec le débogueur PowerShell, vous pouvez utiliser cette applet de commande pour afficher la pile des appels dans un script ou une fonction en dehors du débogueur.</span><span class="sxs-lookup"><span data-stu-id="cbe96-108">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="cbe96-109">Pour exécuter une commande **obtenir-PsCallStack** dans le débogueur, tapez `k` ou `Get-PSCallStack` .</span><span class="sxs-lookup"><span data-stu-id="cbe96-109">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="cbe96-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cbe96-110">EXAMPLES</span></span>

### <span data-ttu-id="cbe96-111">Exemple 1 : obtenir la pile des appels d’une fonction</span><span class="sxs-lookup"><span data-stu-id="cbe96-111">Example 1: Get the call stack for a function</span></span>

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

<span data-ttu-id="cbe96-112">Cette commande utilise l’applet de commande **PsCallStack** pour afficher la pile des appels pour My-alias, une fonction simple qui obtient les alias d’un nom d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cbe96-112">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="cbe96-113">La première commande entre la fonction à l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cbe96-113">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="cbe96-114">La deuxième commande utilise l'applet de commande Set-PSBreakpoint pour définir un point d'arrêt sur la fonction My-Alias.</span><span class="sxs-lookup"><span data-stu-id="cbe96-114">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="cbe96-115">La troisième commande utilise la fonction My-Alias pour obtenir tous les alias dans la session active de l'applet de commande Get-Content.</span><span class="sxs-lookup"><span data-stu-id="cbe96-115">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="cbe96-116">Le débogueur s'arrête à l'appel de la fonction.</span><span class="sxs-lookup"><span data-stu-id="cbe96-116">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="cbe96-117">Deux commandes (s) pas à pas d'entrée consécutives commencent à exécuter la fonction ligne par ligne.</span><span class="sxs-lookup"><span data-stu-id="cbe96-117">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="cbe96-118">Ensuite, une commande **PsCallStack** est utilisée pour récupérer la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="cbe96-118">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="cbe96-119">La dernière commande est une commande pas à pas de sortie (o) qui quitte le débogueur et continue d'exécuter le script jusqu'à la fin.</span><span class="sxs-lookup"><span data-stu-id="cbe96-119">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="cbe96-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbe96-120">PARAMETERS</span></span>

### <span data-ttu-id="cbe96-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbe96-121">CommonParameters</span></span>

<span data-ttu-id="cbe96-122">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cbe96-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbe96-123">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cbe96-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbe96-124">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cbe96-124">INPUTS</span></span>

### <span data-ttu-id="cbe96-125">None</span><span class="sxs-lookup"><span data-stu-id="cbe96-125">None</span></span>

<span data-ttu-id="cbe96-126">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cbe96-126">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="cbe96-127">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cbe96-127">OUTPUTS</span></span>

### <span data-ttu-id="cbe96-128">System. Management. Automation. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="cbe96-128">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="cbe96-129">La méthode **obtient-PsCallStack** retourne un objet qui représente les éléments de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="cbe96-129">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="cbe96-130">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cbe96-130">NOTES</span></span>

## <span data-ttu-id="cbe96-131">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cbe96-131">RELATED LINKS</span></span>

[<span data-ttu-id="cbe96-132">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cbe96-132">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="cbe96-133">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cbe96-133">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="cbe96-134">Format-Table</span><span class="sxs-lookup"><span data-stu-id="cbe96-134">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="cbe96-135">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cbe96-135">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="cbe96-136">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cbe96-136">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="cbe96-137">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cbe96-137">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

