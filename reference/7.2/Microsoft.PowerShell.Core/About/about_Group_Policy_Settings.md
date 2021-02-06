---
description: Décrit les paramètres de stratégie de groupe pour PowerShell
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 5ca13d22c69213dd8bae57a0dd08587c9c2b1541
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595901"
---
# <a name="about-group-policy-settings"></a><span data-ttu-id="14cc4-103">À propos des paramètres de stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="14cc4-103">About Group Policy Settings</span></span>

## <a name="short-description"></a><span data-ttu-id="14cc4-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="14cc4-104">Short description</span></span>
<span data-ttu-id="14cc4-105">Décrit les paramètres de stratégie de groupe pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="14cc4-105">Describes the Group Policy settings for PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="14cc4-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="14cc4-106">Long description</span></span>

<span data-ttu-id="14cc4-107">PowerShell comprend des paramètres de stratégie de groupe pour vous aider à définir des valeurs de configuration cohérentes pour les ordinateurs Windows dans un environnement d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="14cc4-107">PowerShell includes Group Policy settings to help you define consistent configuration values for Windows computers in an enterprise environment.</span></span>

<span data-ttu-id="14cc4-108">Les paramètres de stratégie de groupe PowerShell se trouvent dans les chemins d’accès de stratégie de groupe suivants :</span><span class="sxs-lookup"><span data-stu-id="14cc4-108">The PowerShell Group Policy settings are in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

<span data-ttu-id="14cc4-109">Les paramètres de stratégie de groupe dans le chemin de configuration utilisateur ont priorité sur les paramètres de stratégie de groupe dans le chemin de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14cc4-109">Group policy settings in the User Configuration path take precedence over Group Policy settings in the Computer Configuration path.</span></span>

<span data-ttu-id="14cc4-110">PowerShell 7 comprend des modèles de stratégie de groupe et un script d’installation dans `$PSHOME`.</span><span class="sxs-lookup"><span data-stu-id="14cc4-110">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="14cc4-111">Les outils de stratégie de groupe utilisent des fichiers de modèles d’administration (`.admx`, `.adml`) pour remplir les paramètres de stratégie dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="14cc4-111">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="14cc4-112">Cela permet aux administrateurs de gérer les paramètres de stratégie basés sur le registre.</span><span class="sxs-lookup"><span data-stu-id="14cc4-112">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="14cc4-113">Le `InstallPSCorePolicyDefinitions.ps1` script installe **PowerShell Core modèles d’administration** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="14cc4-113">The `InstallPSCorePolicyDefinitions.ps1` script installs **PowerShell Core Administrative Templates** on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode       LastWriteTime         Length Name
----       -------------         ------ ----
-a---      2/27/2020 12:38 AM     15861 InstallPSCorePolicyDefinitions.ps1
-a---      2/27/2020 12:28 AM      9675 PowerShellCoreExecutionPolicy.adml
-a---      2/27/2020 12:28 AM      6201 PowerShellCoreExecutionPolicy.admx
```

<span data-ttu-id="14cc4-114">Après avoir installé les modèles, vous pouvez modifier ces paramètres dans l’éditeur de stratégie de groupe ( `gpedit.msc` ).</span><span class="sxs-lookup"><span data-stu-id="14cc4-114">After installing the templates, you can edit these settings in the Group Policy editor (`gpedit.msc`).</span></span>

<span data-ttu-id="14cc4-115">Les stratégies sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14cc4-115">The policies are as follows:</span></span>

- <span data-ttu-id="14cc4-116">Configuration de session de console : définit un point de terminaison de configuration dans lequel PowerShell est exécuté.</span><span class="sxs-lookup"><span data-stu-id="14cc4-116">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="14cc4-117">Activer la journalisation des modules : définit la propriété **LogPipelineExecutionDetails** des modules.</span><span class="sxs-lookup"><span data-stu-id="14cc4-117">Turn on Module Logging: Sets the **LogPipelineExecutionDetails** property of modules.</span></span>
- <span data-ttu-id="14cc4-118">Activer la journalisation de blocs de scripts PowerShell : active la journalisation détaillée de tous les scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14cc4-118">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="14cc4-119">Activer l’exécution des scripts : définit la stratégie d'exécution de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14cc4-119">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="14cc4-120">Activer la transcription PowerShell : active la capture d’entrée et de sortie de commandes PowerShell dans des transcriptions textuelles.</span><span class="sxs-lookup"><span data-stu-id="14cc4-120">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="14cc4-121">Définir le chemin source par défaut pour `Update-Help` : définit la source de l’aide actualisable dans un répertoire, et non sur Internet.</span><span class="sxs-lookup"><span data-stu-id="14cc4-121">Set the default source path for `Update-Help`: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="14cc4-122">Chaque paramètre de stratégie de groupe PowerShell a une option (« utiliser le paramètre de stratégie Windows PowerShell ») pour utiliser la valeur d’un paramètre de stratégie de groupe Windows PowerShell similaire qui se trouve dans les chemins d’accès de stratégie de groupe suivants :</span><span class="sxs-lookup"><span data-stu-id="14cc4-122">Each PowerShell Group Policy setting has an option ('Use Windows PowerShell Policy setting' field) to use the value from a similar Windows PowerShell Group Policy setting that is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

> [!NOTE]
> <span data-ttu-id="14cc4-123">Ces **modèles d’administration PowerShell Core** n’incluent pas de paramètres pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14cc4-123">These **PowerShell Core Administrative Templates** do not include settings for Windows PowerShell.</span></span> <span data-ttu-id="14cc4-124">Pour plus d’informations sur l’acquisition d’autres modèles et la configuration de la stratégie de groupe, voir [How to Create and Manage the central Store for stratégie de groupe modèles d’administration dans Windows][gpstore].</span><span class="sxs-lookup"><span data-stu-id="14cc4-124">For more information about acquiring other templates and configuring Group policy, see [How to create and manage the Central Store for Group Policy Administrative Templates in Windows][gpstore].</span></span>

## <a name="console-session-configuration"></a><span data-ttu-id="14cc4-125">Configuration de session de la console</span><span class="sxs-lookup"><span data-stu-id="14cc4-125">Console session configuration</span></span>

<span data-ttu-id="14cc4-126">Le paramètre de la stratégie de configuration de la session de la **console** spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté.</span><span class="sxs-lookup"><span data-stu-id="14cc4-126">The **Console session configuration** policy setting specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="14cc4-127">Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="14cc4-127">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

## <a name="turn-on-module-logging"></a><span data-ttu-id="14cc4-128">Activer la journalisation des modules</span><span class="sxs-lookup"><span data-stu-id="14cc4-128">Turn on module logging</span></span>

<span data-ttu-id="14cc4-129">Le paramètre de stratégie **activer la journalisation du module** active la journalisation pour les modules PowerShell sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="14cc4-129">The **Turn on Module Logging** policy setting turns on logging for selected PowerShell modules.</span></span> <span data-ttu-id="14cc4-130">Le paramètre s’applique à toutes les sessions sur tous les ordinateurs concernés.</span><span class="sxs-lookup"><span data-stu-id="14cc4-130">The setting is effective in all sessions on all affected computers.</span></span>

<span data-ttu-id="14cc4-131">Si vous activez ce paramètre de stratégie et spécifiez un ou plusieurs modules, les événements d’exécution de pipeline pour les modules spécifiés sont enregistrés dans le journal Windows PowerShell dans observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="14cc4-131">If you enable this policy setting and specify one or more modules, pipeline execution events for the specified modules are recorded in the Windows PowerShell log in Event Viewer.</span></span>

<span data-ttu-id="14cc4-132">Si vous désactivez ce paramètre de stratégie, la journalisation des événements d’exécution est désactivée pour tous les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14cc4-132">If you disable this policy setting, logging of execution events is disabled for all PowerShell modules.</span></span>

<span data-ttu-id="14cc4-133">Si ce paramètre de stratégie n’est pas configuré, la propriété **LogPipelineExecutionDetails** de chaque module détermine si les événements d’exécution d’un module sont journalisés.</span><span class="sxs-lookup"><span data-stu-id="14cc4-133">If this policy setting is not configured, the **LogPipelineExecutionDetails** property of each module determines whether the execution events of a module are logged.</span></span> <span data-ttu-id="14cc4-134">Par défaut, la propriété **LogPipelineExecutionDetails** de tous les modules est définie sur false.</span><span class="sxs-lookup"><span data-stu-id="14cc4-134">By default, the **LogPipelineExecutionDetails** property of all modules is set to False.</span></span>

<span data-ttu-id="14cc4-135">Pour activer la journalisation de module pour un module, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="14cc4-135">To turn on module logging for a module, use the following command format.</span></span> <span data-ttu-id="14cc4-136">Le module doit être importé dans la session et le paramètre est effectif uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="14cc4-136">The module must be imported into the session and the setting is effective only in the current session.</span></span>

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

<span data-ttu-id="14cc4-137">Pour activer la journalisation des modules pour toutes les sessions sur un ordinateur particulier, ajoutez les commandes précédentes au profil PowerShell « tous les utilisateurs » ( `$Profile.AllUsersAllHosts` ).</span><span class="sxs-lookup"><span data-stu-id="14cc4-137">To turn on module logging for all sessions on a particular computer, add the previous commands to the 'All Users' PowerShell profile (`$Profile.AllUsersAllHosts`).</span></span>

<span data-ttu-id="14cc4-138">Pour plus d’informations sur la journalisation des modules, consultez [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="14cc4-138">For more information about module logging, see [about_Modules](about_Modules.md).</span></span>

## <a name="turn-on-powershell-script-block-logging"></a><span data-ttu-id="14cc4-139">Activer la journalisation des blocs de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="14cc4-139">Turn on PowerShell script block logging</span></span>

<span data-ttu-id="14cc4-140">Le paramètre de stratégie activer la journalisation des **blocs de script PowerShell** active la journalisation de toutes les entrées de script PowerShell dans le journal des événements opérationnels de Microsoft-Windows-PowerShell/.</span><span class="sxs-lookup"><span data-stu-id="14cc4-140">The **Turn on PowerShell Script Block Logging** policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log.</span></span> <span data-ttu-id="14cc4-141">Si vous activez ce paramètre de stratégie, PowerShell Core enregistre le traitement des commandes, des blocs de script, des fonctions et des scripts, qu’il soit appelé de manière interactive ou par le biais de l’automatisation.</span><span class="sxs-lookup"><span data-stu-id="14cc4-141">If you enable this policy setting, PowerShell Core will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation.</span></span>

<span data-ttu-id="14cc4-142">Si vous désactivez ce paramètre de stratégie, la journalisation des entrées de script PowerShell est désactivée.</span><span class="sxs-lookup"><span data-stu-id="14cc4-142">If you disable this policy setting, logging of PowerShell script input is disabled.</span></span> <span data-ttu-id="14cc4-143">Si vous activez la journalisation des appels de bloc de script, PowerShell journalise en plus les événements lors de l’appel d’une commande, un bloc de script, d’une fonction, ou quand un script démarre ou s’arrête.</span><span class="sxs-lookup"><span data-stu-id="14cc4-143">If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops.</span></span> <span data-ttu-id="14cc4-144">L’activation de la journalisation des appels génère un grand volume de journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="14cc4-144">Enabling Invocation Logging generates a high volume of event logs.</span></span>

## <a name="turn-on-script-execution"></a><span data-ttu-id="14cc4-145">Activer l’exécution du script</span><span class="sxs-lookup"><span data-stu-id="14cc4-145">Turn on script execution</span></span>

<span data-ttu-id="14cc4-146">Le paramètre de stratégie **activer l’exécution du script** définit la stratégie d’exécution pour les ordinateurs et les utilisateurs, qui détermine quels scripts sont autorisés à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="14cc4-146">The **Turn on Script Execution** policy setting sets the execution policy for computers and users, which determines which scripts are permitted to run.</span></span>

<span data-ttu-id="14cc4-147">Si vous activez le paramètre de stratégie, vous pouvez sélectionner parmi les paramètres de stratégie suivants.</span><span class="sxs-lookup"><span data-stu-id="14cc4-147">If you enable the policy setting, you can select from among the following policy settings.</span></span>

- <span data-ttu-id="14cc4-148">**Autoriser uniquement les scripts signés** permet aux scripts de s’exécuter uniquement s’ils sont signés par un éditeur approuvé.</span><span class="sxs-lookup"><span data-stu-id="14cc4-148">**Allow only signed scripts** allows scripts to execute only if they are signed by a trusted publisher.</span></span> <span data-ttu-id="14cc4-149">Ce paramètre de stratégie est équivalent à la stratégie d’exécution AllSigned.</span><span class="sxs-lookup"><span data-stu-id="14cc4-149">This policy setting is equivalent to the AllSigned execution policy.</span></span>

- <span data-ttu-id="14cc4-150">**Autoriser les scripts locaux et les scripts signés distants** autorise l’exécution de tous les scripts locaux.</span><span class="sxs-lookup"><span data-stu-id="14cc4-150">**Allow local scripts and remote signed scripts** allows all local scripts to run.</span></span> <span data-ttu-id="14cc4-151">Les scripts provenant d’Internet doivent être signés par un éditeur approuvé.</span><span class="sxs-lookup"><span data-stu-id="14cc4-151">Scripts that originate from the Internet must be signed by a trusted publisher.</span></span> <span data-ttu-id="14cc4-152">Ce paramètre de stratégie est équivalent à la stratégie d’exécution RemoteSigned.</span><span class="sxs-lookup"><span data-stu-id="14cc4-152">This policy setting is equivalent to the RemoteSigned execution policy.</span></span>

- <span data-ttu-id="14cc4-153">**Autoriser tous les scripts** autorise l’exécution de tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="14cc4-153">**Allow all scripts** allows all scripts to run.</span></span> <span data-ttu-id="14cc4-154">Ce paramètre de stratégie équivaut à la stratégie d’exécution illimitée.</span><span class="sxs-lookup"><span data-stu-id="14cc4-154">This policy setting is equivalent to the Unrestricted execution policy.</span></span>

<span data-ttu-id="14cc4-155">Si vous désactivez ce paramètre de stratégie, aucun script n’est autorisé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="14cc4-155">If you disable this policy setting, no scripts are allowed to run.</span></span> <span data-ttu-id="14cc4-156">Ce paramètre de stratégie est équivalent à la stratégie d’exécution restreinte.</span><span class="sxs-lookup"><span data-stu-id="14cc4-156">This policy setting is equivalent to the Restricted execution policy.</span></span>

<span data-ttu-id="14cc4-157">Si vous désactivez ou ne configurez pas ce paramètre de stratégie, la stratégie d’exécution définie pour l’ordinateur ou l’utilisateur par l' `Set-ExecutionPolicy` applet de commande détermine si les scripts sont autorisés à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="14cc4-157">If you disable or do not configure this policy setting, the execution policy that is set for the computer or user by the `Set-ExecutionPolicy` cmdlet determines whether scripts are permitted to run.</span></span> <span data-ttu-id="14cc4-158">La valeur par défaut est Restricted.</span><span class="sxs-lookup"><span data-stu-id="14cc4-158">The default value is Restricted.</span></span>

<span data-ttu-id="14cc4-159">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="14cc4-159">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="turn-on-powershell-transcription"></a><span data-ttu-id="14cc4-160">Activer la transcription PowerShell</span><span class="sxs-lookup"><span data-stu-id="14cc4-160">Turn on powershell transcription</span></span>

<span data-ttu-id="14cc4-161">Le paramètre de stratégie **activer la transcription PowerShell** vous permet de capturer l’entrée et la sortie des commandes PowerShell Core dans des transcriptions textuelles.</span><span class="sxs-lookup"><span data-stu-id="14cc4-161">The **Turn on PowerShell Transcription** policy setting lets you capture the input and output of PowerShell Core commands into text-based transcripts.</span></span> <span data-ttu-id="14cc4-162">Si vous activez ce paramètre de stratégie, PowerShell Core active la journalisation de la transcription pour PowerShell Core et toutes les autres applications qui exploitent le moteur PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="14cc4-162">If you enable this policy setting, PowerShell Core will enable transcription logging for PowerShell Core and any other applications that leverage the PowerShell Core engine.</span></span> <span data-ttu-id="14cc4-163">Par défaut, PowerShell Core enregistre la sortie de transcription dans le répertoire Mes documents de chaque utilisateur, avec un nom de fichier qui comprend « PowerShell_transcript », ainsi que le nom de l’ordinateur et l’heure de début.</span><span class="sxs-lookup"><span data-stu-id="14cc4-163">By default, PowerShell Core will record transcript output to each users' My Documents directory, with a file name that includes 'PowerShell_transcript', along with the computer name and time started.</span></span>
<span data-ttu-id="14cc4-164">L’activation de cette stratégie revient à appeler l’applet de commande Start-Transcript sur chaque session PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="14cc4-164">Enabling this policy is equivalent to calling the Start-Transcript cmdlet on each PowerShell Core session.</span></span>

<span data-ttu-id="14cc4-165">Si vous désactivez ce paramètre de stratégie, la journalisation transcription des applications basées sur PowerShell est désactivée par défaut, bien que la transcription puisse toujours être activée via l’applet de commande Start-Transcript.</span><span class="sxs-lookup"><span data-stu-id="14cc4-165">If you disable this policy setting, transcription logging of PowerShell-based applications is disabled by default, although transcripting can still be enabled through the Start-Transcript cmdlet.</span></span>

<span data-ttu-id="14cc4-166">Si vous utilisez le paramètre OutputDirectory pour activer la journalisation des transcriptions dans un emplacement partagé, veillez à limiter l’accès à ce répertoire pour empêcher les utilisateurs d’afficher les transcriptions d’autres utilisateurs ou ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="14cc4-166">If you use the OutputDirectory setting to enable transcription logging to a shared location, be sure to limit access to that directory to prevent users from viewing the transcripts of other users or computers.</span></span>

## <a name="set-the-default-source-path-for-update-help"></a><span data-ttu-id="14cc4-167">Définir le chemin source par défaut de Update-Help</span><span class="sxs-lookup"><span data-stu-id="14cc4-167">Set the default source path for Update-Help</span></span>

<span data-ttu-id="14cc4-168">Le paramètre **définir le chemin d’accès source par défaut pour la stratégie Update-Help** définit une valeur par défaut pour le paramètre **SourcePath** de l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="14cc4-168">The **Set the Default Source Path for Update-Help** policy setting sets a default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span>
<span data-ttu-id="14cc4-169">Ce paramètre empêche les utilisateurs d’utiliser l’applet de commande `Update-Help` pour télécharger les fichiers d’aide à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="14cc4-169">This setting prevents users from using the `Update-Help` cmdlet to download help files from the Internet.</span></span>

> [!NOTE]
> <span data-ttu-id="14cc4-170">Ce paramètre stratégie de groupe s’affiche sous **Configuration ordinateur** et **Configuration utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="14cc4-170">This Group Policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="14cc4-171">Toutefois, seul le paramètre stratégie de groupe sous **Configuration ordinateur** est effectif.</span><span class="sxs-lookup"><span data-stu-id="14cc4-171">However, only the Group Policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="14cc4-172">Le paramètre stratégie de groupe sous **Configuration utilisateur** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="14cc4-172">The Group Policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="14cc4-173">L' `Update-Help` applet de commande télécharge et installe les fichiers d’aide les plus récents pour les modules PowerShell et les installe sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14cc4-173">The `Update-Help` cmdlet downloads and installs the newest help files for PowerShell modules and installs them on the computer.</span></span> <span data-ttu-id="14cc4-174">Par défaut, `Update-Help` télécharge les nouveaux fichiers d’aide à partir d’un emplacement Internet spécifié par le module.</span><span class="sxs-lookup"><span data-stu-id="14cc4-174">By default, `Update-Help` downloads new help files from an Internet location specified by the module.</span></span>

<span data-ttu-id="14cc4-175">Toutefois, vous pouvez utiliser l' `Save-Help` applet de commande pour télécharger les fichiers d’aide les plus récents vers un emplacement de système de fichiers, tel qu’un partage réseau, puis utiliser l' `Update-Help` applet de commande pour obtenir les fichiers d’aide à partir de l’emplacement du système de fichiers et les installer sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14cc4-175">However, you can use the `Save-Help` cmdlet to download the newest help files to a file system location, such as a network share, and then use the `Update-Help` cmdlet to get the help files from the file system location and install them on the computer.</span></span> <span data-ttu-id="14cc4-176">Le paramètre **SourcePath** de l' `Update-Help` applet de commande spécifie l’emplacement du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="14cc4-176">The **SourcePath** parameter of the `Update-Help` cmdlet specifies the file system location.</span></span>

<span data-ttu-id="14cc4-177">En fournissant une valeur par défaut pour le paramètre **SourcePath** , ce stratégie de groupe paramètre ajoute implicitement le paramètre **SourcePath** à toutes les `Update-Help` commandes.</span><span class="sxs-lookup"><span data-stu-id="14cc4-177">By providing a default value for the **SourcePath** parameter, this Group Policy setting implicitly adds the **SourcePath** parameter to all `Update-Help` commands.</span></span> <span data-ttu-id="14cc4-178">Les utilisateurs peuvent remplacer l’emplacement spécifique du système de fichiers spécifié comme valeur par défaut en entrant un emplacement de système de fichiers différent.</span><span class="sxs-lookup"><span data-stu-id="14cc4-178">Users can override the particular file system location specified as the default value by entering a different file system location.</span></span>
<span data-ttu-id="14cc4-179">Mais ils ne peuvent pas supprimer le paramètre **SourcePath** de la `Update-Help` commande.</span><span class="sxs-lookup"><span data-stu-id="14cc4-179">But they cannot remove the **SourcePath** parameter from the `Update-Help` command.</span></span>

<span data-ttu-id="14cc4-180">Si vous activez ce paramètre de stratégie, vous pouvez spécifier une valeur par défaut pour le paramètre **SourcePath** .</span><span class="sxs-lookup"><span data-stu-id="14cc4-180">If you enable this policy setting, you can specify a default value for the **SourcePath** parameter.</span></span> <span data-ttu-id="14cc4-181">Entrez un emplacement de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="14cc4-181">Enter a file system location.</span></span>

<span data-ttu-id="14cc4-182">Si ce paramètre de stratégie est désactivé ou n’est pas configuré, il n’existe pas de valeur par défaut pour le paramètre **SourcePath** de l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="14cc4-182">If this policy setting is disabled or not configured, there is no default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="14cc4-183">Les utilisateurs peuvent télécharger l’aide à partir d’Internet ou à partir de n’importe quel emplacement du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="14cc4-183">Users can download help from the Internet or from any file system location.</span></span>

<span data-ttu-id="14cc4-184">Pour plus d’informations, voir [about_Updatable_Help](about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="14cc4-184">For more information, see [about_Updatable_Help](about_Updatable_Help.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="14cc4-185">Mots clés</span><span class="sxs-lookup"><span data-stu-id="14cc4-185">Keywords</span></span>

<span data-ttu-id="14cc4-186">about_Group_Policies about_GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="14cc4-186">about_Group_Policies about_GroupPolicy</span></span>

## <a name="see-also"></a><span data-ttu-id="14cc4-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14cc4-187">See also</span></span>

[<span data-ttu-id="14cc4-188">RFC principale de la stratégie PowerShell</span><span class="sxs-lookup"><span data-stu-id="14cc4-188">PowerShell Core Policy RFC</span></span>](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[<span data-ttu-id="14cc4-189">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="14cc4-189">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="14cc4-190">about_Modules</span><span class="sxs-lookup"><span data-stu-id="14cc4-190">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="14cc4-191">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="14cc4-191">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="14cc4-192">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="14cc4-192">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="14cc4-193">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="14cc4-193">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="14cc4-194">Get-Module</span><span class="sxs-lookup"><span data-stu-id="14cc4-194">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="14cc4-195">Update-Help</span><span class="sxs-lookup"><span data-stu-id="14cc4-195">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)

[<span data-ttu-id="14cc4-196">Save-Help</span><span class="sxs-lookup"><span data-stu-id="14cc4-196">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759

