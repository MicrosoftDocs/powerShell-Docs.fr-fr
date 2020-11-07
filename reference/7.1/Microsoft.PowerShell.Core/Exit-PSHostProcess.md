---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 368d29b7cdcbe2725399da0896eed87ddb372236
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342142"
---
# <span data-ttu-id="b7c4f-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="b7c4f-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="b7c4f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b7c4f-104">SYNOPSIS</span></span>
<span data-ttu-id="b7c4f-105">Ferme une session interactive avec un processus local.</span><span class="sxs-lookup"><span data-stu-id="b7c4f-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="b7c4f-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b7c4f-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="b7c4f-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b7c4f-107">DESCRIPTION</span></span>

<span data-ttu-id="b7c4f-108">L' `Exit-PSHostProcess` applet de commande ferme une session interactive avec un processus local que vous avez ouvert en exécutant l’applet de commande `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="b7c4f-108">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="b7c4f-109">Vous exécutez l' `Exit-PSHostProcess` applet de commande à partir du processus, lorsque vous avez terminé le débogage ou que vous dépannez un script qui s’exécute dans un processus.</span><span class="sxs-lookup"><span data-stu-id="b7c4f-109">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="b7c4f-110">À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="b7c4f-110">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="b7c4f-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b7c4f-111">EXAMPLES</span></span>

### <span data-ttu-id="b7c4f-112">Exemple 1 : quitter un processus</span><span class="sxs-lookup"><span data-stu-id="b7c4f-112">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="b7c4f-113">Dans cet exemple, vous avez travaillé dans un processus actif pour déboguer un script qui s’exécute dans une instance d’exécution dans le processus, comme décrit dans `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="b7c4f-113">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="b7c4f-114">Une fois que vous avez tapé la `exit` commande pour quitter le débogueur, exécutez l' `Exit-PSHostProcess` applet de commande pour fermer votre session interactive avec le processus.</span><span class="sxs-lookup"><span data-stu-id="b7c4f-114">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="b7c4f-115">L’applet de commande ferme votre session dans le processus et vous renvoie à l' `PS C:\>` invite.</span><span class="sxs-lookup"><span data-stu-id="b7c4f-115">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="b7c4f-116">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="b7c4f-116">PARAMETERS</span></span>

### <span data-ttu-id="b7c4f-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7c4f-117">CommonParameters</span></span>

<span data-ttu-id="b7c4f-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7c4f-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7c4f-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7c4f-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7c4f-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b7c4f-120">INPUTS</span></span>

## <span data-ttu-id="b7c4f-121">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b7c4f-121">OUTPUTS</span></span>

## <span data-ttu-id="b7c4f-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b7c4f-122">NOTES</span></span>

## <span data-ttu-id="b7c4f-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b7c4f-123">RELATED LINKS</span></span>

[<span data-ttu-id="b7c4f-124">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="b7c4f-124">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)

