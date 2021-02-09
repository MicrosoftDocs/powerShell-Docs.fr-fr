---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b764aadc28d175f08fdcbaf56e904ff9310eb35b
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975071"
---
# <span data-ttu-id="4be00-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-103">Exit-PSSession</span></span>

## <span data-ttu-id="4be00-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4be00-104">Synopsis</span></span>
<span data-ttu-id="4be00-105">Termine une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="4be00-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="4be00-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4be00-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="4be00-107">Description</span><span class="sxs-lookup"><span data-stu-id="4be00-107">Description</span></span>

<span data-ttu-id="4be00-108">L' `Exit-PSSession` applet de commande met fin aux sessions interactives que vous avez démarrées à l’aide de la `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4be00-108">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="4be00-109">Vous pouvez également utiliser le `exit` mot clé pour mettre fin à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="4be00-109">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="4be00-110">L’effet est le même que pour l’utilisation de `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4be00-110">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="4be00-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="4be00-111">Examples</span></span>

### <span data-ttu-id="4be00-112">Exemple 1 : Démarrer et arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="4be00-112">Example 1: Start and stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="4be00-113">Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="4be00-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="4be00-114">Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="4be00-115">Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session PowerShell (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="4be00-115">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="4be00-116">Étant donné que la session interactive a été démarrée à l’aide d’une session PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="4be00-116">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="4be00-117">Si vous utilisez le paramètre _ComputerName_ , `Enter-PSSession` crée une session temporaire qu’elle ferme quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="4be00-117">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="4be00-118">La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="4be00-118">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="4be00-119">La commande enregistre la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="4be00-119">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="4be00-120">La deuxième commande utilise `Enter-PSSession` pour démarrer une session interactive à l’aide de la session **PSSession** dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="4be00-120">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="4be00-121">La troisième commande utilise `Exit-PSSession` pour arrêter la session interactive.</span><span class="sxs-lookup"><span data-stu-id="4be00-121">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="4be00-122">La dernière commande affiche la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="4be00-122">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="4be00-123">La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.</span><span class="sxs-lookup"><span data-stu-id="4be00-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="4be00-124">Exemple 3 : utiliser le mot clé Exit pour arrêter une session</span><span class="sxs-lookup"><span data-stu-id="4be00-124">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="4be00-125">Cet exemple utilise le `exit` mot clé pour arrêter une session interactive démarrée à l’aide de `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4be00-125">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="4be00-126">Le `exit` mot clé a le même effet que l’utilisation de `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4be00-126">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="4be00-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4be00-127">Parameters</span></span>

### <span data-ttu-id="4be00-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4be00-128">CommonParameters</span></span>

<span data-ttu-id="4be00-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4be00-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4be00-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4be00-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4be00-131">Entrées</span><span class="sxs-lookup"><span data-stu-id="4be00-131">Inputs</span></span>

### <span data-ttu-id="4be00-132">None</span><span class="sxs-lookup"><span data-stu-id="4be00-132">None</span></span>

<span data-ttu-id="4be00-133">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4be00-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4be00-134">Sorties</span><span class="sxs-lookup"><span data-stu-id="4be00-134">Outputs</span></span>

### <span data-ttu-id="4be00-135">None</span><span class="sxs-lookup"><span data-stu-id="4be00-135">None</span></span>

<span data-ttu-id="4be00-136">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="4be00-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="4be00-137">Notes</span><span class="sxs-lookup"><span data-stu-id="4be00-137">Notes</span></span>

<span data-ttu-id="4be00-138">Cette applet de commande accepte uniquement les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="4be00-138">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="4be00-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4be00-139">RELATED LINKS</span></span>

[<span data-ttu-id="4be00-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="4be00-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="4be00-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="4be00-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="4be00-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4be00-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="4be00-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="4be00-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="4be00-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="4be00-147">Remove-PSSession</span></span>](Remove-PSSession.md)
