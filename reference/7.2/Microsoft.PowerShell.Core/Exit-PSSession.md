---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b76f7dc87105318285c930b6cd2ae4ae10c2b0e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603473"
---
# <span data-ttu-id="cf076-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-102">Exit-PSSession</span></span>

## <span data-ttu-id="cf076-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cf076-103">SYNOPSIS</span></span>
<span data-ttu-id="cf076-104">Termine une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="cf076-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="cf076-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="cf076-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="cf076-106">Description</span><span class="sxs-lookup"><span data-stu-id="cf076-106">DESCRIPTION</span></span>

<span data-ttu-id="cf076-107">L’applet de commande **Exit-PSSession** met fin aux sessions interactives que vous avez démarrées à l’aide de l’applet de commande Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="cf076-107">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="cf076-108">Vous pouvez également utiliser le mot clé **Exit** pour mettre fin à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="cf076-108">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="cf076-109">L’effet est identique à celui de **Exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="cf076-109">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="cf076-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cf076-110">EXAMPLES</span></span>

### <span data-ttu-id="cf076-111">Exemple 1 : Démarrer et arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="cf076-111">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="cf076-112">Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="cf076-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="cf076-113">Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="cf076-114">Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session PowerShell (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="cf076-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="cf076-115">Étant donné que la session interactive a été démarrée à l’aide d’une session PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="cf076-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="cf076-116">Si vous utilisez le paramètre *ComputerName* , **Enter-PSSession** crée une session temporaire qu’elle ferme quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="cf076-116">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="cf076-117">La première commande utilise l’applet de commande New-PSSession pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="cf076-117">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="cf076-118">La commande enregistre la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="cf076-118">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="cf076-119">La deuxième commande utilise **Enter-PSSession** pour démarrer une session interactive à l’aide de la session **PSSession** dans $s.</span><span class="sxs-lookup"><span data-stu-id="cf076-119">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="cf076-120">La troisième commande utilise **Exit-PSSession** pour arrêter la session interactive.</span><span class="sxs-lookup"><span data-stu-id="cf076-120">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="cf076-121">La dernière commande affiche la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="cf076-121">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="cf076-122">La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.</span><span class="sxs-lookup"><span data-stu-id="cf076-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="cf076-123">Exemple 3 : utiliser le mot clé Exit pour arrêter une session</span><span class="sxs-lookup"><span data-stu-id="cf076-123">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="cf076-124">Cet exemple utilise le mot clé **Exit** pour arrêter une session interactive démarrée à l’aide de **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="cf076-124">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="cf076-125">Le mot clé **Exit** a le même effet que l’utilisation **de Exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="cf076-125">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="cf076-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf076-126">PARAMETERS</span></span>

### <span data-ttu-id="cf076-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf076-127">CommonParameters</span></span>

<span data-ttu-id="cf076-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cf076-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf076-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cf076-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf076-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cf076-130">INPUTS</span></span>

### <span data-ttu-id="cf076-131">None</span><span class="sxs-lookup"><span data-stu-id="cf076-131">None</span></span>

<span data-ttu-id="cf076-132">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cf076-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="cf076-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cf076-133">OUTPUTS</span></span>

### <span data-ttu-id="cf076-134">None</span><span class="sxs-lookup"><span data-stu-id="cf076-134">None</span></span>

<span data-ttu-id="cf076-135">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="cf076-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="cf076-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cf076-136">NOTES</span></span>

* <span data-ttu-id="cf076-137">Cette applet de commande accepte uniquement les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="cf076-137">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="cf076-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cf076-138">RELATED LINKS</span></span>

[<span data-ttu-id="cf076-139">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="cf076-140">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="cf076-141">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="cf076-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="cf076-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="cf076-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="cf076-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="cf076-145">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="cf076-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf076-146">Remove-PSSession</span></span>](Remove-PSSession.md)

