---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205282"
---
# Invoke-WmiMethod

## SYNOPSIS
Appelle les méthodes WMI.

## SYNTAX

### classe (par défaut)

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### query

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Invoke-WmiMethod` applet de commande appelle les méthodes des objets Windows Management Instrumentation (WMI).

Les nouvelles applets de commande Common Information Model (CIM), introduites dans Windows PowerShell 3,0, effectuent les mêmes tâches que les applets de commande WMI. Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme CIM, qui permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs Windows et ceux qui exécutent d’autres systèmes d’exploitation. Au lieu d’utiliser `Invoke-WmiMethod` , envisagez d’utiliser [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).

## EXEMPLES

### Exemple 1 : répertorier l’ordre requis des objets WMI

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

Cette commande répertorie l’ordre requis des objets. L’appel de WMI dans PowerShell 3.0 diffère des autres méthodes et nécessite que les valeurs d’objets soient entrées dans un ordre spécifique.

### Exemple 2 : démarrer une instance d’une application

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

Cette commande démarre une instance du bloc-notes en appelant la `Create` méthode de la classe **Win32_Process** .

La propriété **returnValue** est remplie avec un 0 et la propriété **ProcessID** est remplie avec un entier (numéro d’ID de processus suivant) si la commande est terminée.

### Exemple 3 : renommer un fichier

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

Cette commande renomme un fichier. Elle utilise le paramètre **path** pour référencer une instance de la classe **CIM_Datafile** . Elle applique ensuite la méthode Rename à cette instance particulière.

La propriété **returnValue** est remplie avec un 0 si la commande est terminée.

### Exemple 4 : passage d’un tableau de valeurs à l’aide de `-ArgumentList`

Exemple utilisant un tableau d’objets `$binSD` suivi d’une `$null` valeur.

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## PARAMETERS

### -ArgumentList

Spécifie les paramètres à passer à la méthode appelée. La valeur de ce paramètre doit être un tableau d’objets et doit apparaître dans l’ordre requis par la méthode appelée. L' `Invoke-CimCommand` applet de commande n’a pas ces limitations.

Pour déterminer l’ordre dans lequel répertorier ces objets, exécutez la `GetMethodParameters()` méthode sur la classe WMI, comme illustré dans l’exemple 1, à la fin de cette rubrique.

> [!IMPORTANT]
> si la première valeur est un tableau qui contient plusieurs éléments, une seconde valeur $null est requise. Sinon, la commande génère une erreur, par exemple « Impossible d’effectuer un cast d’un objet de type ’System.Byte’ en type ’System.Array’ ». Consultez l’exemple 4 ci-dessus.

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan. Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.

Quand vous utilisez le paramètre **AsJob** , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l'invite de commandes. Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche. Si `Invoke-WmiMethod` est utilisé sur un ordinateur distant, la tâche est créée sur l’ordinateur local et les résultats des ordinateurs distants sont automatiquement retournés à l’ordinateur local. Pour gérer la tâche, utilisez les applets de commande contenant le nom Job (applets de commande Job). Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.

pour utiliser ce paramètre avec des ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour l'accès distant. En outre, vous devez démarrer Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur dans Windows Vista et les versions ultérieures de Windows. Pour plus d'informations, consultez about_Remote_Requirements.

Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez about_Jobs et about_Remote_Jobs.

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

Spécifie le niveau d’authentification à utiliser avec la connexion WMI. Les valeurs valides pour ce paramètre sont :

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
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autorité

Spécifie l'autorité à utiliser pour authentifier la connexion WMI. Vous pouvez spécifier l’authentification Windows NT LAN Manager (NTLM) ou Kerberos standard. Pour utiliser NTLM, affectez au paramètre d'autorité la valeur ntlmdomain:\<DomainName\>, où \<DomainName\> identifie un nom de domaine NTLM valide. Pour utiliser Kerberos, spécifiez Kerberos : \<DomainName\ServerName\> . Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Classe

Spécifie la classe WMI qui contient une méthode statique à appeler.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie, sous forme de tableau de chaînes, les ordinateurs sur lesquels cette applet de commande exécute la commande. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel. Tapez un nom d’utilisateur, tel que `User01` , `Domain01\User01` ou `User@Contoso.com` . Ou entrez un objet **PSCredential** , tel qu’un objet qui est retourné par l’applet de commande Get-Credential. Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

Indique que cette applet de commande active tous les privilèges de l’utilisateur actuel avant que la commande effectue l’appel WMI.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Emprunt d’identité

Spécifie le niveau d'emprunt d'identité à utiliser. Les valeurs valides pour ce paramètre sont :

- 0 : Default (Lit le Registre local pour connaître le niveau d'emprunt d'identité par défaut, qui a généralement la valeur « 3 : Impersonate ».)
- 1 : Anonymous (Masque les informations d'identification de l'appelant.)
- 2 : Identify (Permet aux objets d'interroger les informations d'identification de l'appelant.)
- 3 : Impersonate (Permet aux objets d'utiliser les informations d'identification de l'appelant.)
- 4 : Delegate (Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.)

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie un objet **ManagementObject** à utiliser comme entrée. Quand ce paramètre est utilisé, tous les autres paramètres, à l’exception des paramètres **Flag** et **argument** , sont ignorés.

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### Paramètres régionaux

Spécifie les paramètres régionaux par défaut pour les objets WMI. Spécifiez la valeur du paramètre **locale** sous la forme d’un tableau au `MS_<LCID>` format dans l’ordre de préférence.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom de la méthode à appeler. Ce paramètre est obligatoire et ne peut ni avoir la valeur Null ni être vide.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms

Lorsqu’il est utilisé avec le paramètre **Class** , ce paramètre spécifie l’espace de noms de l’espace de stockage WMI dans lequel se trouve la classe ou l’objet WMI référencé.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès de l’objet WMI d’une classe WMI, ou spécifie le chemin d’accès de l’objet WMI d’une instance d’une classe WMI. La classe ou l’instance que vous spécifiez doit contenir la méthode spécifiée dans le paramètre **Name** .

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie une valeur de limitation pour le nombre d’opérations WMI qui peuvent être exécutées simultanément.
Ce paramètre est utilisé conjointement avec le paramètre **AsJob** . La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

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

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

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

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucune entrée.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[Get-WmiObject](Get-WmiObject.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)
