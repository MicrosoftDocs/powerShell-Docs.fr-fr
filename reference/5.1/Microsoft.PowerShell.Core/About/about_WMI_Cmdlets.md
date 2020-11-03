---
description: Fournit des informations générales sur Windows Management Instrumentation (WMI) et Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207882"
---
# <a name="about-wmi-cmdlets"></a><span data-ttu-id="ec637-104">À propos des applets de commande WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-104">About WMI Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="ec637-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="ec637-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="ec637-106">Fournit des informations générales sur Windows Management Instrumentation (WMI) et Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec637-106">Provides background information about Windows Management Instrumentation (WMI) and Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ec637-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="ec637-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ec637-108">Cette rubrique fournit des informations sur la technologie WMI, les applets de commande WMI pour Windows PowerShell, la communication à distance basée sur WMI, les accélérateurs WMI et la résolution des problèmes WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-108">This topic provides information about WMI technology, the WMI cmdlets for Windows PowerShell, WMI-based remoting, WMI accelerators, and WMI troubleshooting.</span></span> <span data-ttu-id="ec637-109">Elle propose également des liens vers d'autres informations sur WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-109">This topic also provides links to more information about WMI.</span></span>

### <a name="about-wmi"></a><span data-ttu-id="ec637-110">À PROPOS DE WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-110">ABOUT WMI</span></span>

<span data-ttu-id="ec637-111">WMI est l’implémentation Microsoft de WBEM (Web-Based Enterprise Management), qui est une initiative de l’industrie pour développer une technologie standard permettant d’accéder aux informations de gestion dans un environnement d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ec637-111">Windows Management Instrumentation (WMI) is the Microsoft implementation of Web-Based Enterprise Management (WBEM), which is an industry initiative to develop a standard technology for accessing management information in an enterprise environment.</span></span> <span data-ttu-id="ec637-112">WMI utilise la norme industrielle CIM (Common Information Model) pour représenter les systèmes, applications, réseaux, périphériques et autres composants managés.</span><span class="sxs-lookup"><span data-stu-id="ec637-112">WMI uses the Common Information Model (CIM) industry standard to represent systems, applications, networks, devices, and other managed components.</span></span> <span data-ttu-id="ec637-113">La norme CIM est développée et gérée par Distributed Management Task Force (DMTF).</span><span class="sxs-lookup"><span data-stu-id="ec637-113">CIM is developed and maintained by the Distributed Management Task Force (DMTF).</span></span> <span data-ttu-id="ec637-114">Vous pouvez utiliser WMI pour gérer les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="ec637-114">You can use WMI to manage both local and remote computers.</span></span> <span data-ttu-id="ec637-115">Par exemple, vous pouvez utiliser WMI pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec637-115">For example, you can use WMI to do the following:</span></span>

- <span data-ttu-id="ec637-116">Démarrez un processus sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-116">Start a process on a remote computer.</span></span>
- <span data-ttu-id="ec637-117">Redémarrez un ordinateur à distance.</span><span class="sxs-lookup"><span data-stu-id="ec637-117">Restart a computer remotely.</span></span>
- <span data-ttu-id="ec637-118">Obtenir la liste des applications installées sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-118">Get a list of the applications that are installed on a local or remote computer.</span></span>
- <span data-ttu-id="ec637-119">Interrogez les journaux des événements Windows sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-119">Query the Windows event logs on a local or remote computer.</span></span>

### <a name="the-wmi-cmdlets-for-windows-powershell"></a><span data-ttu-id="ec637-120">APPLETS DE COMMANDE WMI POUR WINDOWS POWERSHELL</span><span class="sxs-lookup"><span data-stu-id="ec637-120">THE WMI CMDLETS FOR WINDOWS POWERSHELL</span></span>

<span data-ttu-id="ec637-121">Windows PowerShell implémente les fonctionnalités WMI via un ensemble d’applets de commande qui sont disponibles dans Windows PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="ec637-121">Windows PowerShell implements WMI functionality through a set of cmdlets that are available in Windows PowerShell by default.</span></span> <span data-ttu-id="ec637-122">Vous pouvez utiliser ces applets de commande pour effectuer les tâches de bout en bout nécessaires à la gestion des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="ec637-122">You can use these cmdlets to complete the end-to-end tasks necessary to manage local and remote computers.</span></span>

<span data-ttu-id="ec637-123">Les applets de commande WMI suivantes sont incluses.</span><span class="sxs-lookup"><span data-stu-id="ec637-123">The following WMI cmdlets are included.</span></span>

|<span data-ttu-id="ec637-124">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="ec637-124">Cmdlet</span></span>           |<span data-ttu-id="ec637-125">Description</span><span class="sxs-lookup"><span data-stu-id="ec637-125">Description</span></span>                                   |
|-----------------|----------------------------------------------|
|<span data-ttu-id="ec637-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ec637-126">Get-WmiObject</span></span>    |<span data-ttu-id="ec637-127">Obtient des instances de classes ou d’informations WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-127">Gets instances of WMI classes or information</span></span>  |
|                 |<span data-ttu-id="ec637-128">sur les classes disponibles.</span><span class="sxs-lookup"><span data-stu-id="ec637-128">about the available classes.</span></span>                  |
|<span data-ttu-id="ec637-129">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="ec637-129">Invoke-WmiMethod</span></span> |<span data-ttu-id="ec637-130">Appelle les méthodes WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-130">Calls WMI methods.</span></span>                            |
|<span data-ttu-id="ec637-131">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="ec637-131">Register-WmiEvent</span></span>|<span data-ttu-id="ec637-132">S’abonne à un événement WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-132">Subscribes to a WMI event.</span></span>                    |
|<span data-ttu-id="ec637-133">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ec637-133">Remove-WmiObject</span></span> |<span data-ttu-id="ec637-134">Supprime des instances et des classes WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-134">Deletes WMI classes and instances.</span></span>            |
|<span data-ttu-id="ec637-135">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="ec637-135">Set-WmiInstance</span></span>  |<span data-ttu-id="ec637-136">Crée ou modifie des instances de classes WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-136">Creates or modifies instances of WMI classes.</span></span> |

### <a name="sample-commands"></a><span data-ttu-id="ec637-137">EXEMPLES DE COMMANDES</span><span class="sxs-lookup"><span data-stu-id="ec637-137">SAMPLE COMMANDS</span></span>
<span data-ttu-id="ec637-138">La commande suivante affiche les informations du BIOS de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ec637-138">The following command displays the BIOS information for the local computer.</span></span>

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

<span data-ttu-id="ec637-139">La commande suivante affiche des informations sur le service WinRM pour trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ec637-139">The following command displays information about the WinRM service for three remote computers.</span></span>

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

<span data-ttu-id="ec637-140">La commande plus complexe suivante quitte toutes les instances d’un programme.</span><span class="sxs-lookup"><span data-stu-id="ec637-140">The following more complex command exits all instances of a program.</span></span>

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a><span data-ttu-id="ec637-141">COMMUNICATION À DISTANCE BASÉE SUR WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-141">WMI-BASED REMOTING</span></span>

<span data-ttu-id="ec637-142">Bien que la possibilité de gérer un système local via WMI soit utile, il s’agit des fonctionnalités de communication à distance qui rendent WMI un outil d’administration puissant.</span><span class="sxs-lookup"><span data-stu-id="ec637-142">While the ability to manage a local system through WMI is useful, it is the remoting capabilities that make WMI a powerful administrative tool.</span></span> <span data-ttu-id="ec637-143">WMI utilise le modèle DCOM (Distributed Component Object Model) de Microsoft pour se connecter aux systèmes et les gérer.</span><span class="sxs-lookup"><span data-stu-id="ec637-143">WMI uses Microsoft's Distributed Component Object Model (DCOM) to connect to and manage systems.</span></span> <span data-ttu-id="ec637-144">Vous devrez peut-être configurer certains systèmes pour autoriser les connexions DCOM.</span><span class="sxs-lookup"><span data-stu-id="ec637-144">You might have to configure some systems to allow DCOM connections.</span></span>
<span data-ttu-id="ec637-145">Les paramètres de pare-feu et les autorisations DCOM verrouillées peuvent bloquer la capacité de WMI à gérer à distance les systèmes.</span><span class="sxs-lookup"><span data-stu-id="ec637-145">Firewall settings and locked-down DCOM permissions can block WMI's ability to remotely manage systems.</span></span>

### <a name="wmi-type-accelerators"></a><span data-ttu-id="ec637-146">ACCÉLÉRATEURS DE TYPE WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-146">WMI TYPE ACCELERATORS</span></span>

<span data-ttu-id="ec637-147">Windows PowerShell comprend des accélérateurs de type WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-147">Windows PowerShell includes WMI type accelerators.</span></span> <span data-ttu-id="ec637-148">Ces accélérateurs de type WMI (raccourcis) permettent un accès plus direct à un objet WMI qu’une approche d’accélérateur sans type.</span><span class="sxs-lookup"><span data-stu-id="ec637-148">These WMI type accelerators (shortcuts) allow more direct access to a WMI objects than a non-type accelerator approach would allow.</span></span>

<span data-ttu-id="ec637-149">Les accélérateurs de type suivants sont pris en charge avec WMI :</span><span class="sxs-lookup"><span data-stu-id="ec637-149">The following type accelerators are supported with WMI:</span></span>

<span data-ttu-id="ec637-150">[WMISEARCHER]-raccourci pour la recherche d’objets WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-150">[WMISEARCHER] - A shortcut for searching for WMI objects.</span></span>

<span data-ttu-id="ec637-151">[WMICLASS]-raccourci pour accéder aux propriétés et méthodes statiques d’une classe.</span><span class="sxs-lookup"><span data-stu-id="ec637-151">[WMICLASS] - A shortcut for accessing the static properties and methods of a class.</span></span>

<span data-ttu-id="ec637-152">[WMI]-raccourci pour obtenir une instance unique d’une classe.</span><span class="sxs-lookup"><span data-stu-id="ec637-152">[WMI] - A shortcut for getting a single instance of a class.</span></span>

<span data-ttu-id="ec637-153">[WMISEARCHER] est un accélérateur de type pour un ManagementObjectSearcher.</span><span class="sxs-lookup"><span data-stu-id="ec637-153">[WMISEARCHER] is a type accelerator for a ManagementObjectSearcher.</span></span> <span data-ttu-id="ec637-154">Un constructeur de chaîne peut être utilisé pour créer un programme de recherche dans lequel vous pouvez ensuite effectuer une opération d’extraction () sur.</span><span class="sxs-lookup"><span data-stu-id="ec637-154">It can take a string constructor to create a searcher that you can then do a GET() on.</span></span>

<span data-ttu-id="ec637-155">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ec637-155">For example:</span></span>

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

<span data-ttu-id="ec637-156">[WMICLASS] est un accélérateur de type pour ManagementClass.</span><span class="sxs-lookup"><span data-stu-id="ec637-156">[WMICLASS] is a type accelerator for ManagementClass.</span></span> <span data-ttu-id="ec637-157">Il a un constructeur de chaîne qui prend un chemin d’accès WMI local ou absolu à une classe WMI et retourne un objet lié à cette classe.</span><span class="sxs-lookup"><span data-stu-id="ec637-157">This has a string constructor that takes a local or absolute WMI path to a WMI class and returns an object that is bound to that class.</span></span>

<span data-ttu-id="ec637-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ec637-158">For example:</span></span>

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

<span data-ttu-id="ec637-159">[WMI] est un accélérateur de type pour ManagementObject.</span><span class="sxs-lookup"><span data-stu-id="ec637-159">[WMI] is a type accelerator for ManagementObject.</span></span> <span data-ttu-id="ec637-160">Il a un constructeur de chaîne qui prend un chemin d’accès WMI local ou absolu à une instance WMI et retourne un objet lié à cette instance.</span><span class="sxs-lookup"><span data-stu-id="ec637-160">This has a string constructor that takes a local or absolute WMI path to a WMI instance and returns an object that is bound to that instance.</span></span>

<span data-ttu-id="ec637-161">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ec637-161">For example:</span></span>

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a><span data-ttu-id="ec637-162">RÉSOLUTION DES PROBLÈMES WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-162">WMI TROUBLESHOOTING</span></span>

<span data-ttu-id="ec637-163">Les problèmes suivants sont les problèmes les plus courants qui peuvent se produire lorsque vous essayez de vous connecter à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-163">The following problems are the most common problems that might occur when you try to connect to a remote computer.</span></span>

<span data-ttu-id="ec637-164">Problème 1 : l’ordinateur distant n’est pas en ligne.</span><span class="sxs-lookup"><span data-stu-id="ec637-164">Problem 1: The remote computer is not online.</span></span>

<span data-ttu-id="ec637-165">Si un ordinateur est hors connexion, vous ne pourrez pas vous y connecter à l’aide de WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-165">If a computer is offline, you will not be able to connect to it by using WMI.</span></span>
<span data-ttu-id="ec637-166">Vous pouvez recevoir le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="ec637-166">You may receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

<span data-ttu-id="ec637-167">Si vous recevez ce message d’erreur, vérifiez que l’ordinateur est en ligne.</span><span class="sxs-lookup"><span data-stu-id="ec637-167">If you receive this error message, verify that the computer is online.</span></span> <span data-ttu-id="ec637-168">Essayez d’exécuter une commande ping sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-168">Try to ping the remote computer.</span></span>

<span data-ttu-id="ec637-169">Problème 2 : vous ne disposez pas de droits d’administrateur local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-169">Problem 2: You do not have local administrator rights on the remote computer.</span></span>

<span data-ttu-id="ec637-170">Pour utiliser WMI à distance, vous devez disposer de droits d’administrateur local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-170">To use WMI remotely, you must have local administrator rights on the remote computer.</span></span> <span data-ttu-id="ec637-171">Si vous ne le faites pas, l’accès à cet ordinateur sera refusé.</span><span class="sxs-lookup"><span data-stu-id="ec637-171">If you do not, access to that computer will be denied.</span></span>

<span data-ttu-id="ec637-172">Pour vérifier la sécurité de l’espace de noms :</span><span class="sxs-lookup"><span data-stu-id="ec637-172">To verify namespace security:</span></span>

1. <span data-ttu-id="ec637-173">Cliquez sur Démarrer, cliquez avec le bouton droit sur Poste de travail, puis cliquez sur gérer.</span><span class="sxs-lookup"><span data-stu-id="ec637-173">Click Start, right-click My Computer, and then click Manage.</span></span>
2. <span data-ttu-id="ec637-174">Dans gestion de l’ordinateur, développez Services et applications, cliquez avec le bouton droit sur contrôle WMI, puis cliquez sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="ec637-174">In Computer Management, expand Services and Applications, right-click WMI Control, and then click Properties.</span></span>
3. <span data-ttu-id="ec637-175">Dans la boîte de dialogue Propriétés du contrôle WMI, cliquez sur l’onglet sécurité.</span><span class="sxs-lookup"><span data-stu-id="ec637-175">In the WMI Control Properties dialog box, click  the Security tab.</span></span>

<span data-ttu-id="ec637-176">Problème 3 : un pare-feu bloque l’accès à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec637-176">Problem 3: A firewall is blocking access to the remote computer.</span></span>

<span data-ttu-id="ec637-177">WMI utilise les protocoles DCOM (Distributed COM) et RPC (Remote Procedure Call) pour traverser le réseau.</span><span class="sxs-lookup"><span data-stu-id="ec637-177">WMI uses the DCOM (Distributed COM) and RPC (Remote Procedure Call) protocols to traverse the network.</span></span> <span data-ttu-id="ec637-178">Par défaut, de nombreux pare-feu bloquent le trafic DCOM et RPC.</span><span class="sxs-lookup"><span data-stu-id="ec637-178">By default, many firewalls block DCOM and RPC traffic.</span></span> <span data-ttu-id="ec637-179">Si votre pare-feu bloque ces protocoles, votre connexion échouera.</span><span class="sxs-lookup"><span data-stu-id="ec637-179">If your firewall is blocking these protocols, your connection will fail.</span></span> <span data-ttu-id="ec637-180">Par exemple, le pare-feu Windows dans Microsoft Windows XP Service Pack 2 est configuré pour bloquer automatiquement tout le trafic réseau non sollicité, y compris DCOM et WMI.</span><span class="sxs-lookup"><span data-stu-id="ec637-180">For example, Windows Firewall in Microsoft Windows XP Service Pack 2 is configured to automatically block all unsolicited network traffic, including DCOM and WMI.</span></span> <span data-ttu-id="ec637-181">Dans sa configuration par défaut, le pare-feu Windows rejette une demande WMI entrante et vous recevez le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="ec637-181">In its default configuration, Windows Firewall rejects an incoming WMI request, and you receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a><span data-ttu-id="ec637-182">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="ec637-182">SEE ALSO</span></span>

[<span data-ttu-id="ec637-183">À propos de WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-183">About WMI</span></span>](/windows/win32/wmisdk/about-wmi)

[<span data-ttu-id="ec637-184">Résolution des problèmes WMI</span><span class="sxs-lookup"><span data-stu-id="ec637-184">WMI Troubleshooting</span></span>](/windows/win32/wmisdk/wmi-troubleshooting)

[<span data-ttu-id="ec637-185">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ec637-185">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="ec637-186">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="ec637-186">Invoke-WmiMethod</span></span>](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[<span data-ttu-id="ec637-187">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="ec637-187">Register-WmiEvent</span></span>](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[<span data-ttu-id="ec637-188">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ec637-188">Remove-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[<span data-ttu-id="ec637-189">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="ec637-189">Set-WmiInstance</span></span>](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
