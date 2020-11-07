---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: f2d5613b97e784fc9e1096d3687c156a77d21908
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343094"
---
# <span data-ttu-id="e0a26-103">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="e0a26-103">New-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="e0a26-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e0a26-104">SYNOPSIS</span></span>
<span data-ttu-id="e0a26-105">Crée un fichier qui définit une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-105">Creates a file that defines a session configuration.</span></span>

## <span data-ttu-id="e0a26-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e0a26-106">SYNTAX</span></span>

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

## <span data-ttu-id="e0a26-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0a26-107">DESCRIPTION</span></span>

<span data-ttu-id="e0a26-108">L' `New-PSSessionConfigurationFile` applet de commande crée un fichier de paramètres qui définissent une configuration de session et l’environnement des sessions créées à l’aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-108">The `New-PSSessionConfigurationFile` cmdlet creates a file of settings that define a session configuration and the environment of sessions that are created by using the session configuration.</span></span>
<span data-ttu-id="e0a26-109">Pour utiliser le fichier dans une configuration de session, utilisez le paramètre **path** des `Register-PSSessionConfiguration` applets de commande ou `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-109">To use the file in a session configuration, use the **Path** parameter of the `Register-PSSessionConfiguration` or `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="e0a26-110">Le fichier de configuration de session créé par l' `New-PSSessionConfigurationFile` utilisateur est un fichier texte lisible qui contient une table de hachage des propriétés et valeurs de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-110">The session configuration file that `New-PSSessionConfigurationFile` creates is a human-readable text file that contains a hash table of the session configuration properties and values.</span></span> <span data-ttu-id="e0a26-111">Le fichier a une `.pssc` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e0a26-111">The file has a `.pssc` filename extension.</span></span>

<span data-ttu-id="e0a26-112">Tous les paramètres de `New-PSSessionConfigurationFile` sont facultatifs, à l’exception du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-112">All parameters of `New-PSSessionConfigurationFile` are optional, except for the **Path** parameter.</span></span>
<span data-ttu-id="e0a26-113">Si vous omettez un paramètre, la clé correspondante dans le fichier de configuration de session est commentée, sauf indication contraire dans la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="e0a26-113">If you omit a parameter, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span>

<span data-ttu-id="e0a26-114">Une configuration de session, également appelée point de terminaison, est une collection de paramètres sur l’ordinateur local qui définissent l’environnement des sessions PowerShell ( **sessions PSSession** ) qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-114">A session configuration, also known as an endpoint, is a collection of settings on the local computer that define the environment for PowerShell sessions ( **PSSessions** ) that connect to the computer.</span></span> <span data-ttu-id="e0a26-115">Tous les **sessions PSSession** utilisent une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-115">All **PSSessions** use a session configuration.</span></span> <span data-ttu-id="e0a26-116">Pour spécifier une configuration de session particulière, utilisez le paramètre **ConfigurationName** des applets de commande qui créent une session, telle que l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-116">To specify a particular session configuration, use the **ConfigurationName** parameter of cmdlets that create a session, such as the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="e0a26-117">Un session configuration file facilite la définition d'une configuration de session en vous évitant d'utiliser des scripts ou des assemblys de code complexes.</span><span class="sxs-lookup"><span data-stu-id="e0a26-117">A session configuration file makes it easy to define a session configuration without complex scripts or code assemblies.</span></span> <span data-ttu-id="e0a26-118">Les paramètres du fichier sont utilisés avec le script de démarrage facultatif et tous les assemblys de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-118">The settings in the file are used with the optional startup script and any assemblies in the session configuration.</span></span>

<span data-ttu-id="e0a26-119">Pour plus d’informations sur les configurations de session et les fichiers de configuration de session, consultez [about_session_configurations](About/about_Session_Configurations.md) et [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="e0a26-119">For more information about session configurations and session configuration files, see [about_Session_Configurations](About/about_Session_Configurations.md) and [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="e0a26-120">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0a26-120">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="e0a26-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e0a26-121">EXAMPLES</span></span>

### <span data-ttu-id="e0a26-122">Exemple 1 : création et utilisation d’une session nolanguage</span><span class="sxs-lookup"><span data-stu-id="e0a26-122">Example 1: Creating and using a NoLanguage session</span></span>

<span data-ttu-id="e0a26-123">Cet exemple montre comment créer et les effets de l’utilisation d’une session sans langage.</span><span class="sxs-lookup"><span data-stu-id="e0a26-123">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="e0a26-124">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e0a26-124">The steps include:</span></span>

1. <span data-ttu-id="e0a26-125">Créez un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-125">Create a new configuration file.</span></span>
1. <span data-ttu-id="e0a26-126">Enregistrez la configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-126">Register the configuration.</span></span>
1. <span data-ttu-id="e0a26-127">Créez une nouvelle session qui utilise la configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-127">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="e0a26-128">Exécutez les commandes de cette nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-128">Run commands in that new session.</span></span>

<span data-ttu-id="e0a26-129">Pour exécuter les commandes de cet exemple, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-129">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="e0a26-130">Cette option est requise pour exécuter l' `Register-PSSessionConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0a26-130">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

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

<span data-ttu-id="e0a26-131">Dans cet exemple, le `Invoke-Command` échoue car **LanguageMode** a la valeur **nolanguage**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-131">In this example, the `Invoke-Command` fails because the **LanguageMode** is set to **NoLanguage**.</span></span>

### <span data-ttu-id="e0a26-132">Exemple 2 : création et utilisation d’une session RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="e0a26-132">Example 2: Creating and using a RestrictedLanguage session</span></span>

<span data-ttu-id="e0a26-133">Cet exemple montre comment créer et les effets de l’utilisation d’une session sans langage.</span><span class="sxs-lookup"><span data-stu-id="e0a26-133">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="e0a26-134">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e0a26-134">The steps include:</span></span>

1. <span data-ttu-id="e0a26-135">Créez un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-135">Create a new configuration file.</span></span>
1. <span data-ttu-id="e0a26-136">Enregistrez la configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-136">Register the configuration.</span></span>
1. <span data-ttu-id="e0a26-137">Créez une nouvelle session qui utilise la configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-137">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="e0a26-138">Exécutez les commandes de cette nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-138">Run commands in that new session.</span></span>

<span data-ttu-id="e0a26-139">Pour exécuter les commandes de cet exemple, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-139">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="e0a26-140">Cette option est requise pour exécuter l' `Register-PSSessionConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0a26-140">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

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

<span data-ttu-id="e0a26-141">Dans cet exemple, le `Invoke-Command` fonctionne, car **LanguageMode** a la valeur **RestrictedLanguage**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-141">In this example, the `Invoke-Command` succeeds because the **LanguageMode** is set to **RestrictedLanguage**.</span></span>

### <span data-ttu-id="e0a26-142">Exemple 3 : modification d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="e0a26-142">Example 3: Changing a Session Configuration File</span></span>

<span data-ttu-id="e0a26-143">Cet exemple montre comment modifier le fichier de configuration de session utilisé dans une session existante nommée « ITTasks ».</span><span class="sxs-lookup"><span data-stu-id="e0a26-143">This example shows how to change the session configuration file that is used in an existing session named "ITTasks".</span></span> <span data-ttu-id="e0a26-144">Auparavant, ces sessions avaient uniquement les modules de base et un module interne **ITTasks** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-144">Previously, these sessions had only the core modules and an internal **ITTasks** module.</span></span> <span data-ttu-id="e0a26-145">L’administrateur souhaite ajouter le module **PSScheduledJob** aux sessions créées à l’aide de la configuration de session ITTasks.</span><span class="sxs-lookup"><span data-stu-id="e0a26-145">The administrator wants to add the **PSScheduledJob** module to sessions created by using the ITTasks session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

<span data-ttu-id="e0a26-146">L' `New-PSSessionConfigurationFile` applet de commande pour créer un fichier de configuration de session qui importe les modules requis.</span><span class="sxs-lookup"><span data-stu-id="e0a26-146">The `New-PSSessionConfigurationFile` cmdlet to create a session configuration file that imports the required modules.</span></span> <span data-ttu-id="e0a26-147">L' `Set-PSSessionConfiguration` applet de commande remplace le fichier de configuration actuel par le nouveau.</span><span class="sxs-lookup"><span data-stu-id="e0a26-147">The `Set-PSSessionConfiguration` cmdlet replaces the current configuration file with the new one.</span></span> <span data-ttu-id="e0a26-148">Cette nouvelle configuration affecte uniquement les nouvelles sessions créées après la modification.</span><span class="sxs-lookup"><span data-stu-id="e0a26-148">This new configuration only affects new sessions created after the change.</span></span>
<span data-ttu-id="e0a26-149">Les sessions « ITTasks » existantes ne sont pas affectées.</span><span class="sxs-lookup"><span data-stu-id="e0a26-149">Existing "ITTasks" sessions are not affected.</span></span>

### <span data-ttu-id="e0a26-150">Exemple 4 : modification d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="e0a26-150">Example 4: Editing a Session Configuration File</span></span>

<span data-ttu-id="e0a26-151">Cet exemple montre comment changer une configuration de session en modifiant la copie de la configuration de session active du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-151">This example shows how to change a session configuration by editing the active session configuration copy of the configuration file.</span></span> <span data-ttu-id="e0a26-152">Pour modifier la copie de configuration de session du fichier de configuration, vous devez disposer d’un accès contrôle total au fichier.</span><span class="sxs-lookup"><span data-stu-id="e0a26-152">To modify the session configuration copy of the configuration file, you must have full control access to the file.</span></span> <span data-ttu-id="e0a26-153">Vous devrez peut-être modifier les autorisations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="e0a26-153">This may require you to change the permissions on the file.</span></span>

<span data-ttu-id="e0a26-154">Dans ce scénario, nous souhaitons ajouter un nouvel alias pour l’applet de commande `Select-String` en modifiant le fichier de configuration actif.</span><span class="sxs-lookup"><span data-stu-id="e0a26-154">In this scenario, we want to add a new alias for the `Select-String` cmdlet by editing the active configuration file.</span></span>

<span data-ttu-id="e0a26-155">L’exemple de code ci-dessous effectue les étapes suivantes pour effectuer cette modification :</span><span class="sxs-lookup"><span data-stu-id="e0a26-155">The example code below performs the following steps to make this change:</span></span>

1. <span data-ttu-id="e0a26-156">Obtient le chemin d’accès au fichier de configuration pour la session ITConfig.</span><span class="sxs-lookup"><span data-stu-id="e0a26-156">Get the configuration file path for the ITConfig session.</span></span>
1. <span data-ttu-id="e0a26-157">L’utilisateur modifie le fichier de configuration à l’aide de **Notepad.exe** pour modifier la valeur **AliasDefinitions** comme suit : `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-157">The user edits the configuration file using **Notepad.exe** to change the **AliasDefinitions** value as follows: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})`.</span></span>
1. <span data-ttu-id="e0a26-158">Testez le fichier de configuration mis à jour.</span><span class="sxs-lookup"><span data-stu-id="e0a26-158">Test the updated configuration file.</span></span>

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

<span data-ttu-id="e0a26-159">Utilisez le paramètre **Verbose** avec `Test-PSSessionConfigurationFile` pour afficher les erreurs détectées.</span><span class="sxs-lookup"><span data-stu-id="e0a26-159">Use the **Verbose** parameter with `Test-PSSessionConfigurationFile` to display any errors that are detected.</span></span> <span data-ttu-id="e0a26-160">L’applet de commande retourne `$True` si aucune erreur n’est détectée dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e0a26-160">The cmdlet returns `$True` if no errors are detected in the file.</span></span>

### <span data-ttu-id="e0a26-161">Exemple 5 : créer un exemple de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e0a26-161">Example 5: Create a sample configuration file</span></span>

<span data-ttu-id="e0a26-162">Cet exemple montre une `New-PSSessionConfigurationFile` commande qui utilise tous les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0a26-162">This example shows a `New-PSSessionConfigurationFile` command that uses all the cmdlet parameters.</span></span>
<span data-ttu-id="e0a26-163">Il est inclus pour illustrer le format d'entrée approprié de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="e0a26-163">It is included to show the correct input format for each parameter.</span></span>

<span data-ttu-id="e0a26-164">Le SampleFile.pssc résultant est affiché dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="e0a26-164">The resulting SampleFile.pssc is displayed in the output.</span></span>

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

## <span data-ttu-id="e0a26-165">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="e0a26-165">PARAMETERS</span></span>

### <span data-ttu-id="e0a26-166">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="e0a26-166">-AliasDefinitions</span></span>

<span data-ttu-id="e0a26-167">Ajoute les alias spécifiés aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-167">Adds the specified aliases to sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-168">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0a26-168">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="e0a26-169">Nom : nom de l’alias.</span><span class="sxs-lookup"><span data-stu-id="e0a26-169">Name - Name of the alias.</span></span> <span data-ttu-id="e0a26-170">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-170">This key is required.</span></span>
- <span data-ttu-id="e0a26-171">Value : commande représentée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="e0a26-171">Value - The command that the alias represents.</span></span> <span data-ttu-id="e0a26-172">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-172">This key is required.</span></span>
- <span data-ttu-id="e0a26-173">Description : chaîne de texte qui décrit l’alias.</span><span class="sxs-lookup"><span data-stu-id="e0a26-173">Description - A text string that describes the alias.</span></span> <span data-ttu-id="e0a26-174">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="e0a26-174">This key is optional.</span></span>
- <span data-ttu-id="e0a26-175">Options-options d’alias.</span><span class="sxs-lookup"><span data-stu-id="e0a26-175">Options - Alias options.</span></span> <span data-ttu-id="e0a26-176">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="e0a26-176">This key is optional.</span></span> <span data-ttu-id="e0a26-177">La valeur par défaut est **None**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-177">The default value is **None**.</span></span> <span data-ttu-id="e0a26-178">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="e0a26-178">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="e0a26-179">Par exemple : `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span><span class="sxs-lookup"><span data-stu-id="e0a26-179">For example: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span></span>

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

### <span data-ttu-id="e0a26-180">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="e0a26-180">-AssembliesToLoad</span></span>

<span data-ttu-id="e0a26-181">Spécifie les assemblys à charger dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-181">Specifies the assemblies to load into the sessions that use the session configuration.</span></span>

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

### <span data-ttu-id="e0a26-182">-Auteur</span><span class="sxs-lookup"><span data-stu-id="e0a26-182">-Author</span></span>

<span data-ttu-id="e0a26-183">Spécifie l’auteur de la configuration de session ou du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-183">Specifies the author of the session configuration or the configuration file.</span></span> <span data-ttu-id="e0a26-184">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e0a26-184">The default is the current user.</span></span> <span data-ttu-id="e0a26-185">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-185">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="e0a26-186">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="e0a26-186">-CompanyName</span></span>

<span data-ttu-id="e0a26-187">Spécifie la société qui a créé la configuration de session ou le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0a26-187">Specifies the company that created the session configuration or the configuration file.</span></span> <span data-ttu-id="e0a26-188">La valeur par défaut est **Unknown**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-188">The default value is **Unknown**.</span></span> <span data-ttu-id="e0a26-189">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-189">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="e0a26-190">-Copyright</span><span class="sxs-lookup"><span data-stu-id="e0a26-190">-Copyright</span></span>

<span data-ttu-id="e0a26-191">Spécifie un copyright du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-191">Specifies a copyright the session configuration file.</span></span> <span data-ttu-id="e0a26-192">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-192">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

<span data-ttu-id="e0a26-193">Si vous omettez ce paramètre, `New-PSSessionConfigurationFile` génère une déclaration de droits d’auteur à l’aide de la valeur du paramètre **auteur** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-193">If you omit this parameter, `New-PSSessionConfigurationFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="e0a26-194">Description</span><span class="sxs-lookup"><span data-stu-id="e0a26-194">-Description</span></span>

<span data-ttu-id="e0a26-195">Spécifie une description de la configuration de session ou du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-195">Specifies a description of the session configuration or the session configuration file.</span></span> <span data-ttu-id="e0a26-196">La valeur de ce paramètre est visible dans le fichier de configuration de session, mais il ne s'agit pas d'une propriété de l'objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-196">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="e0a26-197">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="e0a26-197">-EnvironmentVariables</span></span>

<span data-ttu-id="e0a26-198">Ajoute des variables d'environnement à la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-198">Adds environment variables to the session.</span></span> <span data-ttu-id="e0a26-199">Entrez une table de hachage dans laquelle les clés sont les noms des variables d'environnement, et les valeurs sont les valeurs des variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="e0a26-199">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="e0a26-200">Par exemple : `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span><span class="sxs-lookup"><span data-stu-id="e0a26-200">For example: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span></span>

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

### <span data-ttu-id="e0a26-201">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e0a26-201">-ExecutionPolicy</span></span>

<span data-ttu-id="e0a26-202">Spécifie la stratégie d'exécution des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-202">Specifies the execution policy of sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-203">Si vous omettez ce paramètre, la valeur de la clé **ExecutionPolicy** dans le fichier de configuration de session est **Restricted**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-203">If you omit this parameter, the value of the **ExecutionPolicy** key in the session configuration file is **Restricted**.</span></span> <span data-ttu-id="e0a26-204">Pour plus d’informations sur les stratégies d’exécution dans PowerShell, consultez [about_Execution_Policies](about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="e0a26-204">For information about execution policies in PowerShell, see [about_Execution_Policies](about/about_Execution_Policies.md).</span></span>

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

### <span data-ttu-id="e0a26-205">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="e0a26-205">-FormatsToProcess</span></span>

<span data-ttu-id="e0a26-206">Spécifie les fichiers de mise en forme (.ps1xml) qui s'exécutent dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-206">Specifies the formatting files (.ps1xml) that run in sessions that use the session configuration.</span></span>
<span data-ttu-id="e0a26-207">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e0a26-207">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="e0a26-208">-Full</span><span class="sxs-lookup"><span data-stu-id="e0a26-208">-Full</span></span>

<span data-ttu-id="e0a26-209">Indique que cette opération comprend toutes les propriétés de configuration possibles dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-209">Indicates that this operation includes all possible configuration properties in the session configuration file.</span></span>

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

### <span data-ttu-id="e0a26-210">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="e0a26-210">-FunctionDefinitions</span></span>

<span data-ttu-id="e0a26-211">Ajoute les fonctions spécifiées aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-211">Adds the specified functions to sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-212">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0a26-212">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="e0a26-213">Nom : nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e0a26-213">Name - Name of the function.</span></span> <span data-ttu-id="e0a26-214">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-214">This key is required.</span></span>
- <span data-ttu-id="e0a26-215">ScriptBlock : corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e0a26-215">ScriptBlock - Function body.</span></span> <span data-ttu-id="e0a26-216">Entrez un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="e0a26-216">Enter a script block.</span></span> <span data-ttu-id="e0a26-217">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-217">This key is required.</span></span>
- <span data-ttu-id="e0a26-218">Options-options de fonction.</span><span class="sxs-lookup"><span data-stu-id="e0a26-218">Options - Function options.</span></span> <span data-ttu-id="e0a26-219">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="e0a26-219">This key is optional.</span></span> <span data-ttu-id="e0a26-220">La valeur par défaut est **None**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-220">The default value is **None**.</span></span> <span data-ttu-id="e0a26-221">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="e0a26-221">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="e0a26-222">Par exemple : `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="e0a26-222">For example: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span></span>

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

### <span data-ttu-id="e0a26-223">-GroupManagedServiceAccount</span><span class="sxs-lookup"><span data-stu-id="e0a26-223">-GroupManagedServiceAccount</span></span>

<span data-ttu-id="e0a26-224">Configure les sessions à l’aide de cette configuration de session pour s’exécuter dans le contexte du compte de service administré de groupe spécifié.</span><span class="sxs-lookup"><span data-stu-id="e0a26-224">Configures sessions using this session configuration to run under the context of the specified Group Managed Service Account.</span></span> <span data-ttu-id="e0a26-225">L’ordinateur sur lequel cette configuration de session est inscrite doit avoir l’autorisation de demander le mot de passe gMSA pour que les sessions soient créées avec succès.</span><span class="sxs-lookup"><span data-stu-id="e0a26-225">The machine where this session configuration is registered must have permission to request the gMSA password in order for sessions to be created successfully.</span></span> <span data-ttu-id="e0a26-226">Ce champ ne peut pas être utilisé avec le paramètre **runasvirtualaccount doit avoir** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-226">This field cannot be used with the **RunAsVirtualAccount** parameter.</span></span>

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

### <span data-ttu-id="e0a26-227">-Guid</span><span class="sxs-lookup"><span data-stu-id="e0a26-227">-Guid</span></span>

<span data-ttu-id="e0a26-228">Spécifie un identificateur unique pour le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-228">Specifies a unique identifier for the session configuration file.</span></span> <span data-ttu-id="e0a26-229">Si vous omettez ce paramètre, `New-PSSessionConfigurationFile` génère un GUID pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="e0a26-229">If you omit this parameter, `New-PSSessionConfigurationFile` generates a GUID for the file.</span></span> <span data-ttu-id="e0a26-230">Pour créer un nouveau GUID dans PowerShell, tapez `New-Guid` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-230">To create a new GUID in PowerShell, type `New-Guid`.</span></span>

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

### <span data-ttu-id="e0a26-231">-LanguageMode</span><span class="sxs-lookup"><span data-stu-id="e0a26-231">-LanguageMode</span></span>

<span data-ttu-id="e0a26-232">Détermine les éléments du langage PowerShell autorisés dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-232">Determines which elements of the PowerShell language are permitted in sessions that use this session configuration.</span></span> <span data-ttu-id="e0a26-233">Vous pouvez utiliser ce paramètre pour limiter les commandes que certains utilisateurs peuvent exécuter sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-233">You can use this parameter to restrict the commands that particular users can run on the computer.</span></span>

<span data-ttu-id="e0a26-234">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="e0a26-234">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e0a26-235">FullLanguage : tous les éléments de langage sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e0a26-235">FullLanguage - All language elements are permitted.</span></span>
- <span data-ttu-id="e0a26-236">ConstrainedLanguage-les commandes qui contiennent des scripts à évaluer ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="e0a26-236">ConstrainedLanguage - Commands that contain scripts to be evaluated are not allowed.</span></span> <span data-ttu-id="e0a26-237">Le mode ConstrainedLanguage restreint l'accès utilisateur aux types, objets ou méthodes Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0a26-237">The ConstrainedLanguage mode restricts user access to Microsoft .NET Framework types, objects, or methods.</span></span>
- <span data-ttu-id="e0a26-238">Nolanguage : les utilisateurs peuvent exécuter des applets de commande et des fonctions, mais ils ne sont pas autorisés à utiliser des éléments de langage, tels que des blocs de script, des variables ou des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="e0a26-238">NoLanguage - Users may run cmdlets and functions, but are not permitted to use any language elements, such as script blocks, variables, or operators.</span></span>
- <span data-ttu-id="e0a26-239">RestrictedLanguage : les utilisateurs peuvent exécuter des applets de commande et des fonctions, mais ils ne sont pas autorisés à utiliser des blocs de script ou des variables, à l’exception des variables autorisées suivantes : `$PSCulture` , `$PSUICulture` ,, `$True` `$False` et `$Null` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-239">RestrictedLanguage - Users may run cmdlets and functions, but are not permitted to use script blocks or variables except for the following permitted variables: `$PSCulture`, `$PSUICulture`, `$True`, `$False`, and `$Null`.</span></span> <span data-ttu-id="e0a26-240">Les utilisateurs peuvent utiliser uniquement les opérateurs de comparaison de base ( `-eq` , `-gt` , `-lt` ).</span><span class="sxs-lookup"><span data-stu-id="e0a26-240">Users may use only the basic comparison operators (`-eq`, `-gt`, `-lt`).</span></span> <span data-ttu-id="e0a26-241">Les instructions d'assignation, les références de propriété et les appels de méthode ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="e0a26-241">Assignment statements, property references, and method calls are not permitted.</span></span>

<span data-ttu-id="e0a26-242">La valeur par défaut du paramètre **LanguageMode** dépend de la valeur du paramètre **SessionType**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-242">The default value of the **LanguageMode** parameter depends on the value of the **SessionType** parameter.</span></span>

- <span data-ttu-id="e0a26-243">Vide-nolanguage</span><span class="sxs-lookup"><span data-stu-id="e0a26-243">Empty - NoLanguage</span></span>
- <span data-ttu-id="e0a26-244">RestrictedRemoteServer-nolanguage</span><span class="sxs-lookup"><span data-stu-id="e0a26-244">RestrictedRemoteServer - NoLanguage</span></span>
- <span data-ttu-id="e0a26-245">Par défaut-FullLanguage</span><span class="sxs-lookup"><span data-stu-id="e0a26-245">Default - FullLanguage</span></span>

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

### <span data-ttu-id="e0a26-246">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="e0a26-246">-ModulesToImport</span></span>

<span data-ttu-id="e0a26-247">Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-247">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="e0a26-248">Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions à distance, mais à moins que les applets de commande ne soient exclues, les utilisateurs peuvent utiliser les `Import-Module` applets de commande et `Add-PSSnapin` pour ajouter des modules et des composants logiciels enfichables à la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-248">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into remote sessions, but unless the cmdlets are excluded, users can use the `Import-Module` and `Add-PSSnapin` cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="e0a26-249">Chaque module ou composant logiciel enfichable inclus dans la valeur de ce paramètre peut être représenté par une chaîne ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="e0a26-249">Each module or snap-in in the value of this parameter can be represented by a string or as a hash table.</span></span> <span data-ttu-id="e0a26-250">Une chaîne de module se compose uniquement du nom du module ou du composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="e0a26-250">A module string consists only of the name of the module or snap-in.</span></span> <span data-ttu-id="e0a26-251">Une table de hachage de module peut inclure des clés **modulename** , **ModuleVersion** et **GUID** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-251">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="e0a26-252">Seule la clé **ModuleName** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-252">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="e0a26-253">Par exemple, la valeur suivante se compose d'une chaîne et d'une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="e0a26-253">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="e0a26-254">Toutes les combinaisons de chaînes et de tables de hachage, dans n'importe quel ordre, sont valides.</span><span class="sxs-lookup"><span data-stu-id="e0a26-254">Any combination of strings and hash tables, in any order, is valid.</span></span>

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

<span data-ttu-id="e0a26-255">La valeur du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` est prioritaire sur la valeur de la clé **ModulesToImport** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-255">The value of the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **ModulesToImport** key in the session configuration file.</span></span>

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

### <span data-ttu-id="e0a26-256">-MountUserDrive</span><span class="sxs-lookup"><span data-stu-id="e0a26-256">-MountUserDrive</span></span>

<span data-ttu-id="e0a26-257">Configure les sessions qui utilisent cette configuration de session pour exposer le `User:` PSDrive.</span><span class="sxs-lookup"><span data-stu-id="e0a26-257">Configures sessions that use this session configuration to expose the `User:` PSDrive.</span></span> <span data-ttu-id="e0a26-258">Les lecteurs utilisateur sont uniques pour chaque utilisateur qui se connecte et permettent aux utilisateurs de copier des données vers et depuis des points de terminaison PowerShell, même si le fournisseur du système de fichiers n’est pas exposé.</span><span class="sxs-lookup"><span data-stu-id="e0a26-258">User drives are unique for each connecting user and allow users to copy data to and from PowerShell endpoints even if the File System provider is not exposed.</span></span> <span data-ttu-id="e0a26-259">Les racines de lecteur utilisateur sont créées sous `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-259">User drive roots are created under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="e0a26-260">Pour chaque utilisateur qui se connecte au point de terminaison, un dossier est créé avec le nom `$env:USERDOMAIN_$env:USERNAME`.</span><span class="sxs-lookup"><span data-stu-id="e0a26-260">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="e0a26-261">Le contenu du lecteur utilisateur est conservé entre les sessions utilisateur et n’est pas automatiquement supprimé.</span><span class="sxs-lookup"><span data-stu-id="e0a26-261">Contents in the user drive persist across user sessions and are not automatically removed.</span></span> <span data-ttu-id="e0a26-262">Par défaut, les utilisateurs peuvent uniquement stocker jusqu’à 50 Mo de données dans le lecteur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-262">By default, users can only store up to 50MB of data in the user drive.</span></span> <span data-ttu-id="e0a26-263">Cela peut être personnalisé avec le paramètre **UserDriveMaximumSize** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-263">This can be customized with the **UserDriveMaximumSize** parameter.</span></span>

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

### <span data-ttu-id="e0a26-264">-Path</span><span class="sxs-lookup"><span data-stu-id="e0a26-264">-Path</span></span>

<span data-ttu-id="e0a26-265">Spécifie le chemin d’accès et le nom du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-265">Specifies the path and filename of the session configuration file.</span></span> <span data-ttu-id="e0a26-266">Le fichier doit avoir une `.pssc` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e0a26-266">The file must have a `.pssc` file name extension.</span></span>

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

### <span data-ttu-id="e0a26-267">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="e0a26-267">-PowerShellVersion</span></span>

<span data-ttu-id="e0a26-268">Spécifie la version du moteur PowerShell dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-268">Specifies the version of the PowerShell engine in sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-269">Les valeurs acceptables pour ce paramètre sont les suivantes : 2,0 et 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0a26-269">The acceptable values for this parameter are: 2.0 and 3.0.</span></span> <span data-ttu-id="e0a26-270">Si vous omettez ce paramètre, la clé **PowerShellVersion** est commentée et la dernière version de PowerShell s’exécute dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-270">If you omit this parameter, the **PowerShellVersion** key is commented-out and newest version of PowerShell runs in the session.</span></span>

<span data-ttu-id="e0a26-271">La valeur du paramètre **psversion** de l’applet de commande `Register-PSSessionConfiguration` est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-271">The value of the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

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

### <span data-ttu-id="e0a26-272">-RequiredGroups</span><span class="sxs-lookup"><span data-stu-id="e0a26-272">-RequiredGroups</span></span>

<span data-ttu-id="e0a26-273">Spécifie les règles d’accès conditionnel pour les utilisateurs se connectant à des sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-273">Specifies conditional access rules for users connecting to sessions that use this session configuration.</span></span>

<span data-ttu-id="e0a26-274">Entrez une table de hachage pour composer votre liste de règles en utilisant uniquement 1 clé par table de hachage, « et » ou « ou », puis définissez la valeur sur un tableau de noms de groupes de sécurité ou de tables de hachage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e0a26-274">Enter a hashtable to compose your list of rules using only 1 key per hashtable, 'And' or 'Or', and set the value to an array of security group names or additional hashtables.</span></span>

<span data-ttu-id="e0a26-275">Exemple nécessitant la connexion des utilisateurs aux membres d’un groupe unique : `@{ And = 'MyRequiredGroup' }`</span><span class="sxs-lookup"><span data-stu-id="e0a26-275">Example requiring connecting users to be members of a single group: `@{ And = 'MyRequiredGroup' }`</span></span>

<span data-ttu-id="e0a26-276">Exemple nécessitant que les utilisateurs appartiennent au groupe A, ou aux deux groupes B et C, pour accéder au point de terminaison : `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span><span class="sxs-lookup"><span data-stu-id="e0a26-276">Example requiring users to belong to group A, or both groups B and C, to access the endpoint: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span></span>

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

### <span data-ttu-id="e0a26-277">-RoleDefinitions</span><span class="sxs-lookup"><span data-stu-id="e0a26-277">-RoleDefinitions</span></span>

<span data-ttu-id="e0a26-278">Spécifie le mappage entre les groupes de sécurité (ou les utilisateurs) et les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="e0a26-278">Specifies the mapping between security groups (or users) and role capabilities.</span></span> <span data-ttu-id="e0a26-279">Les utilisateurs sont autorisés à accéder à toutes les fonctionnalités de rôle qui s’appliquent à leur appartenance à un groupe au moment de la création de la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-279">Users will be granted access to all role capabilities which apply to their group membership at the time the session is created.</span></span>

<span data-ttu-id="e0a26-280">Entrez une table de hachage dans laquelle les clés sont le nom du groupe de sécurité et les valeurs sont des tables de hachage qui contiennent une liste de fonctionnalités de rôle qui doivent être mises à la disposition du groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e0a26-280">Enter a hash table in which the keys are the name of the security group and the values are hash tables that contain a list of role capabilities that should be made available to the security group.</span></span>

<span data-ttu-id="e0a26-281">Par exemple : `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span><span class="sxs-lookup"><span data-stu-id="e0a26-281">For example: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span></span>

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

### <span data-ttu-id="e0a26-282">-Runasvirtualaccount doit avoir</span><span class="sxs-lookup"><span data-stu-id="e0a26-282">-RunAsVirtualAccount</span></span>

<span data-ttu-id="e0a26-283">Configure les sessions qui utilisent cette configuration de session pour être exécutées en tant que compte d’administrateur (virtuel) de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-283">Configures sessions using this session configuration to be run as the computer's (virtual) administrator account.</span></span> <span data-ttu-id="e0a26-284">Ce champ ne peut pas être utilisé avec le paramètre **GroupManagedServiceAccount** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-284">This field cannot be used with the **GroupManagedServiceAccount** parameter.</span></span>

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

### <span data-ttu-id="e0a26-285">-RunAsVirtualAccountGroups</span><span class="sxs-lookup"><span data-stu-id="e0a26-285">-RunAsVirtualAccountGroups</span></span>

<span data-ttu-id="e0a26-286">Spécifie les groupes de sécurité à associer au compte virtuel lorsqu’une session qui utilise la configuration de session est exécutée en tant que compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="e0a26-286">Specifies the security groups to be associated with the virtual account when a session that uses the session configuration is run as a virtual account.</span></span> <span data-ttu-id="e0a26-287">En cas d’omission, le compte virtuel appartient aux administrateurs de domaine sur les contrôleurs de domaine et aux administrateurs sur tous les autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="e0a26-287">If omitted, the virtual account belongs to Domain Admins on domain controllers and Administrators on all other computers.</span></span>

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

### <span data-ttu-id="e0a26-288">-SchemaVersion</span><span class="sxs-lookup"><span data-stu-id="e0a26-288">-SchemaVersion</span></span>

<span data-ttu-id="e0a26-289">Spécifie la version du schéma du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-289">Specifies the version of the session configuration file schema.</span></span> <span data-ttu-id="e0a26-290">La valeur par défaut est « 1.0.0.0 ».</span><span class="sxs-lookup"><span data-stu-id="e0a26-290">The default value is "1.0.0.0".</span></span>

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

### <span data-ttu-id="e0a26-291">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="e0a26-291">-ScriptsToProcess</span></span>

<span data-ttu-id="e0a26-292">Ajoute les scripts spécifiés aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-292">Adds the specified scripts to sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-293">Entrez le chemin d'accès et les noms de fichiers des scripts.</span><span class="sxs-lookup"><span data-stu-id="e0a26-293">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="e0a26-294">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="e0a26-294">The value of this parameter must be a full or absolute path of script file names.</span></span>

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

### <span data-ttu-id="e0a26-295">-SessionType</span><span class="sxs-lookup"><span data-stu-id="e0a26-295">-SessionType</span></span>

<span data-ttu-id="e0a26-296">Spécifie le type de session créé à l'aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-296">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="e0a26-297">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="e0a26-297">The default value is Default.</span></span> <span data-ttu-id="e0a26-298">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="e0a26-298">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e0a26-299">Vide : aucun module n’est ajouté à la session par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0a26-299">Empty - No modules are added to session by default.</span></span> <span data-ttu-id="e0a26-300">Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-300">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span> <span data-ttu-id="e0a26-301">Cette option est conçue pour vous permettre de créer des sessions personnalisées en ajoutant des commandes sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="e0a26-301">This option is designed for you to create custom sessions by adding selected commands.</span></span> <span data-ttu-id="e0a26-302">Si vous n'ajoutez pas de commandes à une session vide, la session est limitée aux expressions et risque d'être inutilisable.</span><span class="sxs-lookup"><span data-stu-id="e0a26-302">If you do not add commands to an empty session, the session is limited to expressions and might not be usable.</span></span>
- <span data-ttu-id="e0a26-303">Default : ajoute le module Microsoft. PowerShell. Core à la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-303">Default - Adds the Microsoft.PowerShell.Core module to the session.</span></span> <span data-ttu-id="e0a26-304">Ce module comprend l' `Import-Module` applet de commande que les utilisateurs peuvent utiliser pour importer d’autres modules, sauf si vous interdisez explicitement cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0a26-304">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit this cmdlet.</span></span>
- <span data-ttu-id="e0a26-305">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="e0a26-305">RestrictedRemoteServer.</span></span> <span data-ttu-id="e0a26-306">Comprend uniquement les fonctions proxy suivantes : `Exit-PSSession` , `Get-Command` , `Get-FormatData` , `Get-Help` , `Measure-Object` , `Out-Default` et `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="e0a26-306">Includes only the following proxy functions: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span>
  <span data-ttu-id="e0a26-307">Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-307">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>

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

### <span data-ttu-id="e0a26-308">-TranscriptDirectory</span><span class="sxs-lookup"><span data-stu-id="e0a26-308">-TranscriptDirectory</span></span>

<span data-ttu-id="e0a26-309">Spécifie le répertoire où placer les transcriptions de session pour les sessions à l’aide de cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-309">Specifies the directory to place session transcripts for sessions using this session configuration.</span></span>

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

### <span data-ttu-id="e0a26-310">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="e0a26-310">-TypesToProcess</span></span>

<span data-ttu-id="e0a26-311">Ajoute les `.ps1xml` fichiers de types spécifiés aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-311">Adds the specified `.ps1xml` type files to sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-312">Entrez les noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="e0a26-312">Enter the type filenames.</span></span> <span data-ttu-id="e0a26-313">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu aux noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="e0a26-313">The value of this parameter must be a full or absolute path to type filenames.</span></span>

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

### <span data-ttu-id="e0a26-314">-UserDriveMaximumSize</span><span class="sxs-lookup"><span data-stu-id="e0a26-314">-UserDriveMaximumSize</span></span>

<span data-ttu-id="e0a26-315">Spécifie la taille maximale des lecteurs utilisateur exposés dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-315">Specifies the maximum size for user drives exposed in sessions that use this session configuration.</span></span>
<span data-ttu-id="e0a26-316">En cas d’omission, la taille par défaut de chaque `User:` racine de lecteur est de 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="e0a26-316">When omitted, the default size of each `User:` drive root is 50MB.</span></span>

<span data-ttu-id="e0a26-317">Ce paramètre doit être utilisé avec **MountUserDrive**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-317">This parameter should be used with **MountUserDrive**.</span></span>

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

### <span data-ttu-id="e0a26-318">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="e0a26-318">-VariableDefinitions</span></span>

<span data-ttu-id="e0a26-319">Ajoute les variables spécifiées aux sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-319">Adds the specified variables to sessions that use the session configuration.</span></span> <span data-ttu-id="e0a26-320">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0a26-320">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="e0a26-321">Nom : nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="e0a26-321">Name - Name of the variable.</span></span> <span data-ttu-id="e0a26-322">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-322">This key is required.</span></span>
- <span data-ttu-id="e0a26-323">Valeur de variable de valeur.</span><span class="sxs-lookup"><span data-stu-id="e0a26-323">Value - Variable value.</span></span> <span data-ttu-id="e0a26-324">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-324">This key is required.</span></span>
- <span data-ttu-id="e0a26-325">Options-options de variable.</span><span class="sxs-lookup"><span data-stu-id="e0a26-325">Options - Variable options.</span></span> <span data-ttu-id="e0a26-326">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="e0a26-326">This key is optional.</span></span> <span data-ttu-id="e0a26-327">La valeur par défaut est **None**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-327">The default value is **None**.</span></span> <span data-ttu-id="e0a26-328">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="e0a26-328">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="e0a26-329">Par exemple : `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="e0a26-329">For example: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span></span>

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

### <span data-ttu-id="e0a26-330">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="e0a26-330">-VisibleAliases</span></span>

<span data-ttu-id="e0a26-331">Limite les alias de la session à ceux spécifiés dans la valeur de ce paramètre, ainsi qu'à tous les alias que vous définissez dans le paramètre **AliasDefinition**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-331">Limits the aliases in the session to those specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="e0a26-332">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e0a26-332">Wildcard characters are supported.</span></span> <span data-ttu-id="e0a26-333">Par défaut, tous les alias définis par le moteur PowerShell et tous les alias que les modules exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-333">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="e0a26-334">Par exemple : `VisibleAliases='gcm', 'gp'`</span><span class="sxs-lookup"><span data-stu-id="e0a26-334">For example: `VisibleAliases='gcm', 'gp'`</span></span>

<span data-ttu-id="e0a26-335">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-335">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="e0a26-336">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="e0a26-336">-VisibleCmdlets</span></span>

<span data-ttu-id="e0a26-337">Limite les applets de commande de la session à celles spécifiées dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="e0a26-337">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="e0a26-338">Les caractères génériques et les noms de module qualifiés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e0a26-338">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="e0a26-339">Par défaut, toutes les applets de commande que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-339">By default, all cmdlets that modules in the session export are visible in the session.</span></span> <span data-ttu-id="e0a26-340">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-340">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="e0a26-341">Si aucun module de **ModulesToImport** n’expose l’applet de commande, le module approprié tentera d’être chargé.</span><span class="sxs-lookup"><span data-stu-id="e0a26-341">If no modules in **ModulesToImport** expose the cmdlet, the appropriate module will attempt to be autoloaded.</span></span>

<span data-ttu-id="e0a26-342">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-342">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="e0a26-343">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="e0a26-343">-VisibleExternalCommands</span></span>

<span data-ttu-id="e0a26-344">Limite les fichiers binaires externes, les scripts et les commandes qui peuvent être exécutés dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="e0a26-344">Limits the external binaries, scripts, and commands that can be executed in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="e0a26-345">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e0a26-345">Wildcard characters are supported.</span></span>

<span data-ttu-id="e0a26-346">Par défaut, aucune commande externe n’est visible dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-346">By default, no external commands are visible in the session.</span></span>

<span data-ttu-id="e0a26-347">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à partir de la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-347">When any **Visible** parameter is included in the session configuration file, PowerShell, removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="e0a26-348">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="e0a26-348">-VisibleFunctions</span></span>

<span data-ttu-id="e0a26-349">Limite les fonctions de la session à celles spécifiées dans la valeur de ce paramètre, ainsi qu'à toutes les fonctions que vous définissez dans le paramètre **FunctionDefinition**.</span><span class="sxs-lookup"><span data-stu-id="e0a26-349">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinition** parameter.</span></span> <span data-ttu-id="e0a26-350">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e0a26-350">Wildcard characters are supported.</span></span>

<span data-ttu-id="e0a26-351">Par défaut, toutes les fonctions que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-351">By default, all functions that modules in the session export are visible in the session.</span></span> <span data-ttu-id="e0a26-352">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-352">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span>

<span data-ttu-id="e0a26-353">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son alias de bureau à pas de la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-353">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="e0a26-354">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="e0a26-354">-VisibleProviders</span></span>

<span data-ttu-id="e0a26-355">Limite les fournisseurs PowerShell dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="e0a26-355">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="e0a26-356">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e0a26-356">Wildcard characters are supported.</span></span>

<span data-ttu-id="e0a26-357">Par défaut, tous les fournisseurs que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-357">By default, all providers that modules in the session export are visible in the session.</span></span> <span data-ttu-id="e0a26-358">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-358">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="e0a26-359">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-359">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="e0a26-360">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0a26-360">CommonParameters</span></span>

<span data-ttu-id="e0a26-361">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0a26-361">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0a26-362">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e0a26-362">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0a26-363">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e0a26-363">INPUTS</span></span>

### <span data-ttu-id="e0a26-364">Aucun</span><span class="sxs-lookup"><span data-stu-id="e0a26-364">None</span></span>

<span data-ttu-id="e0a26-365">Vous ne pouvez pas diriger d’objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0a26-365">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="e0a26-366">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e0a26-366">OUTPUTS</span></span>

### <span data-ttu-id="e0a26-367">Aucun</span><span class="sxs-lookup"><span data-stu-id="e0a26-367">None</span></span>

<span data-ttu-id="e0a26-368">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e0a26-368">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e0a26-369">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e0a26-369">NOTES</span></span>

<span data-ttu-id="e0a26-370">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="e0a26-370">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="e0a26-371">Les paramètres, tels que **VisibleCmdlets** et **VisibleProviders** , n’importent pas d’éléments dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-371">Parameters, such as **VisibleCmdlets** and **VisibleProviders** , do not import items into the session.</span></span> <span data-ttu-id="e0a26-372">À la place, ils sélectionnent les éléments importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-372">Instead, they select from among the items imported into the session.</span></span> <span data-ttu-id="e0a26-373">Par exemple, si la valeur du paramètre **VisibleProviders** est le fournisseur de certificats, mais que le paramètre **ModulesToImport** ne spécifie pas le module **Microsoft. PowerShell. Security** qui contient le fournisseur de certificats, le fournisseur de certificats n’est pas visible dans la session.</span><span class="sxs-lookup"><span data-stu-id="e0a26-373">For example, if the value of the **VisibleProviders** parameter is the Certificate provider, but the **ModulesToImport** parameter does not specify the **Microsoft.PowerShell.Security** module that contains the Certificate provider, the Certificate provider is not visible in the session.</span></span>
- <span data-ttu-id="e0a26-374">`New-PSSessionConfigurationFile` crée un fichier de configuration de session qui a une extension de nom de fichier. PSSC dans le chemin d’accès que vous spécifiez dans le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="e0a26-374">`New-PSSessionConfigurationFile` creates a session configuration file that has a .pssc file name extension in the path that you specify in the **Path** parameter.</span></span> <span data-ttu-id="e0a26-375">Lorsque vous utilisez le fichier de configuration de session pour créer une configuration de session, l’applet de commande `Register-PSSessionConfiguration` copie le fichier de configuration et enregistre une copie active du fichier dans le sous-répertoire **SessionConfig** du `$PSHOME` répertoire.</span><span class="sxs-lookup"><span data-stu-id="e0a26-375">When you use the session configuration file to create a session configuration, the `Register-PSSessionConfiguration` cmdlet copies the configuration file and saves an active copy of the file in the **SessionConfig** subdirectory of the `$PSHOME` directory.</span></span>

  <span data-ttu-id="e0a26-376">La propriété **ConfigFilePath** de la configuration de session contient le chemin d’accès complet du fichier de configuration de session active.</span><span class="sxs-lookup"><span data-stu-id="e0a26-376">The **ConfigFilePath** property of the session configuration contains the fully qualified path of the active session configuration file.</span></span> <span data-ttu-id="e0a26-377">Vous pouvez modifier le fichier de configuration actif dans le `$PSHOME` répertoire à tout moment à l’aide de n’importe quel éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="e0a26-377">You can modify the active configuration file in the `$PSHOME` directory at any time using any text editor.</span></span> <span data-ttu-id="e0a26-378">Les changements que vous apportez affectent toutes les nouvelles sessions qui utilisent la configuration de session, mais pas les sessions existantes.</span><span class="sxs-lookup"><span data-stu-id="e0a26-378">The changes that you make affect all new sessions that use the session configuration, but not existing sessions.</span></span>

  <span data-ttu-id="e0a26-379">Avant d’utiliser un fichier de configuration de session modifié, utilisez l' `Test-PSSessionConfigurationFile` applet de commande pour vérifier que les entrées du fichier de configuration sont valides.</span><span class="sxs-lookup"><span data-stu-id="e0a26-379">Before using an edited session configuration file, use the `Test-PSSessionConfigurationFile` cmdlet to verify that the configuration file entries are valid.</span></span>

## <span data-ttu-id="e0a26-380">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e0a26-380">RELATED LINKS</span></span>

[<span data-ttu-id="e0a26-381">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a26-381">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="e0a26-382">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a26-382">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="e0a26-383">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a26-383">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="e0a26-384">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a26-384">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="e0a26-385">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a26-385">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="e0a26-386">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="e0a26-386">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="e0a26-387">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a26-387">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="e0a26-388">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="e0a26-388">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="e0a26-389">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="e0a26-389">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="e0a26-390">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="e0a26-390">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
