---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203493"
---
# Set-WmiInstance

## SYNOPSIS
Crée ou met à jour une instance d'une classe WMI (Windows Management Instrumentation) existante.

## SYNTAX

### classe (par défaut)

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### query

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L' `Set-WmiInstance` applet de commande crée ou met à jour une instance d’une classe Windows Management Instrumentation (WMI) existante.
L'instance créée ou mise à jour est écrite dans l'espace de stockage WMI.

De nouvelles applets de commande CIM, introduites dans Windows PowerShell 3.0, effectuent les mêmes tâches que les applets de commande WMI.
Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme Common Information Model (CIM).
Cela permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs Windows et ceux qui exécutent d’autres systèmes d’exploitation.
Au lieu d’utiliser `Set-WmiInstance` , envisagez d’utiliser les applets de commande [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) ou [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) .

## EXEMPLES

### Exemple 1 : définir le niveau de journalisation WMI

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

Cette commande affecte la valeur 2 au niveau de journalisation WMI.
La commande passe la propriété à définir et la valeur, ensemble considérée comme une paire de valeurs, dans le paramètre d’argument.
Le paramètre accepte une table de hachage qui est définie par la construction @{propriété = valeur}.
Les informations de classe qui sont retournées reflètent la nouvelle valeur.

### Exemple 2 : créer une variable d’environnement et sa valeur

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

Cette commande crée la variable d’environnement testvar qui a la valeur TestValue.
Pour ce faire, il crée une nouvelle instance de la classe **Win32_Environment** WMI.
Cette opération nécessite des informations d’identification appropriées et vous devrez peut-être redémarrer Windows PowerShell pour afficher la nouvelle variable d’environnement.

### Exemple 3 : définir le niveau de journalisation WMI pour plusieurs ordinateurs distants

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

Cette commande affecte la valeur 2 au niveau de journalisation WMI.
La commande passe la propriété à définir et la valeur, ensemble considérée comme une paire de valeurs, dans le paramètre d’argument.
Le paramètre accepte une table de hachage qui est définie par la construction @{propriété = valeur}.
L'information de classe retournée reflète la nouvelle valeur.

## PARAMETERS

### -Arguments
Spécifie le nom de la propriété à modifier et la nouvelle valeur pour cette propriété.
Le nom et la valeur doivent être une paire nom-valeur.
La paire nom-valeur est passée sur la ligne de commande en tant que table de hachage.
Par exemple :

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
Indique que ce cmdket s’exécute en tant que tâche en arrière-plan.
Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.

Lorsque vous spécifiez le paramètre *AsJob* , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l’invite de commandes.
Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.
Si **Set-WmiInstance** est utilisé pour un ordinateur distant, la tâche est créée sur l’ordinateur local et les résultats des ordinateurs distants sont automatiquement retournés à l’ordinateur local.
Pour gérer le travail, utilisez les applets de commande qui contiennent le nom du **travail** (les applets de commande **Job** ).
Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.

Pour utiliser ce paramètre avec des ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.
En outre, vous devez démarrer Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur dans Windows Vista et les versions ultérieures du système d’exploitation Windows.
Pour plus d'informations, consultez about_Remote_Requirements.

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
Spécifie le niveau d’authentification qui doit être utilisé avec la connexion WMI.
Les valeurs valides pour ce paramètre sont :

- -1 : inchangé.
- 0 : Default.
- 1 : aucune.
Aucune authentification n’est effectuée.
- 2 : se connecter.
L’authentification est effectuée uniquement lorsque le client établit une relation avec l’application.
- 3 : appeler.
L’authentification est effectuée uniquement au début de chaque appel lorsque l’application reçoit la demande.
- 4 : paquet.
L’authentification est effectuée sur toutes les données reçues du client.
- 5 : PacketIntegrity.
Toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.
- 6 : PacketPrivacy.
Les propriétés des autres niveaux d’authentification sont utilisées, et toutes les données sont chiffrées.

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
Spécifie l'autorité à utiliser pour authentifier la connexion WMI.
Vous pouvez spécifier l'authentification Kerberos ou NTLM standard.
Pour utiliser NTLM, affectez au paramètre d'autorité la valeur ntlmdomain:\<DomainName\>, où \<DomainName\> identifie un nom de domaine NTLM valide.
Pour utiliser Kerberos, spécifiez Kerberos : \<DomainName\> \\ \<ServerName\> .
Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.

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
Spécifie le nom d'une classe WMI.

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
Spécifie le nom de l’ordinateur sur lequel cette applet de commande s’exécute.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.

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
Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande Get-Credential.
Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Ce paramètre n’est pas pris en charge par les fournisseurs installés avec le paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.

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
Indique que cette applet de commande active toutes les autorisations de l’utilisateur actuel avant la commande qu’il effectue l’appel WMI.

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
Spécifie le niveau d'emprunt d'identité à utiliser.
Les valeurs valides pour ce paramètre sont :

- 0 : Default.
Lit le registre local pour le niveau d’emprunt d’identité par défaut, qui est généralement défini sur 3 : Impersonate.
- 1 : Anonymous.
Masque les informations d'identification de l'appelant.
- 2 : Identify.
Permet aux objets d'interroger les informations d'identification de l'appelant.
- 3 : Impersonate.
Permet aux objets d'utiliser les informations d'identification de l'appelant.
- 4 : Delegate.
Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.

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
Spécifie un objet **ManagementObject** à utiliser comme entrée.
Lorsque ce paramètre est utilisé, tous les autres paramètres, à l’exception du paramètre *arguments* , sont ignorés.

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
Spécifie les paramètres régionaux par défaut pour les objets WMI.
Les paramètres *régionaux* sont spécifiés dans un tableau au format MS_ \<LCID\> dans l’ordre par défaut.

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

### -Espace de noms
Spécifie l’espace de noms de l’espace de stockage WMI dans lequel se trouve la classe WMI référencée lorsqu’elle est utilisée avec le paramètre de *classe* .

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
Spécifie un chemin d’accès d’objet WMI de l’instance que vous souhaitez créer ou mettre à jour.

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

### -PutType
Indique s’il convient de créer ou de mettre à jour l’instance WMI.
Les valeurs valides pour ce paramètre sont :

- UpdateOnly.
met à jour une instance WMI existante.
- CreateOnly.
crée une instance WMI.
- UpdateOrCreate.
met à jour l'instance WMI si elle existe, ou crée une instance s'il n'existe aucune instance.

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Ce paramètre est utilisé conjointement avec le paramètre *AsJob* .
La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

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
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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
Cette applet de commande n'accepte aucune entrée.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)
