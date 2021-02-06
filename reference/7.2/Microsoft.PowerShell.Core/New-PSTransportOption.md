---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: fa19ee7d1856eee91a6b1d6a8352017457031202
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596731"
---
# <span data-ttu-id="16a38-102">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="16a38-102">New-PSTransportOption</span></span>

## <span data-ttu-id="16a38-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="16a38-103">SYNOPSIS</span></span>
<span data-ttu-id="16a38-104">Crée un objet qui contient des options avancées pour une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-104">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="16a38-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="16a38-105">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="16a38-106">Description</span><span class="sxs-lookup"><span data-stu-id="16a38-106">DESCRIPTION</span></span>

<span data-ttu-id="16a38-107">L'applet de commande **New-PSTransportOption** crée un objet qui contient des options de transport pour les configurations de sessions.</span><span class="sxs-lookup"><span data-stu-id="16a38-107">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="16a38-108">Vous pouvez utiliser l’objet comme valeur du paramètre *TransportOption* des applets de commande qui créent ou modifient une configuration de session, comme les applets de commande Register-PSSessionConfiguration et Set-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="16a38-108">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="16a38-109">Vous pouvez également modifier les paramètres d'option de transport en modifiant les valeurs des propriétés de configuration de session dans le lecteur WSMan:.</span><span class="sxs-lookup"><span data-stu-id="16a38-109">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="16a38-110">Pour plus d’informations, consultez fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="16a38-110">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="16a38-111">Les options de configuration de session représentent les valeurs de session définies côté serveur ou la fin de la réception d’une connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="16a38-111">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="16a38-112">L’extrémité côté client ou d’envoi de la connexion peut définir des valeurs d’option de session lors de la création de la session, ou lorsque le client se déconnecte de la session ou se reconnecte.</span><span class="sxs-lookup"><span data-stu-id="16a38-112">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="16a38-113">Sauf indication contraire, en cas de conflit des valeurs des paramètres, les valeurs côté client sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="16a38-113">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="16a38-114">Toutefois, les valeurs côté client ne peuvent pas dépasser les valeurs maximales et les quotas définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-114">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="16a38-115">Sans paramètres, **New-PSTransportOption** génère un objet d’option de transport qui a des valeurs NULL pour toutes les options.</span><span class="sxs-lookup"><span data-stu-id="16a38-115">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="16a38-116">Si vous omettez un paramètre, l'objet a une valeur null pour la propriété représentée par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="16a38-116">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="16a38-117">Une valeur NULL n’affecte pas la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-117">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="16a38-118">Pour plus d’informations sur les options de session, consultez New-PSSessionOption.</span><span class="sxs-lookup"><span data-stu-id="16a38-118">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="16a38-119">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="16a38-119">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="16a38-120">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="16a38-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="16a38-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="16a38-121">EXAMPLES</span></span>

### <span data-ttu-id="16a38-122">Exemple 1 : générer une option de transport par défaut</span><span class="sxs-lookup"><span data-stu-id="16a38-122">Example 1: Generate a default transport option</span></span>

```powershell
New-PSTransportOption
```

```Output
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

<span data-ttu-id="16a38-123">Cette commande exécute la commande **New-PSTransportOption** sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="16a38-123">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="16a38-124">La sortie indique que l’applet de commande génère un objet d’option de transport qui a des valeurs NULL pour toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="16a38-124">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="16a38-125">Exemple 2 : accéder aux options de configuration de session</span><span class="sxs-lookup"><span data-stu-id="16a38-125">Example 2: Get session configuration options</span></span>

<span data-ttu-id="16a38-126">Cet exemple montre comment utiliser un objet d’options de transport pour définir des options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-126">This example shows how to use a transport options object to set session configuration options.</span></span>

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
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

<span data-ttu-id="16a38-127">La première commande utilise l'applet de commande **New-PSTransportOption** pour créer un objet d'options de transport, qu'elle enregistre dans la variable $t.</span><span class="sxs-lookup"><span data-stu-id="16a38-127">The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable.</span></span> <span data-ttu-id="16a38-128">La commande utilise le paramètre *MaxSessions* pour augmenter le nombre maximal de sessions à 40.</span><span class="sxs-lookup"><span data-stu-id="16a38-128">The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.</span></span>

<span data-ttu-id="16a38-129">La deuxième commande utilise l'applet de commande **Register-PSSessionConfiguration** pour créer la configuration de session ITTasks.</span><span class="sxs-lookup"><span data-stu-id="16a38-129">The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration.</span></span> <span data-ttu-id="16a38-130">La commande utilise le paramètre *TransportOption* pour spécifier l'objet d'options de transport dans la variable $t.</span><span class="sxs-lookup"><span data-stu-id="16a38-130">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="16a38-131">La troisième commande utilise l’applet de commande Get-PSSessionConfiguration pour obtenir les configurations de session ITTasks et l’applet de commande Format-List pour afficher toutes les propriétés de l’objet de configuration de session dans une liste.</span><span class="sxs-lookup"><span data-stu-id="16a38-131">The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list.</span></span> <span data-ttu-id="16a38-132">La sortie indique que la valeur de la propriété **MaxShells** de la configuration de session est 40.</span><span class="sxs-lookup"><span data-stu-id="16a38-132">The output shows that the value of the **MaxShells** property of the session configuration is 40.</span></span>

### <span data-ttu-id="16a38-133">Exemple 3 : définition d’une option de transport</span><span class="sxs-lookup"><span data-stu-id="16a38-133">Example 3: Setting a transport option</span></span>

<span data-ttu-id="16a38-134">Cette commande montre l'effet de la définition d'une option de transport dans une configuration de session sur les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-134">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
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

<span data-ttu-id="16a38-135">La première commande utilise l'applet de commande **New-PSTransportOption** pour créer un objet d'options de transport.</span><span class="sxs-lookup"><span data-stu-id="16a38-135">The first command uses the **New-PSTransportOption** cmdlet to create a transport option object.</span></span> <span data-ttu-id="16a38-136">La commande utilise le paramètre *IdleTimeoutSec* pour affecter une heure (3 600 secondes) à la valeur de propriété **IdleTimeoutSec** de l'objet.</span><span class="sxs-lookup"><span data-stu-id="16a38-136">The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds).</span></span> <span data-ttu-id="16a38-137">La commande enregistre l'objet d'options de transport dans la variable $t.</span><span class="sxs-lookup"><span data-stu-id="16a38-137">The command saves the transport objects object in the $t variable.</span></span>

<span data-ttu-id="16a38-138">La deuxième commande utilise l’applet de commande Set-PSSessionConfiguration pour modifier les options de transport de la configuration de session ITTasks.</span><span class="sxs-lookup"><span data-stu-id="16a38-138">The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration.</span></span> <span data-ttu-id="16a38-139">La commande utilise le paramètre *TransportOption* pour spécifier l'objet d'options de transport dans la variable $t.</span><span class="sxs-lookup"><span data-stu-id="16a38-139">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="16a38-140">La troisième commande utilise l’applet de commande New-PSSession pour créer la session MyITTasks sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="16a38-140">The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer.</span></span> <span data-ttu-id="16a38-141">La commande utilise la propriété **ConfigurationName** pour spécifier la configuration de session ITTasks.</span><span class="sxs-lookup"><span data-stu-id="16a38-141">The command uses the **ConfigurationName** property to specify the ITTasks session configuration.</span></span> <span data-ttu-id="16a38-142">La commande enregistre la session dans la variable $s. Notez que la commande n’utilise pas le paramètre *SessionOption* de **New-PSSession** pour définir un délai d’inactivité personnalisé pour la session.</span><span class="sxs-lookup"><span data-stu-id="16a38-142">The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session.</span></span> <span data-ttu-id="16a38-143">Si c’est le cas, la valeur du délai d’inactivité définie dans l’option de session est prioritaire sur le délai d’inactivité défini dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-143">If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.</span></span>

<span data-ttu-id="16a38-144">La quatrième commande utilise l’applet de commande Format-List pour afficher toutes les propriétés de la session dans la variable $s dans une liste.</span><span class="sxs-lookup"><span data-stu-id="16a38-144">The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list.</span></span> <span data-ttu-id="16a38-145">La sortie indique que la session a un délai d’inactivité d’une heure (360 000 millisecondes).</span><span class="sxs-lookup"><span data-stu-id="16a38-145">The output shows that the session has an idle time-out of one hour (360,000 milliseconds).</span></span>

## <span data-ttu-id="16a38-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="16a38-146">PARAMETERS</span></span>

### <span data-ttu-id="16a38-147">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="16a38-147">-IdleTimeoutSec</span></span>

<span data-ttu-id="16a38-148">Détermine la durée pendant laquelle chaque session reste ouverte si l’ordinateur distant ne reçoit pas de communication de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="16a38-148">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="16a38-149">Cela comprend le signal de pulsation.</span><span class="sxs-lookup"><span data-stu-id="16a38-149">This includes the heartbeat signal.</span></span>
<span data-ttu-id="16a38-150">Quand le délai expire, la session se ferme.</span><span class="sxs-lookup"><span data-stu-id="16a38-150">When the interval expires, the session closes.</span></span>

<span data-ttu-id="16a38-151">La valeur du délai d’inactivité revêt une importance particulière lorsque l’utilisateur a l’intention de se déconnecter et de se reconnecter à une session.</span><span class="sxs-lookup"><span data-stu-id="16a38-151">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="16a38-152">L'utilisateur ne peut se reconnecter que si la session n'a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="16a38-152">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="16a38-153">Le paramètre *IdleTimeoutSec* correspond à la propriété **IdleTimeoutMs** d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-153">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="16a38-154">Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="16a38-154">Enter a value in seconds.</span></span>
<span data-ttu-id="16a38-155">La valeur par défaut est 7 200 (2 heures).</span><span class="sxs-lookup"><span data-stu-id="16a38-155">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="16a38-156">La valeur minimale est 60 (1 minute).</span><span class="sxs-lookup"><span data-stu-id="16a38-156">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="16a38-157">La valeur maximale est la valeur de la propriété **IdleTimeout** des objets Shell dans la configuration WSMan ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).</span><span class="sxs-lookup"><span data-stu-id="16a38-157">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="16a38-158">La valeur par défaut est égale à 7 200 000 millisecondes (2 heures).</span><span class="sxs-lookup"><span data-stu-id="16a38-158">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="16a38-159">Si une valeur de délai d’inactivité est définie dans les options de session et dans la configuration de session, la valeur définie dans les options de session est prioritaire, mais elle ne peut pas dépasser la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-159">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="16a38-160">Pour définir la valeur de la propriété **MaxIdleTimeoutMs**, utilisez le paramètre *MaxIdleTimeoutSec*.</span><span class="sxs-lookup"><span data-stu-id="16a38-160">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

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

### <span data-ttu-id="16a38-161">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="16a38-161">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="16a38-162">Limite le nombre de commandes qui peuvent s’exécuter simultanément dans chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-162">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="16a38-163">La valeur par défaut est 1000.</span><span class="sxs-lookup"><span data-stu-id="16a38-163">The default value is 1000.</span></span>

<span data-ttu-id="16a38-164">Le paramètre *MaxConcurrentCommandsPerSession* correspond à la propriété **MaxConcurrentCommandsPerShell** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-164">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

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

### <span data-ttu-id="16a38-165">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="16a38-165">-MaxConcurrentUsers</span></span>

<span data-ttu-id="16a38-166">Limite le nombre d’utilisateurs qui peuvent exécuter des commandes simultanément dans chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-166">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="16a38-167">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="16a38-167">The default value is 5.</span></span>

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

### <span data-ttu-id="16a38-168">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="16a38-168">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="16a38-169">Limite le délai d’inactivité défini pour chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-169">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="16a38-170">La valeur par défaut est \[ int \] :: MaxValue (~ 25 jours).</span><span class="sxs-lookup"><span data-stu-id="16a38-170">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="16a38-171">La valeur du délai d’inactivité revêt une importance particulière lorsque l’utilisateur a l’intention de se déconnecter et de se reconnecter à une session.</span><span class="sxs-lookup"><span data-stu-id="16a38-171">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="16a38-172">L'utilisateur ne peut se reconnecter que si la session n'a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="16a38-172">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="16a38-173">Le paramètre *MaxIdleTimeoutSec* correspond à la propriété **MaxIdleTimeoutMs** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-173">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

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

### <span data-ttu-id="16a38-174">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="16a38-174">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="16a38-175">Limite la mémoire utilisée par chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-175">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="16a38-176">Entrez une valeur en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="16a38-176">Enter a value in megabytes.</span></span>
<span data-ttu-id="16a38-177">La valeur par défaut est 1 024 mégaoctets (1 Go).</span><span class="sxs-lookup"><span data-stu-id="16a38-177">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="16a38-178">Le paramètre *MaxMemoryPerSessionMB* correspond à la propriété **MaxMemoryPerShellMB** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-178">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

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

### <span data-ttu-id="16a38-179">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="16a38-179">-MaxProcessesPerSession</span></span>

<span data-ttu-id="16a38-180">Limite le nombre de processus exécutés dans chaque session à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-180">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="16a38-181">La valeur par défaut est 15.</span><span class="sxs-lookup"><span data-stu-id="16a38-181">The default value is 15.</span></span>

<span data-ttu-id="16a38-182">Le paramètre *MaxProcessesPerSession* correspond à la propriété **MaxProcessesPerShell** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-182">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

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

### <span data-ttu-id="16a38-183">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="16a38-183">-MaxSessions</span></span>

<span data-ttu-id="16a38-184">Limite le nombre de sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-184">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="16a38-185">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="16a38-185">The default value is 25.</span></span>

<span data-ttu-id="16a38-186">Le paramètre *maxsessions* correspond à la propriété **MaxShells** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-186">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

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

### <span data-ttu-id="16a38-187">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="16a38-187">-MaxSessionsPerUser</span></span>

<span data-ttu-id="16a38-188">Limite le nombre de sessions qui utilisent la configuration de session et s'exécutent avec les informations d'identification d'un utilisateur donné à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-188">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="16a38-189">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="16a38-189">The default value is 25.</span></span>

<span data-ttu-id="16a38-190">Lorsque vous spécifiez cette valeur, pensez que de nombreux utilisateurs peuvent utiliser les informations d’identification d’un utilisateur exécuter en tant qu’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="16a38-190">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="16a38-191">Le paramètre *MaxSessionsPerUser* correspond à la propriété **MaxShellsPerUser** d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="16a38-191">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

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

### <span data-ttu-id="16a38-192">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="16a38-192">-OutputBufferingMode</span></span>

<span data-ttu-id="16a38-193">Détermine comment la sortie de la commande est gérée dans des sessions déconnectées quand la mémoire tampon de sortie est pleine.</span><span class="sxs-lookup"><span data-stu-id="16a38-193">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="16a38-194">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="16a38-194">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="16a38-195">Bloquer.</span><span class="sxs-lookup"><span data-stu-id="16a38-195">Block.</span></span>
<span data-ttu-id="16a38-196">Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée.</span><span class="sxs-lookup"><span data-stu-id="16a38-196">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="16a38-197">Drop.</span><span class="sxs-lookup"><span data-stu-id="16a38-197">Drop.</span></span>
<span data-ttu-id="16a38-198">Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="16a38-198">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="16a38-199">Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.</span><span class="sxs-lookup"><span data-stu-id="16a38-199">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="16a38-200">Aucun.</span><span class="sxs-lookup"><span data-stu-id="16a38-200">None.</span></span>
<span data-ttu-id="16a38-201">Aucun mode de mise en mémoire tampon de sortie n'est spécifié.</span><span class="sxs-lookup"><span data-stu-id="16a38-201">No output buffering mode is specified.</span></span>

<span data-ttu-id="16a38-202">La valeur par défaut de la propriété **OutputBufferingMode** des sessions est Block.</span><span class="sxs-lookup"><span data-stu-id="16a38-202">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

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

### <span data-ttu-id="16a38-203">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="16a38-203">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="16a38-204">Limite le délai d’attente pour chaque processus hôte à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16a38-204">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="16a38-205">La valeur par défaut, 0, signifie qu’il n’y a aucune valeur de délai d’attente pour le processus.</span><span class="sxs-lookup"><span data-stu-id="16a38-205">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="16a38-206">D’autres configurations de sessions ont des valeurs de délai d’attente par processus.</span><span class="sxs-lookup"><span data-stu-id="16a38-206">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="16a38-207">Par exemple, la configuration de session **Microsoft. PowerShell. Workflow** a une valeur de délai d’attente par processus de 28800 secondes (8 heures).</span><span class="sxs-lookup"><span data-stu-id="16a38-207">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

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

### <span data-ttu-id="16a38-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="16a38-208">CommonParameters</span></span>

<span data-ttu-id="16a38-209">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="16a38-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="16a38-210">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="16a38-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="16a38-211">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="16a38-211">INPUTS</span></span>

### <span data-ttu-id="16a38-212">None</span><span class="sxs-lookup"><span data-stu-id="16a38-212">None</span></span>

<span data-ttu-id="16a38-213">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16a38-213">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="16a38-214">SORTIES</span><span class="sxs-lookup"><span data-stu-id="16a38-214">OUTPUTS</span></span>

### <span data-ttu-id="16a38-215">Microsoft. PowerShell. Commands. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="16a38-215">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="16a38-216">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="16a38-216">NOTES</span></span>

- <span data-ttu-id="16a38-217">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="16a38-217">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="16a38-218">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="16a38-218">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="16a38-219">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="16a38-219">RELATED LINKS</span></span>

[<span data-ttu-id="16a38-220">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="16a38-220">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="16a38-221">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="16a38-221">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="16a38-222">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="16a38-222">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="16a38-223">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="16a38-223">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

