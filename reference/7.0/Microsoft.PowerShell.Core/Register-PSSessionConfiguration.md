---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: c0dd413e315d5905467d5591ed64eb971cbb0dbe
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201489"
---
# <span data-ttu-id="06d95-103">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d95-103">Register-PSSessionConfiguration</span></span>

## <span data-ttu-id="06d95-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="06d95-104">SYNOPSIS</span></span>
<span data-ttu-id="06d95-105">Crée et enregistre une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-105">Creates and registers a new session configuration.</span></span>

## <span data-ttu-id="06d95-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="06d95-106">SYNTAX</span></span>

### <span data-ttu-id="06d95-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="06d95-107">NameParameterSet (Default)</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06d95-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="06d95-108">AssemblyNameParameterSet</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06d95-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="06d95-109">SessionConfigurationFile</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="06d95-110">Description</span><span class="sxs-lookup"><span data-stu-id="06d95-110">DESCRIPTION</span></span>

<span data-ttu-id="06d95-111">L' `Register-PSSessionConfiguration` applet de commande crée et enregistre une nouvelle configuration de session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="06d95-111">The `Register-PSSessionConfiguration` cmdlet creates and registers a new session configuration on the local computer.</span></span> <span data-ttu-id="06d95-112">Il s’agit d’une applet de commande avancée que vous pouvez utiliser pour créer des sessions personnalisées pour les utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="06d95-112">This is an advanced cmdlet that you can use to create custom sessions for remote users.</span></span>

<span data-ttu-id="06d95-113">Chaque session PowerShell ( **PSSession** ) utilise une configuration de session, également appelée point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="06d95-113">Every PowerShell session ( **PSSession** ) uses a session configuration, also known as an endpoint.</span></span>
<span data-ttu-id="06d95-114">Quand les utilisateurs créent une session qui se connecte à l’ordinateur, ils peuvent sélectionner une configuration de session ou utiliser la configuration de session par défaut qui est inscrite lorsque vous activez la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06d95-114">When users create a session that connects to the computer, they can select a session configuration or use the default session configuration that is registered when you enable PowerShell remoting.</span></span>
<span data-ttu-id="06d95-115">Les utilisateurs peuvent également définir la variable de préférence $PSSessionConfigurationName, qui spécifie une configuration par défaut pour les sessions à distance créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="06d95-115">Users can also set the $PSSessionConfigurationName preference variable, which specifies a default configuration for remote sessions created in the current session.</span></span>

<span data-ttu-id="06d95-116">La configuration de session définit l'environnement pour la session à distance.</span><span class="sxs-lookup"><span data-stu-id="06d95-116">The session configuration defines the environment for the remote session.</span></span> <span data-ttu-id="06d95-117">Cette configuration peut déterminer les commandes et les éléments de langage qui sont disponibles dans la session. Elle peut aussi inclure des paramètres qui protègent l'ordinateur, tels que ceux qui limitent la quantité de données que la session peut recevoir à distance dans un objet ou une commande unique.</span><span class="sxs-lookup"><span data-stu-id="06d95-117">The configuration can determine which commands and language elements are available in the session, and it can include settings that protect the computer, such as those that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="06d95-118">Le descripteur de sécurité de la configuration de session détermine quels utilisateurs sont autorisés à utiliser la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-118">The security descriptor of the session configuration determines which users have permission to use the session configuration.</span></span>

<span data-ttu-id="06d95-119">Vous pouvez définir les éléments de configuration en utilisant un assembly qui implémente une nouvelle classe de configuration, ainsi qu'un script qui s'exécute dans la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-119">You can define the elements of configuration by using an assembly that implements a new configuration class and by using a script that runs in the session.</span></span> <span data-ttu-id="06d95-120">À compter de PowerShell 3,0, vous pouvez également utiliser un fichier de configuration de session pour définir la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-120">Beginning in PowerShell 3.0, you can also use a session configuration file to define the session configuration.</span></span>

<span data-ttu-id="06d95-121">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="06d95-121">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>
<span data-ttu-id="06d95-122">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="06d95-122">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

## <span data-ttu-id="06d95-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="06d95-123">EXAMPLES</span></span>

### <span data-ttu-id="06d95-124">Exemple 1 : inscrire une configuration de session NewShell</span><span class="sxs-lookup"><span data-stu-id="06d95-124">Example 1: Register a NewShell session configuration</span></span>

<span data-ttu-id="06d95-125">Dans cet exemple, nous enregistrons la configuration de session **NewShell** .</span><span class="sxs-lookup"><span data-stu-id="06d95-125">In this example, we register the **NewShell** session configuration.</span></span> <span data-ttu-id="06d95-126">Les paramètres **AssemblyName** et **ApplicationBase** spécifient l’emplacement du fichier **MyShell.dll** , qui spécifie les applets de commande et les fournisseurs dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-126">The **AssemblyName** and **ApplicationBase** parameters specify the location of the **MyShell.dll** file, which specifies the cmdlets and providers in the session configuration.</span></span> <span data-ttu-id="06d95-127">Le paramètre **ConfigurationTypeName** spécifie la classe de configuration à utiliser à partir de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="06d95-127">The **ConfigurationTypeName** parameter specifies the configuration class to use from the assembly.</span></span>

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

<span data-ttu-id="06d95-128">Pour utiliser cette configuration, tapez `New-PSSession -ConfigurationName newshell` .</span><span class="sxs-lookup"><span data-stu-id="06d95-128">To use this configuration, type `New-PSSession -ConfigurationName newshell`.</span></span>

### <span data-ttu-id="06d95-129">Exemple 2 : inscrire une configuration de session MaintenanceShell</span><span class="sxs-lookup"><span data-stu-id="06d95-129">Example 2: Register a MaintenanceShell session configuration</span></span>

<span data-ttu-id="06d95-130">Cet exemple enregistre la configuration de session **MaintenanceShell** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="06d95-130">This example registers the **MaintenanceShell** session configuration on the local computer.</span></span> <span data-ttu-id="06d95-131">Le paramètre **StartupScript** spécifie le `Maintenance.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="06d95-131">The **StartupScript** parameter specifies the `Maintenance.ps1` script.</span></span>

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

<span data-ttu-id="06d95-132">Quand un utilisateur utilise une `New-PSSession` commande et sélectionne la configuration **MaintenanceShell** , le `Maintenance.ps1` script s’exécute dans la nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="06d95-132">When a user uses a `New-PSSession` command and selects the **MaintenanceShell** configuration, the `Maintenance.ps1` script runs in the new session.</span></span> <span data-ttu-id="06d95-133">Le script peut configurer la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-133">The script can configure the session.</span></span> <span data-ttu-id="06d95-134">Cela comprend l’importation de modules et la définition de la stratégie d’exécution pour la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-134">This includes importing modules and setting the execution policy for the session.</span></span> <span data-ttu-id="06d95-135">Si le script génère des erreurs, y compris des erreurs sans fin d’exécution, la `New-PSSession` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="06d95-135">If the script generates any errors, including non-terminating errors, the `New-PSSession` command fails.</span></span>

### <span data-ttu-id="06d95-136">Exemple 3 : inscrire une configuration de session</span><span class="sxs-lookup"><span data-stu-id="06d95-136">Example 3: Register a session configuration</span></span>

<span data-ttu-id="06d95-137">Cet exemple enregistre la configuration de session **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="06d95-137">This example registers the **AdminShell** session configuration.</span></span>

<span data-ttu-id="06d95-138">La `$sessionParams` variable est une Hashtable contenant toutes les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="06d95-138">The `$sessionParams` variable is a hashtable containing all the parameter values.</span></span> <span data-ttu-id="06d95-139">Ce Hashtable est passé à l’applet de commande à l’aide de la projection PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06d95-139">This hashtable is passed to the cmdlet using PowerShell splatting.</span></span> <span data-ttu-id="06d95-140">La `Register-PSSessionConfiguration` commande utilise le paramètre **SecurityDescritorSDDL** pour spécifier le SDDL dans la valeur de la `$sddl` variable et le paramètre **MaximumReceivedObjectSizeMB** pour augmenter la limite de taille d’objet.</span><span class="sxs-lookup"><span data-stu-id="06d95-140">The `Register-PSSessionConfiguration` command uses the **SecurityDescritorSDDL** parameter to specify the SDDL in the value of the `$sddl` variable and the **MaximumReceivedObjectSizeMB** parameter to increase the object size limit.</span></span> <span data-ttu-id="06d95-141">Elle utilise également le paramètre **StartupScript** pour spécifier un script qui configure la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-141">It also uses the **StartupScript** parameter to specify a script that configures the session.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### <span data-ttu-id="06d95-142">Exemple 4 : retourner un élément de conteneur de configuration</span><span class="sxs-lookup"><span data-stu-id="06d95-142">Example 4: Return a configuration container element</span></span>

<span data-ttu-id="06d95-143">Cet exemple montre comment inscrire la configuration **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="06d95-143">This example shows how to register the **MaintenanceShell** configuration.</span></span>
<span data-ttu-id="06d95-144">`Register-PSSessionConfiguration` retourne un objet **WSManConfigContainerElement** stocké dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="06d95-144">`Register-PSSessionConfiguration` returns a **WSManConfigContainerElement** object stored in the `$s` variable.</span></span> <span data-ttu-id="06d95-145">`Format-List` affiche toutes les propriétés de l’objet retourné.</span><span class="sxs-lookup"><span data-stu-id="06d95-145">`Format-List` displays all the properties of the returned object.</span></span> <span data-ttu-id="06d95-146">La propriété **PSPath** indique que l'objet est stocké dans un répertoire du lecteur WSMan:.</span><span class="sxs-lookup"><span data-stu-id="06d95-146">The **PSPath** property shows that the object is stored in a directory of the WSMan: drive.</span></span> <span data-ttu-id="06d95-147">`Get-ChildItem` (alias `dir` ) affiche les éléments dans le `WSMan:\LocalHost\PlugIn` chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="06d95-147">`Get-ChildItem` (alias `dir`) displays the items in the `WSMan:\LocalHost\PlugIn` path.</span></span> <span data-ttu-id="06d95-148">Celles-ci incluent la nouvelle configuration **MaintenanceShell** et les deux configurations par défaut fournies avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06d95-148">These include the new **MaintenanceShell** configuration and the two default configurations that come with PowerShell.</span></span>

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### <span data-ttu-id="06d95-149">Exemple 5 : inscrire une configuration de session à l’aide d’un script de démarrage</span><span class="sxs-lookup"><span data-stu-id="06d95-149">Example 5: Register a session configuration with a startup script</span></span>

<span data-ttu-id="06d95-150">Dans cet exemple, nous créons et enregistrons la configuration de session **WithProfile** .</span><span class="sxs-lookup"><span data-stu-id="06d95-150">In this example we create and register the **WithProfile** session configuration.</span></span> <span data-ttu-id="06d95-151">Le paramètre **StartupScript** indique à PowerShell d’exécuter le script spécifié pour toute session qui utilise la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-151">The **StartupScript** parameter directs PowerShell to run the specified script for any session that uses the session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

<span data-ttu-id="06d95-152">Le script contient une commande unique qui utilise l'appel de source de type « dot sourcing » pour exécuter le profil **CurrentUserAllHosts** de l'utilisateur dans l'étendue actuelle de la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-152">The script contains a single command that uses dot sourcing to run the user's **CurrentUserAllHosts** profile in the current scope of the session.</span></span>

<span data-ttu-id="06d95-153">Pour plus d'informations sur les profils, consultez [about_Profiles](./About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="06d95-153">For more information about profiles, see [about_Profiles](./About/about_Profiles.md).</span></span> <span data-ttu-id="06d95-154">Pour plus d'informations sur l'appel de source de type « dot sourcing », consultez [about_Scopes](./About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="06d95-154">For more information about dot sourcing, see [about_Scopes](./About/about_Scopes.md).</span></span>

## <span data-ttu-id="06d95-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="06d95-155">PARAMETERS</span></span>

### <span data-ttu-id="06d95-156">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="06d95-156">-AccessMode</span></span>

<span data-ttu-id="06d95-157">Active et désactive la configuration de session et détermine si elle peut être utilisée pour les sessions locales ou distantes sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06d95-157">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="06d95-158">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="06d95-158">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="06d95-159">Désactivé.</span><span class="sxs-lookup"><span data-stu-id="06d95-159">Disabled.</span></span> <span data-ttu-id="06d95-160">désactive la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-160">Disables the session configuration.</span></span> <span data-ttu-id="06d95-161">Elle ne peut pas être utilisée pour l'accès local ou distant à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06d95-161">It cannot be used for remote or local access to the computer.</span></span>
- <span data-ttu-id="06d95-162">Local.</span><span class="sxs-lookup"><span data-stu-id="06d95-162">Local.</span></span> <span data-ttu-id="06d95-163">Permet aux utilisateurs de l’ordinateur local d’utiliser la configuration de session pour créer une session de bouclage locale sur le même ordinateur, mais refuse l’accès aux utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="06d95-163">Allows users of the local computer to use the session configuration to create a local loopback session on the same computer, but denies access to remote users.</span></span>
- <span data-ttu-id="06d95-164">Distant.</span><span class="sxs-lookup"><span data-stu-id="06d95-164">Remote.</span></span> <span data-ttu-id="06d95-165">permet aux utilisateurs locaux et distants d'utiliser la configuration de session pour créer des sessions et exécuter des commandes sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06d95-165">Allows local and remote users to use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="06d95-166">La valeur par défaut est Remote.</span><span class="sxs-lookup"><span data-stu-id="06d95-166">The default value is Remote.</span></span>

<span data-ttu-id="06d95-167">D’autres applets de commande peuvent remplacer la valeur de ce paramètre ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="06d95-167">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="06d95-168">Par exemple, l' `Enable-PSRemoting` applet de commande permet l’accès à distance à toutes les configurations de session, l’applet de commande `Enable-PSSessionConfiguration` active les configurations de session, et l' `Disable-PSRemoting` applet de commande empêche l’accès à distance à toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-168">For example, the `Enable-PSRemoting` cmdlet allows for remote access to all session configurations, the `Enable-PSSessionConfiguration` cmdlet enables session configurations, and the `Disable-PSRemoting` cmdlet prevents remote access to all session configurations.</span></span>

<span data-ttu-id="06d95-169">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-169">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-170">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="06d95-170">-ApplicationBase</span></span>

<span data-ttu-id="06d95-171">Spécifie le chemin d’accès du fichier d’assembly ( \* . dll) qui est spécifié dans la valeur du paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="06d95-171">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span> <span data-ttu-id="06d95-172">Utilisez ce paramètre quand la valeur du paramètre **AssemblyName** n'inclut pas de chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="06d95-172">Use this parameter when the value of the **AssemblyName** parameter does not include a path.</span></span> <span data-ttu-id="06d95-173">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="06d95-173">The default is the current directory.</span></span>

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

### <span data-ttu-id="06d95-174">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="06d95-174">-AssemblyName</span></span>

<span data-ttu-id="06d95-175">Spécifie le nom d’un fichier d’assembly ( \* . dll) dans lequel le type de configuration est défini.</span><span class="sxs-lookup"><span data-stu-id="06d95-175">Specifies the name of an assembly file (\*.dll) in which the configuration type is defined.</span></span> <span data-ttu-id="06d95-176">Vous pouvez spécifier le chemin d’accès du fichier. dll dans ce paramètre ou dans la valeur du paramètre **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="06d95-176">You can specify the path of the .dll in this parameter or in the value of the **ApplicationBase** parameter.</span></span>

<span data-ttu-id="06d95-177">Ce paramètre est obligatoire lorsque vous spécifiez le paramètre **ConfigurationTypeName** .</span><span class="sxs-lookup"><span data-stu-id="06d95-177">This parameter is required when you specify the **ConfigurationTypeName** parameter.</span></span>

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

### <span data-ttu-id="06d95-178">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="06d95-178">-ConfigurationTypeName</span></span>

<span data-ttu-id="06d95-179">Spécifie le nom qualifié complet du type Microsoft .NET Framework qui est utilisé pour cette configuration.</span><span class="sxs-lookup"><span data-stu-id="06d95-179">Specifies the fully qualified name of the Microsoft .NET Framework type that is used for this configuration.</span></span> <span data-ttu-id="06d95-180">Le type que vous spécifiez doit implémenter la classe **System.Management.Automation.Remoting.PSSessionConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="06d95-180">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="06d95-181">Pour spécifier le fichier d’assembly ( \* . dll) qui implémente le type de configuration, spécifiez les paramètres **AssemblyName** et **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="06d95-181">To specify the assembly file (\*.dll) that implements the configuration type, specify the **AssemblyName** and **ApplicationBase** parameters.</span></span>

<span data-ttu-id="06d95-182">La création d’un type vous permet de contrôler davantage d’aspects de la configuration de session, tels que l’exposition ou le masquage de certains paramètres des applets de commande, ou la définition de limites de taille d’objet et de taille des données que les utilisateurs ne peuvent pas remplacer.</span><span class="sxs-lookup"><span data-stu-id="06d95-182">Creating a type lets you control more aspects of the session configuration, such as exposing or hiding certain parameters of cmdlets, or setting data size and object size limits that users cannot override.</span></span>

<span data-ttu-id="06d95-183">Si vous omettez ce paramètre, la classe **DefaultRemotePowerShellConfiguration** est utilisée pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-183">If you omit this parameter, the **DefaultRemotePowerShellConfiguration** class is used for the session configuration.</span></span>

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

### <span data-ttu-id="06d95-184">-Force</span><span class="sxs-lookup"><span data-stu-id="06d95-184">-Force</span></span>

<span data-ttu-id="06d95-185">Supprime toutes les invites utilisateur et redémarre le service **WinRM** sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="06d95-185">Suppresses all user prompts and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="06d95-186">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="06d95-186">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="06d95-187">Pour éviter un redémarrage et supprimer l’invite de redémarrage, spécifiez le paramètre **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="06d95-187">To prevent a restart and suppress the restart prompt, specify the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="06d95-188">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="06d95-188">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="06d95-189">Spécifie une limite pour la quantité de données qui peut être envoyée à cet ordinateur dans une commande à distance unique.</span><span class="sxs-lookup"><span data-stu-id="06d95-189">Specifies a limit for the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="06d95-190">Entrez la taille des données en mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="06d95-190">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="06d95-191">La valeur par défaut est 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="06d95-191">The default is 50 MB.</span></span>

<span data-ttu-id="06d95-192">Si une limite de taille de données est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite figurant dans le type de configuration est utilisée et la valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="06d95-192">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="06d95-193">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="06d95-193">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="06d95-194">Spécifie une limite pour la quantité de données qui peuvent être envoyées à cet ordinateur dans un objet unique.</span><span class="sxs-lookup"><span data-stu-id="06d95-194">Specifies a limit for the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="06d95-195">Entrez la taille des données en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="06d95-195">Enter the data size in megabytes.</span></span> <span data-ttu-id="06d95-196">La valeur par défaut est 10 Mo.</span><span class="sxs-lookup"><span data-stu-id="06d95-196">The default is 10 MB.</span></span>

<span data-ttu-id="06d95-197">Si une limite de taille d'objet est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite figurant dans le type de configuration est utilisée et la valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="06d95-197">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="06d95-198">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="06d95-198">-ModulesToImport</span></span>

<span data-ttu-id="06d95-199">Spécifie les modules qui sont importés automatiquement dans des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-199">Specifies the modules that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="06d95-200">Par défaut, seul **Microsoft. PowerShell. Core** est importé dans les sessions.</span><span class="sxs-lookup"><span data-stu-id="06d95-200">By default, only **Microsoft.PowerShell.Core** is imported into sessions.</span></span> <span data-ttu-id="06d95-201">À moins que les applets de commande ne soient exclues, vous pouvez utiliser `Import-Module` pour ajouter des modules à la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-201">Unless the cmdlets are excluded, you can use `Import-Module` to add modules to the session.</span></span>

<span data-ttu-id="06d95-202">Les modules spécifiés dans cette valeur de paramètre sont importés en compléments dans les modules spécifiés par le paramètre **SessionType** et ceux répertoriés dans la clé **ModulesToImport** du fichier de configuration de session ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="06d95-202">The modules specified in this parameter value are imported in additions to modules that are specified by the **SessionType** parameter and those listed in the **ModulesToImport** key in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="06d95-203">Toutefois, les paramètres dans le fichier de configuration de session peuvent masquer les commandes exportées par les modules ou empêcher les utilisateurs de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="06d95-203">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="06d95-204">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-204">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-205">-Name</span><span class="sxs-lookup"><span data-stu-id="06d95-205">-Name</span></span>

<span data-ttu-id="06d95-206">Spécifie un nom pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-206">Specifies a name for the session configuration.</span></span> <span data-ttu-id="06d95-207">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06d95-207">This parameter is required.</span></span>

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

### <span data-ttu-id="06d95-208">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="06d95-208">-NoServiceRestart</span></span>

<span data-ttu-id="06d95-209">Ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="06d95-209">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="06d95-210">Par défaut, lorsque vous exécutez une `Register-PSSessionConfiguration` commande, vous êtes invité à redémarrer le service **WinRM** pour que la nouvelle configuration de session soit effective.</span><span class="sxs-lookup"><span data-stu-id="06d95-210">By default, when you run a `Register-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="06d95-211">Tant que le service **WinRM** n’est pas redémarré, la nouvelle configuration de session n’est pas effective.</span><span class="sxs-lookup"><span data-stu-id="06d95-211">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="06d95-212">Pour redémarrer le service **WinRM** sans demander confirmation, spécifiez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="06d95-212">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="06d95-213">Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d95-213">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="06d95-214">-Path</span><span class="sxs-lookup"><span data-stu-id="06d95-214">-Path</span></span>

<span data-ttu-id="06d95-215">Spécifie le chemin d’accès et le nom de fichier d’un fichier de configuration de session (. PSSC), tel que celui créé par `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="06d95-215">Specifies the path and filename of a session configuration file (.pssc), such as one created by `New-PSSessionConfigurationFile`.</span></span> <span data-ttu-id="06d95-216">Si vous omettez le chemin d'accès, la valeur par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="06d95-216">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="06d95-217">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-218">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="06d95-218">-ProcessorArchitecture</span></span>

<span data-ttu-id="06d95-219">Détermine si une version 32 bits ou 64 bits du processus PowerShell est démarrée dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-219">Determines whether a 32-bit or 64-bit version of the PowerShell process is started in sessions that use this session configuration.</span></span> <span data-ttu-id="06d95-220">Les valeurs acceptables pour ce paramètre sont : x86 (32 bits) et AMD64 (64 bits).</span><span class="sxs-lookup"><span data-stu-id="06d95-220">The acceptable values for this parameter are: x86 (32-bit) and AMD64 (64-bit).</span></span> <span data-ttu-id="06d95-221">La valeur par défaut est déterminée par l'architecture de processeur de l'ordinateur qui héberge la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-221">The default value is determined by the processor architecture of the computer that hosts the session configuration.</span></span>

<span data-ttu-id="06d95-222">Vous pouvez utiliser ce paramètre pour créer une session 32 bits sur un ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="06d95-222">You can use this parameter to create a 32-bit session on a 64-bit computer.</span></span> <span data-ttu-id="06d95-223">Échec des tentatives de création d'un processus 64 bits sur un ordinateur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="06d95-223">Attempts to create a 64-bit process on a 32-bit computer fail.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="06d95-224">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="06d95-224">-PSVersion</span></span>

<span data-ttu-id="06d95-225">Spécifie la version de PowerShell dans les sessions qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-225">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="06d95-226">La valeur de ce paramètre est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-226">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="06d95-227">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-228">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="06d95-228">-RunAsCredential</span></span>

<span data-ttu-id="06d95-229">Spécifie des informations d’identification pour les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-229">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="06d95-230">Par défaut, les commandes s'exécutent avec les autorisations de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="06d95-230">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="06d95-231">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-231">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-232">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="06d95-232">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="06d95-233">Spécifie une chaîne SDDL (Security Descriptor Definition Language) pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="06d95-233">Specifies a Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="06d95-234">Cette chaîne détermine les autorisations qui sont nécessaires pour utiliser la nouvelle configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-234">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="06d95-235">Pour utiliser une configuration de session dans une session, les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="06d95-235">To use a session configuration in a session, users must have at least Execute (Invoke) permission for the configuration.</span></span>

<span data-ttu-id="06d95-236">Si le descripteur de sécurité est complexe, envisagez d'utiliser le paramètre **ShowSecurityDescriptorUI** au lieu de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="06d95-236">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this parameter.</span></span> <span data-ttu-id="06d95-237">Vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="06d95-237">You cannot use both parameters in the same command.</span></span>

<span data-ttu-id="06d95-238">Si vous omettez ce paramètre, le SDDL racine pour le service **WinRM** est utilisé pour cette configuration.</span><span class="sxs-lookup"><span data-stu-id="06d95-238">If you omit this parameter, the root SDDL for the **WinRM** service is used for this configuration.</span></span>
<span data-ttu-id="06d95-239">Pour afficher ou modifier la chaîne SDDL racine, utilisez le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="06d95-239">To view or change the root SDDL, use the WSMan provider.</span></span> <span data-ttu-id="06d95-240">Par exemple, `Get-Item wsman:\localhost\service\rootSDDL`.</span><span class="sxs-lookup"><span data-stu-id="06d95-240">For example `Get-Item wsman:\localhost\service\rootSDDL`.</span></span> <span data-ttu-id="06d95-241">Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="06d95-241">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

### <span data-ttu-id="06d95-242">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="06d95-242">-SessionTypeOption</span></span>

<span data-ttu-id="06d95-243">Spécifie les options spécifiques au type pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-243">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="06d95-244">Entrez un objet d’options de type de session, tel que l’objet **PSWorkflowExecutionOption** retourné par l’applet de commande `New-PSWorkflowExecutionOption` .</span><span class="sxs-lookup"><span data-stu-id="06d95-244">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="06d95-245">Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-245">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="06d95-246">Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-246">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="06d95-247">Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-247">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="06d95-248">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-248">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-249">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="06d95-249">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="06d95-250">Indique que cette applet de commande affiche une feuille de propriétés qui vous aide à créer le SDDL pour la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-250">Indicates that this cmdlet displays a property sheet that helps you create the SDDL for the session configuration.</span></span> <span data-ttu-id="06d95-251">La feuille de propriétés s’affiche une fois que vous avez entré la `Register-PSSessionConfiguration` commande, puis redémarré le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="06d95-251">The property sheet appears after you enter the `Register-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="06d95-252">Lorsque vous définissez les autorisations pour la configuration, n’oubliez pas que les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour utiliser la configuration de session dans une session.</span><span class="sxs-lookup"><span data-stu-id="06d95-252">When setting the permissions for the configuration, remember that users must have at least Execute (Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="06d95-253">Vous ne pouvez pas utiliser le paramètre **SecurityDescriptorSDDL** et ce paramètre dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="06d95-253">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="06d95-254">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="06d95-254">-StartupScript</span></span>

<span data-ttu-id="06d95-255">Spécifie le chemin d’accès complet d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06d95-255">Specifies the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="06d95-256">Le script spécifié est exécuté dans la nouvelle session qui utilise la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-256">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="06d95-257">Vous pouvez utiliser le script pour configurer la session en plus.</span><span class="sxs-lookup"><span data-stu-id="06d95-257">You can use the script to additionally configure the session.</span></span> <span data-ttu-id="06d95-258">Si le script génère une erreur, même une erreur sans fin d’exécution, la session n’est pas créée et la `New-PSSession` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="06d95-258">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="06d95-259">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="06d95-259">-ThreadOptions</span></span>

<span data-ttu-id="06d95-260">Spécifie la manière dont les threads sont créés et utilisés lors de l’exécution d’une commande dans la session.</span><span class="sxs-lookup"><span data-stu-id="06d95-260">Specifies how threads are created and used when a command runs in the session.</span></span> <span data-ttu-id="06d95-261">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="06d95-261">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="06d95-262">Default</span><span class="sxs-lookup"><span data-stu-id="06d95-262">Default</span></span>
- <span data-ttu-id="06d95-263">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="06d95-263">ReuseThread</span></span>
- <span data-ttu-id="06d95-264">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="06d95-264">UseCurrentThread</span></span>
- <span data-ttu-id="06d95-265">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="06d95-265">UseNewThread</span></span>

<span data-ttu-id="06d95-266">La valeur par défaut est **UseCurrentThread** .</span><span class="sxs-lookup"><span data-stu-id="06d95-266">The default value is **UseCurrentThread** .</span></span>

<span data-ttu-id="06d95-267">Pour plus d’informations, consultez [énumération PSThreadOptions](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="06d95-267">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span></span>

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

### <span data-ttu-id="06d95-268">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="06d95-268">-TransportOption</span></span>

<span data-ttu-id="06d95-269">Spécifie l’option de transport.</span><span class="sxs-lookup"><span data-stu-id="06d95-269">Specifies the transport option.</span></span>

<span data-ttu-id="06d95-270">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-270">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-271">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="06d95-271">-UseSharedProcess</span></span>

<span data-ttu-id="06d95-272">Utilisez un seul processus pour héberger toutes les sessions qui sont démarrées par le même utilisateur et utiliser la même configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d95-272">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="06d95-273">Par défaut, chaque session est hébergée dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="06d95-273">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="06d95-274">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d95-274">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d95-275">-Confirm</span><span class="sxs-lookup"><span data-stu-id="06d95-275">-Confirm</span></span>

<span data-ttu-id="06d95-276">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d95-276">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="06d95-277">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="06d95-277">-WhatIf</span></span>

<span data-ttu-id="06d95-278">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d95-278">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="06d95-279">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="06d95-279">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="06d95-280">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="06d95-280">-ThreadApartmentState</span></span>

<span data-ttu-id="06d95-281">Spécifie l’état de cloisonnement du module de thread à utiliser.</span><span class="sxs-lookup"><span data-stu-id="06d95-281">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="06d95-282">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="06d95-282">Acceptable values are:</span></span>

- <span data-ttu-id="06d95-283">Unknown</span><span class="sxs-lookup"><span data-stu-id="06d95-283">Unknown</span></span>
- <span data-ttu-id="06d95-284">MTA</span><span class="sxs-lookup"><span data-stu-id="06d95-284">MTA</span></span>
- <span data-ttu-id="06d95-285">STA</span><span class="sxs-lookup"><span data-stu-id="06d95-285">STA</span></span>

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

### <span data-ttu-id="06d95-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06d95-286">CommonParameters</span></span>

<span data-ttu-id="06d95-287">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="06d95-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06d95-288">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="06d95-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06d95-289">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="06d95-289">INPUTS</span></span>

### <span data-ttu-id="06d95-290">Aucun</span><span class="sxs-lookup"><span data-stu-id="06d95-290">None</span></span>

<span data-ttu-id="06d95-291">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d95-291">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="06d95-292">SORTIES</span><span class="sxs-lookup"><span data-stu-id="06d95-292">OUTPUTS</span></span>

### <span data-ttu-id="06d95-293">Microsoft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="06d95-293">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>

## <span data-ttu-id="06d95-294">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="06d95-294">NOTES</span></span>

<span data-ttu-id="06d95-295">Pour exécuter cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="06d95-295">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="06d95-296">Cette applet de commande génère du code XML qui représente une configuration de plug-in WS-Management (Web Services for Management) et envoie le code XML à WS-Management, qui enregistre le plug-in sur l’ordinateur local ( `New-Item wsman:\localhost\plugin` ).</span><span class="sxs-lookup"><span data-stu-id="06d95-296">This cmdlet generates XML that represents a Web Services for Management (WS-Management) plug-in configuration and sends the XML to WS-Management, which registers the plug-in on the local computer (`New-Item wsman:\localhost\plugin`).</span></span>

<span data-ttu-id="06d95-297">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="06d95-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="06d95-298">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="06d95-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="06d95-299">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="06d95-299">RELATED LINKS</span></span>

[<span data-ttu-id="06d95-300">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d95-300">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="06d95-301">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d95-301">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="06d95-302">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d95-302">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="06d95-303">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="06d95-303">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="06d95-304">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d95-304">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="06d95-305">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="06d95-305">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="06d95-306">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d95-306">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="06d95-307">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="06d95-307">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="06d95-308">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="06d95-308">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="06d95-309">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="06d95-309">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
