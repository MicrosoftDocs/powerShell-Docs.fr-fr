---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: d0c5f0a967ecd6eb07d7268cc9e25be93cc5f34c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205626"
---
# Get-PSSessionConfiguration

## SYNOPSIS
Obtient les configurations de session inscrites sur l'ordinateur.

## SYNTAX

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## Description

L' `Get-PSSessionConfiguration` applet de commande obtient les configurations de session qui ont été inscrites sur l’ordinateur local. Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.

À compter de PowerShell 3,0, vous pouvez définir les propriétés d’une configuration de session à l’aide d’un fichier de configuration de session (. PSSC). Cette fonctionnalité vous permet de créer des sessions personnalisées et restreintes sans avoir à écrire un programme informatique. Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

En outre, à compter de PowerShell 3,0, de nouvelles propriétés de note ont été ajoutées à l’objet de configuration de session `Get-PSSessionConfiguration` retourné par. Ces propriétés permettent aux utilisateurs et aux auteurs de configuration de session d'examiner et de comparer les configurations de session facilement.

Pour créer et inscrire une configuration de session, utilisez l’applet de commande `Register-PSSessionConfiguration` .
Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

## EXEMPLES

### Exemple 1 : récupération des configurations de session sur l’ordinateur local

```powershell
Get-PSSessionConfiguration
```

### Exemple 2 : récupération des deux configurations de session par défaut

La commande utilise le paramètre **Name** de `Get-PSSessionConfiguration` pour récupérer uniquement les configurations de session dont les noms commencent par « Microsoft ».

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### Exemple 3 : obtenir les propriétés et les valeurs d’une configuration de session

Cet exemple illustre les propriétés et les valeurs de propriété d'une configuration de session qui a été créée à l'aide d'un fichier de configuration de session.

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

L’exemple utilise l' `Get-PSSessionConfiguration` applet de commande pour obtenir la configuration de session complète. Un opérateur de pipeline envoie la configuration de session complète à l’applet de commande `Format-List` . Le paramètre **Property** avec la valeur `*` (All) est dirigé vers l’affichage de `Format-List` toutes les propriétés et valeurs de l’objet dans une liste.

La sortie inclut des informations utiles, notamment l’auteur de la configuration de session, le type de session, le mode de langage et la stratégie d’exécution des sessions créées avec cette configuration de session, les quotas de session et le chemin d’accès complet au fichier de configuration de session.

Cette vue d'une configuration de session est utilisée pour les sessions qui incluent un fichier de configuration de session.
Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

### Exemple 4 : autre moyen d’examiner les configurations de session

Cet exemple utilise l' `Get-ChildItem` applet de commande (alias `dir` ) dans le lecteur WSMan : Provider pour examiner le contenu du nœud de plug-in. Il s'agit d'une autre façon d'examiner les configurations de session sur l'ordinateur.

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

Le nœud de **plug-in** contient des objets **ContainerElement** (Microsoft. WSMan. Management. WSManConfigContainerElement) qui représentent les configurations de session PowerShell inscrites, ainsi que d’autres plug-ins pour WS-Management.

### Exemple 6 : afficher les configurations de session sur un ordinateur distant

Cet exemple montre comment utiliser le fournisseur WSMan pour afficher les configurations de session sur un ordinateur distant. Cette méthode ne fournit pas autant d’informations qu’une `Get-PSSessionConfiguration` commande, mais l’utilisateur n’a pas besoin d’être membre du groupe administrateurs pour exécuter cette applet de commande.

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

L' `Connect-WSMan` applet de commande se connecte au service WinRM sur l’ordinateur distant SERVEUR01. L' `Get-ChildItem` applet `dir` de commande (alias) du lecteur WSMan : obtient les éléments du chemin d’accès **Server01\Plugin** . La sortie affiche les éléments dans le répertoire Plugin sur l'ordinateur Server01. Les éléments incluent les configurations de session, qui sont un type de plug-in WSMan, ainsi que d'autres types de plug-in sur l'ordinateur.

### Exemple 7 : obtenir des configurations de session détaillées à partir d’un ordinateur distant

Cet exemple montre comment exécuter une `Get-PSSessionConfiguration` commande sur un ordinateur distant. La commande nécessite que la délégation CredSSP soit activée dans les paramètres du client sur l'ordinateur local et dans les paramètres de service sur l'ordinateur distant.

Pour exécuter les commandes de cet exemple, vous devez être membre du groupe Administrateurs sur les ordinateurs locaux et distants, et vous devez démarrer PowerShell avec l’option **exécuter en tant qu’administrateur** .

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

L' `Enable-WSManCredSSP` applet de commande active la délégation **CredSSP** sur SERVEUR01, l’ordinateur local. L' `Connect-WSMan` applet de commande se connecte à l’ordinateur Server02. Cette action ajoute un nœud pour Server02 au lecteur WSMan : sur l’ordinateur local, ce qui vous permet d’afficher et de modifier les paramètres de WS-Management sur l’ordinateur Server02. L' `Set-Item` applet de commande remplace la valeur de l’élément **CredSSP** dans le nœud service de l’ordinateur Server02 par **true** . Cela configure les paramètres de service sur l'ordinateur distant. L' `Invoke-Command` applet `Get-PSSessionConfiguration` de commande exécute la commande sur l’ordinateur Server02. La commande utilise le paramètre **Credential** , ainsi que le paramètre **Authentication** avec la valeur **CredSSP** . La sortie indique les configurations de session sur l'ordinateur distant Server02.

### Exemple 8 : obtenir l’URI de ressource d’une configuration de session

Cet exemple est utile pour définir la valeur de la `$PSSessionConfigurationName` variable de préférence, qui prend un URI de ressource.

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

La `$PSSessionConfigurationName` variable spécifie la configuration par défaut utilisée lors de la création d’une session. Cette variable est définie sur l'ordinateur local, mais elle spécifie une configuration sur l'ordinateur distant. Pour plus d’informations sur la `$PSSessionConfiguration` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

## PARAMETERS

### -Force

Supprime l'invite de redémarrage du service WinRM, si le service n'est pas déjà en cours d'exécution.

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

### -Name

Obtient uniquement les configurations de session portant le nom ou le modèle de nom spécifié. Entrez un ou plusieurs noms de configuration de session. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration

## REMARQUES

- Pour exécuter cette applet de commande, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

- Pour afficher les configurations de session sur l'ordinateur, vous devez être membre du groupe Administrateurs sur l'ordinateur.

- Pour exécuter une `Get-PSSessionConfiguration` commande sur un ordinateur distant, l’authentification du fournisseur de services de sécurité des informations d’identification (CredSSP) doit être activée dans les paramètres du client sur l’ordinateur local (à l’aide de la `Enable-WSManCredSSP` cmdlet) et dans les paramètres de service sur l’ordinateur distant. En outre, vous devez utiliser la valeur **CredSSP** du paramètre **Authentication** lors de l’établissement de la session à distance. Dans le cas contraire, l'accès est refusé.

- Les propriétés de note de l’objet qui `Get-PSSessionConfiguration` retourne s’affichent sur l’objet uniquement lorsqu’elles ont une valeur. Seules les configurations de session créées à l’aide d’un fichier de configuration de session ont toutes les propriétés définies.

- Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options. En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.

- Vous pouvez utiliser les commandes du lecteur WSMan pour modifier les propriétés des configurations de session.
  Toutefois, vous ne pouvez pas utiliser le lecteur WSMan : dans PowerShell 2,0 pour modifier les propriétés de configuration de session introduites dans PowerShell 3,0, telles que **OutputBufferingMode** . Les commandes PowerShell 2,0 ne génèrent pas d’erreur, mais elles sont inefficaces. Pour modifier les propriétés introduites dans PowerShell 3,0, utilisez le lecteur WSMan : dans PowerShell 3,0.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
