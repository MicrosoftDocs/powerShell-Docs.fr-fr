---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: c3645a6ba83081bd5ac31a13af0f67f6538db22a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="c90f6-102">Création et connexion à un point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="c90f6-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="c90f6-103">Pour créer un point de terminaison JEA, vous devez créer et inscrire un fichier de configuration de session PowerShell spécialement configuré, que vous pouvez générer avec l’applet de commande **New-PSSessionConfigurationFile**.</span><span class="sxs-lookup"><span data-stu-id="c90f6-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

<span data-ttu-id="c90f6-104">Cela crée un fichier de configuration de session qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="c90f6-104">This will create a session configuration file that looks like this:</span></span> 
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

} 
```
<span data-ttu-id="c90f6-105">Quand vous créez un point de terminaison JEA, vous devez définir les paramètres suivants de la commande (et les clés correspondantes dans le fichier) :</span><span class="sxs-lookup"><span data-stu-id="c90f6-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="c90f6-106">SessionType doit avoir la valeur RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="c90f6-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="c90f6-107">RunAsVirtualAccount doit avoir la valeur **$true**</span><span class="sxs-lookup"><span data-stu-id="c90f6-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="c90f6-108">TranscriptPath doit avoir comme valeur le répertoire où les transcriptions « avec procuration de privilège » seront enregistrées après chaque session</span><span class="sxs-lookup"><span data-stu-id="c90f6-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="c90f6-109">RoleDefinitions doit avoir comme valeur une table de hachage qui définit les groupes qui ont accès aux différentes « capacités de rôle »</span><span class="sxs-lookup"><span data-stu-id="c90f6-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="c90f6-110">Ce champ définit **qui** peut faire **quoi** sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c90f6-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="c90f6-111">Les capacités de rôle sont des fichiers spéciaux dont nous verront plus loin la signification.</span><span class="sxs-lookup"><span data-stu-id="c90f6-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="c90f6-112">Le champ RoleDefinitions définit les groupes qui avaient accès aux différentes capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="c90f6-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="c90f6-113">Une capacité de rôle est un fichier qui définit un ensemble de capacités qui seront exposées aux utilisateurs qui se connectent.</span><span class="sxs-lookup"><span data-stu-id="c90f6-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="c90f6-114">Vous pouvez créer des capacités de rôle avec la commande **New-PSRoleCapabilityFile**.</span><span class="sxs-lookup"><span data-stu-id="c90f6-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

<span data-ttu-id="c90f6-115">Cela génère un modèle de capacité de rôle qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="c90f6-115">This will generate a template role capability that looks like this:</span></span>
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

} 

```
<span data-ttu-id="c90f6-116">Pour pouvoir être utilisées par une configuration de session JEA, les capacités de rôle doivent être enregistrées en tant que modules PowerShell valides dans un répertoire nommé « RoleCapabilities ».</span><span class="sxs-lookup"><span data-stu-id="c90f6-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="c90f6-117">Un module peut avoir plusieurs fichiers de capacités de rôle, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="c90f6-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="c90f6-118">Pour commencer à configurer les applets de commande, les fonctions, les alias et les scripts auxquels un utilisateur peut accéder lors de la connexion à une session JEA, ajoutez vos propres règles dans le fichier de capacité de rôle après les modèles commentés.</span><span class="sxs-lookup"><span data-stu-id="c90f6-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="c90f6-119">Pour étudier de manière approfondie comment configurer des capacités de rôle, consultez le [guide d’expérience](http://aka.ms/JEA) complet.</span><span class="sxs-lookup"><span data-stu-id="c90f6-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="c90f6-120">Pour finir, une fois que vous avez terminé de personnaliser votre configuration de session et les capacités de rôle associées, enregistrez cette configuration de session et créez le point de terminaison en exécutant **Register-PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="c90f6-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="c90f6-121">Se connecter à un point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="c90f6-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="c90f6-122">La connexion à un point de terminaison JEA s’effectue comme pour tout autre point de terminaison PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c90f6-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="c90f6-123">Il suffit de donner votre nom de point de terminaison JEA comme paramètre « ConfigurationName » pour **New-PSSession**, **Invoke-Command** ou **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c90f6-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="c90f6-124">Une fois connecté à la session JEA, vous êtes limité à l’exécution des commandes figurant dans la liste approuvée dans les capacités de rôle auxquelles vous avez accès.</span><span class="sxs-lookup"><span data-stu-id="c90f6-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="c90f6-125">Si vous essayez d’exécuter une commande non autorisée pour votre rôle, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="c90f6-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>

