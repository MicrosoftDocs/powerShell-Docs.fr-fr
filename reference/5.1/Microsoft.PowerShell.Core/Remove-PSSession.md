---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: e613b8a0250b966adc832f4e61c637c41d63f19f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202678"
---
# <span data-ttu-id="f272f-103">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-103">Remove-PSSession</span></span>

## <span data-ttu-id="f272f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f272f-104">SYNOPSIS</span></span>
<span data-ttu-id="f272f-105">Ferme une ou plusieurs sessions PowerShell (sessions PSSession).</span><span class="sxs-lookup"><span data-stu-id="f272f-105">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="f272f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f272f-106">SYNTAX</span></span>

### <span data-ttu-id="f272f-107">ID (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f272f-107">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-108">session</span><span class="sxs-lookup"><span data-stu-id="f272f-108">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-109">ContainerId</span><span class="sxs-lookup"><span data-stu-id="f272f-109">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-110">VMId</span><span class="sxs-lookup"><span data-stu-id="f272f-110">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-111">VMName</span><span class="sxs-lookup"><span data-stu-id="f272f-111">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f272f-112">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-113">Nom</span><span class="sxs-lookup"><span data-stu-id="f272f-113">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f272f-114">ComputerName</span><span class="sxs-lookup"><span data-stu-id="f272f-114">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f272f-115">Description</span><span class="sxs-lookup"><span data-stu-id="f272f-115">DESCRIPTION</span></span>

<span data-ttu-id="f272f-116">L’applet de commande **Remove-PSSession** ferme les sessions PowerShell ( **sessions PSSession** ) dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-116">The **Remove-PSSession** cmdlet closes PowerShell sessions ( **PSSessions** ) in the current session.</span></span>
<span data-ttu-id="f272f-117">Elle arrête toutes les commandes qui s’exécutent dans **sessions PSSession** , met fin à la **session PSSession** et libère les ressources utilisées par la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f272f-117">It stops any commands that are running in the **PSSessions** , ends the **PSSession** , and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="f272f-118">Si la **session PSSession** est connectée à un ordinateur distant, cette applet de commande ferme également la connexion entre les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="f272f-118">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="f272f-119">Pour supprimer une session **PSSession** , entrez *le nom* , *ComputerName* , *ID* ou *InstanceID* de la session.</span><span class="sxs-lookup"><span data-stu-id="f272f-119">To remove a **PSSession** , enter the *Name* , *ComputerName* , *ID* , or *InstanceID* of the session.</span></span>

<span data-ttu-id="f272f-120">Si vous avez enregistré la session *PSSession* dans une variable, l’objet de session reste dans la variable, mais l’état de la session *PSSession* est fermé.</span><span class="sxs-lookup"><span data-stu-id="f272f-120">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="f272f-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f272f-121">EXAMPLES</span></span>

### <span data-ttu-id="f272f-122">Exemple 1 : supprimer des sessions à l’aide d’ID</span><span class="sxs-lookup"><span data-stu-id="f272f-122">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="f272f-123">Cette commande supprime les **sessions PSSession** qui ont les ID 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="f272f-123">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="f272f-124">Exemple 2 : supprimer toutes les sessions de la session active</span><span class="sxs-lookup"><span data-stu-id="f272f-124">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="f272f-125">Ces commandes suppriment toutes les **sessions PSSession** de la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-125">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="f272f-126">Bien que les formats des trois commandes semblent différents, ils ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="f272f-126">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="f272f-127">Exemple 3 : fermer des sessions à l’aide de noms</span><span class="sxs-lookup"><span data-stu-id="f272f-127">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="f272f-128">Ces commandes ferment les **sessions PSSession** connectées aux ordinateurs dont le nom commence par serv.</span><span class="sxs-lookup"><span data-stu-id="f272f-128">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="f272f-129">Exemple 4 : fermer les sessions connectées à un port</span><span class="sxs-lookup"><span data-stu-id="f272f-129">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="f272f-130">Cette commande ferme les **sessions PSSession** connectés au port 90.</span><span class="sxs-lookup"><span data-stu-id="f272f-130">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="f272f-131">Vous pouvez utiliser ce format de commande pour identifier les **sessions PSSession** par des propriétés autres que *ComputerName* , *Name* , *InstanceID* et *ID* .</span><span class="sxs-lookup"><span data-stu-id="f272f-131">You can use this command format to identify **PSSessions** by properties other than *ComputerName* , *Name* , *InstanceID* , and *ID* .</span></span>

### <span data-ttu-id="f272f-132">Exemple 5 : fermer une session en fonction de l’ID d’instance</span><span class="sxs-lookup"><span data-stu-id="f272f-132">Example 5: Close a session based on instance ID</span></span>

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

<span data-ttu-id="f272f-133">Ces commandes indiquent comment fermer une **session PSSession** en fonction de son ID d’instance, ou **RemoteRunspaceID** .</span><span class="sxs-lookup"><span data-stu-id="f272f-133">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID** .</span></span>

<span data-ttu-id="f272f-134">La première commande utilise l’applet de commande **obten-PSSession** pour récupérer le **sessions PSSession** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-134">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="f272f-135">Elle utilise un opérateur de pipeline (|) pour envoyer le **sessions PSSession** à l’applet de commande Format-Table, qui met en forme leurs propriétés **ComputerName** et **InstanceID** dans une table.</span><span class="sxs-lookup"><span data-stu-id="f272f-135">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="f272f-136">Le paramètre *AutoSize* compresse les colonnes à afficher.</span><span class="sxs-lookup"><span data-stu-id="f272f-136">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="f272f-137">À partir de l’affichage qui en résulte, vous pouvez identifier la **session PSSession** à fermer, puis copier et coller l' *InstanceID* de cette **session PSSession** dans la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="f272f-137">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="f272f-138">La deuxième commande utilise l’applet de commande **Remove-PSSession** pour supprimer la *session PSSession* avec l’ID d’instance spécifié.</span><span class="sxs-lookup"><span data-stu-id="f272f-138">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="f272f-139">Exemple 6 : créer une fonction qui supprime toutes les sessions dans la session active</span><span class="sxs-lookup"><span data-stu-id="f272f-139">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="f272f-140">Cette fonction supprime toutes les **sessions PSSession** de la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-140">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="f272f-141">Après avoir ajouté cette fonction à votre profil PowerShell, pour supprimer toutes les sessions, tapez `EndPSS` .</span><span class="sxs-lookup"><span data-stu-id="f272f-141">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="f272f-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f272f-142">PARAMETERS</span></span>

### <span data-ttu-id="f272f-143">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f272f-143">-ComputerName</span></span>

<span data-ttu-id="f272f-144">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f272f-144">Specifies an array of names of computers.</span></span>
<span data-ttu-id="f272f-145">Cette applet de commande ferme les **sessions PSSession** connectés aux ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-145">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="f272f-146">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f272f-146">Wildcard characters are permitted.</span></span>

<span data-ttu-id="f272f-147">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f272f-147">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="f272f-148">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="f272f-148">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

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

### <span data-ttu-id="f272f-149">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="f272f-149">-ContainerId</span></span>

<span data-ttu-id="f272f-150">Spécifie un tableau d’ID de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f272f-150">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="f272f-151">Cette applet de commande supprime les sessions pour chacun des conteneurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-151">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="f272f-152">Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="f272f-152">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="f272f-153">Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="f272f-153">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="f272f-154">-Id</span><span class="sxs-lookup"><span data-stu-id="f272f-154">-Id</span></span>

<span data-ttu-id="f272f-155">Spécifie un tableau d’ID de sessions.</span><span class="sxs-lookup"><span data-stu-id="f272f-155">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="f272f-156">Cette applet de commande ferme le *sessions PSSession* avec les ID spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-156">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="f272f-157">Tapez un ou plusieurs ID, en les séparant par des virgules, ou utilisez l’opérateur de plage (..) pour spécifier une plage d’ID.</span><span class="sxs-lookup"><span data-stu-id="f272f-157">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="f272f-158">Un ID est un entier qui identifie de façon unique la session **PSSession** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-158">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="f272f-159">Il est plus facile à mémoriser et à taper que *InstanceID* , mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-159">It is easier to remember and type than the *InstanceId* , but it is unique only in the current session.</span></span>
<span data-ttu-id="f272f-160">Pour Rechercher l’ID d’une **session PSSession** , exécutez l’applet de commande Get-PSSession sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="f272f-160">To find the ID of a **PSSession** , run the Get-PSSession cmdlet without parameters.</span></span>

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

### <span data-ttu-id="f272f-161">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f272f-161">-InstanceId</span></span>

<span data-ttu-id="f272f-162">Spécifie un tableau d’ID d’instance.</span><span class="sxs-lookup"><span data-stu-id="f272f-162">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="f272f-163">Cette applet de commande ferme les **sessions PSSession** qui ont les ID d’instance spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-163">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="f272f-164">L’ID d’instance est un GUID qui identifie de façon unique une session **PSSession** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-164">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="f272f-165">L’ID d’instance est unique, même si plusieurs sessions sont en cours d’exécution sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f272f-165">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="f272f-166">L’ID d’instance est stocké dans la propriété **InstanceID** de l’objet qui représente une **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f272f-166">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession** .</span></span>
<span data-ttu-id="f272f-167">Pour Rechercher l' **InstanceID** de **sessions PSSession** dans la session active, tapez `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="f272f-167">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

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

### <span data-ttu-id="f272f-168">-Name</span><span class="sxs-lookup"><span data-stu-id="f272f-168">-Name</span></span>

<span data-ttu-id="f272f-169">Spécifie un tableau de noms conviviaux de sessions.</span><span class="sxs-lookup"><span data-stu-id="f272f-169">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="f272f-170">Cette applet de commande ferme les **sessions PSSession** qui ont les noms conviviaux spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-170">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="f272f-171">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f272f-171">Wildcard characters are permitted.</span></span>

<span data-ttu-id="f272f-172">Étant donné que le nom convivial d’une **session PSSession** peut ne pas être unique, lorsque vous utilisez le paramètre *Name* , envisagez d’utiliser également le paramètre *WhatIf* ou *Confirm* dans la commande **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f272f-172">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

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

### <span data-ttu-id="f272f-173">-Session</span><span class="sxs-lookup"><span data-stu-id="f272f-173">-Session</span></span>

<span data-ttu-id="f272f-174">Spécifie les objets de session du **sessions PSSession** à fermer.</span><span class="sxs-lookup"><span data-stu-id="f272f-174">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="f272f-175">Entrez une variable qui contient **sessions PSSession** ou une commande qui crée ou obtient le **sessions PSSession** , tel qu’une commande New-PSSession ou la commande **obtenir-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f272f-175">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions** , such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="f272f-176">Vous pouvez également diriger un ou plusieurs objets de session vers **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f272f-176">You can also pipe one or more session objects to **Remove-PSSession** .</span></span>

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

### <span data-ttu-id="f272f-177">-VMId</span><span class="sxs-lookup"><span data-stu-id="f272f-177">-VMId</span></span>

<span data-ttu-id="f272f-178">Spécifie un tableau d’ID de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="f272f-178">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="f272f-179">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-179">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="f272f-180">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f272f-180">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="f272f-181">-VMName</span><span class="sxs-lookup"><span data-stu-id="f272f-181">-VMName</span></span>

<span data-ttu-id="f272f-182">Spécifie un tableau de noms d'ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="f272f-182">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="f272f-183">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f272f-183">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="f272f-184">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l’applet de commande **obtenir-VM** .</span><span class="sxs-lookup"><span data-stu-id="f272f-184">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

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

### <span data-ttu-id="f272f-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f272f-185">-Confirm</span></span>

<span data-ttu-id="f272f-186">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f272f-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f272f-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f272f-187">-WhatIf</span></span>

<span data-ttu-id="f272f-188">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f272f-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f272f-189">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="f272f-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f272f-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f272f-190">CommonParameters</span></span>

<span data-ttu-id="f272f-191">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f272f-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f272f-192">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f272f-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f272f-193">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f272f-193">INPUTS</span></span>

### <span data-ttu-id="f272f-194">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-194">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="f272f-195">Vous pouvez diriger un objet de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f272f-195">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="f272f-196">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f272f-196">OUTPUTS</span></span>

### <span data-ttu-id="f272f-197">Aucun</span><span class="sxs-lookup"><span data-stu-id="f272f-197">None</span></span>

<span data-ttu-id="f272f-198">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="f272f-198">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="f272f-199">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f272f-199">NOTES</span></span>

* <span data-ttu-id="f272f-200">Le paramètre *ID* est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f272f-200">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="f272f-201">Pour supprimer tous les **sessions PSSession** de la session active, tapez `Get-PSSession | Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f272f-201">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="f272f-202">Une **session PSSession** utilise une connexion permanente à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f272f-202">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="f272f-203">Créez une **session PSSession** pour exécuter une série de commandes qui partagent des données.</span><span class="sxs-lookup"><span data-stu-id="f272f-203">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="f272f-204">Pour plus d'informations, voir `Get-Help about_PSSessions`.</span><span class="sxs-lookup"><span data-stu-id="f272f-204">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="f272f-205">Les **sessions PSSession** sont spécifiques à la session active.</span><span class="sxs-lookup"><span data-stu-id="f272f-205">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="f272f-206">Lorsque vous terminez une session, les **sessions PSSession** que vous avez créés dans cette session sont fermés de force.</span><span class="sxs-lookup"><span data-stu-id="f272f-206">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="f272f-207">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f272f-207">RELATED LINKS</span></span>

[<span data-ttu-id="f272f-208">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-208">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="f272f-209">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-209">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="f272f-210">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-210">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="f272f-211">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-211">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="f272f-212">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-212">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="f272f-213">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f272f-213">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f272f-214">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-214">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="f272f-215">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="f272f-215">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="f272f-216">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f272f-216">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="f272f-217">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f272f-217">about_Remote</span></span>](About/about_Remote.md)
