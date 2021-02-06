---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: cd0e2b62464a4c34278d42b833a669c6c28e377f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598791"
---
# <span data-ttu-id="ad956-102">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-102">Remove-PSSession</span></span>

## <span data-ttu-id="ad956-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ad956-103">SYNOPSIS</span></span>
<span data-ttu-id="ad956-104">Ferme une ou plusieurs sessions PowerShell (sessions PSSession).</span><span class="sxs-lookup"><span data-stu-id="ad956-104">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="ad956-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ad956-105">SYNTAX</span></span>

### <span data-ttu-id="ad956-106">ID (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ad956-106">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-107">Session</span><span class="sxs-lookup"><span data-stu-id="ad956-107">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-108">ContainerId</span><span class="sxs-lookup"><span data-stu-id="ad956-108">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-109">VMId</span><span class="sxs-lookup"><span data-stu-id="ad956-109">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-110">VMName</span><span class="sxs-lookup"><span data-stu-id="ad956-110">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ad956-111">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-112">Nom</span><span class="sxs-lookup"><span data-stu-id="ad956-112">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad956-113">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ad956-113">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ad956-114">Description</span><span class="sxs-lookup"><span data-stu-id="ad956-114">DESCRIPTION</span></span>

<span data-ttu-id="ad956-115">L’applet de commande **Remove-PSSession** ferme les sessions PowerShell (**sessions PSSession**) dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-115">The **Remove-PSSession** cmdlet closes PowerShell sessions (**PSSessions**) in the current session.</span></span>
<span data-ttu-id="ad956-116">Elle arrête toutes les commandes qui s’exécutent dans **sessions PSSession**, met fin à la **session PSSession** et libère les ressources utilisées par la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="ad956-116">It stops any commands that are running in the **PSSessions**, ends the **PSSession**, and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="ad956-117">Si la **session PSSession** est connectée à un ordinateur distant, cette applet de commande ferme également la connexion entre les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="ad956-117">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="ad956-118">Pour supprimer une session **PSSession**, entrez *le nom*, *ComputerName*, *ID* ou *InstanceID* de la session.</span><span class="sxs-lookup"><span data-stu-id="ad956-118">To remove a **PSSession**, enter the *Name*, *ComputerName*, *ID*, or *InstanceID* of the session.</span></span>

<span data-ttu-id="ad956-119">Si vous avez enregistré la session *PSSession* dans une variable, l’objet de session reste dans la variable, mais l’état de la session *PSSession* est fermé.</span><span class="sxs-lookup"><span data-stu-id="ad956-119">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="ad956-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ad956-120">EXAMPLES</span></span>

### <span data-ttu-id="ad956-121">Exemple 1 : supprimer des sessions à l’aide d’ID</span><span class="sxs-lookup"><span data-stu-id="ad956-121">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="ad956-122">Cette commande supprime les **sessions PSSession** qui ont les ID 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="ad956-122">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="ad956-123">Exemple 2 : supprimer toutes les sessions de la session active</span><span class="sxs-lookup"><span data-stu-id="ad956-123">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="ad956-124">Ces commandes suppriment toutes les **sessions PSSession** de la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-124">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="ad956-125">Bien que les formats des trois commandes semblent différents, ils ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="ad956-125">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="ad956-126">Exemple 3 : fermer des sessions à l’aide de noms</span><span class="sxs-lookup"><span data-stu-id="ad956-126">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="ad956-127">Ces commandes ferment les **sessions PSSession** connectées aux ordinateurs dont le nom commence par serv.</span><span class="sxs-lookup"><span data-stu-id="ad956-127">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="ad956-128">Exemple 4 : fermer les sessions connectées à un port</span><span class="sxs-lookup"><span data-stu-id="ad956-128">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="ad956-129">Cette commande ferme les **sessions PSSession** connectés au port 90.</span><span class="sxs-lookup"><span data-stu-id="ad956-129">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="ad956-130">Vous pouvez utiliser ce format de commande pour identifier les **sessions PSSession** par des propriétés autres que *ComputerName*, *Name*, *InstanceID* et *ID*.</span><span class="sxs-lookup"><span data-stu-id="ad956-130">You can use this command format to identify **PSSessions** by properties other than *ComputerName*, *Name*, *InstanceID*, and *ID*.</span></span>

### <span data-ttu-id="ad956-131">Exemple 5 : fermer une session en fonction de l’ID d’instance</span><span class="sxs-lookup"><span data-stu-id="ad956-131">Example 5: Close a session based on instance ID</span></span>

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

<span data-ttu-id="ad956-132">Ces commandes indiquent comment fermer une **session PSSession** en fonction de son ID d’instance, ou **RemoteRunspaceID**.</span><span class="sxs-lookup"><span data-stu-id="ad956-132">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="ad956-133">La première commande utilise l’applet de commande **obten-PSSession** pour récupérer le **sessions PSSession** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-133">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="ad956-134">Elle utilise un opérateur de pipeline (|) pour envoyer le **sessions PSSession** à l’applet de commande Format-Table, qui met en forme leurs propriétés **ComputerName** et **InstanceID** dans une table.</span><span class="sxs-lookup"><span data-stu-id="ad956-134">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="ad956-135">Le paramètre *AutoSize* compresse les colonnes à afficher.</span><span class="sxs-lookup"><span data-stu-id="ad956-135">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="ad956-136">À partir de l’affichage qui en résulte, vous pouvez identifier la **session PSSession** à fermer, puis copier et coller l' *InstanceID* de cette **session PSSession** dans la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="ad956-136">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="ad956-137">La deuxième commande utilise l’applet de commande **Remove-PSSession** pour supprimer la *session PSSession* avec l’ID d’instance spécifié.</span><span class="sxs-lookup"><span data-stu-id="ad956-137">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="ad956-138">Exemple 6 : créer une fonction qui supprime toutes les sessions dans la session active</span><span class="sxs-lookup"><span data-stu-id="ad956-138">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="ad956-139">Cette fonction supprime toutes les **sessions PSSession** de la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-139">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="ad956-140">Après avoir ajouté cette fonction à votre profil PowerShell, pour supprimer toutes les sessions, tapez `EndPSS` .</span><span class="sxs-lookup"><span data-stu-id="ad956-140">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="ad956-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad956-141">PARAMETERS</span></span>

### <span data-ttu-id="ad956-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ad956-142">-ComputerName</span></span>

<span data-ttu-id="ad956-143">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="ad956-143">Specifies an array of names of computers.</span></span>
<span data-ttu-id="ad956-144">Cette applet de commande ferme les **sessions PSSession** connectés aux ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-144">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="ad956-145">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ad956-145">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ad956-146">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ad956-146">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="ad956-147">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="ad956-147">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ad956-148">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="ad956-148">-ContainerId</span></span>

<span data-ttu-id="ad956-149">Spécifie un tableau d’ID de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ad956-149">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="ad956-150">Cette applet de commande supprime les sessions pour chacun des conteneurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-150">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="ad956-151">Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="ad956-151">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="ad956-152">Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="ad956-152">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad956-153">-Id</span><span class="sxs-lookup"><span data-stu-id="ad956-153">-Id</span></span>

<span data-ttu-id="ad956-154">Spécifie un tableau d’ID de sessions.</span><span class="sxs-lookup"><span data-stu-id="ad956-154">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="ad956-155">Cette applet de commande ferme le *sessions PSSession* avec les ID spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-155">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="ad956-156">Tapez un ou plusieurs ID, en les séparant par des virgules, ou utilisez l’opérateur de plage (..) pour spécifier une plage d’ID.</span><span class="sxs-lookup"><span data-stu-id="ad956-156">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="ad956-157">Un ID est un entier qui identifie de façon unique la session **PSSession** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-157">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="ad956-158">Il est plus facile à mémoriser et à taper que *InstanceID*, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-158">It is easier to remember and type than the *InstanceId*, but it is unique only in the current session.</span></span>
<span data-ttu-id="ad956-159">Pour Rechercher l’ID d’une **session PSSession**, exécutez l’applet de commande Get-PSSession sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="ad956-159">To find the ID of a **PSSession**, run the Get-PSSession cmdlet without parameters.</span></span>

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

### <span data-ttu-id="ad956-160">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="ad956-160">-InstanceId</span></span>

<span data-ttu-id="ad956-161">Spécifie un tableau d’ID d’instance.</span><span class="sxs-lookup"><span data-stu-id="ad956-161">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="ad956-162">Cette applet de commande ferme les **sessions PSSession** qui ont les ID d’instance spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-162">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="ad956-163">L’ID d’instance est un GUID qui identifie de façon unique une session **PSSession** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-163">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="ad956-164">L’ID d’instance est unique, même si plusieurs sessions sont en cours d’exécution sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad956-164">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="ad956-165">L’ID d’instance est stocké dans la propriété **InstanceID** de l’objet qui représente une **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="ad956-165">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="ad956-166">Pour Rechercher l' **InstanceID** de **sessions PSSession** dans la session active, tapez `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="ad956-166">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

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

### <span data-ttu-id="ad956-167">-Name</span><span class="sxs-lookup"><span data-stu-id="ad956-167">-Name</span></span>

<span data-ttu-id="ad956-168">Spécifie un tableau de noms conviviaux de sessions.</span><span class="sxs-lookup"><span data-stu-id="ad956-168">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="ad956-169">Cette applet de commande ferme les **sessions PSSession** qui ont les noms conviviaux spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-169">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="ad956-170">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ad956-170">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ad956-171">Étant donné que le nom convivial d’une **session PSSession** peut ne pas être unique, lorsque vous utilisez le paramètre *Name* , envisagez d’utiliser également le paramètre *WhatIf* ou *Confirm* dans la commande **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="ad956-171">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

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

### <span data-ttu-id="ad956-172">-Session</span><span class="sxs-lookup"><span data-stu-id="ad956-172">-Session</span></span>

<span data-ttu-id="ad956-173">Spécifie les objets de session du **sessions PSSession** à fermer.</span><span class="sxs-lookup"><span data-stu-id="ad956-173">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="ad956-174">Entrez une variable qui contient **sessions PSSession** ou une commande qui crée ou obtient le **sessions PSSession**, tel qu’une commande New-PSSession ou la commande **obtenir-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="ad956-174">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions**, such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="ad956-175">Vous pouvez également diriger un ou plusieurs objets de session vers **Remove-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="ad956-175">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

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

### <span data-ttu-id="ad956-176">-VMId</span><span class="sxs-lookup"><span data-stu-id="ad956-176">-VMId</span></span>

<span data-ttu-id="ad956-177">Spécifie un tableau d’ID de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="ad956-177">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="ad956-178">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-178">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="ad956-179">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ad956-179">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad956-180">-VMName</span><span class="sxs-lookup"><span data-stu-id="ad956-180">-VMName</span></span>

<span data-ttu-id="ad956-181">Spécifie un tableau de noms d'ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="ad956-181">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="ad956-182">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad956-182">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="ad956-183">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l’applet de commande **obtenir-VM** .</span><span class="sxs-lookup"><span data-stu-id="ad956-183">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad956-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ad956-184">-Confirm</span></span>

<span data-ttu-id="ad956-185">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad956-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ad956-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ad956-186">-WhatIf</span></span>

<span data-ttu-id="ad956-187">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad956-187">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ad956-188">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ad956-188">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ad956-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad956-189">CommonParameters</span></span>

<span data-ttu-id="ad956-190">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ad956-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad956-191">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ad956-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad956-192">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ad956-192">INPUTS</span></span>

### <span data-ttu-id="ad956-193">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-193">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="ad956-194">Vous pouvez diriger un objet de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad956-194">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="ad956-195">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ad956-195">OUTPUTS</span></span>

### <span data-ttu-id="ad956-196">None</span><span class="sxs-lookup"><span data-stu-id="ad956-196">None</span></span>

<span data-ttu-id="ad956-197">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="ad956-197">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="ad956-198">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ad956-198">NOTES</span></span>

* <span data-ttu-id="ad956-199">Le paramètre *ID* est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ad956-199">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="ad956-200">Pour supprimer tous les **sessions PSSession** de la session active, tapez `Get-PSSession | Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ad956-200">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="ad956-201">Une **session PSSession** utilise une connexion permanente à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ad956-201">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="ad956-202">Créez une **session PSSession** pour exécuter une série de commandes qui partagent des données.</span><span class="sxs-lookup"><span data-stu-id="ad956-202">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="ad956-203">Pour plus d'informations, voir `Get-Help about_PSSessions`.</span><span class="sxs-lookup"><span data-stu-id="ad956-203">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="ad956-204">Les **sessions PSSession** sont spécifiques à la session active.</span><span class="sxs-lookup"><span data-stu-id="ad956-204">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="ad956-205">Lorsque vous terminez une session, les **sessions PSSession** que vous avez créés dans cette session sont fermés de force.</span><span class="sxs-lookup"><span data-stu-id="ad956-205">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="ad956-206">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ad956-206">RELATED LINKS</span></span>

[<span data-ttu-id="ad956-207">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-207">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="ad956-208">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-208">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="ad956-209">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-209">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="ad956-210">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-210">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="ad956-211">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-211">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="ad956-212">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ad956-212">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="ad956-213">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-213">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="ad956-214">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad956-214">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="ad956-215">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ad956-215">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="ad956-216">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ad956-216">about_Remote</span></span>](About/about_Remote.md)

