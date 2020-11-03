---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 300fc3dee2e0d625e5aea42bfdcf45ea2e8b5a7f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205674"
---
# <span data-ttu-id="378ae-103">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-103">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="378ae-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="378ae-104">SYNOPSIS</span></span>
<span data-ttu-id="378ae-105">Obtient les configurations de session inscrites sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="378ae-105">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="378ae-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="378ae-106">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="378ae-107">Description</span><span class="sxs-lookup"><span data-stu-id="378ae-107">DESCRIPTION</span></span>

<span data-ttu-id="378ae-108">L' `Get-PSSessionConfiguration` applet de commande obtient les configurations de session qui ont été inscrites sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="378ae-108">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="378ae-109">Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="378ae-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="378ae-110">À compter de PowerShell 3,0, vous pouvez définir les propriétés d’une configuration de session à l’aide d’un fichier de configuration de session (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="378ae-110">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="378ae-111">Cette fonctionnalité vous permet de créer des sessions personnalisées et restreintes sans avoir à écrire un programme informatique.</span><span class="sxs-lookup"><span data-stu-id="378ae-111">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="378ae-112">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-112">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="378ae-113">En outre, à compter de PowerShell 3,0, de nouvelles propriétés de note ont été ajoutées à l’objet de configuration de session `Get-PSSessionConfiguration` retourné par.</span><span class="sxs-lookup"><span data-stu-id="378ae-113">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="378ae-114">Ces propriétés permettent aux utilisateurs et aux auteurs de configuration de session d'examiner et de comparer les configurations de session facilement.</span><span class="sxs-lookup"><span data-stu-id="378ae-114">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="378ae-115">Pour créer et inscrire une configuration de session, utilisez l’applet de commande `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="378ae-115">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="378ae-116">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="378ae-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="378ae-117">EXAMPLES</span></span>

### <span data-ttu-id="378ae-118">Exemple 1 : récupération des configurations de session sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="378ae-118">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="378ae-119">Exemple 2 : récupération des deux configurations de session par défaut</span><span class="sxs-lookup"><span data-stu-id="378ae-119">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="378ae-120">La commande utilise le paramètre **Name** de `Get-PSSessionConfiguration` pour récupérer uniquement les configurations de session dont les noms commencent par « Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="378ae-120">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="378ae-121">Exemple 3 : obtenir les propriétés et les valeurs d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="378ae-121">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="378ae-122">Cet exemple illustre les propriétés et les valeurs de propriété d'une configuration de session qui a été créée à l'aide d'un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="378ae-122">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

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

<span data-ttu-id="378ae-123">L’exemple utilise l' `Get-PSSessionConfiguration` applet de commande pour obtenir la configuration de session complète.</span><span class="sxs-lookup"><span data-stu-id="378ae-123">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="378ae-124">Un opérateur de pipeline envoie la configuration de session complète à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="378ae-124">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="378ae-125">Le paramètre **Property** avec la valeur `*` (All) est dirigé vers l’affichage de `Format-List` toutes les propriétés et valeurs de l’objet dans une liste.</span><span class="sxs-lookup"><span data-stu-id="378ae-125">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="378ae-126">La sortie inclut des informations utiles, notamment l’auteur de la configuration de session, le type de session, le mode de langage et la stratégie d’exécution des sessions créées avec cette configuration de session, les quotas de session et le chemin d’accès complet au fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="378ae-126">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="378ae-127">Cette vue d'une configuration de session est utilisée pour les sessions qui incluent un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="378ae-127">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="378ae-128">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-128">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="378ae-129">Exemple 4 : autre moyen d’examiner les configurations de session</span><span class="sxs-lookup"><span data-stu-id="378ae-129">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="378ae-130">Cet exemple utilise l' `Get-ChildItem` applet de commande (alias `dir` ) dans le lecteur WSMan : Provider pour examiner le contenu du nœud de plug-in.</span><span class="sxs-lookup"><span data-stu-id="378ae-130">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="378ae-131">Il s'agit d'une autre façon d'examiner les configurations de session sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="378ae-131">This is another way to look at the session configurations on the computer.</span></span>

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

<span data-ttu-id="378ae-132">Le nœud de **plug-in** contient des objets **ContainerElement** (Microsoft. WSMan. Management. WSManConfigContainerElement) qui représentent les configurations de session PowerShell inscrites, ainsi que d’autres plug-ins pour WS-Management.</span><span class="sxs-lookup"><span data-stu-id="378ae-132">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="378ae-133">Exemple 6 : afficher les configurations de session sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="378ae-133">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="378ae-134">Cet exemple montre comment utiliser le fournisseur WSMan pour afficher les configurations de session sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="378ae-134">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="378ae-135">Cette méthode ne fournit pas autant d’informations qu’une `Get-PSSessionConfiguration` commande, mais l’utilisateur n’a pas besoin d’être membre du groupe administrateurs pour exécuter cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="378ae-135">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

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

<span data-ttu-id="378ae-136">L' `Connect-WSMan` applet de commande se connecte au service WinRM sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="378ae-136">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="378ae-137">L' `Get-ChildItem` applet `dir` de commande (alias) du lecteur WSMan : obtient les éléments du chemin d’accès **Server01\Plugin** .</span><span class="sxs-lookup"><span data-stu-id="378ae-137">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="378ae-138">La sortie affiche les éléments dans le répertoire Plugin sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="378ae-138">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="378ae-139">Les éléments incluent les configurations de session, qui sont un type de plug-in WSMan, ainsi que d'autres types de plug-in sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="378ae-139">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="378ae-140">Exemple 7 : obtenir des configurations de session détaillées à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="378ae-140">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="378ae-141">Cet exemple montre comment exécuter une `Get-PSSessionConfiguration` commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="378ae-141">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="378ae-142">La commande nécessite que la délégation CredSSP soit activée dans les paramètres du client sur l'ordinateur local et dans les paramètres de service sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="378ae-142">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="378ae-143">Pour exécuter les commandes de cet exemple, vous devez être membre du groupe Administrateurs sur les ordinateurs locaux et distants, et vous devez démarrer PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="378ae-143">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

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

<span data-ttu-id="378ae-144">L' `Enable-WSManCredSSP` applet de commande active la délégation **CredSSP** sur SERVEUR01, l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="378ae-144">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="378ae-145">L' `Connect-WSMan` applet de commande se connecte à l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="378ae-145">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="378ae-146">Cette action ajoute un nœud pour Server02 au lecteur WSMan : sur l’ordinateur local, ce qui vous permet d’afficher et de modifier les paramètres de WS-Management sur l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="378ae-146">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="378ae-147">L' `Set-Item` applet de commande remplace la valeur de l’élément **CredSSP** dans le nœud service de l’ordinateur Server02 par **true** .</span><span class="sxs-lookup"><span data-stu-id="378ae-147">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True** .</span></span> <span data-ttu-id="378ae-148">Cela configure les paramètres de service sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="378ae-148">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="378ae-149">L' `Invoke-Command` applet `Get-PSSessionConfiguration` de commande exécute la commande sur l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="378ae-149">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="378ae-150">La commande utilise le paramètre **Credential** , ainsi que le paramètre **Authentication** avec la valeur **CredSSP** .</span><span class="sxs-lookup"><span data-stu-id="378ae-150">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP** .</span></span> <span data-ttu-id="378ae-151">La sortie indique les configurations de session sur l'ordinateur distant Server02.</span><span class="sxs-lookup"><span data-stu-id="378ae-151">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="378ae-152">Exemple 8 : obtenir l’URI de ressource d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="378ae-152">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="378ae-153">Cet exemple est utile pour définir la valeur de la `$PSSessionConfigurationName` variable de préférence, qui prend un URI de ressource.</span><span class="sxs-lookup"><span data-stu-id="378ae-153">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="378ae-154">La `$PSSessionConfigurationName` variable spécifie la configuration par défaut utilisée lors de la création d’une session.</span><span class="sxs-lookup"><span data-stu-id="378ae-154">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="378ae-155">Cette variable est définie sur l'ordinateur local, mais elle spécifie une configuration sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="378ae-155">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="378ae-156">Pour plus d’informations sur la `$PSSessionConfiguration` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-156">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="378ae-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="378ae-157">PARAMETERS</span></span>

### <span data-ttu-id="378ae-158">-Force</span><span class="sxs-lookup"><span data-stu-id="378ae-158">-Force</span></span>

<span data-ttu-id="378ae-159">Supprime l'invite de redémarrage du service WinRM, si le service n'est pas déjà en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="378ae-159">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="378ae-160">-Name</span><span class="sxs-lookup"><span data-stu-id="378ae-160">-Name</span></span>

<span data-ttu-id="378ae-161">Obtient uniquement les configurations de session portant le nom ou le modèle de nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="378ae-161">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="378ae-162">Entrez un ou plusieurs noms de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="378ae-162">Enter one or more session configuration names.</span></span> <span data-ttu-id="378ae-163">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="378ae-163">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="378ae-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="378ae-164">CommonParameters</span></span>

<span data-ttu-id="378ae-165">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="378ae-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="378ae-166">Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-166">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="378ae-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="378ae-167">INPUTS</span></span>

### <span data-ttu-id="378ae-168">Aucun</span><span class="sxs-lookup"><span data-stu-id="378ae-168">None</span></span>

<span data-ttu-id="378ae-169">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="378ae-169">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="378ae-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="378ae-170">OUTPUTS</span></span>

### <span data-ttu-id="378ae-171">Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="378ae-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="378ae-172">NOTES</span></span>

- <span data-ttu-id="378ae-173">Pour exécuter cette applet de commande, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="378ae-173">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="378ae-174">Pour afficher les configurations de session sur l'ordinateur, vous devez être membre du groupe Administrateurs sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="378ae-174">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="378ae-175">Pour exécuter une `Get-PSSessionConfiguration` commande sur un ordinateur distant, l’authentification du fournisseur de services de sécurité des informations d’identification (CredSSP) doit être activée dans les paramètres du client sur l’ordinateur local (à l’aide de la `Enable-WSManCredSSP` cmdlet) et dans les paramètres de service sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="378ae-175">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="378ae-176">En outre, vous devez utiliser la valeur **CredSSP** du paramètre **Authentication** lors de l’établissement de la session à distance.</span><span class="sxs-lookup"><span data-stu-id="378ae-176">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="378ae-177">Dans le cas contraire, l'accès est refusé.</span><span class="sxs-lookup"><span data-stu-id="378ae-177">Otherwise, access is denied.</span></span>

- <span data-ttu-id="378ae-178">Les propriétés de note de l’objet qui `Get-PSSessionConfiguration` retourne s’affichent sur l’objet uniquement lorsqu’elles ont une valeur.</span><span class="sxs-lookup"><span data-stu-id="378ae-178">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="378ae-179">Seules les configurations de session créées à l’aide d’un fichier de configuration de session ont toutes les propriétés définies.</span><span class="sxs-lookup"><span data-stu-id="378ae-179">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="378ae-180">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="378ae-180">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="378ae-181">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="378ae-181">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="378ae-182">Vous pouvez utiliser les commandes du lecteur WSMan pour modifier les propriétés des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="378ae-182">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="378ae-183">Toutefois, vous ne pouvez pas utiliser le lecteur WSMan : dans PowerShell 2,0 pour modifier les propriétés de configuration de session introduites dans PowerShell 3,0, telles que **OutputBufferingMode** .</span><span class="sxs-lookup"><span data-stu-id="378ae-183">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="378ae-184">Les commandes PowerShell 2,0 ne génèrent pas d’erreur, mais elles sont inefficaces.</span><span class="sxs-lookup"><span data-stu-id="378ae-184">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="378ae-185">Pour modifier les propriétés introduites dans PowerShell 3,0, utilisez le lecteur WSMan : dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="378ae-185">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="378ae-186">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="378ae-186">RELATED LINKS</span></span>

[<span data-ttu-id="378ae-187">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-187">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="378ae-188">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-188">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="378ae-189">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-189">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="378ae-190">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="378ae-190">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="378ae-191">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="378ae-191">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="378ae-192">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-192">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="378ae-193">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-193">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="378ae-194">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="378ae-194">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="378ae-195">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="378ae-195">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="378ae-196">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="378ae-196">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="378ae-197">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="378ae-197">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="378ae-198">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="378ae-198">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

