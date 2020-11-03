---
description: Décrit comment accéder aux variables d’environnement Windows dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 3004e01e59d30005ad2fbfa92897f43471a41384
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208045"
---
# <a name="about-environment-variables"></a><span data-ttu-id="4b3f8-104">À propos des variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="4b3f8-104">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="4b3f8-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="4b3f8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="4b3f8-106">Décrit comment accéder aux variables d’environnement Windows dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-106">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4b3f8-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="4b3f8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="4b3f8-108">Les variables d’environnement stockent des informations sur l’environnement du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-108">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="4b3f8-109">Ces informations incluent des détails tels que le chemin d’accès du système d’exploitation, le nombre de processeurs utilisés par le système d’exploitation et l’emplacement des dossiers temporaires.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-109">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="4b3f8-110">Les variables d’environnement stockent les données utilisées par le système d’exploitation et d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-110">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="4b3f8-111">Par exemple, la `WINDIR` variable d’environnement contient l’emplacement du répertoire d’installation de Windows.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-111">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="4b3f8-112">Les programmes peuvent interroger la valeur de cette variable pour déterminer où se trouvent les fichiers de système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-112">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="4b3f8-113">PowerShell peut accéder aux variables d’environnement et les gérer dans toutes les plateformes de système d’exploitation prises en charge.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-113">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="4b3f8-114">Le fournisseur d’environnement PowerShell simplifie ce processus en facilitant l’affichage et la modification des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-114">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="4b3f8-115">Contrairement aux autres types de variables dans PowerShell, les variables d’environnement sont héritées par les processus enfants, tels que les tâches en arrière-plan locales et les sessions dans lesquelles les membres du module s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-115">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="4b3f8-116">Ainsi, les variables d’environnement sont bien adaptées au stockage des valeurs nécessaires dans les processus parents et enfants.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-116">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="4b3f8-117">Utilisation et modification des variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="4b3f8-117">Using and changing environment variables</span></span>

<span data-ttu-id="4b3f8-118">Sur Windows, les variables d’environnement peuvent être définies dans trois étendues :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-118">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="4b3f8-119">Portée de l’ordinateur (ou système)</span><span class="sxs-lookup"><span data-stu-id="4b3f8-119">Machine (or System) scope</span></span>
- <span data-ttu-id="4b3f8-120">Étendue d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="4b3f8-120">User scope</span></span>
- <span data-ttu-id="4b3f8-121">Portée du processus</span><span class="sxs-lookup"><span data-stu-id="4b3f8-121">Process scope</span></span>

<span data-ttu-id="4b3f8-122">La portée du _processus_ contient les variables d’environnement disponibles dans le processus en cours, ou la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-122">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="4b3f8-123">Cette liste de variables est héritée du processus parent et est construite à partir des variables dans les étendues de l' _ordinateur_ et de l' _utilisateur_ .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-123">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span>

<span data-ttu-id="4b3f8-124">Vous pouvez afficher et modifier les valeurs des variables d’environnement sans utiliser une applet de commande à l’aide d’une syntaxe de variable avec le fournisseur de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="4b3f8-125">Pour afficher la valeur d’une variable d’environnement, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="4b3f8-126">Par exemple, pour afficher la valeur de la `WINDIR` variable d’environnement, tapez la commande suivante à l’invite de commandes PowerShell :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="4b3f8-127">Dans cette syntaxe, le signe dollar ( `$` ) indique une variable, et le nom du lecteur ( `Env:` ) indique une variable d’environnement suivie du nom de la variable ( `windir` ).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="4b3f8-128">Lorsque vous modifiez des variables d’environnement dans PowerShell, la modification affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="4b3f8-129">Ce comportement ressemble au comportement de la `Set` commande dans l’interface de commande Windows et `Setenv` à la commande dans les environnements UNIX.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="4b3f8-130">Pour modifier des valeurs dans les portées de l’ordinateur ou de l’utilisateur, vous devez utiliser les méthodes de la classe **System. Environment** .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="4b3f8-131">Pour apporter des modifications aux variables de l’étendue de l’ordinateur, doit également avoir l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="4b3f8-132">Si vous tentez de modifier une valeur sans autorisation suffisante, la commande échoue et PowerShell affiche une erreur.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="4b3f8-133">Vous pouvez modifier les valeurs des variables sans utiliser une applet de commande à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="4b3f8-134">Par exemple, pour ajouter `;c:\temp` à la valeur de la `Path` variable d’environnement, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="4b3f8-135">Vous pouvez également utiliser les applets de commande Item, telles que `Set-Item` , `Remove-Item` et `Copy-Item` pour modifier les valeurs des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-135">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="4b3f8-136">Par exemple, pour utiliser l' `Set-Item` applet de commande pour ajouter `;c:\temp` à la valeur de la `Path` variable d’environnement, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-136">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="4b3f8-137">Dans cette commande, la valeur est placée entre parenthèses afin qu’elle soit interprétée comme une unité.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-137">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="4b3f8-138">Variables d’environnement qui stockent des préférences</span><span class="sxs-lookup"><span data-stu-id="4b3f8-138">Environment variables that store preferences</span></span>

<span data-ttu-id="4b3f8-139">Les fonctionnalités PowerShell peuvent utiliser des variables d’environnement pour stocker les préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-139">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="4b3f8-140">Ces variables fonctionnent comme des variables de préférence, mais elles sont héritées par les sessions enfants des sessions dans lesquelles elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-140">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="4b3f8-141">Pour plus d’informations sur les variables de préférence, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-141">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="4b3f8-142">Les variables d’environnement qui stockent les préférences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-142">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="4b3f8-143">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="4b3f8-143">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="4b3f8-144">Stocke la stratégie d’exécution définie pour la session active.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-144">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="4b3f8-145">Cette variable d’environnement existe uniquement lorsque vous définissez une stratégie d’exécution pour une seule session.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-145">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="4b3f8-146">Vous pouvez le faire de deux manières différentes.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-146">You can do this in two different ways.</span></span>

  - <span data-ttu-id="4b3f8-147">Démarrez une session à partir de la ligne de commande à l’aide du paramètre **ExecutionPolicy** pour définir la stratégie d’exécution de la session.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-147">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="4b3f8-148">Utilisez l'applet de commande `Set-ExecutionPolicy`.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-148">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="4b3f8-149">Utilisez le paramètre scope avec la valeur « Process ».</span><span class="sxs-lookup"><span data-stu-id="4b3f8-149">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="4b3f8-150">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-150">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="4b3f8-151">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="4b3f8-151">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="4b3f8-152">PowerShell vous permet de contrôler le fichier utilisé pour mettre en cache les données relatives aux modules et à leurs applets de commande.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-152">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="4b3f8-153">Le cache est lu au démarrage lors de la recherche d’une commande et est écrit sur un thread d’arrière-plan quelque temps après l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-153">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="4b3f8-154">L’emplacement par défaut du cache est le suivant :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-154">Default location of the cache is:</span></span>

  - `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`

  <span data-ttu-id="4b3f8-155">Le nom de fichier par défaut du cache est `ModuleAnalysisCache` .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-155">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="4b3f8-156">Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement avant de Démarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-156">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="4b3f8-157">Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-157">Changes to this environment variable only affect child processes.</span></span>
  <span data-ttu-id="4b3f8-158">La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-158">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4b3f8-159">Si la découverte de commande ne fonctionne pas correctement, par exemple IntelliSense affiche des commandes qui n’existent pas, vous pouvez supprimer le fichier cache.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-159">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="4b3f8-160">Le cache est recréé la prochaine fois que vous démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-160">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="4b3f8-161">Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-161">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="4b3f8-162">Cela définit le chemin d’accès à l’appareil **nul** .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-162">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="4b3f8-163">PowerShell ne peut pas écrire dans le chemin d’accès, mais aucune erreur n’est retournée.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-163">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="4b3f8-164">Vous pouvez voir les erreurs signalées à l’aide d’un suivi :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-164">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="4b3f8-165">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="4b3f8-165">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="4b3f8-166">Lors de l’écriture du cache d’analyse de module, PowerShell recherche les modules qui n’existent plus afin d’éviter un cache trop volumineux.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-166">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="4b3f8-167">Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant cette valeur de variable d’environnement sur `1` .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-167">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="4b3f8-168">La définition de cette variable d’environnement prend effet immédiatement dans le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-168">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="4b3f8-169">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4b3f8-169">PSModulePath</span></span>

  <span data-ttu-id="4b3f8-170">La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-170">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="4b3f8-171">Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-171">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="4b3f8-172">Emplacements à l’ensemble du système : ces dossiers contiennent des modules fournis avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-172">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="4b3f8-173">Les modules sont stockés à l' `$PSHOME\Modules` emplacement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-173">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="4b3f8-174">Il s’agit également de l’emplacement où sont installés les modules de gestion Windows.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-174">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="4b3f8-175">Modules installés par l’utilisateur : il s’agit de modules installés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-175">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="4b3f8-176">`Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-176">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="4b3f8-177">Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-177">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="4b3f8-178">Sur Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME\Documents\PowerShell\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-178">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="4b3f8-179">L’emplacement de l’étendue **ALLUSERS** est `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-179">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>

  <span data-ttu-id="4b3f8-180">En outre, les programmes d’installation qui installent des modules dans d’autres répertoires, tels que le répertoire Program Files, peuvent ajouter leurs emplacements à la valeur de `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-180">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="4b3f8-181">Pour plus d’informations, consultez [about_PSModulePath](about_PSModulePath.md).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-181">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="4b3f8-182">Gestion des variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="4b3f8-182">Managing environment variables</span></span>

<span data-ttu-id="4b3f8-183">PowerShell offre plusieurs méthodes différentes pour la gestion des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-183">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="4b3f8-184">Lecteur du fournisseur de l’environnement</span><span class="sxs-lookup"><span data-stu-id="4b3f8-184">The Environment provider drive</span></span>
- <span data-ttu-id="4b3f8-185">Applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="4b3f8-185">The Item cmdlets</span></span>
- <span data-ttu-id="4b3f8-186">Classe .NET **System. Environment**</span><span class="sxs-lookup"><span data-stu-id="4b3f8-186">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="4b3f8-187">Sur Windows, le panneau de configuration système</span><span class="sxs-lookup"><span data-stu-id="4b3f8-187">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="4b3f8-188">Utilisation du fournisseur d’environnement</span><span class="sxs-lookup"><span data-stu-id="4b3f8-188">Using the Environment provider</span></span>

<span data-ttu-id="4b3f8-189">Chaque variable d’environnement est représentée par une instance de la classe **System. Collections. DictionaryEntry** .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-189">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="4b3f8-190">Dans chaque objet **DictionaryEntry** , le nom de la variable d’environnement est la clé du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-190">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="4b3f8-191">La valeur de la variable est la valeur du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-191">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="4b3f8-192">Pour afficher les propriétés et les méthodes de l’objet qui représente une variable d’environnement dans PowerShell, utilisez l’applet de commande `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-192">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="4b3f8-193">Par exemple, pour afficher les méthodes et les propriétés de tous les objets du `Env:` lecteur, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-193">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="4b3f8-194">Le fournisseur d’environnement PowerShell vous permet d’accéder aux variables d’environnement dans un lecteur PowerShell (le `Env:` lecteur).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-194">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="4b3f8-195">Ce lecteur ressemble plus à un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-195">This drive looks much like a file system drive.</span></span> <span data-ttu-id="4b3f8-196">Pour accéder au `Env:` lecteur, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-196">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="4b3f8-197">Utilisez les applets de commande content pour récupérer ou définir les valeurs d’une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-197">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="4b3f8-198">Vous pouvez afficher les variables d’environnement dans le `Env:` lecteur à partir de n’importe quel autre lecteur PowerShell, et vous pouvez accéder au `Env:` lecteur pour afficher et modifier les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-198">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="4b3f8-199">Utilisation des applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="4b3f8-199">Using Item cmdlets</span></span>

<span data-ttu-id="4b3f8-200">Lorsque vous faites référence à une variable d’environnement, tapez le `Env:` nom du lecteur, suivi du nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-200">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="4b3f8-201">Par exemple, pour afficher la valeur de la `COMPUTERNAME` variable d’environnement, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-201">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="4b3f8-202">Pour afficher les valeurs de toutes les variables d’environnement, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-202">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="4b3f8-203">Étant donné que les variables d’environnement n’ont pas d’éléments enfants, la sortie de `Get-Item` et `Get-ChildItem` est la même.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-203">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="4b3f8-204">Par défaut, PowerShell affiche les variables d’environnement dans l’ordre dans lequel elles les récupère.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-204">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="4b3f8-205">Pour trier la liste des variables d’environnement par nom de variable, dirigez la sortie d’une `Get-ChildItem` commande vers l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-205">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="4b3f8-206">Par exemple, à partir de n’importe quel lecteur PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-206">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="4b3f8-207">Vous pouvez également accéder au lecteur à l' `Env:` aide de l’applet de commande `Set-Location` :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-207">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="4b3f8-208">Lorsque vous êtes dans le `Env:` lecteur, vous pouvez omettre le `Env:` nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-208">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="4b3f8-209">Par exemple, pour afficher toutes les variables d’environnement, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-209">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="4b3f8-210">Pour afficher la valeur de la `COMPUTERNAME` variable à partir du `Env:` lecteur, tapez :</span><span class="sxs-lookup"><span data-stu-id="4b3f8-210">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="4b3f8-211">Enregistrement des modifications apportées aux variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="4b3f8-211">Saving changes to environment variables</span></span>

<span data-ttu-id="4b3f8-212">Pour apporter une modification permanente à une variable d’environnement sur Windows, utilisez le panneau de configuration système.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-212">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="4b3f8-213">Sélectionnez **paramètres système avancés** .</span><span class="sxs-lookup"><span data-stu-id="4b3f8-213">Select **Advanced System Settings** .</span></span> <span data-ttu-id="4b3f8-214">Sous l’onglet **avancé** , cliquez sur **variable d’environnement...** . Vous pouvez ajouter ou modifier des variables d’environnement existantes dans les étendues **utilisateur** et **système** (ordinateur).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-214">On the **Advanced** tab, click **Environment Variable...** . You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="4b3f8-215">Windows écrit ces valeurs dans le registre afin qu’elles soient conservées entre les sessions et les redémarrages du système.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-215">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="4b3f8-216">Vous pouvez également ajouter ou modifier des variables d’environnement dans votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-216">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="4b3f8-217">Cette méthode fonctionne pour n’importe quelle version de PowerShell sur n’importe quelle plateforme prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-217">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="4b3f8-218">Utilisation des méthodes System. Environment</span><span class="sxs-lookup"><span data-stu-id="4b3f8-218">Using System.Environment methods</span></span>

<span data-ttu-id="4b3f8-219">La classe **System. Environment** fournit des méthodes **GetEnvironmentVariable** et **SetEnvironmentVariable ne contient** qui vous permettent de spécifier la portée de la variable.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-219">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="4b3f8-220">L’exemple suivant utilise la méthode **GetEnvironmentVariable** pour récupérer le paramètre de l’ordinateur de `PSModulePath` et la méthode **SetEnvironmentVariable ne contient** pour ajouter le `C:\Program Files\Fabrikam\Modules` chemin d’accès à la valeur.</span><span class="sxs-lookup"><span data-stu-id="4b3f8-220">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="4b3f8-221">Pour plus d’informations sur les méthodes de la classe **System. Environment** , consultez [méthodes d’environnement](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="4b3f8-221">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b3f8-222">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="4b3f8-222">SEE ALSO</span></span>

- [<span data-ttu-id="4b3f8-223">Environnement (fournisseur)</span><span class="sxs-lookup"><span data-stu-id="4b3f8-223">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="4b3f8-224">about_Modules</span><span class="sxs-lookup"><span data-stu-id="4b3f8-224">about_Modules</span></span>](about_Modules.md)
