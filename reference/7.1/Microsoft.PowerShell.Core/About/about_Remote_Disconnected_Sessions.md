---
description: Explique comment se déconnecter et se reconnecter à une session PowerShell (PSSession).
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 68903485ce92a692453bfba4aa5097dd062437f9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207738"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="519a8-104">À propos des sessions déconnectées distantes</span><span class="sxs-lookup"><span data-stu-id="519a8-104">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="519a8-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="519a8-105">Short description</span></span>

<span data-ttu-id="519a8-106">Explique comment se déconnecter et se reconnecter à une session PowerShell (PSSession).</span><span class="sxs-lookup"><span data-stu-id="519a8-106">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="519a8-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="519a8-107">Long description</span></span>

<span data-ttu-id="519a8-108">À compter de PowerShell 3,0, vous pouvez vous déconnecter d’une session PSSession et vous reconnecter à la session PSSession sur le même ordinateur ou sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-108">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="519a8-109">L’état de session est conservé et les commandes de la session PSSession continuent à s’exécuter pendant que la session est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-109">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="519a8-110">La fonctionnalité sessions déconnectées n’est disponible que lorsque l’ordinateur distant exécute PowerShell 3,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="519a8-110">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="519a8-111">La fonctionnalité sessions déconnectées vous permet de fermer la session dans laquelle une session PSSession a été créée, et même de fermer PowerShell et d’arrêter l’ordinateur, sans interrompre les commandes qui s’exécutent dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="519a8-111">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="519a8-112">Les sessions déconnectées sont utiles pour exécuter des commandes qui prennent beaucoup de temps et fournissent la flexibilité du temps et des appareils requis par les professionnels de l’informatique.</span><span class="sxs-lookup"><span data-stu-id="519a8-112">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="519a8-113">Vous ne pouvez pas vous déconnecter d’une session interactive démarrée à l’aide de l’applet de commande `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-113">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="519a8-114">Vous pouvez utiliser des sessions déconnectées pour gérer des sessions PSSession qui ont été déconnectés involontairement suite à une panne de réseau ou d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-114">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="519a8-115">Dans l’utilisation réelle, la fonctionnalité sessions déconnectées vous permet de commencer à résoudre un problème, d’attirer votre attention sur un problème de priorité plus élevée, puis de reprendre le travail sur la solution, même sur un autre ordinateur situé à un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="519a8-115">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="519a8-116">Applets de commande de session déconnectée</span><span class="sxs-lookup"><span data-stu-id="519a8-116">Disconnected session cmdlets</span></span>

<span data-ttu-id="519a8-117">Les applets de commande suivantes prennent en charge la fonctionnalité sessions déconnectées :</span><span class="sxs-lookup"><span data-stu-id="519a8-117">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="519a8-118">`Connect-PSSession`: Se connecte à une session PSSession déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-118">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="519a8-119">`Disconnect-PSSession`: Déconnecte une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="519a8-119">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="519a8-120">`Get-PSSession`: Obtient sessions PSSession sur l’ordinateur local ou sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="519a8-120">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="519a8-121">`Receive-PSSession`: Obtient les résultats des commandes exécutées dans des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="519a8-121">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="519a8-122">`Invoke-Command`: Le paramètre **InDisconnectedSession** crée une session PSSession et se déconnecte immédiatement.</span><span class="sxs-lookup"><span data-stu-id="519a8-122">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="519a8-123">Fonctionnement de la fonctionnalité sessions déconnectées</span><span class="sxs-lookup"><span data-stu-id="519a8-123">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="519a8-124">À compter de PowerShell 3,0, les sessions PSSession sont indépendants des sessions dans lesquelles ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="519a8-124">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="519a8-125">Les sessions PSSession actifs sont conservés sur l’ordinateur distant ou **côté serveur** de la connexion, même si la session dans laquelle la session PSSession a été créée est fermée et que l’ordinateur d’origine est arrêté ou déconnecté du réseau.</span><span class="sxs-lookup"><span data-stu-id="519a8-125">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="519a8-126">Dans PowerShell 2,0, la session PSSession est supprimée de l’ordinateur distant lorsqu’elle est déconnectée de la session d’origine ou que la session dans laquelle elle a été créée se termine.</span><span class="sxs-lookup"><span data-stu-id="519a8-126">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="519a8-127">Lorsque vous déconnectez une session PSSession, la session PSSession reste active et est conservée sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="519a8-127">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="519a8-128">L’état de session passe de **en cours d’exécution** à **déconnecté** .</span><span class="sxs-lookup"><span data-stu-id="519a8-128">The session state changes from **Running** to **Disconnected** .</span></span> <span data-ttu-id="519a8-129">Vous pouvez vous reconnecter à une session PSSession déconnectée à partir de la session active ou d’une autre session sur le même ordinateur ou à partir d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-129">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="519a8-130">L’ordinateur distant qui gère la session doit être en cours d’exécution et être connecté au réseau.</span><span class="sxs-lookup"><span data-stu-id="519a8-130">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="519a8-131">Les commandes d’une session PSSession déconnectée continuent à s’exécuter sans interruption sur l’ordinateur distant jusqu’à ce que la commande soit terminée ou que la mémoire tampon de sortie soit remplie.</span><span class="sxs-lookup"><span data-stu-id="519a8-131">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="519a8-132">Pour empêcher une mémoire tampon de sortie complète d’interrompre une commande, utilisez le paramètre **OutputBufferingMode** des `Disconnect-PSSession` applets de commande, `New-PSSessionOption` ou `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="519a8-132">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="519a8-133">Les sessions déconnectées sont conservées dans l’état déconnecté sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="519a8-133">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="519a8-134">Ils sont disponibles pour vous reconnecter, jusqu’à ce que vous supprimiez la session PSSession, par exemple à l’aide de l’applet de commande `Remove-PSSession` , ou jusqu’à ce que le délai d’inactivité de la session PSSession arrive à expiration.</span><span class="sxs-lookup"><span data-stu-id="519a8-134">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="519a8-135">Vous pouvez ajuster le délai d’inactivité d’une session PSSession à l’aide des paramètres **IdleTimeoutSec** ou **IdleTimeout** des `Disconnect-PSSession` applets de commande, `New-PSSessionOption` ou `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="519a8-135">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="519a8-136">Un autre utilisateur peut se connecter à sessions PSSession que vous avez créé, mais uniquement s’il peut fournir les informations d’identification qui ont été utilisées pour créer la session, ou utiliser les `RunAs` informations d’identification de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-136">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="519a8-137">Obtention de sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="519a8-137">How to get PSSessions</span></span>

<span data-ttu-id="519a8-138">À compter de PowerShell 3,0, l' `Get-PSSession` applet de commande obtient sessions PSSession sur l’ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="519a8-138">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="519a8-139">Il peut également recevoir des sessions PSSession qui ont été créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="519a8-139">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="519a8-140">Pour accéder à sessions PSSession sur l’ordinateur local ou les ordinateurs distants, utilisez les paramètres **ComputerName** ou **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="519a8-140">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="519a8-141">Sans paramètres, `Get-PSSession` obtient PSSession qui a été créé dans la session locale, quel que soit l’emplacement où elles se terminent.</span><span class="sxs-lookup"><span data-stu-id="519a8-141">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="519a8-142">Lorsque vous obtenez des sessions PSSession, n’oubliez pas de les Rechercher sur l’ordinateur sur lequel ils sont conservés, c’est-à-dire sur l’ordinateur distant ou **côté serveur** .</span><span class="sxs-lookup"><span data-stu-id="519a8-142">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="519a8-143">Par exemple, si vous créez une session PSSession sur l’ordinateur Serveur01, récupérez la session à partir de l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="519a8-143">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="519a8-144">Si vous créez une session PSSession à partir d’un autre ordinateur sur l’ordinateur local, récupérez la session à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="519a8-144">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="519a8-145">La séquence de commandes suivante montre comment `Get-PSSession` fonctionne.</span><span class="sxs-lookup"><span data-stu-id="519a8-145">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="519a8-146">La première commande crée une session sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="519a8-146">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="519a8-147">La session se trouve sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="519a8-147">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="519a8-148">Pour obtenir la session, utilisez le paramètre **ComputerName** de `Get-PSSession` avec la valeur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="519a8-148">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="519a8-149">Si la valeur du paramètre **ComputerName** de `Get-PSSession` est localhost, `Get-PSSession` obtient les sessions PSSession qui se terminent à et sont conservés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="519a8-149">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="519a8-150">Elle n’obtient pas de sessions PSSession sur l’ordinateur Serveur01, même si elles ont été démarrées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="519a8-150">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="519a8-151">Pour récupérer les sessions qui ont été créées dans la session active, utilisez l’applet de commande `Get-PSSession` sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="519a8-151">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="519a8-152">Dans cet exemple, `Get-PSSession` obtient la session PSSession créée dans la session active et se connecte à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="519a8-152">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="519a8-153">Comment déconnecter des sessions</span><span class="sxs-lookup"><span data-stu-id="519a8-153">How to disconnect sessions</span></span>

<span data-ttu-id="519a8-154">Pour déconnecter une session PSSession, utilisez l’applet de commande `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-154">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="519a8-155">Pour identifier la session PSSession, utilisez le paramètre de **session** ou le pipeline a PSSession des `New-PSSession` applets de commande ou `Get-PSSession` à `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-155">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="519a8-156">La commande suivante déconnecte la session PSSession à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="519a8-156">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="519a8-157">Notez que la valeur de la propriété **State** est **Disconnected** et que la **disponibilité** est **None** .</span><span class="sxs-lookup"><span data-stu-id="519a8-157">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None** .</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="519a8-158">Pour créer une session déconnectée, utilisez le paramètre **InDisconnectedSession** de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="519a8-158">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="519a8-159">Il crée une session, démarre la commande et se déconnecte immédiatement, avant que la commande puisse retourner une sortie.</span><span class="sxs-lookup"><span data-stu-id="519a8-159">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="519a8-160">La commande suivante exécute une `Get-WinEvent` commande dans une session déconnectée sur l’ordinateur distant SERVER02.</span><span class="sxs-lookup"><span data-stu-id="519a8-160">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="519a8-161">Comment se connecter à des sessions déconnectées</span><span class="sxs-lookup"><span data-stu-id="519a8-161">How to connect to disconnected sessions</span></span>

<span data-ttu-id="519a8-162">Vous pouvez vous connecter à n’importe quelle session PSSession déconnectée à partir de la session dans laquelle vous avez créé la session PSSession ou d’autres sessions sur l’ordinateur local ou sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="519a8-162">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="519a8-163">Vous pouvez créer une session PSSession, exécuter des commandes dans la session PSSession, vous déconnecter de la session PSSession, fermer PowerShell et arrêter l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-163">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="519a8-164">Quelques heures plus tard, vous pouvez ouvrir un autre ordinateur, obtenir la session PSSession, vous y connecter et obtenir les résultats des commandes exécutées dans la session PSSession pendant qu’elle était déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-164">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="519a8-165">Vous pouvez ensuite exécuter d’autres commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="519a8-165">Then you can run more commands in the session.</span></span>

<span data-ttu-id="519a8-166">Pour connecter une session PSSession déconnectée, utilisez l’applet de commande `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-166">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="519a8-167">Utilisez les paramètres **ComputerName** ou **ConnectionUri** pour identifier la session PSSession ou le pipeline d’une session PSSession `Get-PSSession` `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-167">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="519a8-168">La commande suivante obtient les sessions sur l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="519a8-168">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="519a8-169">La sortie comprend deux sessions déconnectées, qui sont toutes deux disponibles.</span><span class="sxs-lookup"><span data-stu-id="519a8-169">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="519a8-170">La commande suivante permet de se connecter à session2.</span><span class="sxs-lookup"><span data-stu-id="519a8-170">The following command connects to Session2.</span></span> <span data-ttu-id="519a8-171">La session PSSession est maintenant ouverte et disponible.</span><span class="sxs-lookup"><span data-stu-id="519a8-171">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="519a8-172">Obtention des résultats</span><span class="sxs-lookup"><span data-stu-id="519a8-172">How to get the results</span></span>

<span data-ttu-id="519a8-173">Pour obtenir les résultats des commandes exécutées dans une session PSSession déconnectée, utilisez l’applet de commande `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-173">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="519a8-174">Vous pouvez utiliser `Receive-PSSession` plutôt que l’applet de commande `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-174">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="519a8-175">Si la session est déjà reconnectée, `Receive-PSSession` obtient les résultats des commandes exécutées lorsque la session a été déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-175">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="519a8-176">Si la session PSSession est toujours déconnectée, `Receive-PSSession` se connecte à celle-ci, puis obtient les résultats des commandes qui ont été exécutées pendant qu’elle a été déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-176">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="519a8-177">`Receive-PSSession` peut retourner les résultats dans un travail (de façon asynchrone) ou au programme hôte (de façon synchrone).</span><span class="sxs-lookup"><span data-stu-id="519a8-177">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="519a8-178">Utilisez le paramètre **distarget** pour sélectionner un **travail** ou un **hôte** .</span><span class="sxs-lookup"><span data-stu-id="519a8-178">Use the **OutTarget** parameter to select **Job** or **Host** .</span></span> <span data-ttu-id="519a8-179">La valeur par défaut est **Host** .</span><span class="sxs-lookup"><span data-stu-id="519a8-179">The default value is **Host** .</span></span> <span data-ttu-id="519a8-180">Toutefois, si la commande en cours de réception a été démarrée dans la session active en tant que **tâche** , elle est retournée par défaut en tant que **tâche** .</span><span class="sxs-lookup"><span data-stu-id="519a8-180">However, if the command that's being received was started in the current session as a **Job** , it's returned as a **Job** by default.</span></span>

<span data-ttu-id="519a8-181">La commande suivante utilise l' `Receive-PSSession` applet de commande pour se connecter à la session PSSession sur l’ordinateur Server02 et obtenir les résultats de la `Get-WinEvent` commande exécutée dans la session session3.</span><span class="sxs-lookup"><span data-stu-id="519a8-181">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="519a8-182">La commande utilise le paramètre **distarget** pour obtenir les résultats dans un **travail** .</span><span class="sxs-lookup"><span data-stu-id="519a8-182">The command uses the **OutTarget** parameter to get the results in a **Job** .</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="519a8-183">Pour obtenir les résultats du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="519a8-183">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a><span data-ttu-id="519a8-184">Propriétés d’État et de disponibilité</span><span class="sxs-lookup"><span data-stu-id="519a8-184">State and Availability properties</span></span>

<span data-ttu-id="519a8-185">Les propriétés d' **État** et de **disponibilité** d’une session PSSession déconnectée vous indiquent si la session est disponible pour vous y reconnecter.</span><span class="sxs-lookup"><span data-stu-id="519a8-185">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="519a8-186">Quand une session PSSession est connectée à la session active, son état est **ouvert** et sa disponibilité est **disponible** .</span><span class="sxs-lookup"><span data-stu-id="519a8-186">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available** .</span></span> <span data-ttu-id="519a8-187">Lorsque vous vous déconnectez de la session PSSession, l’État PSSession est **déconnecté** et sa disponibilité est **None** .</span><span class="sxs-lookup"><span data-stu-id="519a8-187">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None** .</span></span>

<span data-ttu-id="519a8-188">La valeur de la propriété **State** dépend de la session active.</span><span class="sxs-lookup"><span data-stu-id="519a8-188">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="519a8-189">La valeur **Disconnected** signifie que la session PSSession n’est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="519a8-189">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="519a8-190">Mais cela ne signifie pas que la session PSSession est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="519a8-190">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="519a8-191">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="519a8-191">It might be connected to a different session.</span></span>

<span data-ttu-id="519a8-192">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session PSSession, utilisez la propriété **Availability** .</span><span class="sxs-lookup"><span data-stu-id="519a8-192">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="519a8-193">La valeur **None** indique que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="519a8-193">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="519a8-194">La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session PSSession, car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="519a8-194">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="519a8-195">L’exemple suivant est exécuté dans deux sessions PowerShell sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-195">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="519a8-196">Notez les valeurs modifiées des propriétés d' **État** et de **disponibilité** dans chaque session lorsque la session PSSession est déconnectée et reconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-196">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

<span data-ttu-id="519a8-197">Les sessions déconnectées sont conservées sur l’ordinateur distant jusqu’à ce que vous les supprimiez, par exemple à l’aide de l’applet de commande `Remove-PSSession` ou qu’elles expirent. La propriété **IdleTimeout** d’une session PSSession détermine la durée pendant laquelle une session déconnectée est conservée avant d’être supprimée.</span><span class="sxs-lookup"><span data-stu-id="519a8-197">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="519a8-198">Les sessions PSSession sont inactifs lorsque le **thread de pulsation** ne reçoit pas de réponse.</span><span class="sxs-lookup"><span data-stu-id="519a8-198">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="519a8-199">La déconnexion d’une session rend celle-ci inactive et démarre l’horloge **IdleTimeout** , même si les commandes sont toujours en cours d’exécution dans la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-199">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="519a8-200">PowerShell considère que les sessions déconnectées sont actives, mais inactives.</span><span class="sxs-lookup"><span data-stu-id="519a8-200">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="519a8-201">Lors de la création et de la déconnexion des sessions, vérifiez que le délai d’inactivité dans la session PSSession est suffisamment long pour maintenir la session en fonction de vos besoins, mais pas si longtemps qu’elle consomme des ressources inutiles sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="519a8-201">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="519a8-202">La propriété **IdleTimeoutMs** de la configuration de session détermine le délai d’inactivité par défaut des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-202">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="519a8-203">Vous pouvez remplacer la valeur par défaut, mais la valeur que vous utilisez ne peut pas dépasser la propriété **MaxIdleTimeoutMs** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-203">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="519a8-204">Pour rechercher la valeur des valeurs **IdleTimeoutMs** et **MaxIdleTimeoutMs** d’une configuration de session, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="519a8-204">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="519a8-205">Vous pouvez remplacer la valeur par défaut dans la configuration de session et définir le délai d’inactivité d’une session PSSession lorsque vous créez une session PSSession et lorsque vous vous déconnectez.</span><span class="sxs-lookup"><span data-stu-id="519a8-205">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="519a8-206">Si vous êtes membre du groupe Administrateurs sur l’ordinateur distant, vous pouvez créer et modifier les propriétés **IdleTimeoutMs** et **MaxIdleTimeoutMs** des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-206">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="519a8-207">Valeurs du délai d’inactivité</span><span class="sxs-lookup"><span data-stu-id="519a8-207">Idle timeout values</span></span>

<span data-ttu-id="519a8-208">La valeur du délai d’inactivité des configurations de session et des options de session est exprimée en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="519a8-208">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="519a8-209">La valeur du délai d’inactivité des sessions et des options de configuration de session est en secondes.</span><span class="sxs-lookup"><span data-stu-id="519a8-209">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="519a8-210">Vous pouvez définir le délai d’inactivité d’une session PSSession quand vous créez la session PSSession ( `New-PSSession` , `Invoke-Command` ) et lorsque vous vous déconnectez de celle-ci ( `Disconnect-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="519a8-210">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="519a8-211">Toutefois, vous ne pouvez pas modifier la valeur **IdleTimeout** lorsque vous vous connectez à la session PSSession ( `Connect-PSSession` ) ou obtenir les résultats ( `Receive-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="519a8-211">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="519a8-212">Les `Connect-PSSession` applets de commande et `Receive-PSSession` ont un paramètre **SessionOption** qui prend un objet **SessionOption** , tel que celui retourné par l’applet de commande `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="519a8-212">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="519a8-213">La valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la `$PSSessionOption` variable preference ne modifient pas la valeur de l’option **IdleTimeout** de la session PSSession dans une `Connect-PSSession` commande ou `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-213">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="519a8-214">Pour créer une session PSSession avec une valeur de délai d’inactivité particulière, créez une `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="519a8-214">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="519a8-215">Définissez la valeur de la propriété **IdleTimeout** sur la valeur souhaitée (en millisecondes).</span><span class="sxs-lookup"><span data-stu-id="519a8-215">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="519a8-216">Lorsque vous créez des sessions PSSession, les valeurs de `$PSSessionOption` variables sont prioritaires sur les valeurs de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-216">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="519a8-217">Par exemple, la commande suivante définit un délai d’inactivité de 48 heures :</span><span class="sxs-lookup"><span data-stu-id="519a8-217">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="519a8-218">Pour créer une session PSSession avec une valeur de délai d’inactivité particulière, utilisez le paramètre **IdleTimeoutMSec** de l’applet de commande `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="519a8-218">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="519a8-219">Utilisez ensuite l’option de session dans la valeur du paramètre **SessionOption** des `New-PSSession` applets de commande ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="519a8-219">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="519a8-220">Les valeurs définies lors de la création de la session sont prioritaires par rapport aux valeurs définies dans la `$PSSessionOption` variable de préférence et la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-220">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="519a8-221">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-221">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="519a8-222">Pour modifier le délai d’inactivité d’une session PSSession lors de la déconnexion, utilisez le paramètre **IdleTimeoutSec** de l’applet de commande `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-222">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="519a8-223">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-223">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="519a8-224">Pour créer une configuration de session avec un délai d’inactivité particulier et un délai d’inactivité maximal, utilisez les paramètres **IdleTimeoutSec** et **MaxIdleTimeoutSec** de l’applet de commande `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="519a8-224">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="519a8-225">Ensuite, utilisez l’option de transport dans la valeur du paramètre **TransportOption** de `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="519a8-225">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="519a8-226">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-226">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="519a8-227">Pour modifier le délai d’inactivité par défaut et le délai d’inactivité maximal pour une configuration de session, utilisez les paramètres **IdleTimeoutSec** et **MaxIdleTimeoutSec** de l’applet de commande `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="519a8-227">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="519a8-228">Ensuite, utilisez l’option de transport dans la valeur du paramètre **TransportOption** de `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="519a8-228">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="519a8-229">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-229">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="519a8-230">Mode de mise en mémoire tampon de sortie</span><span class="sxs-lookup"><span data-stu-id="519a8-230">Output buffering mode</span></span>

<span data-ttu-id="519a8-231">Le mode de mise en mémoire tampon de sortie d’une session PSSession détermine comment la sortie de la commande est gérée lorsque la mémoire tampon de sortie de la session PSSession est pleine.</span><span class="sxs-lookup"><span data-stu-id="519a8-231">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="519a8-232">Dans une session déconnectée, le mode de mise en mémoire tampon de sortie détermine en réalité si la commande continue de s’exécuter pendant que la session est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-232">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="519a8-233">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="519a8-233">The valid values as follows:</span></span>

- <span data-ttu-id="519a8-234">**Bloquer** .</span><span class="sxs-lookup"><span data-stu-id="519a8-234">**Block** .</span></span> <span data-ttu-id="519a8-235">Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée.</span><span class="sxs-lookup"><span data-stu-id="519a8-235">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="519a8-236">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="519a8-236">The default value.</span></span>
- <span data-ttu-id="519a8-237">**Supprimer** .</span><span class="sxs-lookup"><span data-stu-id="519a8-237">**Drop** .</span></span> <span data-ttu-id="519a8-238">Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="519a8-238">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="519a8-239">À mesure que de nouvelles sorties sont générées, la sortie la plus ancienne est ignorée.</span><span class="sxs-lookup"><span data-stu-id="519a8-239">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="519a8-240">**Block** conserve les données, mais peut interrompre la commande.</span><span class="sxs-lookup"><span data-stu-id="519a8-240">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="519a8-241">La valeur **Drop** permet l'exécution de la commande, même si des données peuvent être perdues.</span><span class="sxs-lookup"><span data-stu-id="519a8-241">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="519a8-242">Quand vous utilisez la valeur **Drop** , redirigez la sortie de la commande vers un fichier sur disque.</span><span class="sxs-lookup"><span data-stu-id="519a8-242">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="519a8-243">Cette valeur est recommandée pour les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="519a8-243">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="519a8-244">La propriété **OutputBufferingMode** de la configuration de session détermine le mode de mise en mémoire tampon de sortie par défaut des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-244">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="519a8-245">Pour trouver la valeur de la configuration de session **OutputBufferingMode** , vous pouvez utiliser l’un des formats de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="519a8-245">To find a session configuration's value of the **OutputBufferingMode** , you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="519a8-246">Vous pouvez remplacer la valeur par défaut dans la configuration de session et définir le mode de mise en mémoire tampon de sortie d’une session PSSession quand vous créez une session PSSession, lorsque vous vous déconnectez, et lorsque vous vous reconnectez.</span><span class="sxs-lookup"><span data-stu-id="519a8-246">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="519a8-247">Si vous êtes membre du groupe Administrateurs sur l’ordinateur distant, vous pouvez créer et modifier le mode de mise en mémoire tampon de sortie des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-247">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="519a8-248">Pour créer une session PSSession avec le mode de **suppression** de la mise en mémoire tampon de sortie, créez une `$PSSessionOption` variable de préférence dans laquelle la valeur de la propriété **OutputBufferingMode** est **Drop** .</span><span class="sxs-lookup"><span data-stu-id="519a8-248">To create a PSSession with an output buffering mode of **Drop** , create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop** .</span></span>

<span data-ttu-id="519a8-249">Lorsque vous créez des sessions PSSession, les valeurs de `$PSSessionOption` variables sont prioritaires sur les valeurs de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-249">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="519a8-250">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-250">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="519a8-251">Pour créer une session PSSession avec le mode de mise en mémoire tampon de sortie **Drop** , utilisez le paramètre **OutputBufferingMode** de l' `New-PSSessionOption` applet de commande pour créer une option de session avec la valeur **Drop** .</span><span class="sxs-lookup"><span data-stu-id="519a8-251">To create a PSSession with an output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop** .</span></span> <span data-ttu-id="519a8-252">Utilisez ensuite l’option de session dans la valeur du paramètre **SessionOption** des `New-PSSession` applets de commande ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="519a8-252">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="519a8-253">Les valeurs définies lors de la création de la session sont prioritaires par rapport aux valeurs définies dans la `$PSSessionOption` variable de préférence et la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="519a8-253">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="519a8-254">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-254">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="519a8-255">Pour modifier le mode de mise en mémoire tampon de sortie d’une session PSSession lors de la déconnexion, utilisez le paramètre **OutputBufferingMode** de l’applet de commande `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-255">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="519a8-256">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-256">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="519a8-257">Pour modifier le mode de mise en mémoire tampon de sortie d’une session PSSession lors de la reconnexion, utilisez le paramètre **OutputBufferingMode** de l' `New-PSSessionOption` applet de commande pour créer une option de session avec la valeur **Drop** .</span><span class="sxs-lookup"><span data-stu-id="519a8-257">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop** .</span></span> <span data-ttu-id="519a8-258">Ensuite, utilisez l’option de session dans la valeur du paramètre **SessionOption** de `Connect-PSSession` ou `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="519a8-258">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="519a8-259">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-259">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="519a8-260">Pour créer une configuration de session avec le mode de **suppression** de la mise en mémoire tampon de sortie par défaut, utilisez le paramètre **OutputBufferingMode** de l' `New-PSTransportOption` applet de commande pour créer un objet d’option de transport avec la valeur **Drop** .</span><span class="sxs-lookup"><span data-stu-id="519a8-260">To create a session configuration with a default output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop** .</span></span> <span data-ttu-id="519a8-261">Ensuite, utilisez l’option de transport dans la valeur du paramètre **TransportOption** de `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="519a8-261">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="519a8-262">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-262">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="519a8-263">Pour modifier le mode de mise en mémoire tampon de sortie par défaut d’une configuration de session, utilisez le paramètre **OutputBufferingMode** de l' `New-PSTransportOption` applet de commande pour créer une option de transport avec la valeur **Drop** .</span><span class="sxs-lookup"><span data-stu-id="519a8-263">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop** .</span></span> <span data-ttu-id="519a8-264">Ensuite, utilisez l’option de transport dans la valeur du paramètre **SessionOption** de `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="519a8-264">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="519a8-265">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="519a8-265">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="519a8-266">Déconnexion de sessions de bouclage</span><span class="sxs-lookup"><span data-stu-id="519a8-266">Disconnecting loopback sessions</span></span>

<span data-ttu-id="519a8-267">Les sessions de bouclage, ou sessions locales, sont des sessions PSSession qui proviennent et se terminent sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-267">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="519a8-268">Comme les autres sessions PSSession, les sessions de bouclage actives sont conservées sur l’ordinateur à l’extrémité distante de la connexion (ordinateur local), ce qui vous permet de vous déconnecter et de vous reconnecter aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="519a8-268">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="519a8-269">Par défaut, les sessions de bouclage sont créées avec un jeton de sécurité réseau qui n’autorise pas les commandes exécutées dans la session à accéder à d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="519a8-269">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="519a8-270">Vous pouvez vous reconnecter aux sessions de bouclage qui ont un jeton de sécurité réseau à partir de n’importe quelle session sur l’ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="519a8-270">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="519a8-271">Toutefois, si vous utilisez le paramètre **EnableNetworkAccess** de l’applet de commande, `New-PSSession` `Enter-PSSession` ou `Invoke-Command` , la session de bouclage est créée avec un jeton de sécurité interactif.</span><span class="sxs-lookup"><span data-stu-id="519a8-271">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="519a8-272">Le jeton interactif active les commandes qui s’exécutent dans la session de bouclage pour récupérer des données à partir d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="519a8-272">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="519a8-273">Vous pouvez déconnecter des sessions de bouclage avec des jetons interactifs, puis vous y reconnecter à partir de la même session ou d’une autre session sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="519a8-273">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="519a8-274">Toutefois, pour empêcher les accès malveillants, vous pouvez vous reconnecter aux sessions de bouclage avec des jetons interactifs uniquement à partir de l’ordinateur sur lequel ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="519a8-274">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="519a8-275">En attente de travaux dans les sessions déconnectées</span><span class="sxs-lookup"><span data-stu-id="519a8-275">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="519a8-276">L' `Wait-Job` applet de commande attend qu’une tâche se termine, puis retourne à l’invite de commandes ou à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="519a8-276">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="519a8-277">Par défaut, `Wait-Job` retourne si la session dans laquelle un travail est en cours d’exécution est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="519a8-277">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="519a8-278">Pour demander `Wait-Job` à l’applet de commande d’attendre que la session soit reconnectée, à l’état **ouvert** , utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="519a8-278">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="519a8-279">Pour plus d’informations, consultez [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span><span class="sxs-lookup"><span data-stu-id="519a8-279">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="519a8-280">Sessions fiables et déconnexion non intentionnelle</span><span class="sxs-lookup"><span data-stu-id="519a8-280">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="519a8-281">Une session PSSession peut être déconnectée de manière involontaire en raison d’une panne de l’ordinateur ou d’un réseau.</span><span class="sxs-lookup"><span data-stu-id="519a8-281">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="519a8-282">PowerShell tente de récupérer la session PSSession, mais son succès dépend de la gravité et de la durée de la cause.</span><span class="sxs-lookup"><span data-stu-id="519a8-282">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="519a8-283">L’état d’une session PSSession déconnectée de manière involontaire peut être **interrompu** ou **fermé** , mais il peut également être **déconnecté** .</span><span class="sxs-lookup"><span data-stu-id="519a8-283">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed** , but it might also be **Disconnected** .</span></span> <span data-ttu-id="519a8-284">Si la valeur de l' **État** est **Disconnected** , vous pouvez utiliser les mêmes techniques pour gérer la session PSSession que si la session était déconnectée intentionnellement.</span><span class="sxs-lookup"><span data-stu-id="519a8-284">If the value of **State** is **Disconnected** , you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="519a8-285">Par exemple, vous pouvez utiliser la `Connect-PSSession` cmdlet pour vous reconnecter à la session et l' `Receive-PSSession` applet de commande pour obtenir les résultats des commandes exécutées pendant la déconnexion de la session.</span><span class="sxs-lookup"><span data-stu-id="519a8-285">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="519a8-286">Si vous fermez (quittez) la session dans laquelle une session PSSession a été créée alors que les commandes s’exécutent dans la session PSSession, PowerShell maintient la session PSSession à l’état **déconnecté** sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="519a8-286">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="519a8-287">Si vous fermez (quittez) la session dans laquelle une session PSSession a été créée, mais qu’aucune commande n’est en cours d’exécution dans la session PSSession, PowerShell ne tente pas de maintenir la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="519a8-287">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="519a8-288">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="519a8-288">See also</span></span>

[<span data-ttu-id="519a8-289">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="519a8-289">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="519a8-290">about_Remote</span><span class="sxs-lookup"><span data-stu-id="519a8-290">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="519a8-291">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="519a8-291">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="519a8-292">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="519a8-292">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="519a8-293">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="519a8-293">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="519a8-294">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="519a8-294">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="519a8-295">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="519a8-295">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="519a8-296">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="519a8-296">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="519a8-297">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="519a8-297">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="519a8-298">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="519a8-298">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

