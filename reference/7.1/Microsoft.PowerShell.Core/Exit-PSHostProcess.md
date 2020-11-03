---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: b7e2bf7cff84e92f4c174ef01861ee5c0a822bea
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200955"
---
# <span data-ttu-id="32100-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="32100-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="32100-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="32100-104">SYNOPSIS</span></span>
<span data-ttu-id="32100-105">Ferme une session interactive avec un processus local.</span><span class="sxs-lookup"><span data-stu-id="32100-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="32100-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32100-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="32100-107">Description</span><span class="sxs-lookup"><span data-stu-id="32100-107">DESCRIPTION</span></span>

<span data-ttu-id="32100-108">L’applet de commande **Exit-PSHostProcess** ferme une session interactive avec un processus local que vous avez ouvert en exécutant l’applet de commande Enter-PSHostProcess.</span><span class="sxs-lookup"><span data-stu-id="32100-108">The **Exit-PSHostProcess** cmdlet closes an interactive session with a local process that you have opened by running the Enter-PSHostProcess cmdlet.</span></span> <span data-ttu-id="32100-109">Vous exécutez l’applet de commande **Exit-PSHostProcess** à partir du processus, lorsque vous avez terminé le débogage ou que vous dépannez un script qui s’exécute dans un processus.</span><span class="sxs-lookup"><span data-stu-id="32100-109">You run the **Exit-PSHostProcess** cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span>

## <span data-ttu-id="32100-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="32100-110">EXAMPLES</span></span>

### <span data-ttu-id="32100-111">Exemple 1 : quitter un processus</span><span class="sxs-lookup"><span data-stu-id="32100-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="32100-112">Dans cet exemple, vous avez travaillé dans un processus actif pour déboguer un script qui s’exécute dans une instance d’exécution dans le processus, comme décrit dans Enter-PSHostProcess.</span><span class="sxs-lookup"><span data-stu-id="32100-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in Enter-PSHostProcess.</span></span> <span data-ttu-id="32100-113">Une fois que vous avez tapé la commande **Exit** pour quitter le débogueur, exécutez l’applet de commande **Exit-PSHostProcess** pour fermer votre session interactive avec le processus.</span><span class="sxs-lookup"><span data-stu-id="32100-113">After you type the **exit** command to exit the debugger, run the **Exit-PSHostProcess** cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="32100-114">L’applet de commande ferme votre session dans le processus et vous renvoie à l’invite PS C : \\ \> .</span><span class="sxs-lookup"><span data-stu-id="32100-114">The cmdlet closes your session in the process, and returns you to the PS C:\\\> prompt.</span></span>

## <span data-ttu-id="32100-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32100-115">PARAMETERS</span></span>

### <span data-ttu-id="32100-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32100-116">CommonParameters</span></span>

<span data-ttu-id="32100-117">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32100-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32100-118">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="32100-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32100-119">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="32100-119">INPUTS</span></span>

## <span data-ttu-id="32100-120">SORTIES</span><span class="sxs-lookup"><span data-stu-id="32100-120">OUTPUTS</span></span>

## <span data-ttu-id="32100-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="32100-121">NOTES</span></span>

## <span data-ttu-id="32100-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="32100-122">RELATED LINKS</span></span>

[<span data-ttu-id="32100-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="32100-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)

