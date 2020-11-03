---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 9257c0a1829cc9cc85029f7c6fdc8e61b0ed7e56
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205370"
---
# <span data-ttu-id="d2c5a-103">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="d2c5a-103">New-PSTransportOption</span></span>

## <span data-ttu-id="d2c5a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d2c5a-104">SYNOPSIS</span></span>

<span data-ttu-id="d2c5a-105">Crée un objet qui contient des options avancées pour une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-105">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="d2c5a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2c5a-106">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="d2c5a-107">Description</span><span class="sxs-lookup"><span data-stu-id="d2c5a-107">DESCRIPTION</span></span>

<span data-ttu-id="d2c5a-108">L'applet de commande **New-PSTransportOption** crée un objet qui contient des options de transport pour les configurations de sessions.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-108">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="d2c5a-109">Vous pouvez utiliser l’objet comme valeur du paramètre *TransportOption* des applets de commande qui créent ou modifient une configuration de session, comme les applets de commande Register-PSSessionConfiguration et Set-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-109">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="d2c5a-110">Vous pouvez également modifier les paramètres d'option de transport en modifiant les valeurs des propriétés de configuration de session dans le lecteur WSMan:.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-110">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="d2c5a-111">Pour plus d’informations, consultez fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-111">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="d2c5a-112">Les options de configuration de session représentent les valeurs de session définies côté serveur ou la fin de la réception d’une connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-112">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="d2c5a-113">L’extrémité côté client ou d’envoi de la connexion peut définir des valeurs d’option de session lors de la création de la session, ou lorsque le client se déconnecte de la session ou se reconnecte.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-113">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="d2c5a-114">Sauf indication contraire, en cas de conflit des valeurs des paramètres, les valeurs côté client sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-114">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="d2c5a-115">Toutefois, les valeurs côté client ne peuvent pas dépasser les valeurs maximales et les quotas définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-115">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="d2c5a-116">Sans paramètres, **New-PSTransportOption** génère un objet d’option de transport qui a des valeurs NULL pour toutes les options.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-116">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="d2c5a-117">Si vous omettez un paramètre, l'objet a une valeur null pour la propriété représentée par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-117">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="d2c5a-118">Une valeur NULL n’affecte pas la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-118">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="d2c5a-119">Pour plus d’informations sur les options de session, consultez New-PSSessionOption.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-119">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="d2c5a-120">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-120">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="d2c5a-121">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="d2c5a-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d2c5a-122">EXAMPLES</span></span>

### <span data-ttu-id="d2c5a-123">Exemple 1 : générer une option de transport par défaut</span><span class="sxs-lookup"><span data-stu-id="d2c5a-123">Example 1: Generate a default transport option</span></span>

```
PS C:\> New-PSTransportOption
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

<span data-ttu-id="d2c5a-124">Cette commande exécute la commande **New-PSTransportOption** sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-124">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="d2c5a-125">La sortie indique que l’applet de commande génère un objet d’option de transport qui a des valeurs NULL pour toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-125">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="d2c5a-126">Exemple 2 : accéder aux options de configuration de session</span><span class="sxs-lookup"><span data-stu-id="d2c5a-126">Example 2: Get session configuration options</span></span>

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable. The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.
PS C:\> $t = New-PSTransportOption -MaxSessions 40

The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Register-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list. The output shows that the value of the **MaxShells** property of the session configuration is 40.
PS C:\> Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
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
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="d2c5a-127">Cet exemple montre comment utiliser un objet d’options de transport pour définir des options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-127">This example shows how to use a transport options object to set session configuration options.</span></span>

### <span data-ttu-id="d2c5a-128">Exemple 3 : définition d’une option de transport</span><span class="sxs-lookup"><span data-stu-id="d2c5a-128">Example 3: Setting a transport option</span></span>

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport option object. The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds). The command saves the transport objects object in the $t variable.
PS C:\> $t = New-PSTransportOption -IdleTimeoutSec 3600

The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Set-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer. The command uses the **ConfigurationName** property to specify the ITTasks session configuration. The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session. If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.
PS C:\> $s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks

The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list. The output shows that the session has an idle time-out of one hour (360,000 milliseconds).
PS C:\> $s | Format-List -Property *
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

<span data-ttu-id="d2c5a-129">Cette commande montre l'effet de la définition d'une option de transport dans une configuration de session sur les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-129">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

## <span data-ttu-id="d2c5a-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2c5a-130">PARAMETERS</span></span>

### <span data-ttu-id="d2c5a-131">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="d2c5a-131">-IdleTimeoutSec</span></span>

<span data-ttu-id="d2c5a-132">Détermine la durée pendant laquelle chaque session reste ouverte si l’ordinateur distant ne reçoit pas de communication de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-132">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="d2c5a-133">Cela comprend le signal de pulsation.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-133">This includes the heartbeat signal.</span></span>
<span data-ttu-id="d2c5a-134">Quand le délai expire, la session se ferme.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-134">When the interval expires, the session closes.</span></span>

<span data-ttu-id="d2c5a-135">La valeur du délai d’inactivité revêt une importance particulière lorsque l’utilisateur a l’intention de se déconnecter et de se reconnecter à une session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-135">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="d2c5a-136">L'utilisateur ne peut se reconnecter que si la session n'a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-136">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="d2c5a-137">Le paramètre *IdleTimeoutSec* correspond à la propriété **IdleTimeoutMs** d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-137">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="d2c5a-138">Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-138">Enter a value in seconds.</span></span>
<span data-ttu-id="d2c5a-139">La valeur par défaut est 7 200 (2 heures).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-139">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="d2c5a-140">La valeur minimale est 60 (1 minute).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-140">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="d2c5a-141">La valeur maximale est la valeur de la propriété **IdleTimeout** des objets Shell dans la configuration WSMan ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-141">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="d2c5a-142">La valeur par défaut est égale à 7 200 000 millisecondes (2 heures).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-142">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="d2c5a-143">Si une valeur de délai d’inactivité est définie dans les options de session et dans la configuration de session, la valeur définie dans les options de session est prioritaire, mais elle ne peut pas dépasser la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-143">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="d2c5a-144">Pour définir la valeur de la propriété **MaxIdleTimeoutMs** , utilisez le paramètre *MaxIdleTimeoutSec* .</span><span class="sxs-lookup"><span data-stu-id="d2c5a-144">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-145">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="d2c5a-145">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="d2c5a-146">Limite le nombre de commandes qui peuvent s’exécuter simultanément dans chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-146">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="d2c5a-147">La valeur par défaut est 1000.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-147">The default value is 1000.</span></span>

<span data-ttu-id="d2c5a-148">Le paramètre *MaxConcurrentCommandsPerSession* correspond à la propriété **MaxConcurrentCommandsPerShell** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-148">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-149">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="d2c5a-149">-MaxConcurrentUsers</span></span>

<span data-ttu-id="d2c5a-150">Limite le nombre d’utilisateurs qui peuvent exécuter des commandes simultanément dans chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-150">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="d2c5a-151">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-151">The default value is 5.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-152">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="d2c5a-152">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="d2c5a-153">Limite le délai d’inactivité défini pour chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-153">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="d2c5a-154">La valeur par défaut est \[ int \] :: MaxValue (~ 25 jours).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-154">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="d2c5a-155">La valeur du délai d’inactivité revêt une importance particulière lorsque l’utilisateur a l’intention de se déconnecter et de se reconnecter à une session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-155">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="d2c5a-156">L'utilisateur ne peut se reconnecter que si la session n'a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-156">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="d2c5a-157">Le paramètre *MaxIdleTimeoutSec* correspond à la propriété **MaxIdleTimeoutMs** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-157">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-158">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="d2c5a-158">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="d2c5a-159">Limite la mémoire utilisée par chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-159">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="d2c5a-160">Entrez une valeur en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-160">Enter a value in megabytes.</span></span>
<span data-ttu-id="d2c5a-161">La valeur par défaut est 1 024 mégaoctets (1 Go).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-161">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="d2c5a-162">Le paramètre *MaxMemoryPerSessionMB* correspond à la propriété **MaxMemoryPerShellMB** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-162">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-163">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="d2c5a-163">-MaxProcessesPerSession</span></span>

<span data-ttu-id="d2c5a-164">Limite le nombre de processus exécutés dans chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-164">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="d2c5a-165">La valeur par défaut est 15.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-165">The default value is 15.</span></span>

<span data-ttu-id="d2c5a-166">Le paramètre *MaxProcessesPerSession* correspond à la propriété **MaxProcessesPerShell** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-166">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-167">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="d2c5a-167">-MaxSessions</span></span>

<span data-ttu-id="d2c5a-168">Limite le nombre de sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-168">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="d2c5a-169">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-169">The default value is 25.</span></span>

<span data-ttu-id="d2c5a-170">Le paramètre *maxsessions* correspond à la propriété **MaxShells** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-170">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-171">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="d2c5a-171">-MaxSessionsPerUser</span></span>

<span data-ttu-id="d2c5a-172">Limite le nombre de sessions qui utilisent la configuration de session et s'exécutent avec les informations d'identification d'un utilisateur donné à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-172">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="d2c5a-173">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-173">The default value is 25.</span></span>

<span data-ttu-id="d2c5a-174">Lorsque vous spécifiez cette valeur, pensez que de nombreux utilisateurs peuvent utiliser les informations d’identification d’un utilisateur exécuter en tant qu’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-174">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="d2c5a-175">Le paramètre *MaxSessionsPerUser* correspond à la propriété **MaxShellsPerUser** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-175">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-176">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="d2c5a-176">-OutputBufferingMode</span></span>

<span data-ttu-id="d2c5a-177">Détermine comment la sortie de la commande est gérée dans des sessions déconnectées quand la mémoire tampon de sortie est pleine.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-177">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="d2c5a-178">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d2c5a-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d2c5a-179">Bloquer.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-179">Block.</span></span>
<span data-ttu-id="d2c5a-180">Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-180">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="d2c5a-181">Drop.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-181">Drop.</span></span>
<span data-ttu-id="d2c5a-182">Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-182">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="d2c5a-183">Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-183">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="d2c5a-184">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-184">None.</span></span>
<span data-ttu-id="d2c5a-185">Aucun mode de mise en mémoire tampon de sortie n'est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-185">No output buffering mode is specified.</span></span>

<span data-ttu-id="d2c5a-186">La valeur par défaut de la propriété **OutputBufferingMode** des sessions est Block.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-186">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-187">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="d2c5a-187">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="d2c5a-188">Limite le délai d’attente pour chaque processus hôte à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-188">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="d2c5a-189">La valeur par défaut, 0, signifie qu’il n’y a aucune valeur de délai d’attente pour le processus.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-189">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="d2c5a-190">D’autres configurations de sessions ont des valeurs de délai d’attente par processus.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-190">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="d2c5a-191">Par exemple, la configuration de session **Microsoft. PowerShell. Workflow** a une valeur de délai d’attente par processus de 28800 secondes (8 heures).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-191">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c5a-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2c5a-192">CommonParameters</span></span>
<span data-ttu-id="d2c5a-193">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2c5a-194">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d2c5a-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d2c5a-195">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d2c5a-195">INPUTS</span></span>

### <span data-ttu-id="d2c5a-196">Aucun</span><span class="sxs-lookup"><span data-stu-id="d2c5a-196">None</span></span>

<span data-ttu-id="d2c5a-197">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-197">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d2c5a-198">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d2c5a-198">OUTPUTS</span></span>

### <span data-ttu-id="d2c5a-199">Microsoft. PowerShell. Commands. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="d2c5a-199">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="d2c5a-200">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d2c5a-200">NOTES</span></span>

- <span data-ttu-id="d2c5a-201">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-201">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="d2c5a-202">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d2c5a-202">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="d2c5a-203">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d2c5a-203">RELATED LINKS</span></span>

[<span data-ttu-id="d2c5a-204">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d2c5a-204">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="d2c5a-205">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="d2c5a-205">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="d2c5a-206">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2c5a-206">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="d2c5a-207">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2c5a-207">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)
