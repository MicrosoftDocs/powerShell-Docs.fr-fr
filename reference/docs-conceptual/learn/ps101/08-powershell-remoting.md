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
# <a name="chapter-8---powershell-remoting"></a>Chapitre 8 - Communication à distance PowerShell

PowerShell propose de nombreuses façons différentes d’exécuter des commandes sur des ordinateurs distants. Dans le dernier chapitre, vous avez vu comment interroger à distance WMI à l’aide des applets de commande CIM. PowerShell comprend également plusieurs applets de commande avec un paramètre **ComputerName** intégré.

Comme indiqué dans l’exemple suivant, `Get-Command` peut être utilisée avec le paramètre **ParameterName** pour déterminer les commandes qui ont un paramètre **ComputerName**.

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

Les commandes comme `Get-Process` et `Get-Hotfix` ont un paramètre **ComputerName**. L’exécution de commandes sur des ordinateurs distants n’est pas une solution à long terme retenue par Microsoft. Même si vous trouvez une commande ayant un paramètre **ComputerName**, il est probable que vous deviez spécifier d’autres informations d’identification et qu’il n’y ait pas de paramètre **Credential**. Si vous avez décidé d’exécuter PowerShell à partir d’un compte avec élévation de privilèges, un pare-feu entre vous et l’ordinateur distant peut bloquer la demande.

Pour utiliser les commandes de communication à distance PowerShell présentées dans ce chapitre, la communication à distance PowerShell doit être activée sur l’ordinateur distant. Utilisez l’applet de commande `Enable-PSRemoting` pour activer la communication à distance PowerShell.

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

## <a name="one-to-one-remoting"></a>Communication à distance un-à-un

Si vous voulez que votre session à distance soit interactive, la communication à distance un-à-un est ce que vous voulez.
Ce type de communication à distance est fourni par le biais de l’applet de commande `Enter-PSSession`.

Dans le dernier chapitre, j’ai stocké mes informations d’identification d’administrateur de domaine dans une variable nommée `$Cred`. Si vous ne l’avez pas déjà fait, continuez en stockant vos informations d’identification d’administrateur de domaine dans la variable `$Cred`.

Cela vous permet d’entrer les informations d’identification une seule fois et de les utiliser pour chaque commande tant que votre session PowerShell actuelle est active.

```powershell
$Cred = Get-Credential
```

Créez une session de communication à distance PowerShell un-à-un sur le contrôleur de domaine nommé dc01.

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

Notez que, dans l’exemple précédent, l’invite PowerShell est précédée de `[dc01]`. Cela signifie que vous êtes dans une session PowerShell interactive sur l’ordinateur distant nommé dc01. Toutes les commandes que vous exécutez s’exécutent sur dc01, et non sur votre ordinateur local. De plus, n’oubliez pas que vous avez uniquement accès aux commandes PowerShell qui existent sur l’ordinateur distant, et pas à celles de votre ordinateur local. En d’autres termes, si vous avez installé des modules supplémentaires sur votre ordinateur, ces derniers ne sont pas accessibles sur l’ordinateur distant.

Quand vous êtes connecté à un ordinateur distant par le biais d’une session de communication à distance PowerShell interactive un-à-un, vous vous trouvez en fait sur l’ordinateur distant. Les objets sont des objets normaux tout comme ceux que vous utilisez dans l’ensemble de cette documentation.

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

Quand vous avez terminé d’utiliser l’ordinateur distant, quittez la session de communication à distance un-à-un à l’aide de l’applet de commande `Exit-PSSession`.

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a>Communication à distance un-à-plusieurs

Vous pouvez parfois être amené à effectuer une tâche de manière interactive sur un ordinateur distant. Mais la communication à distance est beaucoup plus puissante quand une tâche est exécutée simultanément sur plusieurs ordinateurs distants. Utilisez l’applet de commande `Invoke-Command` pour exécuter une commande sur un ou plusieurs ordinateurs distants en même temps.

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

Dans l’exemple précédent, trois serveurs ont été interrogés pour obtenir l’état du service de temps Windows. L’applet de commande `Get-Service` a été placée dans le bloc de script de `Invoke-Command`. `Get-Service` s’exécute en fait sur l’ordinateur distant et les résultats sont retournés à votre ordinateur local sous la forme d’objets désérialisés.

La redirection de la commande précédente vers `Get-Member` indique que les résultats sont en effet des objets désérialisés.

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

Notez que la majorité des méthodes sont manquantes sur les objets désérialisés. Cela signifie qu’il ne s’agit pas d’objets actifs ; ils sont inertes. Vous ne pouvez pas démarrer ou arrêter un service à l’aide d’un objet désérialisé, car il s’agit d’une capture instantanée de l’état de cet objet au moment où la commande s’est exécutée sur l’ordinateur distant.

Cela ne signifie pas que vous ne pouvez pas démarrer ou arrêter un service à l’aide d’une méthode avec `Invoke-Command`. Cela signifie simplement que la méthode doit être appelée dans la session à distance.

Je vais arrêter le service de temps Windows sur ces trois serveurs distants à l’aide de la méthode **Stop()** pour en apporter la preuve.

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

Comme mentionné dans un chapitre précédent, s’il existe une applet de commande pour accomplir une tâche, je vous recommande de l’utiliser plutôt que d’utiliser une méthode. Dans le scénario précédent, je recommande l’utilisation de l’applet de commande `Stop-Service` au lieu de la méthode stop. J’ai choisi d’utiliser la méthode **Stop()** pour prouver une chose, car de nombreuses personnes pensent à tort qu’il n’est pas possible d’appeler des méthodes lors de l’utilisation de la communication à distance PowerShell. Elles ne peuvent pas être appelées sur l’objet qui est retourné car il est désérialisé, mais elles peuvent être appelées dans la session à distance elle-même.

## <a name="powershell-sessions"></a>Sessions PowerShell

Dans le dernier exemple de la section précédente, j’ai exécuté deux commandes à l’aide de l’applet de commande `Invoke-Command`.
Cela signifie que deux sessions distinctes devaient être configurées et désactivées pour exécuter ces deux commandes.

À l’instar des sessions CIM présentées dans le chapitre 7, une session PowerShell sur un ordinateur distant peut être utilisée pour exécuter plusieurs commandes sur l’ordinateur distant sans la surcharge d’une nouvelle session pour chaque commande individuelle.

Créez une session PowerShell sur chacun des trois ordinateurs avec lesquels nous travaillons dans ce chapitre : DC01, SQL02 et WEB01.

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

À présent, utilisez la variable nommée `$Session` pour démarrer le service de temps Windows à l’aide d’une méthode et vérifier l’état de ce service.

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

Une fois la session créée à l’aide d’autres informations d’identification, il n’est plus nécessaire de spécifier les informations d’identification à chaque exécution d’une commande.

Une fois que vous avez terminé d’utiliser les sessions, veillez à les supprimer.

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez appris à utiliser la communication à distance PowerShell, à exécuter des commandes dans une session interactive avec un ordinateur distant et à exécuter des commandes sur plusieurs ordinateurs à l’aide de la communication à distance un-à-plusieurs. Vous avez également découvert les avantages de l’utilisation d’une session PowerShell lors de l’exécution de plusieurs commandes sur le même ordinateur distant.

## <a name="review"></a>Révision

1. Comment activer la communication à distance PowerShell ?
1. Quelle est la commande PowerShell permettant de démarrer une session interactive avec un ordinateur distant ?
1. Quel avantage présente l’utilisation d’une session de communication à distance PowerShell par rapport à la simple spécification du nom de l’ordinateur avec chaque commande ?
1. Est-il possible d’utiliser une session de communication à distance PowerShell avec une session de communication à distance un-à-un ?
1. Quelle est la différence entre le type des objets retournés par les applets de commande et ceux retournés lors de l’exécution de ces mêmes applets de commande sur des ordinateurs distants avec `Invoke-Command` ?

## <a name="recommended-reading"></a>Lecture recommandée

- [about_Remote][]
- [about_Remote_FAQ][]
- [about_Remote_Output][]
- [about_Remote_Requirements][]
- [about_Remote_Troubleshooting][]
- [about_Remote_Variables][]

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
