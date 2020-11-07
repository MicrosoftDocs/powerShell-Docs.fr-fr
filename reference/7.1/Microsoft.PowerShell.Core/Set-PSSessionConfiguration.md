---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 788e7b9d261a862658f4cf7453f35228dd3ffab6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345848"
---
# <span data-ttu-id="c4934-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4934-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="c4934-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c4934-104">SYNOPSIS</span></span>
<span data-ttu-id="c4934-105">Modifie les propriétés d'une configuration de session enregistrée.</span><span class="sxs-lookup"><span data-stu-id="c4934-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="c4934-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c4934-106">SYNTAX</span></span>

### <span data-ttu-id="c4934-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c4934-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c4934-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="c4934-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c4934-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="c4934-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="c4934-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c4934-110">DESCRIPTION</span></span>

<span data-ttu-id="c4934-111">L' `Set-PSSessionConfiguration` applet de commande modifie les propriétés des configurations de session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c4934-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="c4934-112">Utilisez le paramètre **Name** pour identifier la configuration de session que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="c4934-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="c4934-113">Utilisez les autres paramètres pour spécifier les nouvelles valeurs des propriétés de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="c4934-114">Pour supprimer une valeur de propriété de la configuration et utiliser la valeur par défaut, entrez une chaîne vide ("") ou une valeur `$Null` pour le paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="c4934-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="c4934-115">À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="c4934-116">Cette fonctionnalité offre une méthode simple et intuitive pour définir ou modifier les propriétés des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="c4934-117">Pour spécifier un fichier de configuration de session, utilisez le paramètre **path** de `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="c4934-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="c4934-118">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="c4934-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="c4934-119">Pour plus d’informations sur la création et la modification d’un fichier de configuration de session, consultez l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="c4934-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="c4934-120">Les configurations de session définissent l’environnement des sessions à distance ( **sessions PSSession** ) qui se connectent à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c4934-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="c4934-121">Chaque session **PSSession** utilise une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="c4934-122">La configuration de session détermine les fonctionnalités de la session **PSSession** , telles que les modules qui sont disponibles dans la session, les applets de commande qui sont autorisées à s’exécuter, le mode de langage, les quotas et les délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="c4934-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="c4934-123">Le descripteur de sécurité de la configuration de session détermine qui peut utiliser la configuration de session pour se connecter à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c4934-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="c4934-124">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c4934-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="c4934-125">Pour afficher les propriétés d’une configuration de session, utilisez l’applet de commande `Get-PSSessionConfiguration` ou le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="c4934-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="c4934-126">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="c4934-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="c4934-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c4934-127">EXAMPLES</span></span>

### <span data-ttu-id="c4934-128">Exemple 1 : créer et modifier une configuration de session</span><span class="sxs-lookup"><span data-stu-id="c4934-128">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="c4934-129">Cet exemple montre comment ajouter et supprimer un script de démarrage d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-129">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="c4934-130">La première commande crée la configuration **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="c4934-130">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="c4934-131">La deuxième commande ajoute le `AdminConfig.ps1` script à la configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-131">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="c4934-132">La modification est effective quand vous redémarrez **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="c4934-132">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="c4934-133">La troisième commande supprime le `AdminConfig.ps1` script de la configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-133">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="c4934-134">Exemple 2 : afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="c4934-134">Example 2: Display results</span></span>

<span data-ttu-id="c4934-135">Cet exemple augmente la valeur de la propriété **MaximumReceivedObjectSizeMB** à 20.</span><span class="sxs-lookup"><span data-stu-id="c4934-135">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="c4934-136">Cette commande vous invite également à redémarrer le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="c4934-136">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="c4934-137">La modification n’est pas effective tant que le service **WinRM** n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="c4934-137">The change is not effective until the **WinRM** service is restarted.</span></span>

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

### <span data-ttu-id="c4934-138">Exemple 3 : afficher les résultats de différentes façons</span><span class="sxs-lookup"><span data-stu-id="c4934-138">Example 3: Display results in different ways</span></span>

<span data-ttu-id="c4934-139">Dans cet exemple, `Set-PSSessionConfiguration` modifie le script de démarrage dans la configuration de session **MaintenanceShell** en `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="c4934-139">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="c4934-140">La sortie affiche la modification et vous invite à redémarrer le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="c4934-140">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="c4934-141">La réponse est « y » (Oui).</span><span class="sxs-lookup"><span data-stu-id="c4934-141">The response is "y" (yes).</span></span>

<span data-ttu-id="c4934-142">`Get-PSSessionConfiguration` Obtient la configuration de session **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="c4934-142">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="c4934-143">L’opérateur de pipeline (|) envoie les résultats de la commande à `Format-List` , qui affiche toutes les propriétés de l’objet de configuration dans une liste.</span><span class="sxs-lookup"><span data-stu-id="c4934-143">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="c4934-144">Ensuite, à l’aide du fournisseur WSMan, nous allons voir les paramètres d’initialisation de la configuration **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="c4934-144">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="c4934-145">`Get-ChildItem` (alias `dir` ) Obtient les éléments enfants dans le nœud **InitializationParameters** pour le plug-in **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="c4934-145">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="c4934-146">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="c4934-146">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

## <span data-ttu-id="c4934-147">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="c4934-147">PARAMETERS</span></span>

### <span data-ttu-id="c4934-148">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="c4934-148">-AccessMode</span></span>

<span data-ttu-id="c4934-149">Active et désactive la configuration de session et détermine si elle peut être utilisée pour les sessions locales ou distantes sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c4934-149">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="c4934-150">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c4934-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c4934-151">Désactivé.</span><span class="sxs-lookup"><span data-stu-id="c4934-151">Disabled.</span></span> <span data-ttu-id="c4934-152">désactive la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-152">Disables the session configuration.</span></span> <span data-ttu-id="c4934-153">Elle ne peut pas être utilisée pour l'accès local ou distant à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c4934-153">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="c4934-154">Cette valeur affecte la **Enabled** valeur `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` **false** à la propriété Enabled de la configuration de session ().</span><span class="sxs-lookup"><span data-stu-id="c4934-154">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="c4934-155">Local.</span><span class="sxs-lookup"><span data-stu-id="c4934-155">Local.</span></span> <span data-ttu-id="c4934-156">ajoute un entrée **Network_Deny_All** au descripteur de sécurité de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-156">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="c4934-157">Les utilisateurs de l’ordinateur local peuvent utiliser la configuration de session pour créer une session de bouclage locale sur le même ordinateur, mais l’accès est refusé aux utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="c4934-157">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="c4934-158">Distant.</span><span class="sxs-lookup"><span data-stu-id="c4934-158">Remote.</span></span> <span data-ttu-id="c4934-159">supprime les entrées **Deny_All** et **Network_Deny_All** des descripteurs de sécurité de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-159">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="c4934-160">Les utilisateurs des ordinateurs locaux et distants peuvent utiliser la configuration de session pour créer des sessions et exécuter des commandes sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c4934-160">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="c4934-161">La valeur par défaut est **Remote**.</span><span class="sxs-lookup"><span data-stu-id="c4934-161">The default value is **Remote**.</span></span>

<span data-ttu-id="c4934-162">D’autres applets de commande peuvent remplacer la valeur de ce paramètre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="c4934-162">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="c4934-163">Par exemple, l' `Enable-PSRemoting` applet de commande active toutes les configurations de session sur l’ordinateur et autorise l’accès à distance à celles-ci, et l’applet de commande `Disable-PSRemoting` autorise uniquement l’accès local à toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c4934-163">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="c4934-164">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-164">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-165">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="c4934-165">-ApplicationBase</span></span>

<span data-ttu-id="c4934-166">Spécifie le chemin d’accès du fichier d’assembly ( \* . dll) qui est spécifié dans la valeur du paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="c4934-166">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="c4934-167">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="c4934-167">-AssemblyName</span></span>

<span data-ttu-id="c4934-168">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c4934-168">Specifies the assembly name.</span></span> <span data-ttu-id="c4934-169">Cette applet de commande crée une configuration de session basée sur une classe définie dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="c4934-169">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="c4934-170">Entrez le nom de fichier ou le chemin d’accès complet d’un fichier. dll d’assembly qui définit une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-170">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="c4934-171">Si vous entrez uniquement le nom du fichier, vous pouvez entrer le chemin d’accès dans la valeur du paramètre **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="c4934-171">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

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

### <span data-ttu-id="c4934-172">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="c4934-172">-ConfigurationTypeName</span></span>

<span data-ttu-id="c4934-173">Spécifie le type de la configuration de session définie dans l'assembly dans le paramètre **AssemblyName**.</span><span class="sxs-lookup"><span data-stu-id="c4934-173">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="c4934-174">Le type que vous spécifiez doit implémenter la classe **System.Management.Automation.Remoting.PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="c4934-174">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="c4934-175">Ce paramètre est obligatoire quand vous spécifiez un nom d'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4934-175">This parameter is required when you specify an assembly name.</span></span>

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

### <span data-ttu-id="c4934-176">-Force</span><span class="sxs-lookup"><span data-stu-id="c4934-176">-Force</span></span>

<span data-ttu-id="c4934-177">Supprime toutes les invites utilisateur et redémarre le service **WinRM** sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="c4934-177">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="c4934-178">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-178">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="c4934-179">Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart**.</span><span class="sxs-lookup"><span data-stu-id="c4934-179">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="c4934-180">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="c4934-180">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="c4934-181">Spécifie la limite de la quantité de données qui peut être envoyée à cet ordinateur dans une commande à distance unique.</span><span class="sxs-lookup"><span data-stu-id="c4934-181">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="c4934-182">Entrez la taille des données en mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="c4934-182">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="c4934-183">La valeur par défaut est 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="c4934-183">The default is 50 MB.</span></span>

<span data-ttu-id="c4934-184">Si une limite de taille des données est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c4934-184">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="c4934-185">La valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="c4934-185">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="c4934-186">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="c4934-186">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="c4934-187">Spécifie les limites de la quantité de données qui peuvent être envoyées à cet ordinateur dans un objet unique.</span><span class="sxs-lookup"><span data-stu-id="c4934-187">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="c4934-188">Entrez la taille des données en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="c4934-188">Enter the data size in megabytes.</span></span> <span data-ttu-id="c4934-189">La valeur par défaut est 10 Mo.</span><span class="sxs-lookup"><span data-stu-id="c4934-189">The default is 10 MB.</span></span>

<span data-ttu-id="c4934-190">Si une limite de taille d’objet est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c4934-190">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="c4934-191">La valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="c4934-191">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="c4934-192">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="c4934-192">-ModulesToImport</span></span>

<span data-ttu-id="c4934-193">Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-193">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="c4934-194">Entrez les noms des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="c4934-194">Enter the module and snap-in names.</span></span>

<span data-ttu-id="c4934-195">Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions, mais à moins que les applets de commande ne soient exclues, vous pouvez utiliser les `Import-Module` applets de commande et Add-PSSnapin pour ajouter des modules et des composants logiciels enfichables à la session.</span><span class="sxs-lookup"><span data-stu-id="c4934-195">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="c4934-196">Les modules spécifiés dans cette valeur de paramètre sont importés en compléments des modules spécifiés dans le fichier de configuration de session ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="c4934-196">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="c4934-197">Toutefois, les paramètres dans le fichier de configuration de session peuvent masquer les commandes exportées par les modules ou empêcher les utilisateurs de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="c4934-197">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="c4934-198">Les modules spécifiés dans cette valeur de paramètre remplacent la liste de modules spécifiée à l’aide du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="c4934-198">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="c4934-199">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-199">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-200">-Name</span><span class="sxs-lookup"><span data-stu-id="c4934-200">-Name</span></span>

<span data-ttu-id="c4934-201">Spécifie le nom de la configuration de session que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="c4934-201">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="c4934-202">Vous ne pouvez pas utiliser ce paramètre pour modifier le nom de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-202">You cannot use this parameter to change the name of the session configuration.</span></span>

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

### <span data-ttu-id="c4934-203">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="c4934-203">-NoServiceRestart</span></span>

<span data-ttu-id="c4934-204">Ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="c4934-204">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="c4934-205">Par défaut, lorsque vous exécutez `Set-PSSessionConfiguration` , vous êtes invité à redémarrer le service **WinRM** pour que la nouvelle configuration de session soit effective.</span><span class="sxs-lookup"><span data-stu-id="c4934-205">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="c4934-206">Tant que le service **WinRM** n’est pas redémarré, la nouvelle configuration de session n’est pas effective.</span><span class="sxs-lookup"><span data-stu-id="c4934-206">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="c4934-207">Pour redémarrer le service **WinRM** sans invite, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="c4934-207">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="c4934-208">Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4934-208">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="c4934-209">-Path</span><span class="sxs-lookup"><span data-stu-id="c4934-209">-Path</span></span>

<span data-ttu-id="c4934-210">Spécifie le chemin d’accès d’un fichier de configuration de session (. PSSC), tel que celui créé par l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="c4934-210">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="c4934-211">Si vous omettez le chemin d'accès, la valeur par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c4934-211">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="c4934-212">Pour plus d’informations sur la modification d’un fichier de configuration de session, consultez la rubrique d’aide de l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="c4934-212">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="c4934-213">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-213">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-214">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="c4934-214">-PSVersion</span></span>

<span data-ttu-id="c4934-215">Spécifie la version de PowerShell dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-215">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="c4934-216">La valeur de ce paramètre est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-216">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="c4934-217">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-218">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c4934-218">-RunAsCredential</span></span>

<span data-ttu-id="c4934-219">Spécifie des informations d’identification pour les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="c4934-219">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="c4934-220">Par défaut, les commandes s'exécutent avec les autorisations de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c4934-220">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="c4934-221">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-221">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-222">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="c4934-222">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="c4934-223">Spécifie une chaîne SDDL (Security Descriptor Definition Language) différente pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-223">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="c4934-224">Cette chaîne détermine les autorisations qui sont nécessaires pour utiliser la nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-224">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="c4934-225">Pour utiliser une configuration de session dans une session, les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-225">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="c4934-226">Pour utiliser le descripteur de sécurité par défaut pour la configuration, entrez une chaîne vide ("") ou une valeur `$Null` .</span><span class="sxs-lookup"><span data-stu-id="c4934-226">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="c4934-227">La valeur par défaut est le SDDL racine dans le WSMan:.</span><span class="sxs-lookup"><span data-stu-id="c4934-227">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="c4934-228">Si le descripteur de sécurité est complexe, envisagez d’utiliser le paramètre **ShowSecurityDescriptorUI** au lieu de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c4934-228">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="c4934-229">Vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="c4934-229">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="c4934-230">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="c4934-230">-SessionTypeOption</span></span>

<span data-ttu-id="c4934-231">Spécifie les options spécifiques au type pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-231">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="c4934-232">Entrez un objet d’options de type de session, tel que l’objet **PSWorkflowExecutionOption** retourné par l’applet de commande `New-PSWorkflowExecutionOption` .</span><span class="sxs-lookup"><span data-stu-id="c4934-232">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="c4934-233">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-233">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="c4934-234">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-234">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="c4934-235">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-235">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="c4934-236">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-236">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-237">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="c4934-237">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="c4934-238">Indique que cette applet de commande est une feuille de propriétés qui vous aide à créer un nouveau SDDL pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-238">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="c4934-239">La feuille de propriétés s’affiche après l’exécution de la `Set-PSSessionConfiguration` commande, puis le redémarrage du service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="c4934-239">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="c4934-240">Lorsque vous définissez des autorisations sur la configuration, n’oubliez pas que les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour utiliser la configuration de session dans une session.</span><span class="sxs-lookup"><span data-stu-id="c4934-240">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="c4934-241">Vous ne pouvez pas utiliser le paramètre **SecurityDescriptorSDDL** et ce paramètre dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="c4934-241">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="c4934-242">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="c4934-242">-StartupScript</span></span>

<span data-ttu-id="c4934-243">Spécifie le script de démarrage pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-243">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="c4934-244">Entrez le chemin d’accès complet d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4934-244">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="c4934-245">Le script spécifié est exécuté dans la nouvelle session qui utilise la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-245">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="c4934-246">Pour supprimer un script de démarrage d’une configuration de session, entrez une chaîne vide ("") ou une valeur `$Null` .</span><span class="sxs-lookup"><span data-stu-id="c4934-246">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="c4934-247">Vous pouvez utiliser un script de démarrage pour configurer davantage la session utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c4934-247">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="c4934-248">Si le script génère une erreur, même une erreur sans fin d’exécution, la session n’est pas créée et la `New-PSSession` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="c4934-248">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="c4934-249">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="c4934-249">-ThreadOptions</span></span>

<span data-ttu-id="c4934-250">Spécifie le paramètre des options de thread dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c4934-250">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="c4934-251">Ce paramètre définit comment les threads sont créés et utilisés quand une commande est exécutée dans la session.</span><span class="sxs-lookup"><span data-stu-id="c4934-251">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="c4934-252">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c4934-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c4934-253">Default</span><span class="sxs-lookup"><span data-stu-id="c4934-253">Default</span></span>
- <span data-ttu-id="c4934-254">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="c4934-254">ReuseThread</span></span>
- <span data-ttu-id="c4934-255">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="c4934-255">UseCurrentThread</span></span>
- <span data-ttu-id="c4934-256">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="c4934-256">UseNewThread</span></span>

<span data-ttu-id="c4934-257">La valeur par défaut est **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="c4934-257">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="c4934-258">Pour plus d’informations, consultez [énumération PSThreadOptions](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span><span class="sxs-lookup"><span data-stu-id="c4934-258">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

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

### <span data-ttu-id="c4934-259">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="c4934-259">-TransportOption</span></span>

<span data-ttu-id="c4934-260">Spécifie les options de transport pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-260">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="c4934-261">Entrez un objet d’options de transport, tel que l’objet **WSManConfigurationOption** retourné par l’applet de commande `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="c4934-261">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="c4934-262">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-262">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="c4934-263">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-263">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="c4934-264">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-264">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="c4934-265">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-265">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-266">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="c4934-266">-UseSharedProcess</span></span>

<span data-ttu-id="c4934-267">Utilisez un seul processus pour héberger toutes les sessions qui sont démarrées par le même utilisateur et utiliser la même configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-267">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="c4934-268">Par défaut, chaque session est hébergée dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="c4934-268">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="c4934-269">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-269">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c4934-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c4934-270">-Confirm</span></span>

<span data-ttu-id="c4934-271">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4934-271">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c4934-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c4934-272">-WhatIf</span></span>

<span data-ttu-id="c4934-273">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4934-273">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c4934-274">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c4934-274">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c4934-275">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="c4934-275">-ThreadApartmentState</span></span>

<span data-ttu-id="c4934-276">Spécifie l’état de cloisonnement du module de thread à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c4934-276">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="c4934-277">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="c4934-277">Acceptable values are:</span></span>

- <span data-ttu-id="c4934-278">Inconnu</span><span class="sxs-lookup"><span data-stu-id="c4934-278">Unknown</span></span>
- <span data-ttu-id="c4934-279">MTA</span><span class="sxs-lookup"><span data-stu-id="c4934-279">MTA</span></span>
- <span data-ttu-id="c4934-280">STA</span><span class="sxs-lookup"><span data-stu-id="c4934-280">STA</span></span>

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

### <span data-ttu-id="c4934-281">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4934-281">CommonParameters</span></span>

<span data-ttu-id="c4934-282">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4934-282">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4934-283">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c4934-283">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4934-284">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c4934-284">INPUTS</span></span>

### <span data-ttu-id="c4934-285">Aucun</span><span class="sxs-lookup"><span data-stu-id="c4934-285">None</span></span>

<span data-ttu-id="c4934-286">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4934-286">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c4934-287">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c4934-287">OUTPUTS</span></span>

### <span data-ttu-id="c4934-288">Microsoft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="c4934-288">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="c4934-289">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c4934-289">NOTES</span></span>

<span data-ttu-id="c4934-290">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="c4934-290">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="c4934-291">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="c4934-291">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="c4934-292">L' `Set-PSSessionConfiguration` applet de commande ne modifie pas le nom de la configuration et le fournisseur **WSMan** ne prend pas en charge l’applet de commande `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="c4934-292">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="c4934-293">Pour modifier le nom d’une configuration de session, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration, puis utilisez l' `Register-PSSessionConfiguration` applet de commande pour créer et inscrire une nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-293">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="c4934-294">Vous pouvez utiliser l' `Set-PSSessionConfiguration` applet de commande pour modifier les configurations de session Microsoft. PowerShell et Microsoft. powershell32 par défaut.</span><span class="sxs-lookup"><span data-stu-id="c4934-294">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="c4934-295">Elles ne sont pas protégées.</span><span class="sxs-lookup"><span data-stu-id="c4934-295">They are not protected.</span></span> <span data-ttu-id="c4934-296">Pour revenir à la version d’origine d’une configuration de session par défaut, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration de session par défaut, puis utilisez l' `Enable-PSRemoting` applet de commande pour la restaurer.</span><span class="sxs-lookup"><span data-stu-id="c4934-296">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="c4934-297">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="c4934-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="c4934-298">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c4934-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="c4934-299">Vous pouvez utiliser les commandes du lecteur WSMan pour modifier les propriétés des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="c4934-299">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="c4934-300">Toutefois, vous ne pouvez pas utiliser le lecteur WSMan : dans PowerShell 2,0 pour modifier les propriétés de configuration de session introduites dans PowerShell 3,0, telles que **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="c4934-300">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="c4934-301">Les commandes Windows PowerShell 2.0 ne génèrent pas d'erreur, mais elles sont inefficaces.</span><span class="sxs-lookup"><span data-stu-id="c4934-301">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="c4934-302">Pour modifier les propriétés introduites dans PowerShell 3,0, utilisez le lecteur WSMan : dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4934-302">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="c4934-303">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c4934-303">RELATED LINKS</span></span>

[<span data-ttu-id="c4934-304">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4934-304">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="c4934-305">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4934-305">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="c4934-306">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4934-306">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="c4934-307">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="c4934-307">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="c4934-308">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="c4934-308">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="c4934-309">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="c4934-309">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="c4934-310">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4934-310">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="c4934-311">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="c4934-311">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="c4934-312">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4934-312">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="c4934-313">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="c4934-313">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="c4934-314">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="c4934-314">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="c4934-315">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="c4934-315">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
