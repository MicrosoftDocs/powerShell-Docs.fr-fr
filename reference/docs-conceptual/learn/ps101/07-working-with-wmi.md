---
title: Utilisation de WMI
description: PowerShell comprend depuis toujours des applets de commande pour l’utilisation de WMI.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438290"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="b2197-103">Chapitre 7 - Utilisation de WMI</span><span class="sxs-lookup"><span data-stu-id="b2197-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="b2197-104">WMI et CIM</span><span class="sxs-lookup"><span data-stu-id="b2197-104">WMI and CIM</span></span>

<span data-ttu-id="b2197-105">Par défaut, PowerShell est fourni avec des applets de commande permettant d’utiliser d’autres technologies telles que Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="b2197-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="b2197-106">Il existe plusieurs applets de commande WMI natives dans PowerShell. Il n’est donc pas nécessaire d’installer d’autres logiciels ou modules.</span><span class="sxs-lookup"><span data-stu-id="b2197-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="b2197-107">PowerShell comprend depuis toujours des applets de commande pour l’utilisation de WMI.</span><span class="sxs-lookup"><span data-stu-id="b2197-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="b2197-108">Vous pouvez utiliser `Get-Command` pour connaître les applets de commande WMI qui existent dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2197-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="b2197-109">Les résultats suivants proviennent de mon ordinateur Windows 10 Lab Environment sur lequel j’exécute PowerShell version 5.1.</span><span class="sxs-lookup"><span data-stu-id="b2197-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="b2197-110">Vos résultats peuvent différer selon la version de PowerShell que vous exécutez.</span><span class="sxs-lookup"><span data-stu-id="b2197-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="b2197-111">Les applets de commande CIM (Common Information Model) datent de la version 3.0 de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2197-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="b2197-112">Les applets de commande CIM sont conçues pour être utilisées sur des ordinateurs Windows et non Windows.</span><span class="sxs-lookup"><span data-stu-id="b2197-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="b2197-113">Les applets de commande WMI sont aujourd’hui dépréciées, c’est pourquoi je vous recommande d’utiliser les applets de commande CIM à la place des anciennes WMI.</span><span class="sxs-lookup"><span data-stu-id="b2197-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="b2197-114">Les applets de commande CIM sont toutes contenues dans un module.</span><span class="sxs-lookup"><span data-stu-id="b2197-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="b2197-115">Pour obtenir la liste des applets de commande CIM, utilisez `Get-Command` avec le paramètre **Module**, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b2197-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="b2197-116">Les applets de commande CIM vous permettent toujours d’utiliser WMI. Ne soyez donc pas surpris si vous entendez quelqu’un dire : « Quand j’interroge WMI avec les applets de commande CIM PowerShell... »</span><span class="sxs-lookup"><span data-stu-id="b2197-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="b2197-117">Comme je l’ai déjà mentionné, WMI est une technologie distincte de PowerShell. Les applets de commande CIM vous permettent simplement d’accéder à WMI.</span><span class="sxs-lookup"><span data-stu-id="b2197-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="b2197-118">Vous pouvez tomber sur un ancien VBScript qui utilise le langage de requêtes WMI (WQL) pour interroger WMI, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b2197-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="b2197-119">Vous pouvez exécuter la requête WQL à partir de ce VBScript et l’utiliser avec l’applet de commande `Get-CimInstance` sans aucune modification.</span><span class="sxs-lookup"><span data-stu-id="b2197-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="b2197-120">Ce n’est pas comme ça que je m’y prends généralement pour interroger WMI avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2197-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="b2197-121">Cela dit, cette méthode fonctionne et elle vous permet d’effectuer facilement la migration des scripts VBScript existants vers PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2197-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="b2197-122">Lorsque je commence à écrire une ligne de code pour interroger WMI, j’utilise la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="b2197-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="b2197-123">Si je veux uniquement le numéro de série, je peux rediriger la sortie vers `Select-Object` et spécifier uniquement la propriété **SerialNumber**.</span><span class="sxs-lookup"><span data-stu-id="b2197-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="b2197-124">Par défaut, plusieurs propriétés sont récupérées en arrière-plan et ne sont jamais utilisées.</span><span class="sxs-lookup"><span data-stu-id="b2197-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="b2197-125">Cela peut ne pas avoir d’importance lorsque vous interrogez WMI sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b2197-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="b2197-126">Toutefois, une fois que vous commencez à interroger des ordinateurs distants, non seulement vous utilisez du temps de traitement supplémentaire pour obtenir les informations dont vous avez besoin, mais en plus, vous récupérez sur le réseau d’autres informations dont vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="b2197-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="b2197-127">`Get-CimInstance` a un paramètre **Property** qui limite la quantité d’informations récupérées.</span><span class="sxs-lookup"><span data-stu-id="b2197-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="b2197-128">Cela rend l’interrogation de WMI plus efficace.</span><span class="sxs-lookup"><span data-stu-id="b2197-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="b2197-129">Les résultats précédents ont retourné un objet.</span><span class="sxs-lookup"><span data-stu-id="b2197-129">The previous results returned an object.</span></span> <span data-ttu-id="b2197-130">Pour retourner une chaîne simple, utilisez le paramètre **ExpandProperty**.</span><span class="sxs-lookup"><span data-stu-id="b2197-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="b2197-131">Vous pouvez également utiliser le style de syntaxe en pointillés pour retourner une chaîne simple.</span><span class="sxs-lookup"><span data-stu-id="b2197-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="b2197-132">Cela vous évite d’avoir à rediriger les données vers `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="b2197-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="b2197-133">Interroger des ordinateurs distants avec les applets de commande CIM</span><span class="sxs-lookup"><span data-stu-id="b2197-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="b2197-134">J’exécute toujours PowerShell en tant qu’administrateur local et utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="b2197-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="b2197-135">Lorsque j’essaie d’interroger des informations à partir d’un ordinateur distant à l’aide de l’applet de commande `Get-CimInstance`, je reçois un message d’erreur de type Accès refusé.</span><span class="sxs-lookup"><span data-stu-id="b2197-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="b2197-136">De nombreux utilisateurs de PowerShell ont des inquiétudes quant à la sécurité. Pourtant, les autorisations PowerShell sont exactement les mêmes que celles de l’interface graphique utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b2197-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="b2197-137">Exactement les mêmes.</span><span class="sxs-lookup"><span data-stu-id="b2197-137">No more and no less.</span></span> <span data-ttu-id="b2197-138">Dans l’exemple précédent, le problème vient du fait que l’utilisateur qui exécute PowerShell ne dispose pas des droits nécessaires pour interroger les informations WMI à partir du serveur DC01.</span><span class="sxs-lookup"><span data-stu-id="b2197-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="b2197-139">Je pourrais relancer PowerShell en tant qu’administrateur de domaine, puisque `Get-CimInstance` n’a pas de paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="b2197-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="b2197-140">Cela dit, ce n’est vraiment pas une bonne idée, car cela signifierait que tout ce que j’exécute à partir de PowerShell le serait en tant qu’administrateur de domaine. Et selon la situation, cela pourrait engendrer d’importants risques de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b2197-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="b2197-141">Si j’utilise le principe du « privilège minimum », je peux appliquer les privilèges de mon compte d’administrateur de domaine au niveau d’une seule commande, à l’aide du paramètre **Credential**, si la commande dispose de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="b2197-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="b2197-142">`Get-CimInstance` n’a pas de paramètre **Credential**. Dans ce scénario, la solution consiste donc à créer d’abord un **CimSession**.</span><span class="sxs-lookup"><span data-stu-id="b2197-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="b2197-143">J’utilise ensuite **CimSession** à la place d’un nom d’ordinateur pour interroger WMI sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b2197-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="b2197-144">La session CIM a été stockée dans une variable nommée `$CimSession`.</span><span class="sxs-lookup"><span data-stu-id="b2197-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="b2197-145">Notez que j’ai également spécifié l’applet de commande `Get-Credential` entre parenthèses pour qu’elle s’exécute en premier, en m’invitant à fournir d’autres informations d’identification avant de créer la nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="b2197-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="b2197-146">Plus loin dans ce chapitre, je vous montrerai une méthode plus efficace pour spécifier d’autres informations d’identification. Toutefois, il est important de comprendre ce concept de base avant qu’il ne devienne plus complexe.</span><span class="sxs-lookup"><span data-stu-id="b2197-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="b2197-147">La session CIM créée dans l’exemple précédent peut désormais être utilisée avec l’applet de commande `Get-CimInstance` pour interroger les informations du BIOS à partir de WMI sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b2197-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="b2197-148">L’utilisation des sessions CIM présente plusieurs avantages par rapport au simple fait de spécifier un nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2197-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="b2197-149">Lorsque vous exécutez plusieurs requêtes sur un même ordinateur, l’utilisation d’une session CIM est plus efficace que le fait d’utiliser le nom de l’ordinateur pour chaque requête.</span><span class="sxs-lookup"><span data-stu-id="b2197-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="b2197-150">La création d’une session CIM ne configure la connexion qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="b2197-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="b2197-151">Ensuite, plusieurs requêtes utilisent cette même session pour récupérer des informations.</span><span class="sxs-lookup"><span data-stu-id="b2197-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="b2197-152">L’utilisation du nom de l’ordinateur nécessite que les applets de commande configurent et suppriment la connexion pour chaque requête.</span><span class="sxs-lookup"><span data-stu-id="b2197-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="b2197-153">L’applet de commande `Get-CimInstance` utilise le protocole WSMan par défaut, ce qui signifie que l’ordinateur distant a besoin de PowerShell version 3.0 ou ultérieure pour se connecter.</span><span class="sxs-lookup"><span data-stu-id="b2197-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="b2197-154">En fait, ce n’est pas la version de PowerShell qui importe, mais la version de la pile.</span><span class="sxs-lookup"><span data-stu-id="b2197-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="b2197-155">Pour connaître la version de la pile, utilisez l’applet de commande `Test-WSMan`.</span><span class="sxs-lookup"><span data-stu-id="b2197-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="b2197-156">Il doit s’agir de la version 3.0.</span><span class="sxs-lookup"><span data-stu-id="b2197-156">It needs to be version 3.0.</span></span> <span data-ttu-id="b2197-157">Il s’agit de la version que vous trouverez avec PowerShell version 3.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="b2197-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="b2197-158">Les anciennes applets de commande WMI utilisent le protocole DCOM, qui est compatible avec les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="b2197-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="b2197-159">Toutefois, DCOM est généralement bloqué par le Pare-feu sur les versions récentes de Windows.</span><span class="sxs-lookup"><span data-stu-id="b2197-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="b2197-160">L’applet de commande `New-CimSessionOption` vous permet de créer une connexion via le protocole DCOM, en vue de l’utiliser avec `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="b2197-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="b2197-161">Cela vous permet d’utiliser l’applet de commande `Get-CimInstance` pour communiquer avec les versions de Windows antérieures à Windows Server 2000.</span><span class="sxs-lookup"><span data-stu-id="b2197-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="b2197-162">Cela signifie également que PowerShell n’est pas nécessaire sur l’ordinateur distant lorsque vous utilisez l’applet de commande `Get-CimInstance` avec un CimSession qui est configuré pour utiliser le protocole DCOM.</span><span class="sxs-lookup"><span data-stu-id="b2197-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="b2197-163">Créez l’option de protocole DCOM à l’aide de l’applet de commande `New-CimSessionOption` et stockez-la dans une variable.</span><span class="sxs-lookup"><span data-stu-id="b2197-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="b2197-164">Pour plus d’efficacité, vous pouvez stocker vos informations d’identification d’administrateur de domaine (ou avec privilèges élevés) dans une variable afin de ne pas avoir à les entrer pour chaque commande.</span><span class="sxs-lookup"><span data-stu-id="b2197-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="b2197-165">J’ai un serveur nommé SQL03 qui exécute Windows Server 2008 (non R2).</span><span class="sxs-lookup"><span data-stu-id="b2197-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="b2197-166">Il s’agit du plus récent des systèmes d’exploitation Windows Server sur lesquels PowerShell n’est pas installé par défaut.</span><span class="sxs-lookup"><span data-stu-id="b2197-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="b2197-167">Créez un **CimSession** pour SQL03 en utilisant le protocole DCOM.</span><span class="sxs-lookup"><span data-stu-id="b2197-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="b2197-168">Notez que cette fois-ci, dans la commande précédente, j’ai spécifié la variable nommée `$Cred` comme la valeur du paramètre **Credential**, afin de ne pas avoir à entrer les informations d’identification manuellement une nouvelle fois.</span><span class="sxs-lookup"><span data-stu-id="b2197-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="b2197-169">La sortie de la requête est la même, quel que soit le protocole sous-jacent utilisé.</span><span class="sxs-lookup"><span data-stu-id="b2197-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="b2197-170">L’applet de commande `Get-CimSession` est utilisée pour voir quels **CimSessions** sont actuellement connectés et quels protocoles ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="b2197-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="b2197-171">Récupérez puis stockez les deux **CimSessions** créés précédemment dans une variable nommée `$CimSession`.</span><span class="sxs-lookup"><span data-stu-id="b2197-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="b2197-172">Interrogez les deux ordinateurs à l’aide d’une seule commande, l’une utilisant le protocole WSMan et l’autre utilisant le protocole DCOM.</span><span class="sxs-lookup"><span data-stu-id="b2197-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="b2197-173">J’ai écrit de nombreux articles de blog sur les applets de commande WMI et CIM.</span><span class="sxs-lookup"><span data-stu-id="b2197-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="b2197-174">L’un des plus utiles concerne une fonction que j’ai créée pour déterminer automatiquement quel protocole utiliser entre WSMan et DCOM, et pour configurer la session CIM automatiquement et non manuellement.</span><span class="sxs-lookup"><span data-stu-id="b2197-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="b2197-175">Cet article de blog est intitulé [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span><span class="sxs-lookup"><span data-stu-id="b2197-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="b2197-176">Lorsque vous avez terminé une session CIM, vous devez la supprimer avec l’applet de commande `Remove-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="b2197-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="b2197-177">Pour supprimer toutes les sessions CIM, il suffit de rediriger `Get-CimSession` vers `Remove-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="b2197-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="b2197-178">Résumé</span><span class="sxs-lookup"><span data-stu-id="b2197-178">Summary</span></span>

<span data-ttu-id="b2197-179">Dans ce chapitre, vous avez vu comment vous servir de PowerShell pour utiliser WMI sur des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="b2197-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="b2197-180">Vous avez également vu comment utiliser les applets de commande CIM pour travailler sur des ordinateurs distants avec le protocole WSMan ou DCOM.</span><span class="sxs-lookup"><span data-stu-id="b2197-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="b2197-181">Révision</span><span class="sxs-lookup"><span data-stu-id="b2197-181">Review</span></span>

1. <span data-ttu-id="b2197-182">Quelle est la différence entre les applets de commande WMI et les applets de commande CIM ?</span><span class="sxs-lookup"><span data-stu-id="b2197-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="b2197-183">Par défaut, quel protocole l’applet de commande `Get-CimInstance` utilise-t-elle ?</span><span class="sxs-lookup"><span data-stu-id="b2197-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="b2197-184">Quels sont les avantages de l’utilisation d’une session CIM par rapport à la spécification d’un nom d’ordinateur avec `Get-CimInstance` ?</span><span class="sxs-lookup"><span data-stu-id="b2197-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="b2197-185">Comment spécifier un protocole autre que celui par défaut avec `Get-CimInstance` ?</span><span class="sxs-lookup"><span data-stu-id="b2197-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="b2197-186">Comment fermer ou supprimer des sessions CIM ?</span><span class="sxs-lookup"><span data-stu-id="b2197-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="b2197-187">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="b2197-187">Recommended Reading</span></span>

- <span data-ttu-id="b2197-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="b2197-188">[about_WMI][]</span></span>
- <span data-ttu-id="b2197-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="b2197-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="b2197-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="b2197-190">[about_WQL][]</span></span>
- <span data-ttu-id="b2197-191">[Module CimCmdlets][]</span><span class="sxs-lookup"><span data-stu-id="b2197-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="b2197-192">[Vidéo : Utilisation des applets de commande CIM et des sessions CIM][]</span><span class="sxs-lookup"><span data-stu-id="b2197-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[Module CimCmdlets]: /powershell/module/cimcmdlets/
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[Vidéo : Utilisation des applets de commande CIM et des sessions CIM]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
