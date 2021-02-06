---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Module d’importation
ms.openlocfilehash: 1b8164be05f011e13945323a6288426bd2d41183
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "99603888"
---
# Module d’importation

## SYNOPSIS
Ajoute des modules à la session active.

## SYNTAXE

### Nom (par défaut)

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### PSSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### CimSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### UseWindowsPowerShell

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### FullyQualifiedName

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### FullyQualifiedNameAndPSSession

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### FullyQualifiedNameAndUseWindowsPowerShell

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### Assembly

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### ModuleInfo

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## Description

L' `Import-Module` applet de commande ajoute un ou plusieurs modules à la session active. À compter de PowerShell 3,0, les modules installés sont automatiquement importés dans la session lorsque vous utilisez des commandes ou des fournisseurs dans le module. Toutefois, vous pouvez toujours utiliser la `Import-Module` commande pour importer un module.
Vous pouvez désactiver l’importation automatique de modules à l’aide de la `$PSModuleAutoloadingPreference` variable de préférence. Pour plus d’informations sur la `$PSModuleAutoloadingPreference` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

Un module est un package qui contient des membres qui peuvent être utilisés dans PowerShell. Les membres incluent des applets de commande, des fournisseurs, des scripts, des fonctions, des variables et d’autres outils et fichiers. Après avoir importé un module, vous pouvez utiliser ses membres dans votre session. Pour plus d’informations sur les modules, consultez [about_Modules](About/about_Modules.md).

Par défaut, `Import-Module` importe tous les membres que le module exporte, mais vous pouvez utiliser les paramètres **alias**, **Function**, **applets** de commande et **variables** pour limiter les membres qui sont importés. Le paramètre **NoClobber** empêche `Import-Module` d’importer des membres qui ont les mêmes noms que les membres de la session active.

`Import-Module` importe un module uniquement dans la session active. Pour importer le module dans chaque nouvelle session, ajoutez une `Import-Module` commande à votre profil PowerShell. Pour plus d'informations sur les profils, consultez [about_Profiles](About/about_Profiles.md).

Vous pouvez gérer les ordinateurs Windows distants pour lesquels la communication à distance PowerShell est activée en créant une **session PSSession** sur l’ordinateur distant. Utilisez ensuite le paramètre **PSSession** de `Import-Module` pour importer les modules installés sur l’ordinateur distant. Lorsque vous utilisez les commandes importées dans la session active, les commandes s’exécutent implicitement sur l’ordinateur distant.

À partir de Windows PowerShell 3,0, vous pouvez utiliser `Import-Module` pour importer des modules Common Information Model (CIM). Les modules CIM définissent des applets de commande dans des fichiers CDXML (cmdlet Definition XML). Cette fonctionnalité vous permet d’utiliser des applets de commande qui sont implémentées dans des assemblys de code non managé, telles que celles écrites en C++.

Pour les ordinateurs distants sur lesquels la communication à distance PowerShell n’est pas activée, y compris les ordinateurs qui n’exécutent pas le système d’exploitation Windows, vous pouvez utiliser le paramètre **CIMSession** de `Import-Module` pour importer des modules CIM à partir de l’ordinateur distant. Les commandes importées s’exécutent implicitement sur l’ordinateur distant. Un **CIMSession** est une connexion à Windows Management Instrumentation (WMI) sur l’ordinateur distant.

## EXEMPLES

### Exemple 1 : importer les membres d’un module dans la session active

Cet exemple importe les membres du module **PSDiagnostics** dans la session active.

```powershell
Import-Module -Name PSDiagnostics
```

### Exemple 2 : importer tous les modules spécifiés par le chemin d’accès du module

Cet exemple importe tous les modules disponibles dans le chemin d’accès spécifié par la `$env:PSModulePath` variable d’environnement dans la session active.

```powershell
Get-Module -ListAvailable | Import-Module
```

### Exemple 3 : importer les membres de plusieurs modules dans la session active

Cet exemple importe les membres des modules **PSDiagnostics** et **DISM** dans la session active.

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

L' `Get-Module` applet de commande obtient les modules **PSDiagnostics** et **DISM** et enregistre les objets dans la `$m` variable. Le paramètre **listAvailable** est obligatoire lorsque vous obtenez des modules qui ne sont pas encore importés dans la session.

Le paramètre **ModuleInfo** de `Import-Module` est utilisé pour importer les modules dans la session active.

### Exemple 4 : importer tous les modules spécifiés par un chemin d’accès

Cet exemple utilise un chemin d’accès explicite pour identifier le module à importer.

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

L’utilisation du paramètre **Verbose** entraîne le `Import-Module` signalement de la progression au cours du chargement du module.
Sans le paramètre **Verbose**, **PassThru** ou **AsCustomObject** , `Import-Module` ne génère pas de sortie lors de l’importation d’un module.

### Exemple 5 : limiter les membres de module importés dans une session

Cet exemple montre comment limiter les membres de module qui sont importés dans la session et l’effet de cette commande sur la session. Le paramètre de **fonction** limite les membres importés à partir du module. Vous pouvez également utiliser les paramètres **alias**, **variable** et **applet** de commande pour restreindre les autres membres qu’un module importe.

L' `Get-Module` applet de commande obtient l’objet qui représente le module **PSDiagnostics** . La propriété **ExportedCmdlets** répertorie toutes les applets de commande exportées par le module, même si elles n’ont pas été importées.

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

L’utilisation du paramètre **module** de l' `Get-Command` applet de commande affiche les commandes qui ont été importées à partir du module **PSDiagnostics** . Les résultats confirment que seules `Disable-PSTrace` les `Enable-PSTrace` applets de commande et ont été importées.

### Exemple 6 : importer les membres d’un module et ajouter un préfixe

Cet exemple importe le module **PSDiagnostics** dans la session active, ajoute un préfixe aux noms des membres, puis affiche les noms des membres préfixés. Le paramètre **prefix** de `Import-Module` ajoute le préfixe **x** à tous les membres qui sont importés à partir du module. Le préfixe s’applique uniquement aux membres de la session active. Il ne modifie pas le module. Le paramètre **PassThru** retourne un objet de module qui représente le module importé.

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

`Get-Command` Obtient les membres qui ont été importés à partir du module. La sortie indique que les membres de module ont été correctement préfixés.

### Exemple 7 : obtenir et utiliser un objet personnalisé

Cet exemple montre comment récupérer et utiliser l’objet personnalisé retourné par `Import-Module` .

Les objets personnalisés incluent des membres synthétiques représentant chacun des membres de module importés. Par exemple, les applets de commande et les fonctions dans un module sont converties en méthodes de script de l'objet personnalisé.

Les objets personnalisés sont utiles pour l’écriture de scripts. Ils sont également utiles quand plusieurs objets importés ont le même nom. Utiliser la méthode de script d'un objet équivaut à spécifier le nom qualifié complet d'un membre importé, y compris son nom de module.

Le paramètre **AsCustomObject** peut être utilisé uniquement lors de l’importation d’un module de script. Utilisez `Get-Module` pour déterminer lequel des modules disponibles est un module de script.

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

Le `Show-Calendar` module de script est importé à l’aide du paramètre **AsCustomObject** pour demander un objet personnalisé et le paramètre **PassThru** pour retourner l’objet. L’objet personnalisé résultant est enregistré dans la `$a` variable.

La `$a` variable est dirigée vers l' `Get-Member` applet de commande pour afficher les propriétés et les méthodes de l’objet enregistré. La sortie illustre une `Show-Calendar` méthode de script.

Pour appeler la `Show-Calendar` méthode de script, le nom de la méthode doit être placé entre guillemets, car le nom contient un trait d’Union.

### Exemple 8 : réimporter un module dans la même session

Cet exemple montre comment utiliser le paramètre **force** de `Import-Module` lorsque vous réimportez un module dans la même session. Le paramètre **force** supprime le module chargé, puis le réimporte.

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

La première commande importe le module **PSDiagnostics** . La deuxième commande réimporte le module, cette fois en utilisant le paramètre **Prefix**.

Sans le paramètre **force** , la session inclut deux copies de chaque applet de commande **PSDiagnostics** , l’une avec le nom standard et l’autre avec le nom préfixé.

### Exemple 9 : exécuter des commandes qui ont été masquées par des commandes importées

Cet exemple montre comment exécuter des commandes qui ont été masquées par des commandes importées. Le module **TestModule** comprend une fonction nommée `Get-Date` qui retourne l’année et le jour de l’année.

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

La première `Get-Date` applet de commande retourne un objet **DateTime** avec la date actuelle. Après l’importation du module **TestModule** , `Get-Date` retourne l’année et le jour de l’année.

L’utilisation du paramètre **All** de `Get-Command` affiche toutes les `Get-Date` commandes dans la session. Les résultats montrent qu’il y a deux `Get-Date` commandes dans la session, une fonction du module **TestModule** et une applet de commande du module **Microsoft. PowerShell. Utility** .

Comme les fonctions sont prioritaires sur les applets de commande, la `Get-Date` fonction du module **TestModule** s’exécute à la place de l’applet de commande `Get-Date` . Pour exécuter la version d’origine de `Get-Date` , vous devez qualifier le nom de la commande avec le nom du module.

Pour plus d’informations sur la priorité des commandes dans PowerShell, consultez [about_Command_Precedence](about/about_Command_Precedence.md).

### Exemple 10 : importer une version minimale d’un module

Cet exemple importe le module **PowerShellGet** . Elle utilise le paramètre **MinimumVersion** de `Import-Module` pour importer uniquement la version 2.0.0 ou ultérieure du module.

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

Vous pouvez également utiliser le paramètre **RequiredVersion** pour importer une version particulière d’un module, ou utiliser les paramètres **module** et **version** du `#Requires` mot clé pour exiger une version particulière d’un module dans un script.

### Exemple 11 : importer à l’aide d’un nom complet

Cet exemple importe une version spécifique d’un module à l’aide de FullyQualifiedName.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### Exemple 12 : importer à l’aide d’un chemin d’accès complet

Cet exemple importe une version spécifique d’un module à l’aide du chemin d’accès qualifié complet.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### Exemple 13 : importer un module à partir d’un ordinateur distant

Cet exemple montre comment utiliser l' `Import-Module` applet de commande pour importer un module à partir d’un ordinateur distant.
Cette commande utilise la fonctionnalité de communication à distance implicite de PowerShell.

Quand vous importez des modules à partir d'une autre session, vous pouvez utiliser les applets de commande dans la session active.
Toutefois, les commandes qui utilisent les applets de commande s’exécutent dans la session à distance.

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

`New-PSSession` crée une session à distance (**PSSession**) sur l’ordinateur SERVEUR01. La **session PSSession** est enregistrée dans la `$s` variable.

Le `Get-Module` fait d’exécuter avec le paramètre **PSSession** indique que le module **netsecurity** est installé et disponible sur l’ordinateur distant. Cette commande revient à utiliser l' `Invoke-Command` applet de commande pour exécuter la `Get-Module` commande dans la session à distance. Par exemple : (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`

L’exécution `Import-Module` de avec le paramètre **PSSession** importe le module **netsecurity** à partir de l’ordinateur distant dans la session active. L' `Get-Command` applet de commande est utilisée pour récupérer les commandes qui commencent par le **pare-feu** d' **extraction** et d’inclusion dans le module **netsecurity** . La sortie confirme que le module et ses applets de commande ont été importés dans la session active.

Ensuite, l' `Get-NetFirewallRule` applet de commande obtient Windows Remote Management règles de pare-feu sur l’ordinateur SERVEUR01. Cela équivaut à utiliser l' `Invoke-Command` applet de commande pour s’exécuter `Get-NetFirewallRule` sur la session à distance.

### Exemple 14 : gérer le stockage sur un ordinateur distant sans système d’exploitation Windows

Dans cet exemple, l’administrateur de l’ordinateur a installé le fournisseur WMI de détection de module, qui vous permet d’utiliser des commandes CIM conçues pour le fournisseur.

L' `New-CimSession` applet de commande crée une session sur l’ordinateur distant nommé RSDGF03. La session se connecte au service WMI sur l’ordinateur distant. La session CIM est enregistrée dans la `$cs` variable.
`Import-Module` utilise le **CimSession** dans `$cs` pour importer le module CIM de **stockage** à partir de l’ordinateur RSDGF03.

L' `Get-Command` applet `Get-Disk` de commande affiche la commande dans le module de **stockage** . Lorsque vous importez un module CIM dans la session locale, PowerShell convertit les fichiers CDXML pour chaque commande en scripts PowerShell, qui apparaissent sous la forme de fonctions dans la session locale.

Bien que `Get-Disk` soit tapé dans la session locale, l’applet de commande s’exécute implicitement sur l’ordinateur distant à partir duquel elle a été importée. La commande retourne des objets de l’ordinateur distant à la session locale.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## PARAMETERS

### -Alias

Spécifie les alias que cette applet de commande importe à partir du module dans la session active. Entrez une liste séparée par des virgules des alias. Les caractères génériques sont autorisés.

Au moment de leur importation, certains modules exportent automatiquement les alias sélectionnés dans votre session.
Ce paramètre vous permet d'effectuer votre choix parmi les alias exportés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ArgumentList

Spécifie un tableau d’arguments, ou valeurs de paramètre, qui sont passés à un module de script pendant la `Import-Module` commande. Ce paramètre n’est valide que lorsque vous importez un module de script.

Vous pouvez également faire référence au paramètre **argumentlist** par son alias, **args**. Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

Indique que cette applet de commande retourne un objet personnalisé avec des membres qui représentent les membres de module importés. Ce paramètre n'est valide que pour les modules de script.

Quand vous utilisez le paramètre **AsCustomObject** , `Import-Module` importe les membres de module dans la session, puis retourne un objet **PSCustomObject** au lieu d’un objet **PSModuleInfo** . Vous pouvez enregistrer l'objet personnalisé dans une variable et utiliser la notation par points pour appeler les membres.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Assembly

Spécifie un tableau d’objets d’assembly. Cette applet de commande importe les applets de commande et les fournisseurs implémentés dans les objets d’assembly spécifiés. Entrez une variable qui contient les objets d'assembly ou une commande qui crée des objets d'assembly. Vous pouvez également diriger un objet assembly vers `Import-Module` .

Quand vous utilisez ce paramètre, seuls les applets de commande et les fournisseurs implémentés par les assemblys spécifiés sont importés. Si le module contient d’autres fichiers, ils ne sont pas importés et il se peut que vous ne soyez pas membre important du module. Utilisez ce paramètre pour déboguer et tester le module, ou quand vous êtes invité à l’utiliser par l’auteur du module.

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimNamespace

Spécifie l'espace de noms d'un autre fournisseur CIM qui expose des modules CIM. La valeur par défaut est l'espace de noms du fournisseur WMI pour la découverte de module.

Utilisez ce paramètre pour importer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas un système d’exploitation Windows.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

Spécifie un autre emplacement pour les modules CIM. La valeur par défaut est l’URI de ressource du fournisseur WMI de détection de module sur l’ordinateur distant.

Utilisez ce paramètre pour importer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas un système d’exploitation Windows.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

Spécifie une session CIM sur l'ordinateur distant. Entrez une variable qui contient la session CIM ou une commande qui obtient la session CIM, telle qu’une commande [CimSession](../CimCmdlets/Get-CimSession.md) .

`Import-Module` utilise la connexion de session CIM pour importer des modules à partir de l’ordinateur distant dans la session active. Lorsque vous utilisez les commandes du module importé dans la session active, les commandes s’exécutent sur l’ordinateur distant.

Vous pouvez utiliser ce paramètre pour importer des modules à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows, et d’ordinateurs Windows qui disposent de PowerShell, mais pour lesquels la communication à distance PowerShell n’est pas activée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Applet de commande

Spécifie un tableau d’applets de commande importées par cette applet de commande à partir du module dans la session active.
Les caractères génériques sont autorisés.

Au moment de leur importation, certains modules exportent automatiquement les applets de commande sélectionnées dans votre session.
Ce paramètre vous permet d'effectuer votre choix parmi les applets de commande exportées.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -DisableNameChecking

Indique que cette applet de commande supprime le message qui vous avertit lorsque vous importez une applet de commande ou une fonction dont le nom comprend un verbe non approuvé ou un caractère interdit.

Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, PowerShell affiche le message d’avertissement suivant :

> AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables. Utilisez le paramètre Verbose pour obtenir plus d'informations ou tapez Get-Verb pour afficher la liste des verbes approuvés.

Ce message n'est qu'un avertissement. Le module entier est toujours importé, y compris les commandes non conformes. Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Ce paramètre entraîne le chargement ou le rechargement d’un module au-dessus de celui en cours.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

Spécifie le nom qualifié complet du module sous la forme d’une table de hachage. La valeur peut être une combinaison de chaînes et de tables de hachage. La table de hachage a les clés suivantes.

- `ModuleName` - **Obligatoire** Spécifie le nom du module.
- `GUID` - **Facultatif** Spécifie le GUID du module.
- Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous. Ces clés ne peuvent pas être utilisées ensemble.
  - `ModuleVersion` -Spécifie une version minimale acceptable du module.
  - `RequiredVersion` -Spécifie une version exacte et obligatoire du module.
  - `MaximumVersion` -Spécifie la version maximale acceptable du module.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Fonction

Spécifie un tableau de fonctions que cette applet de commande importe à partir du module dans la session active.
Les caractères génériques sont autorisés. Au moment de leur importation, certains modules exportent automatiquement les fonctions sélectionnées dans votre session. Ce paramètre vous permet d'effectuer votre choix parmi les fonctions exportées.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Global

Indique que cette applet de commande importe des modules dans l’état de session global pour qu’ils soient disponibles pour toutes les commandes dans la session.

Par défaut, lorsque l' `Import-Module` applet de commande est appelée à partir de l’invite de commandes, d’un fichier de script ou d’un scriptblock, toutes les commandes sont importées dans l’état de session global.

Lorsqu’elle est appelée à partir d’un autre module, `Import-Module` l’applet de commande importe les commandes d’un module, y compris les commandes des modules imbriqués, dans l’état de session du module appelant.

> [!TIP]
> Vous devez éviter `Import-Module` d’appeler à partir d’un module. Au lieu de cela, déclarez le module cible comme un module imbriqué dans le manifeste du module parent. La déclaration des modules imbriqués améliore la détectabilité des dépendances.

Le paramètre **Global** équivaut au paramètre **Scope** avec la valeur **Global**.

Pour restreindre les commandes qu’un module exporte, utilisez une `Export-ModuleMember` commande dans le module de script.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie une version maximale. Cette applet de commande importe uniquement une version du module qui est inférieure ou égale à la valeur spécifiée. Si aucune version n’est qualifiée, `Import-Module` retourne une erreur.

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie une version minimale. Cette applet de commande importe uniquement une version du module qui est supérieure ou égale à la valeur spécifiée. Utilisez le nom de paramètre **MinimumVersion** ou son alias, **Version**. Si aucune version n’est qualifiée, `Import-Module` génère une erreur.

Pour spécifier une version exacte, utilisez le paramètre **RequiredVersion**. Vous pouvez également utiliser les paramètres **module** et **version** du mot clé **#Requires** pour exiger une version spécifique d’un module dans un script.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleInfo

Spécifie un tableau d’objets de module à importer. Entrez une variable qui contient les objets de module ou une commande qui obtient les objets de module, tels que la commande suivante : `Get-Module -ListAvailable` . Vous pouvez également diriger les objets de module vers `Import-Module` .

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des modules à importer. Entrez le nom du module ou le nom d’un fichier dans le module, tel qu’un `.psd1` fichier, `.psm1` , `.dll` ou `.ps1` . Les chemins d'accès aux fichiers sont facultatifs. Les caractères génériques ne sont pas autorisés. Vous pouvez également diriger les noms de module et les noms de fichiers vers `Import-Module` .

Si vous omettez un chemin d’accès, `Import-Module` recherche le module dans les chemins d’accès enregistrés dans la `$env:PSModulePath` variable d’environnement.

Spécifiez uniquement le nom du module chaque fois que possible. Quand vous spécifiez un nom de fichier, seuls les membres qui sont implémentés dans ce fichier sont importés. Si le module contient d’autres fichiers, ils ne sont pas importés et il se peut que vous ne soyez pas membre important du module.

> [!NOTE]
> Bien qu’il soit possible d’importer un fichier de script ( `.ps1` ) en tant que module, les fichiers de script ne sont généralement pas structurés comme un fichier de modules de script ( `.psm1` ). L’importation d’un fichier de script ne garantit pas qu’il est utilisable en tant que module. Pour plus d’informations, consultez [about_Modules](about/about_Modules.md).

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -NoClobber

Empêche l’importation des commandes qui ont les mêmes noms que les commandes existantes dans la session active. Par défaut, `Import-Module` importe toutes les commandes de module exportées.

Les commandes qui ont le même nom peuvent masquer ou remplacer des commandes dans la session. Pour éviter les conflits de nom de commande dans une session, utilisez les paramètres **Prefix** ou **NoClobber**. Pour plus d'informations sur les conflits de nom et la priorité des commandes, consultez « Modules et conflits de noms » dans [about_Modules](about/about_Modules.md) et [about_Command_Precedence](about/about_Command_Precedence.md).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prefix

Spécifie un préfixe que cette applet de commande ajoute aux noms des membres de module importés.

Utilisez ce paramètre pour éviter les conflits de noms qui peuvent se produire quand des membres différents dans la session ont le même nom. Ce paramètre ne modifie pas le module, et il n’affecte pas les fichiers que le module importe pour son propre usage. Ils sont appelés modules imbriqués. Cette applet de commande affecte uniquement les noms des membres dans la session active.

Par exemple, si vous spécifiez le préfixe UTC, puis importez une applet de commande `Get-Date` , l’applet de commande est connue dans la session en tant que `Get-UTCDate` , et elle n’est pas confondue avec l’applet de commande d’origine `Get-Date` .

La valeur de ce paramètre est prioritaire sur la propriété **DefaultCommandPrefix** du module, qui spécifie le préfixe par défaut.

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

### -PSSession

Spécifie une session PowerShell managée par l’utilisateur (**PSSession**) à partir de laquelle cette applet de commande importe des modules dans la session active. Entrez une variable qui contient une **session PSSession** ou une commande qui obtient une **session PSSession**, telle qu’une `Get-PSSession` commande.

Quand vous importez un module à partir d'une autre session dans la session active, vous pouvez utiliser les applets de commande du module dans la session active, tout comme vous utiliseriez des applets de commande à partir d'un module local. Les commandes qui utilisent les applets de commande distantes s’exécutent dans la session à distance, mais les détails de l’accès distant sont gérés en arrière-plan par PowerShell.

Ce paramètre utilise la fonctionnalité de communication à distance implicite de PowerShell. Cela équivaut à utiliser l' `Import-PSSession` applet de commande pour importer des modules particuliers à partir d’une session.

`Import-Module` Impossible d’importer les modules PowerShell Core à partir d’une autre session. Les modules PowerShell Core portent des noms qui commencent par Microsoft. PowerShell.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie une version du module que cette applet de commande importe. Si la version n’est pas installée, `Import-Module` génère une erreur.

Par défaut, `Import-Module` importe le module sans vérifier le numéro de version.

Pour spécifier une version minimale, utilisez le paramètre **MinimumVersion**. Vous pouvez également utiliser les paramètres **module** et **version** du mot clé **#Requires** pour exiger une version spécifique d’un module dans un script.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

Les scripts qui utilisent **RequiredVersion** pour importer des modules inclus avec les versions existantes du système d’exploitation Windows ne s’exécutent pas automatiquement dans les versions ultérieures du système d’exploitation Windows. En effet, les numéros de version de module PowerShell dans les versions ultérieures du système d’exploitation Windows sont plus élevés que les numéros de version de module dans les versions existantes du système d’exploitation Windows.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Étendue

Spécifie une étendue dans laquelle cette applet de commande importe le module.

Les valeurs valides pour ce paramètre sont :

- **Global**. disponible pour toutes les commandes dans la session. Équivalent au paramètre **Global**.
- **Local**. Disponible uniquement dans l'étendue actuelle.

Par défaut, lorsque l' `Import-Module` applet de commande est appelée à partir de l’invite de commandes, d’un fichier de script ou d’un scriptblock, toutes les commandes sont importées dans l’état de session global. Vous pouvez utiliser le `-Scope Local` paramètre pour importer le contenu d’un module dans la portée du script ou du scriptblock.

Lorsqu’elle est appelée à partir d’un autre module, `Import-Module` l’applet de commande importe les commandes d’un module, y compris les commandes des modules imbriqués, dans l’état de session de l’appelant. La spécification de `-Scope Global` ou `-Global` indique que cette applet de commande importe des modules dans l’état de session global pour qu’ils soient disponibles pour toutes les commandes de la session.

Le paramètre **Global** équivaut au paramètre **Scope** avec la valeur **Global**.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

Spécifie un tableau de variables que cette applet de commande importe du module dans la session active.
Entrez une liste de variables. Les caractères génériques sont autorisés.

Au moment de leur importation, certains modules exportent automatiquement les variables sélectionnées dans votre session.
Ce paramètre vous permet d'effectuer votre choix parmi les variables exportées.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -SkipEditionCheck

Ignore la vérification sur le `CompatiblePSEditions` champ.

Permet de charger un module à partir du `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` répertoire du module dans PowerShell Core quand ce module ne spécifie pas `Core` dans le `CompatiblePSEditions` champ de manifeste.

Lorsque vous importez un module à partir d’un autre chemin d’accès, ce commutateur n’a aucun effet, car la vérification n’est pas effectuée. Sur Linux et macOS, ce commutateur ne fait rien.

Pour plus d’informations, consultez [about_PowerShell_Editions](About/about_PowerShell_Editions.md).

> [!WARNING]
> `Import-Module -SkipEditionCheck` l’importation d’un module risque toujours d’échouer. Même si elle réussit, l’appel d’une commande à partir du module peut échouer plus tard lorsqu’elle essaie d’utiliser une API incompatible.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedName, FullyQualifiedNameAndPSSession, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseWindowsPowerShell

Charge le module à l’aide de la fonctionnalité de compatibilité Windows PowerShell. Pour plus d’informations, consultez [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. String, System. Management. Automation. PSModuleInfo, System. Reflection. assembly

Vous pouvez diriger un nom de module, un objet de module ou un objet d’assembly vers cette applet de commande.

## SORTIES

### None, System. Management. Automation. PSModuleInfo ou System. Management. Automation. PSCustomObject

Par défaut, `Import-Module` ne génère pas de sortie. Si vous spécifiez le paramètre **PassThru** , l’applet de commande génère un objet **System. Management. Automation. PSModuleInfo** qui représente le module. Si vous spécifiez le paramètre **AsCustomObject** , il génère un objet **PSCustomObject** .

## REMARQUES

- Avant de pouvoir importer un module, le module doit être installé sur l’ordinateur local. Autrement dit, le répertoire de module doit être copié vers un répertoire qui est accessible à votre ordinateur local. Pour plus d’informations, consultez [about_Modules](About/about_Modules.md).

  Vous pouvez également utiliser les paramètres **PSSession** et **CIMSession** pour importer des modules qui sont installés sur des ordinateurs distants. Toutefois, les commandes qui utilisent les applets de commande dans ces modules s’exécutent dans la session à distance sur l’ordinateur distant.

- Si vous importez des membres portant le même nom et le même type dans votre session, PowerShell utilise par défaut le membre importé en dernier. Les variables et les alias sont remplacés, et les originaux ne sont pas accessibles. Les fonctions, les applets de commande et les fournisseurs sont simplement occultés par les nouveaux membres. Ils sont accessibles en qualifiant le nom de commande avec le nom de son composant logiciel enfichable, module ou chemin d’accès de fonction.

- Pour mettre à jour les données de mise en forme pour les commandes qui ont été importées à partir d’un module, utilisez l’applet de commande `Update-FormatData` . `Update-FormatData` met également à jour les données de mise en forme pour les commandes de la session qui ont été importées à partir de modules. Si le fichier de mise en forme d’un module est modifié, vous pouvez exécuter une `Update-FormatData` commande pour mettre à jour les données de mise en forme des commandes importées. Vous n’avez pas besoin de réimporter le module.

- À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec PowerShell sont empaquetées dans des modules. Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables (**PSSnapins**). L’exception est **Microsoft. PowerShell. Core**, qui est toujours un composant logiciel enfichable. En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.

  Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez la [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).

- Dans Windows PowerShell 2,0, certaines des valeurs de propriété de l’objet de module, telles que les valeurs de propriété **ExportedCmdlets** et **NestedModules** , n’ont pas été remplies tant que le module n’a pas été importé.

- Si vous tentez d’importer un module qui contient des assemblys en mode mixte qui ne sont pas compatibles avec Windows PowerShell 3.0, `Import-Module` retourne un message d’erreur semblable à celui-ci.

  > Import-Module : l’assembly en mode mixte est généré avec la version’v 2.0.50727 'du runtime et ne peut pas être chargé dans le runtime 4,0 sans informations de configuration supplémentaires.

  Cette erreur se produit lorsqu’un module conçu pour Windows PowerShell 2,0 contient au moins un assembly de module mixte. Assembly de module mixte qui comprend du code managé et non managé, tel que C++ et C#.

  Pour importer un module qui contient des assemblys en mode mixte, démarrez Windows PowerShell 2,0 à l’aide de la commande suivante, puis réessayez d’exécuter la `Import-Module` commande.

  `PowerShell.exe -Version 2.0`

- Pour utiliser la fonctionnalité de session CIM, l'ordinateur distant doit disposer de l'accès distant WS-Management et de Windows Management Instrumentation (WMI), qui est l'implémentation Microsoft du modèle CIM (Common Information Model) standard. L'ordinateur doit également disposer du fournisseur WMI pour la découverte de module ou un autre fournisseur CIM qui a les mêmes fonctionnalités de base.

  Vous pouvez utiliser la fonctionnalité de session CIM sur les ordinateurs qui n’exécutent pas de système d’exploitation Windows et sur les ordinateurs Windows qui disposent de PowerShell, mais pour lesquels la communication à distance PowerShell n’est pas activée.

  Vous pouvez également utiliser les paramètres CIM pour obtenir des modules CIM à partir d’ordinateurs sur lesquels la communication à distance PowerShell est activée, y compris l’ordinateur local. Lorsque vous créez une session CIM sur l’ordinateur local, PowerShell utilise DCOM au lieu de WMI pour créer la session.

- Par défaut, `Import-Module` importe les modules dans la portée globale même en cas d’appel à partir d’une portée descendante. L’étendue de niveau supérieur et toutes les portées descendantes ont accès aux éléments exportés du module.

  Dans une portée descendante, `-Scope Local` limite l’importation à cette portée et à toutes ses étendues descendantes. Les étendues parentes ne voient pas les membres importés.

  > [!NOTE]
  > `Get-Module` affiche tous les modules chargés dans la session active. Cela comprend les modules chargés localement dans une portée descendante. Utilisez `Get-Command -Module modulename` pour voir quels membres sont chargés dans l’étendue actuelle.

  `Import-Module` ne charge pas les définitions de classe et d’énumération dans le module. Utilisez l' `using module` instruction au début de votre script. Cela importe le module, y compris les définitions de classe et d’énumération. Pour plus d’informations, consultez [about_Using](About/about_Using.md).

## LIENS CONNEXES

[about_Modules](about/about_Modules.md)

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
