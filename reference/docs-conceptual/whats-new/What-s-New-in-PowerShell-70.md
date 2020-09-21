---
title: Nouveautés de PowerShell 7.0
description: Nouvelles fonctionnalités et modifications de PowerShell 7.0
ms.date: 03/04/2020
ms.openlocfilehash: d52b536efd9d7a1f8e6b01a58952f08ca49016b1
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162458"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="d555f-103">Nouveautés de PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="d555f-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="d555f-104">PowerShell 7.0 est une édition de multiplateforme open source (Windows, macOS et Linux) conçue pour gérer des environnements hétérogènes et le cloud hybride.</span><span class="sxs-lookup"><span data-stu-id="d555f-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="d555f-105">Dans cette version, nous présentons plusieurs fonctionnalités, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d555f-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="d555f-106">Parallélisation de pipeline avec `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="d555f-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="d555f-107">Nouveaux opérateurs :</span><span class="sxs-lookup"><span data-stu-id="d555f-107">New operators:</span></span>
  - <span data-ttu-id="d555f-108">Opérateur ternaire : `a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="d555f-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="d555f-109">Opérateurs de chaîne de pipeline : `||` et `&&`</span><span class="sxs-lookup"><span data-stu-id="d555f-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="d555f-110">Opérations conditionnelles Null : `??` et `??=`</span><span class="sxs-lookup"><span data-stu-id="d555f-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="d555f-111">Un affichage des erreurs simplifié et dynamique ainsi qu’une cmdlet `Get-Error` pour étudier plus facilement les erreurs</span><span class="sxs-lookup"><span data-stu-id="d555f-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="d555f-112">Une couche de compatibilité qui permet aux utilisateurs d’importer des modules dans une session Windows PowerShell implicite</span><span class="sxs-lookup"><span data-stu-id="d555f-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="d555f-113">Notifications automatiques en cas de nouvelles versions</span><span class="sxs-lookup"><span data-stu-id="d555f-113">Automatic new version notifications</span></span>
- <span data-ttu-id="d555f-114">La possibilité d’appeler des ressources DSC directement à partir de PowerShell 7 (stade expérimental)</span><span class="sxs-lookup"><span data-stu-id="d555f-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="d555f-115">Pour afficher une liste complète des fonctionnalités et des correctifs, consultez les [journaux des modifications](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span><span class="sxs-lookup"><span data-stu-id="d555f-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="d555f-116">Où puis-je installer PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="d555f-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="d555f-117">PowerShell 7 prend actuellement en charge les systèmes d’exploitation suivants sur x64, notamment :</span><span class="sxs-lookup"><span data-stu-id="d555f-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="d555f-118">Windows 8.1 et 10</span><span class="sxs-lookup"><span data-stu-id="d555f-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="d555f-119">Windows Server 2012, 2012 R2, 2016 et 2019</span><span class="sxs-lookup"><span data-stu-id="d555f-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="d555f-120">macOS 10.13+</span><span class="sxs-lookup"><span data-stu-id="d555f-120">macOS 10.13+</span></span>
- <span data-ttu-id="d555f-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d555f-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="d555f-122">Fedora 30+</span><span class="sxs-lookup"><span data-stu-id="d555f-122">Fedora 30+</span></span>
- <span data-ttu-id="d555f-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d555f-123">Debian 9</span></span>
- <span data-ttu-id="d555f-124">Ubuntu LTS 16.04+</span><span class="sxs-lookup"><span data-stu-id="d555f-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="d555f-125">Alpine Linux 3.8+</span><span class="sxs-lookup"><span data-stu-id="d555f-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="d555f-126">En outre, PowerShell 7.0 prend en charge les versions ARM32 et ARM64 de Debian, Ubuntu et ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="d555f-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="d555f-127">Consultez les instructions d’installation pour votre système d’exploitation par défaut [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) ou [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="d555f-128">Bien qu’ils ne soit pas officiellement pris en charge, la communauté a également fourni des packages pour [Arch](https://aur.archlinux.org/packages/powershell/) et Kali Linux.</span><span class="sxs-lookup"><span data-stu-id="d555f-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-129">Debian 10 et CentOS 8 ne prennent actuellement pas en charge la communication à distance WinRM.</span><span class="sxs-lookup"><span data-stu-id="d555f-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="d555f-130">Pour plus d’informations sur la configuration de la communication à distance basée sur SSH, consultez [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="d555f-131">Pour plus d’informations à jour sur les systèmes d’exploitation pris en charge et le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="d555f-132">Exécution de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="d555f-132">Running PowerShell 7</span></span>

<span data-ttu-id="d555f-133">PowerShell 7 s’installe dans un répertoire distinct de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d555f-133">PowerShell 7 installs to a directory seperately from Windows PowerShell.</span></span>
<span data-ttu-id="d555f-134">Cela vous permet d’exécuter PowerShell 7 côte à côte avec Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="d555f-134">This enables you to run PowerShell 7 side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="d555f-135">Pour PowerShell Core 6.x, PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="d555f-135">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="d555f-136">PowerShell 7 est installé sur `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="d555f-136">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="d555f-137">Le dossier `%programfiles%\PowerShell\7` est ajouté à `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="d555f-137">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="d555f-138">Le package d’installation PowerShell 7 met à niveau les versions précédentes de PowerShell Core 6.x :</span><span class="sxs-lookup"><span data-stu-id="d555f-138">The PowerShell 7 installer package upgrades previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="d555f-139">PowerShell Core 6.x sur Windows : `%programfiles%\PowerShell\6` est remplacé par `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="d555f-139">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="d555f-140">Linux : `/opt/microsoft/powershell/6` est remplacée par `/opt/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="d555f-140">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="d555f-141">macOS : `/usr/local/microsoft/powershell/6` est remplacée par `/usr/local/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="d555f-141">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-142">Dans Windows PowerShell, l’exécutable permettant de lancer PowerShell est nommé `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="d555f-142">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="d555f-143">Dans la version 6 et les versions ultérieures, le nom de l’exécutable est modifié pour prendre en charge l’exécution côte à côte.</span><span class="sxs-lookup"><span data-stu-id="d555f-143">In version 6 and above, the executable name is changed to support side-by-side execution.</span></span> <span data-ttu-id="d555f-144">Le nouveau nom de l’exécutable permettant de lancer PowerShell 7 est `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="d555f-144">The new executable name to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="d555f-145">Les builds préliminaires sont conservées en tant que `pwsh-preview` au lieu de `pwsh` sous le répertoire 7-préversion.</span><span class="sxs-lookup"><span data-stu-id="d555f-145">Preview builds remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="d555f-146">Compatibilité descendante avec Windows PowerShell améliorée</span><span class="sxs-lookup"><span data-stu-id="d555f-146">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="d555f-147">PowerShell 7.0 marque un passage à .NET Core 3.1, ce qui permet d’améliorer significativement la compatibilité descendante avec les modules Windows PowerShell existants.</span><span class="sxs-lookup"><span data-stu-id="d555f-147">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="d555f-148">Ceci inclut de nombreux modules sur Windows qui nécessitent une fonctionnalité GUI comme `Out-GridView` et `Show-Command`, ainsi que de nombreux modules de gestion des rôles fournis avec Windows.</span><span class="sxs-lookup"><span data-stu-id="d555f-148">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="d555f-149">Pour Windows, un nouveau paramètre de commutateur **UseWindowsPowerShell** est ajouté à `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="d555f-149">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="d555f-150">Ce commutateur crée un module proxy dans PowerShell 7, qui utilise un processus Windows PowerShell local pour exécuter implicitement toutes les cmdlets contenues dans ce module.</span><span class="sxs-lookup"><span data-stu-id="d555f-150">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="d555f-151">Pour plus d’informations sur [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-151">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="d555f-152">Pour plus d’informations sur les modules Microsoft fonctionnant avec PowerShell 7.0, consultez le [tableau de compatibilité des modules](https://aka.ms/PSModuleCompat).</span><span class="sxs-lookup"><span data-stu-id="d555f-152">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="d555f-153">Exécution parallèle ajoutée à ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d555f-153">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="d555f-154">La cmdlet `ForEach-Object`, qui itère des éléments dans une collection, dispose maintenant d’un parallélisme intégré avec le nouveau paramètre **Parallèle**.</span><span class="sxs-lookup"><span data-stu-id="d555f-154">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="d555f-155">Par défaut, les blocs de scripts parallèles utilisent le répertoire de travail actuel de l’appelant qui a démarré les tâches parallèles.</span><span class="sxs-lookup"><span data-stu-id="d555f-155">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="d555f-156">Dans cet exemple, 50 000 entrées de 5 journaux système sont récupérées sur un ordinateur local Windows :</span><span class="sxs-lookup"><span data-stu-id="d555f-156">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="d555f-157">Le paramètre **Parallèle** spécifie le bloc de script exécuté en parallèle pour chaque nom du journal d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d555f-157">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="d555f-158">Le nouveau paramètre **ThrottleLimit** limite le nombre de blocs de scripts exécutés en parallèle à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="d555f-158">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="d555f-159">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="d555f-159">The default is 5.</span></span>

<span data-ttu-id="d555f-160">Utilisez la variable `$_` pour représenter l'objet d’entrée actuel dans le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="d555f-160">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="d555f-161">Utilisez l’étendue `$using:` pour transférer des références de variable vers le bloc de script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d555f-161">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="d555f-162">Pour plus d’informations sur [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-162">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="d555f-163">Opérateur ternaire</span><span class="sxs-lookup"><span data-stu-id="d555f-163">Ternary operator</span></span>

<span data-ttu-id="d555f-164">PowerShell 7.0 introduit un opérateur ternaire qui se comporte comme une instruction `if-else` simplifiée.</span><span class="sxs-lookup"><span data-stu-id="d555f-164">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="d555f-165">L’opérateur ternaire de PowerShell est étroitement modélisé à partir de la syntaxe C# de l’opérateur ternaire :</span><span class="sxs-lookup"><span data-stu-id="d555f-165">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="d555f-166">L’expression de condition est toujours évaluée et son résultat est converti en **booléenne** pour déterminer la prochaine branche à évaluer :</span><span class="sxs-lookup"><span data-stu-id="d555f-166">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="d555f-167">L’expression `<if-true>` est exécutée si l’expression `<condition>` a la valeur true</span><span class="sxs-lookup"><span data-stu-id="d555f-167">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="d555f-168">L’expression `<if-false>` est exécutée si l’expression `<condition>` a la valeur false</span><span class="sxs-lookup"><span data-stu-id="d555f-168">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="d555f-169">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d555f-169">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="d555f-170">Dans cet exemple, si le chemin existe, **Le chemin existe** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d555f-170">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="d555f-171">Si le chemin n’existe pas, **Chemin introuvable** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d555f-171">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="d555f-172">Pour plus d’informations [À propos de Si](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-172">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="d555f-173">Opérateurs de chaîne de pipeline</span><span class="sxs-lookup"><span data-stu-id="d555f-173">Pipeline chain operators</span></span>

<span data-ttu-id="d555f-174">PowerShell 7 implémente les opérateurs `&&` et `||` pour attacher des pipelines de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="d555f-174">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="d555f-175">Ces opérateurs sont connus dans PowerShell en tant qu’« opérateurs de chaîne de pipeline » et sont similaires à des listes AND et OR dans des interpréteurs de commandes tels que **Bash** et **Zsh**, de même que des symboles de traitement conditionnel dans l’interface de commande Windows (**cmd.exe**).</span><span class="sxs-lookup"><span data-stu-id="d555f-175">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="d555f-176">L’opérateur `&&` exécute le pipeline droit si l’exécution du pipeline gauche a réussi.</span><span class="sxs-lookup"><span data-stu-id="d555f-176">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="d555f-177">Inversement, l’opérateur `||` exécute le pipeline droit si l’exécution du pipeline gauche a échoué.</span><span class="sxs-lookup"><span data-stu-id="d555f-177">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-178">Ces opérateurs utilisent les variables `$?` et `$LASTEXITCODE` pour déterminer si un pipeline a échoué.</span><span class="sxs-lookup"><span data-stu-id="d555f-178">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="d555f-179">Cela vous permet de les utiliser avec des commandes natives, et pas seulement avec des cmdlet ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="d555f-179">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="d555f-180">Ici, la première commande réussit et la deuxième commande est exécutée :</span><span class="sxs-lookup"><span data-stu-id="d555f-180">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="d555f-181">Ici, la première commande échoue et la deuxième commande n’est pas exécutée :</span><span class="sxs-lookup"><span data-stu-id="d555f-181">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="d555f-182">Ici, la première commande réussit, la deuxième commande n’est pas exécutée :</span><span class="sxs-lookup"><span data-stu-id="d555f-182">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="d555f-183">Ici, la première commande échoue, donc la deuxième commande est exécutée :</span><span class="sxs-lookup"><span data-stu-id="d555f-183">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="d555f-184">Pour plus d'informations [À propos des opérateurs de chaîne de pipeline](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-184">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="d555f-185">Coalesence Null, assignation et opérateurs conditionnels</span><span class="sxs-lookup"><span data-stu-id="d555f-185">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="d555f-186">PowerShell 7 inclut l’opérateur de coalescence Null `??`, l’assignation conditionnelle Null `??=` et les opérateurs d’accès conditionnel des membres `?.` et `?[]`.</span><span class="sxs-lookup"><span data-stu-id="d555f-186">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="d555f-187">Opérateur de coalescence Null ??</span><span class="sxs-lookup"><span data-stu-id="d555f-187">Null-coalescing Operator ??</span></span>

<span data-ttu-id="d555f-188">L’opérateur de coalescence Null `??` retourne la valeur de son opérande gauche s’il n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="d555f-188">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="d555f-189">Dans le cas contraire, il évalue l’opérande droit et retourne son résultat.</span><span class="sxs-lookup"><span data-stu-id="d555f-189">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="d555f-190">L’opérateur `??` n’évalue pas son opérande droit si l’opérande gauche a la valeur non Null.</span><span class="sxs-lookup"><span data-stu-id="d555f-190">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="d555f-191">Dans l’exemple suivant, l’opérande droit n’est pas évalué :</span><span class="sxs-lookup"><span data-stu-id="d555f-191">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="d555f-192">Opérateur d’assignation conditionnelle Null ??=</span><span class="sxs-lookup"><span data-stu-id="d555f-192">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="d555f-193">L’opérateur d’assignation conditionnelle Null `??=` assigne la valeur de son opérande droit à son opérande gauche uniquement si l’opérande gauche a la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="d555f-193">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="d555f-194">L’opérateur `??=` n’évalue pas son opérande droit si l’opérande gauche a la valeur non null.</span><span class="sxs-lookup"><span data-stu-id="d555f-194">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="d555f-195">Dans l’exemple suivant, l’opérande droit n’est pas évalué :</span><span class="sxs-lookup"><span data-stu-id="d555f-195">In the following example, the right-hand operand is not evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="d555f-196">Opérateurs d’accès conditionnel des membres Null ?.</span><span class="sxs-lookup"><span data-stu-id="d555f-196">Null conditional member access operators ?.</span></span> <span data-ttu-id="d555f-197">et ?[] (Expérimental)</span><span class="sxs-lookup"><span data-stu-id="d555f-197">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-198">Il s’agit d’une fonctionnalité expérimentale nommée **PSNullConditionalOperators**.</span><span class="sxs-lookup"><span data-stu-id="d555f-198">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="d555f-199">En savoir plus [À Propos des fonctionnalités expérimentales](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-199">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="d555f-200">Un opérateur conditionnel Null n’autorise les membres, `?.`, ou les éléments, `?[]`, à accéder à son opérande que si cet opérande a la valeur non Null ; sinon, il retourne la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="d555f-200">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-201">Étant donné que PowerShell permet à `?` de faire partie du nom de la variable, la spécification formelle du nom de la variable est requise pour l’utilisation de ces opérateurs.</span><span class="sxs-lookup"><span data-stu-id="d555f-201">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="d555f-202">Il est donc nécessaire d’utiliser `{}` autour des noms de variables comme `${a}` ou lorsque `?` fait partie du nom de la variable `${a?}`.</span><span class="sxs-lookup"><span data-stu-id="d555f-202">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="d555f-203">Dans l’exemple suivant, la valeur de la propriété de membre **État** est retournée :</span><span class="sxs-lookup"><span data-stu-id="d555f-203">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="d555f-204">L’exemple suivant retourne la valeur Null, sans essayer d’accéder au nom du membre **État** :</span><span class="sxs-lookup"><span data-stu-id="d555f-204">The following example returns null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="d555f-205">De même, avec `?[]`, la valeur de l’élément est retournée :</span><span class="sxs-lookup"><span data-stu-id="d555f-205">Similarly, using `?[]`, the value of the element is returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="d555f-206">Et lorsque l’opérande a la valeur Null, l’élément n’est pas accessible et la valeur Null est retournée :</span><span class="sxs-lookup"><span data-stu-id="d555f-206">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="d555f-207">Pour plus d’informations [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-207">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="d555f-208">Nouvelle vue ConciseView et cmdlet Get-Error</span><span class="sxs-lookup"><span data-stu-id="d555f-208">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="d555f-209">PowerShell 7.0 optimise l’affichage des messages d’erreur pour améliorer la lisibilité des erreurs de script et interactives avec un nouvel affichage par défaut **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="d555f-209">PowerShell 7.0 enhances the display of error messages to improve the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="d555f-210">Les affichages peuvent être sélectionnées par l’utilisateur via la variable de préférence `$ErrorView`.</span><span class="sxs-lookup"><span data-stu-id="d555f-210">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="d555f-211">Avec **ConciseView**, si une erreur ne provient pas d’un script ou d’un analyseur, le message d’erreur a une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="d555f-211">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="d555f-212">Si l’erreur se produit pendant l’exécution du script ou s’il s’agit d’une erreur d’analyse, PowerShell retourne un message d’erreur de plusieurs lignes contenant l’erreur, un pointeur et un message d’erreur qui indique l’emplacement de l’erreur dans cette ligne.</span><span class="sxs-lookup"><span data-stu-id="d555f-212">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="d555f-213">Si le terminal ne prend pas en charge les séquences d’échappement de couleur ANSI (VT100), les couleurs ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="d555f-213">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![Affichage d’erreur à partir d’un script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="d555f-215">L’affichage par défaut dans PowerShell 7 est **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="d555f-215">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="d555f-216">L’affichage par défaut précédent était **NormalView** et vous pouvez le sélectionner en définissant la variable de préférence `$ErrorView`.</span><span class="sxs-lookup"><span data-stu-id="d555f-216">The previous default view was **NormalView** and you can select thisby setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="d555f-217">Une nouvelle propriété **ErrorAccentColor** est ajoutée à `$Host.PrivateData` pour prendre en charge la modification de la couleur d’accentuation du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d555f-217">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="d555f-218">Une nouvelle cmdlet `Get-Error` fournit un affichage détaillé de l’erreur complète si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="d555f-218">A new cmdlet `Get-Error` provides a complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="d555f-219">Par défaut, la cmdlet affiche les détails complets, notamment les exceptions internes, de la dernière erreur qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d555f-219">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Afficher à partir de la Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="d555f-221">La cmdlet `Get-Error` prend en charge l’entrée du pipeline à l’aide de la variable intégrée `$Error`.</span><span class="sxs-lookup"><span data-stu-id="d555f-221">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="d555f-222">`Get-Error` affiche toutes les erreurs communiquées.</span><span class="sxs-lookup"><span data-stu-id="d555f-222">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="d555f-223">La cmdlet `Get-Error` prend en charge le paramètre **le plus récent**, ce qui vous permet de spécifier le nombre d’erreurs de la session active que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="d555f-223">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="d555f-224">Pour plus d’informations sur [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-224">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="d555f-225">Notification en cas de nouvelle version</span><span class="sxs-lookup"><span data-stu-id="d555f-225">New version notification</span></span>

<span data-ttu-id="d555f-226">PowerShell 7 utilise des notifications de mise à jour pour avertir les utilisateurs de l’existence de mises à jour de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d555f-226">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="d555f-227">Une fois par jour, PowerShell interroge un service en ligne pour déterminer si une version plus récente est disponible.</span><span class="sxs-lookup"><span data-stu-id="d555f-227">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-228">La vérification des mises à jour a lieu pendant la première session sur une période donnée de 24 heures.</span><span class="sxs-lookup"><span data-stu-id="d555f-228">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="d555f-229">Pour des raisons de performances, la vérification des mises à jour démarre 3 secondes après le début de la session.</span><span class="sxs-lookup"><span data-stu-id="d555f-229">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="d555f-230">La notification s’affiche uniquement au début des sessions suivantes.</span><span class="sxs-lookup"><span data-stu-id="d555f-230">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="d555f-231">Par défaut, PowerShell s’abonne à l’un des deux canaux de notification différents en fonction de sa version/branche.</span><span class="sxs-lookup"><span data-stu-id="d555f-231">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="d555f-232">Les versions de PowerShell prises en charge généralement disponibles ne retournent de notifications que pour les versions mises à jour en disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="d555f-232">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="d555f-233">La préversion et la version finale (RC) informent des mises à jour de la préversion, de la version finale (RC) et de la version en disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="d555f-233">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="d555f-234">Le comportement de notification de mise à jour peut être modifié à l’aide de la variable d’environnement `$Env:POWERSHELL_UPDATECHECK`.</span><span class="sxs-lookup"><span data-stu-id="d555f-234">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="d555f-235">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="d555f-235">The following values are supported:</span></span>

- <span data-ttu-id="d555f-236">**Par défaut** revient à ne pas définir `$Env:POWERSHELL_UPDATECHECK`</span><span class="sxs-lookup"><span data-stu-id="d555f-236">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="d555f-237">Les versions en disponibilité générale (GA) informent des mises à jour des versions GA</span><span class="sxs-lookup"><span data-stu-id="d555f-237">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="d555f-238">La préversion/les versions finales (RC) informent des mises à jour des versions en disponibilité générale (GA) et des préversions.</span><span class="sxs-lookup"><span data-stu-id="d555f-238">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="d555f-239">**Désactiver** désactive la fonctionnalité de notification de mise à jour</span><span class="sxs-lookup"><span data-stu-id="d555f-239">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="d555f-240">**LTS** signale uniquement les mises à jour des versions GA LTS (Long-Term-Servicing)</span><span class="sxs-lookup"><span data-stu-id="d555f-240">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-241">La variable d’environnement `$Env:POWERSHELL_UPDATECHECK` n’existe pas tant qu’elle n’est pas définie pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="d555f-241">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="d555f-242">Pour définir la notification de version pour les versions de `LTS` uniquement :</span><span class="sxs-lookup"><span data-stu-id="d555f-242">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="d555f-243">Pour définir la notification de version pour le comportement `Default` uniquement :</span><span class="sxs-lookup"><span data-stu-id="d555f-243">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="d555f-244">Pour plus d'informations [À propos des notifications de mise à jour](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-244">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="d555f-245">Nouvelle prise en charge des ressources DSC avec Invoke-DSCResource (expérimental)</span><span class="sxs-lookup"><span data-stu-id="d555f-245">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="d555f-246">Il s’agit d’une fonctionnalité expérimentale nommée **PSDesiredStateConfiguration.InvokeDscResource**.</span><span class="sxs-lookup"><span data-stu-id="d555f-246">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="d555f-247">En savoir plus [À Propos des fonctionnalités expérimentales](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-247">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="d555f-248">La cmdlet `Invoke-DscResource` exécute une méthode d’une ressource Desired State Configuration (DSC) PowerShell spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d555f-248">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="d555f-249">Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration.</span><span class="sxs-lookup"><span data-stu-id="d555f-249">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="d555f-250">À l’aide de cette cmdlet, les produits de gestion de la configuration peuvent gérer Windows ou Linux à l’aide de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="d555f-250">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="d555f-251">Cette cmdlet de commande permet également de déboguer des ressources lorsque le moteur DSC s’exécute avec le débogage activé.</span><span class="sxs-lookup"><span data-stu-id="d555f-251">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="d555f-252">Cette commande appelle la méthode **Set** d’une ressource nommée **WindowsProcess** et fournit les propriétés obligatoires **Path** et **Arguments** pour démarrer le processus Windows spécifié.</span><span class="sxs-lookup"><span data-stu-id="d555f-252">This command invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

<span data-ttu-id="d555f-253">Pour plus d’informations sur [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="d555f-253">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="d555f-254">Dernières modifications et améliorations</span><span class="sxs-lookup"><span data-stu-id="d555f-254">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="d555f-255">Dernières modifications</span><span class="sxs-lookup"><span data-stu-id="d555f-255">Breaking Changes</span></span>

- <span data-ttu-id="d555f-256">Prise en charge de LTS et des canaux par défaut par la notification de mise à jour (#11132)</span><span class="sxs-lookup"><span data-stu-id="d555f-256">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="d555f-257">Mise à jour de Test-Connection pour qu’elle fonctionne de façon plus similaire à Windows PowerShell (#10697) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-257">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-258">Preserve $?</span><span class="sxs-lookup"><span data-stu-id="d555f-258">Preserve $?</span></span> <span data-ttu-id="d555f-259">pour ParenExpression, SubExpression et ArrayExpression (#11040)</span><span class="sxs-lookup"><span data-stu-id="d555f-259">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="d555f-260">Transformation du répertoire de travail en répertoire actuel dans Start-Job (#10920) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-260">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-261">Reflet cohérent par $PSCulturedes modifications de culture dans la session (#10138) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-261">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="d555f-262">Mises à jour et correctifs du moteur</span><span class="sxs-lookup"><span data-stu-id="d555f-262">Engine Updates and Fixes</span></span>

- <span data-ttu-id="d555f-263">Améliorations des API de point d’arrêt pour les scénarios distants (#11312)</span><span class="sxs-lookup"><span data-stu-id="d555f-263">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="d555f-264">Correction de la fuite de définition de classe PowerShell dans une autre instance d’exécution (#11273)</span><span class="sxs-lookup"><span data-stu-id="d555f-264">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="d555f-265">Correction d’une régression dans la mise en forme provoquée par la primitive FirstOrDefault ajoutée à 7.0.0-Preview1 (#11258)</span><span class="sxs-lookup"><span data-stu-id="d555f-265">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="d555f-266">Modules Microsoft supplémentaires à suivre dans la télémétrie PS7 (#10751)</span><span class="sxs-lookup"><span data-stu-id="d555f-266">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="d555f-267">Transformation des fonctionnalités approuvées en fonctionnalités non expérimentales (#11303)</span><span class="sxs-lookup"><span data-stu-id="d555f-267">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="d555f-268">Mise à jour de ConciseView pour utiliser TargetObject le cas échéant (#11075)</span><span class="sxs-lookup"><span data-stu-id="d555f-268">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="d555f-269">Correction de NullReferenceException dans les méthodes publiques CompletionCompleters (#11274)</span><span class="sxs-lookup"><span data-stu-id="d555f-269">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="d555f-270">Correction de la vérification de l’état du cloisonnement de threads sur les plateformes non-Windows (#11301)</span><span class="sxs-lookup"><span data-stu-id="d555f-270">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="d555f-271">Mise à jour du paramètre PSModulePath pour concaténer les variables d’environnement du processus et de l’ordinateur (#11276)</span><span class="sxs-lookup"><span data-stu-id="d555f-271">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="d555f-272">Passage de .NET Core à 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="d555f-272">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="d555f-273">Correction de la détection de $PSHOME devant $env:PATH (#11141)</span><span class="sxs-lookup"><span data-stu-id="d555f-273">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="d555f-274">Autorisation pour pwsh d’hériter de $env:PSModulePath et d’activer powershell.exe pour démarrer correctement (#11057)</span><span class="sxs-lookup"><span data-stu-id="d555f-274">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="d555f-275">Passage à .NET Core 3.1 préversion 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="d555f-275">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="d555f-276">Refactorisation des vérifications d’étiquettes d’analyse dans le fournisseur du système de fichiers (#10431) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-276">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-277">Remplacement de CR et de la nouvelle ligne par un caractère 0x23CE dans la journalisation des scripts (#10616)</span><span class="sxs-lookup"><span data-stu-id="d555f-277">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="d555f-278">Correction d’une fuite de ressources en annulant l’inscription du gestionnaire d’événements dans AppDomain.CurrentDomain.ProcessExit (#10626)</span><span class="sxs-lookup"><span data-stu-id="d555f-278">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="d555f-279">Ajout de la prise en charge à ActionPreference.Break pour s’arrêter dans le débogueur lorsque des messages de débogage, d’erreur, d’information, de progression, de commentaires ou d’avertissement sont générés (#8205) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-279">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-280">Activation du démarrage des compléments du panneau de configuration dans PowerShell Core sans spécifier une extension .CPL.</span><span class="sxs-lookup"><span data-stu-id="d555f-280">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="d555f-281">(#9828)</span><span class="sxs-lookup"><span data-stu-id="d555f-281">(#9828)</span></span>
- <span data-ttu-id="d555f-282">Prise en charge des nombres négatifs dans l’opérateur -split (#8960) (Merci @ece-jacob-scott !)</span><span class="sxs-lookup"><span data-stu-id="d555f-282">Support negative numbers in -split operator (#8960) (Thanks @ece-jacob-scott!)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="d555f-283">Mises à jour et correctifs d’applets de commande générales</span><span class="sxs-lookup"><span data-stu-id="d555f-283">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="d555f-284">Correction du problème sur Raspbian pour la définition de la date des modifications de fichier dans la fonctionnalité expérimentale UnixStat (#11313)</span><span class="sxs-lookup"><span data-stu-id="d555f-284">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="d555f-285">Ajout de -AsPlainText à ConvertFrom-SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="d555f-285">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="d555f-286">Vérification de la version de WindowsPS ajoutée pour WinCompat (#11148)</span><span class="sxs-lookup"><span data-stu-id="d555f-286">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="d555f-287">Correction des rapports d’erreur dans certains scénarios WinCompat (#11259)</span><span class="sxs-lookup"><span data-stu-id="d555f-287">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="d555f-288">Ajout d’un programme de résolution binaire natif (#11032) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-288">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-289">Mise à jour du calcul de la largeur de char pour respecter correctement les chars CJK (#11262)</span><span class="sxs-lookup"><span data-stu-id="d555f-289">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="d555f-290">Ajout d’Unblock-File pour macOS (#11137)</span><span class="sxs-lookup"><span data-stu-id="d555f-290">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="d555f-291">Correction de la régression dans Get-PSCallStack (#11210) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-291">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-292">Suppression du chargement automatique du module ScheduledJob lors de l’utilisation de cmdlets de tâches (#11194)</span><span class="sxs-lookup"><span data-stu-id="d555f-292">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="d555f-293">Ajout d’OutputType à la cmdlet Get-Error et conservation du nom de type (#10856)</span><span class="sxs-lookup"><span data-stu-id="d555f-293">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="d555f-294">Correction de la référence null dans la propriété SupportsVirtualTerminal (#11105)</span><span class="sxs-lookup"><span data-stu-id="d555f-294">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="d555f-295">Ajout de la limite d’enregistrement dans Get-WinEvent (#10648) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-295">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-296">Correction du runtime de telle manière que StopUpstreamCommandsException ne soit pas rempli dans -ErrorVariable (#10840)</span><span class="sxs-lookup"><span data-stu-id="d555f-296">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="d555f-297">Définition de l’encodage de sortie sur [console]::OutputEncoding pour les commandes natives (#10824)</span><span class="sxs-lookup"><span data-stu-id="d555f-297">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="d555f-298">Prise en charge des blocs de code multilignes dans des exemples (#10776) (Merci @Greg-Smulko !)</span><span class="sxs-lookup"><span data-stu-id="d555f-298">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="d555f-299">Ajout d’un paramètre de culture à la cmdlet Select-String (#10943) (Merci @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="d555f-299">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-300">Correction du chemin du répertoire de Start-Job avec la barre oblique inverse de fin (#11041)</span><span class="sxs-lookup"><span data-stu-id="d555f-300">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="d555f-301">ConvertFrom-Json : Désencapsulage des collections par défaut (#10861) (Merci @danstur !)</span><span class="sxs-lookup"><span data-stu-id="d555f-301">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="d555f-302">Utilisation de la table de hachage pour la cmdlet Group-Object avec les commutateurs -CaseSensitive et -AsHashtable (#11030) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-302">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-303">Gestion d’exception en cas d’échec de l’énumération des fichiers lors de la reconstruction du chemin pour obtenir une casse correcte (#11014)</span><span class="sxs-lookup"><span data-stu-id="d555f-303">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="d555f-304">Correction de ConciseView pour afficher l’activité au lieu de myCommand (#11007)</span><span class="sxs-lookup"><span data-stu-id="d555f-304">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="d555f-305">Autorisation de cmdlets web d’ignorer les états d’erreur HTTP (#10466) (Merci @vdamewood !)</span><span class="sxs-lookup"><span data-stu-id="d555f-305">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="d555f-306">Correction de la canalisation de plusieurs CommandInfo vers Get-Command (#10929)</span><span class="sxs-lookup"><span data-stu-id="d555f-306">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="d555f-307">Rajout de l’applet de commande pour Windows (#10933)</span><span class="sxs-lookup"><span data-stu-id="d555f-307">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="d555f-308">Traitement de [AutomationNull]::Value et [NullString]::Value en tant que $null par ConvertTo-JSON (#10957)</span><span class="sxs-lookup"><span data-stu-id="d555f-308">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="d555f-309">Suppression des crochets de l’adresse ipv6 pour la communication à distance SSH (#10968)</span><span class="sxs-lookup"><span data-stu-id="d555f-309">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="d555f-310">Correction d’incident si la commande envoyée à pwsh est simplement un espace blanc (#10977)</span><span class="sxs-lookup"><span data-stu-id="d555f-310">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="d555f-311">Ajout de Get-Clipboard et Set-Clipboard multiplateformes (#10340)</span><span class="sxs-lookup"><span data-stu-id="d555f-311">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="d555f-312">Correction du paramètre du chemin d’origine de l’objet système de fichiers pour qu’il n’ait pas de barre oblique de fin supplémentaire (#10959)</span><span class="sxs-lookup"><span data-stu-id="d555f-312">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="d555f-313">Prise en charge de $Null pour ConvertTo-Json (#10947)</span><span class="sxs-lookup"><span data-stu-id="d555f-313">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="d555f-314">Rajout de la commande Out-Printer sur Windows (#10906)</span><span class="sxs-lookup"><span data-stu-id="d555f-314">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="d555f-315">Correction de Start-Job-WorkingDirectory avec un espace blanc (#10951)</span><span class="sxs-lookup"><span data-stu-id="d555f-315">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="d555f-316">Retourne la valeur par défaut lors de l’obtention de Null pour un paramètre dans PSConfiguration.cs (#10963) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-316">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-317">Gestion de l’exception d’E/S comme étant sans fin d’exécution (#10950)</span><span class="sxs-lookup"><span data-stu-id="d555f-317">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="d555f-318">Ajout d’un assembly GraphicalHost pour activer Out-GridView, Show-Command et Get-Help-ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="d555f-318">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="d555f-319">Prise de ComputerName via pipeline dans Get-HotFix (#10852) (Merci @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="d555f-319">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="d555f-320">Correction de la saisie semi-automatique des paramètres via la touche Tab pour afficher les paramètres communs disponibles (#10850)</span><span class="sxs-lookup"><span data-stu-id="d555f-320">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="d555f-321">Correction de GetCorrectCasedPath() pour commencer par vérifier si des entrées de fichier système sont retournées avant d’appeler First() (#10930)</span><span class="sxs-lookup"><span data-stu-id="d555f-321">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="d555f-322">Transformation du répertoire de travail en répertoire actuel dans Start-Job (#10920) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-322">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-323">Modification de TabExpansion2 pour ne pas demander -CursorColumn et traitement en tant que $InputScript.Length (#10849)</span><span class="sxs-lookup"><span data-stu-id="d555f-323">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="d555f-324">Gestion au cas où l’hôte ne peut pas retourner des lignes ou des colonnes d’écran (#10938)</span><span class="sxs-lookup"><span data-stu-id="d555f-324">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="d555f-325">Correction de l’utilisation des couleurs d’accentuation pour les hôtes qui ne les prennent pas en charge (#10937)</span><span class="sxs-lookup"><span data-stu-id="d555f-325">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="d555f-326">Rajout de la commande Update-List (#10922)</span><span class="sxs-lookup"><span data-stu-id="d555f-326">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="d555f-327">Mise à jour de l’ID FWLink pour Clear-RecycleBin (#10925)</span><span class="sxs-lookup"><span data-stu-id="d555f-327">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="d555f-328">Lors de la saisie semi-automatique via la touche Tab, ignorer le fichier si la lecture de ses attributs est impossible (#10910)</span><span class="sxs-lookup"><span data-stu-id="d555f-328">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="d555f-329">Rajout de Clear-RecycleBin pour Windows (#10909)</span><span class="sxs-lookup"><span data-stu-id="d555f-329">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="d555f-330">Ajout de `$env:__SuppressAnsiEscapeSequences` pour contrôler s’il faut avoir une séquence d’échappement VT dans la sortie (#10814)</span><span class="sxs-lookup"><span data-stu-id="d555f-330">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="d555f-331">Ajout du paramètre NoEmphasize pour colorier la sortie Select-String (#8963) (Merci @derek-xia !)</span><span class="sxs-lookup"><span data-stu-id="d555f-331">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="d555f-332">Rajout de la cmdlet Get-HotFix (#10740)</span><span class="sxs-lookup"><span data-stu-id="d555f-332">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="d555f-333">Add-Type rendu utilisable dans les applications qui hébergent PowerShell (#10587)</span><span class="sxs-lookup"><span data-stu-id="d555f-333">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="d555f-334">Utilisation d’un ordre d’évaluation plus efficace dans LanguagePrimitives.IsNullLike() (#10781) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-334">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-335">Amélioration de la gestion de l’entrée redirigée de collection mixte et des flux d’entrée redirigés au Format-Hex (#8674) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-335">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-336">Utilisation de la conversion de type dans les tables de hachage SSHConnection quand la valeur ne correspond pas au type attendu (#10720) (Merci @SeeminglyScience !)</span><span class="sxs-lookup"><span data-stu-id="d555f-336">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="d555f-337">Correction du comportement de Get-Content -ReadCount 0 quand -TotalCount est défini (#10749) (Merci @eugenesmlv !)</span><span class="sxs-lookup"><span data-stu-id="d555f-337">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="d555f-338">Message d’erreur d’accès de reformulation refusé dans Get-WinEvent (#10639) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-338">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-339">Activation de la saisie semi-automatique via la touche Tab pour l’affectation de variable qui est une énumération ou un type avec restriction (#10646)</span><span class="sxs-lookup"><span data-stu-id="d555f-339">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="d555f-340">Suppression de la propriété de communication à distance SourceLength inutilisée provoquant des problèmes de mise en forme (#10765)</span><span class="sxs-lookup"><span data-stu-id="d555f-340">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="d555f-341">Ajout du paramètre -Delimiter à ConvertFrom-StringData (#10665) (Merci @steviecoaster !)</span><span class="sxs-lookup"><span data-stu-id="d555f-341">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="d555f-342">Ajout du paramètre de position pour ScriptBlock lorsqu’Invoke-Command est utilisé avec SSH (#10721) (Merci @machgo !)</span><span class="sxs-lookup"><span data-stu-id="d555f-342">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="d555f-343">Affichage d’informations de contexte de ligne s’il y a plusieurs lignes, mais pas de nom de script pour ConciseView (#10746)</span><span class="sxs-lookup"><span data-stu-id="d555f-343">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="d555f-344">Ajout de la prise en charge de \\wsl$\ paths au fournisseur de système de fichiers (#10674)</span><span class="sxs-lookup"><span data-stu-id="d555f-344">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="d555f-345">Ajout du jeton manquant pour TokenKind.QuestionMark dans l’analyseur (#10706)</span><span class="sxs-lookup"><span data-stu-id="d555f-345">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="d555f-346">Définition du répertoire de travail actuel de chaque script d’exécution ForEach-Object-Parallel au même emplacement que le script appelant.</span><span class="sxs-lookup"><span data-stu-id="d555f-346">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="d555f-347">(#10672)</span><span class="sxs-lookup"><span data-stu-id="d555f-347">(#10672)</span></span>
- <span data-ttu-id="d555f-348">Remplacement d’api-ms-win-core-file-l1-2-2.dll par Kernell32.dll pour les API FindFirstStreamW et FindNextStreamW (#10680) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-348">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-349">Adaptation du script d’aide à la mise en forme pour une meilleure tolérance StrictMode (#10563)</span><span class="sxs-lookup"><span data-stu-id="d555f-349">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="d555f-350">Ajout du paramètre -SecurityDescriptorSDDL à New-Service (#10483) (Merci @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="d555f-350">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="d555f-351">Suppression de la sortie d’information, consolidation de l’utilisation du test ping dans Test-Connection (#10478) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-351">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-352">Lecture des points d’analyse spéciaux sans y accéder (#10662) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-352">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-353">Sortie directe Clear-Host sur le terminal (#10681) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-353">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-354">Rajout d’une nouvelle ligne pour le regroupement avec Format-Table et -Property (#10653)</span><span class="sxs-lookup"><span data-stu-id="d555f-354">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="d555f-355">Suppression de [ValidateNotNullOrEmpty] de -InputObject sur Get-Random pour autoriser une chaîne vide (#10644)</span><span class="sxs-lookup"><span data-stu-id="d555f-355">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="d555f-356">Algorithme de distance de la chaîne système rendu insensible à la casse (#10549) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-356">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-357">Correction de l’exception de référence Null dans le traitement de l’entrée ForEach-Object-Parallel (#10577)</span><span class="sxs-lookup"><span data-stu-id="d555f-357">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="d555f-358">Ajout de définitions de stratégie de groupe PowerShell Core (#10468)</span><span class="sxs-lookup"><span data-stu-id="d555f-358">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="d555f-359">Mise à jour de l’hôte de la console pour prendre en charge les séquences de contrôle XTPUSHSGR/XTPOPSGR VT utilisées dans les scénarios de composabilité.</span><span class="sxs-lookup"><span data-stu-id="d555f-359">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="d555f-360">(#10208)</span><span class="sxs-lookup"><span data-stu-id="d555f-360">(#10208)</span></span>
- <span data-ttu-id="d555f-361">Ajout du paramètre WorkingDirectory à Start-Job (#10324) (Merci @davinci26 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-361">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="d555f-362">Suppression du gestionnaire d’événements à l’origine de la réplication erronée des modifications de point d’arrêt dans le débogueur de l’instance d’exécution de l’hôte (#10503) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-362">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-363">Remplacement d’api-ms-win-core-job-12-1-0.dll par Kernell32.dll dans l’API Microsoft.PowerShell.Commands.NativeMethods P/Invoke (#10417) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-363">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-364">Correction de la sortie incorrecte pour New-Service dans l’affectation de variable et de-OutVariable (#10444) (Merci @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="d555f-364">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="d555f-365">Résolution des problèmes d’outils globaux autour du code de sortie, des paramètres de ligne de commande et du chemin avec des espaces (#10461)</span><span class="sxs-lookup"><span data-stu-id="d555f-365">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="d555f-366">Correction de la récursivité dans OneDrive : modification de FindFirstFileEx() pour utiliser le type SafeFindHandle (#10405)</span><span class="sxs-lookup"><span data-stu-id="d555f-366">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="d555f-367">Chargement automatique de PSReadLine sur Windows ignoré si le lecteur d’écran NVDA est actif (#10385)</span><span class="sxs-lookup"><span data-stu-id="d555f-367">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="d555f-368">Passage des versions de module built-with-PowerShell vers 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="d555f-368">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="d555f-369">Ajout de la levée d’une erreur dans Add-Type si un type portant le même nom existe déjà (#9609) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-369">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="d555f-370">Performances</span><span class="sxs-lookup"><span data-stu-id="d555f-370">Performance</span></span>

- <span data-ttu-id="d555f-371">Éviter d’utiliser la fermeture dans Parser.SaveError (#11006)</span><span class="sxs-lookup"><span data-stu-id="d555f-371">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="d555f-372">Amélioration de la mise en cache lors de la création d’instances Regex (#10657) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-372">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-373">Amélioration du traitement des données de type PowerShell intégrées detypes.ps1xml, typesV3.ps1xml et GetEvent.types.ps1xml (#10898)</span><span class="sxs-lookup"><span data-stu-id="d555f-373">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="d555f-374">Mise à jour de PSConfiguration.ReadValueFromFile pour l’accélérer et augmenter l’efficacité de la mémoire (#10839)</span><span class="sxs-lookup"><span data-stu-id="d555f-374">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="d555f-375">Ajout d’améliorations de performances mineures pour l’initialisation de l’instance d’exécution (#10569) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-375">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-376">Accélération de ForEach-Object pour ses scénarios couramment utilisés (#10454) et résolution du problème de performance ForEach-Object-Parallel avec de nombreuses instances d’exécution (#10455)</span><span class="sxs-lookup"><span data-stu-id="d555f-376">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="d555f-377">Nettoyage du code</span><span class="sxs-lookup"><span data-stu-id="d555f-377">Code Cleanup</span></span>

- <span data-ttu-id="d555f-378">Modification du texte des commentaires et des éléments pour respecter les normes Microsoft (#11304)</span><span class="sxs-lookup"><span data-stu-id="d555f-378">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="d555f-379">Problèmes de style de nettoyage dans Compiler.cs (#10368) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-379">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-380">Suppression du convertisseur de type inutilisé pour CommaDelimitedStringCollection (#11000) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-380">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-381">Style de nettoyage dans InitialSessionState.cs (#10865) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-381">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-382">Nettoyage du code pour la classe PSSession (#11001)</span><span class="sxs-lookup"><span data-stu-id="d555f-382">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="d555f-383">Suppression de la fonctionnalité « exécuter Update-Help de Get-Help lorsque Get-Help s’exécute pour la première fois » (#10974)</span><span class="sxs-lookup"><span data-stu-id="d555f-383">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="d555f-384">Résolution des problèmes de style (#10998) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-384">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-385">Nettoyage : utilisez l’alias de type intégré (#10882) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-385">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-386">Suppression de la clé de paramètre inutilisée ConsolePrompting et évitement d’une création de chaîne inutile lors de l’interrogation du paramètre ExecutionPolicy (#10985)</span><span class="sxs-lookup"><span data-stu-id="d555f-386">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="d555f-387">Désactivation du contrôle de notification de mise à jour pour les builds quotidiennes (#10903) (Merci @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="d555f-387">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="d555f-388">Rétablissement de l’API de débogage perdue dans #10338 (#10808)</span><span class="sxs-lookup"><span data-stu-id="d555f-388">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="d555f-389">Suppression de la référence WorkflowJobSourceAdapter qui n’est plus utilisée (#10326) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-389">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-390">Nettoyage des interfaces COM dans le code de liste de raccourcis en résolvant les attributs PreserveSig (#9899) (Merci @weltkante !)</span><span class="sxs-lookup"><span data-stu-id="d555f-390">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="d555f-391">Ajout d’un commentaire décrivant la raison pour laquelle -ia n’est pas l’alias du paramètre commun -InformationAction (#10703) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-391">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-392">Renommage d’InvokeCommandCmdlet.cs en InvokeExpressionCommand.cs (#10659) (Merci @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="d555f-392">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="d555f-393">Ajout des nettoyages de code mineurs relatifs aux notifications de mise à jour (#10698)</span><span class="sxs-lookup"><span data-stu-id="d555f-393">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="d555f-394">Suppression de la logique de flux de travail dépréciée des scripts d’installation de communication à distance (#10320) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-394">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-395">Mise à jour du format d’aide pour utiliser la casse appropriée (#10678) (Merci @tnieto88 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-395">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="d555f-396">Nettoyage des problèmes de style CodeFactor arrivant dans les validations pour le mois dernier (#10591) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-396">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-397">Correction de la faute de frappe dans la description de la fonctionnalité expérimentale PSTernaryOperator (#10586) (Merci @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="d555f-397">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="d555f-398">Convertissement de la valeur d’énumération ActionPreference.Suspend en un État réservé non pris en charge et suppression de la restriction de l’utilisation d’ActionPreference.Ignore dans les variables de préférence (#10317) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-398">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-399">Remplacement d’ArrayList par List\<T> pour obtenir du code plus lisible et plus fiable sans modifier les fonctionnalités (#10333) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-399">Replace ArrayList with List\<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-400">Corrections de style de code dans TestConnectionCommand (#10439) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-400">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-401">Nettoyage d’AutomationEngine et suppression de l’appel de méthode SetSessionStateDrive supplémentaire (#10416) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-401">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-402">Renommage de ParameterSetName par défaut en séparateur pour ConvertTo-Csv et ConvertFrom-Csv (#10425)</span><span class="sxs-lookup"><span data-stu-id="d555f-402">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="d555f-403">Outils</span><span class="sxs-lookup"><span data-stu-id="d555f-403">Tools</span></span>

- <span data-ttu-id="d555f-404">Ajout du paramètre par défaut pour la propriété SDKToUse afin qu’elle soit générée dans VS (#11085)</span><span class="sxs-lookup"><span data-stu-id="d555f-404">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="d555f-405">Install-Powershell.ps1 : Ajout d’un paramètre pour utiliser l’installation MSI (#10921) (Merci @MJECloud !)</span><span class="sxs-lookup"><span data-stu-id="d555f-405">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="d555f-406">Ajout d’exemples de base pour install-PowerShell.ps1 (#10914) (Merci @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="d555f-406">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="d555f-407">Gestion d’une chaîne vide par Install-PowerShellRemoting.ps1 dans le paramètre PowerShellHome (#10526) (Merci @Orca88 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-407">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="d555f-408">Basculement de /etc/lsb-release vers /etc/os-release dans install-powershell.sh (#10773) (Merci @Himura2la !)</span><span class="sxs-lookup"><span data-stu-id="d555f-408">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="d555f-409">Vérification de pwsh.exe et de pwsh dans la version quotidienne sur Windows (#10738) (Merci @centreboard !)</span><span class="sxs-lookup"><span data-stu-id="d555f-409">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="d555f-410">Suppression de l’actionnement inutile dans installpsh-osx.sh (#10752)</span><span class="sxs-lookup"><span data-stu-id="d555f-410">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="d555f-411">Mise à jour d’install-PowerShell.ps1 pour vérifier la build quotidienne déjà installée (#10489)</span><span class="sxs-lookup"><span data-stu-id="d555f-411">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="d555f-412">Tests</span><span class="sxs-lookup"><span data-stu-id="d555f-412">Tests</span></span>

- <span data-ttu-id="d555f-413">Mise en attente du test DSC non fiable (#11131)</span><span class="sxs-lookup"><span data-stu-id="d555f-413">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="d555f-414">Correction du test StringData pour valider correctement les clés de tables de hachage (#10810)</span><span class="sxs-lookup"><span data-stu-id="d555f-414">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="d555f-415">Déchargement des modules de test (#11061) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-415">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-416">Augmentation du temps entre les nouvelles tentatives de test d’URL (#11015)</span><span class="sxs-lookup"><span data-stu-id="d555f-416">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="d555f-417">Mise à jour les tests pour décrire précisément les actions de test.</span><span class="sxs-lookup"><span data-stu-id="d555f-417">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="d555f-418">(#10928) (Merci @romero126 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-418">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="d555f-419">Le test non fiable TestAppDomainProcessExitEvenHandlerNotLeaking est temporairement ignoré (#10827)</span><span class="sxs-lookup"><span data-stu-id="d555f-419">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="d555f-420">Stabilisation du test de fuite du gestionnaire d'événements (#10790)</span><span class="sxs-lookup"><span data-stu-id="d555f-420">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="d555f-421">Synchronisation de la mise en majuscules dans CI YAML (#10767) (Merci @RDIL !)</span><span class="sxs-lookup"><span data-stu-id="d555f-421">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="d555f-422">Ajout d’un test pour la correction de fuite du gestionnaire d'événements (#10768)</span><span class="sxs-lookup"><span data-stu-id="d555f-422">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="d555f-423">Ajout du test Get-ChildItem (#10507) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-423">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-424">Remplacement du langage ambigu des tests du commutateur au paramètre pour garantir la précision (#10666) (Merci @romero126 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-424">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="d555f-425">Ajout d’une vérification expérimentale aux tests ForEach-Object-Parallel (#10354) (Merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="d555f-425">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="d555f-426">Mise à jour des tests de validation Alpine (#10428)</span><span class="sxs-lookup"><span data-stu-id="d555f-426">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="d555f-427">Améliorations des builds et des packages</span><span class="sxs-lookup"><span data-stu-id="d555f-427">Build and Package Improvements</span></span>

- <span data-ttu-id="d555f-428">Correction de la signature de package NuGet pour la génération de packages coordonnés (#11316)</span><span class="sxs-lookup"><span data-stu-id="d555f-428">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="d555f-429">Mise à jour des dépendances de PowerShell Gallery et de NuGet (#11323)</span><span class="sxs-lookup"><span data-stu-id="d555f-429">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="d555f-430">Passage de Microsoft.ApplicationInsights 2.11.0 à 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="d555f-430">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="d555f-431">Passage de Microsoft.CodeAnalysis.CSharp de 3.3.1 à 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="d555f-431">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="d555f-432">Mise à jour des packages pour Debian 10 et 11 (#11236)</span><span class="sxs-lookup"><span data-stu-id="d555f-432">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="d555f-433">Activation des fonctionnalités expérimentales antérieures à la version RC uniquement (#11162)</span><span class="sxs-lookup"><span data-stu-id="d555f-433">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="d555f-434">Mise à jour de la version macOS minimale (#11163)</span><span class="sxs-lookup"><span data-stu-id="d555f-434">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="d555f-435">Passage de NJsonSchema de 10.0.27 à 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="d555f-435">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="d555f-436">Mise à jour des liens dans README.md et metadata.json pour la préversion 5 (#10854)</span><span class="sxs-lookup"><span data-stu-id="d555f-436">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="d555f-437">Sélection des fichiers pour les tests de compatibilité détenus par PowerShell (#10837)</span><span class="sxs-lookup"><span data-stu-id="d555f-437">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="d555f-438">Autorisation de la génération du package win7x86 msix.</span><span class="sxs-lookup"><span data-stu-id="d555f-438">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="d555f-439">(Interne 10515)</span><span class="sxs-lookup"><span data-stu-id="d555f-439">(Internal 10515)</span></span>
- <span data-ttu-id="d555f-440">Autorisation du passage des versions sémantiques à la fonction NormalizeVersion (#11087)</span><span class="sxs-lookup"><span data-stu-id="d555f-440">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="d555f-441">Passage de l’infrastructure .NET Core à la version 3.1-preview.3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="d555f-441">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="d555f-442">Passage de PSReadLine de 2.0.0-beta5 à 2.0.0-beta6 dans/src/Modules (#11078)</span><span class="sxs-lookup"><span data-stu-id="d555f-442">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="d555f-443">Passage de Newtonsoft.Json de 12.0.2 à 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="d555f-443">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="d555f-444">Ajout des packages Debian 10, 11 et CentOS 8 (#11028)</span><span class="sxs-lookup"><span data-stu-id="d555f-444">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="d555f-445">Chargement du fichier Json Build-info avec le champ ReleaseDate (#10986)</span><span class="sxs-lookup"><span data-stu-id="d555f-445">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="d555f-446">Passage de l’infrastructure .NET Core à la version 3.1-preview.2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="d555f-446">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="d555f-447">Activation de la build du package MSIX x86 (#10934)</span><span class="sxs-lookup"><span data-stu-id="d555f-447">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="d555f-448">Mise à jour de l’URL du script d’installation du kit de développement logiciel (SDK) dotnet dans build.psm1 (#10927)</span><span class="sxs-lookup"><span data-stu-id="d555f-448">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="d555f-449">Passage de Markdig.Signed de 0.17.1 à 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="d555f-449">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="d555f-450">Passage de ThreadJob de 2.0.1 à 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="d555f-450">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="d555f-451">Mise à jour du manifeste AppX et du module de packaging pour respecter les exigences du MS Store (#10878)</span><span class="sxs-lookup"><span data-stu-id="d555f-451">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="d555f-452">Mise à jour de la référence de package pour le kit de développement logiciel (SDK) PowerShell vers preview.5 (interne 10295)</span><span class="sxs-lookup"><span data-stu-id="d555f-452">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="d555f-453">Mise à jour de ThirdPartyNotices.txt (#10834)</span><span class="sxs-lookup"><span data-stu-id="d555f-453">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="d555f-454">Passage de Microsoft. PowerShell.Native à 7.0.0-preview.3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="d555f-454">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="d555f-455">Passage de Microsoft.ApplicationInsights 2.10.0 à 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="d555f-455">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="d555f-456">Passage de NJsonSchema de 10.0.24 à 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="d555f-456">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="d555f-457">Ajout de la prise en charge MacPorts au système de build (#10736) (Merci @Lucius-Q-User !)</span><span class="sxs-lookup"><span data-stu-id="d555f-457">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="d555f-458">Passage de PackageManagement de 1.4.4 à 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="d555f-458">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="d555f-459">Passage de NJsonSchema de 10.0.23 à 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="d555f-459">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="d555f-460">Ajout d’une variable d’environnement pour différencier la télémétrie client/serveur dans MSI (#10612)</span><span class="sxs-lookup"><span data-stu-id="d555f-460">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="d555f-461">Passage de PSDesiredStateConfiguration de 2.0.3 à 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="d555f-461">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="d555f-462">Passage de Microsoft.CodeAnalysis.CSharp de 3.2.1 à 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="d555f-462">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="d555f-463">Mise à jour vers .Net Core 3.0 RTM (#10604) (Merci @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="d555f-463">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="d555f-464">Mise à jour du packaging MSIX pour que la version réponde aux exigences du Windows Store (#10588)</span><span class="sxs-lookup"><span data-stu-id="d555f-464">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="d555f-465">Passage de la version PowerShellGet de 2.2 à 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="d555f-465">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="d555f-466">Passage de PackageManagement de 1.4.3 à 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="d555f-466">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="d555f-467">Mise à jour de README.md et de metadata.json vers 7.0.0-preview.4 (interne 10011)</span><span class="sxs-lookup"><span data-stu-id="d555f-467">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="d555f-468">Mise à niveau de la version de .Net Core 3.0 de la préversion 9 à la version finale RC1 (#10552) (Merci @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="d555f-468">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="d555f-469">Correction de la génération de la liste ExperimentalFeature (interne 9996)</span><span class="sxs-lookup"><span data-stu-id="d555f-469">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="d555f-470">Passage de la version de PSReadLine de 2.0.0-beta4 à 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="d555f-470">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="d555f-471">Correction du script de build de version pour définir la balise de mise en production</span><span class="sxs-lookup"><span data-stu-id="d555f-471">Fix release build script to set release tag</span></span>
- <span data-ttu-id="d555f-472">Mise à jour de la version de Microsoft.PowerShell.Native vers 7.0.0-preview.2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="d555f-472">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="d555f-473">Mise à niveau vers Netcoreapp3.0 preview9 (#10484) (Merci @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="d555f-473">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="d555f-474">Assurez-vous que la build coordonnée quotidienne sait qu’il s’agit d’une build quotidienne (#10464)</span><span class="sxs-lookup"><span data-stu-id="d555f-474">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="d555f-475">Mise à jour de la build du package combiné pour publier les builds quotidiennes (#10449)</span><span class="sxs-lookup"><span data-stu-id="d555f-475">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="d555f-476">Suppression de la référence appveyor (#10445) (Merci @RDIL !)</span><span class="sxs-lookup"><span data-stu-id="d555f-476">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="d555f-477">Passage de la version de NJsonSchema de 10.0.22 à 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="d555f-477">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="d555f-478">Suppression de l’effacement du dossier de build Linux-x64, car certaines dépendances pour Alpine en ont besoin (#10407)</span><span class="sxs-lookup"><span data-stu-id="d555f-478">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="d555f-479">Contenu de la documentation et de l'aide</span><span class="sxs-lookup"><span data-stu-id="d555f-479">Documentation and Help Content</span></span>

- <span data-ttu-id="d555f-480">Refactorisation des journaux de modification dans un seul journal par version (#11165)</span><span class="sxs-lookup"><span data-stu-id="d555f-480">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="d555f-481">Correction de FWLinks pour les documents d’aide en ligne de PowerShell 7 (#11071)</span><span class="sxs-lookup"><span data-stu-id="d555f-481">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="d555f-482">Mise à jour de CONTRIBUTING.md (#11096) (Merci @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-482">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="d555f-483">Correction des liens du document d’installation dans README.md (#11083)</span><span class="sxs-lookup"><span data-stu-id="d555f-483">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="d555f-484">Ajout d’exemples au script install-powershell.ps1 (#11024) (Merci @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="d555f-484">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="d555f-485">Correction de l’accentuation de Select-String et d’Import-DscResource dans CHANGELOG.md (#10890)</span><span class="sxs-lookup"><span data-stu-id="d555f-485">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="d555f-486">Suppression du lien obsolète de powershell-beginners-guide.md (#10926)</span><span class="sxs-lookup"><span data-stu-id="d555f-486">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="d555f-487">Fusion des journaux de modification stables et de maintenance (#10527)</span><span class="sxs-lookup"><span data-stu-id="d555f-487">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="d555f-488">Mise à jour de la version .NET utilisée dans les documents de build (#10775) (Merci @Greg-Smulko !)</span><span class="sxs-lookup"><span data-stu-id="d555f-488">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="d555f-489">Remplacez les liens de MSDN par docs.microsoft.com dans powershell-beginners-guide.md (#10778) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="d555f-489">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="d555f-490">Correction du lien de vue d’ensemble DSC rompu (#10702)</span><span class="sxs-lookup"><span data-stu-id="d555f-490">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="d555f-491">Mise à jour de Support_Question.md pour créer un lien vers Stack Overflow comme une autre ressource de la communauté (#10638) (Merci @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="d555f-491">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="d555f-492">Ajout d’une architecture de processeur au modèle de demande de distribution (#10661)</span><span class="sxs-lookup"><span data-stu-id="d555f-492">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="d555f-493">Ajout d’un nouveau livre PowerShell MoL aux documents d’apprentissage PowerShell (#10602)</span><span class="sxs-lookup"><span data-stu-id="d555f-493">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="d555f-494">Mise à jour de README.md et des métadonnées pour les versions v6.1.6 and v6.2.3 (#10523)</span><span class="sxs-lookup"><span data-stu-id="d555f-494">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="d555f-495">Correction d’une faute de frappe dans README.md (#10465) (Merci @vedhasp !)</span><span class="sxs-lookup"><span data-stu-id="d555f-495">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="d555f-496">Ajout d’une référence au module PSKoans de la documentation des ressources de formation (#10369) (Merci @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="d555f-496">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="d555f-497">Mise à jour de README.md et de metadata.json vers 7.0.0-preview.3 (interne 10393)</span><span class="sxs-lookup"><span data-stu-id="d555f-497">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
