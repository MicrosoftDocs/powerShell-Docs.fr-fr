---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: a1a8c6fcc16bcddc3bfcdade56cd75aadd179b74
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603661"
---
# <span data-ttu-id="8df63-102">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="8df63-102">Exit-PSHostProcess</span></span>

## <span data-ttu-id="8df63-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8df63-103">SYNOPSIS</span></span>
<span data-ttu-id="8df63-104">Ferme une session interactive avec un processus local.</span><span class="sxs-lookup"><span data-stu-id="8df63-104">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="8df63-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8df63-105">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="8df63-106">Description</span><span class="sxs-lookup"><span data-stu-id="8df63-106">DESCRIPTION</span></span>

<span data-ttu-id="8df63-107">L' `Exit-PSHostProcess` applet de commande ferme une session interactive avec un processus local que vous avez ouvert en exécutant l’applet de commande `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="8df63-107">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="8df63-108">Vous exécutez l' `Exit-PSHostProcess` applet de commande à partir du processus, lorsque vous avez terminé le débogage ou que vous dépannez un script qui s’exécute dans un processus.</span><span class="sxs-lookup"><span data-stu-id="8df63-108">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="8df63-109">À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="8df63-109">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="8df63-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8df63-110">EXAMPLES</span></span>

### <span data-ttu-id="8df63-111">Exemple 1 : quitter un processus</span><span class="sxs-lookup"><span data-stu-id="8df63-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="8df63-112">Dans cet exemple, vous avez travaillé dans un processus actif pour déboguer un script qui s’exécute dans une instance d’exécution dans le processus, comme décrit dans `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="8df63-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="8df63-113">Une fois que vous avez tapé la `exit` commande pour quitter le débogueur, exécutez l' `Exit-PSHostProcess` applet de commande pour fermer votre session interactive avec le processus.</span><span class="sxs-lookup"><span data-stu-id="8df63-113">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="8df63-114">L’applet de commande ferme votre session dans le processus et vous renvoie à l' `PS C:\>` invite.</span><span class="sxs-lookup"><span data-stu-id="8df63-114">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="8df63-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8df63-115">PARAMETERS</span></span>

### <span data-ttu-id="8df63-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8df63-116">CommonParameters</span></span>

<span data-ttu-id="8df63-117">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8df63-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8df63-118">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8df63-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8df63-119">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8df63-119">INPUTS</span></span>

## <span data-ttu-id="8df63-120">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8df63-120">OUTPUTS</span></span>

## <span data-ttu-id="8df63-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8df63-121">NOTES</span></span>

## <span data-ttu-id="8df63-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8df63-122">RELATED LINKS</span></span>

[<span data-ttu-id="8df63-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="8df63-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)

