---
description: Explique comment rediriger la sortie de PowerShell vers des fichiers texte.
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 2f2081bbfcc2cfc97eaa5a3c2c527cdd9cd61d2c
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040878"
---
# <a name="about-redirection"></a><span data-ttu-id="edbfa-103">À propos de la redirection</span><span class="sxs-lookup"><span data-stu-id="edbfa-103">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="edbfa-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="edbfa-104">Short description</span></span>
<span data-ttu-id="edbfa-105">Explique comment rediriger la sortie de PowerShell vers des fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="edbfa-105">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="edbfa-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="edbfa-106">Long description</span></span>

<span data-ttu-id="edbfa-107">Par défaut, PowerShell envoie la sortie à l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="edbfa-107">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="edbfa-108">Il s’agit généralement de l’application console.</span><span class="sxs-lookup"><span data-stu-id="edbfa-108">Usually this is the console application.</span></span> <span data-ttu-id="edbfa-109">Toutefois, vous pouvez diriger la sortie vers un fichier texte et vous pouvez rediriger la sortie d’erreur vers le flux de sortie normal.</span><span class="sxs-lookup"><span data-stu-id="edbfa-109">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="edbfa-110">Vous pouvez utiliser les méthodes suivantes pour rediriger la sortie :</span><span class="sxs-lookup"><span data-stu-id="edbfa-110">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="edbfa-111">Utilisez l' `Out-File` applet de commande, qui envoie une sortie de commande à un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="edbfa-111">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="edbfa-112">En général, vous utilisez l’applet de commande `Out-File` lorsque vous avez besoin d’utiliser ses paramètres, tels que les `Encoding` paramètres,, `Force` `Width` ou `NoClobber` .</span><span class="sxs-lookup"><span data-stu-id="edbfa-112">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="edbfa-113">Utilisez l' `Tee-Object` applet de commande, qui envoie une sortie de commande à un fichier texte, puis l’envoie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="edbfa-113">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="edbfa-114">Utilisez les opérateurs de redirection PowerShell.</span><span class="sxs-lookup"><span data-stu-id="edbfa-114">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="edbfa-115">L’utilisation de l’opérateur de redirection avec une cible de fichier est fonctionnellement équivalente à la fonctionnalité de canalisation `Out-File` sans aucun paramètre supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="edbfa-115">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="edbfa-116">Pour plus d’informations sur les flux, consultez [about_Output_Streams](about_Output_Streams.md).</span><span class="sxs-lookup"><span data-stu-id="edbfa-116">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="edbfa-117">Flux de sortie redirigés</span><span class="sxs-lookup"><span data-stu-id="edbfa-117">Redirectable output streams</span></span>

<span data-ttu-id="edbfa-118">PowerShell prend en charge la redirection des flux de sortie suivants.</span><span class="sxs-lookup"><span data-stu-id="edbfa-118">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="edbfa-119">Train #</span><span class="sxs-lookup"><span data-stu-id="edbfa-119">Stream #</span></span> |      <span data-ttu-id="edbfa-120">Description</span><span class="sxs-lookup"><span data-stu-id="edbfa-120">Description</span></span>       | <span data-ttu-id="edbfa-121">Introduite dans</span><span class="sxs-lookup"><span data-stu-id="edbfa-121">Introduced in</span></span>  |    <span data-ttu-id="edbfa-122">Écrire l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="edbfa-122">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="edbfa-123">1</span><span class="sxs-lookup"><span data-stu-id="edbfa-123">1</span></span>        | <span data-ttu-id="edbfa-124">**Opération réussie** Train</span><span class="sxs-lookup"><span data-stu-id="edbfa-124">**Success** Stream</span></span>     | <span data-ttu-id="edbfa-125">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-125">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="edbfa-126">2</span><span class="sxs-lookup"><span data-stu-id="edbfa-126">2</span></span>        | <span data-ttu-id="edbfa-127">**Erreur** Train</span><span class="sxs-lookup"><span data-stu-id="edbfa-127">**Error** Stream</span></span>       | <span data-ttu-id="edbfa-128">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-128">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="edbfa-129">3</span><span class="sxs-lookup"><span data-stu-id="edbfa-129">3</span></span>        | <span data-ttu-id="edbfa-130">**Avertissement** Train</span><span class="sxs-lookup"><span data-stu-id="edbfa-130">**Warning** Stream</span></span>     | <span data-ttu-id="edbfa-131">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-131">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="edbfa-132">4</span><span class="sxs-lookup"><span data-stu-id="edbfa-132">4</span></span>        | <span data-ttu-id="edbfa-133">**Commentaires** Train</span><span class="sxs-lookup"><span data-stu-id="edbfa-133">**Verbose** Stream</span></span>     | <span data-ttu-id="edbfa-134">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-134">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="edbfa-135">5</span><span class="sxs-lookup"><span data-stu-id="edbfa-135">5</span></span>        | <span data-ttu-id="edbfa-136">**Débogage** Train</span><span class="sxs-lookup"><span data-stu-id="edbfa-136">**Debug** Stream</span></span>       | <span data-ttu-id="edbfa-137">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-137">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="edbfa-138">6</span><span class="sxs-lookup"><span data-stu-id="edbfa-138">6</span></span>        | <span data-ttu-id="edbfa-139">**Informations** Train</span><span class="sxs-lookup"><span data-stu-id="edbfa-139">**Information** Stream</span></span> | <span data-ttu-id="edbfa-140">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-140">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="edbfa-141">Tous les flux</span><span class="sxs-lookup"><span data-stu-id="edbfa-141">All Streams</span></span>            | <span data-ttu-id="edbfa-142">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="edbfa-142">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="edbfa-143">Il y a également un flux de **progression** dans PowerShell, mais il ne prend pas en charge la redirection.</span><span class="sxs-lookup"><span data-stu-id="edbfa-143">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="edbfa-144">Opérateurs de redirection PowerShell</span><span class="sxs-lookup"><span data-stu-id="edbfa-144">PowerShell redirection operators</span></span>

<span data-ttu-id="edbfa-145">Les opérateurs de redirection PowerShell sont les suivants, où `n` représente le numéro de flux.</span><span class="sxs-lookup"><span data-stu-id="edbfa-145">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="edbfa-146">Le flux de **réussite** ( `1` ) est la valeur par défaut si aucun flux n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="edbfa-146">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="edbfa-147">Opérateur</span><span class="sxs-lookup"><span data-stu-id="edbfa-147">Operator</span></span> |                         <span data-ttu-id="edbfa-148">Description</span><span class="sxs-lookup"><span data-stu-id="edbfa-148">Description</span></span>                         | <span data-ttu-id="edbfa-149">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edbfa-149">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="edbfa-150">Envoie le flux spécifié à un fichier.</span><span class="sxs-lookup"><span data-stu-id="edbfa-150">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="edbfa-151">**Ajoute** le flux spécifié à un fichier.</span><span class="sxs-lookup"><span data-stu-id="edbfa-151">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="edbfa-152">_Redirige_ le flux spécifié vers le flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="edbfa-152">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="edbfa-153">Contrairement à certains shells UNIX, vous pouvez rediriger uniquement les autres flux vers le flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="edbfa-153">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="edbfa-154">Exemples</span><span class="sxs-lookup"><span data-stu-id="edbfa-154">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="edbfa-155">Exemple 1 : rediriger les erreurs et la sortie vers un fichier</span><span class="sxs-lookup"><span data-stu-id="edbfa-155">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="edbfa-156">Cet exemple s’exécute `dir` sur un élément qui sera correctement exécuté, et sur un élément qui génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="edbfa-156">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="edbfa-157">Il utilise `2>&1` pour rediriger le flux d' **Erreurs** vers le flux de **réussite** , et `>` pour envoyer le flux de **réussite** obtenu à un fichier appelé `dir.log`</span><span class="sxs-lookup"><span data-stu-id="edbfa-157">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="edbfa-158">Exemple 2 : envoyer toutes les données de flux de réussite à un fichier</span><span class="sxs-lookup"><span data-stu-id="edbfa-158">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="edbfa-159">Cet exemple envoie toutes les données de flux de **réussite** à un fichier appelé `script.log` .</span><span class="sxs-lookup"><span data-stu-id="edbfa-159">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="edbfa-160">Exemple 3 : envoyer des flux de réussite, d’avertissement et d’erreur à un fichier</span><span class="sxs-lookup"><span data-stu-id="edbfa-160">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="edbfa-161">Cet exemple montre comment combiner des opérateurs de redirection pour obtenir le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="edbfa-161">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > C:\Temp\redirection.log
```

- <span data-ttu-id="edbfa-162">`3>&1` redirige le flux d' **Avertissement** vers le flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="edbfa-162">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="edbfa-163">`2>&1` redirige le flux d' **Erreurs** vers le flux de **réussite** (qui contient également toutes les données de flux d' **Avertissement** )</span><span class="sxs-lookup"><span data-stu-id="edbfa-163">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="edbfa-164">`>` redirige le flux de **réussite** (qui contient désormais à la fois des flux d' **avertissements** et d' **Erreurs** ) vers un fichier appelé `C:\temp\redirection.log` )</span><span class="sxs-lookup"><span data-stu-id="edbfa-164">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="edbfa-165">Exemple 4 : rediriger tous les flux vers un fichier</span><span class="sxs-lookup"><span data-stu-id="edbfa-165">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="edbfa-166">Cet exemple envoie tous les flux de sortie à partir d’un script appelé `script.ps1` dans un fichier appelé `script.log`</span><span class="sxs-lookup"><span data-stu-id="edbfa-166">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="edbfa-167">Exemple 5 : supprimer toutes les données de flux de Write-Host et d’informations</span><span class="sxs-lookup"><span data-stu-id="edbfa-167">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="edbfa-168">Cet exemple supprime toutes les données de flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="edbfa-168">This example suppresses all information stream data.</span></span> <span data-ttu-id="edbfa-169">Pour en savoir plus sur les applets de commande de flux d' **informations** , consultez [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) et [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information) .</span><span class="sxs-lookup"><span data-stu-id="edbfa-169">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="edbfa-170">Exemple 6 : afficher l’effet des préférences d’action</span><span class="sxs-lookup"><span data-stu-id="edbfa-170">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="edbfa-171">Les paramètres et les variables de préférence d’action peuvent modifier ce qui est écrit dans un flux de données particulier.</span><span class="sxs-lookup"><span data-stu-id="edbfa-171">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="edbfa-172">Le script de cet exemple montre comment la valeur de `$ErrorActionPreference` affecte ce qui est écrit dans le flux d' **Erreurs** .</span><span class="sxs-lookup"><span data-stu-id="edbfa-172">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

<span data-ttu-id="edbfa-173">Lorsque nous exécutons ce script, nous recevons une invite quand `$ErrorActionPreference` a la valeur `Inquire` .</span><span class="sxs-lookup"><span data-stu-id="edbfa-173">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

<span data-ttu-id="edbfa-174">Lorsque nous examinons le fichier journal, nous voyons ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="edbfa-174">When we examine the log file we see the following:</span></span>

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a><span data-ttu-id="edbfa-175">Remarques</span><span class="sxs-lookup"><span data-stu-id="edbfa-175">Notes</span></span>

<span data-ttu-id="edbfa-176">Les opérateurs de redirection qui n’ajoutent pas de données ( `>` et `n>` ) remplacent le contenu actuel du fichier spécifié sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="edbfa-176">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="edbfa-177">Toutefois, si le fichier est un fichier système, masqué et en lecture seule, la redirection **échoue**.</span><span class="sxs-lookup"><span data-stu-id="edbfa-177">However, if the file is a read-only, hidden, or system file, the redirection **fails**.</span></span> <span data-ttu-id="edbfa-178">Les opérateurs de redirection d’ajout ( `>>` et `n>>` ) n’écrivent pas dans un fichier en lecture seule, mais ils ajoutent du contenu à un fichier système ou masqué.</span><span class="sxs-lookup"><span data-stu-id="edbfa-178">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="edbfa-179">Pour forcer la redirection du contenu vers un fichier système, masqué ou en lecture seule, utilisez l' `Out-File` applet de commande avec son `Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="edbfa-179">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="edbfa-180">Lorsque vous écrivez dans des fichiers, les opérateurs de redirection utilisent l' `UTF8NoBOM` encodage.</span><span class="sxs-lookup"><span data-stu-id="edbfa-180">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="edbfa-181">Si le fichier a un encodage différent, il est possible que la sortie ne soit pas correctement mise en forme.</span><span class="sxs-lookup"><span data-stu-id="edbfa-181">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="edbfa-182">Pour écrire dans des fichiers avec un encodage différent, utilisez l' `Out-File` applet de commande avec son `Encoding` paramètre.</span><span class="sxs-lookup"><span data-stu-id="edbfa-182">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="edbfa-183">Confusion potentielle avec les opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="edbfa-183">Potential confusion with comparison operators</span></span>

<span data-ttu-id="edbfa-184">L' `>` opérateur ne doit pas être confondu avec l’opérateur de comparaison [supérieur](about_Comparison_Operators.md#-gt--ge--lt-and--le) à (souvent désigné comme `>` dans d’autres langages de programmation).</span><span class="sxs-lookup"><span data-stu-id="edbfa-184">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt--ge--lt-and--le) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="edbfa-185">Selon les objets comparés, la sortie à l’aide de `>` peut sembler correcte (car 36 n’est pas supérieur à 42).</span><span class="sxs-lookup"><span data-stu-id="edbfa-185">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="edbfa-186">Toutefois, une vérification du système de fichiers local peut voir qu’un fichier appelé `42` a été écrit avec le contenu `36` .</span><span class="sxs-lookup"><span data-stu-id="edbfa-186">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="edbfa-187">Toute tentative d’utilisation de la comparaison inverse `<` (inférieure à) génère une erreur système :</span><span class="sxs-lookup"><span data-stu-id="edbfa-187">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
    + CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="edbfa-188">Si la comparaison numérique est l’opération requise, elle `-lt` `-gt` doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="edbfa-188">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="edbfa-189">Pour plus d’informations, consultez l' `-gt` opérateur dans [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le).</span><span class="sxs-lookup"><span data-stu-id="edbfa-189">For more information, see the `-gt` operator in [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le).</span></span>

## <a name="see-also"></a><span data-ttu-id="edbfa-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edbfa-190">See also</span></span>

- [<span data-ttu-id="edbfa-191">Out-File</span><span class="sxs-lookup"><span data-stu-id="edbfa-191">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="edbfa-192">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="edbfa-192">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="edbfa-193">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="edbfa-193">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="edbfa-194">Write-Error</span><span class="sxs-lookup"><span data-stu-id="edbfa-194">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="edbfa-195">Write-Host</span><span class="sxs-lookup"><span data-stu-id="edbfa-195">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="edbfa-196">Write-Information</span><span class="sxs-lookup"><span data-stu-id="edbfa-196">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="edbfa-197">Write-Output</span><span class="sxs-lookup"><span data-stu-id="edbfa-197">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="edbfa-198">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="edbfa-198">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="edbfa-199">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="edbfa-199">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="edbfa-200">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="edbfa-200">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="edbfa-201">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="edbfa-201">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="edbfa-202">about_Operators</span><span class="sxs-lookup"><span data-stu-id="edbfa-202">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="edbfa-203">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="edbfa-203">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="edbfa-204">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="edbfa-204">about_Path_Syntax</span></span>](about_Path_Syntax.md)
