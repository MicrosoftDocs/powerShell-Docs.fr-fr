---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: e4910e95a417da61661aaddd98b2dc7da9f98a3d
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093716"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Création et connexion à un point de terminaison JEA
Pour créer un point de terminaison JEA, vous devez créer et inscrire un fichier de configuration de session PowerShell spécialement configuré, que vous pouvez générer avec l’applet de commande **New-PSSessionConfigurationFile**.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Cela crée un fichier de configuration de session qui ressemble à ceci :
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
Quand vous créez un point de terminaison JEA, vous devez définir les paramètres suivants de la commande (et les clés correspondantes dans le fichier) :
1.  SessionType doit avoir la valeur RestrictedRemoteServer
2.  RunAsVirtualAccount doit avoir la valeur **$true**
3.  TranscriptPath doit avoir comme valeur le répertoire où les transcriptions « avec procuration de privilège » seront enregistrées après chaque session
4.  RoleDefinitions doit avoir comme valeur une table de hachage qui définit les groupes qui ont accès aux différentes « capacités de rôle »  Ce champ définit **qui** peut faire **quoi** sur ce point de terminaison.   Les capacités de rôle sont des fichiers spéciaux dont nous verront plus loin la signification.


Le champ RoleDefinitions définit les groupes qui avaient accès aux différentes capacités de rôle.  Une capacité de rôle est un fichier qui définit un ensemble de capacités qui seront exposées aux utilisateurs qui se connectent.  Vous pouvez créer des capacités de rôle avec la commande **New-PSRoleCapabilityFile**.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Cela génère un modèle de capacité de rôle qui ressemble à ceci :
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

Pour pouvoir être utilisées par une configuration de session JEA, les capacités de rôle doivent être enregistrées en tant que modules PowerShell valides dans un répertoire nommé « RoleCapabilities ». Un module peut avoir plusieurs fichiers de capacités de rôle, si vous le souhaitez.

Pour commencer à configurer les applets de commande, les fonctions, les alias et les scripts auxquels un utilisateur peut accéder lors de la connexion à une session JEA, ajoutez vos propres règles dans le fichier de capacité de rôle après les modèles commentés. Pour étudier de manière approfondie comment configurer des capacités de rôle, consultez le [guide d’expérience](http://aka.ms/JEA) complet.

Pour finir, une fois que vous avez terminé de personnaliser votre configuration de session et les capacités de rôle associées, enregistrez cette configuration de session et créez le point de terminaison en exécutant **Register-PSSessionConfiguration**.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Se connecter à un point de terminaison JEA

La connexion à un point de terminaison JEA s’effectue comme pour tout autre point de terminaison PowerShell.  Il suffit de donner votre nom de point de terminaison JEA comme paramètre « ConfigurationName » pour **New-PSSession**, **Invoke-Command** ou **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

Une fois connecté à la session JEA, vous êtes limité à l’exécution des commandes figurant dans la liste approuvée dans les capacités de rôle auxquelles vous avez accès. Si vous essayez d’exécuter une commande non autorisée pour votre rôle, une erreur se produit.