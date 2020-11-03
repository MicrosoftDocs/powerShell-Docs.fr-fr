---
description: Explique comment rediriger la sortie de PowerShell vers des fichiers texte.
keywords: PowerShell, applet de commande
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 59151c31857f12e3a78fd6d292a6a952c312c850
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208445"
---
# <a name="about-redirection"></a><span data-ttu-id="d476a-104">À propos de la redirection</span><span class="sxs-lookup"><span data-stu-id="d476a-104">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="d476a-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="d476a-105">Short description</span></span>
<span data-ttu-id="d476a-106">Explique comment rediriger la sortie de PowerShell vers des fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="d476a-106">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="d476a-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="d476a-107">Long description</span></span>

<span data-ttu-id="d476a-108">Par défaut, PowerShell envoie la sortie à l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d476a-108">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="d476a-109">Il s’agit généralement de l’application console.</span><span class="sxs-lookup"><span data-stu-id="d476a-109">Usually this is the console application.</span></span> <span data-ttu-id="d476a-110">Toutefois, vous pouvez diriger la sortie vers un fichier texte et vous pouvez rediriger la sortie d’erreur vers le flux de sortie normal.</span><span class="sxs-lookup"><span data-stu-id="d476a-110">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="d476a-111">Vous pouvez utiliser les méthodes suivantes pour rediriger la sortie :</span><span class="sxs-lookup"><span data-stu-id="d476a-111">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="d476a-112">Utilisez l' `Out-File` applet de commande, qui envoie une sortie de commande à un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="d476a-112">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="d476a-113">En général, vous utilisez l’applet de commande `Out-File` lorsque vous avez besoin d’utiliser ses paramètres, tels que les `Encoding` paramètres,, `Force` `Width` ou `NoClobber` .</span><span class="sxs-lookup"><span data-stu-id="d476a-113">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="d476a-114">Utilisez l' `Tee-Object` applet de commande, qui envoie une sortie de commande à un fichier texte, puis l’envoie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="d476a-114">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="d476a-115">Utilisez les opérateurs de redirection PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d476a-115">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="d476a-116">L’utilisation de l’opérateur de redirection avec une cible de fichier est fonctionnellement équivalente à la fonctionnalité de canalisation `Out-File` sans aucun paramètre supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d476a-116">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="d476a-117">Pour plus d’informations sur les flux, consultez [about_Output_Streams](about_Output_Streams.md).</span><span class="sxs-lookup"><span data-stu-id="d476a-117">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="d476a-118">Flux de sortie redirigés</span><span class="sxs-lookup"><span data-stu-id="d476a-118">Redirectable output streams</span></span>

<span data-ttu-id="d476a-119">PowerShell prend en charge la redirection des flux de sortie suivants.</span><span class="sxs-lookup"><span data-stu-id="d476a-119">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="d476a-120">Train #</span><span class="sxs-lookup"><span data-stu-id="d476a-120">Stream #</span></span> |      <span data-ttu-id="d476a-121">Description</span><span class="sxs-lookup"><span data-stu-id="d476a-121">Description</span></span>       | <span data-ttu-id="d476a-122">Introduite dans</span><span class="sxs-lookup"><span data-stu-id="d476a-122">Introduced in</span></span>  |    <span data-ttu-id="d476a-123">Écrire l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d476a-123">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="d476a-124">1</span><span class="sxs-lookup"><span data-stu-id="d476a-124">1</span></span>        | <span data-ttu-id="d476a-125">**Opération réussie** Train</span><span class="sxs-lookup"><span data-stu-id="d476a-125">**Success** Stream</span></span>     | <span data-ttu-id="d476a-126">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="d476a-126">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="d476a-127">2</span><span class="sxs-lookup"><span data-stu-id="d476a-127">2</span></span>        | <span data-ttu-id="d476a-128">**Erreur** Train</span><span class="sxs-lookup"><span data-stu-id="d476a-128">**Error** Stream</span></span>       | <span data-ttu-id="d476a-129">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="d476a-129">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="d476a-130">3</span><span class="sxs-lookup"><span data-stu-id="d476a-130">3</span></span>        | <span data-ttu-id="d476a-131">**Avertissement** Train</span><span class="sxs-lookup"><span data-stu-id="d476a-131">**Warning** Stream</span></span>     | <span data-ttu-id="d476a-132">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d476a-132">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="d476a-133">4</span><span class="sxs-lookup"><span data-stu-id="d476a-133">4</span></span>        | <span data-ttu-id="d476a-134">**Commentaires** Train</span><span class="sxs-lookup"><span data-stu-id="d476a-134">**Verbose** Stream</span></span>     | <span data-ttu-id="d476a-135">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d476a-135">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="d476a-136">5</span><span class="sxs-lookup"><span data-stu-id="d476a-136">5</span></span>        | <span data-ttu-id="d476a-137">**Débogage** Train</span><span class="sxs-lookup"><span data-stu-id="d476a-137">**Debug** Stream</span></span>       | <span data-ttu-id="d476a-138">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d476a-138">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="d476a-139">6</span><span class="sxs-lookup"><span data-stu-id="d476a-139">6</span></span>        | <span data-ttu-id="d476a-140">**Informations** Train</span><span class="sxs-lookup"><span data-stu-id="d476a-140">**Information** Stream</span></span> | <span data-ttu-id="d476a-141">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d476a-141">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="d476a-142">Tous les flux</span><span class="sxs-lookup"><span data-stu-id="d476a-142">All Streams</span></span>            | <span data-ttu-id="d476a-143">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d476a-143">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="d476a-144">Il y a également un flux de **progression** dans PowerShell, mais il ne prend pas en charge la redirection.</span><span class="sxs-lookup"><span data-stu-id="d476a-144">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="d476a-145">Opérateurs de redirection PowerShell</span><span class="sxs-lookup"><span data-stu-id="d476a-145">PowerShell redirection operators</span></span>

<span data-ttu-id="d476a-146">Les opérateurs de redirection PowerShell sont les suivants, où `n` représente le numéro de flux.</span><span class="sxs-lookup"><span data-stu-id="d476a-146">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="d476a-147">Le flux de **réussite** ( `1` ) est la valeur par défaut si aucun flux n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d476a-147">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="d476a-148">Opérateur</span><span class="sxs-lookup"><span data-stu-id="d476a-148">Operator</span></span> |                         <span data-ttu-id="d476a-149">Description</span><span class="sxs-lookup"><span data-stu-id="d476a-149">Description</span></span>                         | <span data-ttu-id="d476a-150">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d476a-150">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="d476a-151">Envoie le flux spécifié à un fichier.</span><span class="sxs-lookup"><span data-stu-id="d476a-151">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="d476a-152">**Ajoute** le flux spécifié à un fichier.</span><span class="sxs-lookup"><span data-stu-id="d476a-152">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="d476a-153">_Redirige_ le flux spécifié vers le flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="d476a-153">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="d476a-154">Contrairement à certains shells UNIX, vous pouvez rediriger uniquement les autres flux vers le flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="d476a-154">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="d476a-155">Exemples</span><span class="sxs-lookup"><span data-stu-id="d476a-155">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="d476a-156">Exemple 1 : rediriger les erreurs et la sortie vers un fichier</span><span class="sxs-lookup"><span data-stu-id="d476a-156">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="d476a-157">Cet exemple s’exécute `dir` sur un élément qui sera correctement exécuté, et sur un élément qui génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="d476a-157">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="d476a-158">Il utilise `2>&1` pour rediriger le flux d' **Erreurs** vers le flux de **réussite** , et `>` pour envoyer le flux de **réussite** obtenu à un fichier appelé `dir.log`</span><span class="sxs-lookup"><span data-stu-id="d476a-158">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="d476a-159">Exemple 2 : envoyer toutes les données de flux de réussite à un fichier</span><span class="sxs-lookup"><span data-stu-id="d476a-159">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="d476a-160">Cet exemple envoie toutes les données de flux de **réussite** à un fichier appelé `script.log` .</span><span class="sxs-lookup"><span data-stu-id="d476a-160">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="d476a-161">Exemple 3 : envoyer des flux de réussite, d’avertissement et d’erreur à un fichier</span><span class="sxs-lookup"><span data-stu-id="d476a-161">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="d476a-162">Cet exemple montre comment combiner des opérateurs de redirection pour obtenir le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="d476a-162">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- <span data-ttu-id="d476a-163">`3>&1` redirige le flux d' **Avertissement** vers le flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="d476a-163">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="d476a-164">`2>&1` redirige le flux d' **Erreurs** vers le flux de **réussite** (qui contient également toutes les données de flux d' **Avertissement** )</span><span class="sxs-lookup"><span data-stu-id="d476a-164">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="d476a-165">`>` redirige le flux de **réussite** (qui contient désormais à la fois des flux d' **avertissements** et d' **Erreurs** ) vers un fichier appelé `C:\temp\redirection.log` )</span><span class="sxs-lookup"><span data-stu-id="d476a-165">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="d476a-166">Exemple 4 : rediriger tous les flux vers un fichier</span><span class="sxs-lookup"><span data-stu-id="d476a-166">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="d476a-167">Cet exemple envoie tous les flux de sortie à partir d’un script appelé `script.ps1` dans un fichier appelé `script.log`</span><span class="sxs-lookup"><span data-stu-id="d476a-167">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="d476a-168">Exemple 5 : supprimer toutes les données de flux de Write-Host et d’informations</span><span class="sxs-lookup"><span data-stu-id="d476a-168">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="d476a-169">Cet exemple supprime toutes les données de flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="d476a-169">This example suppresses all information stream data.</span></span> <span data-ttu-id="d476a-170">Pour en savoir plus sur les applets de commande de flux d' **informations** , consultez [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) et [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information) .</span><span class="sxs-lookup"><span data-stu-id="d476a-170">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="d476a-171">Exemple 6 : afficher l’effet des préférences d’action</span><span class="sxs-lookup"><span data-stu-id="d476a-171">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="d476a-172">Les paramètres et les variables de préférence d’action peuvent modifier ce qui est écrit dans un flux de données particulier.</span><span class="sxs-lookup"><span data-stu-id="d476a-172">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="d476a-173">Le script de cet exemple montre comment la valeur de `$ErrorActionPreference` affecte ce qui est écrit dans le flux d' **Erreurs** .</span><span class="sxs-lookup"><span data-stu-id="d476a-173">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

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

<span data-ttu-id="d476a-174">Lorsque nous exécutons ce script, nous recevons une invite quand `$ErrorActionPreference` a la valeur `Inquire` .</span><span class="sxs-lookup"><span data-stu-id="d476a-174">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

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

<span data-ttu-id="d476a-175">Lorsque nous examinons le fichier journal, nous voyons ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d476a-175">When we examine the log file we see the following:</span></span>

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

## <a name="notes"></a><span data-ttu-id="d476a-176">Notes</span><span class="sxs-lookup"><span data-stu-id="d476a-176">Notes</span></span>

<span data-ttu-id="d476a-177">Les opérateurs de redirection qui n’ajoutent pas de données ( `>` et `n>` ) remplacent le contenu actuel du fichier spécifié sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="d476a-177">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="d476a-178">Toutefois, si le fichier est un fichier système, masqué et en lecture seule, la redirection **échoue** .</span><span class="sxs-lookup"><span data-stu-id="d476a-178">However, if the file is a read-only, hidden, or system file, the redirection **fails** .</span></span> <span data-ttu-id="d476a-179">Les opérateurs de redirection d’ajout ( `>>` et `n>>` ) n’écrivent pas dans un fichier en lecture seule, mais ils ajoutent du contenu à un fichier système ou masqué.</span><span class="sxs-lookup"><span data-stu-id="d476a-179">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="d476a-180">Pour forcer la redirection du contenu vers un fichier système, masqué ou en lecture seule, utilisez l' `Out-File` applet de commande avec son `Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d476a-180">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="d476a-181">Lorsque vous écrivez dans des fichiers, les opérateurs de redirection utilisent l' `UTF8NoBOM` encodage.</span><span class="sxs-lookup"><span data-stu-id="d476a-181">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="d476a-182">Si le fichier a un encodage différent, il est possible que la sortie ne soit pas correctement mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d476a-182">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="d476a-183">Pour écrire dans des fichiers avec un encodage différent, utilisez l' `Out-File` applet de commande avec son `Encoding` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d476a-183">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="d476a-184">Confusion potentielle avec les opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="d476a-184">Potential confusion with comparison operators</span></span>

<span data-ttu-id="d476a-185">L' `>` opérateur ne doit pas être confondu avec l’opérateur de comparaison [supérieur](about_Comparison_Operators.md#-gt) à (souvent désigné comme `>` dans d’autres langages de programmation).</span><span class="sxs-lookup"><span data-stu-id="d476a-185">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="d476a-186">Selon les objets comparés, la sortie à l’aide de `>` peut sembler correcte (car 36 n’est pas supérieur à 42).</span><span class="sxs-lookup"><span data-stu-id="d476a-186">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="d476a-187">Toutefois, une vérification du système de fichiers local peut voir qu’un fichier appelé `42` a été écrit avec le contenu `36` .</span><span class="sxs-lookup"><span data-stu-id="d476a-187">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="d476a-188">Toute tentative d’utilisation de la comparaison inverse `<` (inférieure à) génère une erreur système :</span><span class="sxs-lookup"><span data-stu-id="d476a-188">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="d476a-189">Si la comparaison numérique est l’opération requise, elle `-lt` `-gt` doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="d476a-189">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="d476a-190">Voir : [ `-gt` opérateur de comparaison](about_Comparison_Operators.md#-gt)</span><span class="sxs-lookup"><span data-stu-id="d476a-190">See: [`-gt` Comparison Operator](about_Comparison_Operators.md#-gt)</span></span>

## <a name="see-also"></a><span data-ttu-id="d476a-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d476a-191">See also</span></span>

- [<span data-ttu-id="d476a-192">Out-File</span><span class="sxs-lookup"><span data-stu-id="d476a-192">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="d476a-193">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="d476a-193">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="d476a-194">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="d476a-194">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="d476a-195">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="d476a-195">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="d476a-196">Write-Host</span><span class="sxs-lookup"><span data-stu-id="d476a-196">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="d476a-197">Write-Information</span><span class="sxs-lookup"><span data-stu-id="d476a-197">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="d476a-198">Write-Output</span><span class="sxs-lookup"><span data-stu-id="d476a-198">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="d476a-199">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="d476a-199">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="d476a-200">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="d476a-200">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="d476a-201">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="d476a-201">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="d476a-202">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="d476a-202">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="d476a-203">about_Operators</span><span class="sxs-lookup"><span data-stu-id="d476a-203">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="d476a-204">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="d476a-204">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="d476a-205">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="d476a-205">about_Path_Syntax</span></span>](about_Path_Syntax.md)
