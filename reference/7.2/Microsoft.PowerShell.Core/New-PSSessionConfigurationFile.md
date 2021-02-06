---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: a41c52bf163aa0a73b54e75b5192389a14da82bb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595720"
---
# <span data-ttu-id="1392c-102">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1392c-102">New-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="1392c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1392c-103">SYNOPSIS</span></span>
<span data-ttu-id="1392c-104">Crée un fichier qui définit une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-104">Creates a file that defines a session configuration.</span></span>

## <span data-ttu-id="1392c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1392c-105">SYNTAX</span></span>

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

## <span data-ttu-id="1392c-106">Description</span><span class="sxs-lookup"><span data-stu-id="1392c-106">DESCRIPTION</span></span>

<span data-ttu-id="1392c-107">L' `New-PSSessionConfigurationFile` applet de commande crée un fichier de paramètres qui définissent une configuration de session et l’environnement des sessions créées à l’aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-107">The `New-PSSessionConfigurationFile` cmdlet creates a file of settings that define a session configuration and the environment of sessions that are created by using the session configuration.</span></span>
<span data-ttu-id="1392c-108">Pour utiliser le fichier dans une configuration de session, utilisez le paramètre **path** des `Register-PSSessionConfiguration` applets de commande ou `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1392c-108">To use the file in a session configuration, use the **Path** parameter of the `Register-PSSessionConfiguration` or `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="1392c-109">Le fichier de configuration de session créé par l' `New-PSSessionConfigurationFile` utilisateur est un fichier texte lisible qui contient une table de hachage des propriétés et valeurs de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-109">The session configuration file that `New-PSSessionConfigurationFile` creates is a human-readable text file that contains a hash table of the session configuration properties and values.</span></span> <span data-ttu-id="1392c-110">Le fichier a une `.pssc` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="1392c-110">The file has a `.pssc` filename extension.</span></span>

<span data-ttu-id="1392c-111">Tous les paramètres de `New-PSSessionConfigurationFile` sont facultatifs, à l’exception du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="1392c-111">All parameters of `New-PSSessionConfigurationFile` are optional, except for the **Path** parameter.</span></span>
<span data-ttu-id="1392c-112">Si vous omettez un paramètre, la clé correspondante dans le fichier de configuration de session est commentée, sauf indication contraire dans la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="1392c-112">If you omit a parameter, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span>

<span data-ttu-id="1392c-113">Une configuration de session, également appelée point de terminaison, est une collection de paramètres sur l’ordinateur local qui définissent l’environnement des sessions PowerShell (**sessions PSSession**) qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1392c-113">A session configuration, also known as an endpoint, is a collection of settings on the local computer that define the environment for PowerShell sessions (**PSSessions**) that connect to the computer.</span></span> <span data-ttu-id="1392c-114">Tous les **sessions PSSession** utilisent une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-114">All **PSSessions** use a session configuration.</span></span> <span data-ttu-id="1392c-115">Pour spécifier une configuration de session particulière, utilisez le paramètre **ConfigurationName** des applets de commande qui créent une session, telle que l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1392c-115">To specify a particular session configuration, use the **ConfigurationName** parameter of cmdlets that create a session, such as the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="1392c-116">Un session configuration file facilite la définition d'une configuration de session en vous évitant d'utiliser des scripts ou des assemblys de code complexes.</span><span class="sxs-lookup"><span data-stu-id="1392c-116">A session configuration file makes it easy to define a session configuration without complex scripts or code assemblies.</span></span> <span data-ttu-id="1392c-117">Les paramètres du fichier sont utilisés avec le script de démarrage facultatif et tous les assemblys de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-117">The settings in the file are used with the optional startup script and any assemblies in the session configuration.</span></span>

<span data-ttu-id="1392c-118">Pour plus d’informations sur les configurations de session et les fichiers de configuration de session, consultez [about_session_configurations](About/about_Session_Configurations.md) et [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="1392c-118">For more information about session configurations and session configuration files, see [about_Session_Configurations](About/about_Session_Configurations.md) and [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="1392c-119">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1392c-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="1392c-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1392c-120">EXAMPLES</span></span>

### <span data-ttu-id="1392c-121">Exemple 1 : création et utilisation d’une session nolanguage</span><span class="sxs-lookup"><span data-stu-id="1392c-121">Example 1: Creating and using a NoLanguage session</span></span>

<span data-ttu-id="1392c-122">Cet exemple montre comment créer et les effets de l’utilisation d’une session sans langage.</span><span class="sxs-lookup"><span data-stu-id="1392c-122">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="1392c-123">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1392c-123">The steps include:</span></span>

1. <span data-ttu-id="1392c-124">Créez un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-124">Create a new configuration file.</span></span>
1. <span data-ttu-id="1392c-125">Enregistrez la configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-125">Register the configuration.</span></span>
1. <span data-ttu-id="1392c-126">Créez une nouvelle session qui utilise la configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-126">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="1392c-127">Exécutez les commandes de cette nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="1392c-127">Run commands in that new session.</span></span>

<span data-ttu-id="1392c-128">Pour exécuter les commandes de cet exemple, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="1392c-128">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="1392c-129">Cette option est requise pour exécuter l' `Register-PSSessionConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1392c-129">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

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

<span data-ttu-id="1392c-130">Dans cet exemple, le `Invoke-Command` échoue car **LanguageMode** a la valeur **nolanguage**.</span><span class="sxs-lookup"><span data-stu-id="1392c-130">In this example, the `Invoke-Command` fails because the **LanguageMode** is set to **NoLanguage**.</span></span>

### <span data-ttu-id="1392c-131">Exemple 2 : création et utilisation d’une session RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="1392c-131">Example 2: Creating and using a RestrictedLanguage session</span></span>

<span data-ttu-id="1392c-132">Cet exemple montre comment créer et les effets de l’utilisation d’une session sans langage.</span><span class="sxs-lookup"><span data-stu-id="1392c-132">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="1392c-133">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1392c-133">The steps include:</span></span>

1. <span data-ttu-id="1392c-134">Créez un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-134">Create a new configuration file.</span></span>
1. <span data-ttu-id="1392c-135">Enregistrez la configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-135">Register the configuration.</span></span>
1. <span data-ttu-id="1392c-136">Créez une nouvelle session qui utilise la configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-136">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="1392c-137">Exécutez les commandes de cette nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="1392c-137">Run commands in that new session.</span></span>

<span data-ttu-id="1392c-138">Pour exécuter les commandes de cet exemple, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="1392c-138">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="1392c-139">Cette option est requise pour exécuter l' `Register-PSSessionConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1392c-139">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

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

<span data-ttu-id="1392c-140">Dans cet exemple, le `Invoke-Command` fonctionne, car **LanguageMode** a la valeur **RestrictedLanguage**.</span><span class="sxs-lookup"><span data-stu-id="1392c-140">In this example, the `Invoke-Command` succeeds because the **LanguageMode** is set to **RestrictedLanguage**.</span></span>

### <span data-ttu-id="1392c-141">Exemple 3 : modification d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="1392c-141">Example 3: Changing a Session Configuration File</span></span>

<span data-ttu-id="1392c-142">Cet exemple montre comment modifier le fichier de configuration de session utilisé dans une session existante nommée « ITTasks ».</span><span class="sxs-lookup"><span data-stu-id="1392c-142">This example shows how to change the session configuration file that is used in an existing session named "ITTasks".</span></span> <span data-ttu-id="1392c-143">Auparavant, ces sessions avaient uniquement les modules de base et un module interne **ITTasks** .</span><span class="sxs-lookup"><span data-stu-id="1392c-143">Previously, these sessions had only the core modules and an internal **ITTasks** module.</span></span> <span data-ttu-id="1392c-144">L’administrateur souhaite ajouter le module **PSScheduledJob** aux sessions créées à l’aide de la configuration de session ITTasks.</span><span class="sxs-lookup"><span data-stu-id="1392c-144">The administrator wants to add the **PSScheduledJob** module to sessions created by using the ITTasks session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

<span data-ttu-id="1392c-145">L' `New-PSSessionConfigurationFile` applet de commande pour créer un fichier de configuration de session qui importe les modules requis.</span><span class="sxs-lookup"><span data-stu-id="1392c-145">The `New-PSSessionConfigurationFile` cmdlet to create a session configuration file that imports the required modules.</span></span> <span data-ttu-id="1392c-146">L' `Set-PSSessionConfiguration` applet de commande remplace le fichier de configuration actuel par le nouveau.</span><span class="sxs-lookup"><span data-stu-id="1392c-146">The `Set-PSSessionConfiguration` cmdlet replaces the current configuration file with the new one.</span></span> <span data-ttu-id="1392c-147">Cette nouvelle configuration affecte uniquement les nouvelles sessions créées après la modification.</span><span class="sxs-lookup"><span data-stu-id="1392c-147">This new configuration only affects new sessions created after the change.</span></span>
<span data-ttu-id="1392c-148">Les sessions « ITTasks » existantes ne sont pas affectées.</span><span class="sxs-lookup"><span data-stu-id="1392c-148">Existing "ITTasks" sessions are not affected.</span></span>

### <span data-ttu-id="1392c-149">Exemple 4 : modification d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="1392c-149">Example 4: Editing a Session Configuration File</span></span>

<span data-ttu-id="1392c-150">Cet exemple montre comment changer une configuration de session en modifiant la copie de la configuration de session active du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-150">This example shows how to change a session configuration by editing the active session configuration copy of the configuration file.</span></span> <span data-ttu-id="1392c-151">Pour modifier la copie de configuration de session du fichier de configuration, vous devez disposer d’un accès contrôle total au fichier.</span><span class="sxs-lookup"><span data-stu-id="1392c-151">To modify the session configuration copy of the configuration file, you must have full control access to the file.</span></span> <span data-ttu-id="1392c-152">Vous devrez peut-être modifier les autorisations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="1392c-152">This may require you to change the permissions on the file.</span></span>

<span data-ttu-id="1392c-153">Dans ce scénario, nous souhaitons ajouter un nouvel alias pour l’applet de commande `Select-String` en modifiant le fichier de configuration actif.</span><span class="sxs-lookup"><span data-stu-id="1392c-153">In this scenario, we want to add a new alias for the `Select-String` cmdlet by editing the active configuration file.</span></span>

<span data-ttu-id="1392c-154">L’exemple de code ci-dessous effectue les étapes suivantes pour effectuer cette modification :</span><span class="sxs-lookup"><span data-stu-id="1392c-154">The example code below performs the following steps to make this change:</span></span>

1. <span data-ttu-id="1392c-155">Obtient le chemin d’accès au fichier de configuration pour la session ITConfig.</span><span class="sxs-lookup"><span data-stu-id="1392c-155">Get the configuration file path for the ITConfig session.</span></span>
1. <span data-ttu-id="1392c-156">L’utilisateur modifie le fichier de configuration à l’aide de **Notepad.exe** pour modifier la valeur **AliasDefinitions** comme suit : `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .</span><span class="sxs-lookup"><span data-stu-id="1392c-156">The user edits the configuration file using **Notepad.exe** to change the **AliasDefinitions** value as follows: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})`.</span></span>
1. <span data-ttu-id="1392c-157">Testez le fichier de configuration mis à jour.</span><span class="sxs-lookup"><span data-stu-id="1392c-157">Test the updated configuration file.</span></span>

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

<span data-ttu-id="1392c-158">Utilisez le paramètre **Verbose** avec `Test-PSSessionConfigurationFile` pour afficher les erreurs détectées.</span><span class="sxs-lookup"><span data-stu-id="1392c-158">Use the **Verbose** parameter with `Test-PSSessionConfigurationFile` to display any errors that are detected.</span></span> <span data-ttu-id="1392c-159">L’applet de commande retourne `$True` si aucune erreur n’est détectée dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="1392c-159">The cmdlet returns `$True` if no errors are detected in the file.</span></span>

### <span data-ttu-id="1392c-160">Exemple 5 : créer un exemple de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="1392c-160">Example 5: Create a sample configuration file</span></span>

<span data-ttu-id="1392c-161">Cet exemple montre une `New-PSSessionConfigurationFile` commande qui utilise tous les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1392c-161">This example shows a `New-PSSessionConfigurationFile` command that uses all the cmdlet parameters.</span></span>
<span data-ttu-id="1392c-162">Il est inclus pour illustrer le format d'entrée approprié de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="1392c-162">It is included to show the correct input format for each parameter.</span></span>

<span data-ttu-id="1392c-163">Le SampleFile.pssc résultant est affiché dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="1392c-163">The resulting SampleFile.pssc is displayed in the output.</span></span>

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

## <span data-ttu-id="1392c-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1392c-164">PARAMETERS</span></span>

### <span data-ttu-id="1392c-165">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="1392c-165">-AliasDefinitions</span></span>

<span data-ttu-id="1392c-166">Ajoute les alias spécifiés aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-166">Adds the specified aliases to sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-167">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="1392c-167">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="1392c-168">Nom : nom de l’alias.</span><span class="sxs-lookup"><span data-stu-id="1392c-168">Name - Name of the alias.</span></span> <span data-ttu-id="1392c-169">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-169">This key is required.</span></span>
- <span data-ttu-id="1392c-170">Value : commande représentée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="1392c-170">Value - The command that the alias represents.</span></span> <span data-ttu-id="1392c-171">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-171">This key is required.</span></span>
- <span data-ttu-id="1392c-172">Description : chaîne de texte qui décrit l’alias.</span><span class="sxs-lookup"><span data-stu-id="1392c-172">Description - A text string that describes the alias.</span></span> <span data-ttu-id="1392c-173">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="1392c-173">This key is optional.</span></span>
- <span data-ttu-id="1392c-174">Options-options d’alias.</span><span class="sxs-lookup"><span data-stu-id="1392c-174">Options - Alias options.</span></span> <span data-ttu-id="1392c-175">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="1392c-175">This key is optional.</span></span> <span data-ttu-id="1392c-176">La valeur par défaut est **None**.</span><span class="sxs-lookup"><span data-stu-id="1392c-176">The default value is **None**.</span></span> <span data-ttu-id="1392c-177">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="1392c-177">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="1392c-178">Par exemple : `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span><span class="sxs-lookup"><span data-stu-id="1392c-178">For example: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span></span>

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

### <span data-ttu-id="1392c-179">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="1392c-179">-AssembliesToLoad</span></span>

<span data-ttu-id="1392c-180">Spécifie les assemblys à charger dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-180">Specifies the assemblies to load into the sessions that use the session configuration.</span></span>

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

### <span data-ttu-id="1392c-181">-Auteur</span><span class="sxs-lookup"><span data-stu-id="1392c-181">-Author</span></span>

<span data-ttu-id="1392c-182">Spécifie l’auteur de la configuration de session ou du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-182">Specifies the author of the session configuration or the configuration file.</span></span> <span data-ttu-id="1392c-183">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="1392c-183">The default is the current user.</span></span> <span data-ttu-id="1392c-184">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-184">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="1392c-185">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="1392c-185">-CompanyName</span></span>

<span data-ttu-id="1392c-186">Spécifie la société qui a créé la configuration de session ou le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1392c-186">Specifies the company that created the session configuration or the configuration file.</span></span> <span data-ttu-id="1392c-187">La valeur par défaut est **Unknown**.</span><span class="sxs-lookup"><span data-stu-id="1392c-187">The default value is **Unknown**.</span></span> <span data-ttu-id="1392c-188">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-188">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="1392c-189">-Copyright</span><span class="sxs-lookup"><span data-stu-id="1392c-189">-Copyright</span></span>

<span data-ttu-id="1392c-190">Spécifie un copyright du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-190">Specifies a copyright the session configuration file.</span></span> <span data-ttu-id="1392c-191">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-191">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

<span data-ttu-id="1392c-192">Si vous omettez ce paramètre, `New-PSSessionConfigurationFile` génère une déclaration de droits d’auteur à l’aide de la valeur du paramètre **auteur** .</span><span class="sxs-lookup"><span data-stu-id="1392c-192">If you omit this parameter, `New-PSSessionConfigurationFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="1392c-193">Description</span><span class="sxs-lookup"><span data-stu-id="1392c-193">-Description</span></span>

<span data-ttu-id="1392c-194">Spécifie une description de la configuration de session ou du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-194">Specifies a description of the session configuration or the session configuration file.</span></span> <span data-ttu-id="1392c-195">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-195">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="1392c-196">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="1392c-196">-EnvironmentVariables</span></span>

<span data-ttu-id="1392c-197">Ajoute des variables d'environnement à la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-197">Adds environment variables to the session.</span></span> <span data-ttu-id="1392c-198">Entrez une table de hachage dans laquelle les clés sont les noms des variables d'environnement, et les valeurs sont les valeurs des variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="1392c-198">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="1392c-199">Par exemple : `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span><span class="sxs-lookup"><span data-stu-id="1392c-199">For example: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span></span>

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

### <span data-ttu-id="1392c-200">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="1392c-200">-ExecutionPolicy</span></span>

<span data-ttu-id="1392c-201">Spécifie la stratégie d'exécution des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-201">Specifies the execution policy of sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-202">Si vous omettez ce paramètre, la valeur de la clé **ExecutionPolicy** dans le fichier de configuration de session est **Restricted**.</span><span class="sxs-lookup"><span data-stu-id="1392c-202">If you omit this parameter, the value of the **ExecutionPolicy** key in the session configuration file is **Restricted**.</span></span> <span data-ttu-id="1392c-203">Pour plus d’informations sur les stratégies d’exécution dans PowerShell, consultez [about_Execution_Policies](about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="1392c-203">For information about execution policies in PowerShell, see [about_Execution_Policies](about/about_Execution_Policies.md).</span></span>

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

### <span data-ttu-id="1392c-204">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="1392c-204">-FormatsToProcess</span></span>

<span data-ttu-id="1392c-205">Spécifie les fichiers de mise en forme (.ps1xml) qui s'exécutent dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-205">Specifies the formatting files (.ps1xml) that run in sessions that use the session configuration.</span></span>
<span data-ttu-id="1392c-206">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1392c-206">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="1392c-207">-Full</span><span class="sxs-lookup"><span data-stu-id="1392c-207">-Full</span></span>

<span data-ttu-id="1392c-208">Indique que cette opération comprend toutes les propriétés de configuration possibles dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-208">Indicates that this operation includes all possible configuration properties in the session configuration file.</span></span>

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

### <span data-ttu-id="1392c-209">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="1392c-209">-FunctionDefinitions</span></span>

<span data-ttu-id="1392c-210">Ajoute les fonctions spécifiées aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-210">Adds the specified functions to sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-211">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="1392c-211">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="1392c-212">Nom : nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1392c-212">Name - Name of the function.</span></span> <span data-ttu-id="1392c-213">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-213">This key is required.</span></span>
- <span data-ttu-id="1392c-214">ScriptBlock : corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1392c-214">ScriptBlock - Function body.</span></span> <span data-ttu-id="1392c-215">Entrez un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="1392c-215">Enter a script block.</span></span> <span data-ttu-id="1392c-216">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-216">This key is required.</span></span>
- <span data-ttu-id="1392c-217">Options-options de fonction.</span><span class="sxs-lookup"><span data-stu-id="1392c-217">Options - Function options.</span></span> <span data-ttu-id="1392c-218">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="1392c-218">This key is optional.</span></span> <span data-ttu-id="1392c-219">La valeur par défaut est **None**.</span><span class="sxs-lookup"><span data-stu-id="1392c-219">The default value is **None**.</span></span> <span data-ttu-id="1392c-220">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="1392c-220">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="1392c-221">Par exemple : `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="1392c-221">For example: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span></span>

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

### <span data-ttu-id="1392c-222">-GroupManagedServiceAccount</span><span class="sxs-lookup"><span data-stu-id="1392c-222">-GroupManagedServiceAccount</span></span>

<span data-ttu-id="1392c-223">Configure les sessions à l’aide de cette configuration de session pour s’exécuter dans le contexte du compte de service administré de groupe spécifié.</span><span class="sxs-lookup"><span data-stu-id="1392c-223">Configures sessions using this session configuration to run under the context of the specified Group Managed Service Account.</span></span> <span data-ttu-id="1392c-224">L’ordinateur sur lequel cette configuration de session est inscrite doit avoir l’autorisation de demander le mot de passe gMSA pour que les sessions soient créées avec succès.</span><span class="sxs-lookup"><span data-stu-id="1392c-224">The machine where this session configuration is registered must have permission to request the gMSA password in order for sessions to be created successfully.</span></span> <span data-ttu-id="1392c-225">Ce champ ne peut pas être utilisé avec le paramètre **runasvirtualaccount doit avoir** .</span><span class="sxs-lookup"><span data-stu-id="1392c-225">This field cannot be used with the **RunAsVirtualAccount** parameter.</span></span>

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

### <span data-ttu-id="1392c-226">-Guid</span><span class="sxs-lookup"><span data-stu-id="1392c-226">-Guid</span></span>

<span data-ttu-id="1392c-227">Spécifie un identificateur unique pour le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-227">Specifies a unique identifier for the session configuration file.</span></span> <span data-ttu-id="1392c-228">Si vous omettez ce paramètre, `New-PSSessionConfigurationFile` génère un GUID pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="1392c-228">If you omit this parameter, `New-PSSessionConfigurationFile` generates a GUID for the file.</span></span> <span data-ttu-id="1392c-229">Pour créer un nouveau GUID dans PowerShell, tapez `New-Guid` .</span><span class="sxs-lookup"><span data-stu-id="1392c-229">To create a new GUID in PowerShell, type `New-Guid`.</span></span>

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

### <span data-ttu-id="1392c-230">-LanguageMode</span><span class="sxs-lookup"><span data-stu-id="1392c-230">-LanguageMode</span></span>

<span data-ttu-id="1392c-231">Détermine les éléments du langage PowerShell autorisés dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-231">Determines which elements of the PowerShell language are permitted in sessions that use this session configuration.</span></span> <span data-ttu-id="1392c-232">Vous pouvez utiliser ce paramètre pour limiter les commandes que certains utilisateurs peuvent exécuter sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1392c-232">You can use this parameter to restrict the commands that particular users can run on the computer.</span></span>

<span data-ttu-id="1392c-233">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1392c-233">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1392c-234">FullLanguage : tous les éléments de langage sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1392c-234">FullLanguage - All language elements are permitted.</span></span>
- <span data-ttu-id="1392c-235">ConstrainedLanguage-les commandes qui contiennent des scripts à évaluer ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="1392c-235">ConstrainedLanguage - Commands that contain scripts to be evaluated are not allowed.</span></span> <span data-ttu-id="1392c-236">Le mode ConstrainedLanguage restreint l'accès utilisateur aux types, objets ou méthodes Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1392c-236">The ConstrainedLanguage mode restricts user access to Microsoft .NET Framework types, objects, or methods.</span></span>
- <span data-ttu-id="1392c-237">Nolanguage : les utilisateurs peuvent exécuter des applets de commande et des fonctions, mais ils ne sont pas autorisés à utiliser des éléments de langage, tels que des blocs de script, des variables ou des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="1392c-237">NoLanguage - Users may run cmdlets and functions, but are not permitted to use any language elements, such as script blocks, variables, or operators.</span></span>
- <span data-ttu-id="1392c-238">RestrictedLanguage : les utilisateurs peuvent exécuter des applets de commande et des fonctions, mais ils ne sont pas autorisés à utiliser des blocs de script ou des variables, à l’exception des variables autorisées suivantes : `$PSCulture` , `$PSUICulture` ,, `$True` `$False` et `$Null` .</span><span class="sxs-lookup"><span data-stu-id="1392c-238">RestrictedLanguage - Users may run cmdlets and functions, but are not permitted to use script blocks or variables except for the following permitted variables: `$PSCulture`, `$PSUICulture`, `$True`, `$False`, and `$Null`.</span></span> <span data-ttu-id="1392c-239">Les utilisateurs peuvent utiliser uniquement les opérateurs de comparaison de base ( `-eq` , `-gt` , `-lt` ).</span><span class="sxs-lookup"><span data-stu-id="1392c-239">Users may use only the basic comparison operators (`-eq`, `-gt`, `-lt`).</span></span> <span data-ttu-id="1392c-240">Les instructions d'assignation, les références de propriété et les appels de méthode ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="1392c-240">Assignment statements, property references, and method calls are not permitted.</span></span>

<span data-ttu-id="1392c-241">La valeur par défaut du paramètre **LanguageMode** dépend de la valeur du paramètre **SessionType**.</span><span class="sxs-lookup"><span data-stu-id="1392c-241">The default value of the **LanguageMode** parameter depends on the value of the **SessionType** parameter.</span></span>

- <span data-ttu-id="1392c-242">Vide-nolanguage</span><span class="sxs-lookup"><span data-stu-id="1392c-242">Empty - NoLanguage</span></span>
- <span data-ttu-id="1392c-243">RestrictedRemoteServer-nolanguage</span><span class="sxs-lookup"><span data-stu-id="1392c-243">RestrictedRemoteServer - NoLanguage</span></span>
- <span data-ttu-id="1392c-244">Par défaut-FullLanguage</span><span class="sxs-lookup"><span data-stu-id="1392c-244">Default - FullLanguage</span></span>

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

### <span data-ttu-id="1392c-245">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="1392c-245">-ModulesToImport</span></span>

<span data-ttu-id="1392c-246">Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-246">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="1392c-247">Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions à distance, mais à moins que les applets de commande ne soient exclues, les utilisateurs peuvent utiliser les `Import-Module` applets de commande et `Add-PSSnapin` pour ajouter des modules et des composants logiciels enfichables à la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-247">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into remote sessions, but unless the cmdlets are excluded, users can use the `Import-Module` and `Add-PSSnapin` cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="1392c-248">Chaque module ou composant logiciel enfichable inclus dans la valeur de ce paramètre peut être représenté par une chaîne ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="1392c-248">Each module or snap-in in the value of this parameter can be represented by a string or as a hash table.</span></span> <span data-ttu-id="1392c-249">Une chaîne de module se compose uniquement du nom du module ou du composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="1392c-249">A module string consists only of the name of the module or snap-in.</span></span> <span data-ttu-id="1392c-250">Une table de hachage de module peut inclure des clés **modulename**, **ModuleVersion** et **GUID** .</span><span class="sxs-lookup"><span data-stu-id="1392c-250">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="1392c-251">Seule la clé **ModuleName** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-251">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="1392c-252">Par exemple, la valeur suivante se compose d'une chaîne et d'une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="1392c-252">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="1392c-253">Toutes les combinaisons de chaînes et de tables de hachage, dans n'importe quel ordre, sont valides.</span><span class="sxs-lookup"><span data-stu-id="1392c-253">Any combination of strings and hash tables, in any order, is valid.</span></span>

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

<span data-ttu-id="1392c-254">La valeur du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` est prioritaire sur la valeur de la clé **ModulesToImport** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-254">The value of the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **ModulesToImport** key in the session configuration file.</span></span>

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

### <span data-ttu-id="1392c-255">-MountUserDrive</span><span class="sxs-lookup"><span data-stu-id="1392c-255">-MountUserDrive</span></span>

<span data-ttu-id="1392c-256">Configure les sessions qui utilisent cette configuration de session pour exposer le `User:` PSDrive.</span><span class="sxs-lookup"><span data-stu-id="1392c-256">Configures sessions that use this session configuration to expose the `User:` PSDrive.</span></span> <span data-ttu-id="1392c-257">Les lecteurs utilisateur sont uniques pour chaque utilisateur qui se connecte et permettent aux utilisateurs de copier des données vers et depuis des points de terminaison PowerShell, même si le fournisseur du système de fichiers n’est pas exposé.</span><span class="sxs-lookup"><span data-stu-id="1392c-257">User drives are unique for each connecting user and allow users to copy data to and from PowerShell endpoints even if the File System provider is not exposed.</span></span> <span data-ttu-id="1392c-258">Les racines de lecteur utilisateur sont créées sous `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` .</span><span class="sxs-lookup"><span data-stu-id="1392c-258">User drive roots are created under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="1392c-259">Pour chaque utilisateur qui se connecte au point de terminaison, un dossier est créé avec le nom `$env:USERDOMAIN_$env:USERNAME`.</span><span class="sxs-lookup"><span data-stu-id="1392c-259">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="1392c-260">Le contenu du lecteur utilisateur est conservé entre les sessions utilisateur et n’est pas automatiquement supprimé.</span><span class="sxs-lookup"><span data-stu-id="1392c-260">Contents in the user drive persist across user sessions and are not automatically removed.</span></span> <span data-ttu-id="1392c-261">Par défaut, les utilisateurs peuvent uniquement stocker jusqu’à 50 Mo de données dans le lecteur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1392c-261">By default, users can only store up to 50MB of data in the user drive.</span></span> <span data-ttu-id="1392c-262">Cela peut être personnalisé avec le paramètre **UserDriveMaximumSize** .</span><span class="sxs-lookup"><span data-stu-id="1392c-262">This can be customized with the **UserDriveMaximumSize** parameter.</span></span>

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

### <span data-ttu-id="1392c-263">-Path</span><span class="sxs-lookup"><span data-stu-id="1392c-263">-Path</span></span>

<span data-ttu-id="1392c-264">Spécifie le chemin d’accès et le nom du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-264">Specifies the path and filename of the session configuration file.</span></span> <span data-ttu-id="1392c-265">Le fichier doit avoir une `.pssc` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="1392c-265">The file must have a `.pssc` file name extension.</span></span>

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

### <span data-ttu-id="1392c-266">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="1392c-266">-PowerShellVersion</span></span>

<span data-ttu-id="1392c-267">Spécifie la version du moteur PowerShell dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-267">Specifies the version of the PowerShell engine in sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-268">Les valeurs acceptables pour ce paramètre sont les suivantes : 2,0 et 3,0.</span><span class="sxs-lookup"><span data-stu-id="1392c-268">The acceptable values for this parameter are: 2.0 and 3.0.</span></span> <span data-ttu-id="1392c-269">Si vous omettez ce paramètre, la clé **PowerShellVersion** est commentée et la dernière version de PowerShell s’exécute dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-269">If you omit this parameter, the **PowerShellVersion** key is commented-out and newest version of PowerShell runs in the session.</span></span>

<span data-ttu-id="1392c-270">La valeur du paramètre **psversion** de l’applet de commande `Register-PSSessionConfiguration` est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-270">The value of the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

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

### <span data-ttu-id="1392c-271">-RequiredGroups</span><span class="sxs-lookup"><span data-stu-id="1392c-271">-RequiredGroups</span></span>

<span data-ttu-id="1392c-272">Spécifie les règles d’accès conditionnel pour les utilisateurs se connectant à des sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-272">Specifies conditional access rules for users connecting to sessions that use this session configuration.</span></span>

<span data-ttu-id="1392c-273">Entrez une table de hachage pour composer votre liste de règles en utilisant uniquement 1 clé par table de hachage, « et » ou « ou », puis définissez la valeur sur un tableau de noms de groupes de sécurité ou de tables de hachage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1392c-273">Enter a hashtable to compose your list of rules using only 1 key per hashtable, 'And' or 'Or', and set the value to an array of security group names or additional hashtables.</span></span>

<span data-ttu-id="1392c-274">Exemple nécessitant la connexion des utilisateurs aux membres d’un groupe unique : `@{ And = 'MyRequiredGroup' }`</span><span class="sxs-lookup"><span data-stu-id="1392c-274">Example requiring connecting users to be members of a single group: `@{ And = 'MyRequiredGroup' }`</span></span>

<span data-ttu-id="1392c-275">Exemple nécessitant que les utilisateurs appartiennent au groupe A, ou aux deux groupes B et C, pour accéder au point de terminaison : `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span><span class="sxs-lookup"><span data-stu-id="1392c-275">Example requiring users to belong to group A, or both groups B and C, to access the endpoint: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span></span>

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

### <span data-ttu-id="1392c-276">-RoleDefinitions</span><span class="sxs-lookup"><span data-stu-id="1392c-276">-RoleDefinitions</span></span>

<span data-ttu-id="1392c-277">Spécifie le mappage entre les groupes de sécurité (ou les utilisateurs) et les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1392c-277">Specifies the mapping between security groups (or users) and role capabilities.</span></span> <span data-ttu-id="1392c-278">Les utilisateurs sont autorisés à accéder à toutes les fonctionnalités de rôle qui s’appliquent à leur appartenance à un groupe au moment de la création de la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-278">Users will be granted access to all role capabilities which apply to their group membership at the time the session is created.</span></span>

<span data-ttu-id="1392c-279">Entrez une table de hachage dans laquelle les clés sont le nom du groupe de sécurité et les valeurs sont des tables de hachage qui contiennent une liste de fonctionnalités de rôle qui doivent être mises à la disposition du groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1392c-279">Enter a hash table in which the keys are the name of the security group and the values are hash tables that contain a list of role capabilities that should be made available to the security group.</span></span>

<span data-ttu-id="1392c-280">Par exemple : `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span><span class="sxs-lookup"><span data-stu-id="1392c-280">For example: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span></span>

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

### <span data-ttu-id="1392c-281">-Runasvirtualaccount doit avoir</span><span class="sxs-lookup"><span data-stu-id="1392c-281">-RunAsVirtualAccount</span></span>

<span data-ttu-id="1392c-282">Configure les sessions qui utilisent cette configuration de session pour être exécutées en tant que compte d’administrateur (virtuel) de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1392c-282">Configures sessions using this session configuration to be run as the computer's (virtual) administrator account.</span></span> <span data-ttu-id="1392c-283">Ce champ ne peut pas être utilisé avec le paramètre **GroupManagedServiceAccount** .</span><span class="sxs-lookup"><span data-stu-id="1392c-283">This field cannot be used with the **GroupManagedServiceAccount** parameter.</span></span>

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

### <span data-ttu-id="1392c-284">-RunAsVirtualAccountGroups</span><span class="sxs-lookup"><span data-stu-id="1392c-284">-RunAsVirtualAccountGroups</span></span>

<span data-ttu-id="1392c-285">Spécifie les groupes de sécurité à associer au compte virtuel lorsqu’une session qui utilise la configuration de session est exécutée en tant que compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="1392c-285">Specifies the security groups to be associated with the virtual account when a session that uses the session configuration is run as a virtual account.</span></span> <span data-ttu-id="1392c-286">En cas d’omission, le compte virtuel appartient aux administrateurs de domaine sur les contrôleurs de domaine et aux administrateurs sur tous les autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="1392c-286">If omitted, the virtual account belongs to Domain Admins on domain controllers and Administrators on all other computers.</span></span>

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

### <span data-ttu-id="1392c-287">-SchemaVersion</span><span class="sxs-lookup"><span data-stu-id="1392c-287">-SchemaVersion</span></span>

<span data-ttu-id="1392c-288">Spécifie la version du schéma du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-288">Specifies the version of the session configuration file schema.</span></span> <span data-ttu-id="1392c-289">La valeur par défaut est « 1.0.0.0 ».</span><span class="sxs-lookup"><span data-stu-id="1392c-289">The default value is "1.0.0.0".</span></span>

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

### <span data-ttu-id="1392c-290">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="1392c-290">-ScriptsToProcess</span></span>

<span data-ttu-id="1392c-291">Ajoute les scripts spécifiés aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-291">Adds the specified scripts to sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-292">Entrez le chemin d'accès et les noms de fichiers des scripts.</span><span class="sxs-lookup"><span data-stu-id="1392c-292">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="1392c-293">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="1392c-293">The value of this parameter must be a full or absolute path of script file names.</span></span>

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

### <span data-ttu-id="1392c-294">-SessionType</span><span class="sxs-lookup"><span data-stu-id="1392c-294">-SessionType</span></span>

<span data-ttu-id="1392c-295">Spécifie le type de session créé à l'aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-295">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="1392c-296">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="1392c-296">The default value is Default.</span></span> <span data-ttu-id="1392c-297">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1392c-297">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1392c-298">Vide : aucun module n’est ajouté à la session par défaut.</span><span class="sxs-lookup"><span data-stu-id="1392c-298">Empty - No modules are added to session by default.</span></span> <span data-ttu-id="1392c-299">Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-299">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span> <span data-ttu-id="1392c-300">Cette option est conçue pour vous permettre de créer des sessions personnalisées en ajoutant des commandes sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="1392c-300">This option is designed for you to create custom sessions by adding selected commands.</span></span> <span data-ttu-id="1392c-301">Si vous n'ajoutez pas de commandes à une session vide, la session est limitée aux expressions et risque d'être inutilisable.</span><span class="sxs-lookup"><span data-stu-id="1392c-301">If you do not add commands to an empty session, the session is limited to expressions and might not be usable.</span></span>
- <span data-ttu-id="1392c-302">Default : ajoute le module Microsoft. PowerShell. Core à la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-302">Default - Adds the Microsoft.PowerShell.Core module to the session.</span></span> <span data-ttu-id="1392c-303">Ce module comprend l' `Import-Module` applet de commande que les utilisateurs peuvent utiliser pour importer d’autres modules, sauf si vous interdisez explicitement cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1392c-303">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit this cmdlet.</span></span>
- <span data-ttu-id="1392c-304">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="1392c-304">RestrictedRemoteServer.</span></span> <span data-ttu-id="1392c-305">Comprend uniquement les fonctions proxy suivantes : `Exit-PSSession` , `Get-Command` , `Get-FormatData` , `Get-Help` , `Measure-Object` , `Out-Default` et `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1392c-305">Includes only the following proxy functions: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span>
  <span data-ttu-id="1392c-306">Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-306">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>

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

### <span data-ttu-id="1392c-307">-TranscriptDirectory</span><span class="sxs-lookup"><span data-stu-id="1392c-307">-TranscriptDirectory</span></span>

<span data-ttu-id="1392c-308">Spécifie le répertoire où placer les transcriptions de session pour les sessions à l’aide de cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-308">Specifies the directory to place session transcripts for sessions using this session configuration.</span></span>

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

### <span data-ttu-id="1392c-309">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="1392c-309">-TypesToProcess</span></span>

<span data-ttu-id="1392c-310">Ajoute les `.ps1xml` fichiers de types spécifiés aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-310">Adds the specified `.ps1xml` type files to sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-311">Entrez les noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="1392c-311">Enter the type filenames.</span></span> <span data-ttu-id="1392c-312">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu aux noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="1392c-312">The value of this parameter must be a full or absolute path to type filenames.</span></span>

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

### <span data-ttu-id="1392c-313">-UserDriveMaximumSize</span><span class="sxs-lookup"><span data-stu-id="1392c-313">-UserDriveMaximumSize</span></span>

<span data-ttu-id="1392c-314">Spécifie la taille maximale des lecteurs utilisateur exposés dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-314">Specifies the maximum size for user drives exposed in sessions that use this session configuration.</span></span>
<span data-ttu-id="1392c-315">En cas d’omission, la taille par défaut de chaque `User:` racine de lecteur est de 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="1392c-315">When omitted, the default size of each `User:` drive root is 50MB.</span></span>

<span data-ttu-id="1392c-316">Ce paramètre doit être utilisé avec **MountUserDrive**.</span><span class="sxs-lookup"><span data-stu-id="1392c-316">This parameter should be used with **MountUserDrive**.</span></span>

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

### <span data-ttu-id="1392c-317">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="1392c-317">-VariableDefinitions</span></span>

<span data-ttu-id="1392c-318">Ajoute les variables spécifiées aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1392c-318">Adds the specified variables to sessions that use the session configuration.</span></span> <span data-ttu-id="1392c-319">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="1392c-319">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="1392c-320">Nom : nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="1392c-320">Name - Name of the variable.</span></span> <span data-ttu-id="1392c-321">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-321">This key is required.</span></span>
- <span data-ttu-id="1392c-322">Valeur de variable de valeur.</span><span class="sxs-lookup"><span data-stu-id="1392c-322">Value - Variable value.</span></span> <span data-ttu-id="1392c-323">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-323">This key is required.</span></span>
- <span data-ttu-id="1392c-324">Options-options de variable.</span><span class="sxs-lookup"><span data-stu-id="1392c-324">Options - Variable options.</span></span> <span data-ttu-id="1392c-325">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="1392c-325">This key is optional.</span></span> <span data-ttu-id="1392c-326">La valeur par défaut est **None**.</span><span class="sxs-lookup"><span data-stu-id="1392c-326">The default value is **None**.</span></span> <span data-ttu-id="1392c-327">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="1392c-327">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="1392c-328">Par exemple : `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="1392c-328">For example: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span></span>

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

### <span data-ttu-id="1392c-329">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="1392c-329">-VisibleAliases</span></span>

<span data-ttu-id="1392c-330">Limite les alias de la session à ceux spécifiés dans la valeur de ce paramètre, ainsi qu'à tous les alias que vous définissez dans le paramètre **AliasDefinition**.</span><span class="sxs-lookup"><span data-stu-id="1392c-330">Limits the aliases in the session to those specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="1392c-331">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1392c-331">Wildcard characters are supported.</span></span> <span data-ttu-id="1392c-332">Par défaut, tous les alias définis par le moteur PowerShell et tous les alias que les modules exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-332">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="1392c-333">Par exemple : `VisibleAliases='gcm', 'gp'`</span><span class="sxs-lookup"><span data-stu-id="1392c-333">For example: `VisibleAliases='gcm', 'gp'`</span></span>

<span data-ttu-id="1392c-334">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-334">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="1392c-335">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="1392c-335">-VisibleCmdlets</span></span>

<span data-ttu-id="1392c-336">Limite les applets de commande de la session à celles spécifiées dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="1392c-336">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="1392c-337">Les caractères génériques et les noms de module qualifiés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1392c-337">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="1392c-338">Par défaut, toutes les applets de commande que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-338">By default, all cmdlets that modules in the session export are visible in the session.</span></span> <span data-ttu-id="1392c-339">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-339">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="1392c-340">Si aucun module de **ModulesToImport** n’expose l’applet de commande, le module approprié tentera d’être chargé.</span><span class="sxs-lookup"><span data-stu-id="1392c-340">If no modules in **ModulesToImport** expose the cmdlet, the appropriate module will attempt to be autoloaded.</span></span>

<span data-ttu-id="1392c-341">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-341">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="1392c-342">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="1392c-342">-VisibleExternalCommands</span></span>

<span data-ttu-id="1392c-343">Limite les fichiers binaires externes, les scripts et les commandes qui peuvent être exécutés dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="1392c-343">Limits the external binaries, scripts, and commands that can be executed in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="1392c-344">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1392c-344">Wildcard characters are supported.</span></span>

<span data-ttu-id="1392c-345">Par défaut, aucune commande externe n’est visible dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-345">By default, no external commands are visible in the session.</span></span>

<span data-ttu-id="1392c-346">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à partir de la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-346">When any **Visible** parameter is included in the session configuration file, PowerShell, removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="1392c-347">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="1392c-347">-VisibleFunctions</span></span>

<span data-ttu-id="1392c-348">Limite les fonctions de la session à celles spécifiées dans la valeur de ce paramètre, ainsi qu'à toutes les fonctions que vous définissez dans le paramètre **FunctionDefinition**.</span><span class="sxs-lookup"><span data-stu-id="1392c-348">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinition** parameter.</span></span> <span data-ttu-id="1392c-349">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1392c-349">Wildcard characters are supported.</span></span>

<span data-ttu-id="1392c-350">Par défaut, toutes les fonctions que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-350">By default, all functions that modules in the session export are visible in the session.</span></span> <span data-ttu-id="1392c-351">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-351">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span>

<span data-ttu-id="1392c-352">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-352">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="1392c-353">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="1392c-353">-VisibleProviders</span></span>

<span data-ttu-id="1392c-354">Limite les fournisseurs PowerShell dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="1392c-354">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="1392c-355">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1392c-355">Wildcard characters are supported.</span></span>

<span data-ttu-id="1392c-356">Par défaut, tous les fournisseurs que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-356">By default, all providers that modules in the session export are visible in the session.</span></span> <span data-ttu-id="1392c-357">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-357">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="1392c-358">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-358">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="1392c-359">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1392c-359">CommonParameters</span></span>

<span data-ttu-id="1392c-360">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1392c-360">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1392c-361">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1392c-361">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1392c-362">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1392c-362">INPUTS</span></span>

### <span data-ttu-id="1392c-363">None</span><span class="sxs-lookup"><span data-stu-id="1392c-363">None</span></span>

<span data-ttu-id="1392c-364">Vous ne pouvez pas diriger d’objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1392c-364">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="1392c-365">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1392c-365">OUTPUTS</span></span>

### <span data-ttu-id="1392c-366">None</span><span class="sxs-lookup"><span data-stu-id="1392c-366">None</span></span>

<span data-ttu-id="1392c-367">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1392c-367">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1392c-368">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1392c-368">NOTES</span></span>

<span data-ttu-id="1392c-369">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="1392c-369">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="1392c-370">Les paramètres, tels que **VisibleCmdlets** et **VisibleProviders**, n’importent pas d’éléments dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-370">Parameters, such as **VisibleCmdlets** and **VisibleProviders**, do not import items into the session.</span></span> <span data-ttu-id="1392c-371">À la place, ils sélectionnent les éléments importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-371">Instead, they select from among the items imported into the session.</span></span> <span data-ttu-id="1392c-372">Par exemple, si la valeur du paramètre **VisibleProviders** est le fournisseur de certificats, mais que le paramètre **ModulesToImport** ne spécifie pas le module **Microsoft. PowerShell. Security** qui contient le fournisseur de certificats, le fournisseur de certificats n’est pas visible dans la session.</span><span class="sxs-lookup"><span data-stu-id="1392c-372">For example, if the value of the **VisibleProviders** parameter is the Certificate provider, but the **ModulesToImport** parameter does not specify the **Microsoft.PowerShell.Security** module that contains the Certificate provider, the Certificate provider is not visible in the session.</span></span>
- <span data-ttu-id="1392c-373">`New-PSSessionConfigurationFile` crée un fichier de configuration de session qui a une extension de nom de fichier. PSSC dans le chemin d’accès que vous spécifiez dans le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="1392c-373">`New-PSSessionConfigurationFile` creates a session configuration file that has a .pssc file name extension in the path that you specify in the **Path** parameter.</span></span> <span data-ttu-id="1392c-374">Lorsque vous utilisez le fichier de configuration de session pour créer une configuration de session, l’applet de commande `Register-PSSessionConfiguration` copie le fichier de configuration et enregistre une copie active du fichier dans le sous-répertoire **SessionConfig** du `$PSHOME` répertoire.</span><span class="sxs-lookup"><span data-stu-id="1392c-374">When you use the session configuration file to create a session configuration, the `Register-PSSessionConfiguration` cmdlet copies the configuration file and saves an active copy of the file in the **SessionConfig** subdirectory of the `$PSHOME` directory.</span></span>

  <span data-ttu-id="1392c-375">La propriété **ConfigFilePath** de la configuration de session contient le chemin d’accès complet du fichier de configuration de session active.</span><span class="sxs-lookup"><span data-stu-id="1392c-375">The **ConfigFilePath** property of the session configuration contains the fully qualified path of the active session configuration file.</span></span> <span data-ttu-id="1392c-376">Vous pouvez modifier le fichier de configuration actif dans le `$PSHOME` répertoire à tout moment à l’aide de n’importe quel éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="1392c-376">You can modify the active configuration file in the `$PSHOME` directory at any time using any text editor.</span></span> <span data-ttu-id="1392c-377">Les changements que vous apportez affectent toutes les nouvelles sessions qui utilisent la configuration de session, mais pas les sessions existantes.</span><span class="sxs-lookup"><span data-stu-id="1392c-377">The changes that you make affect all new sessions that use the session configuration, but not existing sessions.</span></span>

  <span data-ttu-id="1392c-378">Avant d’utiliser un fichier de configuration de session modifié, utilisez l' `Test-PSSessionConfigurationFile` applet de commande pour vérifier que les entrées du fichier de configuration sont valides.</span><span class="sxs-lookup"><span data-stu-id="1392c-378">Before using an edited session configuration file, use the `Test-PSSessionConfigurationFile` cmdlet to verify that the configuration file entries are valid.</span></span>

## <span data-ttu-id="1392c-379">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1392c-379">RELATED LINKS</span></span>

[<span data-ttu-id="1392c-380">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1392c-380">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="1392c-381">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1392c-381">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="1392c-382">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1392c-382">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="1392c-383">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1392c-383">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="1392c-384">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1392c-384">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="1392c-385">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1392c-385">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="1392c-386">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1392c-386">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="1392c-387">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="1392c-387">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="1392c-388">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="1392c-388">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="1392c-389">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="1392c-389">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
