---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: 566091a53941cd122a10aa2bcb45cddfb1f40cc4
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388618"
---
# <span data-ttu-id="76733-103">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="76733-103">New-PSSessionOption</span></span>

## <span data-ttu-id="76733-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="76733-104">SYNOPSIS</span></span>
<span data-ttu-id="76733-105">Crée un objet qui contient des options avancées pour une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="76733-105">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="76733-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="76733-106">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="76733-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="76733-107">DESCRIPTION</span></span>

<span data-ttu-id="76733-108">L' `New-PSSessionOption` applet de commande crée un objet qui contient des options avancées pour une session gérée par l’utilisateur ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="76733-108">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session ( **PSSession** ).</span></span> <span data-ttu-id="76733-109">Vous pouvez utiliser l’objet comme valeur du paramètre **SessionOption** des applets de commande qui créent une **session PSSession** , comme `New-PSSession` , `Enter-PSSession` et `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="76733-109">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession** , such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="76733-110">Sans paramètres, `New-PSSessionOption` génère un objet qui contient les valeurs par défaut pour toutes les options.</span><span class="sxs-lookup"><span data-stu-id="76733-110">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="76733-111">Comme toutes les propriétés peuvent être modifiées, vous pouvez utiliser l'objet résultant comme modèle et créer des objets d'option standard pour votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="76733-111">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="76733-112">Vous pouvez également enregistrer un objet d’option de session dans la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="76733-112">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="76733-113">Les valeurs de cette variable établissent de nouvelles valeurs par défaut pour les options de session.</span><span class="sxs-lookup"><span data-stu-id="76733-113">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="76733-114">Elles sont effectives quand aucune option de session n'est définie pour la session, et elles sont prioritaires sur les options définies dans la configuration de session. Vous pouvez cependant les remplacer en spécifiant des options de session ou un objet d'option de session dans une applet de commande qui crée une session.</span><span class="sxs-lookup"><span data-stu-id="76733-114">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="76733-115">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="76733-115">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="76733-116">Quand vous utilisez un objet d'option de session dans une applet de commande qui crée une session, les valeurs d'option de session sont prioritaires sur les valeurs par défaut pour l'ensemble des sessions dans la variable de préférence $PSSessionOption et dans la configuration de la session.</span><span class="sxs-lookup"><span data-stu-id="76733-116">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="76733-117">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="76733-117">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="76733-118">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="76733-118">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="76733-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="76733-119">EXAMPLES</span></span>

### <span data-ttu-id="76733-120">Exemple 1 : créer une option de session par défaut</span><span class="sxs-lookup"><span data-stu-id="76733-120">Example 1: Create a default session option</span></span>

<span data-ttu-id="76733-121">Cette commande crée un objet d’option de session avec toutes les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="76733-121">This command creates a session option object that has all of the default values.</span></span>

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### <span data-ttu-id="76733-122">Exemple 2 : configurer une session à l’aide d’un objet d’option de session</span><span class="sxs-lookup"><span data-stu-id="76733-122">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="76733-123">Cet exemple montre comment utiliser un objet d'option de session pour configurer une session.</span><span class="sxs-lookup"><span data-stu-id="76733-123">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="76733-124">La première commande crée un objet d’option de session et l’enregistre dans la valeur de la `$pso` variable.</span><span class="sxs-lookup"><span data-stu-id="76733-124">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="76733-125">La deuxième commande utilise l' `New-PSSession` applet de commande pour créer une session sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="76733-125">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="76733-126">La commande utilise l’objet d’option de session dans la valeur de la `$pso` variable comme valeur du paramètre **SessionOption** de la commande.</span><span class="sxs-lookup"><span data-stu-id="76733-126">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="76733-127">Exemple 3 : démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="76733-127">Example 3: Start an interactive session</span></span>

<span data-ttu-id="76733-128">Cette commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="76733-128">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="76733-129">La valeur du paramètre **SessionOption** est une `New-PSSessionOption` commande qui a les paramètres **nocryption** et **NoCompression** .</span><span class="sxs-lookup"><span data-stu-id="76733-129">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="76733-130">La `New-PSSessionOption` commande est placée entre parenthèses pour vérifier qu’elle s’exécute avant la `Enter-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="76733-130">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="76733-131">Exemple 4 : modifier un objet d’option de session</span><span class="sxs-lookup"><span data-stu-id="76733-131">Example 4: Modify a session option object</span></span>

<span data-ttu-id="76733-132">Cet exemple montre que vous pouvez modifier l’objet d’option de session.</span><span class="sxs-lookup"><span data-stu-id="76733-132">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="76733-133">Toutes les propriétés ont des valeurs en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="76733-133">All properties have read/write values.</span></span>

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

<span data-ttu-id="76733-134">Utilisez cette méthode pour créer un objet de session standard pour votre entreprise, puis créez-en des versions personnalisées pour des utilisations particulières.</span><span class="sxs-lookup"><span data-stu-id="76733-134">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="76733-135">Exemple 5 : créer une variable de préférence</span><span class="sxs-lookup"><span data-stu-id="76733-135">Example 5: Create a preference variable</span></span>

<span data-ttu-id="76733-136">Cette commande crée une `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="76733-136">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="76733-137">Lorsque la `$PSSessionOption` variable de préférence se produit dans la session, elle établit des valeurs par défaut pour les options dans les sessions créées à l’aide des `New-PSSession` applets de commande, `Enter-PSSession` et `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="76733-137">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="76733-138">Pour rendre la `$PSSessionOption` variable disponible dans toutes les sessions, ajoutez-la à votre session PowerShell et à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76733-138">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="76733-139">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="76733-139">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="76733-140">Pour plus d'informations sur les profils, consultez [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="76733-140">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="76733-141">Exemple 6 : répondre aux exigences d’une configuration de session à distance</span><span class="sxs-lookup"><span data-stu-id="76733-141">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="76733-142">Cet exemple montre comment utiliser un objet **SessionOption** pour satisfaire aux spécifications requises pour la configuration d'une session à distance.</span><span class="sxs-lookup"><span data-stu-id="76733-142">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="76733-143">La première commande utilise l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session qui a la propriété **SkipCNCheck** .</span><span class="sxs-lookup"><span data-stu-id="76733-143">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="76733-144">La commande enregistre l’objet de session résultant dans la `$skipCN` variable.</span><span class="sxs-lookup"><span data-stu-id="76733-144">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="76733-145">La deuxième commande utilise l' `New-PSSession` applet de commande pour créer une nouvelle session sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="76733-145">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="76733-146">La `$skipCN` variable check est utilisée dans la valeur du paramètre **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="76733-146">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="76733-147">Étant donné que l’ordinateur est identifié par son adresse IP, la valeur du paramètre **ComputerName** ne correspond à aucun des noms communs du certificat utilisé pour protocole SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="76733-147">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="76733-148">Par conséquent, l'option **SkipCNCheck** est requise.</span><span class="sxs-lookup"><span data-stu-id="76733-148">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="76733-149">Exemple 7 : rendre les arguments disponibles pour une session à distance</span><span class="sxs-lookup"><span data-stu-id="76733-149">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="76733-150">Cet exemple montre comment utiliser le paramètre **ApplicationArguments** de l' `New-PSSessionOption` applet de commande pour rendre des données supplémentaires disponibles pour la session à distance.</span><span class="sxs-lookup"><span data-stu-id="76733-150">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

<span data-ttu-id="76733-151">La première commande crée une table de hachage avec deux clés, **Team** et **use**.</span><span class="sxs-lookup"><span data-stu-id="76733-151">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="76733-152">La commande enregistre la table de hachage dans la `$team` variable.</span><span class="sxs-lookup"><span data-stu-id="76733-152">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="76733-153">Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](about/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="76733-153">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="76733-154">Ensuite, l' `New-PSSessionOption` applet de commande, à l’aide du paramètre **ApplicationArguments** , crée un objet d’option de session enregistré dans la `$team` variable.</span><span class="sxs-lookup"><span data-stu-id="76733-154">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="76733-155">Lorsque `New-PSSessionOption` crée l’objet d’option de session, il convertit automatiquement la table de hachage dans la valeur du paramètre **ApplicationArguments** en un dictionnaire primitif afin que les données puissent être transmises de manière fiable à la session à distance.</span><span class="sxs-lookup"><span data-stu-id="76733-155">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="76733-156">L' `New-PSSession` applet de commande démarre une session sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="76733-156">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="76733-157">Elle utilise le paramètre **SessionOption** pour inclure les options dans la `$teamOption` variable.</span><span class="sxs-lookup"><span data-stu-id="76733-157">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="76733-158">L' `Invoke-Command` applet de commande montre que les données de la `$team` variable sont disponibles pour les commandes dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="76733-158">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="76733-159">Les données s’affichent dans la propriété **ApplicationArguments** de la `$PSSenderInfo` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="76733-159">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="76733-160">Le dernier `Invoke-Command` montre comment les données peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="76733-160">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="76733-161">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="76733-161">PARAMETERS</span></span>

### <span data-ttu-id="76733-162">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="76733-162">-ApplicationArguments</span></span>

<span data-ttu-id="76733-163">Spécifie un dictionnaire primitif qui est envoyé à la session à distance.</span><span class="sxs-lookup"><span data-stu-id="76733-163">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="76733-164">Les commandes et les scripts dans la session à distance, y compris les scripts de démarrage dans la configuration de session, peuvent trouver ce dictionnaire dans la propriété **ApplicationArguments** de la `$PSSenderInfo` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="76733-164">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="76733-165">Vous pouvez utiliser ce paramètre pour envoyer des données à la session à distance.</span><span class="sxs-lookup"><span data-stu-id="76733-165">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="76733-166">Pour plus d’informations, consultez [about_Hash_Tables](about/about_Hash_Tables.md), [about_session_configurations](About/about_Session_Configurations.md)et [about_Automatic_Variables](about/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="76733-166">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-167">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="76733-167">-CancelTimeout</span></span>

<span data-ttu-id="76733-168">Détermine la durée pendant laquelle PowerShell attend qu’une opération d’annulation (CTRL + C) se termine avant de se terminer.</span><span class="sxs-lookup"><span data-stu-id="76733-168">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="76733-169">Entrez une valeur en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="76733-169">Enter a value in milliseconds.</span></span>

<span data-ttu-id="76733-170">La valeur par défaut est 60000 (une minute).</span><span class="sxs-lookup"><span data-stu-id="76733-170">The default value is 60000 (one minute).</span></span> <span data-ttu-id="76733-171">Une valeur 0 (zéro) signifie qu'il n'y a pas de délai d'attente et que la commande continue indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="76733-171">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-172">-Culture</span><span class="sxs-lookup"><span data-stu-id="76733-172">-Culture</span></span>

<span data-ttu-id="76733-173">Spécifie la culture à utiliser pour la session.</span><span class="sxs-lookup"><span data-stu-id="76733-173">Specifies the culture to use for the session.</span></span> <span data-ttu-id="76733-174">Entrez un nom de culture au `<languagecode2>-<country/regioncode2>` format (comme `ja-JP` ), une variable qui contient un objet **CultureInfo** ou une commande qui obtient un objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="76733-174">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="76733-175">La valeur par défaut est `$Null` , et la culture définie dans le système d’exploitation est utilisée dans la session.</span><span class="sxs-lookup"><span data-stu-id="76733-175">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-176">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="76733-176">-IdleTimeout</span></span>

<span data-ttu-id="76733-177">Détermine la durée pendant laquelle la session reste ouverte si l’ordinateur distant ne reçoit pas de communication de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="76733-177">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="76733-178">Cela comprend le signal de pulsation.</span><span class="sxs-lookup"><span data-stu-id="76733-178">This includes the heartbeat signal.</span></span> <span data-ttu-id="76733-179">Quand le délai expire, la session se ferme.</span><span class="sxs-lookup"><span data-stu-id="76733-179">When the interval expires, the session closes.</span></span>

<span data-ttu-id="76733-180">La valeur du délai d’inactivité est importante si vous envisagez de vous déconnecter et de vous reconnecter à une session.</span><span class="sxs-lookup"><span data-stu-id="76733-180">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="76733-181">Vous pouvez vous reconnecter seulement si la session n'est pas expirée.</span><span class="sxs-lookup"><span data-stu-id="76733-181">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="76733-182">Entrez une valeur en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="76733-182">Enter a value in milliseconds.</span></span> <span data-ttu-id="76733-183">La valeur minimale est 60000 (1 minute).</span><span class="sxs-lookup"><span data-stu-id="76733-183">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="76733-184">La valeur maximale est la valeur de la propriété **MaxIdleTimeoutms** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="76733-184">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="76733-185">La valeur par défaut,-1, ne définit pas un délai d’inactivité.</span><span class="sxs-lookup"><span data-stu-id="76733-185">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="76733-186">La session utilise le délai d’inactivité défini dans les options de session, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="76733-186">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="76733-187">Si aucune valeur n’est définie (-1), la session utilise la valeur de la propriété **IdleTimeoutMs** de la configuration de session ou la valeur du délai d’attente de l’interpréteur de commandes WSMan ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), selon la valeur la plus petite.</span><span class="sxs-lookup"><span data-stu-id="76733-187">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="76733-188">Si le délai d'inactivité défini dans les options de session dépasse la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session, la commande de création d'une session échoue.</span><span class="sxs-lookup"><span data-stu-id="76733-188">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="76733-189">La valeur **IdleTimeoutMs** de la configuration de session **Microsoft. PowerShell** par défaut est de 7,2 millions millisecondes (2 heures).</span><span class="sxs-lookup"><span data-stu-id="76733-189">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="76733-190">Sa valeur de **MaxIdleTimeoutMs** est de 2147483647 millisecondes ( \> 24 jours).</span><span class="sxs-lookup"><span data-stu-id="76733-190">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="76733-191">La valeur par défaut du délai d’inactivité de l’interpréteur de commandes WSMan ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) est de 7,2 millions millisecondes (2 heures).</span><span class="sxs-lookup"><span data-stu-id="76733-191">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="76733-192">La valeur du délai d’inactivité d’une session peut également être modifiée lors de la déconnexion d’une session ou de la reconnexion à une session.</span><span class="sxs-lookup"><span data-stu-id="76733-192">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="76733-193">Pour plus d’informations, consultez `Disconnect-PSSession` et `Connect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="76733-193">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="76733-194">Dans Windows PowerShell 2.0, la valeur par défaut du paramètre **IdleTimeout** est 240000 (4 minutes).</span><span class="sxs-lookup"><span data-stu-id="76733-194">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-195">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="76733-195">-IncludePortInSPN</span></span>

<span data-ttu-id="76733-196">Comprend le numéro de port dans le nom de principal du service (SPN) utilisé pour l’authentification Kerberos, par exemple, `HTTP://<ComputerName>:5985` .</span><span class="sxs-lookup"><span data-stu-id="76733-196">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="76733-197">Cette option permet à un client qui utilise un nom de principal du service qui n'est pas le nom par défaut de s'authentifier auprès d'un ordinateur distant qui utilise l'authentification Kerberos.</span><span class="sxs-lookup"><span data-stu-id="76733-197">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="76733-198">L'option est conçue pour les entreprises où plusieurs services prenant en charge l'authentification Kerberos s'exécutent sous différents comptes d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="76733-198">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="76733-199">Par exemple, une application IIS qui autorise l’authentification Kerberos peut exiger que le nom principal de service par défaut soit inscrit auprès d’un compte d’utilisateur différent du compte d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="76733-199">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="76733-200">Dans ce cas, la communication à distance PowerShell ne peut pas utiliser Kerberos pour s’authentifier, car elle requiert un nom de principal du service inscrit auprès du compte d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="76733-200">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="76733-201">Pour résoudre ce problème, les administrateurs peuvent créer des noms de principal du service différents, par exemple à l’aide de **Setspn.exe** , qui sont inscrits auprès de différents comptes d’utilisateur et peuvent les distinguer en incluant le numéro de port dans le nom de principal du service.</span><span class="sxs-lookup"><span data-stu-id="76733-201">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe** , that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="76733-202">Pour plus d’informations, consultez [vue d’ensemble de setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="76733-202">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="76733-203">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="76733-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-204">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="76733-204">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="76733-205">Spécifie le nombre de tentatives de connexion de PowerShell à un ordinateur cible en cas d’échec de la tentative en cours en raison de problèmes réseau.</span><span class="sxs-lookup"><span data-stu-id="76733-205">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="76733-206">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="76733-206">The default value is 5.</span></span>

<span data-ttu-id="76733-207">Ce paramètre a été ajouté pour PowerShell version 5,0.</span><span class="sxs-lookup"><span data-stu-id="76733-207">This parameter was added for PowerShell version 5.0.</span></span>

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

### <span data-ttu-id="76733-208">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="76733-208">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="76733-209">Spécifie le nombre maximal d'octets que l'ordinateur local peut recevoir de l'ordinateur distant dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="76733-209">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="76733-210">Entrez une valeur en octets.</span><span class="sxs-lookup"><span data-stu-id="76733-210">Enter a value in bytes.</span></span> <span data-ttu-id="76733-211">Par défaut, il n'existe pas de limite de taille des données.</span><span class="sxs-lookup"><span data-stu-id="76733-211">By default, there is no data size limit.</span></span>

<span data-ttu-id="76733-212">Cette option est conçue pour protéger les ressources sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="76733-212">This option is designed to protect the resources on the client computer.</span></span>

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

### <span data-ttu-id="76733-213">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="76733-213">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="76733-214">Spécifie la taille maximale d'un objet que l'ordinateur local peut recevoir de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="76733-214">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="76733-215">Cette option est conçue pour protéger les ressources sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="76733-215">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="76733-216">Entrez une valeur en octets.</span><span class="sxs-lookup"><span data-stu-id="76733-216">Enter a value in bytes.</span></span>

<span data-ttu-id="76733-217">Dans Windows PowerShell 2.0, si vous omettez ce paramètre, la taille des objets n'est pas limitée.</span><span class="sxs-lookup"><span data-stu-id="76733-217">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="76733-218">À compter de Windows PowerShell 3.0, si vous omettez ce paramètre, la valeur par défaut est 200 Mo.</span><span class="sxs-lookup"><span data-stu-id="76733-218">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-219">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="76733-219">-MaximumRedirection</span></span>

<span data-ttu-id="76733-220">Détermine le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="76733-220">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="76733-221">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="76733-221">The default value is 5.</span></span> <span data-ttu-id="76733-222">La valeur 0 (zéro) empêche toute redirection.</span><span class="sxs-lookup"><span data-stu-id="76733-222">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="76733-223">Cette option est utilisée dans la session uniquement lorsque le paramètre **AllowRedirection** est utilisé dans la commande qui crée la session.</span><span class="sxs-lookup"><span data-stu-id="76733-223">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-224">-NoCompression</span><span class="sxs-lookup"><span data-stu-id="76733-224">-NoCompression</span></span>

<span data-ttu-id="76733-225">Désactive la compression de paquets dans la session.</span><span class="sxs-lookup"><span data-stu-id="76733-225">Turns off packet compression in the session.</span></span> <span data-ttu-id="76733-226">La compression utilise davantage de cycles processeur, mais rend la transmission plus rapide.</span><span class="sxs-lookup"><span data-stu-id="76733-226">Compression uses more processor cycles, but it makes transmission faster.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-227">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="76733-227">-NoEncryption</span></span>

<span data-ttu-id="76733-228">Désactive le chiffrement des données.</span><span class="sxs-lookup"><span data-stu-id="76733-228">Turns off data encryption.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-229">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="76733-229">-NoMachineProfile</span></span>

<span data-ttu-id="76733-230">Empêche le chargement du profil d'utilisateur Windows de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="76733-230">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="76733-231">Par conséquent, la session peut-être être créée plus rapidement, mais les paramètres de Registre spécifiques à l'utilisateur, les éléments comme des variables d'environnement et les certificats ne sont pas disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="76733-231">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-232">-OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="76733-232">-OpenTimeout</span></span>

<span data-ttu-id="76733-233">Détermine le temps pendant lequel l'ordinateur client attend que la connexion de la session soit établie.</span><span class="sxs-lookup"><span data-stu-id="76733-233">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="76733-234">Quand le délai expire, la commande d'établissement de la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="76733-234">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="76733-235">Entrez une valeur en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="76733-235">Enter a value in milliseconds.</span></span>

<span data-ttu-id="76733-236">La valeur par défaut est 180000 (3 minutes).</span><span class="sxs-lookup"><span data-stu-id="76733-236">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="76733-237">Une valeur 0 (zéro) signifie qu'il n'y a pas de délai d'attente et que la commande continue indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="76733-237">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-238">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="76733-238">-OperationTimeout</span></span>

<span data-ttu-id="76733-239">Détermine la durée maximale pendant laquelle une opération de la session peut s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="76733-239">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="76733-240">Quand le délai expire, l'opération échoue.</span><span class="sxs-lookup"><span data-stu-id="76733-240">When the interval expires, the operation fails.</span></span> <span data-ttu-id="76733-241">Entrez une valeur en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="76733-241">Enter a value in milliseconds.</span></span>

<span data-ttu-id="76733-242">La valeur par défaut est 180000 (3 minutes).</span><span class="sxs-lookup"><span data-stu-id="76733-242">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="76733-243">Une valeur 0 (zéro) signifie qu'il n'y a pas de délai d'attente et que l'opération continue indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="76733-243">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-244">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="76733-244">-OutputBufferingMode</span></span>

<span data-ttu-id="76733-245">Détermine comment la sortie de la commande est gérée dans des sessions déconnectées quand la mémoire tampon de sortie est pleine.</span><span class="sxs-lookup"><span data-stu-id="76733-245">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="76733-246">Si le mode de mise en mémoire tampon de sortie n'est pas défini dans la session ni dans la configuration de session, la valeur par défaut est **Block**.</span><span class="sxs-lookup"><span data-stu-id="76733-246">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="76733-247">Les utilisateurs peuvent également changer le mode de mise en mémoire tampon de sortie lors de la déconnexion de la session.</span><span class="sxs-lookup"><span data-stu-id="76733-247">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="76733-248">Si vous omettez ce paramètre, la valeur de **OutputBufferingMode** de l’objet d’option de session est None.</span><span class="sxs-lookup"><span data-stu-id="76733-248">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="76733-249">La valeur **Block** ou **Drop** remplace l'option de transport du mode de mise en mémoire tampon de sortie définie dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="76733-249">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="76733-250">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="76733-250">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="76733-251">Bloquer.</span><span class="sxs-lookup"><span data-stu-id="76733-251">Block.</span></span> <span data-ttu-id="76733-252">Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée.</span><span class="sxs-lookup"><span data-stu-id="76733-252">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="76733-253">Drop.</span><span class="sxs-lookup"><span data-stu-id="76733-253">Drop.</span></span> <span data-ttu-id="76733-254">Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="76733-254">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="76733-255">Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.</span><span class="sxs-lookup"><span data-stu-id="76733-255">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="76733-256">Aucun.</span><span class="sxs-lookup"><span data-stu-id="76733-256">None.</span></span> <span data-ttu-id="76733-257">Aucun mode de mise en mémoire tampon de sortie n'est spécifié.</span><span class="sxs-lookup"><span data-stu-id="76733-257">No output buffering mode is specified.</span></span>

<span data-ttu-id="76733-258">Pour plus d’informations sur l’option de transport mode de mise en mémoire tampon de sortie, consultez `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="76733-258">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="76733-259">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="76733-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-260">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="76733-260">-ProxyAccessType</span></span>

<span data-ttu-id="76733-261">Détermine quel mécanisme est utilisé pour résoudre le nom d'hôte.</span><span class="sxs-lookup"><span data-stu-id="76733-261">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="76733-262">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="76733-262">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="76733-263">IEConfig</span><span class="sxs-lookup"><span data-stu-id="76733-263">IEConfig</span></span>
- <span data-ttu-id="76733-264">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="76733-264">WinHttpConfig</span></span>
- <span data-ttu-id="76733-265">Détection automatique</span><span class="sxs-lookup"><span data-stu-id="76733-265">AutoDetect</span></span>
- <span data-ttu-id="76733-266">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="76733-266">NoProxyServer</span></span>
- <span data-ttu-id="76733-267">Aucun</span><span class="sxs-lookup"><span data-stu-id="76733-267">None</span></span>

<span data-ttu-id="76733-268">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="76733-268">The default value is None.</span></span>

<span data-ttu-id="76733-269">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération ProxyAccessType](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span><span class="sxs-lookup"><span data-stu-id="76733-269">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span></span>

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-270">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="76733-270">-ProxyAuthentication</span></span>

<span data-ttu-id="76733-271">Spécifie la méthode d'authentification qui est utilisée pour la résolution du proxy.</span><span class="sxs-lookup"><span data-stu-id="76733-271">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="76733-272">Les valeurs acceptables pour ce paramètre sont les suivantes : **Basic** , **Digest** et **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="76733-272">The acceptable values for this parameter are: **Basic** , **Digest** , and **Negotiate**.</span></span> <span data-ttu-id="76733-273">La valeur par défaut est **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="76733-273">The default value is **Negotiate**.</span></span>

<span data-ttu-id="76733-274">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="76733-274">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-275">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="76733-275">-ProxyCredential</span></span>

<span data-ttu-id="76733-276">Spécifie les informations d'identification à utiliser pour l'authentification du proxy.</span><span class="sxs-lookup"><span data-stu-id="76733-276">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="76733-277">Entrez une variable qui contient un objet **PSCredential** ou une commande qui obtient un objet **PSCredential** , tel qu’une `Get-Credential` commande.</span><span class="sxs-lookup"><span data-stu-id="76733-277">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="76733-278">Si cette option n'est pas définie, aucune information d'identification n'est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="76733-278">If this option is not set, no credentials are specified.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-279">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="76733-279">-SkipCACheck</span></span>

<span data-ttu-id="76733-280">Spécifie que lorsqu’il se connecte via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="76733-280">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="76733-281">Utilisez cette option seulement quand l'ordinateur distant est approuvé via un autre mécanisme, par exemple quand l'ordinateur distant fait partie d'un réseau qui est physiquement sécurisé et isolé, ou bien quand l'ordinateur distant est répertorié comme hôte approuvé dans une configuration WinRM.</span><span class="sxs-lookup"><span data-stu-id="76733-281">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-282">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="76733-282">-SkipCNCheck</span></span>

<span data-ttu-id="76733-283">Spécifie que le nom commun de certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="76733-283">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="76733-284">Cette option est utilisée seulement dans les opérations à distance utilisant le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="76733-284">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="76733-285">Utilisez cette option seulement pour des ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="76733-285">Use this option only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-286">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="76733-286">-SkipRevocationCheck</span></span>

<span data-ttu-id="76733-287">Ne vérifie pas l'état de révocation du certificat serveur.</span><span class="sxs-lookup"><span data-stu-id="76733-287">Does not validate the revocation status of the server certificate.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-288">-UICulture</span><span class="sxs-lookup"><span data-stu-id="76733-288">-UICulture</span></span>

<span data-ttu-id="76733-289">Spécifie la culture de l'interface utilisateur à utiliser pour la session.</span><span class="sxs-lookup"><span data-stu-id="76733-289">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="76733-290">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="76733-290">Valid values include:</span></span>

- <span data-ttu-id="76733-291">Nom de culture au `<languagecode2>-<country/regioncode2>` format, tel que `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="76733-291">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="76733-292">Une variable qui contient un objet **CultureInfo**</span><span class="sxs-lookup"><span data-stu-id="76733-292">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="76733-293">Commande qui obtient un objet **CultureInfo** , tel que `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="76733-293">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="76733-294">La valeur par défaut est `$null` , et la culture d’interface utilisateur définie dans le système d’exploitation lors de la création de la session est utilisée dans la session.</span><span class="sxs-lookup"><span data-stu-id="76733-294">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-295">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="76733-295">-UseUTF16</span></span>

<span data-ttu-id="76733-296">Indique que cette applet de commande encode la demande au format UTF16 au lieu du format UTF8.</span><span class="sxs-lookup"><span data-stu-id="76733-296">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="76733-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76733-297">CommonParameters</span></span>

<span data-ttu-id="76733-298">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76733-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76733-299">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="76733-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="76733-300">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="76733-300">INPUTS</span></span>

### <span data-ttu-id="76733-301">Aucun</span><span class="sxs-lookup"><span data-stu-id="76733-301">None</span></span>

<span data-ttu-id="76733-302">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="76733-302">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="76733-303">SORTIES</span><span class="sxs-lookup"><span data-stu-id="76733-303">OUTPUTS</span></span>

### <span data-ttu-id="76733-304">System. Management. Automation. Remoting. PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="76733-304">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="76733-305">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="76733-305">NOTES</span></span>

<span data-ttu-id="76733-306">Si le paramètre **SessionOption** n’est pas utilisé dans une commande pour créer une session **PSSession** , les options de session sont déterminées par les valeurs de propriété de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="76733-306">If the **SessionOption** parameter is not used in a command to create a **PSSession** , the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="76733-307">Pour plus d’informations sur la `$PSSessionOption` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="76733-307">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="76733-308">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="76733-308">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="76733-309">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="76733-309">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="76733-310">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="76733-310">RELATED LINKS</span></span>

[<span data-ttu-id="76733-311">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="76733-311">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="76733-312">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="76733-312">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="76733-313">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="76733-313">New-PSSession</span></span>](New-PSSession.md)
