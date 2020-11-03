---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 61f1d13628763710f01cf0c2ec413f446e4bdd39
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205545"
---
# <span data-ttu-id="2f29a-103">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-103">Connect-PSSession</span></span>

## <span data-ttu-id="2f29a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2f29a-104">SYNOPSIS</span></span>
<span data-ttu-id="2f29a-105">Se reconnecte aux sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-105">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="2f29a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f29a-106">SYNTAX</span></span>

### <span data-ttu-id="2f29a-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2f29a-107">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-108">session</span><span class="sxs-lookup"><span data-stu-id="2f29a-108">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-109">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="2f29a-109">ComputerNameGuid</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-110">ComputerName</span><span class="sxs-lookup"><span data-stu-id="2f29a-110">ComputerName</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-111">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="2f29a-111">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-112">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2f29a-112">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2f29a-113">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f29a-114">Id</span><span class="sxs-lookup"><span data-stu-id="2f29a-114">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2f29a-115">Description</span><span class="sxs-lookup"><span data-stu-id="2f29a-115">DESCRIPTION</span></span>

<span data-ttu-id="2f29a-116">L’applet de commande **Connect-PSSession** se reconnecte aux sessions PowerShell gérées par l’utilisateur ( **sessions PSSession** ) qui ont été déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-116">The **Connect-PSSession** cmdlet reconnects to user-managed PowerShell sessions ( **PSSessions** ) that were disconnected.</span></span>
<span data-ttu-id="2f29a-117">Elle fonctionne sur les sessions déconnectées intentionnellement, par exemple en utilisant l’applet de commande Disconnect-PSSession ou le paramètre *InDisconnectedSession* de l’applet de commande Invoke-Command, et celles qui ont été déconnectées de manière involontaire, par exemple en cas de panne réseau temporaire.</span><span class="sxs-lookup"><span data-stu-id="2f29a-117">It works on sessions that are disconnected intentionally, such as by using the Disconnect-PSSession cmdlet or the *InDisconnectedSession* parameter of the Invoke-Command cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="2f29a-118">**Connect-PSSession** peut se connecter à n’importe quelle session déconnectée qui a été démarrée par le même utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f29a-118">**Connect-PSSession** can connect to any disconnected session that was started by the same user.</span></span>
<span data-ttu-id="2f29a-119">Celles-ci incluent celles qui ont été démarrées par ou déconnectées d’autres sessions sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2f29a-119">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="2f29a-120">Toutefois, **Connect-PSSession** ne peut pas se connecter aux sessions interrompues ou fermées, ou les sessions interactives démarrées à l’aide de l’applet de commande Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="2f29a-120">However, **Connect-PSSession** cannot connect to broken or closed sessions, or interactive sessions started by using the Enter-PSSession cmdlet.</span></span>
<span data-ttu-id="2f29a-121">En outre, vous ne pouvez pas connecter une session à une session démarrée par un autre utilisateur, sauf si vous pouvez fournir les informations d'identification de l'utilisateur qui a créé la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-121">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="2f29a-122">Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez about_Remote_Disconnected_Sessions.</span><span class="sxs-lookup"><span data-stu-id="2f29a-122">For more information about the Disconnected Sessions feature, see about_Remote_Disconnected_Sessions.</span></span>

<span data-ttu-id="2f29a-123">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="2f29a-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="2f29a-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2f29a-124">EXAMPLES</span></span>

### <span data-ttu-id="2f29a-125">Exemple 1 : se reconnecter à une session</span><span class="sxs-lookup"><span data-stu-id="2f29a-125">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="2f29a-126">Cette commande se reconnecte à la session ITTask sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="2f29a-126">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="2f29a-127">La sortie montre que la commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="2f29a-127">The output shows that the command was successful.</span></span>
<span data-ttu-id="2f29a-128">L' **État** de la session est ouvert et la **disponibilité** est disponible, ce qui indique que vous pouvez exécuter des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-128">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="2f29a-129">Exemple 2 : effet de la déconnexion et de la reconnexion</span><span class="sxs-lookup"><span data-stu-id="2f29a-129">Example 2: Effect of disconnecting and reconnecting</span></span>

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

<span data-ttu-id="2f29a-130">Cet exemple montre l'effet de la déconnexion et de la reconnexion à une session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-130">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="2f29a-131">La première commande utilise l’applet de commande Get-PSSession.</span><span class="sxs-lookup"><span data-stu-id="2f29a-131">The first command uses the Get-PSSession cmdlet.</span></span>
<span data-ttu-id="2f29a-132">Sans le paramètre *ComputerName* , la commande récupère uniquement les sessions qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="2f29a-132">Without the *ComputerName* parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="2f29a-133">La sortie indique que la commande récupère la session Backups sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2f29a-133">The output shows that the command gets the Backups session on the local computer.</span></span>
<span data-ttu-id="2f29a-134">L' **État** de la session est ouvert et la **disponibilité** est disponible.</span><span class="sxs-lookup"><span data-stu-id="2f29a-134">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="2f29a-135">La deuxième commande utilise l’applet de commande **obten-PSSession** pour récupérer les objets **PSSession** qui ont été créés dans la session active et l’applet de commande **Disconnect-PSSession** pour déconnecter les sessions.</span><span class="sxs-lookup"><span data-stu-id="2f29a-135">The second command uses the **Get-PSSession** cmdlet to get the **PSSession** objects that were created in the current session and the **Disconnect-PSSession** cmdlet to disconnect the sessions.</span></span>
<span data-ttu-id="2f29a-136">La sortie indique que la session Backups a été déconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-136">The output shows that the Backups session was disconnected.</span></span>
<span data-ttu-id="2f29a-137">L' **État** de la session est disconnected et la **disponibilité** est None.</span><span class="sxs-lookup"><span data-stu-id="2f29a-137">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="2f29a-138">La troisième commande utilise l’applet de commande **obten-PSSession** pour récupérer les objets **PSSession** qui ont été créés dans la session active et l’applet de commande **Connect-PSSession** pour reconnecter les sessions.</span><span class="sxs-lookup"><span data-stu-id="2f29a-138">The third command uses the **Get-PSSession** cmdlet to get the **PSSession** objects that were created in the current session and the **Connect-PSSession** cmdlet to reconnect the sessions.</span></span>
<span data-ttu-id="2f29a-139">La sortie indique que la session Backups a été reconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-139">The output shows that the Backups session was reconnected.</span></span>
<span data-ttu-id="2f29a-140">L' **État** de la session est ouvert et la **disponibilité** est disponible.</span><span class="sxs-lookup"><span data-stu-id="2f29a-140">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="2f29a-141">Si vous utilisez l’applet de commande **Connect-PSSession** sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et ne génère pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2f29a-141">If you use the **Connect-PSSession** cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="2f29a-142">Exemple 3 : série de commandes dans un scénario d’entreprise</span><span class="sxs-lookup"><span data-stu-id="2f29a-142">Example 3: Series of commands in an enterprise scenario</span></span>

```
The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the **New-PSSession** cmdlet to create the ITTask session on the Server01 remote computer. The command uses the *ConfigurationName* parameter to specify the ITTasks session configuration. The command saves the sessions in the $s variable.
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks

 The second command **Invoke-Command** cmdlet to start a background job in the session in the $s variable. It uses the *FilePath* parameter to run the script in the background job.
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

The third command uses the Disconnect-PSSession cmdlet to disconnect from the session in the $s variable. The command uses the *OutputBufferingMode* parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session. It uses the *IdleTimeoutSec* parameter to extend the session time-out to 15 hours.When the command is completed, the administrator locks her computer and goes home for the evening.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell. The fourth command uses the Get-PSSession cmdlet to get the sessions on the Server01 computer. The command finds the ITTask session.The fifth command uses the **Connect-PSSession** cmdlet to connect to the ITTask session. The command saves the session in the $s variable.
PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

The sixth command uses the **Invoke-Command** cmdlet to run a Get-Job command in the session in the $s variable. The output shows that the job finished successfully.The seventh command uses the **Invoke-Command** cmdlet to run a Receive-Job command in the session in the $s variable in the session. The command saves the results in the $BackupSpecs variable.The eighth command uses the **Invoke-Command** cmdlet to runs another script in the session. The command uses the value of the $BackupSpecs variable in the session as input to the script.


PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

The ninth command disconnects from the session in the $s variable.The administrator closes PowerShell and closes the computer. She can reconnect to the session on the next day and check the script status from her work computer.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="2f29a-143">Cette série de commandes montre comment l'applet de commande **Connect-PSSession** peut être utilisée dans un scénario d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="2f29a-143">This series of commands shows how the **Connect-PSSession** cmdlet might be used in an enterprise scenario.</span></span>
<span data-ttu-id="2f29a-144">Dans ce cas, un administrateur système démarre une tâche de longue durée dans une session sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2f29a-144">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span>
<span data-ttu-id="2f29a-145">Après le démarrage de la tâche, l'administrateur se déconnecte de la session et rentre chez lui.</span><span class="sxs-lookup"><span data-stu-id="2f29a-145">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="2f29a-146">Plus tard dans la soirée, l’administrateur se connecte à son ordinateur privé et vérifie que la tâche s’est exécutée jusqu’à ce qu’elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-146">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

## <span data-ttu-id="2f29a-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f29a-147">PARAMETERS</span></span>

### <span data-ttu-id="2f29a-148">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="2f29a-148">-AllowRedirection</span></span>

<span data-ttu-id="2f29a-149">Indique que cette applet de commande autorise la redirection de cette connexion vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="2f29a-149">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="2f29a-150">Quand vous utilisez le paramètre *ConnectionURI* , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="2f29a-150">When you use the *ConnectionURI* parameter, the remote destination can return an instruction to redirect to a different URI.</span></span>
<span data-ttu-id="2f29a-151">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="2f29a-151">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="2f29a-152">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-152">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span>
<span data-ttu-id="2f29a-153">Utilisez le paramètre *MaximumRedirection* de l’applet de commande New-PSSessionOption ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-153">Use the *MaximumRedirection* parameter of the New-PSSessionOption cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span>
<span data-ttu-id="2f29a-154">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="2f29a-154">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-155">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="2f29a-155">-ApplicationName</span></span>

<span data-ttu-id="2f29a-156">Spécifie le nom d'une application.</span><span class="sxs-lookup"><span data-stu-id="2f29a-156">Specifies the name of an application.</span></span>
<span data-ttu-id="2f29a-157">Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-157">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="2f29a-158">Entrez le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="2f29a-158">Enter the application name segment of the connection URI.</span></span>
<span data-ttu-id="2f29a-159">Par exemple, dans l’URI de connexion suivant, le nom de l’application est WSMan : `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="2f29a-159">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span>
<span data-ttu-id="2f29a-160">Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-160">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="2f29a-161">La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="2f29a-161">The value of this parameter is used to select and filter sessions.</span></span>
<span data-ttu-id="2f29a-162">Elle ne modifie pas l'application utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-162">It does not change the application that the session uses.</span></span>

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

### <span data-ttu-id="2f29a-163">-Authentification</span><span class="sxs-lookup"><span data-stu-id="2f29a-163">-Authentication</span></span>

<span data-ttu-id="2f29a-164">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur dans la commande pour se reconnecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-164">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="2f29a-165">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="2f29a-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2f29a-166">Default</span><span class="sxs-lookup"><span data-stu-id="2f29a-166">Default</span></span>
- <span data-ttu-id="2f29a-167">Basic</span><span class="sxs-lookup"><span data-stu-id="2f29a-167">Basic</span></span>
- <span data-ttu-id="2f29a-168">CredSSP</span><span class="sxs-lookup"><span data-stu-id="2f29a-168">Credssp</span></span>
- <span data-ttu-id="2f29a-169">Digest</span><span class="sxs-lookup"><span data-stu-id="2f29a-169">Digest</span></span>
- <span data-ttu-id="2f29a-170">Kerberos</span><span class="sxs-lookup"><span data-stu-id="2f29a-170">Kerberos</span></span>
- <span data-ttu-id="2f29a-171">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2f29a-171">Negotiate</span></span>
- <span data-ttu-id="2f29a-172">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="2f29a-172">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="2f29a-173">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="2f29a-173">The default value is Default.</span></span>

<span data-ttu-id="2f29a-174">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="2f29a-174">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

<span data-ttu-id="2f29a-175">ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="2f29a-175">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="2f29a-176">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="2f29a-176">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="2f29a-177">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="2f29a-177">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-178">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="2f29a-178">-CertificateThumbprint</span></span>

<span data-ttu-id="2f29a-179">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-179">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="2f29a-180">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="2f29a-180">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="2f29a-181">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="2f29a-181">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="2f29a-182">Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="2f29a-182">They can be mapped only to local user accounts.</span></span>
<span data-ttu-id="2f29a-183">Ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="2f29a-183">They do not work with domain accounts.</span></span>

<span data-ttu-id="2f29a-184">Pour obtenir une empreinte numérique de certificat, utilisez une commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f29a-184">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-185">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2f29a-185">-ComputerName</span></span>

<span data-ttu-id="2f29a-186">Spécifie les ordinateurs sur lesquels sont stockées les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-186">Specifies the computers on which the disconnected sessions are stored.</span></span>
<span data-ttu-id="2f29a-187">Les sessions sont stockées sur l’ordinateur qui se trouve côté serveur ou reçoit la fin d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="2f29a-187">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span>
<span data-ttu-id="2f29a-188">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2f29a-188">The default is the local computer.</span></span>

<span data-ttu-id="2f29a-189">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f29a-189">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span>
<span data-ttu-id="2f29a-190">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="2f29a-190">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="2f29a-191">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.)</span><span class="sxs-lookup"><span data-stu-id="2f29a-191">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

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

### <span data-ttu-id="2f29a-192">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="2f29a-192">-ConfigurationName</span></span>

<span data-ttu-id="2f29a-193">Se connecte uniquement à des sessions qui utilisent la configuration de session spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-193">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="2f29a-194">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-194">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span>
<span data-ttu-id="2f29a-195">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="2f29a-195">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>
<span data-ttu-id="2f29a-196">Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-196">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="2f29a-197">La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="2f29a-197">The value of this parameter is used to select and filter sessions.</span></span>
<span data-ttu-id="2f29a-198">Elle ne modifie pas la configuration de session utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-198">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="2f29a-199">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="2f29a-199">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-200">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2f29a-200">-ConnectionUri</span></span>

<span data-ttu-id="2f29a-201">Spécifie les URI des points de terminaison de connexion pour les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-201">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="2f29a-202">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="2f29a-202">The URI must be fully qualified.</span></span>
<span data-ttu-id="2f29a-203">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="2f29a-203">The format of this string is as follows:</span></span>

`\<Transport\>://\<ComputerName\>:\<Port\>/\<ApplicationName\>`

<span data-ttu-id="2f29a-204">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2f29a-204">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="2f29a-205">Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres *UseSSL* et *port* pour spécifier les valeurs d’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="2f29a-205">If you do not specify a connection URI, you can use the *UseSSL* and *Port* parameters to specify the connection URI values.</span></span>

<span data-ttu-id="2f29a-206">Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2f29a-206">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span>
<span data-ttu-id="2f29a-207">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="2f29a-207">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span>
<span data-ttu-id="2f29a-208">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="2f29a-208">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="2f29a-209">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre *AllowRedirection* dans la commande.</span><span class="sxs-lookup"><span data-stu-id="2f29a-209">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the *AllowRedirection* parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-210">-Credential</span><span class="sxs-lookup"><span data-stu-id="2f29a-210">-Credential</span></span>

<span data-ttu-id="2f29a-211">Spécifie un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-211">Specifies a user account that has permission to connect to the disconnected session.</span></span>
<span data-ttu-id="2f29a-212">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2f29a-212">The default is the current user.</span></span>

<span data-ttu-id="2f29a-213">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="2f29a-213">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2f29a-214">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2f29a-214">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2f29a-215">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="2f29a-215">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2f29a-216">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="2f29a-216">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-217">-Id</span><span class="sxs-lookup"><span data-stu-id="2f29a-217">-Id</span></span>

<span data-ttu-id="2f29a-218">Spécifie les ID des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-218">Specifies the IDs of the disconnected sessions.</span></span>
<span data-ttu-id="2f29a-219">Le paramètre *ID* fonctionne uniquement lorsque la session déconnectée a déjà été connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="2f29a-219">The *Id* parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="2f29a-220">Ce paramètre est valide, mais il est sans effet si la session est stockée sur l'ordinateur local sans avoir été connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="2f29a-220">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

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

### <span data-ttu-id="2f29a-221">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="2f29a-221">-InstanceId</span></span>

<span data-ttu-id="2f29a-222">Spécifie les ID d'instance des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-222">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="2f29a-223">L’ID d’instance est un GUID qui identifie de façon unique une **session PSSession** sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="2f29a-223">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="2f29a-224">L’ID d’instance est stocké dans la propriété **InstanceID** de la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-224">The instance ID is stored in the **InstanceID** property of the **PSSession** .</span></span>

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

### <span data-ttu-id="2f29a-225">-Name</span><span class="sxs-lookup"><span data-stu-id="2f29a-225">-Name</span></span>

<span data-ttu-id="2f29a-226">Spécifie les noms conviviaux des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-226">Specifies the friendly names of the disconnected sessions.</span></span>

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

### <span data-ttu-id="2f29a-227">-Port</span><span class="sxs-lookup"><span data-stu-id="2f29a-227">-Port</span></span>

<span data-ttu-id="2f29a-228">Spécifie le port réseau sur l'ordinateur distant qui est utilisé pour se reconnecter à la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-228">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span>
<span data-ttu-id="2f29a-229">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="2f29a-229">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span>
<span data-ttu-id="2f29a-230">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="2f29a-230">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="2f29a-231">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="2f29a-231">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>
<span data-ttu-id="2f29a-232">Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="2f29a-232">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="2f29a-233">N'utilisez pas le paramètre *Port* à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="2f29a-233">Do not use the *Port* parameter unless you must.</span></span>
<span data-ttu-id="2f29a-234">Le port défini dans la commande s'applique à tous les ordinateurs ou toutes les sessions sur lesquelles la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="2f29a-234">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span>
<span data-ttu-id="2f29a-235">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2f29a-235">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="2f29a-236">-Session</span><span class="sxs-lookup"><span data-stu-id="2f29a-236">-Session</span></span>

<span data-ttu-id="2f29a-237">Spécifie les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-237">Specifies the disconnected sessions.</span></span>
<span data-ttu-id="2f29a-238">Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une commande Get-PSSession.</span><span class="sxs-lookup"><span data-stu-id="2f29a-238">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a Get-PSSession command.</span></span>

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

### <span data-ttu-id="2f29a-239">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="2f29a-239">-SessionOption</span></span>

<span data-ttu-id="2f29a-240">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-240">Specifies advanced options for the session.</span></span>
<span data-ttu-id="2f29a-241">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l’applet de commande New-PSSessionOption, ou une table de hachage dans laquelle les clés sont des noms d’options de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-241">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="2f29a-242">Les valeurs par défaut des options sont déterminées par la valeur de la variable de préférence PSSessionOption, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="2f29a-242">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span>
<span data-ttu-id="2f29a-243">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-243">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="2f29a-244">Les valeurs des options de la session sont prioritaires sur les valeurs par défaut des sessions définies dans la variable de préférence $PSSessionOption et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-244">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span>
<span data-ttu-id="2f29a-245">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-245">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="2f29a-246">Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez New-PSSessionOption.</span><span class="sxs-lookup"><span data-stu-id="2f29a-246">For a description of the session options that includes the default values, see New-PSSessionOption.</span></span>
<span data-ttu-id="2f29a-247">Pour plus d’informations sur la variable de préférence **$PSSessionOption** , consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2f29a-247">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="2f29a-248">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="2f29a-248">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f29a-249">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2f29a-249">-ThrottleLimit</span></span>

<span data-ttu-id="2f29a-250">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="2f29a-250">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="2f29a-251">Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-251">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="2f29a-252">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f29a-252">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2f29a-253">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="2f29a-253">-UseSSL</span></span>

<span data-ttu-id="2f29a-254">Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-254">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="2f29a-255">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2f29a-255">By default, SSL is not used.</span></span>

<span data-ttu-id="2f29a-256">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="2f29a-256">WS-Management encrypts all PowerShell content transmitted over the network.</span></span>
<span data-ttu-id="2f29a-257">Le paramètre *UseSSL* est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="2f29a-257">The *UseSSL* parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="2f29a-258">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2f29a-258">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="2f29a-259">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f29a-259">-Confirm</span></span>

<span data-ttu-id="2f29a-260">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f29a-260">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2f29a-261">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f29a-261">-WhatIf</span></span>

<span data-ttu-id="2f29a-262">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f29a-262">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2f29a-263">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-263">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2f29a-264">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f29a-264">CommonParameters</span></span>

<span data-ttu-id="2f29a-265">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f29a-265">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f29a-266">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2f29a-266">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f29a-267">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2f29a-267">INPUTS</span></span>

### <span data-ttu-id="2f29a-268">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-268">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="2f29a-269">Vous pouvez diriger une session ( **PSSession** ) vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f29a-269">You can pipe a session ( **PSSession** ) to this cmdlet.</span></span>

## <span data-ttu-id="2f29a-270">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2f29a-270">OUTPUTS</span></span>

### <span data-ttu-id="2f29a-271">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-271">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="2f29a-272">Cette applet de commande retourne un objet qui représente la session à laquelle elle s’est reconnectée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-272">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="2f29a-273">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2f29a-273">NOTES</span></span>

* <span data-ttu-id="2f29a-274">**Connect-PSSession** se reconnecte uniquement aux sessions déconnectées, c’est-à-dire aux sessions dont la valeur de la propriété **State** est disconnected.</span><span class="sxs-lookup"><span data-stu-id="2f29a-274">**Connect-PSSession** reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="2f29a-275">Seules les sessions connectées à, ou qui se terminent à, les ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures peuvent être déconnectées et reconnectées.</span><span class="sxs-lookup"><span data-stu-id="2f29a-275">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>
* <span data-ttu-id="2f29a-276">Si vous utilisez **Connect-PSSession** sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et elle ne génère pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="2f29a-276">If you use **Connect-PSSession** on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>
* <span data-ttu-id="2f29a-277">Les sessions de bouclage déconnectées avec des jetons interactifs, qui sont créés à l’aide du paramètre *EnableNetworkAccess* , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="2f29a-277">Disconnected loopback sessions with interactive tokens, which are created by using the *EnableNetworkAccess* parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="2f29a-278">Cette restriction protège l'ordinateur contre tout accès malveillant.</span><span class="sxs-lookup"><span data-stu-id="2f29a-278">This restriction protects the computer from malicious access.</span></span>
* <span data-ttu-id="2f29a-279">La valeur de la propriété **State** d’une session **PSSession** est relative à la session active.</span><span class="sxs-lookup"><span data-stu-id="2f29a-279">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
<span data-ttu-id="2f29a-280">Par conséquent, la valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="2f29a-280">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="2f29a-281">Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="2f29a-281">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="2f29a-282">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-282">It might be connected to a different session.</span></span> <span data-ttu-id="2f29a-283">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-283">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="2f29a-284">Une propriété **Availability** avec la valeur None signifie que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-284">An **Availability** value of None indicates that you can connect to the session.</span></span>
<span data-ttu-id="2f29a-285">La valeur Busy indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="2f29a-285">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="2f29a-286">Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="2f29a-286">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) in the MSDN library.</span></span>

  <span data-ttu-id="2f29a-287">Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="2f29a-287">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) in the MSDN library.</span></span>

* <span data-ttu-id="2f29a-288">Vous ne pouvez pas modifier la valeur du délai d’inactivité d’une **session PSSession** quand vous vous connectez à la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-288">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession** .</span></span> <span data-ttu-id="2f29a-289">Le paramètre *SessionOption* de **Connect-PSSession** prend un objet **SessionOption** ayant une valeur **IdleTimeout** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-289">The *SessionOption* parameter of **Connect-PSSession** takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="2f29a-290">Toutefois, la valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la variable $PSSessionOption sont ignorées lors de la connexion à une **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-290">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the $PSSessionOption variable are ignored when connecting to a **PSSession** .</span></span>

  <span data-ttu-id="2f29a-291">Vous pouvez définir et modifier le délai d’inactivité d’une **session PSSession** quand vous créez la **session PSSession** , à l’aide des applets de commande **New-PSSession** ou **Invoke-Command** , et lorsque vous vous déconnectez de la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2f29a-291">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the **New-PSSession** or **Invoke-Command** cmdlets, and when you disconnect from the **PSSession** .</span></span>

  <span data-ttu-id="2f29a-292">La propriété **IdleTimeout** d’une session **PSSession** est critique pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2f29a-292">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span>
<span data-ttu-id="2f29a-293">Une session déconnectée est considérée comme inactive dès qu'elle est déconnectée, même si elle comprend des commandes en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="2f29a-293">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="2f29a-294">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2f29a-294">RELATED LINKS</span></span>

[<span data-ttu-id="2f29a-295">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-295">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="2f29a-296">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-296">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="2f29a-297">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-297">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="2f29a-298">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-298">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="2f29a-299">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f29a-299">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="2f29a-300">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-300">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="2f29a-301">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="2f29a-301">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="2f29a-302">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="2f29a-302">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="2f29a-303">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-303">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="2f29a-304">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f29a-304">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="2f29a-305">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="2f29a-305">Remove-PSSession</span></span>](Remove-PSSession.md)
