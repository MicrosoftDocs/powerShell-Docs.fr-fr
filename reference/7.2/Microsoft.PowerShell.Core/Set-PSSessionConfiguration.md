---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: c3c3c0bbb0436ef2e6857adc35f83e627d03f4b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595719"
---
# <span data-ttu-id="d9b59-102">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b59-102">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="d9b59-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d9b59-103">SYNOPSIS</span></span>
<span data-ttu-id="d9b59-104">Modifie les propriétés d'une configuration de session enregistrée.</span><span class="sxs-lookup"><span data-stu-id="d9b59-104">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="d9b59-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d9b59-105">SYNTAX</span></span>

### <span data-ttu-id="d9b59-106">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d9b59-106">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d9b59-107">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d9b59-107">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d9b59-108">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d9b59-108">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="d9b59-109">Description</span><span class="sxs-lookup"><span data-stu-id="d9b59-109">DESCRIPTION</span></span>

<span data-ttu-id="d9b59-110">L' `Set-PSSessionConfiguration` applet de commande modifie les propriétés des configurations de session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d9b59-110">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="d9b59-111">Utilisez le paramètre **Name** pour identifier la configuration de session que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="d9b59-111">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="d9b59-112">Utilisez les autres paramètres pour spécifier les nouvelles valeurs des propriétés de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-112">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="d9b59-113">Pour supprimer une valeur de propriété de la configuration et utiliser la valeur par défaut, entrez une chaîne vide ("") ou une valeur `$Null` pour le paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="d9b59-113">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="d9b59-114">À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-114">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="d9b59-115">Cette fonctionnalité offre une méthode simple et intuitive pour définir ou modifier les propriétés des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-115">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="d9b59-116">Pour spécifier un fichier de configuration de session, utilisez le paramètre **path** de `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-116">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="d9b59-117">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="d9b59-117">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="d9b59-118">Pour plus d’informations sur la création et la modification d’un fichier de configuration de session, consultez l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-118">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="d9b59-119">Les configurations de session définissent l’environnement des sessions à distance (**sessions PSSession**) qui se connectent à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d9b59-119">Session configurations define the environment of remote sessions (**PSSessions**) that connect to the local computer.</span></span> <span data-ttu-id="d9b59-120">Chaque session **PSSession** utilise une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-120">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="d9b59-121">La configuration de session détermine les fonctionnalités de la session **PSSession**, telles que les modules qui sont disponibles dans la session, les applets de commande qui sont autorisées à s’exécuter, le mode de langage, les quotas et les délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="d9b59-121">The session configuration determines the features of the **PSSession**, such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="d9b59-122">Le descripteur de sécurité de la configuration de session détermine qui peut utiliser la configuration de session pour se connecter à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d9b59-122">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="d9b59-123">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d9b59-123">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="d9b59-124">Pour afficher les propriétés d’une configuration de session, utilisez l’applet de commande `Get-PSSessionConfiguration` ou le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="d9b59-124">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="d9b59-125">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-125">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="d9b59-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d9b59-126">EXAMPLES</span></span>

### <span data-ttu-id="d9b59-127">Exemple 1 : créer et modifier une configuration de session</span><span class="sxs-lookup"><span data-stu-id="d9b59-127">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="d9b59-128">Cet exemple montre comment ajouter et supprimer un script de démarrage d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-128">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="d9b59-129">La première commande crée la configuration **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-129">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="d9b59-130">La deuxième commande ajoute le `AdminConfig.ps1` script à la configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-130">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="d9b59-131">La modification est effective quand vous redémarrez **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-131">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="d9b59-132">La troisième commande supprime le `AdminConfig.ps1` script de la configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-132">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="d9b59-133">Exemple 2 : afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="d9b59-133">Example 2: Display results</span></span>

<span data-ttu-id="d9b59-134">Cet exemple augmente la valeur de la propriété **MaximumReceivedObjectSizeMB** à 20.</span><span class="sxs-lookup"><span data-stu-id="d9b59-134">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="d9b59-135">Cette commande vous invite également à redémarrer le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-135">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="d9b59-136">La modification n’est pas effective tant que le service **WinRM** n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="d9b59-136">The change is not effective until the **WinRM** service is restarted.</span></span>

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### <span data-ttu-id="d9b59-137">Exemple 3 : afficher les résultats de différentes façons</span><span class="sxs-lookup"><span data-stu-id="d9b59-137">Example 3: Display results in different ways</span></span>

<span data-ttu-id="d9b59-138">Dans cet exemple, `Set-PSSessionConfiguration` modifie le script de démarrage dans la configuration de session **MaintenanceShell** en `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-138">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="d9b59-139">La sortie affiche la modification et vous invite à redémarrer le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-139">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="d9b59-140">La réponse est « y » (Oui).</span><span class="sxs-lookup"><span data-stu-id="d9b59-140">The response is "y" (yes).</span></span>

<span data-ttu-id="d9b59-141">`Get-PSSessionConfiguration` Obtient la configuration de session **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-141">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="d9b59-142">L’opérateur de pipeline (|) envoie les résultats de la commande à `Format-List` , qui affiche toutes les propriétés de l’objet de configuration dans une liste.</span><span class="sxs-lookup"><span data-stu-id="d9b59-142">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="d9b59-143">Ensuite, à l’aide du fournisseur WSMan, nous allons voir les paramètres d’initialisation de la configuration **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-143">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="d9b59-144">`Get-ChildItem` (alias `dir` ) Obtient les éléments enfants dans le nœud **InitializationParameters** pour le plug-in **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-144">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="d9b59-145">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-145">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## <span data-ttu-id="d9b59-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9b59-146">PARAMETERS</span></span>

### <span data-ttu-id="d9b59-147">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="d9b59-147">-AccessMode</span></span>

<span data-ttu-id="d9b59-148">Active et désactive la configuration de session et détermine si elle peut être utilisée pour les sessions locales ou distantes sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9b59-148">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="d9b59-149">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d9b59-149">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d9b59-150">Désactivé.</span><span class="sxs-lookup"><span data-stu-id="d9b59-150">Disabled.</span></span> <span data-ttu-id="d9b59-151">désactive la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-151">Disables the session configuration.</span></span> <span data-ttu-id="d9b59-152">Elle ne peut pas être utilisée pour l'accès local ou distant à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9b59-152">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="d9b59-153">Cette valeur affecte la  valeur `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` **false** à la propriété Enabled de la configuration de session ().</span><span class="sxs-lookup"><span data-stu-id="d9b59-153">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="d9b59-154">Local.</span><span class="sxs-lookup"><span data-stu-id="d9b59-154">Local.</span></span> <span data-ttu-id="d9b59-155">ajoute un entrée **Network_Deny_All** au descripteur de sécurité de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-155">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="d9b59-156">Les utilisateurs de l’ordinateur local peuvent utiliser la configuration de session pour créer une session de bouclage locale sur le même ordinateur, mais l’accès est refusé aux utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="d9b59-156">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="d9b59-157">Distant.</span><span class="sxs-lookup"><span data-stu-id="d9b59-157">Remote.</span></span> <span data-ttu-id="d9b59-158">supprime les entrées **Deny_All** et **Network_Deny_All** des descripteurs de sécurité de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-158">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="d9b59-159">Les utilisateurs des ordinateurs locaux et distants peuvent utiliser la configuration de session pour créer des sessions et exécuter des commandes sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9b59-159">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="d9b59-160">La valeur par défaut est **Remote**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-160">The default value is **Remote**.</span></span>

<span data-ttu-id="d9b59-161">D’autres applets de commande peuvent remplacer la valeur de ce paramètre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="d9b59-161">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="d9b59-162">Par exemple, l' `Enable-PSRemoting` applet de commande active toutes les configurations de session sur l’ordinateur et autorise l’accès à distance à celles-ci, et l’applet de commande `Disable-PSRemoting` autorise uniquement l’accès local à toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d9b59-162">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="d9b59-163">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-163">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-164">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="d9b59-164">-ApplicationBase</span></span>

<span data-ttu-id="d9b59-165">Spécifie le chemin d’accès du fichier d’assembly ( \* . dll) qui est spécifié dans la valeur du paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-165">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-166">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="d9b59-166">-AssemblyName</span></span>

<span data-ttu-id="d9b59-167">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d9b59-167">Specifies the assembly name.</span></span> <span data-ttu-id="d9b59-168">Cette applet de commande crée une configuration de session basée sur une classe définie dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="d9b59-168">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="d9b59-169">Entrez le nom de fichier ou le chemin d’accès complet d’un fichier. dll d’assembly qui définit une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-169">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="d9b59-170">Si vous entrez uniquement le nom du fichier, vous pouvez entrer le chemin d’accès dans la valeur du paramètre **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-170">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-171">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="d9b59-171">-ConfigurationTypeName</span></span>

<span data-ttu-id="d9b59-172">Spécifie le type de la configuration de session définie dans l'assembly dans le paramètre **AssemblyName**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-172">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="d9b59-173">Le type que vous spécifiez doit implémenter la classe **System.Management.Automation.Remoting.PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-173">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="d9b59-174">Ce paramètre est obligatoire quand vous spécifiez un nom d'assembly.</span><span class="sxs-lookup"><span data-stu-id="d9b59-174">This parameter is required when you specify an assembly name.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-175">-Force</span><span class="sxs-lookup"><span data-stu-id="d9b59-175">-Force</span></span>

<span data-ttu-id="d9b59-176">Supprime toutes les invites utilisateur et redémarre le service **WinRM** sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="d9b59-176">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="d9b59-177">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-177">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="d9b59-178">Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-178">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="d9b59-179">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="d9b59-179">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="d9b59-180">Spécifie la limite de la quantité de données qui peut être envoyée à cet ordinateur dans une commande à distance unique.</span><span class="sxs-lookup"><span data-stu-id="d9b59-180">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="d9b59-181">Entrez la taille des données en mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="d9b59-181">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="d9b59-182">La valeur par défaut est 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="d9b59-182">The default is 50 MB.</span></span>

<span data-ttu-id="d9b59-183">Si une limite de taille des données est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d9b59-183">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="d9b59-184">La valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="d9b59-184">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-185">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="d9b59-185">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="d9b59-186">Spécifie les limites de la quantité de données qui peuvent être envoyées à cet ordinateur dans un objet unique.</span><span class="sxs-lookup"><span data-stu-id="d9b59-186">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="d9b59-187">Entrez la taille des données en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="d9b59-187">Enter the data size in megabytes.</span></span> <span data-ttu-id="d9b59-188">La valeur par défaut est 10 Mo.</span><span class="sxs-lookup"><span data-stu-id="d9b59-188">The default is 10 MB.</span></span>

<span data-ttu-id="d9b59-189">Si une limite de taille d’objet est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d9b59-189">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="d9b59-190">La valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="d9b59-190">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-191">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="d9b59-191">-ModulesToImport</span></span>

<span data-ttu-id="d9b59-192">Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-192">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="d9b59-193">Entrez les noms des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="d9b59-193">Enter the module and snap-in names.</span></span>

<span data-ttu-id="d9b59-194">Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions, mais à moins que les applets de commande ne soient exclues, vous pouvez utiliser les `Import-Module` applets de commande et Add-PSSnapin pour ajouter des modules et des composants logiciels enfichables à la session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-194">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="d9b59-195">Les modules spécifiés dans cette valeur de paramètre sont importés en compléments des modules spécifiés dans le fichier de configuration de session ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="d9b59-195">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="d9b59-196">Toutefois, les paramètres dans le fichier de configuration de session peuvent masquer les commandes exportées par les modules ou empêcher les utilisateurs de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="d9b59-196">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="d9b59-197">Les modules spécifiés dans cette valeur de paramètre remplacent la liste de modules spécifiée à l’aide du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-197">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="d9b59-198">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-198">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-199">-Name</span><span class="sxs-lookup"><span data-stu-id="d9b59-199">-Name</span></span>

<span data-ttu-id="d9b59-200">Spécifie le nom de la configuration de session que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="d9b59-200">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="d9b59-201">Vous ne pouvez pas utiliser ce paramètre pour modifier le nom de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-201">You cannot use this parameter to change the name of the session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-202">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="d9b59-202">-NoServiceRestart</span></span>

<span data-ttu-id="d9b59-203">Ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="d9b59-203">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="d9b59-204">Par défaut, lorsque vous exécutez `Set-PSSessionConfiguration` , vous êtes invité à redémarrer le service **WinRM** pour que la nouvelle configuration de session soit effective.</span><span class="sxs-lookup"><span data-stu-id="d9b59-204">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="d9b59-205">Tant que le service **WinRM** n’est pas redémarré, la nouvelle configuration de session n’est pas effective.</span><span class="sxs-lookup"><span data-stu-id="d9b59-205">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="d9b59-206">Pour redémarrer le service **WinRM** sans invite, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-206">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="d9b59-207">Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9b59-207">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="d9b59-208">-Path</span><span class="sxs-lookup"><span data-stu-id="d9b59-208">-Path</span></span>

<span data-ttu-id="d9b59-209">Spécifie le chemin d’accès d’un fichier de configuration de session (. PSSC), tel que celui créé par l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-209">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="d9b59-210">Si vous omettez le chemin d'accès, la valeur par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9b59-210">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="d9b59-211">Pour plus d’informations sur la modification d’un fichier de configuration de session, consultez la rubrique d’aide de l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-211">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="d9b59-212">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-212">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-213">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="d9b59-213">-PSVersion</span></span>

<span data-ttu-id="d9b59-214">Spécifie la version de PowerShell dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-214">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="d9b59-215">La valeur de ce paramètre est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-215">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="d9b59-216">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-216">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-217">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d9b59-217">-RunAsCredential</span></span>

<span data-ttu-id="d9b59-218">Spécifie des informations d’identification pour les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-218">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="d9b59-219">Par défaut, les commandes s'exécutent avec les autorisations de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d9b59-219">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="d9b59-220">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-220">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="d9b59-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="d9b59-222">Spécifie une chaîne SDDL (Security Descriptor Definition Language) différente pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-222">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="d9b59-223">Cette chaîne détermine les autorisations qui sont nécessaires pour utiliser la nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-223">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="d9b59-224">Pour utiliser une configuration de session dans une session, les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-224">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="d9b59-225">Pour utiliser le descripteur de sécurité par défaut pour la configuration, entrez une chaîne vide ("") ou une valeur `$Null` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-225">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="d9b59-226">La valeur par défaut est le SDDL racine dans le WSMan:.</span><span class="sxs-lookup"><span data-stu-id="d9b59-226">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="d9b59-227">Si le descripteur de sécurité est complexe, envisagez d’utiliser le paramètre **ShowSecurityDescriptorUI** au lieu de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d9b59-227">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="d9b59-228">Vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d9b59-228">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="d9b59-229">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="d9b59-229">-SessionTypeOption</span></span>

<span data-ttu-id="d9b59-230">Spécifie les options spécifiques au type pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-230">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="d9b59-231">Entrez un objet d’options de type de session, tel que l’objet **PSWorkflowExecutionOption** retourné par l’applet de commande `New-PSWorkflowExecutionOption` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-231">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="d9b59-232">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-232">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="d9b59-233">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-233">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="d9b59-234">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-234">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="d9b59-235">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-235">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-236">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="d9b59-236">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="d9b59-237">Indique que cette applet de commande est une feuille de propriétés qui vous aide à créer un nouveau SDDL pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-237">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="d9b59-238">La feuille de propriétés s’affiche après l’exécution de la `Set-PSSessionConfiguration` commande, puis le redémarrage du service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="d9b59-238">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="d9b59-239">Lorsque vous définissez des autorisations sur la configuration, n’oubliez pas que les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour utiliser la configuration de session dans une session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-239">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="d9b59-240">Vous ne pouvez pas utiliser le paramètre **SecurityDescriptorSDDL** et ce paramètre dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d9b59-240">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="d9b59-241">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="d9b59-241">-StartupScript</span></span>

<span data-ttu-id="d9b59-242">Spécifie le script de démarrage pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-242">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="d9b59-243">Entrez le chemin d’accès complet d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9b59-243">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="d9b59-244">Le script spécifié est exécuté dans la nouvelle session qui utilise la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-244">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="d9b59-245">Pour supprimer un script de démarrage d’une configuration de session, entrez une chaîne vide ("") ou une valeur `$Null` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-245">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="d9b59-246">Vous pouvez utiliser un script de démarrage pour configurer davantage la session utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d9b59-246">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="d9b59-247">Si le script génère une erreur, même une erreur sans fin d’exécution, la session n’est pas créée et la `New-PSSession` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="d9b59-247">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="d9b59-248">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="d9b59-248">-ThreadOptions</span></span>

<span data-ttu-id="d9b59-249">Spécifie le paramètre des options de thread dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d9b59-249">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="d9b59-250">Ce paramètre définit comment les threads sont créés et utilisés quand une commande est exécutée dans la session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-250">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="d9b59-251">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d9b59-251">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d9b59-252">Default</span><span class="sxs-lookup"><span data-stu-id="d9b59-252">Default</span></span>
- <span data-ttu-id="d9b59-253">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="d9b59-253">ReuseThread</span></span>
- <span data-ttu-id="d9b59-254">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="d9b59-254">UseCurrentThread</span></span>
- <span data-ttu-id="d9b59-255">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="d9b59-255">UseNewThread</span></span>

<span data-ttu-id="d9b59-256">La valeur par défaut est **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-256">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="d9b59-257">Pour plus d’informations, consultez [énumération PSThreadOptions](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span><span class="sxs-lookup"><span data-stu-id="d9b59-257">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-258">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="d9b59-258">-TransportOption</span></span>

<span data-ttu-id="d9b59-259">Spécifie les options de transport pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-259">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="d9b59-260">Entrez un objet d’options de transport, tel que l’objet **WSManConfigurationOption** retourné par l’applet de commande `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-260">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="d9b59-261">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-261">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="d9b59-262">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-262">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="d9b59-263">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-263">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="d9b59-264">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-264">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-265">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="d9b59-265">-UseSharedProcess</span></span>

<span data-ttu-id="d9b59-266">Utilisez un seul processus pour héberger toutes les sessions qui sont démarrées par le même utilisateur et utiliser la même configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-266">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="d9b59-267">Par défaut, chaque session est hébergée dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="d9b59-267">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="d9b59-268">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-268">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d9b59-269">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d9b59-269">-Confirm</span></span>

<span data-ttu-id="d9b59-270">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9b59-270">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d9b59-271">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d9b59-271">-WhatIf</span></span>

<span data-ttu-id="d9b59-272">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9b59-272">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d9b59-273">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d9b59-273">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d9b59-274">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="d9b59-274">-ThreadApartmentState</span></span>

<span data-ttu-id="d9b59-275">Spécifie l’état de cloisonnement du module de thread à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d9b59-275">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="d9b59-276">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="d9b59-276">Acceptable values are:</span></span>

- <span data-ttu-id="d9b59-277">Unknown</span><span class="sxs-lookup"><span data-stu-id="d9b59-277">Unknown</span></span>
- <span data-ttu-id="d9b59-278">MTA</span><span class="sxs-lookup"><span data-stu-id="d9b59-278">MTA</span></span>
- <span data-ttu-id="d9b59-279">STA</span><span class="sxs-lookup"><span data-stu-id="d9b59-279">STA</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9b59-280">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d9b59-280">CommonParameters</span></span>

<span data-ttu-id="d9b59-281">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d9b59-281">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d9b59-282">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d9b59-282">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d9b59-283">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d9b59-283">INPUTS</span></span>

### <span data-ttu-id="d9b59-284">None</span><span class="sxs-lookup"><span data-stu-id="d9b59-284">None</span></span>

<span data-ttu-id="d9b59-285">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9b59-285">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d9b59-286">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d9b59-286">OUTPUTS</span></span>

### <span data-ttu-id="d9b59-287">Microsoft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="d9b59-287">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="d9b59-288">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d9b59-288">NOTES</span></span>

<span data-ttu-id="d9b59-289">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="d9b59-289">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="d9b59-290">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d9b59-290">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="d9b59-291">L' `Set-PSSessionConfiguration` applet de commande ne modifie pas le nom de la configuration et le fournisseur **WSMan** ne prend pas en charge l’applet de commande `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="d9b59-291">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="d9b59-292">Pour modifier le nom d’une configuration de session, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration, puis utilisez l' `Register-PSSessionConfiguration` applet de commande pour créer et inscrire une nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-292">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="d9b59-293">Vous pouvez utiliser l' `Set-PSSessionConfiguration` applet de commande pour modifier les configurations de session Microsoft. PowerShell et Microsoft. powershell32 par défaut.</span><span class="sxs-lookup"><span data-stu-id="d9b59-293">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="d9b59-294">Elles ne sont pas protégées.</span><span class="sxs-lookup"><span data-stu-id="d9b59-294">They are not protected.</span></span> <span data-ttu-id="d9b59-295">Pour revenir à la version d’origine d’une configuration de session par défaut, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration de session par défaut, puis utilisez l' `Enable-PSRemoting` applet de commande pour la restaurer.</span><span class="sxs-lookup"><span data-stu-id="d9b59-295">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="d9b59-296">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="d9b59-296">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="d9b59-297">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d9b59-297">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="d9b59-298">Vous pouvez utiliser les commandes du lecteur WSMan pour modifier les propriétés des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="d9b59-298">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="d9b59-299">Toutefois, vous ne pouvez pas utiliser le lecteur WSMan : dans PowerShell 2,0 pour modifier les propriétés de configuration de session introduites dans PowerShell 3,0, telles que **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="d9b59-299">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="d9b59-300">Les commandes Windows PowerShell 2.0 ne génèrent pas d'erreur, mais elles sont inefficaces.</span><span class="sxs-lookup"><span data-stu-id="d9b59-300">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="d9b59-301">Pour modifier les propriétés introduites dans PowerShell 3,0, utilisez le lecteur WSMan : dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9b59-301">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="d9b59-302">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d9b59-302">RELATED LINKS</span></span>

[<span data-ttu-id="d9b59-303">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b59-303">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="d9b59-304">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b59-304">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="d9b59-305">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b59-305">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="d9b59-306">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d9b59-306">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="d9b59-307">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="d9b59-307">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="d9b59-308">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="d9b59-308">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="d9b59-309">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b59-309">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="d9b59-310">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d9b59-310">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="d9b59-311">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b59-311">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="d9b59-312">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="d9b59-312">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="d9b59-313">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="d9b59-313">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="d9b59-314">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="d9b59-314">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
