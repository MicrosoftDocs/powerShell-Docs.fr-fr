---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 1e0c8413a37a9b8877b6af9089ac311459ada20d
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975105"
---
# <span data-ttu-id="20f02-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-103">Exit-PSSession</span></span>

## <span data-ttu-id="20f02-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="20f02-104">Synopsis</span></span>
<span data-ttu-id="20f02-105">Termine une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="20f02-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="20f02-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="20f02-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="20f02-107">Description</span><span class="sxs-lookup"><span data-stu-id="20f02-107">Description</span></span>

<span data-ttu-id="20f02-108">L' `Exit-PSSession` applet de commande met fin aux sessions interactives que vous avez démarrées à l’aide de la `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20f02-108">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="20f02-109">Vous pouvez également utiliser le `exit` mot clé pour mettre fin à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="20f02-109">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="20f02-110">L’effet est le même que pour l’utilisation de `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="20f02-110">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="20f02-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="20f02-111">Examples</span></span>

### <span data-ttu-id="20f02-112">Exemple 1 : Démarrer et arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="20f02-112">Example 1: Start and stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS C:\>
```

<span data-ttu-id="20f02-113">Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="20f02-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="20f02-114">Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="20f02-115">Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session Windows PowerShell (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="20f02-115">These commands start and stop an interactive session with the Server01 computer that uses a Windows PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="20f02-116">Étant donné que la session interactive a été démarrée à l’aide d’une session Windows PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="20f02-116">Because the interactive session was started by using a Windows PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="20f02-117">Si vous utilisez le paramètre _ComputerName_ , `Enter-PSSession` crée une session temporaire qu’elle ferme quand la session interactive se termine.</span><span class="sxs-lookup"><span data-stu-id="20f02-117">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="20f02-118">La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="20f02-118">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="20f02-119">La commande enregistre la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="20f02-119">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="20f02-120">La deuxième commande utilise `Enter-PSSession` pour démarrer une session interactive à l’aide de la session **PSSession** dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="20f02-120">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="20f02-121">La troisième commande utilise `Exit-PSSession` pour arrêter la session interactive.</span><span class="sxs-lookup"><span data-stu-id="20f02-121">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="20f02-122">La dernière commande affiche la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="20f02-122">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="20f02-123">La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.</span><span class="sxs-lookup"><span data-stu-id="20f02-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="20f02-124">Exemple 3 : utiliser le mot clé Exit pour arrêter une session</span><span class="sxs-lookup"><span data-stu-id="20f02-124">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS C:\>
```

<span data-ttu-id="20f02-125">Cet exemple utilise le `exit` mot clé pour arrêter une session interactive démarrée à l’aide de `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="20f02-125">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="20f02-126">Le `exit` mot clé a le même effet que l’utilisation de `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="20f02-126">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="20f02-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20f02-127">Parameters</span></span>

### <span data-ttu-id="20f02-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20f02-128">CommonParameters</span></span>

<span data-ttu-id="20f02-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20f02-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20f02-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="20f02-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20f02-131">Entrées</span><span class="sxs-lookup"><span data-stu-id="20f02-131">Inputs</span></span>

### <span data-ttu-id="20f02-132">None</span><span class="sxs-lookup"><span data-stu-id="20f02-132">None</span></span>

<span data-ttu-id="20f02-133">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="20f02-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="20f02-134">Sorties</span><span class="sxs-lookup"><span data-stu-id="20f02-134">Outputs</span></span>

### <span data-ttu-id="20f02-135">None</span><span class="sxs-lookup"><span data-stu-id="20f02-135">None</span></span>

<span data-ttu-id="20f02-136">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="20f02-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="20f02-137">Notes</span><span class="sxs-lookup"><span data-stu-id="20f02-137">Notes</span></span>

<span data-ttu-id="20f02-138">Cette applet de commande accepte uniquement les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="20f02-138">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="20f02-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="20f02-139">RELATED LINKS</span></span>

[<span data-ttu-id="20f02-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="20f02-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="20f02-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="20f02-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="20f02-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="20f02-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="20f02-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="20f02-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="20f02-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="20f02-147">Remove-PSSession</span></span>](Remove-PSSession.md)
