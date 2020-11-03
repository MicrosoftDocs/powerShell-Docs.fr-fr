---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 4e0b79cae4af290c64f579217a3731aaac401d6d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200838"
---
# <span data-ttu-id="8f2d4-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-103">Exit-PSSession</span></span>

## <span data-ttu-id="8f2d4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8f2d4-104">SYNOPSIS</span></span>
<span data-ttu-id="8f2d4-105">Termine une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="8f2d4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8f2d4-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="8f2d4-107">Description</span><span class="sxs-lookup"><span data-stu-id="8f2d4-107">DESCRIPTION</span></span>

<span data-ttu-id="8f2d4-108">L’applet de commande **Exit-PSSession** met fin aux sessions interactives que vous avez démarrées à l’aide de l’applet de commande Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="8f2d4-109">Vous pouvez également utiliser le mot clé **Exit** pour mettre fin à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="8f2d4-110">L’effet est identique à celui de **Exit-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="8f2d4-110">The effect is the same as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="8f2d4-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8f2d4-111">EXAMPLES</span></span>

### <span data-ttu-id="8f2d4-112">Exemple 1 : Démarrer et arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="8f2d4-112">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="8f2d4-113">Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="8f2d4-114">Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="8f2d4-115">Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session PowerShell ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="8f2d4-115">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="8f2d4-116">Étant donné que la session interactive a été démarrée à l’aide d’une session PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-116">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="8f2d4-117">Si vous utilisez le paramètre *ComputerName* , **Enter-PSSession** crée une session temporaire qu’elle ferme quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="8f2d4-118">La première commande utilise l’applet de commande New-PSSession pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="8f2d4-119">La commande enregistre la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="8f2d4-120">La deuxième commande utilise **Enter-PSSession** pour démarrer une session interactive à l’aide de la session **PSSession** dans $s.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="8f2d4-121">La troisième commande utilise **Exit-PSSession** pour arrêter la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="8f2d4-122">La dernière commande affiche la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="8f2d4-123">La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="8f2d4-124">Exemple 3 : utiliser le mot clé Exit pour arrêter une session</span><span class="sxs-lookup"><span data-stu-id="8f2d4-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="8f2d4-125">Cet exemple utilise le mot clé **Exit** pour arrêter une session interactive démarrée à l’aide de **Enter-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="8f2d4-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession** .</span></span>
<span data-ttu-id="8f2d4-126">Le mot clé **Exit** a le même effet que l’utilisation **de Exit-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="8f2d4-126">The **Exit** keyword has the same effect as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="8f2d4-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8f2d4-127">PARAMETERS</span></span>

### <span data-ttu-id="8f2d4-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8f2d4-128">CommonParameters</span></span>

<span data-ttu-id="8f2d4-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8f2d4-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8f2d4-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8f2d4-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8f2d4-131">INPUTS</span></span>

### <span data-ttu-id="8f2d4-132">Aucun</span><span class="sxs-lookup"><span data-stu-id="8f2d4-132">None</span></span>

<span data-ttu-id="8f2d4-133">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="8f2d4-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8f2d4-134">OUTPUTS</span></span>

### <span data-ttu-id="8f2d4-135">Aucun</span><span class="sxs-lookup"><span data-stu-id="8f2d4-135">None</span></span>

<span data-ttu-id="8f2d4-136">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="8f2d4-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8f2d4-137">NOTES</span></span>

* <span data-ttu-id="8f2d4-138">Cette applet de commande accepte uniquement les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="8f2d4-138">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="8f2d4-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8f2d4-139">RELATED LINKS</span></span>

[<span data-ttu-id="8f2d4-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="8f2d4-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="8f2d4-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="8f2d4-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="8f2d4-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8f2d4-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="8f2d4-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="8f2d4-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="8f2d4-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="8f2d4-147">Remove-PSSession</span></span>](Remove-PSSession.md)
