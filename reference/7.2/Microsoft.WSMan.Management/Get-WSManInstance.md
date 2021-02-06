---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 00680a466c9cc9dd719fbce3d66f4eb10ec47860
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598550"
---
# <span data-ttu-id="74163-102">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="74163-102">Get-WSManInstance</span></span>

## <span data-ttu-id="74163-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="74163-103">SYNOPSIS</span></span>
<span data-ttu-id="74163-104">Affiche les informations de gestion d'une instance de ressource spécifiée par un URI de ressource.</span><span class="sxs-lookup"><span data-stu-id="74163-104">Displays management information for a resource instance specified by a Resource URI.</span></span>

## <span data-ttu-id="74163-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="74163-105">SYNTAX</span></span>

### <span data-ttu-id="74163-106">GetInstance (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="74163-106">GetInstance (Default)</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="74163-107">Énumérer</span><span class="sxs-lookup"><span data-stu-id="74163-107">Enumerate</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="74163-108">Description</span><span class="sxs-lookup"><span data-stu-id="74163-108">DESCRIPTION</span></span>
<span data-ttu-id="74163-109">L’applet de commande **WSManInstance** récupère une instance d’une ressource de gestion qui est spécifiée par une ressource Uniform Resource Identifier (Uri).</span><span class="sxs-lookup"><span data-stu-id="74163-109">The **Get-WSManInstance** cmdlet retrieves an instance of a management resource that is specified by a resource Uniform Resource Identifier (URI).</span></span>
<span data-ttu-id="74163-110">Les informations récupérées peuvent être un jeu d’informations XML complexe, qui est un objet, ou une valeur simple.</span><span class="sxs-lookup"><span data-stu-id="74163-110">The information that is retrieved can be a complex XML information set, which is an object, or a simple value.</span></span>
<span data-ttu-id="74163-111">Cette applet de commande est l’équivalent de la commande d' **extraction** WS-Management (Web Services for Management) standard.</span><span class="sxs-lookup"><span data-stu-id="74163-111">This cmdlet is the equivalent to the standard Web Services for Management (WS-Management) **Get** command.</span></span>

<span data-ttu-id="74163-112">Cette applet de commande utilise la couche de connexion/transport WS-Management pour récupérer les informations.</span><span class="sxs-lookup"><span data-stu-id="74163-112">This cmdlet uses the WS-Management connection/transport layer to retrieve information.</span></span>

## <span data-ttu-id="74163-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="74163-113">EXAMPLES</span></span>

### <span data-ttu-id="74163-114">Exemple 1 : récupération de toutes les informations à partir de WMI</span><span class="sxs-lookup"><span data-stu-id="74163-114">Example 1: Get all information from WMI</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="winrm"} -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : Windows Remote Management (WS-Management)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Windows Remote Management (WinRM) service implements the WS-Management protocol for remote
management. WS-Management is a standard web services protocol used for remote software and
hardware management. The WinRM service listens on the network for WS-Management requests
and processes them. The WinRM Service needs to be configured with a listener using the
winrm.cmd command line tool or through Group Policy in order for it to listen over the
network. The WinRM service provides access to WMI data and enables event collection. Event
collection and subscription to events require that the service is running. WinRM messages
use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is
preconfigured to share a port with IIS on the same computer.  The WinRM service reserves the
/wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any
websites hosted on IIS do not use the /wsman URL prefix.
DesktopInteract         : false
DisplayName             : Windows Remote Management (WS-Management)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : winrm
PathName                : C:\Windows\System32\svchost.exe -k NetworkService
ProcessId               : 948
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0
```

<span data-ttu-id="74163-115">Cette commande retourne toutes les informations que Windows Management Instrumentation (WMI) expose sur le service **WinRM** sur l’ordinateur SERVEUR01 distant.</span><span class="sxs-lookup"><span data-stu-id="74163-115">This command returns all of the information that Windows Management Instrumentation (WMI) exposes about the **WinRM** service on the remote server01 computer.</span></span>

### <span data-ttu-id="74163-116">Exemple 2 : récupération de l’état du service spouleur</span><span class="sxs-lookup"><span data-stu-id="74163-116">Example 2: Get the status of the Spooler service</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

<span data-ttu-id="74163-117">Cette commande retourne uniquement l’état du service **spouleur** sur l’ordinateur SERVEUR01 distant.</span><span class="sxs-lookup"><span data-stu-id="74163-117">This command returns only the status of the **Spooler** service on the remote server01 computer.</span></span>

### <span data-ttu-id="74163-118">Exemple 3 : obtenir des références de point de terminaison pour tous les services</span><span class="sxs-lookup"><span data-stu-id="74163-118">Example 3: Get endpoint references for all services</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/win32_service -ReturnType EPR
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Visual Studio 2008 Remote Debugger
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Allows members of the Administrators group to remotely debug server applications using Visual
Studio 2008. Use the Visual Studio 2008 Remote Debugging Configuration Wizard to enable this
service.
DesktopInteract         : false
DisplayName             : Visual Studio 2008 Remote Debugger
ErrorControl            : Ignore
ExitCode                : 1077
InstallDate             : InstallDate
Name                    : msvsmon90
PathName                : "C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe" /service msvsmon90
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Own Process
Started                 : false
StartMode               : Disabled
StartName               : LocalSystem
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : COMPUTER01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="74163-119">Cette commande retourne des références au point de terminaison qui correspondent à tous les services sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="74163-119">This command returns endpoint references that correspond to all the services on the local computer.</span></span>

### <span data-ttu-id="74163-120">Exemple 4 : accéder aux services qui répondent aux critères spécifiés</span><span class="sxs-lookup"><span data-stu-id="74163-120">Example 4: Get services that meet specified criteria</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/* -Filter "select * from win32_service where StartMode = 'Auto' and State = 'Stopped'" -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Windows Media Center Service Launcher
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Starts Windows Media Center Scheduler and Windows Media Center Receiver services
at startup if TV is enabled within Windows Media Center.
DesktopInteract         : false
DisplayName             : Windows Media Center Service Launcher
ErrorControl            : Ignore
ExitCode                : 0
InstallDate             : InstallDate
Name                    : ehstart
PathName                : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : false
StartMode               : Auto
StartName               : NT AUTHORITY\LocalService
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : Server01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="74163-121">Cette commande répertorie tous les services qui répondent aux critères suivants sur l’ordinateur SERVEUR01 distant :</span><span class="sxs-lookup"><span data-stu-id="74163-121">This command lists all of the services that meet the following criteria on the remote Server01 computer:</span></span>

- <span data-ttu-id="74163-122">Le type de démarrage du service est automatique.</span><span class="sxs-lookup"><span data-stu-id="74163-122">The startup type of the service is Automatic.</span></span>
- <span data-ttu-id="74163-123">Le service est arrêté.</span><span class="sxs-lookup"><span data-stu-id="74163-123">The service is stopped.</span></span>

### <span data-ttu-id="74163-124">Exemple 5 : obtient la configuration de l’écouteur qui correspond aux critères de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="74163-124">Example 5: Get listener configuration that matches criteria on the local computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"}
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.123, ::1, 2001:4898:0:fff:0:5efe:123.123.123.123...}
```

<span data-ttu-id="74163-125">Cette commande répertorie la configuration de l'écouteur WS-Management sur l'ordinateur local pour l'écouteur correspondant aux critères dans l'ensemble de sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="74163-125">This command lists the WS-Management listener configuration on the local computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="74163-126">Exemple 6 : obtenir la configuration de l’écouteur qui correspond aux critères d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="74163-126">Example 6: Get listener configuration that matches criteria on a remote computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"} -ComputerName "Server01"
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.124, ::1, 2001:4898:0:fff:0:5efe:123.123.123.124...}
```

<span data-ttu-id="74163-127">Cette commande répertorie la configuration de l'écouteur WS-Management sur l'ordinateur distant server01 pour l'écouteur correspondant aux critères dans l'ensemble de sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="74163-127">This command lists the WS-Management listener configuration on the remote server01 computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="74163-128">Exemple 7 : obtenir les instances associées associées à une instance spécifiée</span><span class="sxs-lookup"><span data-stu-id="74163-128">Example 7: Get associated instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
xsi                       : http://www.w3.org/2001/XMLSchema-instance
p                         : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_ComputerSystem
cim                       : http://schemas.dmtf.org/wbem/wscim/1/common
type                      : p:Win32_ComputerSystem_Type
lang                      : en-US
AdminPasswordStatus       : 1
AutomaticManagedPagefile  : true
AutomaticResetBootOption  : true
AutomaticResetCapability  : true
BootOptionOnLimit         : BootOptionOnLimit
BootOptionOnWatchDog      : BootOptionOnWatchDog
BootROMSupported          : true
BootupState               : Normal boot
Caption                   : SERVER01
ChassisBootupState        : 3
CreationClassName         : Win32_ComputerSystem
CurrentTimeZone           : -480
DaylightInEffect          : false
Description               : AT/AT COMPATIBLE
DNSHostName               : server01
Domain                    : site01.corp.fabrikam.com
DomainRole                : 1
EnableDaylightSavingsTime : true
FrontPanelResetStatus     : 2
InfraredSupported         : false
InstallDate               : InstallDate
KeyboardPasswordStatus    : 2
LastLoadInfo              : LastLoadInfo
Manufacturer              : Dell Inc.
Model                     : OptiPlex 745
Name                      : SERVER01
NameFormat                : NameFormat
NetworkServerModeEnabled  : true
NumberOfLogicalProcessors : 2
NumberOfProcessors        : 1
OEMStringArray            : www.dell.com
PartOfDomain              : true
PauseAfterReset           : -1
PCSystemType              : 5
PowerManagementSupported  : PowerManagementSupported
PowerOnPasswordStatus     : 1
PowerState                : 0
PowerSupplyState          : 3
PrimaryOwnerContact       : PrimaryOwnerContact
PrimaryOwnerName          : testuser01
ResetCapability           : 1
ResetCount                : -1
ResetLimit                : -1
Roles                     : {LM_Workstation, LM_Server, SQLServer, NT}
Status                    : OK
SystemStartupDelay        : SystemStartupDelay
SystemStartupSetting      : SystemStartupSetting
SystemType                : X86-based PC
ThermalState              : 3
TotalPhysicalMemory       : 3217760256
UserName                  : FABRIKAM\testuser01
WakeUpType                : 6
Workgroup                 : Workgroup
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Remote Procedure Call (RPC)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Serves as the endpoint mapper and COM Service Control Manager. If this service is stopped
or disabled, programs using COM or Remote Procedure Call (RPC) services will not function
properly.
DesktopInteract         : false
DisplayName             : Remote Procedure Call (RPC)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : RpcSs
PathName                : C:\Windows\system32\svchost.exe -k rpcss
ProcessId               : 1100
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0

xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_SystemDriver
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_SystemDriver_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : HTTP
CreationClassName       : Win32_SystemDriver
Description             : HTTP
DesktopInteract         : false
DisplayName             : HTTP
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : HTTP
PathName                : C:\Windows\system32\drivers\HTTP.sys
ServiceSpecificExitCode : 0
ServiceType             : Kernel Driver
Started                 : true
StartMode               : Manual
StartName               :
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
```

<span data-ttu-id="74163-129">Cette commande obtient les instances associées qui sont liées à l'instance spécifiée (winrm).</span><span class="sxs-lookup"><span data-stu-id="74163-129">This command gets the associated instances that are related to the specified instance (winrm).</span></span>

<span data-ttu-id="74163-130">Vous devez mettre le filtre entre guillemets, comme illustré dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="74163-130">You must enclose the filter in quotation marks, as shown in the example.</span></span>

### <span data-ttu-id="74163-131">Exemple 8 : obtenir des instances d’association associées à une instance spécifiée</span><span class="sxs-lookup"><span data-stu-id="74163-131">Example 8: Get association instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

<span data-ttu-id="74163-132">Cette commande obtient les instances d'association qui sont liées à l'instance spécifiée (winrm).</span><span class="sxs-lookup"><span data-stu-id="74163-132">This command gets association instances that are related to the specified instance (winrm).</span></span>
<span data-ttu-id="74163-133">Étant donné que la valeur de *dialecte* est Association et que le paramètre *associations* est utilisé, cette commande retourne les instances d’association, et non les instances associées.</span><span class="sxs-lookup"><span data-stu-id="74163-133">Because the *Dialect* value is association and the *Associations* parameter is used, this command returns association instances, not associated instances.</span></span>

<span data-ttu-id="74163-134">Vous devez mettre le filtre entre guillemets, comme illustré dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="74163-134">You must enclose the filter in quotation marks, as shown in the example.</span></span>

## <span data-ttu-id="74163-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74163-135">PARAMETERS</span></span>

### <span data-ttu-id="74163-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="74163-136">-ApplicationName</span></span>
<span data-ttu-id="74163-137">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="74163-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="74163-138">La valeur par défaut du paramètre *applicationName* est WSMan.</span><span class="sxs-lookup"><span data-stu-id="74163-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="74163-139">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="74163-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="74163-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="74163-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="74163-141">Par exemple : `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="74163-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="74163-142">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="74163-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="74163-143">Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="74163-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="74163-144">Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74163-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="74163-145">Dans ce cas, IIS héberge WS-Management pour des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="74163-145">In this case, IIS hosts WS-Management for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-146">-Associations</span><span class="sxs-lookup"><span data-stu-id="74163-146">-Associations</span></span>
<span data-ttu-id="74163-147">Indique que cette applet de commande obtient les instances d’association, et non les instances associées.</span><span class="sxs-lookup"><span data-stu-id="74163-147">Indicates that this cmdlet gets association instances, not associated instances.</span></span>
<span data-ttu-id="74163-148">Vous pouvez utiliser ce paramètre uniquement quand le paramètre *Dialect* a la valeur Association.</span><span class="sxs-lookup"><span data-stu-id="74163-148">You can use this parameter only when the *Dialect* parameter has a value of Association.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-149">-Authentification</span><span class="sxs-lookup"><span data-stu-id="74163-149">-Authentication</span></span>
<span data-ttu-id="74163-150">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="74163-150">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="74163-151">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="74163-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="74163-152">De base.</span><span class="sxs-lookup"><span data-stu-id="74163-152">Basic.</span></span>
<span data-ttu-id="74163-153">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="74163-153">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="74163-154">Par défaut.</span><span class="sxs-lookup"><span data-stu-id="74163-154">Default.</span></span>
<span data-ttu-id="74163-155">Utilisez la méthode d'authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="74163-155">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="74163-156">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="74163-156">This is the default.</span></span>
- <span data-ttu-id="74163-157">Digest.</span><span class="sxs-lookup"><span data-stu-id="74163-157">Digest.</span></span>
<span data-ttu-id="74163-158">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="74163-158">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="74163-159">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="74163-159">Kerberos.</span></span>
<span data-ttu-id="74163-160">L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="74163-160">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="74163-161">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="74163-161">Negotiate.</span></span>
<span data-ttu-id="74163-162">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="74163-162">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="74163-163">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="74163-163">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="74163-164">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="74163-164">CredSSP.</span></span>
<span data-ttu-id="74163-165">Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="74163-165">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="74163-166">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="74163-166">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="74163-167">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="74163-167">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="74163-168">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="74163-168">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="74163-169">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="74163-169">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-170">-BasePropertiesOnly</span><span class="sxs-lookup"><span data-stu-id="74163-170">-BasePropertiesOnly</span></span>
<span data-ttu-id="74163-171">Indique que cette applet de commande énumère uniquement les propriétés qui font partie de la classe de base spécifiée par le paramètre *resourceuri* .</span><span class="sxs-lookup"><span data-stu-id="74163-171">Indicates that this cmdlet enumerates only the properties that are part of the base class that is specified by the *ResourceURI* parameter.</span></span>
<span data-ttu-id="74163-172">Ce paramètre n’a aucun effet si le paramètre *superficielle* est spécifié.</span><span class="sxs-lookup"><span data-stu-id="74163-172">This parameter has no effect if the *Shallow* parameter is specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases: UBPO, Base

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-173">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="74163-173">-CertificateThumbprint</span></span>
<span data-ttu-id="74163-174">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="74163-174">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="74163-175">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="74163-175">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="74163-176">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="74163-176">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="74163-177">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="74163-177">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="74163-178">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74163-178">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-179">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="74163-179">-ComputerName</span></span>
<span data-ttu-id="74163-180">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="74163-180">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="74163-181">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="74163-181">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="74163-182">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="74163-182">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="74163-183">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="74163-183">The local computer is the default.</span></span>
<span data-ttu-id="74163-184">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="74163-184">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="74163-185">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74163-185">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-186">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="74163-186">-ConnectionURI</span></span>
<span data-ttu-id="74163-187">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="74163-187">Specifies the connection endpoint.</span></span>
<span data-ttu-id="74163-188">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="74163-188">The format of this string is as follows:</span></span>

<span data-ttu-id="74163-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="74163-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="74163-190">La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="74163-190">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="74163-191">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="74163-191">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-192">-Credential</span><span class="sxs-lookup"><span data-stu-id="74163-192">-Credential</span></span>
<span data-ttu-id="74163-193">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="74163-193">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="74163-194">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="74163-194">The default is the current user.</span></span>
<span data-ttu-id="74163-195">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="74163-195">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="74163-196">Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="74163-196">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="74163-197">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="74163-197">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74163-198">-Dialecte</span><span class="sxs-lookup"><span data-stu-id="74163-198">-Dialect</span></span>
<span data-ttu-id="74163-199">Spécifie le dialecte à utiliser dans le prédicat de filtre.</span><span class="sxs-lookup"><span data-stu-id="74163-199">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="74163-200">Ce peut être n'importe quel dialecte pris en charge par le service distant.</span><span class="sxs-lookup"><span data-stu-id="74163-200">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="74163-201">Les alias suivants peuvent être utilisés pour l'URI de dialecte :</span><span class="sxs-lookup"><span data-stu-id="74163-201">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="74163-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="74163-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="74163-203">Sélection `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="74163-203">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="74163-204">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="74163-204">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-205">-Énumérer</span><span class="sxs-lookup"><span data-stu-id="74163-205">-Enumerate</span></span>
<span data-ttu-id="74163-206">Indique que cette applet de commande retourne toutes les instances d’une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="74163-206">Indicates that this cmdlet returns all of the instances of a management resource.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-207">-Filter</span><span class="sxs-lookup"><span data-stu-id="74163-207">-Filter</span></span>
<span data-ttu-id="74163-208">Spécifie l'expression de filtre pour l'énumération.</span><span class="sxs-lookup"><span data-stu-id="74163-208">Specifies the filter expression for the enumeration.</span></span>
<span data-ttu-id="74163-209">Si vous spécifiez ce paramètre, vous devez également spécifier *Dialect*.</span><span class="sxs-lookup"><span data-stu-id="74163-209">If you specify this parameter, you must also specify *Dialect*.</span></span>

<span data-ttu-id="74163-210">Les valeurs valides de ce paramètre dépendent du dialecte spécifié dans *dialecte*.</span><span class="sxs-lookup"><span data-stu-id="74163-210">The valid values of this parameter depend on the dialect that is specified in *Dialect*.</span></span>
<span data-ttu-id="74163-211">Par exemple, si *dialecte* est WQL, le paramètre *Filter* doit contenir une chaîne et la chaîne doit contenir une requête WQL valide, telle que la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="74163-211">For example, if *Dialect* is WQL, the *Filter* parameter must contain a string, and the string must contain a valid WQL query such as the following query:</span></span>

`"Select * from Win32_Service where State != Running"`

<span data-ttu-id="74163-212">Si *Dialect* est Association, *Filter* doit contenir une chaîne et la chaîne doit contenir un filtre valide, tel que le filtre suivant :</span><span class="sxs-lookup"><span data-stu-id="74163-212">If *Dialect* is Association, *Filter* must contain a string, and the string must contain a valid filter, such as the following filter:</span></span>

`-filter:Object=EPR\[;AssociationClassName=AssocClassName\]\[;ResultClassName=ClassName\]\[;Role=RefPropertyName\]\[;ResultRole=RefPropertyName\]}`

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-213">-Fragment</span><span class="sxs-lookup"><span data-stu-id="74163-213">-Fragment</span></span>
<span data-ttu-id="74163-214">Spécifie une section à l'intérieur de l'instance qui doit être mise à jour ou récupérée pour l'opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="74163-214">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="74163-215">Par exemple, pour obtenir l’état d’un service spouleur, spécifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="74163-215">For example, to get the status of a spooler service, specify the following:</span></span>

`-Fragment Status`

```yaml
Type: System.String
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-216">-A</span><span class="sxs-lookup"><span data-stu-id="74163-216">-OptionSet</span></span>
<span data-ttu-id="74163-217">Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="74163-217">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="74163-218">Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="74163-218">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="74163-219">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="74163-219">Any number of options can be specified.</span></span>

<span data-ttu-id="74163-220">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="74163-220">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: OS

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="74163-221">-Port</span><span class="sxs-lookup"><span data-stu-id="74163-221">-Port</span></span>
<span data-ttu-id="74163-222">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="74163-222">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="74163-223">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="74163-223">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="74163-224">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="74163-224">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="74163-225">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="74163-225">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="74163-226">Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="74163-226">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="74163-227">Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="74163-227">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="74163-228">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="74163-228">-ResourceURI</span></span>
<span data-ttu-id="74163-229">Spécifie l’URI de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="74163-229">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="74163-230">L’URI identifie un type spécifique de ressource, tel que des disques ou des processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="74163-230">The URI identifies a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="74163-231">Un URI se compose d’un préfixe et d’un chemin d’accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="74163-231">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="74163-232">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="74163-232">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: RURI

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="74163-233">-ReturnType</span><span class="sxs-lookup"><span data-stu-id="74163-233">-ReturnType</span></span>
<span data-ttu-id="74163-234">Spécifie le type de données à retourner.</span><span class="sxs-lookup"><span data-stu-id="74163-234">Specifies the type of data to be returned.</span></span>
<span data-ttu-id="74163-235">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="74163-235">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="74163-236">Object</span><span class="sxs-lookup"><span data-stu-id="74163-236">Object</span></span>
- <span data-ttu-id="74163-237">EPR</span><span class="sxs-lookup"><span data-stu-id="74163-237">EPR</span></span>
- <span data-ttu-id="74163-238">ObjectAndEPR</span><span class="sxs-lookup"><span data-stu-id="74163-238">ObjectAndEPR</span></span>

<span data-ttu-id="74163-239">La valeur par défaut est Object.</span><span class="sxs-lookup"><span data-stu-id="74163-239">The default value is Object.</span></span>

<span data-ttu-id="74163-240">Si vous spécifiez Object ou si vous ne spécifiez pas ce paramètre, cette applet de commande retourne uniquement les objets.</span><span class="sxs-lookup"><span data-stu-id="74163-240">If you specify Object or do not specify this parameter, this cmdlet returns only objects.</span></span>
<span data-ttu-id="74163-241">Si vous spécifiez la référence de point de terminaison (EPR), cette applet de commande retourne uniquement les références de point de terminaison des objets.</span><span class="sxs-lookup"><span data-stu-id="74163-241">If you specify endpoint reference (EPR) this cmdlet returns only the endpoint references of the objects.</span></span>
<span data-ttu-id="74163-242">Les références au point de terminaison contiennent des informations sur l'URI de ressource et les sélecteurs pour l'instance.</span><span class="sxs-lookup"><span data-stu-id="74163-242">Endpoint references contain information about the resource URI and the selectors for the instance.</span></span>
<span data-ttu-id="74163-243">Si vous spécifiez ObjectAndEPR, cette applet de commande retourne à la fois l’objet et ses références de point de terminaison associées.</span><span class="sxs-lookup"><span data-stu-id="74163-243">If you specify ObjectAndEPR, this cmdlet returns both the object and its associated endpoint references.</span></span>

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases: RT
Accepted values: object, epr, objectandepr

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-244">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="74163-244">-SelectorSet</span></span>
<span data-ttu-id="74163-245">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="74163-245">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="74163-246">Le paramètre *SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="74163-246">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="74163-247">La valeur du paramètre *SelectorSet* doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="74163-247">The value of the *SelectorSet* parameter must be a hash table.</span></span>

<span data-ttu-id="74163-248">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="74163-248">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-249">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="74163-249">-SessionOption</span></span>
<span data-ttu-id="74163-250">Spécifie les options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="74163-250">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="74163-251">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="74163-251">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="74163-252">Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="74163-252">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: SO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-253">-Superficielle</span><span class="sxs-lookup"><span data-stu-id="74163-253">-Shallow</span></span>
<span data-ttu-id="74163-254">Indique que cette applet de commande retourne uniquement les instances de la classe de base spécifiée dans l’URI de ressource.</span><span class="sxs-lookup"><span data-stu-id="74163-254">Indicates that this cmdlet returns only instances of the base class that is specified in the resource URI.</span></span>
<span data-ttu-id="74163-255">Si vous ne spécifiez pas ce paramètre,, cette applet de commande retourne des instances de la classe de base spécifiée dans l’URI et dans toutes ses classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="74163-255">If you do not specify this parameter,, this cmdlet returns instances of the base class that is specified in the URI and in all its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-256">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="74163-256">-UseSSL</span></span>
<span data-ttu-id="74163-257">Spécifie que le protocole SSL (Secure Sockets Layer) (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="74163-257">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="74163-258">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="74163-258">By default, SSL is not used.</span></span>

<span data-ttu-id="74163-259">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="74163-259">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="74163-260">Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="74163-260">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="74163-261">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="74163-261">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SSL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74163-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74163-262">CommonParameters</span></span>
<span data-ttu-id="74163-263">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74163-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74163-264">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="74163-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74163-265">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="74163-265">INPUTS</span></span>

### <span data-ttu-id="74163-266">None</span><span class="sxs-lookup"><span data-stu-id="74163-266">None</span></span>
<span data-ttu-id="74163-267">Cette commande n'accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="74163-267">This command does not accept any input.</span></span>

## <span data-ttu-id="74163-268">SORTIES</span><span class="sxs-lookup"><span data-stu-id="74163-268">OUTPUTS</span></span>

### <span data-ttu-id="74163-269">Élément System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="74163-269">System.Xml.XmlElement</span></span>
<span data-ttu-id="74163-270">Cette applet de commande génère un objet **XmlElement** .</span><span class="sxs-lookup"><span data-stu-id="74163-270">This cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="74163-271">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="74163-271">NOTES</span></span>

## <span data-ttu-id="74163-272">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="74163-272">RELATED LINKS</span></span>

[<span data-ttu-id="74163-273">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="74163-273">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="74163-274">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="74163-274">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="74163-275">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="74163-275">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="74163-276">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="74163-276">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="74163-277">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="74163-277">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="74163-278">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="74163-278">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="74163-279">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="74163-279">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="74163-280">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="74163-280">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="74163-281">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="74163-281">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="74163-282">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="74163-282">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="74163-283">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="74163-283">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="74163-284">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="74163-284">Test-WSMan</span></span>](Test-WSMan.md)

