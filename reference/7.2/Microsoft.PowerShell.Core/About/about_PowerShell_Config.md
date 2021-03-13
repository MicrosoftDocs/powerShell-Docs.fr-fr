---
description: Fichiers de configuration pour PowerShell, remplaçant la configuration du Registre.
Locale: en-US
ms.date: 03/12/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: e6688e91f0cf14ae54a0585ae199f098e98e1146
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412962"
---
# <a name="about-powershell-config"></a><span data-ttu-id="0c0b1-103">À propos de la configuration de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c0b1-103">About PowerShell Config</span></span>

## <a name="short-description"></a><span data-ttu-id="0c0b1-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="0c0b1-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0c0b1-105">Fichiers de configuration pour PowerShell Core, remplaçant la configuration du Registre.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-105">Configuration files for PowerShell Core, replacing Registry configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="0c0b1-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="0c0b1-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="0c0b1-107">Le `powershell.config.json` fichier contient des paramètres de configuration pour PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-107">The `powershell.config.json` file contains configuration settings for PowerShell Core.</span></span> <span data-ttu-id="0c0b1-108">PowerShell charge cette configuration au démarrage.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-108">PowerShell loads this configuration at startup.</span></span> <span data-ttu-id="0c0b1-109">Les paramètres peuvent également être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-109">The settings can also be modified at runtime.</span></span> <span data-ttu-id="0c0b1-110">Auparavant, ces paramètres étaient stockés dans le Registre Windows pour PowerShell, mais ils sont maintenant contenus dans un fichier pour permettre la configuration sur macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-110">Previously, these settings were stored in the Windows Registry for PowerShell, but are now contained in a file to enable configuration on macOS and Linux.</span></span>

> [!WARNING]
> <span data-ttu-id="0c0b1-111">Les clés non reconnues ou les valeurs non valides dans le fichier de configuration sont ignorées en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-111">Unrecognized keys or invalid values in the configuration file are silently ignored.</span></span> <span data-ttu-id="0c0b1-112">Si le `powershell.config.json` fichier contient un JSON non valide, PowerShell ne peut pas démarrer une session interactive.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-112">If the `powershell.config.json` file contains invalid JSON, PowerShell cannot start an interactive session.</span></span> <span data-ttu-id="0c0b1-113">Si cela se produit, vous devez corriger le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-113">If this occurs, you must fix the configuration file.</span></span>

### <a name="allusers-shared-configuration"></a><span data-ttu-id="0c0b1-114">Configuration de AllUsers (partagée)</span><span class="sxs-lookup"><span data-stu-id="0c0b1-114">AllUsers (shared) configuration</span></span>

<span data-ttu-id="0c0b1-115">Un `powershell.config.json` fichier du `$PSHOME` répertoire définit la configuration de toutes les sessions PowerShell Core en cours d’exécution à partir de cette installation de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-115">A `powershell.config.json` file in the `$PSHOME` directory defines the configuration for all PowerShell Core sessions running from that PowerShell Core installation.</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b1-116">L' `$PSHOME` emplacement est défini comme le même répertoire que l’assembly System.Management.Automation.dll en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-116">The `$PSHOME` location is defined as the same directory as the executing System.Management.Automation.dll assembly.</span></span> <span data-ttu-id="0c0b1-117">Cela s’applique également aux instances du kit de développement logiciel (SDK) PowerShell hébergé.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-117">This applies to hosted PowerShell SDK instances as well.</span></span>

### <a name="currentuser-per-user-configurations"></a><span data-ttu-id="0c0b1-118">Configuration CurrentUser (par utilisateur)</span><span class="sxs-lookup"><span data-stu-id="0c0b1-118">CurrentUser (per-user) configurations</span></span>

<span data-ttu-id="0c0b1-119">Vous pouvez également configurer PowerShell par utilisateur en plaçant le fichier dans le répertoire de configuration de l’étendue utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-119">You can also configure PowerShell on a per-user basis by placing the file in the user-scope configuration directory.</span></span> <span data-ttu-id="0c0b1-120">Le répertoire de configuration utilisateur peut être trouvé entre les plateformes à l’aide de la commande `Split-Path $PROFILE.CurrentUserCurrentHost` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-120">The user configuration directory can be found across platforms with the command `Split-Path $PROFILE.CurrentUserCurrentHost`.</span></span>

## <a name="general-configuration-settings"></a><span data-ttu-id="0c0b1-121">Paramètres de configuration généraux</span><span class="sxs-lookup"><span data-stu-id="0c0b1-121">General configuration settings</span></span>

### <a name="executionpolicy"></a><span data-ttu-id="0c0b1-122">ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0c0b1-122">ExecutionPolicy</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c0b1-123">Cette configuration s’applique uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-123">This configuration only applies on Windows platforms.</span></span>

<span data-ttu-id="0c0b1-124">Configure la stratégie d’exécution pour les sessions PowerShell, en déterminant les scripts qui peuvent être exécutés.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-124">Configures the execution policy for PowerShell sessions, determining what scripts can be run.</span></span> <span data-ttu-id="0c0b1-125">Par défaut, PowerShell utilise la stratégie d’exécution existante.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-125">By default, PowerShell uses the existing execution policy.</span></span>

<span data-ttu-id="0c0b1-126">Pour les configurations de AllUsers, cela définit la stratégie d’exécution de **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-126">For AllUsers configurations, this sets the **LocalMachine** execution policy.</span></span>
<span data-ttu-id="0c0b1-127">Pour les configurations CurrentUser, définit la stratégie d’exécution **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-127">For CurrentUser configurations, this sets the **CurrentUser** execution policy.</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b1-128">L' [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) applet de commande modifie ce paramètre dans le fichier de configuration ALLUSERS quand il est appelé avec `-Scope LocalMachine` et modifie ce paramètre dans le fichier de configuration CurrentUser lorsqu’il est appelé avec `-Scope CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-128">The [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet modifies this setting in the AllUsers configuration file when invoked with `-Scope LocalMachine`, and modifies this setting in the CurrentUser configuration file when invoked with `-Scope CurrentUser`.</span></span>

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

<span data-ttu-id="0c0b1-129">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-129">Where:</span></span>

- <span data-ttu-id="0c0b1-130">`<shell-id>` fait référence à l’ID de l’hôte PowerShell actuel.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-130">`<shell-id>` refers to the ID of the current PowerShell host.</span></span> <span data-ttu-id="0c0b1-131">Pour PowerShell Core normal, il s’agit de `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-131">For normal PowerShell Core, this is `Microsoft.PowerShell`.</span></span> <span data-ttu-id="0c0b1-132">Dans une session PowerShell, vous pouvez la découvrir avec `$ShellId` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-132">In any PowerShell session, you can discover it with `$ShellId`.</span></span>
- <span data-ttu-id="0c0b1-133">`<execution-policy>` fait référence à un nom de stratégie d’exécution valide.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-133">`<execution-policy>` refers to a valid execution policy name.</span></span>

<span data-ttu-id="0c0b1-134">L’exemple suivant définit la stratégie d’exécution de PowerShell sur `RemoteSigned` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-134">The following example sets the execution policy of PowerShell to `RemoteSigned`.</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

<span data-ttu-id="0c0b1-135">Dans Windows, les clés de Registre équivalentes se trouvent dans `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` sous `HKEY_LOCAL_MACHINE` et `HKEY_CURRENT_USER` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-135">In Windows, the equivalent registry keys can be found in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`.</span></span>

### <a name="psmodulepath"></a><span data-ttu-id="0c0b1-136">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="0c0b1-136">PSModulePath</span></span>

<span data-ttu-id="0c0b1-137">Remplace les `PSModulePath` paramètres de cette session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-137">Overrides the `PSModulePath` settings for this PowerShell session.</span></span> <span data-ttu-id="0c0b1-138">Si la configuration est pour l’utilisateur actuel, définit le chemin d’accès du module **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-138">If the configuration is for the current user, sets the **CurrentUser** module path.</span></span> <span data-ttu-id="0c0b1-139">Si la configuration est pour tous les utilisateurs, définit le chemin d’accès du module **ALLUSERS** .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-139">If the configuration is for all users, sets the **AllUsers** module path.</span></span>

> [!WARNING]
> <span data-ttu-id="0c0b1-140">La configuration d’un chemin de module **ALLUSERS** ou **CurrentUser** ici ne change pas l’emplacement d’installation d’étendue pour les applets de commande PowerShellGet comme [install-module](/powershell/module/powershellget/install-module).</span><span class="sxs-lookup"><span data-stu-id="0c0b1-140">Configuring an **AllUsers** or **CurrentUser** module path here does not change the scoped installation location for PowerShellGet cmdlets like [Install-Module](/powershell/module/powershellget/install-module).</span></span> <span data-ttu-id="0c0b1-141">Ces applets de commande utilisent toujours les chemins de module _par défaut_ .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-141">These cmdlets always use the _default_ module paths.</span></span>

<span data-ttu-id="0c0b1-142">Si aucune valeur n’est définie, PowerShell utilise la valeur par défaut pour le paramètre de chemin d’accès du module respectif.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-142">If no value is set, PowerShell uses the default value for the respective module path setting.</span></span> <span data-ttu-id="0c0b1-143">Pour plus d’informations sur ces valeurs par défaut, consultez [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath).</span><span class="sxs-lookup"><span data-stu-id="0c0b1-143">For more information about these defaults, see [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath).</span></span>

<span data-ttu-id="0c0b1-144">Ce paramètre permet d’utiliser les variables d’environnement en les incorporant entre des `%` caractères, comme `"%HOME%\Documents\PowerShell\Modules"` , de la même façon que cmd le permet.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-144">This setting allows environment variables to be used by embedding them between `%` characters, like `"%HOME%\Documents\PowerShell\Modules"`, in the same way that CMD allows.</span></span> <span data-ttu-id="0c0b1-145">Cette syntaxe s’applique également à Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-145">This syntax also applies on Linux and macOS.</span></span> <span data-ttu-id="0c0b1-146">Consultez les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-146">See below for examples.</span></span>

```Schema
"PSModulePath": "<ps-module-path>"
```

<span data-ttu-id="0c0b1-147">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-147">Where:</span></span>

- <span data-ttu-id="0c0b1-148">`<ps-module-path>` est le chemin d’accès absolu d’un répertoire de module.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-148">`<ps-module-path>` is the absolute path to a module directory.</span></span> <span data-ttu-id="0c0b1-149">Pour toutes les configurations utilisateur, il s’agit du répertoire du module partagé AllUsers.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-149">For all user configurations, this is the AllUsers shared module directory.</span></span> <span data-ttu-id="0c0b1-150">Pour les configurations utilisateur actuelles, il s’agit du répertoire du module CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-150">For current user configurations, this is CurrentUser module directory.</span></span>

<span data-ttu-id="0c0b1-151">Cet exemple illustre une `PSModulePath` configuration pour un environnement Windows :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-151">This example shows a `PSModulePath` configuration for a Windows environment:</span></span>

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

<span data-ttu-id="0c0b1-152">Cet exemple illustre une `PSModulePath` configuration pour un environnement MacOS ou Linux :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-152">This example shows a `PSModulePath` configuration for a macOS or Linux environment:</span></span>

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

<span data-ttu-id="0c0b1-153">Cet exemple illustre l’incorporation d’une variable d’environnement dans une `PSModulePath` Configuration.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-153">This example shows embedding an environment variable in a `PSModulePath` configuration.</span></span> <span data-ttu-id="0c0b1-154">Notez que l’utilisation de la `HOME` variable d’environnement et du `/` séparateur de répertoires fonctionne sur Windows, MacOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-154">Note that using the `HOME` environment variable and the `/` directory separator, this will work on Windows, macOS and Linux.</span></span>

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

<span data-ttu-id="0c0b1-155">Cet exemple illustre l’incorporation d’une variable d’environnement dans une `PSModulePath` configuration qui fonctionne uniquement sur MacOS et Linux :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-155">This example shows embedding an environment variable in a `PSModulePath` configuration that will only work on macOS and Linux:</span></span>

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> <span data-ttu-id="0c0b1-156">Les variables PowerShell ne peuvent pas être incorporées dans des `PSModulePath` configurations.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-156">PowerShell variables cannot be embedded in `PSModulePath` configurations.</span></span>
> <span data-ttu-id="0c0b1-157">`PSModulePath` les configurations sur Linux et macOS respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-157">`PSModulePath` configurations on Linux and macOS are case-sensitive.</span></span> <span data-ttu-id="0c0b1-158">Une `PSModulePath` configuration doit utiliser des séparateurs de répertoire valides pour la plateforme.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-158">A `PSModulePath` configuration must use valid directory separators for the platform.</span></span> <span data-ttu-id="0c0b1-159">Sur macOS et Linux, cela signifie `/` .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-159">On macOS and Linux, this means `/`.</span></span> <span data-ttu-id="0c0b1-160">Sur Windows, `/` et `\` fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-160">On Windows, both `/` and `\` will work.</span></span>

### <a name="experimentalfeatures"></a><span data-ttu-id="0c0b1-161">ExperimentalFeatures</span><span class="sxs-lookup"><span data-stu-id="0c0b1-161">ExperimentalFeatures</span></span>

<span data-ttu-id="0c0b1-162">Noms des fonctionnalités expérimentales à activer dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-162">The names of the experimental features to enable in PowerShell.</span></span> <span data-ttu-id="0c0b1-163">Par défaut, aucune fonctionnalité expérimentale n’est activée.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-163">By default, no experimental features are enabled.</span></span> <span data-ttu-id="0c0b1-164">La valeur par défaut est un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-164">The default value is an empty array.</span></span>

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

<span data-ttu-id="0c0b1-165">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-165">Where:</span></span>

- <span data-ttu-id="0c0b1-166">`<experimental-feature-name>` nom d’une fonctionnalité expérimentale à activer.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-166">`<experimental-feature-name>` is the name of an experimental feature to enable.</span></span>

<span data-ttu-id="0c0b1-167">L’exemple suivant active les fonctionnalités expérimentales **PSImplicitRemoting** et **PSUseAbbreviationExpansion** lors du démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-167">The following example enables the **PSImplicitRemoting** and **PSUseAbbreviationExpansion** experimental features when PowerShell starts up.</span></span>

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

<span data-ttu-id="0c0b1-168">Pour plus d’informations sur les fonctionnalités expérimentales, consultez [utilisation des fonctionnalités expérimentales](/powershell/scripting/learn/experimental-features).</span><span class="sxs-lookup"><span data-stu-id="0c0b1-168">For more information on experimental features, see [Using experimental features](/powershell/scripting/learn/experimental-features).</span></span>

## <a name="non-windows-logging-configuration"></a><span data-ttu-id="0c0b1-169">Configuration de la journalisation non-Windows</span><span class="sxs-lookup"><span data-stu-id="0c0b1-169">Non-Windows logging configuration</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c0b1-170">Les options de configuration de cette section s’appliquent uniquement à macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-170">The configuration options in this section only apply to macOS and Linux.</span></span>
> <span data-ttu-id="0c0b1-171">La journalisation pour Windows est gérée par le observateur d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-171">Logging for Windows is managed by the Windows Event Viewer.</span></span>

<span data-ttu-id="0c0b1-172">La journalisation de PowerShell sur macOS et Linux peut être configurée dans le fichier de configuration PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-172">PowerShell's logging on macOS and Linux can be configured in the PowerShell configuration file.</span></span> <span data-ttu-id="0c0b1-173">Pour obtenir une description complète de la journalisation PowerShell pour les systèmes non-Windows, consultez [à propos de la journalisation](./about_Logging_Non-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="0c0b1-173">For a full description of PowerShell logging for non-Windows systems, see [About Logging](./about_Logging_Non-Windows.md).</span></span>

### <a name="logidentity"></a><span data-ttu-id="0c0b1-174">LogIdentity</span><span class="sxs-lookup"><span data-stu-id="0c0b1-174">LogIdentity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c0b1-175">Ce paramètre peut uniquement être utilisé dans macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-175">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="0c0b1-176">Définit le nom d’identité utilisé pour écrire dans le journal système.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-176">Sets the identity name used to write to the system log.</span></span> <span data-ttu-id="0c0b1-177">La valeur par défaut est « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="0c0b1-177">The default value is "powershell".</span></span>

```Schema
"LogIdentity": "<log-identity>"
```

<span data-ttu-id="0c0b1-178">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-178">Where:</span></span>

- <span data-ttu-id="0c0b1-179">`<log-identity>` identité de la chaîne que PowerShell doit utiliser pour écrire dans syslog.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-179">`<log-identity>` is the string identity that PowerShell should use for writing to syslog.</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b1-180">Vous souhaiterez peut-être avoir différentes valeurs **LogIdentity** pour chaque instance différente de PowerShell que vous avez installée.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-180">You may want to have different **LogIdentity** values for each different instance of PowerShell you have installed.</span></span>

<span data-ttu-id="0c0b1-181">Dans cet exemple, nous configurons **LogIdentity** pour une version préliminaire de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-181">In this example, we are configuring the **LogIdentity** for a preview release of PowerShell.</span></span>

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a><span data-ttu-id="0c0b1-182">LogLevel</span><span class="sxs-lookup"><span data-stu-id="0c0b1-182">LogLevel</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c0b1-183">Ce paramètre peut uniquement être utilisé dans macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-183">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="0c0b1-184">Spécifie le niveau de gravité minimal auquel PowerShell doit se connecter.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-184">Specifies the minimum severity level at which PowerShell should log.</span></span>

```Schema
"LogLevel": "<log-level>|default"
```

<span data-ttu-id="0c0b1-185">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-185">Where:</span></span>

- <span data-ttu-id="0c0b1-186">`<log-level>` a l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-186">`<log-level>` is one of:</span></span>
  - <span data-ttu-id="0c0b1-187">Toujours</span><span class="sxs-lookup"><span data-stu-id="0c0b1-187">Always</span></span>
  - <span data-ttu-id="0c0b1-188">Critique</span><span class="sxs-lookup"><span data-stu-id="0c0b1-188">Critical</span></span>
  - <span data-ttu-id="0c0b1-189">Error</span><span class="sxs-lookup"><span data-stu-id="0c0b1-189">Error</span></span>
  - <span data-ttu-id="0c0b1-190">Avertissement</span><span class="sxs-lookup"><span data-stu-id="0c0b1-190">Warning</span></span>
  - <span data-ttu-id="0c0b1-191">Informationnel</span><span class="sxs-lookup"><span data-stu-id="0c0b1-191">Informational</span></span>
  - <span data-ttu-id="0c0b1-192">Commentaires</span><span class="sxs-lookup"><span data-stu-id="0c0b1-192">Verbose</span></span>
  - <span data-ttu-id="0c0b1-193">Débogage</span><span class="sxs-lookup"><span data-stu-id="0c0b1-193">Debug</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b1-194">La définition d’un niveau de journalisation active tous les niveaux de journal au-dessus de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-194">Setting a the log level enables all log levels above it.</span></span>

<span data-ttu-id="0c0b1-195">L’affectation de la valeur **par défaut** à ce paramètre est interprétée comme la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-195">Setting this setting to **default** will be interpreted as the default value.</span></span>
<span data-ttu-id="0c0b1-196">La valeur par défaut est **informatif**.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-196">The default value is **Informational**.</span></span>

<span data-ttu-id="0c0b1-197">L’exemple suivant définit la valeur sur **Verbose**.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-197">The following example sets the value to **Verbose**.</span></span>

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a><span data-ttu-id="0c0b1-198">LogChannels</span><span class="sxs-lookup"><span data-stu-id="0c0b1-198">LogChannels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c0b1-199">Ce paramètre peut uniquement être utilisé dans macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-199">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="0c0b1-200">Détermine les canaux de journalisation qui sont activés.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-200">Determines which logging channels are enabled.</span></span>

```Schema
"LogChannels": "<log-channel>,..."
```

<span data-ttu-id="0c0b1-201">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-201">Where:</span></span>

- <span data-ttu-id="0c0b1-202">`<log-channel>` a l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-202">`<log-channel>` is one of:</span></span>
  - <span data-ttu-id="0c0b1-203">Operational : journalise des informations de base sur les activités PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c0b1-203">Operational - logs basic information about PowerShell activities</span></span>
  - <span data-ttu-id="0c0b1-204">Analyse-journalise des informations de diagnostic plus détaillées</span><span class="sxs-lookup"><span data-stu-id="0c0b1-204">Analytic - logs more detailed diagnostic information</span></span>

<span data-ttu-id="0c0b1-205">La valeur par défaut est **Operational**.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-205">The default value is **Operational**.</span></span> <span data-ttu-id="0c0b1-206">Pour activer les deux canaux, incluez les deux valeurs sous la forme d’une seule chaîne séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-206">To enable both channels, include both values as a single comma-separated string.</span></span> <span data-ttu-id="0c0b1-207">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-207">For example:</span></span>

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a><span data-ttu-id="0c0b1-208">LogKeywords</span><span class="sxs-lookup"><span data-stu-id="0c0b1-208">LogKeywords</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c0b1-209">Ce paramètre peut uniquement être utilisé dans macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-209">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="0c0b1-210">Détermine les parties de PowerShell qui sont journalisées.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-210">Determines which parts of PowerShell are logged.</span></span> <span data-ttu-id="0c0b1-211">Par défaut, tous les mots clés de journal sont activés.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-211">By default, all log keywords are enabled.</span></span> <span data-ttu-id="0c0b1-212">Pour activer plusieurs mots clés, répertoriez les valeurs dans une seule chaîne séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-212">To enable multiple keywords, list the values in a single comma-separated string.</span></span>

```Schema
"LogKeywords": "<log-keyword>,..."
```

<span data-ttu-id="0c0b1-213">Où :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-213">Where:</span></span>

- <span data-ttu-id="0c0b1-214">`<log-keyword>` a l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-214">`<log-keyword>` is one of:</span></span>
  - <span data-ttu-id="0c0b1-215">Runspace-gestion de l’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="0c0b1-215">Runspace - runspace management</span></span>
  - <span data-ttu-id="0c0b1-216">Pipeline-opérations de pipeline</span><span class="sxs-lookup"><span data-stu-id="0c0b1-216">Pipeline - pipeline operations</span></span>
  - <span data-ttu-id="0c0b1-217">Gestion du protocole de communication par protocole, par exemple PSRP</span><span class="sxs-lookup"><span data-stu-id="0c0b1-217">Protocol - communication protocol handling, such as PSRP</span></span>
  - <span data-ttu-id="0c0b1-218">Transport-prise en charge de la couche transport, telle que SSH</span><span class="sxs-lookup"><span data-stu-id="0c0b1-218">Transport - transport layer support, such as SSH</span></span>
  - <span data-ttu-id="0c0b1-219">Fonctionnalités hôtes PowerShell hôtes, par exemple l’interaction de la console</span><span class="sxs-lookup"><span data-stu-id="0c0b1-219">Host - PowerShell host functionality, for example console interaction</span></span>
  - <span data-ttu-id="0c0b1-220">Applets de commande-applets de commande builtin PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c0b1-220">Cmdlets -PowerShell builtin cmdlets</span></span>
  - <span data-ttu-id="0c0b1-221">Sérialiseur-logique de sérialisation</span><span class="sxs-lookup"><span data-stu-id="0c0b1-221">Serializer - serialization logic</span></span>
  - <span data-ttu-id="0c0b1-222">Session-État de session PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c0b1-222">Session - PowerShell session state</span></span>
  - <span data-ttu-id="0c0b1-223">ManagedPlugin-plug-in WSMan</span><span class="sxs-lookup"><span data-stu-id="0c0b1-223">ManagedPlugin - WSMan plugin</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b1-224">Il est généralement recommandé de conserver cette valeur non définie, sauf si vous essayez de diagnostiquer un comportement spécifique dans une partie connue de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-224">It is generally advised to leave this value unset unless you are trying to diagnose a specific behavior in a known part of PowerShell.</span></span> <span data-ttu-id="0c0b1-225">La modification de cette valeur réduit uniquement la quantité d’informations journalisées.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-225">Changing this value only decreases the amount of information logged.</span></span>

<span data-ttu-id="0c0b1-226">Cet exemple limite la journalisation aux opérations d’instance d’exécution, à la logique de pipeline et à l’utilisation des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-226">This example limits the logging to runspace operations, pipeline logic, and cmdlet use.</span></span> <span data-ttu-id="0c0b1-227">Tous les autres enregistrements sont omis.</span><span class="sxs-lookup"><span data-stu-id="0c0b1-227">All other logging will be omitted.</span></span>

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a><span data-ttu-id="0c0b1-228">Autres exemples de configurations</span><span class="sxs-lookup"><span data-stu-id="0c0b1-228">More example configurations</span></span>

### <a name="example-windows-configuration"></a><span data-ttu-id="0c0b1-229">Exemple de configuration de Windows</span><span class="sxs-lookup"><span data-stu-id="0c0b1-229">Example Windows configuration</span></span>

<span data-ttu-id="0c0b1-230">Cette configuration a davantage de paramètres définis explicitement :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-230">This configuration has more settings explicitly set:</span></span>

- <span data-ttu-id="0c0b1-231">La stratégie d’exécution pour cette installation de PowerShell est `AllSigned`</span><span class="sxs-lookup"><span data-stu-id="0c0b1-231">Execution policy for this PowerShell installation is `AllSigned`</span></span>
- <span data-ttu-id="0c0b1-232">Le chemin d’accès du module CurrentUser est défini sur un répertoire de module sur un lecteur partagé</span><span class="sxs-lookup"><span data-stu-id="0c0b1-232">The CurrentUser module path is set to a module directory on a shared drive</span></span>
- <span data-ttu-id="0c0b1-233">La `PSImplicitRemotingBatching` fonctionnalité expérimentale est activée</span><span class="sxs-lookup"><span data-stu-id="0c0b1-233">The `PSImplicitRemotingBatching` experimental feature is enabled</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b1-234">Les `ExecutionPolicy` paramètres et ne `PSModulePath` fonctionnent que sur une plate-forme Windows, car le chemin d’accès du module utilise `\` des `;` caractères de séparation et et la stratégie d’exécution n’est pas `Unrestricted` (la seule stratégie autorisée sur les plateformes de type UNIX).</span><span class="sxs-lookup"><span data-stu-id="0c0b1-234">The `ExecutionPolicy` and `PSModulePath` settings here would only work on a Windows platform, since the module path uses `\` and `;` separator characters and the execution policy is not `Unrestricted` (the only policy allowed on UNIX-like platforms).</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a><span data-ttu-id="0c0b1-235">Exemple de configuration non-Windows</span><span class="sxs-lookup"><span data-stu-id="0c0b1-235">Example non-Windows configuration</span></span>

<span data-ttu-id="0c0b1-236">Cette configuration définit un certain nombre d’options qui fonctionnent uniquement dans macOS ou Linux :</span><span class="sxs-lookup"><span data-stu-id="0c0b1-236">This configuration sets a number of options that only work in macOS or Linux:</span></span>

- <span data-ttu-id="0c0b1-237">Le chemin d’accès du module CurrentUser est défini sur un répertoire de module personnalisé dans `$HOME`</span><span class="sxs-lookup"><span data-stu-id="0c0b1-237">The CurrentUser module path is set to a custom module directory in `$HOME`</span></span>
- <span data-ttu-id="0c0b1-238">La fonctionnalité expérimental **PSImplicitRemotingBatching** est activée</span><span class="sxs-lookup"><span data-stu-id="0c0b1-238">The **PSImplicitRemotingBatching** experimental feature is enabled</span></span>
- <span data-ttu-id="0c0b1-239">Le niveau de journalisation PowerShell est défini sur **Verbose**, pour plus d’informations sur la journalisation</span><span class="sxs-lookup"><span data-stu-id="0c0b1-239">The PowerShell logging level is set to **Verbose**, for more logging</span></span>
- <span data-ttu-id="0c0b1-240">Cette installation de PowerShell écrit dans les journaux à l’aide de l’identité **PowerShell d’hébergement** .</span><span class="sxs-lookup"><span data-stu-id="0c0b1-240">This PowerShell installation writes to the logs using the **home-powershell** identity.</span></span>

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a><span data-ttu-id="0c0b1-241">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c0b1-241">See also</span></span>

[<span data-ttu-id="0c0b1-242">À propos des stratégies d’exécution</span><span class="sxs-lookup"><span data-stu-id="0c0b1-242">About Execution Policies</span></span>](./about_Execution_Policies.md)

[<span data-ttu-id="0c0b1-243">À propos des variables automatiques</span><span class="sxs-lookup"><span data-stu-id="0c0b1-243">About Automatic Variables</span></span>](./about_Automatic_Variables.md)
