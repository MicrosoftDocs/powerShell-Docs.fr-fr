---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203982"
---
# Get-WmiObject

## SYNOPSIS
Obtient des instances de classes WMI (Windows Management Instrumentation) ou des informations sur les classes disponibles.

## SYNTAX

### requête (par défaut)

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### list

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### WQLQuery

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### class

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### path

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## Description

À compter de PowerShell 3,0, cette applet de commande a été remplacée par `Get-CimInstance` .

L' `Get-WmiObject` applet de commande obtient des instances de classes WMI ou des informations sur les classes WMI disponibles. Pour spécifier un ordinateur distant, utilisez le paramètre **ComputerName** . Si le paramètre **List** est spécifié, l'applet de commande obtient des informations sur les classes WMI qui sont disponibles dans un espace de noms spécifié. Si le paramètre **Query** est spécifié, l'applet de commande exécute une instruction utilisant le langage de requêtes WMI (WQL).

L' `Get-WmiObject` applet de commande n’utilise pas la communication à distance Windows PowerShell pour effectuer des opérations distantes.
Vous pouvez utiliser le paramètre **ComputerName** de l' `Get-WmiObject` applet de commande même si votre ordinateur n’est pas conforme à la configuration requise pour la communication à distance Windows PowerShell ou n’est pas configuré pour la communication à distance dans Windows PowerShell.

À compter de Windows PowerShell 3,0, la propriété **__Server** de l’objet `Get-WmiObject` retourné par a un alias **PSComputerName** . Vous pouvez ainsi inclure plus facilement le nom de l'ordinateur source dans la sortie et dans les rapports.

## EXEMPLES

### Exemple 1 : récupérer des processus sur l’ordinateur local

Cet exemple obtient les processus sur l’ordinateur local.

```powershell
Get-WmiObject -Class Win32_Process
```

### Exemple 2 : obtenir des services sur un ordinateur distant

Cet exemple obtient les services sur un ordinateur distant. Le paramètre **ComputerName** spécifie l’adresse IP d’un ordinateur distant. Par défaut, le compte d’utilisateur actuel doit être membre du groupe **administrateurs** sur l’ordinateur distant.

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### Exemple 3 : récupération des classes WMI dans l’espace de noms racine ou par défaut de l’ordinateur local

Cet exemple obtient les classes WMI dans l’espace de noms racine ou par défaut de l’ordinateur local.

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### Exemple 4 : obtenir un service nommé sur plusieurs ordinateurs

Cet exemple obtient le service WinRM sur les ordinateurs spécifiés par la valeur du paramètre **ComputerName** .

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

Un opérateur de pipeline (|) envoie la sortie vers l'applet de commande `Format-List`, laquelle ajoute la propriété **PSComputerName** à la sortie par défaut. **PSComputerName** est un alias de la propriété **__Server** des objets `Get-WmiObject` retournées par. Cet alias a été introduit dans PowerShell 3,0.

### Exemple 5 : arrêter un service sur un ordinateur distant

Cet exemple arrête le service WinRM sur un ordinateur distant. `Get-WmiObject` Obtient l’instance de l’objet de service WinRM sur SERVEUR01. Ensuite, il appelle la méthode **StopService** de la classe **Win32_Service** WMI sur cet objet.

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

Cela équivaut à utiliser l’applet de commande `Stop-Service` .

### Exemple 6 : récupération du BIOS sur l’ordinateur local

Cet exemple obtient les informations du BIOS de l’ordinateur local. Le paramètre **Property** de l' `Format-List` applet de commande est utilisé pour afficher toutes les propriétés de l’objet retourné dans une liste. Par défaut, seul le sous-ensemble de propriétés défini dans le `Types.ps1xml` fichier de configuration s’affiche.

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### Exemple 7 : obtenir les services sur un ordinateur distant

Cet exemple utilise le paramètre **Credential** de l' `Get-WmiObject` applet de commande pour obtenir les services sur un ordinateur distant. La valeur du paramètre **Credential** est un nom de compte d'utilisateur. L'utilisateur est invité à entrer un mot de passe.

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> Les informations d’identification ne peuvent pas être utilisées lors du ciblage de l’ordinateur local.

## PARAMETERS

### -Modifié

Obtient ou définit une valeur qui indique si les objets retournés par WMI doivent contenir des informations modifiées. En général, les informations modifiées sont des informations localisables jointes à l'objet WMI (descriptions de propriété et d'objet, par exemple).

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

### -AsJob

Exécute la commande en tant que tâche en arrière-plan. Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.

Quand vous utilisez le paramètre **AsJob** , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l'invite de commandes. Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche. Si `Get-WmiObject` est utilisé sur un ordinateur distant, la tâche est créée sur l’ordinateur local et les résultats des ordinateurs distants sont automatiquement retournés à l’ordinateur local. Pour gérer la tâche, utilisez les applets de commande contenant les applets de commande Job. Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.

> [!NOTE]
> pour utiliser ce paramètre avec des ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour l'accès distant. En outre, vous devez démarrer Windows PowerShell en utilisant l'option « Exécuter en tant qu'administrateur » dans Windows Vista et les versions ultérieures de Windows. Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).

Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).

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

### -Authentification

Spécifie le niveau d’authentification à utiliser avec la connexion WMI.
Les valeurs autorisées sont :

- -1 : Unchanged
- 0 : Default
- 1 : None (Aucune authentification n'est effectuée.)
- 2 : Connect (L'authentification est effectuée uniquement lorsque le client établit une relation avec l'application.)
- 3 : Call (L'authentification est effectuée uniquement au début de chaque appel, quand l'application reçoit une demande.)
- 4 : Packet (L'authentification est effectuée sur toutes les données reçues du client.)
- 5 : PacketIntegrity (toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.)
- 6 : PacketPrivacy (Les propriétés des autres niveaux d'authentification sont utilisées, et toutes les données sont chiffrées.)

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autorité

Spécifie l'autorité à utiliser pour authentifier la connexion WMI. Vous pouvez spécifier l'authentification Kerberos ou NTLM standard. Pour utiliser NTLM, affectez au paramètre d’autorité la valeur `ntlmdomain:<DomainName>` , où `<DomainName>` identifie un nom de domaine NTLM valide. Pour utiliser Kerberos, spécifiez `kerberos:<DomainName>\<ServerName>` . Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.

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

### -Classe

Spécifie le nom d'une classe WMI. Lors de l'utilisation de ce paramètre, l'applet de commande récupère des instances de la classe WMI.

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie l'ordinateur cible pour l'opération de gestion. Entrez un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP. Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'ordinateur local, le nom de domaine complet est requis.

La valeur par défaut est l'ordinateur local. Pour spécifier l'ordinateur local, par exemple dans une liste de noms d'ordinateur, utilisez « localhost », le nom de l'ordinateur local ou un point (.).

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell, laquelle utilise le service Gestion des services Web. Vous pouvez utiliser le paramètre **ComputerName** de `Get-WmiObject` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes WS-Management.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel. Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou User@Contoso.com . Vous pouvez également entrer un objet **PSCredential** , tel qu'un objet qui est retourné par l'applet de commande `Get-Credential`. Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe. Les informations d’identification ne peuvent pas être utilisées lors du ciblage de l’ordinateur local.

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

### -DirectRead

Spécifie si l'accès direct au fournisseur WMI est demandé pour la classe spécifiée, quelles que soient ses classes de base ou ses classes dérivées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

Active tous les privilèges de l'utilisateur actuel avant que la commande ne passe l'appel WMI.

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

### -Filter

Spécifie une clause **Where** à utiliser comme filtre. Utilise la syntaxe du langage de requêtes WMI (WQL).

> [!IMPORTANT]
> n'incluez pas le mot clé **Where** dans la valeur du paramètre. Par exemple, les commandes suivantes retournent uniquement les disques logiques dont le paramètre **DeviceID** a la valeur « c: » et les services ayant pour nom « WinRM », sans utiliser le mot clé **Where** .

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Emprunt d’identité

Spécifie le niveau d'emprunt d'identité à utiliser.

Les valeurs valides pour ce paramètre sont :

- 0 : Default. Lit le registre local pour le niveau d’emprunt d’identité par défaut. La valeur par défaut est généralement définie sur **emprunter l’identité** .
- 1 : Anonymous. Masque les informations d'identification de l'appelant.
- 2 : Identify. Permet aux objets d'interroger les informations d'identification de l'appelant.
- 3 : Impersonate. Permet aux objets d'utiliser les informations d'identification de l'appelant.
- 4 : Delegate. Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -List

Obtient les noms des classes WMI figurant dans l'espace de noms de l'espace de stockage WMI spécifié par le paramètre **Namespace** .

Si vous spécifiez le paramètre **List** , mais pas le paramètre **namespace** , `Get-WmiObject` utilise l’espace de noms **Root\Cimv2** par défaut. Cette applet de commande n’utilise pas l’entrée de Registre **par défaut** de l’espace de noms dans la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` clé de Registre pour déterminer l’espace de noms par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### Paramètres régionaux

Spécifie les paramètres régionaux par défaut pour les objets WMI.
Entrez une valeur au format MS_\<LCID\>.

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

### -Espace de noms

Lorsqu'il est utilisé avec le paramètre **Class** , le paramètre **Namespace** spécifie l'espace de noms de l'espace de stockage WMI dans lequel figure la classe WMI spécifiée. Lorsqu'il est utilisé avec le paramètre **List** , il spécifie l'espace de noms dans lequel collecter les informations sur la classe WMI.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Spécifie les propriétés de classe WMI à partir desquelles cette applet de commande obtient des informations. Entrez les noms des propriétés.

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

Exécute l'instruction utilisant le langage de requêtes WMI (WQL) spécifiée. Ce paramètre ne prend pas en charge les requêtes d'événement.

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recurse

Recherche l'espace de noms actuel et tous les autres espaces de noms pour le nom de classe spécifié par le paramètre **Class** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal d'opérations WMI pouvant être exécutées simultanément. Ce paramètre est valide uniquement lorsque le paramètre **AsJob** est utilisé dans la commande.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers `Get-WmiObject` .

## SORTIES

### PSObject ou System. Management. Automation. RemotingJob

Lorsque vous utilisez le paramètre **AsJob** , l'applet de commande retourne un objet de traitement. Dans le cas contraire, l’objet `Get-WmiObject` retourné dépend de la valeur du paramètre **Class** .

## REMARQUES

Pour accéder aux informations se rapportant à WMI sur un ordinateur distant, l'applet de commande doit s'exécuter sous un compte qui est membre du groupe des administrateurs locaux sur l'ordinateur distant. Le contrôle d'accès par défaut sur l'espace de noms WMI de l'espace de stockage distant peut également être modifié afin d'octroyer des droits d'accès à d'autres comptes.

Seules quelques propriétés de chaque classe WMI sont affichées par défaut. Le jeu de propriétés affichées pour chaque classe WMI est spécifié dans le fichier de configuration Types.ps1xml. Pour obtenir toutes les propriétés d’un objet WMI, utilisez `Get-Member` les `Format-List` applets de commande ou.

## LIENS CONNEXES

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
