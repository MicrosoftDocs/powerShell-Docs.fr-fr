---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205414"
---
# <span data-ttu-id="3aac0-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-103">Stop-Computer</span></span>

## <span data-ttu-id="3aac0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3aac0-104">SYNOPSIS</span></span>
<span data-ttu-id="3aac0-105">Arrête les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="3aac0-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="3aac0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3aac0-106">SYNTAX</span></span>

### <span data-ttu-id="3aac0-107">Tous</span><span class="sxs-lookup"><span data-stu-id="3aac0-107">All</span></span>

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="3aac0-108">Description</span><span class="sxs-lookup"><span data-stu-id="3aac0-108">DESCRIPTION</span></span>

<span data-ttu-id="3aac0-109">L' `Stop-Computer` applet de commande arrête l’ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="3aac0-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="3aac0-110">Vous pouvez utiliser les paramètres de `Stop-Computer` pour exécuter les opérations d’arrêt en tant que tâche en arrière-plan, spécifier les niveaux d’authentification et d’autres informations d’identification, pour limiter les connexions simultanées créées pour exécuter la commande et forcer l’arrêt immédiat.</span><span class="sxs-lookup"><span data-stu-id="3aac0-110">You can use the parameters of `Stop-Computer` to run the shutdown operations as a background job, to specify the authentication levels and alternate credentials, to limit the concurrent connections that are created to run the command, and to force an immediate shut down.</span></span>

<span data-ttu-id="3aac0-111">Cette applet de commande ne requiert pas la communication à distance PowerShell, sauf si vous utilisez le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-111">This cmdlet doesn't require PowerShell remoting unless you use the **AsJob** parameter.</span></span>

## <span data-ttu-id="3aac0-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3aac0-112">EXAMPLES</span></span>

### <span data-ttu-id="3aac0-113">Exemple 1 : arrêter l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="3aac0-113">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="3aac0-114">Cet exemple arrête l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3aac0-114">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="3aac0-115">Exemple 2 : arrêter deux ordinateurs distants et l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="3aac0-115">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="3aac0-116">Cet exemple arrête deux ordinateurs distants et l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3aac0-116">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="3aac0-117">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants et l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3aac0-117">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="3aac0-118">Chaque ordinateur est arrêté.</span><span class="sxs-lookup"><span data-stu-id="3aac0-118">Each computer is shut down.</span></span>

### <span data-ttu-id="3aac0-119">Exemple 3 : arrêter des ordinateurs distants en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="3aac0-119">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="3aac0-120">Dans cet exemple, `Stop-Computer` s’exécute en tant que tâche en arrière-plan sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="3aac0-120">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

<span data-ttu-id="3aac0-121">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="3aac0-121">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="3aac0-122">Le paramètre **AsJob** exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="3aac0-122">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="3aac0-123">Les objets de traitement sont stockés dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-123">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="3aac0-124">Les objets de traitement dans la `$j` variable sont envoyés dans le pipeline à `Receive-Job` , qui obtient les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="3aac0-124">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="3aac0-125">Les objets sont stockés dans la `$results` variable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-125">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="3aac0-126">La `$results` variable affiche les informations sur la tâche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3aac0-126">The `$results` variable displays the job information in the PowerShell console.</span></span>

<span data-ttu-id="3aac0-127">Étant donné que **AsJob** crée la tâche sur l’ordinateur local et retourne automatiquement les résultats à l’ordinateur local, vous pouvez exécuter `Receive-Job` en tant que commande locale.</span><span class="sxs-lookup"><span data-stu-id="3aac0-127">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

### <span data-ttu-id="3aac0-128">Exemple 4 : arrêter un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="3aac0-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="3aac0-129">Cet exemple arrête un ordinateur distant à l’aide de l’authentification spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3aac0-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="3aac0-130">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3aac0-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="3aac0-131">Le paramètre d' **emprunt d’identité** spécifie un emprunt d’identité personnalisé et le paramètre **DcomAuthentication** spécifie les paramètres au niveau de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="3aac0-131">The **Impersonation** parameter specifies a customized impersonation and the **DcomAuthentication** parameter specifies authentication-level settings.</span></span>

### <span data-ttu-id="3aac0-132">Exemple 5 : arrêter des ordinateurs dans un domaine</span><span class="sxs-lookup"><span data-stu-id="3aac0-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="3aac0-133">Dans cet exemple, les commandes forcent l’arrêt immédiat de tous les ordinateurs dans un domaine spécifié.</span><span class="sxs-lookup"><span data-stu-id="3aac0-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

<span data-ttu-id="3aac0-134">`Get-Content` utilise le paramètre **path** pour obtenir un fichier dans le répertoire actif avec la liste des ordinateurs du domaine.</span><span class="sxs-lookup"><span data-stu-id="3aac0-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="3aac0-135">Les objets sont stockés dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="3aac0-136">`Get-Credential` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="3aac0-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="3aac0-137">Les informations d’identification sont stockées dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="3aac0-138">`Stop-Computer` arrête les ordinateurs spécifiés avec la liste des ordinateurs du paramètre **ComputerName** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="3aac0-139">Le paramètre **force** force un arrêt immédiat.</span><span class="sxs-lookup"><span data-stu-id="3aac0-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="3aac0-140">Le paramètre **ThrottleLimit** limite la commande à 10 connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="3aac0-140">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span> <span data-ttu-id="3aac0-141">Le paramètre **Credential** envoie les informations d’identification enregistrées dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-141">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="3aac0-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3aac0-142">PARAMETERS</span></span>

### <span data-ttu-id="3aac0-143">-AsJob</span><span class="sxs-lookup"><span data-stu-id="3aac0-143">-AsJob</span></span>

<span data-ttu-id="3aac0-144">Indique que cette applet de commande s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="3aac0-144">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="3aac0-145">Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-145">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="3aac0-146">Pour plus d'informations, consultez [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aac0-146">For more information, see [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="3aac0-147">Lorsque vous spécifiez le paramètre **AsJob** , la commande retourne immédiatement un objet qui représente la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="3aac0-147">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="3aac0-148">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="3aac0-148">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="3aac0-149">La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3aac0-149">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="3aac0-150">Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="3aac0-150">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="3aac0-151">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) et [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="3aac0-151">For more information about PowerShell background jobs, see [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) and [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="3aac0-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3aac0-152">-ComputerName</span></span>

<span data-ttu-id="3aac0-153">Spécifie les ordinateurs à arrêter.</span><span class="sxs-lookup"><span data-stu-id="3aac0-153">Specifies the computers to stop.</span></span> <span data-ttu-id="3aac0-154">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3aac0-154">The default is the local computer.</span></span>

<span data-ttu-id="3aac0-155">Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="3aac0-155">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="3aac0-156">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur ou localhost.</span><span class="sxs-lookup"><span data-stu-id="3aac0-156">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="3aac0-157">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3aac0-157">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="3aac0-158">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="3aac0-158">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3aac0-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3aac0-159">-Confirm</span></span>

<span data-ttu-id="3aac0-160">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3aac0-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3aac0-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="3aac0-161">-Credential</span></span>

<span data-ttu-id="3aac0-162">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="3aac0-162">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="3aac0-163">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="3aac0-163">The default is the current user.</span></span>

<span data-ttu-id="3aac0-164">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3aac0-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3aac0-165">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="3aac0-165">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="3aac0-166">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="3aac0-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="3aac0-167">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="3aac0-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3aac0-168">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="3aac0-168">-DcomAuthentication</span></span>

<span data-ttu-id="3aac0-169">Spécifie le niveau d’authentification que cette applet de commande utilise avec WMI.</span><span class="sxs-lookup"><span data-stu-id="3aac0-169">Specifies the authentication level that this cmdlet uses with WMI.</span></span> <span data-ttu-id="3aac0-170">`Stop-Computer` utilise WMI.</span><span class="sxs-lookup"><span data-stu-id="3aac0-170">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="3aac0-171">La valeur par défaut est **Packet** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-171">The default value is **Packet** .</span></span>

<span data-ttu-id="3aac0-172">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="3aac0-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3aac0-173">**Par défaut** : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="3aac0-173">**Default** : Windows Authentication.</span></span>
- <span data-ttu-id="3aac0-174">**None** : aucune authentification com.</span><span class="sxs-lookup"><span data-stu-id="3aac0-174">**None** : No COM authentication.</span></span>
- <span data-ttu-id="3aac0-175">**Connect** : authentification com au niveau de la connexion.</span><span class="sxs-lookup"><span data-stu-id="3aac0-175">**Connect** : Connect-level COM authentication.</span></span>
- <span data-ttu-id="3aac0-176">**Appel** : authentification com au niveau de l’appel.</span><span class="sxs-lookup"><span data-stu-id="3aac0-176">**Call** : Call-level COM authentication.</span></span>
- <span data-ttu-id="3aac0-177">**Paquet** : authentification com au niveau du paquet.</span><span class="sxs-lookup"><span data-stu-id="3aac0-177">**Packet** : Packet-level COM authentication.</span></span>
- <span data-ttu-id="3aac0-178">**PacketIntegrity** : authentification com au niveau de l’intégrité du paquet.</span><span class="sxs-lookup"><span data-stu-id="3aac0-178">**PacketIntegrity** : Packet Integrity-level COM authentication.</span></span>
- <span data-ttu-id="3aac0-179">**PacketPrivacy** : authentification com au niveau de la confidentialité des paquets.</span><span class="sxs-lookup"><span data-stu-id="3aac0-179">**PacketPrivacy** : Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="3aac0-180">Non **modifié** : identique à la commande précédente.</span><span class="sxs-lookup"><span data-stu-id="3aac0-180">**Unchanged** : Same as the previous command.</span></span>

<span data-ttu-id="3aac0-181">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span><span class="sxs-lookup"><span data-stu-id="3aac0-181">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3aac0-182">-Force</span><span class="sxs-lookup"><span data-stu-id="3aac0-182">-Force</span></span>

<span data-ttu-id="3aac0-183">Force l’arrêt immédiat de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3aac0-183">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="3aac0-184">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="3aac0-184">-Impersonation</span></span>

<span data-ttu-id="3aac0-185">Spécifie le niveau d’emprunt d’identité à utiliser lorsque cette applet de commande appelle WMI.</span><span class="sxs-lookup"><span data-stu-id="3aac0-185">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="3aac0-186">La valeur par défaut est **Impersonate** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-186">The default value is **Impersonate** .</span></span>

<span data-ttu-id="3aac0-187">`Stop-Computer` utilise WMI.</span><span class="sxs-lookup"><span data-stu-id="3aac0-187">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="3aac0-188">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="3aac0-188">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3aac0-189">**Default** : emprunt d’identité par défaut.</span><span class="sxs-lookup"><span data-stu-id="3aac0-189">**Default** : Default impersonation.</span></span>
- <span data-ttu-id="3aac0-190">**Anonymous** : masque l’identité de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3aac0-190">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="3aac0-191">**Identify** : permet aux objets d’interroger les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3aac0-191">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="3aac0-192">**Impersonate** : permet aux objets d’utiliser les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3aac0-192">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3aac0-193">-Protocol</span><span class="sxs-lookup"><span data-stu-id="3aac0-193">-Protocol</span></span>

<span data-ttu-id="3aac0-194">Spécifie le protocole à utiliser pour redémarrer les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="3aac0-194">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="3aac0-195">Les valeurs acceptables pour ce paramètre sont les suivantes : **WSMan** et **DCOM** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-195">The acceptable values for this parameter are: **WSMan** and **DCOM** .</span></span> <span data-ttu-id="3aac0-196">La valeur par défaut est **DCOM** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-196">The default value is **DCOM** .</span></span>

<span data-ttu-id="3aac0-197">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3aac0-197">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3aac0-198">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3aac0-198">-ThrottleLimit</span></span>

<span data-ttu-id="3aac0-199">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="3aac0-199">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="3aac0-200">Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3aac0-200">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="3aac0-201">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3aac0-201">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="3aac0-202">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="3aac0-202">-WsmanAuthentication</span></span>

<span data-ttu-id="3aac0-203">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="3aac0-203">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="3aac0-204">La valeur par défaut est **Default** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-204">The default value is **Default** .</span></span>

<span data-ttu-id="3aac0-205">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="3aac0-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3aac0-206">Basic</span><span class="sxs-lookup"><span data-stu-id="3aac0-206">Basic</span></span>
- <span data-ttu-id="3aac0-207">CredSSP</span><span class="sxs-lookup"><span data-stu-id="3aac0-207">CredSSP</span></span>
- <span data-ttu-id="3aac0-208">Default</span><span class="sxs-lookup"><span data-stu-id="3aac0-208">Default</span></span>
- <span data-ttu-id="3aac0-209">Digest</span><span class="sxs-lookup"><span data-stu-id="3aac0-209">Digest</span></span>
- <span data-ttu-id="3aac0-210">Kerberos</span><span class="sxs-lookup"><span data-stu-id="3aac0-210">Kerberos</span></span>
- <span data-ttu-id="3aac0-211">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="3aac0-211">Negotiate.</span></span>

<span data-ttu-id="3aac0-212">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="3aac0-212">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="3aac0-213">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="3aac0-213">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="3aac0-214">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="3aac0-214">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="3aac0-215">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="3aac0-215">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="3aac0-216">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3aac0-216">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3aac0-217">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3aac0-217">-WhatIf</span></span>

<span data-ttu-id="3aac0-218">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3aac0-218">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3aac0-219">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="3aac0-219">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="3aac0-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3aac0-220">CommonParameters</span></span>

<span data-ttu-id="3aac0-221">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3aac0-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3aac0-222">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3aac0-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3aac0-223">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3aac0-223">INPUTS</span></span>

### <span data-ttu-id="3aac0-224">Aucun</span><span class="sxs-lookup"><span data-stu-id="3aac0-224">None</span></span>

<span data-ttu-id="3aac0-225">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3aac0-225">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3aac0-226">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3aac0-226">OUTPUTS</span></span>

### <span data-ttu-id="3aac0-227">None ou System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="3aac0-227">None or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="3aac0-228">L’applet de commande retourne un objet **System. Management. Automation. RemotingJob** , si vous spécifiez le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-228">The cmdlet returns a **System.Management.Automation.RemotingJob** object, if you specify the **AsJob** parameter.</span></span> <span data-ttu-id="3aac0-229">Dans le cas contraire, elle ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="3aac0-229">Otherwise, it doesn't generate any output.</span></span>

## <span data-ttu-id="3aac0-230">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3aac0-230">NOTES</span></span>

<span data-ttu-id="3aac0-231">Cette applet de commande utilise la méthode **Win32Shutdown** de la classe WMI **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="3aac0-231">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="3aac0-232">Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3aac0-232">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="3aac0-233">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3aac0-233">RELATED LINKS</span></span>

[<span data-ttu-id="3aac0-234">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-234">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="3aac0-235">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-235">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="3aac0-236">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-236">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="3aac0-237">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-237">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="3aac0-238">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-238">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="3aac0-239">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="3aac0-239">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="3aac0-240">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="3aac0-240">Test-Connection</span></span>](Test-Connection.md)
