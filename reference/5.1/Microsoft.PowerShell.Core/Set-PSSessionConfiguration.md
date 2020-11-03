---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 33773769cd19373764cf4adbe86bb990589948ff
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205374"
---
# <span data-ttu-id="bcf37-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="bcf37-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bcf37-104">SYNOPSIS</span></span>
<span data-ttu-id="bcf37-105">Modifie les propriétés d'une configuration de session enregistrée.</span><span class="sxs-lookup"><span data-stu-id="bcf37-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="bcf37-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bcf37-106">SYNTAX</span></span>

### <span data-ttu-id="bcf37-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="bcf37-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bcf37-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="bcf37-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bcf37-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bcf37-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bcf37-110">Description</span><span class="sxs-lookup"><span data-stu-id="bcf37-110">DESCRIPTION</span></span>

<span data-ttu-id="bcf37-111">L' `Set-PSSessionConfiguration` applet de commande modifie les propriétés des configurations de session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bcf37-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="bcf37-112">Utilisez le paramètre **Name** pour identifier la configuration de session que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="bcf37-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="bcf37-113">Utilisez les autres paramètres pour spécifier les nouvelles valeurs des propriétés de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="bcf37-114">Pour supprimer une valeur de propriété de la configuration et utiliser la valeur par défaut, entrez une chaîne vide ("") ou une valeur `$Null` pour le paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="bcf37-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="bcf37-115">À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="bcf37-116">Cette fonctionnalité offre une méthode simple et intuitive pour définir ou modifier les propriétés des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="bcf37-117">Pour spécifier un fichier de configuration de session, utilisez le paramètre **path** de `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="bcf37-118">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="bcf37-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="bcf37-119">Pour plus d’informations sur la création et la modification d’un fichier de configuration de session, consultez l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="bcf37-120">Les configurations de session définissent l’environnement des sessions à distance ( **sessions PSSession** ) qui se connectent à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bcf37-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="bcf37-121">Chaque session **PSSession** utilise une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="bcf37-122">La configuration de session détermine les fonctionnalités de la session **PSSession** , telles que les modules qui sont disponibles dans la session, les applets de commande qui sont autorisées à s’exécuter, le mode de langage, les quotas et les délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="bcf37-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="bcf37-123">Le descripteur de sécurité de la configuration de session détermine qui peut utiliser la configuration de session pour se connecter à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bcf37-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="bcf37-124">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="bcf37-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="bcf37-125">Pour afficher les propriétés d’une configuration de session, utilisez l’applet de commande `Get-PSSessionConfiguration` ou le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="bcf37-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="bcf37-126">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="bcf37-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bcf37-127">EXAMPLES</span></span>

### <span data-ttu-id="bcf37-128">Exemple 1 : modifier l’état de cloisonnement du thread</span><span class="sxs-lookup"><span data-stu-id="bcf37-128">Example 1: Change the thread apartment state</span></span>

```
PS C:\> Set-PSSessionConfiguration -Name "MaintenanceShell" -ThreadApartmentState STA
```

<span data-ttu-id="bcf37-129">Cette commande définit sur STA l'état de cloisonnement des threads dans la configuration MaintenanceShell.</span><span class="sxs-lookup"><span data-stu-id="bcf37-129">This command changes the thread apartment state in the MaintenanceShell configuration to STA.</span></span>
<span data-ttu-id="bcf37-130">La modification est effective quand vous redémarrez le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-130">The change is effective when you restart the **WinRM** service.</span></span>

### <span data-ttu-id="bcf37-131">Exemple 2 : créer et modifier une configuration de session</span><span class="sxs-lookup"><span data-stu-id="bcf37-131">Example 2: Create and change a session configuration</span></span>

<span data-ttu-id="bcf37-132">Cet exemple montre comment ajouter et supprimer un script de démarrage d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-132">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="bcf37-133">La première commande crée la configuration **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-133">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="bcf37-134">La deuxième commande ajoute le `AdminConfig.ps1` script à la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-134">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="bcf37-135">La modification est effective quand vous redémarrez **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-135">The change is effective when you restart **WinRM** .</span></span>
<span data-ttu-id="bcf37-136">La troisième commande supprime le `AdminConfig.ps1` script de la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-136">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="bcf37-137">Exemple 3 : afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="bcf37-137">Example 3: Display results</span></span>

<span data-ttu-id="bcf37-138">Cet exemple augmente la valeur de la propriété **MaximumReceivedObjectSizeMB** à 20.</span><span class="sxs-lookup"><span data-stu-id="bcf37-138">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="bcf37-139">Cette commande vous invite également à redémarrer le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-139">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="bcf37-140">La modification n’est pas effective tant que le service **WinRM** n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="bcf37-140">The change is not effective until the **WinRM** service is restarted.</span></span>

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

### <span data-ttu-id="bcf37-141">Exemple 4 : afficher les résultats de différentes façons</span><span class="sxs-lookup"><span data-stu-id="bcf37-141">Example 4: Display results in different ways</span></span>

<span data-ttu-id="bcf37-142">Dans cet exemple, `Set-PSSessionConfiguration` modifie le script de démarrage dans la configuration de session **MaintenanceShell** en `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-142">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="bcf37-143">La sortie affiche la modification et vous invite à redémarrer le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-143">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="bcf37-144">La réponse est « y » (Oui).</span><span class="sxs-lookup"><span data-stu-id="bcf37-144">The response is "y" (yes).</span></span>

<span data-ttu-id="bcf37-145">`Get-PSSessionConfiguration` Obtient la configuration de session **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-145">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="bcf37-146">L’opérateur de pipeline (|) envoie les résultats de la commande à `Format-List` , qui affiche toutes les propriétés de l’objet de configuration dans une liste.</span><span class="sxs-lookup"><span data-stu-id="bcf37-146">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="bcf37-147">Ensuite, à l’aide du fournisseur WSMan, nous allons voir les paramètres d’initialisation de la configuration **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-147">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="bcf37-148">`Get-ChildItem` (alias `dir` ) Obtient les éléments enfants dans le nœud **InitializationParameters** pour le plug-in **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-148">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="bcf37-149">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-149">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```
PS> Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

PS> Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *

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

PS> dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## <span data-ttu-id="bcf37-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bcf37-150">PARAMETERS</span></span>

### <span data-ttu-id="bcf37-151">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="bcf37-151">-AccessMode</span></span>

<span data-ttu-id="bcf37-152">Active et désactive la configuration de session et détermine si elle peut être utilisée pour les sessions locales ou distantes sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bcf37-152">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="bcf37-153">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="bcf37-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bcf37-154">Désactivé.</span><span class="sxs-lookup"><span data-stu-id="bcf37-154">Disabled.</span></span> <span data-ttu-id="bcf37-155">désactive la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-155">Disables the session configuration.</span></span> <span data-ttu-id="bcf37-156">Elle ne peut pas être utilisée pour l'accès local ou distant à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bcf37-156">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="bcf37-157">Cette valeur affecte la **Enabled** valeur `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` **false** à la propriété Enabled de la configuration de session ().</span><span class="sxs-lookup"><span data-stu-id="bcf37-157">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False** .</span></span>
- <span data-ttu-id="bcf37-158">Local.</span><span class="sxs-lookup"><span data-stu-id="bcf37-158">Local.</span></span> <span data-ttu-id="bcf37-159">ajoute un entrée **Network_Deny_All** au descripteur de sécurité de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-159">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="bcf37-160">Les utilisateurs de l’ordinateur local peuvent utiliser la configuration de session pour créer une session de bouclage locale sur le même ordinateur, mais l’accès est refusé aux utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="bcf37-160">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="bcf37-161">Distant.</span><span class="sxs-lookup"><span data-stu-id="bcf37-161">Remote.</span></span> <span data-ttu-id="bcf37-162">supprime les entrées **Deny_All** et **Network_Deny_All** des descripteurs de sécurité de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-162">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="bcf37-163">Les utilisateurs des ordinateurs locaux et distants peuvent utiliser la configuration de session pour créer des sessions et exécuter des commandes sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bcf37-163">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="bcf37-164">La valeur par défaut est **Remote** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-164">The default value is **Remote** .</span></span>

<span data-ttu-id="bcf37-165">D’autres applets de commande peuvent remplacer la valeur de ce paramètre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="bcf37-165">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="bcf37-166">Par exemple, l' `Enable-PSRemoting` applet de commande active toutes les configurations de session sur l’ordinateur et autorise l’accès à distance à celles-ci, et l’applet de commande `Disable-PSRemoting` autorise uniquement l’accès local à toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bcf37-166">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="bcf37-167">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-167">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-168">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="bcf37-168">-ApplicationBase</span></span>

<span data-ttu-id="bcf37-169">Spécifie le chemin d’accès du fichier d’assembly ( \* . dll) qui est spécifié dans la valeur du paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-169">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="bcf37-170">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="bcf37-170">-AssemblyName</span></span>

<span data-ttu-id="bcf37-171">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcf37-171">Specifies the assembly name.</span></span> <span data-ttu-id="bcf37-172">Cette applet de commande crée une configuration de session basée sur une classe définie dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="bcf37-172">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="bcf37-173">Entrez le nom de fichier ou le chemin d’accès complet d’un fichier. dll d’assembly qui définit une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-173">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="bcf37-174">Si vous entrez uniquement le nom du fichier, vous pouvez entrer le chemin d’accès dans la valeur du paramètre **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-174">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

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

### <span data-ttu-id="bcf37-175">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="bcf37-175">-ConfigurationTypeName</span></span>

<span data-ttu-id="bcf37-176">Spécifie le type de la configuration de session définie dans l'assembly dans le paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-176">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="bcf37-177">Le type que vous spécifiez doit implémenter la classe **System.Management.Automation.Remoting.PSSessionConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-177">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="bcf37-178">Ce paramètre est obligatoire quand vous spécifiez un nom d'assembly.</span><span class="sxs-lookup"><span data-stu-id="bcf37-178">This parameter is required when you specify an assembly name.</span></span>

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

### <span data-ttu-id="bcf37-179">-Force</span><span class="sxs-lookup"><span data-stu-id="bcf37-179">-Force</span></span>

<span data-ttu-id="bcf37-180">Supprime toutes les invites utilisateur et redémarre le service **WinRM** sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="bcf37-180">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="bcf37-181">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-181">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="bcf37-182">Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-182">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="bcf37-183">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="bcf37-183">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="bcf37-184">Spécifie la limite de la quantité de données qui peut être envoyée à cet ordinateur dans une commande à distance unique.</span><span class="sxs-lookup"><span data-stu-id="bcf37-184">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="bcf37-185">Entrez la taille des données en mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="bcf37-185">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="bcf37-186">La valeur par défaut est 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="bcf37-186">The default is 50 MB.</span></span>

<span data-ttu-id="bcf37-187">Si une limite de taille des données est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bcf37-187">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="bcf37-188">La valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="bcf37-188">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf37-189">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="bcf37-189">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="bcf37-190">Spécifie les limites de la quantité de données qui peuvent être envoyées à cet ordinateur dans un objet unique.</span><span class="sxs-lookup"><span data-stu-id="bcf37-190">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="bcf37-191">Entrez la taille des données en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="bcf37-191">Enter the data size in megabytes.</span></span> <span data-ttu-id="bcf37-192">La valeur par défaut est 10 Mo.</span><span class="sxs-lookup"><span data-stu-id="bcf37-192">The default is 10 MB.</span></span>

<span data-ttu-id="bcf37-193">Si une limite de taille d’objet est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bcf37-193">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="bcf37-194">La valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="bcf37-194">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf37-195">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="bcf37-195">-ModulesToImport</span></span>

<span data-ttu-id="bcf37-196">Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-196">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="bcf37-197">Entrez les noms des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="bcf37-197">Enter the module and snap-in names.</span></span>

<span data-ttu-id="bcf37-198">Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions, mais à moins que les applets de commande ne soient exclues, vous pouvez utiliser les `Import-Module` applets de commande et Add-PSSnapin pour ajouter des modules et des composants logiciels enfichables à la session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-198">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="bcf37-199">Les modules spécifiés dans cette valeur de paramètre sont importés en compléments des modules spécifiés dans le fichier de configuration de session ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="bcf37-199">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="bcf37-200">Toutefois, les paramètres dans le fichier de configuration de session peuvent masquer les commandes exportées par les modules ou empêcher les utilisateurs de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="bcf37-200">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="bcf37-201">Les modules spécifiés dans cette valeur de paramètre remplacent la liste de modules spécifiée à l’aide du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-201">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="bcf37-202">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-202">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-203">-Name</span><span class="sxs-lookup"><span data-stu-id="bcf37-203">-Name</span></span>

<span data-ttu-id="bcf37-204">Spécifie le nom de la configuration de session que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="bcf37-204">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="bcf37-205">Vous ne pouvez pas utiliser ce paramètre pour modifier le nom de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-205">You cannot use this parameter to change the name of the session configuration.</span></span>

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

### <span data-ttu-id="bcf37-206">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="bcf37-206">-NoServiceRestart</span></span>

<span data-ttu-id="bcf37-207">Ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="bcf37-207">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="bcf37-208">Par défaut, lorsque vous exécutez `Set-PSSessionConfiguration` , vous êtes invité à redémarrer le service **WinRM** pour que la nouvelle configuration de session soit effective.</span><span class="sxs-lookup"><span data-stu-id="bcf37-208">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="bcf37-209">Tant que le service **WinRM** n’est pas redémarré, la nouvelle configuration de session n’est pas effective.</span><span class="sxs-lookup"><span data-stu-id="bcf37-209">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="bcf37-210">Pour redémarrer le service **WinRM** sans invite, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-210">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="bcf37-211">Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bcf37-211">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="bcf37-212">-Path</span><span class="sxs-lookup"><span data-stu-id="bcf37-212">-Path</span></span>

<span data-ttu-id="bcf37-213">Spécifie le chemin d’accès d’un fichier de configuration de session (. PSSC), tel que celui créé par l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-213">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="bcf37-214">Si vous omettez le chemin d'accès, la valeur par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="bcf37-214">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="bcf37-215">Pour plus d’informations sur la modification d’un fichier de configuration de session, consultez la rubrique d’aide de l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-215">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="bcf37-216">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-217">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="bcf37-217">-PSVersion</span></span>

<span data-ttu-id="bcf37-218">Spécifie la version de PowerShell dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-218">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="bcf37-219">La valeur de ce paramètre est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-219">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="bcf37-220">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-220">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-221">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bcf37-221">-RunAsCredential</span></span>

<span data-ttu-id="bcf37-222">Spécifie des informations d’identification pour les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-222">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="bcf37-223">Par défaut, les commandes s'exécutent avec les autorisations de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="bcf37-223">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="bcf37-224">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-224">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-225">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="bcf37-225">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="bcf37-226">Spécifie une chaîne SDDL (Security Descriptor Definition Language) différente pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-226">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="bcf37-227">Cette chaîne détermine les autorisations qui sont nécessaires pour utiliser la nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-227">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="bcf37-228">Pour utiliser une configuration de session dans une session, les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-228">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="bcf37-229">Pour utiliser le descripteur de sécurité par défaut pour la configuration, entrez une chaîne vide ("") ou une valeur `$Null` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-229">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="bcf37-230">La valeur par défaut est le SDDL racine dans le WSMan:.</span><span class="sxs-lookup"><span data-stu-id="bcf37-230">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="bcf37-231">Si le descripteur de sécurité est complexe, envisagez d’utiliser le paramètre **ShowSecurityDescriptorUI** au lieu de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="bcf37-231">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="bcf37-232">Vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="bcf37-232">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="bcf37-233">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="bcf37-233">-SessionTypeOption</span></span>

<span data-ttu-id="bcf37-234">Spécifie les options spécifiques au type pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-234">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="bcf37-235">Entrez un objet d’options de type de session, tel que l’objet **PSWorkflowExecutionOption** retourné par l’applet de commande `New-PSWorkflowExecutionOption` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-235">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="bcf37-236">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-236">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="bcf37-237">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-237">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="bcf37-238">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-238">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="bcf37-239">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-239">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-240">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="bcf37-240">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="bcf37-241">Indique que cette applet de commande est une feuille de propriétés qui vous aide à créer un nouveau SDDL pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-241">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="bcf37-242">La feuille de propriétés s’affiche après l’exécution de la `Set-PSSessionConfiguration` commande, puis le redémarrage du service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-242">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="bcf37-243">Lorsque vous définissez des autorisations sur la configuration, n’oubliez pas que les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour utiliser la configuration de session dans une session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-243">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="bcf37-244">Vous ne pouvez pas utiliser le paramètre **SecurityDescriptorSDDL** et ce paramètre dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="bcf37-244">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="bcf37-245">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="bcf37-245">-StartupScript</span></span>

<span data-ttu-id="bcf37-246">Spécifie le script de démarrage pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-246">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="bcf37-247">Entrez le chemin d’accès complet d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcf37-247">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="bcf37-248">Le script spécifié est exécuté dans la nouvelle session qui utilise la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-248">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="bcf37-249">Pour supprimer un script de démarrage d’une configuration de session, entrez une chaîne vide ("") ou une valeur `$Null` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-249">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="bcf37-250">Vous pouvez utiliser un script de démarrage pour configurer davantage la session utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bcf37-250">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="bcf37-251">Si le script génère une erreur, même une erreur sans fin d’exécution, la session n’est pas créée et la `New-PSSession` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="bcf37-251">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="bcf37-252">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="bcf37-252">-ThreadApartmentState</span></span>

<span data-ttu-id="bcf37-253">Spécifie le paramètre d’état de cloisonnement pour les threads dans la session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-253">Specifies the apartment state setting for the threads in the session.</span></span>
<span data-ttu-id="bcf37-254">Les valeurs acceptables pour ce paramètre sont les suivantes : STA, MTA et Unknown.</span><span class="sxs-lookup"><span data-stu-id="bcf37-254">The acceptable values for this parameter are: STA, MTA, and Unknown.</span></span>
<span data-ttu-id="bcf37-255">La valeur par défaut est Unknown.</span><span class="sxs-lookup"><span data-stu-id="bcf37-255">The default value is Unknown.</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:
Accepted values: STA, MTA, Unknown

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf37-256">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="bcf37-256">-ThreadOptions</span></span>

<span data-ttu-id="bcf37-257">Spécifie le paramètre des options de thread dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcf37-257">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="bcf37-258">Ce paramètre définit comment les threads sont créés et utilisés quand une commande est exécutée dans la session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-258">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="bcf37-259">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="bcf37-259">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bcf37-260">Default</span><span class="sxs-lookup"><span data-stu-id="bcf37-260">Default</span></span>
- <span data-ttu-id="bcf37-261">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="bcf37-261">ReuseThread</span></span>
- <span data-ttu-id="bcf37-262">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="bcf37-262">UseCurrentThread</span></span>
- <span data-ttu-id="bcf37-263">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="bcf37-263">UseNewThread</span></span>

<span data-ttu-id="bcf37-264">La valeur par défaut est **UseCurrentThread** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-264">The default value is **UseCurrentThread** .</span></span>

<span data-ttu-id="bcf37-265">Pour plus d’informations, consultez [énumération PSThreadOptions](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span><span class="sxs-lookup"><span data-stu-id="bcf37-265">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

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

### <span data-ttu-id="bcf37-266">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="bcf37-266">-TransportOption</span></span>

<span data-ttu-id="bcf37-267">Spécifie les options de transport pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-267">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="bcf37-268">Entrez un objet d’options de transport, tel que l’objet **WSManConfigurationOption** retourné par l’applet de commande `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-268">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="bcf37-269">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-269">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="bcf37-270">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-270">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="bcf37-271">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-271">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="bcf37-272">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-272">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-273">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="bcf37-273">-UseSharedProcess</span></span>

<span data-ttu-id="bcf37-274">Utilisez un seul processus pour héberger toutes les sessions qui sont démarrées par le même utilisateur et utiliser la même configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-274">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="bcf37-275">Par défaut, chaque session est hébergée dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="bcf37-275">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="bcf37-276">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-276">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bcf37-277">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bcf37-277">-Confirm</span></span>

<span data-ttu-id="bcf37-278">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bcf37-278">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bcf37-279">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bcf37-279">-WhatIf</span></span>

<span data-ttu-id="bcf37-280">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bcf37-280">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bcf37-281">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="bcf37-281">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bcf37-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bcf37-282">CommonParameters</span></span>

<span data-ttu-id="bcf37-283">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bcf37-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bcf37-284">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bcf37-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bcf37-285">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bcf37-285">INPUTS</span></span>

### <span data-ttu-id="bcf37-286">Aucun</span><span class="sxs-lookup"><span data-stu-id="bcf37-286">None</span></span>

<span data-ttu-id="bcf37-287">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bcf37-287">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bcf37-288">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bcf37-288">OUTPUTS</span></span>

### <span data-ttu-id="bcf37-289">Microsoft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="bcf37-289">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="bcf37-290">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bcf37-290">NOTES</span></span>

<span data-ttu-id="bcf37-291">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="bcf37-291">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="bcf37-292">L' `Set-PSSessionConfiguration` applet de commande ne modifie pas le nom de la configuration et le fournisseur **WSMan** ne prend pas en charge l’applet de commande `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="bcf37-292">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="bcf37-293">Pour modifier le nom d’une configuration de session, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration, puis utilisez l' `Register-PSSessionConfiguration` applet de commande pour créer et inscrire une nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-293">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="bcf37-294">Vous pouvez utiliser l' `Set-PSSessionConfiguration` applet de commande pour modifier les configurations de session Microsoft. PowerShell et Microsoft. powershell32 par défaut.</span><span class="sxs-lookup"><span data-stu-id="bcf37-294">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="bcf37-295">Elles ne sont pas protégées.</span><span class="sxs-lookup"><span data-stu-id="bcf37-295">They are not protected.</span></span> <span data-ttu-id="bcf37-296">Pour revenir à la version d’origine d’une configuration de session par défaut, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration de session par défaut, puis utilisez l' `Enable-PSRemoting` applet de commande pour la restaurer.</span><span class="sxs-lookup"><span data-stu-id="bcf37-296">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="bcf37-297">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="bcf37-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="bcf37-298">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="bcf37-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="bcf37-299">Vous pouvez utiliser les commandes du lecteur WSMan pour modifier les propriétés des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="bcf37-299">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="bcf37-300">Toutefois, vous ne pouvez pas utiliser le lecteur WSMan : dans PowerShell 2,0 pour modifier les propriétés de configuration de session introduites dans PowerShell 3,0, telles que **OutputBufferingMode** .</span><span class="sxs-lookup"><span data-stu-id="bcf37-300">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="bcf37-301">Les commandes Windows PowerShell 2.0 ne génèrent pas d'erreur, mais elles sont inefficaces.</span><span class="sxs-lookup"><span data-stu-id="bcf37-301">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="bcf37-302">Pour modifier les propriétés introduites dans PowerShell 3,0, utilisez le lecteur WSMan : dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf37-302">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="bcf37-303">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bcf37-303">RELATED LINKS</span></span>

[<span data-ttu-id="bcf37-304">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-304">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="bcf37-305">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-305">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="bcf37-306">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-306">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="bcf37-307">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bcf37-307">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="bcf37-308">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="bcf37-308">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="bcf37-309">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="bcf37-309">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="bcf37-310">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="bcf37-310">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="bcf37-311">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-311">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="bcf37-312">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-312">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="bcf37-313">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bcf37-313">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="bcf37-314">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcf37-314">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="bcf37-315">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="bcf37-315">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="bcf37-316">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="bcf37-316">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="bcf37-317">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="bcf37-317">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
