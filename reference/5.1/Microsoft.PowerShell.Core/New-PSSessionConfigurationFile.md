---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: 98dd55175321c2b7ebd98d1fb2420993d8aabe97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202269"
---
# New-PSSessionConfigurationFile

## SYNOPSIS
Crée un fichier qui définit une configuration de session.

## SYNTAX

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## Description

L' `New-PSSessionConfigurationFile` applet de commande crée un fichier de paramètres qui définissent une configuration de session et l’environnement des sessions créées à l’aide de la configuration de session.
Pour utiliser le fichier dans une configuration de session, utilisez le paramètre **path** des `Register-PSSessionConfiguration` applets de commande ou `Set-PSSessionConfiguration` .

Le fichier de configuration de session créé par l' `New-PSSessionConfigurationFile` utilisateur est un fichier texte lisible qui contient une table de hachage des propriétés et valeurs de configuration de session. Le fichier a une `.pssc` extension de nom de fichier.

Tous les paramètres de `New-PSSessionConfigurationFile` sont facultatifs, à l’exception du paramètre **path** .
Si vous omettez un paramètre, la clé correspondante dans le fichier de configuration de session est commentée, sauf indication contraire dans la description du paramètre.

Une configuration de session, également appelée point de terminaison, est une collection de paramètres sur l’ordinateur local qui définissent l’environnement des sessions PowerShell ( **sessions PSSession** ) qui se connectent à l’ordinateur. Tous les **sessions PSSession** utilisent une configuration de session. Pour spécifier une configuration de session particulière, utilisez le paramètre **ConfigurationName** des applets de commande qui créent une session, telle que l’applet de commande `New-PSSession` .

Un session configuration file facilite la définition d'une configuration de session en vous évitant d'utiliser des scripts ou des assemblys de code complexes. Les paramètres du fichier sont utilisés avec le script de démarrage facultatif et tous les assemblys de la configuration de session.

Pour plus d’informations sur les configurations de session et les fichiers de configuration de session, consultez [about_session_configurations](About/about_Session_Configurations.md) et [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

Cette applet de commande a été introduite dans PowerShell 3,0.

## EXEMPLES

### Exemple 1 : création et utilisation d’une session nolanguage

Cet exemple montre comment créer et les effets de l’utilisation d’une session sans langage.

Procédez comme suit :

1. Créez un fichier de configuration.
1. Enregistrez la configuration.
1. Créez une nouvelle session qui utilise la configuration.
1. Exécutez les commandes de cette nouvelle session.

Pour exécuter les commandes de cet exemple, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur. Cette option est requise pour exécuter l' `Register-PSSessionConfiguration` applet de commande.

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

Dans cet exemple, le `Invoke-Command` échoue car **LanguageMode** a la valeur **nolanguage** .

### Exemple 2 : création et utilisation d’une session RestrictedLanguage

Cet exemple montre comment créer et les effets de l’utilisation d’une session sans langage.

Procédez comme suit :

1. Créez un fichier de configuration.
1. Enregistrez la configuration.
1. Créez une nouvelle session qui utilise la configuration.
1. Exécutez les commandes de cette nouvelle session.

Pour exécuter les commandes de cet exemple, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur. Cette option est requise pour exécuter l' `Register-PSSessionConfiguration` applet de commande.

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

Dans cet exemple, le `Invoke-Command` fonctionne, car **LanguageMode** a la valeur **RestrictedLanguage** .

### Exemple 3 : modification d’un fichier de configuration de session

Cet exemple montre comment modifier le fichier de configuration de session utilisé dans une session existante nommée « ITTasks ». Auparavant, ces sessions avaient uniquement les modules de base et un module interne **ITTasks** . L’administrateur souhaite ajouter le module **PSScheduledJob** aux sessions créées à l’aide de la configuration de session ITTasks.

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

L' `New-PSSessionConfigurationFile` applet de commande pour créer un fichier de configuration de session qui importe les modules requis. L' `Set-PSSessionConfiguration` applet de commande remplace le fichier de configuration actuel par le nouveau. Cette nouvelle configuration affecte uniquement les nouvelles sessions créées après la modification.
Les sessions « ITTasks » existantes ne sont pas affectées.

### Exemple 4 : modification d’un fichier de configuration de session

Cet exemple montre comment changer une configuration de session en modifiant la copie de la configuration de session active du fichier de configuration. Pour modifier la copie de configuration de session du fichier de configuration, vous devez disposer d’un accès contrôle total au fichier. Vous devrez peut-être modifier les autorisations sur le fichier.

Dans ce scénario, nous souhaitons ajouter un nouvel alias pour l’applet de commande `Select-String` en modifiant le fichier de configuration actif.

L’exemple de code ci-dessous effectue les étapes suivantes pour effectuer cette modification :

1. Obtient le chemin d’accès au fichier de configuration pour la session ITConfig.
1. L’utilisateur modifie le fichier de configuration à l’aide de **Notepad.exe** pour modifier la valeur **AliasDefinitions** comme suit : `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .
1. Testez le fichier de configuration mis à jour.

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

Utilisez le paramètre **Verbose** avec `Test-PSSessionConfigurationFile` pour afficher les erreurs détectées. L’applet de commande retourne `$True` si aucune erreur n’est détectée dans le fichier.

### Exemple 5 : créer un exemple de fichier de configuration

Cet exemple montre une `New-PSSessionConfigurationFile` commande qui utilise tous les paramètres de l’applet de commande.
Il est inclus pour illustrer le format d'entrée approprié de chaque paramètre.

Le SampleFile.pssc résultant est affiché dans la sortie.

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## PARAMETERS

### -AliasDefinitions

Ajoute les alias spécifiés aux sessions qui utilisent la configuration de session. Entrez une table de hachage avec les clés suivantes :

- Nom : nom de l’alias. Cette clé est obligatoire.
- Value : commande représentée par l’alias. Cette clé est obligatoire.
- Description : chaîne de texte qui décrit l’alias. Cette clé est facultative.
- Options-options d’alias. Cette clé est facultative. La valeur par défaut est **None** . Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.

Par exemple : `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

Spécifie les assemblys à charger dans les sessions qui utilisent la configuration de session.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Auteur

Spécifie l’auteur de la configuration de session ou du fichier de configuration. La valeur par défaut est l’utilisateur actuel. La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.

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

### -CompanyName

Spécifie la société qui a créé la configuration de session ou le fichier de configuration. La valeur par défaut est **Unknown** . La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### -Copyright

Spécifie un copyright du fichier de configuration de session. La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.

Si vous omettez ce paramètre, `New-PSSessionConfigurationFile` génère une déclaration de droits d’auteur à l’aide de la valeur du paramètre **auteur** .

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

### Description

Spécifie une description de la configuration de session ou du fichier de configuration de session. La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.

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

### -EnvironmentVariables

Ajoute des variables d'environnement à la session. Entrez une table de hachage dans laquelle les clés sont les noms des variables d'environnement, et les valeurs sont les valeurs des variables d'environnement.

Par exemple : `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionPolicy

Spécifie la stratégie d'exécution des sessions qui utilisent la configuration de session. Si vous omettez ce paramètre, la valeur de la clé **ExecutionPolicy** dans le fichier de configuration de session est **Restricted** . Pour plus d’informations sur les stratégies d’exécution dans PowerShell, consultez [about_Execution_Policies](about/about_Execution_Policies.md).

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Spécifie les fichiers de mise en forme (.ps1xml) qui s'exécutent dans les sessions qui utilisent la configuration de session.
La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des fichiers de mise en forme.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

Indique que cette opération comprend toutes les propriétés de configuration possibles dans le fichier de configuration de session.

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

### -FunctionDefinitions

Ajoute les fonctions spécifiées aux sessions qui utilisent la configuration de session. Entrez une table de hachage avec les clés suivantes :

- Nom : nom de la fonction. Cette clé est obligatoire.
- ScriptBlock : corps de la fonction. Entrez un bloc de script. Cette clé est obligatoire.
- Options-options de fonction. Cette clé est facultative. La valeur par défaut est **None** . Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.

Par exemple : `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GroupManagedServiceAccount

Configure les sessions à l’aide de cette configuration de session pour s’exécuter dans le contexte du compte de service administré de groupe spécifié. L’ordinateur sur lequel cette configuration de session est inscrite doit avoir l’autorisation de demander le mot de passe gMSA pour que les sessions soient créées avec succès. Ce champ ne peut pas être utilisé avec le paramètre **runasvirtualaccount doit avoir** .

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

### -Guid

Spécifie un identificateur unique pour le fichier de configuration de session. Si vous omettez ce paramètre, `New-PSSessionConfigurationFile` génère un GUID pour le fichier. Pour créer un nouveau GUID dans PowerShell, tapez `New-Guid` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LanguageMode

Détermine les éléments du langage PowerShell autorisés dans les sessions qui utilisent cette configuration de session. Vous pouvez utiliser ce paramètre pour limiter les commandes que certains utilisateurs peuvent exécuter sur l'ordinateur.

Les valeurs valides pour ce paramètre sont :

- FullLanguage : tous les éléments de langage sont autorisés.
- ConstrainedLanguage-les commandes qui contiennent des scripts à évaluer ne sont pas autorisées. Le mode ConstrainedLanguage restreint l'accès utilisateur aux types, objets ou méthodes Microsoft .NET Framework.
- Nolanguage : les utilisateurs peuvent exécuter des applets de commande et des fonctions, mais ils ne sont pas autorisés à utiliser des éléments de langage, tels que des blocs de script, des variables ou des opérateurs.
- RestrictedLanguage : les utilisateurs peuvent exécuter des applets de commande et des fonctions, mais ils ne sont pas autorisés à utiliser des blocs de script ou des variables, à l’exception des variables autorisées suivantes : `$PSCulture` , `$PSUICulture` ,, `$True` `$False` et `$Null` . Les utilisateurs peuvent utiliser uniquement les opérateurs de comparaison de base ( `-eq` , `-gt` , `-lt` ). Les instructions d'assignation, les références de propriété et les appels de méthode ne sont pas autorisés.

La valeur par défaut du paramètre **LanguageMode** dépend de la valeur du paramètre **SessionType** .

- Vide-nolanguage
- RestrictedRemoteServer-nolanguage
- Par défaut-FullLanguage

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session.

Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions à distance, mais à moins que les applets de commande ne soient exclues, les utilisateurs peuvent utiliser les `Import-Module` applets de commande et `Add-PSSnapin` pour ajouter des modules et des composants logiciels enfichables à la session.

Chaque module ou composant logiciel enfichable inclus dans la valeur de ce paramètre peut être représenté par une chaîne ou une table de hachage. Une chaîne de module se compose uniquement du nom du module ou du composant logiciel enfichable. Une table de hachage de module peut inclure des clés **modulename** , **ModuleVersion** et **GUID** . Seule la clé **ModuleName** est obligatoire.

Par exemple, la valeur suivante se compose d'une chaîne et d'une table de hachage. Toutes les combinaisons de chaînes et de tables de hachage, dans n'importe quel ordre, sont valides.

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

La valeur du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` est prioritaire sur la valeur de la clé **ModulesToImport** dans le fichier de configuration de session.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MountUserDrive

Configure les sessions qui utilisent cette configuration de session pour exposer le `User:` PSDrive. Les lecteurs utilisateur sont uniques pour chaque utilisateur qui se connecte et permettent aux utilisateurs de copier des données vers et depuis des points de terminaison PowerShell, même si le fournisseur du système de fichiers n’est pas exposé. Les racines de lecteur utilisateur sont créées sous `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` . Pour chaque utilisateur qui se connecte au point de terminaison, un dossier est créé avec le nom `$env:USERDOMAIN_$env:USERNAME`.

Le contenu du lecteur utilisateur est conservé entre les sessions utilisateur et n’est pas automatiquement supprimé. Par défaut, les utilisateurs peuvent uniquement stocker jusqu’à 50 Mo de données dans le lecteur de l’utilisateur. Cela peut être personnalisé avec le paramètre **UserDriveMaximumSize** .

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

### -Path

Spécifie le chemin d’accès et le nom du fichier de configuration de session. Le fichier doit avoir une `.pssc` extension de nom de fichier.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

Spécifie la version du moteur PowerShell dans les sessions qui utilisent la configuration de session. Les valeurs acceptables pour ce paramètre sont les suivantes : 2,0 et 3,0. Si vous omettez ce paramètre, la clé **PowerShellVersion** est commentée et la dernière version de PowerShell s’exécute dans la session.

La valeur du paramètre **psversion** de l’applet de commande `Register-PSSessionConfiguration` est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredGroups

Spécifie les règles d’accès conditionnel pour les utilisateurs se connectant à des sessions qui utilisent cette configuration de session.

Entrez une table de hachage pour composer votre liste de règles en utilisant uniquement 1 clé par table de hachage, « et » ou « ou », puis définissez la valeur sur un tableau de noms de groupes de sécurité ou de tables de hachage supplémentaires.

Exemple nécessitant la connexion des utilisateurs aux membres d’un groupe unique : `@{ And = 'MyRequiredGroup' }`

Exemple nécessitant que les utilisateurs appartiennent au groupe A, ou aux deux groupes B et C, pour accéder au point de terminaison : `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleDefinitions

Spécifie le mappage entre les groupes de sécurité (ou les utilisateurs) et les capacités de rôle. Les utilisateurs sont autorisés à accéder à toutes les fonctionnalités de rôle qui s’appliquent à leur appartenance à un groupe au moment de la création de la session.

Entrez une table de hachage dans laquelle les clés sont le nom du groupe de sécurité et les valeurs sont des tables de hachage qui contiennent une liste de fonctionnalités de rôle qui doivent être mises à la disposition du groupe de sécurité.

Par exemple : `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Runasvirtualaccount doit avoir

Configure les sessions qui utilisent cette configuration de session pour être exécutées en tant que compte d’administrateur (virtuel) de l’ordinateur. Ce champ ne peut pas être utilisé avec le paramètre **GroupManagedServiceAccount** .

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

### -RunAsVirtualAccountGroups

Spécifie les groupes de sécurité à associer au compte virtuel lorsqu’une session qui utilise la configuration de session est exécutée en tant que compte virtuel. En cas d’omission, le compte virtuel appartient aux administrateurs de domaine sur les contrôleurs de domaine et aux administrateurs sur tous les autres ordinateurs.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SchemaVersion

Spécifie la version du schéma du fichier de configuration de session. La valeur par défaut est « 1.0.0.0 ».

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Ajoute les scripts spécifiés aux sessions qui utilisent la configuration de session. Entrez le chemin d'accès et les noms de fichiers des scripts. La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de script.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionType

Spécifie le type de session créé à l'aide de la configuration de session. La valeur par défaut est Default. Les valeurs valides pour ce paramètre sont :

- Vide : aucun module n’est ajouté à la session par défaut. Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session. Cette option est conçue pour vous permettre de créer des sessions personnalisées en ajoutant des commandes sélectionnées. Si vous n'ajoutez pas de commandes à une session vide, la session est limitée aux expressions et risque d'être inutilisable.
- Default : ajoute le module Microsoft. PowerShell. Core à la session. Ce module comprend l' `Import-Module` applet de commande que les utilisateurs peuvent utiliser pour importer d’autres modules, sauf si vous interdisez explicitement cette applet de commande.
- RestrictedRemoteServer. Comprend uniquement les fonctions proxy suivantes : `Exit-PSSession` , `Get-Command` , `Get-FormatData` , `Get-Help` , `Measure-Object` , `Out-Default` et `Select-Object` .
  Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session.

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TranscriptDirectory

Spécifie le répertoire où placer les transcriptions de session pour les sessions à l’aide de cette configuration de session.

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

### -TypesToProcess

Ajoute les `.ps1xml` fichiers de types spécifiés aux sessions qui utilisent la configuration de session. Entrez les noms de fichiers de type. La valeur de ce paramètre doit être un chemin d’accès complet ou absolu aux noms de fichiers de type.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserDriveMaximumSize

Spécifie la taille maximale des lecteurs utilisateur exposés dans les sessions qui utilisent cette configuration de session.
En cas d’omission, la taille par défaut de chaque `User:` racine de lecteur est de 50 Mo.

Ce paramètre doit être utilisé avec **MountUserDrive** .

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

Ajoute les variables spécifiées aux sessions qui utilisent la configuration de session. Entrez une table de hachage avec les clés suivantes :

- Nom : nom de la variable. Cette clé est obligatoire.
- Valeur de variable de valeur. Cette clé est obligatoire.
- Options-options de variable. Cette clé est facultative. La valeur par défaut est **None** . Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.

Par exemple : `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

Limite les alias de la session à ceux spécifiés dans la valeur de ce paramètre, ainsi qu'à tous les alias que vous définissez dans le paramètre **AliasDefinition** . Les caractères génériques sont pris en charge. Par défaut, tous les alias définis par le moteur PowerShell et tous les alias que les modules exportent sont visibles dans la session.

Par exemple : `VisibleAliases='gcm', 'gp'`

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.

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

### -VisibleCmdlets

Limite les applets de commande de la session à celles spécifiées dans la valeur de ce paramètre. Les caractères génériques et les noms de module qualifiés sont pris en charge.

Par défaut, toutes les applets de commande que les modules de la session exportent sont visibles dans la session. Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session. Si aucun module de **ModulesToImport** n’expose l’applet de commande, le module approprié tentera d’être chargé.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleExternalCommands

Limite les fichiers binaires externes, les scripts et les commandes qui peuvent être exécutés dans la session à ceux spécifiés dans la valeur de ce paramètre. Les caractères génériques sont pris en charge.

Par défaut, aucune commande externe n’est visible dans la session.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à partir de la session.

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

### -VisibleFunctions

Limite les fonctions de la session à celles spécifiées dans la valeur de ce paramètre, ainsi qu'à toutes les fonctions que vous définissez dans le paramètre **FunctionDefinition** . Les caractères génériques sont pris en charge.

Par défaut, toutes les fonctions que les modules de la session exportent sont visibles dans la session. Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

Limite les fournisseurs PowerShell dans la session à ceux spécifiés dans la valeur de ce paramètre.
Les caractères génériques sont pris en charge.

Par défaut, tous les fournisseurs que les modules de la session exportent sont visibles dans la session. Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.

Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’objets vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- Les paramètres, tels que **VisibleCmdlets** et **VisibleProviders** , n’importent pas d’éléments dans la session. À la place, ils sélectionnent les éléments importés dans la session. Par exemple, si la valeur du paramètre **VisibleProviders** est le fournisseur de certificats, mais que le paramètre **ModulesToImport** ne spécifie pas le module **Microsoft. PowerShell. Security** qui contient le fournisseur de certificats, le fournisseur de certificats n’est pas visible dans la session.
- `New-PSSessionConfigurationFile` crée un fichier de configuration de session qui a une extension de nom de fichier. PSSC dans le chemin d’accès que vous spécifiez dans le paramètre **path** . Lorsque vous utilisez le fichier de configuration de session pour créer une configuration de session, l’applet de commande `Register-PSSessionConfiguration` copie le fichier de configuration et enregistre une copie active du fichier dans le sous-répertoire **SessionConfig** du `$PSHOME` répertoire.

  La propriété **ConfigFilePath** de la configuration de session contient le chemin d’accès complet du fichier de configuration de session active. Vous pouvez modifier le fichier de configuration actif dans le `$PSHOME` répertoire à tout moment à l’aide de n’importe quel éditeur de texte. Les changements que vous apportez affectent toutes les nouvelles sessions qui utilisent la configuration de session, mais pas les sessions existantes.

  Avant d’utiliser un fichier de configuration de session modifié, utilisez l' `Test-PSSessionConfigurationFile` applet de commande pour vérifier que les entrées du fichier de configuration sont valides.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
