---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 1912df403e3204be623a8c15c04b528c705169e1
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205445"
---
# <span data-ttu-id="d74b6-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="d74b6-103">Restart-Computer</span></span>

## <span data-ttu-id="d74b6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d74b6-104">SYNOPSIS</span></span>
<span data-ttu-id="d74b6-105">Redémarre le système d’exploitation sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="d74b6-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="d74b6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d74b6-106">SYNTAX</span></span>

### <span data-ttu-id="d74b6-107">DefaultSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d74b6-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d74b6-108">Description</span><span class="sxs-lookup"><span data-stu-id="d74b6-108">DESCRIPTION</span></span>

<span data-ttu-id="d74b6-109">L' `Restart-Computer` applet de commande redémarre le système d’exploitation sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="d74b6-109">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="d74b6-110">Vous pouvez utiliser les paramètres de `Restart-Computer` pour exécuter les opérations de redémarrage, pour spécifier les niveaux d’authentification et d’autres informations d’identification, pour limiter les opérations qui s’exécutent en même temps et pour forcer un redémarrage immédiat.</span><span class="sxs-lookup"><span data-stu-id="d74b6-110">You can use the parameters of `Restart-Computer` to run the restart operations, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="d74b6-111">À partir de Windows PowerShell 3,0, vous pouvez attendre la fin du redémarrage avant d’exécuter la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="d74b6-111">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="d74b6-112">Spécifiez un délai d’attente et un intervalle de requête, puis attendez que certains services soient disponibles sur l’ordinateur redémarré.</span><span class="sxs-lookup"><span data-stu-id="d74b6-112">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="d74b6-113">Cette fonctionnalité facilite `Restart-Computer` l’utilisation de dans les scripts et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="d74b6-113">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

## <span data-ttu-id="d74b6-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d74b6-114">EXAMPLES</span></span>

### <span data-ttu-id="d74b6-115">Exemple 1 : redémarrer l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="d74b6-115">Example 1: Restart the local computer</span></span>

<span data-ttu-id="d74b6-116">`Restart-Computer` redémarre l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d74b6-116">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="d74b6-117">Exemple 2 : redémarrer plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="d74b6-117">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="d74b6-118">`Restart-Computer` peut redémarrer les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="d74b6-118">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="d74b6-119">Le paramètre **ComputerName** accepte un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d74b6-119">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="d74b6-120">Exemple 3 : obtenir des noms d’ordinateur à partir d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="d74b6-120">Example 3: Get computer names from a text file</span></span>

<span data-ttu-id="d74b6-121">`Restart-Computer` Obtient une liste de noms d’ordinateurs à partir d’un fichier texte et redémarre les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d74b6-121">`Restart-Computer` gets a list of computer names from a text file and restarts the computers.</span></span> <span data-ttu-id="d74b6-122">Le paramètre **ComputerName** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="d74b6-122">The **ComputerName** parameter isn't specified.</span></span> <span data-ttu-id="d74b6-123">Mais comme il s’agit du premier paramètre de position, il accepte les noms d’ordinateur du fichier texte qui sont envoyés vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d74b6-123">But because it's the first position parameter, it accepts the computer names from the text file that are sent down the pipeline.</span></span>

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

<span data-ttu-id="d74b6-124">`Get-Content` utilise le paramètre **path** pour obtenir une liste de noms d’ordinateurs à partir d’un fichier texte, **Domain01.txt** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-124">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt** .</span></span> <span data-ttu-id="d74b6-125">Les noms d’ordinateur sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d74b6-125">The computer names are sent down the pipeline.</span></span> <span data-ttu-id="d74b6-126">`Restart-Computer` redémarre chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-126">`Restart-Computer` restarts each computer.</span></span>

### <span data-ttu-id="d74b6-127">Exemple 4 : forcer le redémarrage des ordinateurs listés dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="d74b6-127">Example 4: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="d74b6-128">Cet exemple force un redémarrage immédiat des ordinateurs listés dans le `Domain01.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="d74b6-128">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="d74b6-129">Les noms d’ordinateurs du fichier texte sont stockés dans une variable.</span><span class="sxs-lookup"><span data-stu-id="d74b6-129">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="d74b6-130">Le paramètre **force** force un redémarrage immédiat.</span><span class="sxs-lookup"><span data-stu-id="d74b6-130">The **Force** parameter forces an immediate restart.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

<span data-ttu-id="d74b6-131">`Get-Content` utilise le paramètre **path** pour obtenir une liste de noms d’ordinateurs à partir d’un fichier texte, **Domain01.txt** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-131">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt** .</span></span> <span data-ttu-id="d74b6-132">Les noms des ordinateurs sont stockés dans la variable `$Names` .</span><span class="sxs-lookup"><span data-stu-id="d74b6-132">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="d74b6-133">`Get-Credential` vous invite à entrer un nom d’utilisateur et un mot de passe, et stocke les valeurs dans la variable `$Creds` .</span><span class="sxs-lookup"><span data-stu-id="d74b6-133">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="d74b6-134">`Restart-Computer` utilise les paramètres **ComputerName** et **Credential** avec leurs variables.</span><span class="sxs-lookup"><span data-stu-id="d74b6-134">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="d74b6-135">Le paramètre **force** provoque un redémarrage immédiat de chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-135">The **Force** parameter causes an immediate restart of each computer.</span></span>

### <span data-ttu-id="d74b6-136">Exemple 6 : redémarrer un ordinateur distant et attendre PowerShell</span><span class="sxs-lookup"><span data-stu-id="d74b6-136">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="d74b6-137">`Restart-Computer` redémarre l’ordinateur distant, puis attend jusqu’à 5 minutes (300 secondes) que PowerShell soit disponible sur l’ordinateur redémarré avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d74b6-137">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="d74b6-138">`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-138">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** .</span></span> <span data-ttu-id="d74b6-139">Le paramètre **Wait** attend la fin du redémarrage.</span><span class="sxs-lookup"><span data-stu-id="d74b6-139">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="d74b6-140">**Pour** spécifie que PowerShell peut exécuter des commandes sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d74b6-140">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="d74b6-141">Le paramètre **timeout** spécifie une attente de cinq minutes.</span><span class="sxs-lookup"><span data-stu-id="d74b6-141">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="d74b6-142">Le paramètre **delay** interroge l’ordinateur distant toutes les deux secondes pour déterminer s’il est redémarré.</span><span class="sxs-lookup"><span data-stu-id="d74b6-142">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="d74b6-143">Exemple 7 : redémarrer un ordinateur à l’aide de WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="d74b6-143">Example 7: Restart a computer by using WsmanAuthentication</span></span>

<span data-ttu-id="d74b6-144">`Restart-Computer` redémarre l’ordinateur distant à l’aide du mécanisme **WsmanAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-144">`Restart-Computer` restarts the remote computer using the **WsmanAuthentication** mechanism.</span></span>
<span data-ttu-id="d74b6-145">L’authentification Kerberos détermine si l’utilisateur actuel est autorisé à redémarrer l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d74b6-145">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span> <span data-ttu-id="d74b6-146">Pour plus d’informations, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="d74b6-146">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

<span data-ttu-id="d74b6-147">`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-147">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01** .</span></span>
<span data-ttu-id="d74b6-148">Le paramètre **WsmanAuthentication** spécifie la méthode d’authentification comme **Kerberos** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-148">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos** .</span></span>

## <span data-ttu-id="d74b6-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d74b6-149">PARAMETERS</span></span>

### <span data-ttu-id="d74b6-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d74b6-150">-ComputerName</span></span>

<span data-ttu-id="d74b6-151">Spécifie un nom d’ordinateur ou un tableau de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d74b6-151">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="d74b6-152">`Restart-Computer` accepte les objets **ComputerName** du ou des variables.</span><span class="sxs-lookup"><span data-stu-id="d74b6-152">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="d74b6-153">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d74b6-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="d74b6-154">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point `.` ou localhost.</span><span class="sxs-lookup"><span data-stu-id="d74b6-154">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="d74b6-155">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d74b6-155">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="d74b6-156">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="d74b6-156">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="d74b6-157">Si le paramètre **ComputerName** n’est pas spécifié, `Restart-Computer` redémarre l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d74b6-157">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d74b6-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="d74b6-158">-Credential</span></span>

<span data-ttu-id="d74b6-159">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="d74b6-159">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="d74b6-160">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d74b6-160">The default is the current user.</span></span>

<span data-ttu-id="d74b6-161">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="d74b6-161">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d74b6-162">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d74b6-162">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="d74b6-163">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="d74b6-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="d74b6-164">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="d74b6-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="d74b6-165">-Délai</span><span class="sxs-lookup"><span data-stu-id="d74b6-165">-Delay</span></span>

<span data-ttu-id="d74b6-166">Spécifie la fréquence des requêtes, en secondes.</span><span class="sxs-lookup"><span data-stu-id="d74b6-166">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="d74b6-167">PowerShell interroge le service spécifié par le paramètre **for** pour déterminer si le service est disponible après le redémarrage de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-167">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="d74b6-168">Ce paramètre est valide uniquement avec les paramètres **Wait** et **for** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-168">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="d74b6-169">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d74b6-169">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="d74b6-170">Si le paramètre **delay** n’est pas spécifié, `Restart-Computer` utilise un délai de cinq secondes.</span><span class="sxs-lookup"><span data-stu-id="d74b6-170">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d74b6-171">-Pour</span><span class="sxs-lookup"><span data-stu-id="d74b6-171">-For</span></span>

<span data-ttu-id="d74b6-172">Spécifie le comportement de PowerShell, car il attend que le service ou la fonctionnalité spécifié soit disponible après le redémarrage de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-172">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="d74b6-173">Ce paramètre est valide uniquement avec le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-173">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="d74b6-174">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d74b6-174">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d74b6-175">**Default** : attend le redémarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d74b6-175">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="d74b6-176">**PowerShell** : peut exécuter des commandes dans une session à distance PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-176">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="d74b6-177">**WMI** : reçoit une réponse à une requête de Win32_ComputerSystem pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-177">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="d74b6-178">**WinRM** : peut établir une session à distance sur l’ordinateur à l’aide de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="d74b6-178">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="d74b6-179">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d74b6-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d74b6-180">-Force</span><span class="sxs-lookup"><span data-stu-id="d74b6-180">-Force</span></span>

<span data-ttu-id="d74b6-181">Force un redémarrage immédiat de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-181">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d74b6-182">-Timeout</span><span class="sxs-lookup"><span data-stu-id="d74b6-182">-Timeout</span></span>

<span data-ttu-id="d74b6-183">Spécifie la durée de l'attente, en secondes.</span><span class="sxs-lookup"><span data-stu-id="d74b6-183">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="d74b6-184">Lorsque le délai d’attente est écoulé, `Restart-Computer` retourne à l’invite de commandes, même si les ordinateurs ne sont pas redémarrés.</span><span class="sxs-lookup"><span data-stu-id="d74b6-184">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="d74b6-185">Le paramètre **timeout** est valide uniquement avec le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-185">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="d74b6-186">Le **délai d'** attente remplace la période d’attente indéfinie du paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-186">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="d74b6-187">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d74b6-187">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d74b6-188">-Wait</span><span class="sxs-lookup"><span data-stu-id="d74b6-188">-Wait</span></span>

<span data-ttu-id="d74b6-189">`Restart-Computer` supprime l’invite PowerShell et bloque le pipeline jusqu’à ce que les ordinateurs aient redémarré.</span><span class="sxs-lookup"><span data-stu-id="d74b6-189">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="d74b6-190">Vous pouvez utiliser ce paramètre dans un script pour redémarrer les ordinateurs, puis continuer le traitement une fois le redémarrage terminé.</span><span class="sxs-lookup"><span data-stu-id="d74b6-190">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="d74b6-191">Le paramètre **Wait** attend indéfiniment que les ordinateurs redémarrent.</span><span class="sxs-lookup"><span data-stu-id="d74b6-191">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="d74b6-192">Vous pouvez utiliser le **délai d’expiration** pour ajuster le minutage et les paramètres **de** **délai** et pour attendre que des services particuliers soient disponibles sur les ordinateurs redémarrés.</span><span class="sxs-lookup"><span data-stu-id="d74b6-192">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="d74b6-193">Le paramètre **Wait** n’est pas valide lorsque vous redémarrez l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d74b6-193">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="d74b6-194">Si la valeur du paramètre **ComputerName** contient les noms des ordinateurs distants et de l’ordinateur local, `Restart-Computer` génère une erreur sans fin d' **attente** sur l’ordinateur local, mais attend que les ordinateurs distants redémarrent.</span><span class="sxs-lookup"><span data-stu-id="d74b6-194">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="d74b6-195">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d74b6-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d74b6-196">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="d74b6-196">-WsmanAuthentication</span></span>

<span data-ttu-id="d74b6-197">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-197">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="d74b6-198">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d74b6-198">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="d74b6-199">Les valeurs acceptables pour ce paramètre sont les suivantes : de **base** , **CredSSP** , **par défaut** , **Digest** , **Kerberos** et **Negotiate** .</span><span class="sxs-lookup"><span data-stu-id="d74b6-199">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate** .</span></span>

<span data-ttu-id="d74b6-200">Pour plus d’informations, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="d74b6-200">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="d74b6-201">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="d74b6-201">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="d74b6-202">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="d74b6-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="d74b6-203">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="d74b6-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d74b6-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d74b6-204">-Confirm</span></span>

<span data-ttu-id="d74b6-205">Vous invite à confirmer l’exécution `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="d74b6-205">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="d74b6-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d74b6-206">-WhatIf</span></span>

<span data-ttu-id="d74b6-207">Montre ce qui se passerait si le `Restart-Computer` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d74b6-207">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="d74b6-208">L' `Restart-Computer` applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d74b6-208">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d74b6-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d74b6-209">CommonParameters</span></span>

<span data-ttu-id="d74b6-210">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d74b6-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d74b6-211">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d74b6-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d74b6-212">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d74b6-212">INPUTS</span></span>

### <span data-ttu-id="d74b6-213">System.String</span><span class="sxs-lookup"><span data-stu-id="d74b6-213">System.String</span></span>

<span data-ttu-id="d74b6-214">`Restart-Computer` accepte les noms d’ordinateur à partir du ou des variables.</span><span class="sxs-lookup"><span data-stu-id="d74b6-214">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

## <span data-ttu-id="d74b6-215">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d74b6-215">OUTPUTS</span></span>

### <span data-ttu-id="d74b6-216">Aucun</span><span class="sxs-lookup"><span data-stu-id="d74b6-216">None</span></span>

<span data-ttu-id="d74b6-217">`Restart-Computer` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d74b6-217">`Restart-Computer` doesn't generate any output.</span></span>

## <span data-ttu-id="d74b6-218">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d74b6-218">NOTES</span></span>

- <span data-ttu-id="d74b6-219">Dans Windows, `Restart-Computer` utilise la [méthode Win32Shutdown](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) de la classe [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="d74b6-219">In Windows, `Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span> <span data-ttu-id="d74b6-220">Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d74b6-220">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>
- <span data-ttu-id="d74b6-221">Sur Linux et Mac OS, `Restart-Computer` utilise l' `/sbin/shutdown` outil bash.</span><span class="sxs-lookup"><span data-stu-id="d74b6-221">On Linux and Mac OS, `Restart-Computer` uses the `/sbin/shutdown` bash tool.</span></span>

## <span data-ttu-id="d74b6-222">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d74b6-222">RELATED LINKS</span></span>

[<span data-ttu-id="d74b6-223">À propos de Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="d74b6-223">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="d74b6-224">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d74b6-224">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="d74b6-225">Protocole Gestion des services web</span><span class="sxs-lookup"><span data-stu-id="d74b6-225">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
