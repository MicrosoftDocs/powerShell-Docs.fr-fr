---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 62e5081854fbef46554cafcde0b227ee49fd273e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391440"
---
# <span data-ttu-id="17c7c-103">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-103">Connect-PSSession</span></span>

## <span data-ttu-id="17c7c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="17c7c-104">SYNOPSIS</span></span>
<span data-ttu-id="17c7c-105">Se reconnecte aux sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-105">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="17c7c-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="17c7c-106">SYNTAX</span></span>

### <span data-ttu-id="17c7c-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="17c7c-107">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-108">session</span><span class="sxs-lookup"><span data-stu-id="17c7c-108">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-109">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="17c7c-109">ComputerNameGuid</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-110">ComputerName</span><span class="sxs-lookup"><span data-stu-id="17c7c-110">ComputerName</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-111">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="17c7c-111">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-112">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="17c7c-112">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="17c7c-113">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c7c-114">Id</span><span class="sxs-lookup"><span data-stu-id="17c7c-114">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="17c7c-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="17c7c-115">DESCRIPTION</span></span>

<span data-ttu-id="17c7c-116">L' `Connect-PSSession` applet de commande se reconnecte aux sessions PowerShell gérées par l’utilisateur ( **sessions PSSession** ) qui ont été déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-116">The `Connect-PSSession` cmdlet reconnects to user-managed PowerShell sessions ( **PSSessions** ) that were disconnected.</span></span> <span data-ttu-id="17c7c-117">Elle fonctionne sur les sessions déconnectées intentionnellement, par exemple en utilisant l' `Disconnect-PSSession` applet de commande ou le paramètre **InDisconnectedSession** de l’applet de commande `Invoke-Command` , et celles qui ont été déconnectées de manière involontaire, par exemple suite à une panne réseau temporaire.</span><span class="sxs-lookup"><span data-stu-id="17c7c-117">It works on sessions that are disconnected intentionally, such as by using the `Disconnect-PSSession` cmdlet or the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="17c7c-118">`Connect-PSSession` peut se connecter à n’importe quelle session déconnectée qui a été démarrée par le même utilisateur.</span><span class="sxs-lookup"><span data-stu-id="17c7c-118">`Connect-PSSession` can connect to any disconnected session that was started by the same user.</span></span> <span data-ttu-id="17c7c-119">Celles-ci incluent celles qui ont été démarrées par ou déconnectées d’autres sessions sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-119">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="17c7c-120">Toutefois, `Connect-PSSession` ne peut pas se connecter à des sessions interrompues ou fermées, ou à des sessions interactives démarrées à l’aide de l’applet de commande `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="17c7c-120">However, `Connect-PSSession` cannot connect to broken or closed sessions, or interactive sessions started by using the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="17c7c-121">En outre, vous ne pouvez pas connecter une session à une session démarrée par un autre utilisateur, sauf si vous pouvez fournir les informations d'identification de l'utilisateur qui a créé la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-121">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="17c7c-122">Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="17c7c-122">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="17c7c-123">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="17c7c-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="17c7c-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="17c7c-124">EXAMPLES</span></span>

### <span data-ttu-id="17c7c-125">Exemple 1 : se reconnecter à une session</span><span class="sxs-lookup"><span data-stu-id="17c7c-125">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="17c7c-126">Cette commande se reconnecte à la session ITTask sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="17c7c-126">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="17c7c-127">La sortie montre que la commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="17c7c-127">The output shows that the command was successful.</span></span> <span data-ttu-id="17c7c-128">L' **État** de la session est ouvert et la **disponibilité** est disponible, ce qui indique que vous pouvez exécuter des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-128">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="17c7c-129">Exemple 2 : effet de la déconnexion et de la reconnexion</span><span class="sxs-lookup"><span data-stu-id="17c7c-129">Example 2: Effect of disconnecting and reconnecting</span></span>

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

<span data-ttu-id="17c7c-130">Cet exemple montre l'effet de la déconnexion et de la reconnexion à une session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-130">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="17c7c-131">La première commande utilise l' `Get-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-131">The first command uses the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="17c7c-132">Sans le paramètre **ComputerName** , la commande récupère uniquement les sessions qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="17c7c-132">Without the **ComputerName** parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="17c7c-133">La sortie indique que la commande récupère la session Backups sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="17c7c-133">The output shows that the command gets the Backups session on the local computer.</span></span> <span data-ttu-id="17c7c-134">L' **État** de la session est ouvert et la **disponibilité** est disponible.</span><span class="sxs-lookup"><span data-stu-id="17c7c-134">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="17c7c-135">La deuxième commande utilise l' `Get-PSSession` applet de commande pour récupérer les objets **PSSession** qui ont été créés dans la session active et l' `Disconnect-PSSession` applet de commande pour déconnecter les sessions.</span><span class="sxs-lookup"><span data-stu-id="17c7c-135">The second command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Disconnect-PSSession` cmdlet to disconnect the sessions.</span></span> <span data-ttu-id="17c7c-136">La sortie indique que la session Backups a été déconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-136">The output shows that the Backups session was disconnected.</span></span> <span data-ttu-id="17c7c-137">L' **État** de la session est disconnected et la **disponibilité** est None.</span><span class="sxs-lookup"><span data-stu-id="17c7c-137">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="17c7c-138">La troisième commande utilise l' `Get-PSSession` applet de commande pour récupérer les objets **PSSession** qui ont été créés dans la session active et l' `Connect-PSSession` applet de commande pour reconnecter les sessions.</span><span class="sxs-lookup"><span data-stu-id="17c7c-138">The third command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Connect-PSSession` cmdlet to reconnect the sessions.</span></span> <span data-ttu-id="17c7c-139">La sortie indique que la session Backups a été reconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-139">The output shows that the Backups session was reconnected.</span></span> <span data-ttu-id="17c7c-140">L' **État** de la session est ouvert et la **disponibilité** est disponible.</span><span class="sxs-lookup"><span data-stu-id="17c7c-140">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="17c7c-141">Si vous utilisez l' `Connect-PSSession` applet de commande sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et ne génère pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-141">If you use the `Connect-PSSession` cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="17c7c-142">Exemple 3 : série de commandes dans un scénario d’entreprise</span><span class="sxs-lookup"><span data-stu-id="17c7c-142">Example 3: Series of commands in an enterprise scenario</span></span>

<span data-ttu-id="17c7c-143">Cette série de commandes montre comment l' `Connect-PSSession` applet de commande peut être utilisée dans un scénario d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="17c7c-143">This series of commands shows how the `Connect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="17c7c-144">Dans ce cas, un administrateur système démarre une tâche de longue durée dans une session sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="17c7c-144">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span> <span data-ttu-id="17c7c-145">Après le démarrage de la tâche, l'administrateur se déconnecte de la session et rentre chez lui.</span><span class="sxs-lookup"><span data-stu-id="17c7c-145">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="17c7c-146">Plus tard dans la soirée, l’administrateur se connecte à son ordinateur privé et vérifie que la tâche s’est exécutée jusqu’à ce qu’elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-146">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

<span data-ttu-id="17c7c-147">L’administrateur commence par créer des sessions sur un ordinateur distant et à exécuter un script dans la session. La première commande utilise l' `New-PSSession` applet de commande pour créer la session ITTask sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="17c7c-147">The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 remote computer.</span></span> <span data-ttu-id="17c7c-148">La commande utilise le paramètre **ConfigurationName** pour spécifier la configuration de session ITTasks.</span><span class="sxs-lookup"><span data-stu-id="17c7c-148">The command uses the **ConfigurationName** parameter to specify the ITTasks session configuration.</span></span> <span data-ttu-id="17c7c-149">La commande enregistre les sessions dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="17c7c-149">The command saves the sessions in the `$s` variable.</span></span>

<span data-ttu-id="17c7c-150">Deuxième applet de commande `Invoke-Command` pour démarrer une tâche en arrière-plan dans la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="17c7c-150">The second command `Invoke-Command` cmdlet to start a background job in the session in the `$s` variable.</span></span> <span data-ttu-id="17c7c-151">Elle utilise le paramètre **FilePath** pour exécuter le script dans la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="17c7c-151">It uses the **FilePath** parameter to run the script in the background job.</span></span>

<span data-ttu-id="17c7c-152">La troisième commande utilise l' `Disconnect-PSSession` applet de commande pour se déconnecter de la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="17c7c-152">The third command uses the `Disconnect-PSSession` cmdlet to disconnect from the session in the `$s` variable.</span></span> <span data-ttu-id="17c7c-153">La commande utilise le paramètre **OutputBufferingMode** avec la valeur Drop pour empêcher le blocage du script au cas où il devrait transmettre une sortie à la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-153">The command uses the **OutputBufferingMode** parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session.</span></span> <span data-ttu-id="17c7c-154">Elle utilise le paramètre **IdleTimeoutSec** pour étendre le délai d’expiration de session à 15 heures.</span><span class="sxs-lookup"><span data-stu-id="17c7c-154">It uses the **IdleTimeoutSec** parameter to extend the session time-out to 15 hours.</span></span> <span data-ttu-id="17c7c-155">Lorsque la commande est terminée, l’administrateur verrouille son ordinateur et le soir.</span><span class="sxs-lookup"><span data-stu-id="17c7c-155">When the command is completed, the administrator locks her computer and goes home for the evening.</span></span>

<span data-ttu-id="17c7c-156">Plus tard le soir, l’administrateur démarre son ordinateur privé, se connecte au réseau d’entreprise et démarre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17c7c-156">Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell.</span></span> <span data-ttu-id="17c7c-157">La quatrième commande utilise l' `Get-PSSession` applet de commande pour récupérer les sessions sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="17c7c-157">The fourth command uses the `Get-PSSession` cmdlet to get the sessions on the Server01 computer.</span></span> <span data-ttu-id="17c7c-158">La commande recherche la session ITTask. La cinquième commande utilise l' `Connect-PSSession` applet de commande pour se connecter à la session ITTask.</span><span class="sxs-lookup"><span data-stu-id="17c7c-158">The command finds the ITTask session.The fifth command uses the `Connect-PSSession` cmdlet to connect to the ITTask session.</span></span> <span data-ttu-id="17c7c-159">La commande enregistre la session dans la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="17c7c-159">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="17c7c-160">La sixième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Job` commande dans la session de la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="17c7c-160">The sixth command uses the `Invoke-Command` cmdlet to run a `Get-Job` command in the session in the `$s` variable.</span></span> <span data-ttu-id="17c7c-161">La sortie indique que la tâche s’est terminée avec succès. La septième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande dans la session dans la `$s` variable de la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-161">The output shows that the job finished successfully.The seventh command uses the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session in the `$s` variable in the session.</span></span> <span data-ttu-id="17c7c-162">La commande enregistre les résultats dans la `$BackupSpecs` variable. La huitième commande utilise l' `Invoke-Command` applet de commande pour exécuter un autre script dans la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-162">The command saves the results in the `$BackupSpecs` variable.The eighth command uses the `Invoke-Command` cmdlet to runs another script in the session.</span></span> <span data-ttu-id="17c7c-163">La commande utilise la valeur de la `$BackupSpecs` variable de la session comme entrée pour le script.</span><span class="sxs-lookup"><span data-stu-id="17c7c-163">The command uses the value of the `$BackupSpecs` variable in the session as input to the script.</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="17c7c-164">La neuvième commande se déconnecte de la session dans la `$s` variable. L’administrateur ferme PowerShell et ferme l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17c7c-164">The ninth command disconnects from the session in the `$s` variable.The administrator closes PowerShell and closes the computer.</span></span> <span data-ttu-id="17c7c-165">Il peut se reconnecter à la session le jour suivant et vérifier le statut du script à partir de son ordinateur professionnel.</span><span class="sxs-lookup"><span data-stu-id="17c7c-165">She can reconnect to the session on the next day and check the script status from her work computer.</span></span>

## <span data-ttu-id="17c7c-166">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="17c7c-166">PARAMETERS</span></span>

### <span data-ttu-id="17c7c-167">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="17c7c-167">-AllowRedirection</span></span>

<span data-ttu-id="17c7c-168">Indique que cette applet de commande autorise la redirection de cette connexion vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="17c7c-168">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="17c7c-169">Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="17c7c-169">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="17c7c-170">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="17c7c-170">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="17c7c-171">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**.</span><span class="sxs-lookup"><span data-stu-id="17c7c-171">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="17c7c-172">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="17c7c-172">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="17c7c-173">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="17c7c-173">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-174">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="17c7c-174">-ApplicationName</span></span>

<span data-ttu-id="17c7c-175">Spécifie le nom d'une application.</span><span class="sxs-lookup"><span data-stu-id="17c7c-175">Specifies the name of an application.</span></span> <span data-ttu-id="17c7c-176">Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-176">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="17c7c-177">Entrez le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="17c7c-177">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="17c7c-178">Par exemple, dans l’URI de connexion suivant, le nom de l’application est WSMan : `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="17c7c-178">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="17c7c-179">Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-179">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="17c7c-180">La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="17c7c-180">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="17c7c-181">Elle ne modifie pas l'application utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-181">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-182">-Authentification</span><span class="sxs-lookup"><span data-stu-id="17c7c-182">-Authentication</span></span>

<span data-ttu-id="17c7c-183">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur dans la commande pour se reconnecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-183">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="17c7c-184">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="17c7c-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="17c7c-185">Default</span><span class="sxs-lookup"><span data-stu-id="17c7c-185">Default</span></span>
- <span data-ttu-id="17c7c-186">De base</span><span class="sxs-lookup"><span data-stu-id="17c7c-186">Basic</span></span>
- <span data-ttu-id="17c7c-187">CredSSP</span><span class="sxs-lookup"><span data-stu-id="17c7c-187">Credssp</span></span>
- <span data-ttu-id="17c7c-188">Digest</span><span class="sxs-lookup"><span data-stu-id="17c7c-188">Digest</span></span>
- <span data-ttu-id="17c7c-189">Kerberos</span><span class="sxs-lookup"><span data-stu-id="17c7c-189">Kerberos</span></span>
- <span data-ttu-id="17c7c-190">Negotiate</span><span class="sxs-lookup"><span data-stu-id="17c7c-190">Negotiate</span></span>
- <span data-ttu-id="17c7c-191">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="17c7c-191">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="17c7c-192">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="17c7c-192">The default value is Default.</span></span>

<span data-ttu-id="17c7c-193">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="17c7c-193">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="17c7c-194">l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="17c7c-194">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="17c7c-195">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="17c7c-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="17c7c-196">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="17c7c-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-197">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="17c7c-197">-CertificateThumbprint</span></span>

<span data-ttu-id="17c7c-198">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-198">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="17c7c-199">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="17c7c-199">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="17c7c-200">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="17c7c-200">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="17c7c-201">Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="17c7c-201">They can be mapped only to local user accounts.</span></span> <span data-ttu-id="17c7c-202">Ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="17c7c-202">They do not work with domain accounts.</span></span>

<span data-ttu-id="17c7c-203">Pour obtenir une empreinte numérique de certificat, utilisez une `Get-Item` `Get-ChildItem` commande ou dans le lecteur de certificat PowerShell :.</span><span class="sxs-lookup"><span data-stu-id="17c7c-203">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-204">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="17c7c-204">-ComputerName</span></span>

<span data-ttu-id="17c7c-205">Spécifie les ordinateurs sur lesquels sont stockées les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-205">Specifies the computers on which the disconnected sessions are stored.</span></span> <span data-ttu-id="17c7c-206">Les sessions sont stockées sur l’ordinateur qui se trouve côté serveur ou reçoit la fin d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="17c7c-206">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="17c7c-207">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="17c7c-207">The default is the local computer.</span></span>

<span data-ttu-id="17c7c-208">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17c7c-208">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span> <span data-ttu-id="17c7c-209">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="17c7c-209">Wildcard characters are not permitted.</span></span> <span data-ttu-id="17c7c-210">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.)</span><span class="sxs-lookup"><span data-stu-id="17c7c-210">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-211">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="17c7c-211">-ConfigurationName</span></span>

<span data-ttu-id="17c7c-212">Se connecte uniquement à des sessions qui utilisent la configuration de session spécifiée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-212">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="17c7c-213">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-213">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="17c7c-214">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="17c7c-214">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="17c7c-215">Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-215">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="17c7c-216">La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="17c7c-216">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="17c7c-217">Elle ne modifie pas la configuration de session utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-217">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="17c7c-218">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="17c7c-218">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-219">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="17c7c-219">-ConnectionUri</span></span>

<span data-ttu-id="17c7c-220">Spécifie les URI des points de terminaison de connexion pour les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-220">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="17c7c-221">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="17c7c-221">The URI must be fully qualified.</span></span> <span data-ttu-id="17c7c-222">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="17c7c-222">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="17c7c-223">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="17c7c-223">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="17c7c-224">Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres **UseSSL** et **port** pour spécifier les valeurs d’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="17c7c-224">If you do not specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="17c7c-225">Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="17c7c-225">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="17c7c-226">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-226">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="17c7c-227">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-227">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="17c7c-228">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-228">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-229">-Credential</span><span class="sxs-lookup"><span data-stu-id="17c7c-229">-Credential</span></span>

<span data-ttu-id="17c7c-230">Spécifie un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-230">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="17c7c-231">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="17c7c-231">The default is the current user.</span></span>

<span data-ttu-id="17c7c-232">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un `PSCredential` objet généré par l’applet `Get-Credential` de commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-232">Type a user name, such as `User01` or `Domain01\User01`, or enter a `PSCredential` object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="17c7c-233">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="17c7c-233">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="17c7c-234">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="17c7c-234">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="17c7c-235">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="17c7c-235">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-236">-Id</span><span class="sxs-lookup"><span data-stu-id="17c7c-236">-Id</span></span>

<span data-ttu-id="17c7c-237">Spécifie les ID des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-237">Specifies the IDs of the disconnected sessions.</span></span> <span data-ttu-id="17c7c-238">Le paramètre **ID** fonctionne uniquement lorsque la session déconnectée a déjà été connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="17c7c-238">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="17c7c-239">Ce paramètre est valide, mais il est sans effet si la session est stockée sur l'ordinateur local sans avoir été connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="17c7c-239">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-240">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="17c7c-240">-InstanceId</span></span>

<span data-ttu-id="17c7c-241">Spécifie les ID d'instance des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-241">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="17c7c-242">L’ID d’instance est un GUID qui identifie de façon unique une **session PSSession** sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="17c7c-242">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="17c7c-243">L’ID d’instance est stocké dans la propriété **InstanceID** de la **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="17c7c-243">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-244">-Name</span><span class="sxs-lookup"><span data-stu-id="17c7c-244">-Name</span></span>

<span data-ttu-id="17c7c-245">Spécifie les noms conviviaux des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-245">Specifies the friendly names of the disconnected sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-246">-Port</span><span class="sxs-lookup"><span data-stu-id="17c7c-246">-Port</span></span>

<span data-ttu-id="17c7c-247">Spécifie le port réseau sur l'ordinateur distant qui est utilisé pour se reconnecter à la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-247">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span> <span data-ttu-id="17c7c-248">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="17c7c-248">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="17c7c-249">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-249">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="17c7c-250">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="17c7c-250">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="17c7c-251">Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="17c7c-251">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="17c7c-252">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="17c7c-252">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="17c7c-253">Le port défini dans la commande s'applique à tous les ordinateurs ou toutes les sessions sur lesquelles la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="17c7c-253">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="17c7c-254">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-254">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-255">-Session</span><span class="sxs-lookup"><span data-stu-id="17c7c-255">-Session</span></span>

<span data-ttu-id="17c7c-256">Spécifie les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-256">Specifies the disconnected sessions.</span></span> <span data-ttu-id="17c7c-257">Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-257">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-258">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="17c7c-258">-SessionOption</span></span>

<span data-ttu-id="17c7c-259">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-259">Specifies advanced options for the session.</span></span> <span data-ttu-id="17c7c-260">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-260">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="17c7c-261">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="17c7c-261">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="17c7c-262">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-262">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="17c7c-263">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-263">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="17c7c-264">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-264">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="17c7c-265">Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="17c7c-265">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="17c7c-266">Pour plus d’informations sur la variable de préférence **$PSSessionOption** , consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="17c7c-266">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="17c7c-267">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="17c7c-267">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-268">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="17c7c-268">-ThrottleLimit</span></span>

<span data-ttu-id="17c7c-269">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-269">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="17c7c-270">Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-270">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="17c7c-271">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17c7c-271">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-272">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="17c7c-272">-UseSSL</span></span>

<span data-ttu-id="17c7c-273">Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-273">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="17c7c-274">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="17c7c-274">By default, SSL is not used.</span></span>

<span data-ttu-id="17c7c-275">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="17c7c-275">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="17c7c-276">Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="17c7c-276">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="17c7c-277">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="17c7c-277">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-278">-Confirm</span><span class="sxs-lookup"><span data-stu-id="17c7c-278">-Confirm</span></span>

<span data-ttu-id="17c7c-279">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-279">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-280">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="17c7c-280">-WhatIf</span></span>

<span data-ttu-id="17c7c-281">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-281">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="17c7c-282">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-282">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17c7c-283">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17c7c-283">CommonParameters</span></span>

<span data-ttu-id="17c7c-284">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17c7c-284">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17c7c-285">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="17c7c-285">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17c7c-286">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="17c7c-286">INPUTS</span></span>

### <span data-ttu-id="17c7c-287">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-287">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="17c7c-288">Vous pouvez diriger une session ( **PSSession** ) vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="17c7c-288">You can pipe a session ( **PSSession** ) to this cmdlet.</span></span>

## <span data-ttu-id="17c7c-289">SORTIES</span><span class="sxs-lookup"><span data-stu-id="17c7c-289">OUTPUTS</span></span>

### <span data-ttu-id="17c7c-290">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-290">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="17c7c-291">Cette applet de commande retourne un objet qui représente la session à laquelle elle s’est reconnectée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-291">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="17c7c-292">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="17c7c-292">NOTES</span></span>

- <span data-ttu-id="17c7c-293">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="17c7c-293">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="17c7c-294">`Connect-PSSession` se reconnecte uniquement aux sessions déconnectées, c’est-à-dire aux sessions dont la valeur de la propriété **State** est disconnected.</span><span class="sxs-lookup"><span data-stu-id="17c7c-294">`Connect-PSSession` reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="17c7c-295">Seules les sessions connectées à, ou qui se terminent à, les ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures peuvent être déconnectées et reconnectées.</span><span class="sxs-lookup"><span data-stu-id="17c7c-295">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

- <span data-ttu-id="17c7c-296">Si vous utilisez `Connect-PSSession` sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et elle ne génère pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="17c7c-296">If you use `Connect-PSSession` on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>

- <span data-ttu-id="17c7c-297">Les sessions de bouclage déconnectées avec des jetons interactifs, qui sont créés à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="17c7c-297">Disconnected loopback sessions with interactive tokens, which are created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="17c7c-298">Cette restriction protège l'ordinateur contre tout accès malveillant.</span><span class="sxs-lookup"><span data-stu-id="17c7c-298">This restriction protects the computer from malicious access.</span></span>

- <span data-ttu-id="17c7c-299">La valeur de la propriété **State** d’une session **PSSession** est relative à la session active.</span><span class="sxs-lookup"><span data-stu-id="17c7c-299">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="17c7c-300">Par conséquent, la valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="17c7c-300">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="17c7c-301">Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="17c7c-301">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="17c7c-302">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-302">It might be connected to a different session.</span></span> <span data-ttu-id="17c7c-303">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.</span><span class="sxs-lookup"><span data-stu-id="17c7c-303">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="17c7c-304">Une propriété **Availability** avec la valeur None signifie que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-304">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="17c7c-305">La valeur Busy indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="17c7c-305">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="17c7c-306">Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [énumération RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="17c7c-306">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="17c7c-307">Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [énumération RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="17c7c-307">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

- <span data-ttu-id="17c7c-308">Vous ne pouvez pas modifier la valeur du délai d’inactivité d’une **session PSSession** quand vous vous connectez à la **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="17c7c-308">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="17c7c-309">Le paramètre **SessionOption** de `Connect-PSSession` prend un objet **SessionOption** qui a une valeur **IdleTimeout** .</span><span class="sxs-lookup"><span data-stu-id="17c7c-309">The **SessionOption** parameter of `Connect-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="17c7c-310">Toutefois, la valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la `$PSSessionOption` variable sont ignorées lors de la connexion à une **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="17c7c-310">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="17c7c-311">Vous pouvez définir et modifier le délai d’inactivité d’une **session PSSession** quand vous créez la **session PSSession** , à l’aide des `New-PSSession` applets de commande ou `Invoke-Command` , et lorsque vous vous déconnectez de la **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="17c7c-311">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="17c7c-312">La propriété **IdleTimeout** d’une session **PSSession** est critique pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="17c7c-312">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="17c7c-313">Une session déconnectée est considérée comme inactive dès qu'elle est déconnectée, même si elle comprend des commandes en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="17c7c-313">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="17c7c-314">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="17c7c-314">RELATED LINKS</span></span>

[<span data-ttu-id="17c7c-315">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-315">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="17c7c-316">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-316">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="17c7c-317">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-317">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="17c7c-318">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-318">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="17c7c-319">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="17c7c-319">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="17c7c-320">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-320">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="17c7c-321">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="17c7c-321">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="17c7c-322">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="17c7c-322">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="17c7c-323">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-323">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="17c7c-324">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="17c7c-324">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="17c7c-325">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="17c7c-325">Remove-PSSession</span></span>](Remove-PSSession.md)
