---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: c60d17631d0603e4285c34b91dd0971e4e358af0
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208690"
---
# Get-WSManInstance

## SYNOPSIS
Affiche les informations de gestion d'une instance de ressource spécifiée par un URI de ressource.

## SYNTAX

### GetInstance (valeur par défaut)

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### Énumérer

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## Description
L’applet de commande **WSManInstance** récupère une instance d’une ressource de gestion qui est spécifiée par une ressource Uniform Resource Identifier (Uri).
Les informations récupérées peuvent être un jeu d’informations XML complexe, qui est un objet, ou une valeur simple.
Cette applet de commande est l’équivalent de la commande d' **extraction** WS-Management (Web Services for Management) standard.

Cette applet de commande utilise la couche de connexion/transport WS-Management pour récupérer les informations.

## EXEMPLES

### Exemple 1 : récupération de toutes les informations à partir de WMI

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

Cette commande retourne toutes les informations que Windows Management Instrumentation (WMI) expose sur le service **WinRM** sur l’ordinateur SERVEUR01 distant.

### Exemple 2 : récupération de l’état du service spouleur

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

Cette commande retourne uniquement l’état du service **spouleur** sur l’ordinateur SERVEUR01 distant.

### Exemple 3 : obtenir des références de point de terminaison pour tous les services

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

Cette commande retourne des références au point de terminaison qui correspondent à tous les services sur l'ordinateur local.

### Exemple 4 : accéder aux services qui répondent aux critères spécifiés

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

Cette commande répertorie tous les services qui répondent aux critères suivants sur l’ordinateur SERVEUR01 distant :

- Le type de démarrage du service est automatique.
- Le service est arrêté.

### Exemple 5 : obtient la configuration de l’écouteur qui correspond aux critères de l’ordinateur local

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

Cette commande répertorie la configuration de l'écouteur WS-Management sur l'ordinateur local pour l'écouteur correspondant aux critères dans l'ensemble de sélecteurs.

### Exemple 6 : obtenir la configuration de l’écouteur qui correspond aux critères d’un ordinateur distant

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

Cette commande répertorie la configuration de l'écouteur WS-Management sur l'ordinateur distant server01 pour l'écouteur correspondant aux critères dans l'ensemble de sélecteurs.

### Exemple 7 : obtenir les instances associées associées à une instance spécifiée

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

Cette commande obtient les instances associées qui sont liées à l'instance spécifiée (winrm).

Vous devez mettre le filtre entre guillemets, comme illustré dans l'exemple.

### Exemple 8 : obtenir des instances d’association associées à une instance spécifiée

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

Cette commande obtient les instances d'association qui sont liées à l'instance spécifiée (winrm).
Étant donné que la valeur de *dialecte* est Association et que le paramètre *associations* est utilisé, cette commande retourne les instances d’association, et non les instances associées.

Vous devez mettre le filtre entre guillemets, comme illustré dans l'exemple.

## PARAMETERS

### -ApplicationName
Spécifie le nom d'application de la connexion.
La valeur par défaut du paramètre *applicationName* est WSMan.
L'identificateur complet du point de terminaison distant est au format suivant :

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Par exemple : `http://server01:8080/WSMAN`

Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.
Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.
Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.
Dans ce cas, IIS héberge WS-Management pour des performances optimales.

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

### -Associations
Indique que cette applet de commande obtient les instances d’association, et non les instances associées.
Vous pouvez utiliser ce paramètre uniquement quand le paramètre *Dialect* a la valeur Association.

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

### -Authentification
Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.
Les valeurs valides pour ce paramètre sont :

- De base.
L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.
- Par défaut.
Utilisez la méthode d'authentification implémentée par le protocole WS-Management.
Il s’agit de la valeur par défaut.
- Digest.
Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.
- Kerberos.
L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.
- Negotiate.
L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.
Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.
- CredSSP.
Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.
Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.

ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.
Cette pratique augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

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

### -BasePropertiesOnly
Indique que cette applet de commande énumère uniquement les propriétés qui font partie de la classe de base spécifiée par le paramètre *resourceuri* .
Ce paramètre n’a aucun effet si le paramètre *superficielle* est spécifié.

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

### -CertificateThumbprint
Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.
Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client.
Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.

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

### -ComputerName
Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.
La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.
Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.
L'ordinateur local est la valeur par défaut.
Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.
Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.

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

### -ConnectionURI
Spécifie le point de terminaison de connexion.
Le format de cette chaîne est le suivant :

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :

`http://Server01:8080/WSMAN`

L’URI doit être complet.

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

### -Credential
Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.
Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .
Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.
Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

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

### -Dialecte
Spécifie le dialecte à utiliser dans le prédicat de filtre.
Ce peut être n'importe quel dialecte pris en charge par le service distant.
Les alias suivants peuvent être utilisés pour l'URI de dialecte :

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- Sélection `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

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

### -Énumérer
Indique que cette applet de commande retourne toutes les instances d’une ressource de gestion.

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

### -Filter
Spécifie l'expression de filtre pour l'énumération.
Si vous spécifiez ce paramètre, vous devez également spécifier *Dialect* .

Les valeurs valides de ce paramètre dépendent du dialecte spécifié dans *dialecte* .
Par exemple, si *dialecte* est WQL, le paramètre *Filter* doit contenir une chaîne et la chaîne doit contenir une requête WQL valide, telle que la requête suivante :

`"Select * from Win32_Service where State != Running"`

Si *Dialect* est Association, *Filter* doit contenir une chaîne et la chaîne doit contenir un filtre valide, tel que le filtre suivant :

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

### -Fragment
Spécifie une section à l'intérieur de l'instance qui doit être mise à jour ou récupérée pour l'opération spécifiée.
Par exemple, pour obtenir l’état d’un service spouleur, spécifiez les éléments suivants :

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

### -A
Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.
Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.
N'importe quel nombre d'options peut être spécifié.

L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :

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

### -Port
Spécifie le port à utiliser lorsque le client se connecte au service WinRM.
Lorsque le transport est HTTP, le port par défaut est 80.
Lorsque le transport est HTTPS, le port par défaut est 443.

Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.
Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.
Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.

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

### -ResourceURI
Spécifie l’URI de la classe ou de l’instance de ressource.
L’URI identifie un type spécifique de ressource, tel que des disques ou des processus, sur un ordinateur.

Un URI se compose d’un préfixe et d’un chemin d’accès à une ressource.
Par exemple :

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

### -ReturnType
Spécifie le type de données à retourner.
Les valeurs valides pour ce paramètre sont :

- Object
- EPR
- ObjectAndEPR

La valeur par défaut est Object.

Si vous spécifiez Object ou si vous ne spécifiez pas ce paramètre, cette applet de commande retourne uniquement les objets.
Si vous spécifiez la référence de point de terminaison (EPR), cette applet de commande retourne uniquement les références de point de terminaison des objets.
Les références au point de terminaison contiennent des informations sur l'URI de ressource et les sélecteurs pour l'instance.
Si vous spécifiez ObjectAndEPR, cette applet de commande retourne à la fois l’objet et ses références de point de terminaison associées.

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

### -SelectorSet
Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.
Le paramètre *SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.
La valeur du paramètre *SelectorSet* doit être une table de hachage.

L'exemple suivant montre comment spécifier une valeur pour ce paramètre :

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

### -SessionOption
Spécifie les options étendues pour la session WS-Management.
Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.
Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .

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

### -Superficielle
Indique que cette applet de commande retourne uniquement les instances de la classe de base spécifiée dans l’URI de ressource.
Si vous ne spécifiez pas ce paramètre,, cette applet de commande retourne des instances de la classe de base spécifiée dans l’URI et dans toutes ses classes dérivées.

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

### -UseSSL
Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.
Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.
Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.
Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

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

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun
Cette commande n'accepte aucune entrée.

## SORTIES

### Élément System.Xml.Xml
Cette applet de commande génère un objet **XmlElement** .

## REMARQUES

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
