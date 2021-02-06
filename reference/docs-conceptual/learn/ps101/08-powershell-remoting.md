---
title: Communication à distance PowerShell
description: Il existe de nombreuses façons différentes d’exécuter des commandes sur des ordinateurs distants dans PowerShell.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0e467a41282b261c56a89578dbc841725f59a6e0
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598143"
---
# <a name="chapter-8---powershell-remoting"></a><span data-ttu-id="9ca93-103">Chapitre 8 - Communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ca93-103">Chapter 8 - PowerShell remoting</span></span>

<span data-ttu-id="9ca93-104">PowerShell propose de nombreuses façons différentes d’exécuter des commandes sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="9ca93-104">PowerShell has many different ways to run commands against remote computers.</span></span> <span data-ttu-id="9ca93-105">Dans le dernier chapitre, vous avez vu comment interroger à distance WMI à l’aide des applets de commande CIM.</span><span class="sxs-lookup"><span data-stu-id="9ca93-105">In the last chapter, you saw how to remotely query WMI using the CIM cmdlets.</span></span> <span data-ttu-id="9ca93-106">PowerShell comprend également plusieurs applets de commande avec un paramètre **ComputerName** intégré.</span><span class="sxs-lookup"><span data-stu-id="9ca93-106">PowerShell also includes several cmdlets that have a built-in **ComputerName** parameter.</span></span>

<span data-ttu-id="9ca93-107">Comme indiqué dans l’exemple suivant, `Get-Command` peut être utilisée avec le paramètre **ParameterName** pour déterminer les commandes qui ont un paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="9ca93-107">As shown in the following example, `Get-Command` can be used with the **ParameterName** parameter to determine what commands have a **ComputerName** parameter.</span></span>

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

<span data-ttu-id="9ca93-108">Les commandes comme `Get-Process` et `Get-Hotfix` ont un paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="9ca93-108">Commands such as `Get-Process` and `Get-Hotfix` have a **ComputerName** parameter.</span></span> <span data-ttu-id="9ca93-109">L’exécution de commandes sur des ordinateurs distants n’est pas une solution à long terme retenue par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ca93-109">This isn't the long-term direction that Microsoft is heading for running commands against remote computers.</span></span> <span data-ttu-id="9ca93-110">Même si vous trouvez une commande ayant un paramètre **ComputerName**, il est probable que vous deviez spécifier d’autres informations d’identification et qu’il n’y ait pas de paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="9ca93-110">Even if you find a command that has a **ComputerName** parameter, chances are that you'll need to specify alternate credentials and it won't have a **Credential** parameter.</span></span> <span data-ttu-id="9ca93-111">Si vous avez décidé d’exécuter PowerShell à partir d’un compte avec élévation de privilèges, un pare-feu entre vous et l’ordinateur distant peut bloquer la demande.</span><span class="sxs-lookup"><span data-stu-id="9ca93-111">And if you decided to run PowerShell from an elevated account, a firewall between you and the remote computer can block the request.</span></span>

<span data-ttu-id="9ca93-112">Pour utiliser les commandes de communication à distance PowerShell présentées dans ce chapitre, la communication à distance PowerShell doit être activée sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9ca93-112">To use the PowerShell remoting commands that are demonstrated in this chapter, PowerShell remoting must be enabled on the remote computer.</span></span> <span data-ttu-id="9ca93-113">Utilisez l’applet de commande `Enable-PSRemoting` pour activer la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ca93-113">Use the `Enable-PSRemoting` cmdlet to enable PowerShell remoting.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a><span data-ttu-id="9ca93-114">Communication à distance un-à-un</span><span class="sxs-lookup"><span data-stu-id="9ca93-114">One-To-One Remoting</span></span>

<span data-ttu-id="9ca93-115">Si vous voulez que votre session à distance soit interactive, la communication à distance un-à-un est ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="9ca93-115">If you want your remote session to be interactive, then one-to-one remoting is what you want.</span></span>
<span data-ttu-id="9ca93-116">Ce type de communication à distance est fourni par le biais de l’applet de commande `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-116">This type of remoting is provided via the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="9ca93-117">Dans le dernier chapitre, j’ai stocké mes informations d’identification d’administrateur de domaine dans une variable nommée `$Cred`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-117">In the last chapter, I stored my domain admin credentials in a variable named `$Cred`.</span></span> <span data-ttu-id="9ca93-118">Si vous ne l’avez pas déjà fait, continuez en stockant vos informations d’identification d’administrateur de domaine dans la variable `$Cred`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-118">If you haven't already done so, go ahead and store your domain admin credentials in the `$Cred` variable.</span></span>

<span data-ttu-id="9ca93-119">Cela vous permet d’entrer les informations d’identification une seule fois et de les utiliser pour chaque commande tant que votre session PowerShell actuelle est active.</span><span class="sxs-lookup"><span data-stu-id="9ca93-119">This allows you to enter the credentials once and use them on a per command basis as long as your current PowerShell session is active.</span></span>

```powershell
$Cred = Get-Credential
```

<span data-ttu-id="9ca93-120">Créez une session de communication à distance PowerShell un-à-un sur le contrôleur de domaine nommé dc01.</span><span class="sxs-lookup"><span data-stu-id="9ca93-120">Create a one-to-one PowerShell remoting session to the domain controller named dc01.</span></span>

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

<span data-ttu-id="9ca93-121">Notez que, dans l’exemple précédent, l’invite PowerShell est précédée de `[dc01]`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-121">Notice that in the previous example that the PowerShell prompt is preceded by `[dc01]`.</span></span> <span data-ttu-id="9ca93-122">Cela signifie que vous êtes dans une session PowerShell interactive sur l’ordinateur distant nommé dc01.</span><span class="sxs-lookup"><span data-stu-id="9ca93-122">This means you're in an interactive PowerShell session to the remote computer named dc01.</span></span> <span data-ttu-id="9ca93-123">Toutes les commandes que vous exécutez s’exécutent sur dc01, et non sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9ca93-123">Any commands you execute run on dc01, not on your local computer.</span></span> <span data-ttu-id="9ca93-124">De plus, n’oubliez pas que vous avez uniquement accès aux commandes PowerShell qui existent sur l’ordinateur distant, et pas à celles de votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9ca93-124">Also, keep in mind that you only have access to the PowerShell commands that exist on the remote computer and not the ones on your local computer.</span></span> <span data-ttu-id="9ca93-125">En d’autres termes, si vous avez installé des modules supplémentaires sur votre ordinateur, ces derniers ne sont pas accessibles sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9ca93-125">In other words, if you've installed additional modules on your computer, they aren't accessible on the remote computer.</span></span>

<span data-ttu-id="9ca93-126">Quand vous êtes connecté à un ordinateur distant par le biais d’une session de communication à distance PowerShell interactive un-à-un, vous vous trouvez en fait sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9ca93-126">When you're connected to a remote computer via a one-to-one interactive PowerShell remoting session, you're effectively sitting at the remote computer.</span></span> <span data-ttu-id="9ca93-127">Les objets sont des objets normaux tout comme ceux que vous utilisez dans l’ensemble de cette documentation.</span><span class="sxs-lookup"><span data-stu-id="9ca93-127">The objects are normal objects just like the ones you've been working with throughout this entire book.</span></span>

```powershell
[dc01]:  Get-Process | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
[dc01]:
```

<span data-ttu-id="9ca93-128">Quand vous avez terminé d’utiliser l’ordinateur distant, quittez la session de communication à distance un-à-un à l’aide de l’applet de commande `Exit-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-128">When you're done working with the remote computer, exit the one-to-one remoting session by using the `Exit-PSSession` cmdlet.</span></span>

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a><span data-ttu-id="9ca93-129">Communication à distance un-à-plusieurs</span><span class="sxs-lookup"><span data-stu-id="9ca93-129">One-To-Many Remoting</span></span>

<span data-ttu-id="9ca93-130">Vous pouvez parfois être amené à effectuer une tâche de manière interactive sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9ca93-130">Sometimes you may need to perform a task interactively on a remote computer.</span></span> <span data-ttu-id="9ca93-131">Mais la communication à distance est beaucoup plus puissante quand une tâche est exécutée simultanément sur plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="9ca93-131">But remoting is much more powerful when performing a task on multiple remote computers at the same time.</span></span> <span data-ttu-id="9ca93-132">Utilisez l’applet de commande `Invoke-Command` pour exécuter une commande sur un ou plusieurs ordinateurs distants en même temps.</span><span class="sxs-lookup"><span data-stu-id="9ca93-132">Use the `Invoke-Command` cmdlet to run a command against one or more remote computers at the same time.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="9ca93-133">Dans l’exemple précédent, trois serveurs ont été interrogés pour obtenir l’état du service de temps Windows.</span><span class="sxs-lookup"><span data-stu-id="9ca93-133">In the previous example, three servers were queried for the status of the Windows Time service.</span></span> <span data-ttu-id="9ca93-134">L’applet de commande `Get-Service` a été placée dans le bloc de script de `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-134">The `Get-Service` cmdlet was placed inside the script block of `Invoke-Command`.</span></span> <span data-ttu-id="9ca93-135">`Get-Service` s’exécute en fait sur l’ordinateur distant et les résultats sont retournés à votre ordinateur local sous la forme d’objets désérialisés.</span><span class="sxs-lookup"><span data-stu-id="9ca93-135">`Get-Service` actually runs on the remote computer and the results are returned to your local computer as deserialized objects.</span></span>

<span data-ttu-id="9ca93-136">La redirection de la commande précédente vers `Get-Member` indique que les résultats sont en effet des objets désérialisés.</span><span class="sxs-lookup"><span data-stu-id="9ca93-136">Piping the previous command to `Get-Member` shows that the results are indeed deserialized objects.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

<span data-ttu-id="9ca93-137">Notez que la majorité des méthodes sont manquantes sur les objets désérialisés.</span><span class="sxs-lookup"><span data-stu-id="9ca93-137">Notice that the majority of the methods are missing on deserialized objects.</span></span> <span data-ttu-id="9ca93-138">Cela signifie qu’il ne s’agit pas d’objets actifs ; ils sont inertes.</span><span class="sxs-lookup"><span data-stu-id="9ca93-138">This means they're not live objects; they're inert.</span></span> <span data-ttu-id="9ca93-139">Vous ne pouvez pas démarrer ou arrêter un service à l’aide d’un objet désérialisé, car il s’agit d’une capture instantanée de l’état de cet objet au moment où la commande s’est exécutée sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9ca93-139">You can't start or stop a service using a deserialized object because it's a snapshot of the state of that object the point when the command ran on the remote computer.</span></span>

<span data-ttu-id="9ca93-140">Cela ne signifie pas que vous ne pouvez pas démarrer ou arrêter un service à l’aide d’une méthode avec `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-140">That doesn't mean you can't start or stop a service using a method with `Invoke-Command` though.</span></span> <span data-ttu-id="9ca93-141">Cela signifie simplement que la méthode doit être appelée dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="9ca93-141">It just means that the method has to be called in the remote session.</span></span>

<span data-ttu-id="9ca93-142">Je vais arrêter le service de temps Windows sur ces trois serveurs distants à l’aide de la méthode **Stop()** pour en apporter la preuve.</span><span class="sxs-lookup"><span data-stu-id="9ca93-142">I'll stop the Windows Time service on all three of those remote servers using the **Stop()** method to prove this point.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="9ca93-143">Comme mentionné dans un chapitre précédent, s’il existe une applet de commande pour accomplir une tâche, je vous recommande de l’utiliser plutôt que d’utiliser une méthode.</span><span class="sxs-lookup"><span data-stu-id="9ca93-143">As mentioned in a previous chapter, if a cmdlet exists for accomplishing a task, I recommend using it instead of using a method.</span></span> <span data-ttu-id="9ca93-144">Dans le scénario précédent, je recommande l’utilisation de l’applet de commande `Stop-Service` au lieu de la méthode stop.</span><span class="sxs-lookup"><span data-stu-id="9ca93-144">In the previous scenario, I recommend using the `Stop-Service` cmdlet instead of the stop method.</span></span> <span data-ttu-id="9ca93-145">J’ai choisi d’utiliser la méthode **Stop()** pour prouver une chose, car de nombreuses personnes pensent à tort qu’il n’est pas possible d’appeler des méthodes lors de l’utilisation de la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ca93-145">I chose to use the **Stop()** method to prove a point since many people are under the misconception that methods can't be called when using PowerShell remoting.</span></span> <span data-ttu-id="9ca93-146">Elles ne peuvent pas être appelées sur l’objet qui est retourné car il est désérialisé, mais elles peuvent être appelées dans la session à distance elle-même.</span><span class="sxs-lookup"><span data-stu-id="9ca93-146">They can't be called on the object that's returned because it's deserialized, but they can be called in the remote session itself.</span></span>

## <a name="powershell-sessions"></a><span data-ttu-id="9ca93-147">Sessions PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ca93-147">PowerShell Sessions</span></span>

<span data-ttu-id="9ca93-148">Dans le dernier exemple de la section précédente, j’ai exécuté deux commandes à l’aide de l’applet de commande `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="9ca93-148">In the last example in the previous section, I ran two commands using the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="9ca93-149">Cela signifie que deux sessions distinctes devaient être configurées et désactivées pour exécuter ces deux commandes.</span><span class="sxs-lookup"><span data-stu-id="9ca93-149">That means two separate sessions had to be set up and torn down to run those two commands.</span></span>

<span data-ttu-id="9ca93-150">À l’instar des sessions CIM présentées dans le chapitre 7, une session PowerShell sur un ordinateur distant peut être utilisée pour exécuter plusieurs commandes sur l’ordinateur distant sans la surcharge d’une nouvelle session pour chaque commande individuelle.</span><span class="sxs-lookup"><span data-stu-id="9ca93-150">Similar to the CIM sessions discussed in Chapter 7, a PowerShell session to a remote computer can be used to run multiple commands against the remote computer without the overhead of a new session for each individual command.</span></span>

<span data-ttu-id="9ca93-151">Créez une session PowerShell sur chacun des trois ordinateurs avec lesquels nous travaillons dans ce chapitre : DC01, SQL02 et WEB01.</span><span class="sxs-lookup"><span data-stu-id="9ca93-151">Create a PowerShell session to each of the three computers we've been working with in this chapter, DC01, SQL02, and WEB01.</span></span>

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

<span data-ttu-id="9ca93-152">À présent, utilisez la variable nommée `$Session` pour démarrer le service de temps Windows à l’aide d’une méthode et vérifier l’état de ce service.</span><span class="sxs-lookup"><span data-stu-id="9ca93-152">Now use the variable named `$Session` to start the Windows Time service using a method and check the status of the service.</span></span>

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="9ca93-153">Une fois la session créée à l’aide d’autres informations d’identification, il n’est plus nécessaire de spécifier les informations d’identification à chaque exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="9ca93-153">Once the session is created using alternate credentials, it's no longer necessary to specify the credentials each time a command is run.</span></span>

<span data-ttu-id="9ca93-154">Une fois que vous avez terminé d’utiliser les sessions, veillez à les supprimer.</span><span class="sxs-lookup"><span data-stu-id="9ca93-154">When you're finished using the sessions, be sure to remove them.</span></span>

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a><span data-ttu-id="9ca93-155">Résumé</span><span class="sxs-lookup"><span data-stu-id="9ca93-155">Summary</span></span>

<span data-ttu-id="9ca93-156">Dans ce chapitre, vous avez appris à utiliser la communication à distance PowerShell, à exécuter des commandes dans une session interactive avec un ordinateur distant et à exécuter des commandes sur plusieurs ordinateurs à l’aide de la communication à distance un-à-plusieurs.</span><span class="sxs-lookup"><span data-stu-id="9ca93-156">In this chapter you've learned about PowerShell remoting, how to run commands in an interactive session with one remote computer, and how to run commands against multiple computers using one-to-many remoting.</span></span> <span data-ttu-id="9ca93-157">Vous avez également découvert les avantages de l’utilisation d’une session PowerShell lors de l’exécution de plusieurs commandes sur le même ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9ca93-157">You've also learned the benefits of using a PowerShell session when running multiple commands against the same remote computer.</span></span>

## <a name="review"></a><span data-ttu-id="9ca93-158">Révision</span><span class="sxs-lookup"><span data-stu-id="9ca93-158">Review</span></span>

1. <span data-ttu-id="9ca93-159">Comment activer la communication à distance PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="9ca93-159">How do you enable PowerShell remoting?</span></span>
1. <span data-ttu-id="9ca93-160">Quelle est la commande PowerShell permettant de démarrer une session interactive avec un ordinateur distant ?</span><span class="sxs-lookup"><span data-stu-id="9ca93-160">What is the PowerShell command for starting an interactive session with a remote computer?</span></span>
1. <span data-ttu-id="9ca93-161">Quel avantage présente l’utilisation d’une session de communication à distance PowerShell par rapport à la simple spécification du nom de l’ordinateur avec chaque commande ?</span><span class="sxs-lookup"><span data-stu-id="9ca93-161">What is a benefit of using a PowerShell remoting session versus just specifying the computer name with each command?</span></span>
1. <span data-ttu-id="9ca93-162">Est-il possible d’utiliser une session de communication à distance PowerShell avec une session de communication à distance un-à-un ?</span><span class="sxs-lookup"><span data-stu-id="9ca93-162">Can a PowerShell remoting session be used with a one-to-one remoting session?</span></span>
1. <span data-ttu-id="9ca93-163">Quelle est la différence entre le type des objets retournés par les applets de commande et ceux retournés lors de l’exécution de ces mêmes applets de commande sur des ordinateurs distants avec `Invoke-Command` ?</span><span class="sxs-lookup"><span data-stu-id="9ca93-163">What is the difference in the type of objects that are returned by cmdlets versus those returned when running those same cmdlets against remote computers with `Invoke-Command`?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="9ca93-164">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="9ca93-164">Recommended Reading</span></span>

- <span data-ttu-id="9ca93-165">[about_Remote][]</span><span class="sxs-lookup"><span data-stu-id="9ca93-165">[about_Remote][]</span></span>
- <span data-ttu-id="9ca93-166">[about_Remote_FAQ][]</span><span class="sxs-lookup"><span data-stu-id="9ca93-166">[about_Remote_FAQ][]</span></span>
- <span data-ttu-id="9ca93-167">[about_Remote_Output][]</span><span class="sxs-lookup"><span data-stu-id="9ca93-167">[about_Remote_Output][]</span></span>
- <span data-ttu-id="9ca93-168">[about_Remote_Requirements][]</span><span class="sxs-lookup"><span data-stu-id="9ca93-168">[about_Remote_Requirements][]</span></span>
- <span data-ttu-id="9ca93-169">[about_Remote_Troubleshooting][]</span><span class="sxs-lookup"><span data-stu-id="9ca93-169">[about_Remote_Troubleshooting][]</span></span>
- <span data-ttu-id="9ca93-170">[about_Remote_Variables][]</span><span class="sxs-lookup"><span data-stu-id="9ca93-170">[about_Remote_Variables][]</span></span>

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
