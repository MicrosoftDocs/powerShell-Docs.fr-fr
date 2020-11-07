---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: 41f278541d1375697ccb95504b7d7b1d28027786
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344063"
---
# <span data-ttu-id="a16f2-103">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-103">Disconnect-PSSession</span></span>

## <span data-ttu-id="a16f2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a16f2-104">SYNOPSIS</span></span>
<span data-ttu-id="a16f2-105">Se déconnecte d'une session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-105">Disconnects from a session.</span></span>

## <span data-ttu-id="a16f2-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a16f2-106">SYNTAX</span></span>

### <span data-ttu-id="a16f2-107">Session (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a16f2-107">Session (Default)</span></span>

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a16f2-108">Nom</span><span class="sxs-lookup"><span data-stu-id="a16f2-108">Name</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a16f2-109">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a16f2-109">InstanceId</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a16f2-110">Id</span><span class="sxs-lookup"><span data-stu-id="a16f2-110">Id</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a16f2-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a16f2-111">DESCRIPTION</span></span>

<span data-ttu-id="a16f2-112">L' `Disconnect-PSSession` applet de commande déconnecte une session PowerShell (« PSSession »), telle qu’une session démarrée à l’aide `New-PSSession` de l’applet de commande, à partir de la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-112">The `Disconnect-PSSession` cmdlet disconnects a PowerShell session ("PSSession"), such as one started by using the `New-PSSession` cmdlet, from the current session.</span></span> <span data-ttu-id="a16f2-113">Par conséquent, la session PSSession est dans un état déconnecté.</span><span class="sxs-lookup"><span data-stu-id="a16f2-113">As a result, the PSSession is in a disconnected state.</span></span> <span data-ttu-id="a16f2-114">Vous pouvez vous connecter à la session PSSession déconnectée à partir de la session active ou d'une autre session sur l'ordinateur local ou sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a16f2-114">You can connect to the disconnected PSSession from the current session or from another session on the local computer or a different computer.</span></span>

<span data-ttu-id="a16f2-115">L' `Disconnect-PSSession` applet de commande déconnecte uniquement les sessions PSSession ouverts qui sont connectés à la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-115">The `Disconnect-PSSession` cmdlet disconnects only open PSSessions that are connected to the current session.</span></span> <span data-ttu-id="a16f2-116">`Disconnect-PSSession` Impossible de déconnecter les sessions PSSession rompus ou fermés, ou le sessions PSSession interactif a démarré à l’aide de l’applet de commande `Enter-PSSession` et ne peut pas déconnecter les sessions PSSession qui sont connectés à d’autres sessions.</span><span class="sxs-lookup"><span data-stu-id="a16f2-116">`Disconnect-PSSession` cannot disconnect broken or closed PSSessions, or interactive PSSessions started by using the `Enter-PSSession` cmdlet, and it cannot disconnect PSSessions that are connected to other sessions.</span></span>

<span data-ttu-id="a16f2-117">Pour vous reconnecter à une session PSSession déconnectée, utilisez les `Connect-PSSession` applets de commande ou `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="a16f2-117">To reconnect to a disconnected PSSession, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span>

<span data-ttu-id="a16f2-118">Quand une session PSSession est déconnectée, les commandes de la session continuent à s'exécuter jusqu'à ce qu'elles se terminent, sauf si la session PSSession arrive à expiration ou que les commandes de la session PSSession sont bloquées par une mémoire tampon de sortie saturée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-118">When a PSSession is disconnected, the commands in the PSSession continue to run until they complete, unless the PSSession times out or the commands in the PSSession are blocked by a full output buffer.</span></span> <span data-ttu-id="a16f2-119">Pour modifier le délai d'inactivité, utilisez le paramètre **IdleTimeoutSec**.</span><span class="sxs-lookup"><span data-stu-id="a16f2-119">To change the idle timeout, use the **IdleTimeoutSec** parameter.</span></span> <span data-ttu-id="a16f2-120">Pour modifier le mode de mise en mémoire tampon de sortie, utilisez le paramètre **OutputBufferingMode** . vous pouvez également utiliser le paramètre **InDisconnectedSession** de l' `Invoke-Command` applet de commande pour exécuter une commande dans une session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-120">To change the output buffering mode, use the **OutputBufferingMode** parameter You can also use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet to run a command in a disconnected session.</span></span>

<span data-ttu-id="a16f2-121">Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="a16f2-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="a16f2-122">Cette applet de commande est introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="a16f2-122">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a16f2-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a16f2-123">EXAMPLES</span></span>

### <span data-ttu-id="a16f2-124">Exemple 1 : déconnecter une session par nom</span><span class="sxs-lookup"><span data-stu-id="a16f2-124">Example 1 - Disconnect a session by name</span></span>

<span data-ttu-id="a16f2-125">Cette commande déconnecte la session PSSession UpdateSession sur l'ordinateur Server01 de la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-125">This command disconnects the UpdateSession PSSession on the Server01 computer from the current session.</span></span> <span data-ttu-id="a16f2-126">La commande utilise le paramètre **Name** pour identifier la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="a16f2-126">The command uses the **Name** parameter to identify the PSSession.</span></span>

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="a16f2-127">La sortie indique que la tentative de déconnexion a réussi.</span><span class="sxs-lookup"><span data-stu-id="a16f2-127">The output shows that the attempt to disconnect was successful.</span></span> <span data-ttu-id="a16f2-128">L'état de session est Disconnected et la disponibilité est None, ce qui indique que la session n'est pas occupée et peut être reconnectée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-128">The session state is Disconnected and the Availability is None, which indicates that the session is not busy and can be reconnected.</span></span>

### <span data-ttu-id="a16f2-129">Exemple 2 : déconnecter une session d’un ordinateur spécifique</span><span class="sxs-lookup"><span data-stu-id="a16f2-129">Example 2 - Disconnect a session from a specific computer</span></span>

<span data-ttu-id="a16f2-130">Cette commande déconnecte la session PSSession ITTask sur l'ordinateur Server12 de la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-130">This command disconnects the ITTask PSSession on the Server12 computer from the current session.</span></span>
<span data-ttu-id="a16f2-131">La session ITTask a été créée dans la session active et se connecte à l'ordinateur Server12.</span><span class="sxs-lookup"><span data-stu-id="a16f2-131">The ITTask session was created in the current session and connects to the Server12 computer.</span></span> <span data-ttu-id="a16f2-132">La commande utilise l' `Get-PSSession` applet de commande pour accéder à la session et `Disconnect-PSSession` à l’applet de commande pour la déconnecter.</span><span class="sxs-lookup"><span data-stu-id="a16f2-132">The command uses the `Get-PSSession` cmdlet to get the session and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span>

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

<span data-ttu-id="a16f2-133">La `Disconnect-PSSession` commande utilise le paramètre **OutputBufferingMode** pour définir le mode de sortie sur **Drop**.</span><span class="sxs-lookup"><span data-stu-id="a16f2-133">The `Disconnect-PSSession` command uses the **OutputBufferingMode** parameter to set the output mode to **Drop**.</span></span> <span data-ttu-id="a16f2-134">Ce paramètre garantit que le script qui s'exécute dans la session peut continuer de s'exécuter même si la mémoire tampon de la sortie de session est saturée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-134">This setting ensures that the script that is running in the session can continue to run even if the session output buffer is full.</span></span> <span data-ttu-id="a16f2-135">Comme le script écrit sa sortie dans un rapport sur un partage de fichiers, une autre sortie peut être perdue sans conséquence.</span><span class="sxs-lookup"><span data-stu-id="a16f2-135">Because the script writes its output to a report on a file share, other output can be lost without consequence.</span></span>

<span data-ttu-id="a16f2-136">La commande utilise également le paramètre **IdleTimeoutSec** pour étendre le délai d'inactivité de la session à 24 heures.</span><span class="sxs-lookup"><span data-stu-id="a16f2-136">The command also uses the **IdleTimeoutSec** parameter to extend the idle timeout of the session to 24 hours.</span></span> <span data-ttu-id="a16f2-137">Ce paramètre laisse le temps à cet administrateur ou à d'autres administrateurs de se reconnecter à la session pour vérifier que le script s'est exécuté et résoudre les problèmes si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a16f2-137">This setting allows time for this administrator or other administrators to reconnect to the session to verify that the script ran and troubleshoot if needed.</span></span>

### <span data-ttu-id="a16f2-138">Exemple 3 : utilisation de plusieurs sessions PSSession sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="a16f2-138">Example 3 - Using multiple PSSessions on multiple computers</span></span>

<span data-ttu-id="a16f2-139">Cette série de commandes montre comment l' `Disconnect-PSSession` applet de commande peut être utilisée dans un scénario d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="a16f2-139">This series of commands shows how the `Disconnect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="a16f2-140">Dans ce cas, un nouveau technicien démarre un script dans une session sur un ordinateur distant et rencontre un problème.</span><span class="sxs-lookup"><span data-stu-id="a16f2-140">In this case, a new technician starts a script in a session on a remote computer and runs into a problem.</span></span> <span data-ttu-id="a16f2-141">Le technicien se déconnecte de la session afin qu'un responsable plus expérimenté puisse s'y connecter et résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="a16f2-141">The technician disconnects from the session so that a more experienced manager can connect to the session and resolve the problem.</span></span>

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

<span data-ttu-id="a16f2-142">Le technicien commence par la création de sessions sur plusieurs ordinateurs distants et l'exécution d'un script dans chaque session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-142">The technician begins by creating sessions on several remote computers and running a script in each session.</span></span> <span data-ttu-id="a16f2-143">La première commande utilise l' `New-PSSession` applet de commande pour créer la session ITTask sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a16f2-143">The first command uses the `New-PSSession` cmdlet to create the ITTask session on three remote computers.</span></span> <span data-ttu-id="a16f2-144">La commande enregistre les sessions dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="a16f2-144">The command saves the sessions in the $s variable.</span></span> <span data-ttu-id="a16f2-145">La deuxième commande utilise le paramètre **filePath** de l' `Invoke-Command` applet de commande pour exécuter un script dans les sessions de la variable $s.</span><span class="sxs-lookup"><span data-stu-id="a16f2-145">The second command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run a script in the sessions in the $s variable.</span></span>

<span data-ttu-id="a16f2-146">Le script en cours d'exécution sur l'ordinateur Srv1 génère des erreurs inattendues.</span><span class="sxs-lookup"><span data-stu-id="a16f2-146">The script running on the Srv1 computer generates unexpected errors.</span></span> <span data-ttu-id="a16f2-147">Le technicien contacte son responsable et lui demande de l'aide.</span><span class="sxs-lookup"><span data-stu-id="a16f2-147">The technician contacts his manager and asks for assistance.</span></span> <span data-ttu-id="a16f2-148">Le responsable dirige le technicien à se déconnecter de la session pour qu’il puisse l’examiner. La deuxième commande utilise l' `Get-PSSession` applet de commande pour récupérer la session ITTask sur l’ordinateur Srv1 et l' `Disconnect-PSSession` applet de commande pour la déconnecter.</span><span class="sxs-lookup"><span data-stu-id="a16f2-148">The manager directs the technician to disconnect from the session so he can investigate.The second command uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span> <span data-ttu-id="a16f2-149">Cette commande n’affecte pas les sessions ITTask sur les autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a16f2-149">This command does not affect the ITTask sessions on the other computers.</span></span>

<span data-ttu-id="a16f2-150">La troisième commande utilise l' `Get-PSSession` applet de commande pour récupérer les sessions ITTask.</span><span class="sxs-lookup"><span data-stu-id="a16f2-150">The third command uses the `Get-PSSession` cmdlet to get the ITTask sessions.</span></span> <span data-ttu-id="a16f2-151">La sortie indique que les sessions ITTask sur les ordinateurs Srv2 et Srv30 n'ont pas été affectées par la commande de déconnexion.</span><span class="sxs-lookup"><span data-stu-id="a16f2-151">The output shows that the ITTask sessions on the Srv2 and Srv30 computers were not affected by the command to disconnect.</span></span>

<span data-ttu-id="a16f2-152">Le gestionnaire ouvre une session sur son ordinateur privé, se connecte à son réseau d’entreprise, démarre PowerShell et utilise l' `Get-PSSession` applet de commande pour accéder à la session ITTask sur l’ordinateur Srv1.</span><span class="sxs-lookup"><span data-stu-id="a16f2-152">The manager logs on to his home computer, connects to his corporate network, starts PowerShell, and uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="a16f2-153">Il utilise les informations d'identification du technicien pour accéder à la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-153">He uses the credentials of the technician to access the session.</span></span>

<span data-ttu-id="a16f2-154">Ensuite, le gestionnaire utilise l' `Connect-PSSession` applet de commande pour se connecter à la session ITTask sur l’ordinateur Srv1.</span><span class="sxs-lookup"><span data-stu-id="a16f2-154">Next, the manager uses the `Connect-PSSession` cmdlet to connect to the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="a16f2-155">La commande enregistre la session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="a16f2-155">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="a16f2-156">Le gestionnaire utilise l' `Invoke-Command` applet de commande pour exécuter des commandes de diagnostic dans la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="a16f2-156">The manager uses the `Invoke-Command` cmdlet to run some diagnostic commands in the session in the `$s` variable.</span></span> <span data-ttu-id="a16f2-157">Il réalise que le script a échoué, car il n'a pas trouvé de répertoire requis.</span><span class="sxs-lookup"><span data-stu-id="a16f2-157">He recognizes that the script failed because it did not find a required directory.</span></span>
<span data-ttu-id="a16f2-158">Le gestionnaire utilise la `MkDir` fonction pour créer le répertoire, puis il redémarre le `Get-PatchStatus.ps1` script et se déconnecte de la session. Le responsable signale ses conclusions au technicien, suggère qu’il se reconnecte à la session pour effectuer les tâches et lui demande d’ajouter une commande au `Get-PatchStatus.ps1` script qui crée le répertoire requis s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="a16f2-158">The manager uses the `MkDir` function to create the directory, and then he restarts the `Get-PatchStatus.ps1` script and disconnects from the session.The manager reports his findings to the technician, suggests that he reconnect to the session to complete the tasks, and asks him to add a command to the `Get-PatchStatus.ps1` script that creates the required directory if it does not exist.</span></span>

### <span data-ttu-id="a16f2-159">Exemple 4-modifier la valeur du délai d’attente pour une session PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-159">Example 4 - Change the timeout value for a PSSession</span></span>

<span data-ttu-id="a16f2-160">Cet exemple montre comment corriger la valeur de la propriété **IdleTimeout** d'une session pour pouvoir la déconnecter.</span><span class="sxs-lookup"><span data-stu-id="a16f2-160">This example shows how to correct the value of the **IdleTimeout** property of a session so that it can be disconnected.</span></span>

<span data-ttu-id="a16f2-161">La propriété du délai d'inactivité d'une session est essentielle pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée avant sa suppression.</span><span class="sxs-lookup"><span data-stu-id="a16f2-161">The idle timeout property of a session is critical to disconnected sessions, because it determines how long a disconnected session is maintained before it is deleted.</span></span> <span data-ttu-id="a16f2-162">Vous pouvez définir l'option de délai d'inactivité quand vous créez une session et quand vous la déconnectez.</span><span class="sxs-lookup"><span data-stu-id="a16f2-162">You can set the idle timeout option when you create a session and when you disconnect it.</span></span> <span data-ttu-id="a16f2-163">Les valeurs par défaut pour le délai d’inactivité d’une session sont définies dans la `$PSSessionOption` variable de préférence sur l’ordinateur local et dans la configuration de session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a16f2-163">The default values for the idle timeout of a session are set in the `$PSSessionOption` preference variable on the local computer and in the session configuration on the remote computer.</span></span> <span data-ttu-id="a16f2-164">Les valeurs définies pour la session sont prioritaires sur les valeurs définies dans la configuration de session, mais les valeurs de session ne peuvent pas dépasser les quotas définis dans la configuration de la session, tels que la valeur **MaxIdleTimeoutMs**.</span><span class="sxs-lookup"><span data-stu-id="a16f2-164">Values set for the session take precedence over values set in the session configuration, but session values cannot exceed quotas set in the session configuration, such as the **MaxIdleTimeoutMs** value.</span></span>

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

<span data-ttu-id="a16f2-165">La première commande utilise l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-165">The first command uses the `New-PSSessionOption` cmdlet to create a session option object.</span></span> <span data-ttu-id="a16f2-166">Elle utilise le paramètre **IdleTimeout** pour définir un délai d'inactivité de 48 heures (172800000 millisecondes).</span><span class="sxs-lookup"><span data-stu-id="a16f2-166">It uses the **IdleTimeout** parameter to set an idle timeout of 48 hours (172800000 milliseconds).</span></span> <span data-ttu-id="a16f2-167">La commande enregistre l'objet d'options de session dans la variable $Timeout.</span><span class="sxs-lookup"><span data-stu-id="a16f2-167">The command saves the session option object in the $Timeout variable.</span></span>

<span data-ttu-id="a16f2-168">La deuxième commande utilise l' `New-PSSession` applet de commande pour créer la session ITTask sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="a16f2-168">The second command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="a16f2-169">La commande enregistre la session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="a16f2-169">The command save the session in the $s variable.</span></span> <span data-ttu-id="a16f2-170">La valeur du paramètre **SessionOption** est le délai d'inactivité de 48 heures dans la variable $Timeout.</span><span class="sxs-lookup"><span data-stu-id="a16f2-170">The value of the **SessionOption** parameter is the 48-hour idle timeout in the $Timeout variable.</span></span>

<span data-ttu-id="a16f2-171">La troisième commande déconnecte la session ITTask dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="a16f2-171">The third command disconnects the ITTask session in the $s variable.</span></span> <span data-ttu-id="a16f2-172">La commande échoue, car la valeur de délai d'inactivité de la session dépasse le quota **MaxIdleTimeoutMs** dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-172">The command fails because the idle timeout value of the session exceeds the **MaxIdleTimeoutMs** quota in the session configuration.</span></span> <span data-ttu-id="a16f2-173">Comme le délai d'inactivité n'est pas utilisé tant que la session n'est pas déconnectée, cette violation peut passer inaperçue pendant que la session est en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="a16f2-173">Because the idle timeout is not used until the session is disconnected, this violation can go undetected while the session is in use.</span></span>

<span data-ttu-id="a16f2-174">La quatrième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-PSSessionConfiguration` commande pour la configuration de session Microsoft. PowerShell sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="a16f2-174">The fourth command uses the `Invoke-Command` cmdlet to run a `Get-PSSessionConfiguration` command for the Microsoft.PowerShell session configuration on the Server01 computer.</span></span> <span data-ttu-id="a16f2-175">La commande utilise l' `Format-List` applet de commande pour afficher toutes les propriétés de la configuration de session dans une liste. La sortie indique que la propriété **MaxIdleTimeoutMS** , qui établit la valeur **IdleTimeout** maximale autorisée pour les sessions qui utilisent la configuration de session, est de 43,2 millions millisecondes (12 heures).</span><span class="sxs-lookup"><span data-stu-id="a16f2-175">The command uses the `Format-List` cmdlet to display all properties of the session configuration in a list.The output shows that the **MaxIdleTimeoutMS** property, which establishes the maximum permitted **IdleTimeout** value for sessions that use the session configuration, is 43200000 milliseconds (12 hours).</span></span>

<span data-ttu-id="a16f2-176">La cinquième commande obtient les valeurs d'option de la session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="a16f2-176">The fifth command gets the session option values of the session in the $s variable.</span></span> <span data-ttu-id="a16f2-177">Les valeurs de nombreuses options de session sont des propriétés de la propriété **ConnectionInfo** de la propriété d' **instance d’exécution** de la session. La sortie indique que la valeur de la propriété **IdleTimeout** de la session est 172,8 millions millisecondes (48 heures), ce qui viole le quota **MaxIdleTimeoutMs** de 12 heures dans la configuration de session. Pour résoudre ce conflit, vous pouvez utiliser le paramètre **ConfigurationName** pour sélectionner une autre configuration de session ou utiliser le paramètre **IdleTimeout** pour réduire le délai d’inactivité de la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-177">The values of many session options are properties of the **ConnectionInfo** property of the **Runspace** property of the session.The output shows that the value of the **IdleTimeout** property of the session is 172800000 milliseconds (48 hours), which violates the **MaxIdleTimeoutMs** quota of 12 hours in the session configuration.To resolve this conflict, you can use the **ConfigurationName** parameter to select a different session configuration or use the **IdleTimeout** parameter to reduce the idle timeout of the session.</span></span>

<span data-ttu-id="a16f2-178">La sixième commande déconnecte la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-178">The sixth command disconnects the session.</span></span> <span data-ttu-id="a16f2-179">Elle utilise le paramètre **IdleTimeoutSec** pour affecter au délai d'inactivité la valeur maximale de 12 heures.</span><span class="sxs-lookup"><span data-stu-id="a16f2-179">It uses the **IdleTimeoutSec** parameter to set the idle timeout to the 12-hour maximum.</span></span>

<span data-ttu-id="a16f2-180">La septième commande obtient la valeur de la propriété **IdleTimeout** de la session déconnectée, qui est mesurée en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="a16f2-180">The seventh command gets the value of the **IdleTimeout** property of the disconnected session, which is measured in milliseconds.</span></span> <span data-ttu-id="a16f2-181">La sortie confirme que la commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="a16f2-181">The output confirms that the command was successful.</span></span>

## <span data-ttu-id="a16f2-182">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="a16f2-182">PARAMETERS</span></span>

### <span data-ttu-id="a16f2-183">-Id</span><span class="sxs-lookup"><span data-stu-id="a16f2-183">-Id</span></span>

<span data-ttu-id="a16f2-184">Se déconnecte de sessions avec l'ID de session spécifié.</span><span class="sxs-lookup"><span data-stu-id="a16f2-184">Disconnects from sessions with the specified session ID.</span></span> <span data-ttu-id="a16f2-185">Tapez un ou plusieurs ID (séparés par des virgules) ou utilisez l'opérateur de plage (..) pour spécifier une plage d'ID.</span><span class="sxs-lookup"><span data-stu-id="a16f2-185">Type one or more IDs (separated by commas), or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="a16f2-186">Pour obtenir l’ID d’une session, utilisez l' `Get-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a16f2-186">To get the ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="a16f2-187">L'ID d'instance est stocké dans la propriété **ID** de la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-187">The instance ID is stored in the **ID** property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a16f2-188">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="a16f2-188">-IdleTimeoutSec</span></span>

<span data-ttu-id="a16f2-189">Modifie la valeur de délai d'inactivité de la session PSSession déconnectée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-189">Changes the idle timeout value of the disconnected PSSession.</span></span> <span data-ttu-id="a16f2-190">Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="a16f2-190">Enter a value in seconds.</span></span> <span data-ttu-id="a16f2-191">La valeur minimale est 60 (1 minute).</span><span class="sxs-lookup"><span data-stu-id="a16f2-191">The minimum value is 60 (1 minute).</span></span>

<span data-ttu-id="a16f2-192">Le délai d'inactivité détermine la durée pendant laquelle la session PSSession déconnectée est conservée sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a16f2-192">The idle timeout determines how long the disconnected PSSession is maintained on the remote computer.</span></span> <span data-ttu-id="a16f2-193">Quand le délai expire, la session PSSession est supprimée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-193">When the timeout expires, the PSSession is deleted.</span></span>

<span data-ttu-id="a16f2-194">Les sessions PSSession déconnectées sont considérées comme inactives dès qu'elles sont déconnectées, même si elles comprennent des commandes en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a16f2-194">Disconnected PSSessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="a16f2-195">La valeur par défaut pour le délai d'inactivité d'une session est définie par la valeur de la propriété **IdleTimeoutMs** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-195">The default value for the idle timeout of a session is set by the value of the **IdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="a16f2-196">La valeur par défaut est égale à 7 200 000 millisecondes (2 heures).</span><span class="sxs-lookup"><span data-stu-id="a16f2-196">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="a16f2-197">La valeur de ce paramètre est prioritaire sur la valeur de la propriété **IdleTimeout** de la variable de préférence $PSSessionOption et la valeur de délai d'inactivité par défaut dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-197">The value of this parameter takes precedence over the value of the **IdleTimeout** property of the $PSSessionOption preference variable and the default idle timeout value in the session configuration.</span></span> <span data-ttu-id="a16f2-198">Toutefois, cette valeur ne peut pas dépasser la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-198">However, this value cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="a16f2-199">La valeur par défaut de **MaxIdleTimeoutMs** est 12 heures (43200000 millisecondes).</span><span class="sxs-lookup"><span data-stu-id="a16f2-199">The default value of **MaxIdleTimeoutMs** is 12 hours (43200000 milliseconds).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a16f2-200">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="a16f2-200">-InstanceId</span></span>

<span data-ttu-id="a16f2-201">Se déconnecte de sessions avec les ID d'instance spécifiés.</span><span class="sxs-lookup"><span data-stu-id="a16f2-201">Disconnects from sessions with the specified instance IDs.</span></span>

<span data-ttu-id="a16f2-202">L'ID d'instance est un GUID qui identifie une session sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="a16f2-202">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="a16f2-203">L'ID d'instance est unique, même entre plusieurs sessions sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a16f2-203">The instance ID is unique, even across multiple sessions on multiple computers.</span></span>

<span data-ttu-id="a16f2-204">Pour obtenir l’ID d’instance d’une session, utilisez l’applet de commande `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="a16f2-204">To get the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="a16f2-205">L’ID d’instance est stocké dans la propriété **InstanceID** de la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-205">The instance ID is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a16f2-206">-Name</span><span class="sxs-lookup"><span data-stu-id="a16f2-206">-Name</span></span>

<span data-ttu-id="a16f2-207">Se déconnecte de sessions avec les noms conviviaux spécifiés.</span><span class="sxs-lookup"><span data-stu-id="a16f2-207">Disconnects from sessions with the specified friendly names.</span></span> <span data-ttu-id="a16f2-208">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a16f2-208">Wildcards are permitted.</span></span>

<span data-ttu-id="a16f2-209">Pour obtenir le nom convivial d’une session, utilisez l' `Get-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a16f2-209">To get the friendly name of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="a16f2-210">Le nom convivial est stocké dans la propriété **Name** de la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-210">The friendly name is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a16f2-211">-Session</span><span class="sxs-lookup"><span data-stu-id="a16f2-211">-Session</span></span>

<span data-ttu-id="a16f2-212">Se déconnecte de sessions PSSession spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a16f2-212">Disconnects from the specified PSSessions.</span></span> <span data-ttu-id="a16f2-213">Entrez les objets PSSession, tels que ceux que l’applet de commande `New-PSSession` retourne.</span><span class="sxs-lookup"><span data-stu-id="a16f2-213">Enter PSSession objects, such as those that the `New-PSSession` cmdlet returns.</span></span> <span data-ttu-id="a16f2-214">Vous pouvez également diriger un objet PSSession vers `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="a16f2-214">You can also pipe a PSSession object to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="a16f2-215">L' `Get-PSSession` applet de commande peut obtenir toutes les sessions PSSession qui se terminent sur un ordinateur distant, y compris les sessions PSSession qui sont déconnectés et les sessions PSSession qui sont connectés à d’autres sessions sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a16f2-215">The `Get-PSSession` cmdlet can get all PSSessions that terminate at a remote computer, including PSSessions that are disconnected and PSSessions that are connected to other sessions on other computers.</span></span> <span data-ttu-id="a16f2-216">`Disconnect-PSSession` déconnecte uniquement PSSession qui sont connectés à la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-216">`Disconnect-PSSession` disconnects only PSSession that are connected to the current session.</span></span> <span data-ttu-id="a16f2-217">Si vous dirigez d’autres sessions PSSession vers `Disconnect-PSSession` , la `Disconnect-PSSession` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="a16f2-217">If you pipe other PSSessions to `Disconnect-PSSession`, the `Disconnect-PSSession` command fails.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a16f2-218">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a16f2-218">-ThrottleLimit</span></span>

<span data-ttu-id="a16f2-219">Définit la limite de limitation pour la `Disconnect-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="a16f2-219">Sets the throttle limit for the `Disconnect-PSSession` command.</span></span>

<span data-ttu-id="a16f2-220">Le seuil de limitation correspond au nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="a16f2-220">The throttle limit is the maximum number of concurrent connections that can be established to run this command.</span></span> <span data-ttu-id="a16f2-221">Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-221">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="a16f2-222">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a16f2-222">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a16f2-223">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="a16f2-223">-OutputBufferingMode</span></span>

<span data-ttu-id="a16f2-224">Détermine comment la sortie de la commande est gérée dans la session déconnectée quand la mémoire tampon de la sortie est saturée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-224">Determines how command output is managed in the disconnected session when the output buffer is full.</span></span> <span data-ttu-id="a16f2-225">La valeur par défaut est **Block**.</span><span class="sxs-lookup"><span data-stu-id="a16f2-225">The default value is **Block**.</span></span>

<span data-ttu-id="a16f2-226">Si la commande de la session déconnectée retourne une sortie et que la mémoire tampon de la sortie se remplit, la valeur de ce paramètre détermine en réalité si la commande continue de s'exécuter pendant que la session est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-226">If the command in the disconnected session is returning output and the output buffer fills, the value of this parameter effectively determines whether the command continues to run while the session is disconnected.</span></span> <span data-ttu-id="a16f2-227">La valeur **Block** suspend la commande jusqu'à ce que la session soit rouverte.</span><span class="sxs-lookup"><span data-stu-id="a16f2-227">A value of **Block** suspends the command until the session is reconnected.</span></span> <span data-ttu-id="a16f2-228">La valeur **Drop** permet l'exécution de la commande, même si des données peuvent être perdues.</span><span class="sxs-lookup"><span data-stu-id="a16f2-228">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="a16f2-229">Quand vous utilisez la valeur **Drop** , redirigez la sortie de la commande vers un fichier sur disque.</span><span class="sxs-lookup"><span data-stu-id="a16f2-229">When using the **Drop** value, redirect the command output to a file on disk.</span></span>

<span data-ttu-id="a16f2-230">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="a16f2-230">Valid values are:</span></span>

- <span data-ttu-id="a16f2-231">**Bloquer** : lorsque la mémoire tampon de sortie est pleine, l’exécution est suspendue jusqu’à ce que la mémoire tampon soit désactivée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-231">**Block** : When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="a16f2-232">**Drop** : lorsque la mémoire tampon de sortie est pleine, l’exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="a16f2-232">**Drop** : When the output buffer is full, execution continues.</span></span> <span data-ttu-id="a16f2-233">Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-233">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="a16f2-234">**Aucun** : aucun mode de mise en mémoire tampon de sortie n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="a16f2-234">**None** : No output buffering mode is specified.</span></span> <span data-ttu-id="a16f2-235">La valeur de la propriété **OutputBufferingMode** de la configuration de session est utilisée pour la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-235">The value of the **OutputBufferingMode** property of the session configuration is used for the disconnected session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a16f2-236">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a16f2-236">-Confirm</span></span>

<span data-ttu-id="a16f2-237">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a16f2-237">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a16f2-238">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a16f2-238">-WhatIf</span></span>

<span data-ttu-id="a16f2-239">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a16f2-239">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a16f2-240">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-240">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a16f2-241">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a16f2-241">CommonParameters</span></span>

<span data-ttu-id="a16f2-242">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a16f2-242">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a16f2-243">Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a16f2-243">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a16f2-244">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a16f2-244">INPUTS</span></span>

### <span data-ttu-id="a16f2-245">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-245">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="a16f2-246">Vous pouvez diriger une session vers `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="a16f2-246">You can pipe a session to `Disconnect-PSSession`.</span></span>

## <span data-ttu-id="a16f2-247">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a16f2-247">OUTPUTS</span></span>

### <span data-ttu-id="a16f2-248">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-248">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="a16f2-249">`Disconnect-PSSession` retourne un objet qui représente la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-249">`Disconnect-PSSession` returns an object that represents the session that it disconnected.</span></span>

## <span data-ttu-id="a16f2-250">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a16f2-250">NOTES</span></span>

<span data-ttu-id="a16f2-251">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="a16f2-251">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="a16f2-252">L' `Disconnect-PSSession` applet de commande fonctionne uniquement lorsque les ordinateurs locaux et distants exécutent PowerShell 3,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a16f2-252">The `Disconnect-PSSession` cmdlet works only when the local and remote computers are running PowerShell 3.0 or later.</span></span>
- <span data-ttu-id="a16f2-253">Si vous utilisez l' `Disconnect-PSSession` applet de commande sur une session déconnectée, la commande n’a aucun effet sur la session et elle ne génère pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="a16f2-253">If you use the `Disconnect-PSSession` cmdlet on a disconnected session, the command has no effect on the session and it does not generate errors.</span></span>
- <span data-ttu-id="a16f2-254">Les sessions de bouclage déconnectées ayant des jetons de sécurité interactifs (ceux créés avec le paramètre **EnableNetworkAccess** ) peuvent être reconnectées uniquement à partir de l'ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="a16f2-254">Disconnected loopback sessions with interactive security tokens (those created with the **EnableNetworkAccess** parameter) can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="a16f2-255">Cette restriction protège l'ordinateur contre tout accès malveillant.</span><span class="sxs-lookup"><span data-stu-id="a16f2-255">This restriction protects the computer from malicious access.</span></span>
- <span data-ttu-id="a16f2-256">Quand vous déconnectez une session PSSession, l'état de session est **Disconnected** et la disponibilité est **None**.</span><span class="sxs-lookup"><span data-stu-id="a16f2-256">When you disconnect a PSSession, the session state is **Disconnected** and the availability is **None**.</span></span>

  <span data-ttu-id="a16f2-257">La valeur de la propriété **State** dépend de la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-257">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="a16f2-258">Par conséquent, la valeur **Disconnected** signifie que la session PSSession n'est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="a16f2-258">Therefore, a value of **Disconnected** means that the PSSession is not connected to the current session.</span></span> <span data-ttu-id="a16f2-259">Toutefois, cela ne signifie pas que la session PSSession est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="a16f2-259">However, it does not mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="a16f2-260">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-260">It might be connected to a different session.</span></span> <span data-ttu-id="a16f2-261">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.</span><span class="sxs-lookup"><span data-stu-id="a16f2-261">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="a16f2-262">Une propriété **Availability** avec la valeur **None** signifie que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-262">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="a16f2-263">La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session PSSession, car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="a16f2-263">A value of **Busy** indicates that you cannot connect to the PSSession because it is connected to another session.</span></span>

  <span data-ttu-id="a16f2-264">Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [énumération RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="a16f2-264">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="a16f2-265">Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [énumération RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="a16f2-265">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="a16f2-266">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a16f2-266">RELATED LINKS</span></span>

[<span data-ttu-id="a16f2-267">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-267">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="a16f2-268">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-268">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="a16f2-269">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-269">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="a16f2-270">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-270">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="a16f2-271">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16f2-271">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="a16f2-272">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-272">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="a16f2-273">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="a16f2-273">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="a16f2-274">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="a16f2-274">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="a16f2-275">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-275">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="a16f2-276">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16f2-276">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="a16f2-277">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="a16f2-277">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="a16f2-278">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a16f2-278">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="a16f2-279">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a16f2-279">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="a16f2-280">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="a16f2-280">about_Remote_Disconnected_Sessions</span></span>](About/about_Remote_Disconnected_Sessions.md)
