---
title: Découverte des objets, propriétés et méthodes
description: Vous n’avez pas besoin d’être développeur pour comprendre et utiliser les objets, les propriétés et les méthodes.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: f226221da7dd3b663f54cf23439dd7f945ed3a2a
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99595704"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a>Chapitre 3 - Découverte des objets, propriétés et méthodes

Mon premier contact avec un ordinateur fut avec un Commodore 64. Toutefois, mon premier ordinateur moderne était un clone IBM 286 12 MHz équipé de 1 Mo de mémoire, d’un disque dur de 40 Mo, d’un lecteur de disquette 5,25 pouces, d’un moniteur CGA, et qui exécutait Microsoft DOS 3.3.

De nombreux professionnels de l’informatique, comme moi-même, connaissent très bien la ligne de commande. Toutefois, lorsque l’on aborde le sujet des objets, des propriétés et des méthodes, ils se figent et vous répondent « je ne suis pas développeur ». Eh bien devinez quoi ? Vous n’avez pas besoin d’être un développeur pour réussir avec PowerShell. Ne soyez pas découragé par la terminologie. Vous n’allez peut-être pas tout comprendre tout de suite, mais après un peu de pratique, vous commencerez à avoir des révélations. « Ah d’accord ! C’est donc de ça que parlait le livre ! ».

Il est important de tester les exemples sur votre ordinateur pour bénéficier d’une expérience pratique.

## <a name="requirements"></a>Spécifications

Certains des exemples présentés dans ce chapitre nécessitent le module Active Directory PowerShell.
Ce module fait partie des outils d’administration de serveur distant (RSAT) pour Windows. Pour la version 1809 (et versions ultérieures) de Windows, les outils RSAT sont installés comme des fonctionnalités Windows.

- Pour plus d’informations sur l’installation des outils RSAT, consultez [Modules de gestion Windows][].
- Pour les versions antérieures de Windows, consultez [RSAT pour Windows][].

## <a name="get-member"></a>Get-Member

`Get-Member` vous permet de découvrir les objets, les propriétés et les méthodes qui sont disponibles pour les commandes.
Toute commande qui produit une sortie basée sur un objet peut être redirigée vers `Get-Member`. Une propriété est une caractéristique d’un élément. Votre passeport a une propriété appelée « Couleur des yeux » et les valeurs les plus courantes pour cette propriété sont « bleu » et « marron ». Une méthode est une action qui peut être réalisée sur un élément. Pour rester sur l’exemple du passeport, une des méthodes pourraient être « Refuser », car les services des passeports peuvent refuser de vous le délivrer.

### <a name="properties"></a>Propriétés

Dans l’exemple suivant, je vais récupérer des informations sur le service Temps Windows qui est exécuté sur mon ordinateur.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

**Status**, **Name** et **DisplayName** sont des exemples de propriétés, comme ceux du jeu de résultats précédent. La valeur de la propriété **Status** est `Running`, la valeur de la propriété **Name** est `w32time`, et la valeur de **DisplayName** est `Windows Time`.

Je vais maintenant rediriger la même commande vers `Get-Member` :

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

La première ligne des résultats de l’exemple précédent contient une information très importante. **TypeName** indique le type d’objet retourné. Dans cet exemple, un objet **System.ServiceProcess.ServiceController** a été retourné. Ceci est souvent abrégé dans la partie **TypeName** située juste après le dernier point (**ServiceController** dans cet exemple).

Une fois que vous connaissez le type d’objet produit par une commande, vous pouvez utiliser ces informations pour rechercher les commandes qui acceptent ce type d’objet comme entrée.

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

Toutes ces commandes ont un paramètre qui accepte un type d’objet **ServiceController** par pipeline, par entrée de paramètre, ou les deux.

Notez que les propriétés disponibles sont plus nombreuses que celles affichées par défaut. Même si ces propriétés supplémentaires ne sont pas affichées par défaut, vous pouvez les sélectionner à partir du pipeline en redirigeant la commande vers l’applet de commande `Select-Object` et en utilisant le paramètre **Property**. L’exemple suivant sélectionne toutes les propriétés en redirigeant les résultats de `Get-Service` vers `Select-Object`, et en spécifiant le caractère générique `*` comme la valeur du paramètre **Property**.

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

Pour la valeur du paramètre **Property**, vous pouvez également sélectionner certaines propriétés à l’aide d’une liste séparée par des virgules.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

Par défaut, quatre propriétés sont retournées dans un tableau et cinq ou plus sont retournées dans une liste. Certaines commandes utilisent une mise en forme personnalisée pour remplacer le nombre de propriétés affichées par défaut dans un tableau.
Plusieurs applets de commande `Format-*` peuvent être utilisées pour remplacer manuellement ces valeurs par défaut. Les plus courantes sont `Format-Table` et `Format-List`, qui seront toutes les deux abordées dans un prochain chapitre.

Les caractères génériques peuvent être utilisés lors de la spécification des noms de propriété avec `Select-Object`.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

Dans l’exemple précédent, `Can*` a été utilisé comme l’une des valeurs du paramètre **Property** pour retourner toutes les propriétés qui commencent par `Can`. Il s’agissait notamment de **CanPauseAndContinue**, **CanShutdown** et **CanStop**.

### <a name="methods"></a>Méthodes

Une méthode est une action qui peut être réalisée. Utilisez le paramètre **MemberType** pour affiner les résultats de `Get-Member` afin de n’afficher que les méthodes de `Get-Service`.

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

Comme vous pouvez le voir, il existe de nombreuses méthodes. La méthode **Stop** peut être utilisée pour arrêter un service Windows.

```powershell
(Get-Service -Name w32time).Stop()
```

Maintenant, vérifiez que le service Temps Windows a été arrêté.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

Je suis rarement amené à utiliser des méthodes. Toutefois, vous devez savoir vous en servir. Il peut arriver que vous rencontriez une commande `Get-*` sans commande correspondante permettant de la modifier.
Souvent, une méthode peut être utilisée pour réaliser une action qui la modifie. L’applet de commande `Get-SqlAgentJob` du module SqlServer PowerShell en est un bon exemple. Le module est installé dans le cadre de [SQL Server Management Studio (SMSS)][SMSS]. Il n’existe aucune applet de commande `Set-*` correspondante. Toutefois, vous pouvez utiliser une méthode pour effectuer cette même tâche.

Une autre raison pour laquelle il faut connaître les méthodes est que de nombreux débutants supposent qu’il n’est pas possible d’apporter des modifications destructrices avec les commandes `Get-*`. Pourtant, elles peuvent provoquer des problèmes graves si elles ne sont pas utilisées correctement.

Il est préférable d’utiliser une applet de commande pour exécuter l’action (s’il en existe une). Poursuivez en démarrant le service Temps Windows, mais cette fois-ci, utilisez l’applet de commande pour démarrer les services.

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Par défaut, `Start-Service` ne retourne pas de résultats comme la méthode Start de `Get-Service`.
Toutefois, l’un des avantages de l’utilisation d’une applet de commande est que souvent, une applet de commande offre des fonctionnalités qui ne sont pas disponibles avec une méthode. Dans l’exemple précédent, le paramètre **PassThru** a été utilisé. Avec ce paramètre, une applet de commande qui ne produit normalement pas de sortie est amenée à en produire une.

Ne prenez pas de risques concernant la sortie d’une applet de commande. Nous savons tous ce qui se passe lorsque nous faisons des suppositions. Je vais récupérer des informations sur le processus PowerShell qui s’exécute sur mon ordinateur Windows 10 Lab Environment.

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

À présent, je vais maintenant rediriger la même commande vers la commande Get-Member :

```powershell
Get-Process -Name PowerShell | Get-Member
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
```

Notez que les propriétés disponibles sont plus nombreuses que celles affichées par défaut. Un certain nombre de propriétés par défaut ne s’affichent pas en tant que propriétés lors de l’affichage des résultats de `Get-Member`. Cela est dû au fait que la plupart des valeurs affichées, telles que `NPM(K)`, `PM(K)`, `WS(K)` et `CPU(s)`, sont des propriétés calculées. Pour déterminer le nom des propriétés, la commande doit être redirigée vers `Get-Member`.

Si une commande ne produit pas de sortie, elle ne peut pas être redirigée vers `Get-Member`. Étant donné que `Start-Service` ne produit pas de sortie par défaut, elle génère une erreur lorsque vous essayez de la rediriger vers `Get-Member`.

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

Le paramètre **PassThru** peut être spécifié à l’aide de l’applet de commande `Start-Service` pour lui faire produire une sortie, qui est ensuite redirigée vers `Get-Member` sans erreur.

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

Pour être redirigée vers `Get-Member`, une commande doit produire une sortie basée sur un objet.

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

`Out-Host` écrit directement sur l’hôte PowerShell, mais ne produit pas de sortie basée sur les objets pour le pipeline. Elle ne peut donc pas être redirigée vers `Get-Member`.

## <a name="active-directory"></a>Active Directory

> [!NOTE]
> Les outils d’administration de serveur distant qui sont listés dans la section Configuration requise de ce chapitre sont nécessaires pour suivre cette section. En outre, comme indiqué dans la présentation de ce livre, votre ordinateur Windows 10 Lab Environment doit faire partie du domaine de l’environnement lab.

Utilisez `Get-Command` avec le paramètre **Module** pour déterminer quelles commandes ont été ajoutées dans le cadre du module PowerShell ActiveDirectory lors de l’installation des outils d’administration de serveur distant.

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

Au total, 147 commandes ont été ajoutées dans le cadre du module PowerShell ActiveDirectory. Certaines de ces commandes retournent uniquement une partie des propriétés disponibles par défaut.

Avez-vous remarqué quelque chose de différent concernant le nom des commandes de ce module ? La partie consacrée au nom comporte un préfixe AD. Ceci est fréquent avec les commandes de la plupart des modules. Le préfixe est conçu pour éviter les conflits de noms.

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

Même si votre connaissance d’Active Directory est limitée, vous savez probablement qu’un compte d’utilisateur a plus de propriétés que ce qui est indiqué dans cet exemple.

L’applet de commande `Get-ADUser` comporte un paramètre **Properties** qui est utilisé pour spécifier les propriétés supplémentaires (autres que par défaut) que vous souhaitez retourner. La spécification du caractère générique `*` permet de toutes les retourner.

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

Voilà, nous y sommes.

Savez-vous pourquoi les propriétés d’un compte d’utilisateur Active Directory sont si limitées par défaut ? Imaginez ce qui se passerait si vous retourniez chaque propriété de chaque compte d’utilisateur dans votre environnement Active Directory de production. Pensez à la détérioration des performances que cela pourrait provoquer, non seulement pour les contrôleurs de domaine, mais également pour votre réseau. Il est peu probable que vous ayez besoin de toutes les propriétés de toutes façons. Le fait de retourner toutes les propriétés d’un seul compte d’utilisateur est parfaitement acceptable si vous souhaitez connaître les propriétés qu’il contient.

Il n’est pas rare d’exécuter une commande à de nombreuses reprises lors de son prototypage. Si vous envisagez d’exécuter une requête volumineuse, exécutez-la une fois et stockez les résultats dans une variable. Utilisez ensuite le contenu de la variable au lieu d’exécuter plusieurs fois une requête coûteuse.

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

Au lieu d’exécuter la commande précédente plusieurs fois, utilisez le contenu de la variable `$Users`.
Notez que le contenu de la variable n’est pas mis à jour lorsque des modifications sont apportées à cet utilisateur dans Active Directory.

Vous pouvez rediriger la variable `$Users` vers `Get-Member` pour découvrir les propriétés disponibles.

```powershell
$Users | Get-Member
```

Sélectionnez ensuite chaque propriété en redirigeant `$Users` vers `Select-Object`, sans jamais avoir à interroger Active Directory plus d’une fois.

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

Si vous souhaitez interroger Active Directory plusieurs fois, utilisez le paramètre **Properties** pour spécifier les propriétés autres que par défaut de votre choix.

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez vu comment déterminer le type d’objet produit par une commande, comment déterminer quelles propriétés et méthodes sont disponibles pour une commande, et comment utiliser des commandes qui limitent les propriétés retournées par défaut.

## <a name="review"></a>Révision

1. Quel type d’objet est généré par l’applet de commande `Get-Process` ?
1. Comment connaître les propriétés qui sont disponibles pour une commande ?
1. Si une commande existe pour obtenir quelque chose, mais pas pour définir cette même chose, que devez-vous vérifier ?
1. Comment faire produire une sortie à certaines commandes qui ne produisent pas de sortie par défaut ?
1. Si vous prévoyez d’utiliser les résultats d’une commande qui produit une sortie très volumineuse, que devez-vous faire ?

## <a name="recommended-reading"></a>Lecture recommandée

- [Get-Member][]
- [Affichage de la structure des objets (Get-Member)][]
- [about_Objects][]
- [about_Properties][]
- [about_Methods][]
- [Aucune applet de commande PowerShell pour démarrer ou arrêter un événement ? N’oubliez pas de vérifier les méthodes sur les applets de commande obtenir][use-methods]

<!-- link references -->
[RSAT pour Windows]: https://support.microsoft.com/help/2693643
[Modules de gestion Windows]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[Affichage de la structure des objets (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
