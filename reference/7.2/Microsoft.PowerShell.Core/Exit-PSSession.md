---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b1827929c53560cb261cd7b3ba1e5bd407c25700
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975088"
---
# <span data-ttu-id="fa5ca-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-102">Exit-PSSession</span></span>

## <span data-ttu-id="fa5ca-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="fa5ca-103">Synopsis</span></span>
<span data-ttu-id="fa5ca-104">Termine une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="fa5ca-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="fa5ca-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="fa5ca-106">Description</span><span class="sxs-lookup"><span data-stu-id="fa5ca-106">Description</span></span>

<span data-ttu-id="fa5ca-107">L' `Exit-PSSession` applet de commande met fin aux sessions interactives que vous avez démarrées à l’aide de la `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-107">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="fa5ca-108">Vous pouvez également utiliser le `exit` mot clé pour mettre fin à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-108">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="fa5ca-109">L’effet est le même que pour l’utilisation de `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="fa5ca-109">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="fa5ca-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="fa5ca-110">Examples</span></span>

### <span data-ttu-id="fa5ca-111">Exemple 1 : Démarrer et arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="fa5ca-111">Example 1: Start and stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="fa5ca-112">Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="fa5ca-113">Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="fa5ca-114">Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session PowerShell (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="fa5ca-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="fa5ca-115">Étant donné que la session interactive a été démarrée à l’aide d’une session PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="fa5ca-116">Si vous utilisez le paramètre _ComputerName_ , `Enter-PSSession` crée une session temporaire qu’elle ferme quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-116">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="fa5ca-117">La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-117">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="fa5ca-118">La commande enregistre la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-118">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="fa5ca-119">La deuxième commande utilise `Enter-PSSession` pour démarrer une session interactive à l’aide de la session **PSSession** dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="fa5ca-119">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="fa5ca-120">La troisième commande utilise `Exit-PSSession` pour arrêter la session interactive.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-120">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="fa5ca-121">La dernière commande affiche la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-121">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="fa5ca-122">La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="fa5ca-123">Exemple 3 : utiliser le mot clé Exit pour arrêter une session</span><span class="sxs-lookup"><span data-stu-id="fa5ca-123">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="fa5ca-124">Cet exemple utilise le `exit` mot clé pour arrêter une session interactive démarrée à l’aide de `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="fa5ca-124">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="fa5ca-125">Le `exit` mot clé a le même effet que l’utilisation de `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="fa5ca-125">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="fa5ca-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa5ca-126">Parameters</span></span>

### <span data-ttu-id="fa5ca-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fa5ca-127">CommonParameters</span></span>

<span data-ttu-id="fa5ca-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fa5ca-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fa5ca-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fa5ca-130">Entrées</span><span class="sxs-lookup"><span data-stu-id="fa5ca-130">Inputs</span></span>

### <span data-ttu-id="fa5ca-131">None</span><span class="sxs-lookup"><span data-stu-id="fa5ca-131">None</span></span>

<span data-ttu-id="fa5ca-132">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="fa5ca-133">Sorties</span><span class="sxs-lookup"><span data-stu-id="fa5ca-133">Outputs</span></span>

### <span data-ttu-id="fa5ca-134">None</span><span class="sxs-lookup"><span data-stu-id="fa5ca-134">None</span></span>

<span data-ttu-id="fa5ca-135">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="fa5ca-136">Notes</span><span class="sxs-lookup"><span data-stu-id="fa5ca-136">Notes</span></span>

<span data-ttu-id="fa5ca-137">Cette applet de commande accepte uniquement les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="fa5ca-137">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="fa5ca-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fa5ca-138">RELATED LINKS</span></span>

[<span data-ttu-id="fa5ca-139">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="fa5ca-140">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="fa5ca-141">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="fa5ca-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="fa5ca-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="fa5ca-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="fa5ca-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="fa5ca-145">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="fa5ca-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa5ca-146">Remove-PSSession</span></span>](Remove-PSSession.md)
