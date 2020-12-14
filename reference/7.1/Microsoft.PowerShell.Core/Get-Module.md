---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 1f06d1e7114a84ea89097167b188ded605f81aa0
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564535"
---
# Get-Module

## SYNOPSIS
Répertorie les modules importés dans la session active ou qui peuvent être importés à partir du PSModulePath.

## SYNTAXE

### Loaded (valeur par défaut)

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### Disponible

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### PsSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## Description

L' `Get-Module` applet de commande répertorie les modules PowerShell qui ont été importés ou qui peuvent être importés dans une session PowerShell. Sans paramètres, `Get-Module` obtient les modules qui ont été importés dans la session active. Le paramètre **listAvailable** permet de répertorier les modules qui peuvent être importés à partir des chemins d’accès spécifiés dans la variable d’environnement PSModulePath ( `$env:PSModulePath` ).

L’objet de module qui `Get-Module` retourne contient des informations précieuses sur le module. Vous pouvez également diriger les objets de module vers d’autres applets de commande, telles que les `Import-Module` applets de commande et `Remove-Module` .

`Get-Module` répertorie les modules, mais ne les importe pas. À compter de Windows PowerShell 3,0, les modules sont importés automatiquement lorsque vous utilisez une commande dans le module, mais une `Get-Module` commande ne déclenche pas d’importation automatique. Vous pouvez également importer les modules dans votre session à l’aide de l’applet de commande `Import-Module` .

À compter de Windows PowerShell 3,0, vous pouvez importer et importer des modules à partir de sessions à distance dans la session locale. Cette stratégie utilise la fonctionnalité de communication à distance implicite de PowerShell et équivaut à utiliser l’applet de commande `Import-PSSession` . Lorsque vous utilisez des commandes dans des modules importés à partir d’une autre session, les commandes s’exécutent implicitement dans la session à distance. Cette fonctionnalité vous permet de gérer l’ordinateur distant à partir de la session locale.

En outre, à compter de Windows PowerShell 3,0, vous pouvez utiliser `Get-Module` et `Import-Module` pour récupérer et importer des modules Common Information Model (CIM). Les modules CIM définissent des applets de commande dans des fichiers CDXML (cmdlet Definition XML). Cette fonctionnalité vous permet d’utiliser des applets de commande qui sont implémentées dans des assemblys de code non managé, telles que celles écrites en C++.

La communication à distance implicite peut être utilisée pour gérer des ordinateurs distants sur lesquels la communication à distance PowerShell est activée.
Créez une session **PSSession** sur l’ordinateur distant, puis utilisez le paramètre **PSSession** de `Get-Module` pour obtenir les modules PowerShell dans la session à distance. Lorsque vous importez un module à partir de la session à distance, les commandes importées s’exécutent dans la session sur l’ordinateur distant.

Vous pouvez utiliser une stratégie similaire pour gérer les ordinateurs sur lesquels la communication à distance PowerShell n’est pas activée.
Celles-ci incluent les ordinateurs qui n’exécutent pas le système d’exploitation Windows et les ordinateurs qui disposent de PowerShell mais sur lesquels la communication à distance PowerShell n’est pas activée.

Commencez par créer une session CIM sur l’ordinateur distant. Une session CIM est une connexion à Windows Management Instrumentation (WMI) sur l’ordinateur distant. Utilisez ensuite le paramètre **CIMSession** de `Get-Module` pour récupérer les modules CIM à partir de la session CIM. Lorsque vous importez un module CIM à l’aide de l' `Import-Module` applet de commande, puis exécutez les commandes importées, les commandes s’exécutent implicitement sur l’ordinateur distant. Vous pouvez utiliser cette stratégie WMI et CIM pour gérer l'ordinateur distant.

## EXEMPLES

### Exemple 1 : récupérer les modules importés dans la session active

```powershell
Get-Module
```

Cette commande obtient les modules qui ont été importés dans la session active.

### Exemple 2 : récupérer les modules installés et les modules disponibles

```powershell
Get-Module -ListAvailable
```

Cette commande obtient les modules qui sont installés sur l'ordinateur et peuvent être importés dans la session active.

`Get-Module` recherche les modules disponibles dans le chemin d’accès spécifié par la variable d’environnement **$env :P smodulepath** . Pour plus d'informations sur **PSModulePath**, consultez [about_Modules](About/about_Modules.md) et [about_Environment_Variables](About/about_Environment_Variables.md).

### Exemple 3 : récupération de tous les fichiers exportés

```powershell
Get-Module -ListAvailable -All
```

Cette commande obtient tous les fichiers exportés pour tous les modules disponibles.

### Exemple 4 : obtenir un module par son nom complet

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

Cette commande obtient le module **Microsoft. PowerShell. Management** en spécifiant le nom complet du module à l’aide du paramètre **FullyQualifiedName** . La commande dirige ensuite les résultats vers l' `Format-Table` applet de commande pour mettre en forme les résultats sous la forme d’une table dont le **nom** et la **version** sont les en-têtes de colonne.

### Exemple 5 : obtenir les propriétés d’un module

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

Cette commande obtient les propriétés de l’objet **PSModuleInfo** `Get-Module` retourné par. Il existe un objet pour chaque fichier de module.

Vous pouvez utiliser les propriétés pour mettre en forme et filtrer les objets de module. Pour plus d’informations sur les propriétés, consultez [Propriétés de PSModuleInfo](/dotnet/api/system.management.automation.psmoduleinfo).

La sortie comprend les nouvelles propriétés, telles que **Author** et **CompanyName**, qui ont été introduites dans Windows PowerShell 3,0.

### Exemple 6 : regrouper tous les modules par nom

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

Cette commande obtient tous les fichiers de module, importés et disponibles, puis les regroupe par nom de module. Cela vous permet d'afficher les fichiers de module exportés par chaque script.

### Exemple 7 : afficher le contenu d’un manifeste de module

Ces commandes affichent le contenu du manifeste de module pour le module **BitsTransfer** de Windows PowerShell.

Les modules n’ont pas besoin d’avoir des fichiers manifestes. Lorsqu’ils ont un fichier manifeste, le fichier manifeste est requis uniquement pour inclure un numéro de version. Toutefois, les fichiers manifeste fournissent souvent des informations utiles sur un module, ses spécifications et son contenu.

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

La première commande obtient l'objet PSModuleInfo qui représente le module BitsTransfer. Elle enregistre l’objet dans la `$m` variable.

La deuxième commande utilise l' `Get-Content` applet de commande pour récupérer le contenu du fichier manifeste dans le chemin d’accès spécifié. Elle utilise la notation par points pour obtenir le chemin d'accès du fichier manifeste, stocké dans la propriété Path de l'objet. La sortie affiche le contenu du manifeste du module.

### Exemple 8 : répertorier les fichiers dans le répertoire du module

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

Cette commande répertorie les fichiers dans le répertoire du module. Il s'agit d'une autre façon de déterminer ce que contient le module avant son importation. Certains modules peuvent avoir des fichiers d'aide ou des fichiers Lisez-moi qui décrivent le module.

### Exemple 9 : obtenir les modules installés sur un ordinateur

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

Ces commandes obtiennent les modules installés sur l'ordinateur Server01.

La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01. La commande enregistre la **session PSSession** dans la variable $s.

La deuxième commande utilise les paramètres **PSSession** et **listAvailable** de `Get-Module` pour récupérer les modules dans la **session PSSession** dans la `$s` variable.

Si vous dirigez des modules à partir d’autres sessions vers l’applet de commande `Import-Module` , `Import-Module` importe le module dans la session active à l’aide de la fonctionnalité de communication à distance implicite. Cela équivaut à utiliser l’applet de commande `Import-PSSession` . Vous pouvez utiliser les applets de commande du module dans la session active, mais les commandes qui utilisent ces applets de commande s'exécutent en réalité dans la session à distance. Pour plus d’informations, consultez [`Import-Module`](Import-Module.md) et [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).

### Exemple 10 : gérer un ordinateur qui n’exécute pas le système d’exploitation Windows

Les commandes de cet exemple vous permettent de gérer les systèmes de stockage d’un ordinateur distant qui n’exécute pas le système d’exploitation Windows.
Dans cet exemple, comme l'administrateur de l'ordinateur a installé le fournisseur WMI pour la découverte de module, les commandes CIM peuvent utiliser les valeurs par défaut, qui sont conçues pour le fournisseur.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

La première commande utilise l' `New-CimSession` applet de commande pour créer une session sur l’ordinateur distant RSDGF03. La session se connecte à WMI sur l'ordinateur distant. La commande enregistre la session CIM dans la `$cs` variable.

La deuxième commande utilise la session CIM dans la `$cs` variable pour exécuter une `Get-Module` commande sur l’ordinateur RSDGF03. La commande utilise le paramètre Name pour spécifier le module Storage. La commande utilise un opérateur de pipeline (|) pour envoyer le module de stockage à l’applet de commande `Import-Module` , qui l’importe dans la session locale.

La troisième commande exécute l' `Get-Command` applet de commande sur la `Get-Disk` commande dans le module Storage.
Lorsque vous importez un module CIM dans la session locale, PowerShell convertit les fichiers CDXML qui représentent le module CIM en scripts PowerShell, qui apparaissent sous la forme de fonctions dans la session locale.

La quatrième commande exécute la `Get-Disk` commande. Bien que la commande soit tapée dans la session locale, elle s'exécute implicitement sur l'ordinateur distant à partir duquel elle a été importée. La commande récupère des objets de l'ordinateur distant et les retourne à la session locale.

## PARAMETERS

### -All

Indique que cette applet de commande obtient tous les modules de chaque dossier de module, y compris les modules imbriqués, les fichiers manifeste (. psd1), les fichiers de module de script (. psm1) et les fichiers de module binaire (. dll). Sans ce paramètre, `Get-Module` obtient uniquement le module par défaut dans chaque dossier de module.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimNamespace

Spécifie l'espace de noms d'un autre fournisseur CIM qui expose des modules CIM. La valeur par défaut est l'espace de noms du fournisseur WMI pour la découverte de module.

Utilisez ce paramètre pour récupérer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows.

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

Utilisez ce paramètre pour récupérer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows.

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

Spécifie une session CIM sur l'ordinateur distant. Entrez une variable qui contient la session CIM ou une commande qui obtient la session CIM, telle qu’une commande [CimSession](/powershell/module/cimcmdlets/get-cimsession) .

`Get-Module` utilise la connexion de session CIM pour récupérer les modules à partir de l’ordinateur distant. Lorsque vous importez le module à l’aide de l' `Import-Module` applet de commande et que vous utilisez les commandes du module importé dans la session active, les commandes s’exécutent en réalité sur l’ordinateur distant.

Vous pouvez utiliser ce paramètre pour obtenir des modules d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows, ainsi que des ordinateurs qui ont PowerShell, mais sur lesquels la communication à distance PowerShell n’est pas activée.

Le paramètre **CimSession** obtient tous les modules de la session **CIMSession**. Toutefois, vous pouvez importer uniquement les modules CIM ou CDXML (Cmdlet Definition XML).

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

### -FullyQualifiedName

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** . Consultez la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif. Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** . les deux paramètres s’excluent mutuellement.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

Indique que cette applet de commande obtient tous les modules installés. `Get-Module` Obtient les modules dans les chemins d’accès figurant dans la variable d’environnement **PSModulePath** . Sans ce paramètre, `Get-Module` obtient uniquement les modules répertoriés dans la variable d’environnement **PSModulePath** et qui sont chargés dans la session active. **ListAvailable** ne retourne pas d'informations sur les modules qui ne figurent pas dans la variable d'environnement **PSModulePath**, même si ces modules sont chargés dans la session active.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie les noms ou modèles de nom des modules que cette applet de commande obtient. Les caractères génériques sont autorisés. Vous pouvez également rediriger les noms vers `Get-Module` . Vous ne pouvez pas spécifier le paramètre **FullyQualifiedName** dans la même commande qu’un paramètre **Name** .

Le **nom** ne peut pas accepter un GUID de module comme valeur.
Pour retourner des modules en spécifiant un GUID, utilisez **FullyQualifiedName** à la place.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -PSEdition

Obtient les modules qui prennent en charge l’édition spécifiée de PowerShell.

Les valeurs valides pour ce paramètre sont :

- Bureau
- Base

L’applet de commande Get-Module vérifie la propriété **CompatiblePSEditions** de l’objet **PSModuleInfo** pour la valeur spécifiée et retourne uniquement les modules qui l’ont définie.

> [!NOTE]
>
> - **Édition Desktop :** repose sur .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.
> - **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

Obtient les modules de la session PowerShell managée par l’utilisateur spécifiée (**PSSession**). Entrez une variable qui contient la session, une commande qui obtient la session, telle qu’une `Get-PSSession` commande, ou une commande qui crée la session, telle qu’une `New-PSSession` commande.

Lorsque la session est connectée à un ordinateur distant, vous devez spécifier le paramètre **listAvailable** .

Une `Get-Module` commande qui utilise le paramètre **PSSession** équivaut à utiliser l' `Invoke-Command` applet de commande pour exécuter une `Get-Module -ListAvailable` commande dans une **session PSSession**.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Actualiser

Indique que cette applet de commande actualise le cache des commandes installées. Le cache de commande est créé au démarrage de la session. Elle permet `Get-Command` à l’applet de commande d’extraire des commandes des modules qui ne sont pas importés dans la session.

Ce paramètre est conçu pour le développement et les scénarios de test dans lesquels le contenu des modules a changé depuis le début de la session.

Lorsque vous spécifiez le paramètre **Refresh** dans une commande, vous devez spécifier **listAvailable**.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipEditionCheck

Ignore la vérification du `CompatiblePSEditions` champ.

Par défaut, Get-Module ignore les modules `%windir%\System32\WindowsPowerShell\v1.0\Modules` qui ne sont pas spécifiés dans `Core` le champ dans le répertoire `CompatiblePSEditions` . Lorsque ce commutateur est défini, les modules sans `Core` sont inclus, de sorte que les modules sous le chemin d’accès du module Windows PowerShell qui sont incompatibles avec PowerShell Core sont retournés.

Sur macOS et Linux, ce paramètre n’a aucun effet.

Pour plus d’informations, consultez [about_PowerShell_Editions](About/about_PowerShell_Editions.md) .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
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

### System.String

Vous pouvez diriger les noms de module vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSModuleInfo

Cette applet de commande retourne des objets qui représentent des modules.
Lorsque vous spécifiez le paramètre **listAvailable** , `Get-Module` retourne un objet **ModuleInfoGrouping** , qui est un type d’objet **PSModuleInfo** qui a les mêmes propriétés et méthodes.

## REMARQUES

- À compter de Windows PowerShell 3,0, les commandes de base qui sont incluses dans PowerShell sont empaquetées dans des modules. L’exception est **Microsoft. PowerShell. Core**, qui est un composant logiciel enfichable (**PSSnapin**). Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session. Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l' `Import-Module` applet de commande pour les importer.

- Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables (**PSSnapins**). L’exception est **Microsoft. PowerShell. Core**, qui est toujours un composant logiciel enfichable. En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.

  Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).

- `Get-Module` Obtient uniquement les modules dans les emplacements stockés dans la valeur de la variable d’environnement **PSModulePath** ($env :P smodulepath). L' `Import-Module` applet de commande peut importer des modules dans d’autres emplacements, mais vous ne pouvez pas utiliser l' `Get-Module` applet de commande pour les récupérer.

- En outre, à compter de PowerShell 3,0, de nouvelles propriétés ont été ajoutées à l’objet `Get-Module` retourné, ce qui facilite l’apprentissage des modules, même avant leur importation. Toutes les propriétés sont remplies avant l’importation. Celles-ci incluent les propriétés **ExportedCommands**, **ExportedCmdlets** et **ExportedFunctions** qui répertorient les commandes exportées par le module.

- Le paramètre **listAvailable** obtient uniquement les modules correctement formés, c’est-à-dire les dossiers qui contiennent au moins un fichier dont le nom de base est identique au nom du dossier du module. Le nom de base est le nom sans l’extension de nom de fichier. Les dossiers qui contiennent des fichiers portant des noms différents sont considérés comme des conteneurs, mais pas des modules.

  Pour obtenir les modules qui sont implémentés en tant que fichiers DLL, mais qui ne sont pas placés dans un dossier de module, spécifiez à la fois **listAvailable** et **tous** les paramètres.

- Pour utiliser la fonctionnalité de session CIM, l'ordinateur distant doit disposer de l'accès distant WS-Management et de Windows Management Instrumentation (WMI), qui est l'implémentation Microsoft du modèle CIM (Common Information Model) standard. L'ordinateur doit également disposer du fournisseur WMI pour la découverte de module ou d'un autre fournisseur WMI ayant les mêmes fonctionnalités de base.

  Vous pouvez utiliser la fonctionnalité de session CIM sur les ordinateurs qui n’exécutent pas le système d’exploitation Windows et sur les ordinateurs Windows qui disposent de PowerShell, mais sur lesquels la communication à distance PowerShell n’est pas activée.

  Vous pouvez également utiliser les paramètres CIM pour obtenir des modules CIM à partir d’ordinateurs sur lesquels la communication à distance PowerShell est activée. Cela comprend l’ordinateur local. Lorsque vous créez une session CIM sur l’ordinateur local, PowerShell utilise DCOM au lieu de WMI pour créer la session.

## LIENS CONNEXES

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[about_Modules](About/about_Modules.md)

[Get-PSSession](Get-PSSession.md)

[Module d’importation](Import-Module.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[New-PSSession](New-PSSession.md)

[Remove-Module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
