---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: c8b674a895bb323b734f018e5e8654cfec4d0045
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685581"
---
# <span data-ttu-id="5fac6-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-103">ForEach-Object</span></span>

## <span data-ttu-id="5fac6-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5fac6-104">Synopsis</span></span>
<span data-ttu-id="5fac6-105">Effectue une opération sur chaque élément d'une collection d'objets d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="5fac6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fac6-106">Syntax</span></span>

### <span data-ttu-id="5fac6-107">ScriptBlockSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5fac6-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5fac6-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="5fac6-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5fac6-109">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="5fac6-109">ParallelParameterSet</span></span>

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5fac6-110">Description</span><span class="sxs-lookup"><span data-stu-id="5fac6-110">Description</span></span>

<span data-ttu-id="5fac6-111">L' `ForEach-Object` applet de commande effectue une opération sur chaque élément d’une collection d’objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-111">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="5fac6-112">Les objets d’entrée peuvent être dirigés vers l’applet de commande ou spécifiés à l’aide du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-112">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="5fac6-113">À compter de Windows PowerShell 3,0, il existe deux façons de construire une `ForEach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="5fac6-113">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="5fac6-114">**Bloc de script**.</span><span class="sxs-lookup"><span data-stu-id="5fac6-114">**Script block**.</span></span> <span data-ttu-id="5fac6-115">Vous pouvez utiliser un bloc de script pour spécifier l'opération.</span><span class="sxs-lookup"><span data-stu-id="5fac6-115">You can use a script block to specify the operation.</span></span> <span data-ttu-id="5fac6-116">Dans le bloc de script, utilisez la `$_` variable pour représenter l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="5fac6-116">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="5fac6-117">Le bloc de script est la valeur du paramètre **Process**.</span><span class="sxs-lookup"><span data-stu-id="5fac6-117">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="5fac6-118">Le bloc de script peut contenir n’importe quel script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fac6-118">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="5fac6-119">Par exemple, la commande suivante obtient la valeur de la propriété **ProcessName** de chaque processus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5fac6-119">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="5fac6-120">`ForEach-Object` prend en charge les `begin` `process` blocs, et `end` comme décrit dans [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="5fac6-120">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="5fac6-121">Les blocs de script s’exécutent dans la portée de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="5fac6-121">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="5fac6-122">Par conséquent, les blocs ont accès aux variables dans cette portée et peuvent créer de nouvelles variables qui persistent dans cette portée une fois l’applet de commande terminée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-122">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="5fac6-123">**Instruction Operation**.</span><span class="sxs-lookup"><span data-stu-id="5fac6-123">**Operation statement**.</span></span> <span data-ttu-id="5fac6-124">Vous pouvez également écrire une instruction d’opération, qui est bien plus similaire à un langage naturel.</span><span class="sxs-lookup"><span data-stu-id="5fac6-124">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="5fac6-125">Vous pouvez utiliser l'instruction d'opération pour spécifier une valeur de propriété ou appeler une méthode.</span><span class="sxs-lookup"><span data-stu-id="5fac6-125">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="5fac6-126">Les instructions d'opération ont été introduites dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-126">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="5fac6-127">Par exemple, la commande suivante obtient également la valeur de la propriété **ProcessName** de chaque processus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5fac6-127">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="5fac6-128">**Bloc de script en cours d’exécution parallèle**.</span><span class="sxs-lookup"><span data-stu-id="5fac6-128">**Parallel running script block**.</span></span> <span data-ttu-id="5fac6-129">À partir de PowerShell 7,0, un troisième jeu de paramètres est disponible qui exécute chaque bloc de script en parallèle.</span><span class="sxs-lookup"><span data-stu-id="5fac6-129">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="5fac6-130">Le paramètre **ThrottleLimit** limite le nombre de scripts parallèles en cours d’exécution à la fois.</span><span class="sxs-lookup"><span data-stu-id="5fac6-130">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="5fac6-131">Comme précédemment, utilisez la `$_` variable pour représenter l’objet d’entrée actuel dans le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5fac6-131">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="5fac6-132">Utilisez le `$using:` mot clé pour passer des références de variable au script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fac6-132">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="5fac6-133">Dans PowerShell 7, une nouvelle instance d’exécution est créée pour chaque itération de boucle afin de garantir un isolement maximal.</span><span class="sxs-lookup"><span data-stu-id="5fac6-133">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="5fac6-134">Il peut s’agir d’un impact important sur les performances et les ressources si le travail que vous effectuez est faible par rapport à la création de nouveaux instances d’exécution ou si un grand nombre d’itérations effectuent un travail important.</span><span class="sxs-lookup"><span data-stu-id="5fac6-134">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span> <span data-ttu-id="5fac6-135">À partir de PowerShell 7,1, instances d’exécution à partir d’un pool d’instances d’exécution sont réutilisés par défaut.</span><span class="sxs-lookup"><span data-stu-id="5fac6-135">As of PowerShell 7.1, runspaces from a runspace pool are reused by default.</span></span> <span data-ttu-id="5fac6-136">La taille du pool d’instances d’exécution est spécifiée par le paramètre **ThrottleLimit** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-136">The runspace pool size is specified by the **ThrottleLimit** parameter.</span></span> <span data-ttu-id="5fac6-137">La taille du pool d’instances d’exécution par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="5fac6-137">The default runspace pool size is 5.</span></span> <span data-ttu-id="5fac6-138">Vous pouvez toujours créer une nouvelle instance d’exécution pour chaque itération à l’aide du commutateur **UseNewRunspace**</span><span class="sxs-lookup"><span data-stu-id="5fac6-138">You can still create a new runspace for each iteration using the **UseNewRunspace** switch.</span></span>

  <span data-ttu-id="5fac6-139">Par défaut, le scriptblocks parallèle utilise le répertoire de travail actuel de l’appelant qui a démarré les tâches parallèles.</span><span class="sxs-lookup"><span data-stu-id="5fac6-139">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="5fac6-140">Les erreurs sans fin d’exécution sont écrites dans le flux d’erreur de l’applet de commande à mesure qu’elles se produisent en parallèle, scriptblocks.</span><span class="sxs-lookup"><span data-stu-id="5fac6-140">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="5fac6-141">Étant donné que l’ordre d’exécution d’un scriptblock parallèle ne peut pas être déterminé, l’ordre dans lequel les erreurs apparaissent dans le flux d’erreur est aléatoire.</span><span class="sxs-lookup"><span data-stu-id="5fac6-141">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="5fac6-142">De même, les messages écrits dans d’autres flux de données, tels que les avertissements, les commentaires ou les informations, sont écrits dans les flux de données dans un ordre indéterminé.</span><span class="sxs-lookup"><span data-stu-id="5fac6-142">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="5fac6-143">L’arrêt des erreurs, telles que les exceptions, met fin à l’instance parallèle individuelle du scriptblocks dans lequel elles se produisent.</span><span class="sxs-lookup"><span data-stu-id="5fac6-143">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="5fac6-144">Une erreur d’arrêt dans un scriptblocks peut ne pas entraîner l’arrêt de l’applet de commande `Foreach-Object` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-144">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="5fac6-145">L’autre scriptblocks, s’exécutant en parallèle, continue à s’exécuter, sauf s’il rencontre également une erreur de fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fac6-145">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="5fac6-146">L’erreur de fin est écrite dans le flux de données d’erreur en tant que **ErrorRecord** avec un **FullyQualifiedErrorId** de `PSTaskException` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-146">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="5fac6-147">Les erreurs de fin peuvent être converties en erreurs sans fin d’arrêt à l’aide de blocs try/catch ou Trap PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fac6-147">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="5fac6-148">Exemples</span><span class="sxs-lookup"><span data-stu-id="5fac6-148">Examples</span></span>

### <span data-ttu-id="5fac6-149">Exemple 1 : diviser des entiers dans un tableau</span><span class="sxs-lookup"><span data-stu-id="5fac6-149">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="5fac6-150">Cet exemple prend un tableau de trois entiers et divise chacun d’eux par 1024.</span><span class="sxs-lookup"><span data-stu-id="5fac6-150">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="5fac6-151">Exemple 2 : obtenir la longueur de tous les fichiers d’un répertoire</span><span class="sxs-lookup"><span data-stu-id="5fac6-151">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="5fac6-152">Cet exemple traite les fichiers et les répertoires dans le répertoire d’installation de PowerShell `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-152">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="5fac6-153">Si l’objet n’est pas un répertoire, le bloc de script obtient le nom du fichier, divise la valeur de sa propriété **Length** par 1024 et ajoute un espace ("") pour le séparer de l’entrée suivante.</span><span class="sxs-lookup"><span data-stu-id="5fac6-153">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="5fac6-154">L’applet de commande utilise la propriété **PSISContainer** pour déterminer si un objet est un répertoire.</span><span class="sxs-lookup"><span data-stu-id="5fac6-154">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="5fac6-155">Exemple 3 : utiliser les événements système les plus récents</span><span class="sxs-lookup"><span data-stu-id="5fac6-155">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="5fac6-156">Cet exemple écrit les événements les plus récents 1000 du journal des événements système dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="5fac6-156">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="5fac6-157">L’heure actuelle est affichée avant et après le traitement des événements.</span><span class="sxs-lookup"><span data-stu-id="5fac6-157">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="5fac6-158">`Get-EventLog` Obtient les 1000 événements les plus récents du journal des événements système et les stocke dans la `$Events` variable.</span><span class="sxs-lookup"><span data-stu-id="5fac6-158">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="5fac6-159">`$Events` est ensuite redirigé vers l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-159">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="5fac6-160">Le paramètre **Begin** affiche la date et l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="5fac6-160">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="5fac6-161">Ensuite, le paramètre **Process** utilise l' `Out-File` applet de commande pour créer un fichier texte nommé events.txt et stocke la propriété message de chacun des événements dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="5fac6-161">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="5fac6-162">Enfin, le paramètre **End** est utilisé pour afficher la date et l'heure une fois l'ensemble du traitement terminé.</span><span class="sxs-lookup"><span data-stu-id="5fac6-162">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="5fac6-163">Exemple 4 : modifier la valeur d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="5fac6-163">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="5fac6-164">Cet exemple modifie la valeur de l’entrée de Registre **remotePath** dans toutes les sous-clés sous la `HKCU:\Network` clé en texte en majuscules.</span><span class="sxs-lookup"><span data-stu-id="5fac6-164">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="5fac6-165">Vous pouvez utiliser ce format pour modifier la forme ou le contenu d'une valeur d'entrée de Registre.</span><span class="sxs-lookup"><span data-stu-id="5fac6-165">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="5fac6-166">Chaque sous-clé de la clé **réseau** représente un lecteur réseau mappé qui se reconnecte au moment de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="5fac6-166">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="5fac6-167">L'entrée **RemotePath** contient le chemin d'accès UNC du lecteur connecté.</span><span class="sxs-lookup"><span data-stu-id="5fac6-167">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="5fac6-168">Par exemple, si vous mappez le lecteur E : à `\\Server\Share` , une sous-clé **e** est créée dans `HKCU:\Network` avec la valeur de Registre **remotePath** définie sur `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-168">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="5fac6-169">La commande utilise l' `Get-ItemProperty` applet de commande pour récupérer toutes les sous-clés de la clé **réseau** et l’applet de commande `Set-ItemProperty` pour modifier la valeur de l’entrée de Registre **remotePath** dans chaque clé.</span><span class="sxs-lookup"><span data-stu-id="5fac6-169">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="5fac6-170">Dans la `Set-ItemProperty` commande, le chemin d’accès est la valeur de la propriété **PSPath** de la clé de registre.</span><span class="sxs-lookup"><span data-stu-id="5fac6-170">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="5fac6-171">Il s’agit d’une propriété de l’objet Microsoft .NET Framework qui représente la clé de Registre, et non une entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="5fac6-171">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="5fac6-172">La commande utilise la méthode **ToUpper ()** de la valeur **remotePath** , qui est une chaîne (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="5fac6-172">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="5fac6-173">Étant donné que `Set-ItemProperty` modifie la propriété de chaque clé, l’applet de commande `ForEach-Object` est nécessaire pour accéder à la propriété.</span><span class="sxs-lookup"><span data-stu-id="5fac6-173">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="5fac6-174">Exemple 5 : utiliser la variable automatique $Null</span><span class="sxs-lookup"><span data-stu-id="5fac6-174">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="5fac6-175">Cet exemple montre l’effet de la fonction de canalisation de la `$Null` variable automatique à l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-175">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="5fac6-176">Étant donné que PowerShell traite NULL comme un espace réservé explicite, l’applet de commande `ForEach-Object` génère une valeur pour `$Null` , comme c’est le cas pour les autres objets que vous dirigez vers celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5fac6-176">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="5fac6-177">Exemple 6 : récupérer des valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="5fac6-177">Example 6: Get property values</span></span>

<span data-ttu-id="5fac6-178">Cet exemple obtient la valeur de la propriété **path** de tous les modules PowerShell installés à l’aide du paramètre **MemberName** de l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-178">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="5fac6-179">La deuxième commande est équivalente à la première.</span><span class="sxs-lookup"><span data-stu-id="5fac6-179">The second command is equivalent to the first.</span></span> <span data-ttu-id="5fac6-180">Elle utilise l' `Foreach` alias de l' `ForEach-Object` applet de commande et omet le nom du paramètre **MemberName** , qui est facultatif.</span><span class="sxs-lookup"><span data-stu-id="5fac6-180">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="5fac6-181">L' `ForEach-Object` applet de commande est utile pour obtenir les valeurs de propriété, car elle obtient la valeur sans modifier le type, contrairement aux applets de commande **format** ou à l’applet de commande `Select-Object` , qui modifient le type de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="5fac6-181">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="5fac6-182">Exemple 7 : fractionner les noms de modules en noms de composants</span><span class="sxs-lookup"><span data-stu-id="5fac6-182">Example 7: Split module names into component names</span></span>

<span data-ttu-id="5fac6-183">Cet exemple illustre trois façons de fractionner deux noms de module séparés par des points en leurs noms de composants.</span><span class="sxs-lookup"><span data-stu-id="5fac6-183">This example shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="5fac6-184">Elles appellent la méthode **Split** de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5fac6-184">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="5fac6-185">Les trois commandes utilisent une syntaxe différente, mais elles sont équivalentes et interchangeables.</span><span class="sxs-lookup"><span data-stu-id="5fac6-185">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="5fac6-186">La première commande utilise la syntaxe traditionnelle, qui comprend un bloc de script et l’opérateur d’objet en cours `$_` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-186">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="5fac6-187">Elle utilise la syntaxe à point pour spécifier la méthode et des parenthèses pour encadrer l'argument délimiteur.</span><span class="sxs-lookup"><span data-stu-id="5fac6-187">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="5fac6-188">La deuxième commande utilise le paramètre **MemberName** pour spécifier la méthode **Split** et le paramètre **ArgumentName** pour identifier le point (« . ») comme délimiteur de fractionnement.</span><span class="sxs-lookup"><span data-stu-id="5fac6-188">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="5fac6-189">La troisième commande utilise l’alias **foreach** de l' `ForEach-Object` applet de commande et omet les noms des paramètres **MemberName** et **argumentlist** , qui sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="5fac6-189">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="5fac6-190">Exemple 8 : utilisation de ForEach-Object avec deux blocs de script</span><span class="sxs-lookup"><span data-stu-id="5fac6-190">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="5fac6-191">Dans cet exemple, nous passons deux blocs de script positionnels.</span><span class="sxs-lookup"><span data-stu-id="5fac6-191">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="5fac6-192">Tous les blocs de script sont liés au paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-192">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="5fac6-193">Toutefois, elles sont traitées comme si elles avaient été passées aux paramètres **Begin** et **Process** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-193">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="5fac6-194">Exemple 9 : utilisation de ForEach-Object avec plus de deux blocs de script</span><span class="sxs-lookup"><span data-stu-id="5fac6-194">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="5fac6-195">Dans cet exemple, nous passons deux blocs de script positionnels.</span><span class="sxs-lookup"><span data-stu-id="5fac6-195">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="5fac6-196">Tous les blocs de script sont liés au paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-196">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="5fac6-197">Toutefois, elles sont traitées comme si elles avaient été passées aux paramètres **Begin**, **Process** et **end** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-197">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="5fac6-198">Le premier bloc de script est toujours mappé au `begin` bloc, le dernier bloc est mappé au `end` bloc et les blocs entre sont tous mappés au `process` bloc.</span><span class="sxs-lookup"><span data-stu-id="5fac6-198">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="5fac6-199">Exemple 10 : exécuter plusieurs blocs de script pour chaque élément de pipeline</span><span class="sxs-lookup"><span data-stu-id="5fac6-199">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="5fac6-200">Comme indiqué dans l’exemple précédent, plusieurs blocs de script passés à l’aide du paramètre **Process** sont mappés aux paramètres **Begin** et **end** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-200">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="5fac6-201">Pour éviter ce mappage, vous devez fournir des valeurs explicites pour les paramètres de **début** et de **fin** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-201">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### <span data-ttu-id="5fac6-202">Exemple 11 : exécuter un script lent dans des lots parallèles</span><span class="sxs-lookup"><span data-stu-id="5fac6-202">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="5fac6-203">Cet exemple exécute un bloc de script simple qui évalue une chaîne et se met en veille pendant une seconde.</span><span class="sxs-lookup"><span data-stu-id="5fac6-203">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

<span data-ttu-id="5fac6-204">La valeur du paramètre **ThrottleLimit** est définie sur 4 afin que l’entrée soit traitée par lots de quatre.</span><span class="sxs-lookup"><span data-stu-id="5fac6-204">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="5fac6-205">Le `$using:` mot clé est utilisé pour transmettre la `$Message` variable dans chaque bloc de script parallèle.</span><span class="sxs-lookup"><span data-stu-id="5fac6-205">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="5fac6-206">Exemple 12 : récupérer des entrées de journal en parallèle</span><span class="sxs-lookup"><span data-stu-id="5fac6-206">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="5fac6-207">Cet exemple récupère les entrées de journal 50 000 de 5 journaux système sur un ordinateur Windows local.</span><span class="sxs-lookup"><span data-stu-id="5fac6-207">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

<span data-ttu-id="5fac6-208">Le paramètre **Parallèle** spécifie le bloc de script exécuté en parallèle pour chaque nom du journal d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-208">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="5fac6-209">Le paramètre **ThrottleLimit** garantit que les cinq blocs de script s’exécutent en même temps.</span><span class="sxs-lookup"><span data-stu-id="5fac6-209">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="5fac6-210">Exemple 13 : exécuter en parallèle en tant que tâche</span><span class="sxs-lookup"><span data-stu-id="5fac6-210">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="5fac6-211">Cet exemple exécute un bloc de script simple en parallèle, créant deux tâches en arrière-plan à la fois.</span><span class="sxs-lookup"><span data-stu-id="5fac6-211">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

<span data-ttu-id="5fac6-212">la `$job` variable reçoit l’objet de traitement qui collecte les données de sortie et surveille l’état d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fac6-212">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="5fac6-213">L’objet de traitement est dirigé vers `Receive-Job` avec le paramètre de commutateur **Wait** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-213">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="5fac6-214">Et cela diffuse la sortie vers la console, tout comme si `ForEach-Object -Parallel` a été exécuté sans **AsJob**.</span><span class="sxs-lookup"><span data-stu-id="5fac6-214">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="5fac6-215">Exemple 14 : utilisation de références de variable thread-safe</span><span class="sxs-lookup"><span data-stu-id="5fac6-215">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="5fac6-216">Cet exemple appelle des blocs de script en parallèle pour collecter des objets de processus portant un nom unique.</span><span class="sxs-lookup"><span data-stu-id="5fac6-216">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

<span data-ttu-id="5fac6-217">Une seule instance d’un objet **ConcurrentDictionary** est passée à chaque bloc de script pour collecter les objets.</span><span class="sxs-lookup"><span data-stu-id="5fac6-217">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="5fac6-218">Étant donné que le **ConcurrentDictionary** est thread-safe, il peut être modifié en toute sécurité par chaque script parallèle.</span><span class="sxs-lookup"><span data-stu-id="5fac6-218">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="5fac6-219">Un objet non thread-safe, tel que **System. Collections. Generic. dictionary**, ne peut pas être utilisé en toute sécurité ici.</span><span class="sxs-lookup"><span data-stu-id="5fac6-219">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="5fac6-220">Cet exemple est une utilisation très inefficace du paramètre **Parallel** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-220">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="5fac6-221">Le script ajoute simplement l’objet d’entrée à un objet de dictionnaire simultané.</span><span class="sxs-lookup"><span data-stu-id="5fac6-221">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="5fac6-222">Il est trivial et ne justifie pas la surcharge liée à l’appel de chaque script dans un thread séparé.</span><span class="sxs-lookup"><span data-stu-id="5fac6-222">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="5fac6-223">`ForEach-Object`L’exécution normale sans le commutateur **parallèle** est beaucoup plus efficace et plus rapide.</span><span class="sxs-lookup"><span data-stu-id="5fac6-223">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="5fac6-224">Cet exemple est uniquement destiné à illustrer l’utilisation de variables thread-safe.</span><span class="sxs-lookup"><span data-stu-id="5fac6-224">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="5fac6-225">Exemple 15 : écriture d’erreurs avec exécution parallèle</span><span class="sxs-lookup"><span data-stu-id="5fac6-225">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="5fac6-226">Cet exemple écrit dans le flux d’erreur en parallèle, où l’ordre des erreurs écrites est aléatoire.</span><span class="sxs-lookup"><span data-stu-id="5fac6-226">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### <span data-ttu-id="5fac6-227">Exemple 16 : fin des erreurs d’exécution en parallèle</span><span class="sxs-lookup"><span data-stu-id="5fac6-227">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="5fac6-228">Cet exemple illustre une erreur de fin dans un scriptblock en cours d’exécution parallèle.</span><span class="sxs-lookup"><span data-stu-id="5fac6-228">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

<span data-ttu-id="5fac6-229">`Output: 3` n’est jamais écrit, car le scriptblock parallèle de cette itération a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="5fac6-229">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

### <span data-ttu-id="5fac6-230">Exemple 17 : passage de variables dans le script parallèle imbriqué ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="5fac6-230">Example 17: Passing variables in nested parallel script ScriptBlockSet</span></span>

<span data-ttu-id="5fac6-231">Vous pouvez créer une variable en dehors d’un `Foreach-Object -Parallel` scriptblock délimité et l’utiliser à l’intérieur du scriptblock avec le `$using` mot clé.</span><span class="sxs-lookup"><span data-stu-id="5fac6-231">You can create a variable outside a `Foreach-Object -Parallel` scoped scriptblock and use it inside the scriptblock with the `$using` keyword.</span></span>

```powershell
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
}
```

```Output
TestA
TestA
```

```powershell
# You CANNOT create a variable inside a scoped scriptblock
# to be used in a nested foreach parallel scriptblock.
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
    $test2 = 'TestB'
    1..2 | Foreach-Object -Parallel {
        $using:test2
    }
}
```

```Output
Line |
   2 |  1..2 | Foreach-Object -Parallel {
     |         ~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The value of the using variable '$using:test2' cannot be retrieved because it has not been set in the local session.
```

<span data-ttu-id="5fac6-232">Le scriptblock imbriqué ne peut pas accéder à la `$test2` variable et une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-232">The nested scriptblock can't access the `$test2` variable and an error is thrown.</span></span>

## <span data-ttu-id="5fac6-233">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5fac6-233">Parameters</span></span>

### <span data-ttu-id="5fac6-234">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="5fac6-234">-ArgumentList</span></span>

<span data-ttu-id="5fac6-235">Spécifie un tableau d’arguments pour un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="5fac6-235">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="5fac6-236">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="5fac6-236">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="5fac6-237">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-238">-Début</span><span class="sxs-lookup"><span data-stu-id="5fac6-238">-Begin</span></span>

<span data-ttu-id="5fac6-239">Spécifie un bloc de script qui s’exécute avant que cette applet de commande traite tous les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-239">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="5fac6-240">Ce bloc de script n’est exécuté qu’une seule fois pour l’ensemble du pipeline.</span><span class="sxs-lookup"><span data-stu-id="5fac6-240">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="5fac6-241">Pour plus d’informations sur le `begin` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="5fac6-241">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-242">-Fin</span><span class="sxs-lookup"><span data-stu-id="5fac6-242">-End</span></span>

<span data-ttu-id="5fac6-243">Spécifie un bloc de script qui s’exécute après que cette applet de commande a traité tous les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-243">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="5fac6-244">Ce bloc de script n’est exécuté qu’une seule fois pour l’ensemble du pipeline.</span><span class="sxs-lookup"><span data-stu-id="5fac6-244">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="5fac6-245">Pour plus d’informations sur le `end` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="5fac6-245">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-246">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5fac6-246">-InputObject</span></span>

<span data-ttu-id="5fac6-247">Spécifie les objets d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-247">Specifies the input objects.</span></span> <span data-ttu-id="5fac6-248">`ForEach-Object` exécute le bloc de script ou l’instruction d’opération sur chaque objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-248">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="5fac6-249">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="5fac6-249">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="5fac6-250">Quand vous utilisez le paramètre **InputObject** avec `ForEach-Object` , au lieu de rediriger les résultats de la commande vers `ForEach-Object` , la valeur **InputObject** est traitée comme un objet unique.</span><span class="sxs-lookup"><span data-stu-id="5fac6-250">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="5fac6-251">Cela est vrai même si la valeur est une collection qui est le résultat d’une commande, telle que `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-251">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="5fac6-252">Étant donné que **InputObject** ne peut pas retourner des propriétés individuelles d’un tableau ou d’une collection d’objets, il est recommandé, si vous utilisez, `ForEach-Object` d’effectuer des opérations sur une collection d’objets pour les objets qui ont des valeurs spécifiques dans les propriétés définies, `ForEach-Object` comme indiqué dans les exemples de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5fac6-252">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-253">-MemberName</span><span class="sxs-lookup"><span data-stu-id="5fac6-253">-MemberName</span></span>

<span data-ttu-id="5fac6-254">Spécifie la propriété à obtenir ou la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="5fac6-254">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="5fac6-255">Les caractères génériques sont autorisés, mais ne fonctionnent que si la chaîne résultante correspond à une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="5fac6-255">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="5fac6-256">Par exemple, si vous exécutez `Get-Process | ForEach -MemberName *Name` , le modèle de caractère générique correspond à plusieurs membres, ce qui provoque l’échec de la commande.</span><span class="sxs-lookup"><span data-stu-id="5fac6-256">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="5fac6-257">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5fac6-258">-Processus</span><span class="sxs-lookup"><span data-stu-id="5fac6-258">-Process</span></span>

<span data-ttu-id="5fac6-259">Spécifie l'opération qui est effectuée sur chaque objet d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-259">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="5fac6-260">Ce bloc de script est exécuté pour chaque objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5fac6-260">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="5fac6-261">Pour plus d’informations sur le `process` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="5fac6-261">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="5fac6-262">Lorsque vous fournissez plusieurs blocs de script au paramètre **Process** , le premier bloc de script est toujours mappé au `begin` bloc.</span><span class="sxs-lookup"><span data-stu-id="5fac6-262">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="5fac6-263">S’il n’y a que deux blocs de script, le deuxième bloc est mappé au `process` bloc.</span><span class="sxs-lookup"><span data-stu-id="5fac6-263">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="5fac6-264">S’il existe trois blocs de script ou plus, le premier bloc de script est toujours mappé au `begin` bloc, le dernier bloc est mappé au `end` bloc et les blocs entre sont tous mappés au `process` bloc.</span><span class="sxs-lookup"><span data-stu-id="5fac6-264">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-265">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="5fac6-265">-RemainingScripts</span></span>

<span data-ttu-id="5fac6-266">Spécifie tous les blocs de script qui ne sont pas pris par le paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-266">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="5fac6-267">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-268">-Parallel</span><span class="sxs-lookup"><span data-stu-id="5fac6-268">-Parallel</span></span>

<span data-ttu-id="5fac6-269">Spécifie le bloc de script à utiliser pour le traitement parallèle des objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-269">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="5fac6-270">Entrez un bloc de script décrivant l'opération.</span><span class="sxs-lookup"><span data-stu-id="5fac6-270">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="5fac6-271">Ce paramètre a été introduit dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-271">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-272">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5fac6-272">-ThrottleLimit</span></span>

<span data-ttu-id="5fac6-273">Spécifie le nombre de blocs de script en parallèle.</span><span class="sxs-lookup"><span data-stu-id="5fac6-273">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="5fac6-274">Les objets d’entrée sont bloqués jusqu’à ce que le nombre de blocs de script en cours se situe en dessous du **ThrottleLimit**.</span><span class="sxs-lookup"><span data-stu-id="5fac6-274">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="5fac6-275">La valeur par défaut est `5`.</span><span class="sxs-lookup"><span data-stu-id="5fac6-275">The default value is `5`.</span></span>

<span data-ttu-id="5fac6-276">Ce paramètre a été introduit dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-276">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-277">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="5fac6-277">-TimeoutSeconds</span></span>

<span data-ttu-id="5fac6-278">Spécifie le nombre de secondes à attendre que toutes les entrées soient traitées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="5fac6-278">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="5fac6-279">Après le délai d’expiration spécifié, tous les scripts en cours d’exécution sont arrêtés.</span><span class="sxs-lookup"><span data-stu-id="5fac6-279">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="5fac6-280">Et tous les objets d’entrée restants à traiter sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="5fac6-280">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="5fac6-281">La valeur par défaut de `0` désactive le délai d’expiration et `ForEach-Object -Parallel` peut s’exécuter indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="5fac6-281">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="5fac6-282">La frappe de la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> à la ligne de commande arrête une commande en cours d’exécution `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="5fac6-282">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="5fac6-283">Ce paramètre ne peut pas être utilisé avec le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-283">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="5fac6-284">Ce paramètre a été introduit dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-284">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-285">-UseNewRunspace</span><span class="sxs-lookup"><span data-stu-id="5fac6-285">-UseNewRunspace</span></span>

<span data-ttu-id="5fac6-286">Fait en sorte que l’appel parallèle crée une nouvelle instance d’exécution pour chaque itération de boucle au lieu de réutiliser instances d’exécution à partir du pool d’instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fac6-286">Causes the parallel invocation to create a new runspace for every loop iteration instead of reusing runspaces from the runspace pool.</span></span>

<span data-ttu-id="5fac6-287">Ce paramètre a été introduit dans PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="5fac6-287">This parameter was introduced in PowerShell 7.1</span></span>

```yml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-288">-AsJob</span><span class="sxs-lookup"><span data-stu-id="5fac6-288">-AsJob</span></span>

<span data-ttu-id="5fac6-289">Provoque l’exécution de l’appel parallèle en tant que tâche PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fac6-289">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="5fac6-290">Un objet de traitement unique est retourné à la place de la sortie des blocs de script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fac6-290">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="5fac6-291">L’objet de traitement contient des tâches enfants pour chaque bloc de script parallèle qui s’exécute.</span><span class="sxs-lookup"><span data-stu-id="5fac6-291">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="5fac6-292">L’objet de traitement peut être utilisé par toutes les applets de commande PowerShell Job pour surveiller l’État en cours d’exécution et récupérer des données.</span><span class="sxs-lookup"><span data-stu-id="5fac6-292">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="5fac6-293">Ce paramètre a été introduit dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="5fac6-293">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fac6-294">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5fac6-294">-Confirm</span></span>

<span data-ttu-id="5fac6-295">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5fac6-295">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5fac6-296">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5fac6-296">-WhatIf</span></span>

<span data-ttu-id="5fac6-297">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5fac6-297">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5fac6-298">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-298">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5fac6-299">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5fac6-299">CommonParameters</span></span>

<span data-ttu-id="5fac6-300">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5fac6-300">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5fac6-301">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5fac6-301">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5fac6-302">Entrées</span><span class="sxs-lookup"><span data-stu-id="5fac6-302">Inputs</span></span>

### <span data-ttu-id="5fac6-303">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="5fac6-303">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5fac6-304">Vous pouvez diriger n’importe quel objet vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5fac6-304">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="5fac6-305">Sorties</span><span class="sxs-lookup"><span data-stu-id="5fac6-305">Outputs</span></span>

### <span data-ttu-id="5fac6-306">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="5fac6-306">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5fac6-307">Cette applet de commande retourne les objets qui sont déterminés par l’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fac6-307">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="5fac6-308">Notes</span><span class="sxs-lookup"><span data-stu-id="5fac6-308">Notes</span></span>

- <span data-ttu-id="5fac6-309">L' `ForEach-Object` applet de commande fonctionne très bien comme l’instruction **foreach** , sauf que vous ne pouvez pas diriger d’entrée vers une instruction **foreach** .</span><span class="sxs-lookup"><span data-stu-id="5fac6-309">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="5fac6-310">Pour plus d’informations sur l’instruction **foreach** , consultez [about_Foreach](./About/about_Foreach.md).</span><span class="sxs-lookup"><span data-stu-id="5fac6-310">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="5fac6-311">À partir de PowerShell 4,0, `Where` les `ForEach` méthodes et ont été ajoutées pour être utilisées avec les collections.</span><span class="sxs-lookup"><span data-stu-id="5fac6-311">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="5fac6-312">Vous pouvez en savoir plus sur ces nouvelles méthodes ici [about_Arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="5fac6-312">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="5fac6-313">Le `ForEach-Object -Parallel` jeu de paramètres utilise l’API interne de PowerShell pour exécuter chaque bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5fac6-313">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="5fac6-314">Il s’agit d’une surcharge beaucoup plus lourde que l’exécution `ForEach-Object` normale avec un traitement séquentiel.</span><span class="sxs-lookup"><span data-stu-id="5fac6-314">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="5fac6-315">Il est important d’utiliser **Parallel** lorsque la surcharge de l’exécution en parallèle est faible par rapport au travail effectué par le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5fac6-315">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="5fac6-316">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5fac6-316">For example:</span></span>

  - <span data-ttu-id="5fac6-317">Scripts de calcul intensif sur les ordinateurs multicœurs</span><span class="sxs-lookup"><span data-stu-id="5fac6-317">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="5fac6-318">Scripts qui consacrent du temps à attendre des résultats ou à exécuter des opérations sur les fichiers</span><span class="sxs-lookup"><span data-stu-id="5fac6-318">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="5fac6-319">L’utilisation du paramètre **Parallel** peut entraîner une exécution beaucoup plus lente des scripts que la normale.</span><span class="sxs-lookup"><span data-stu-id="5fac6-319">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="5fac6-320">Surtout si les scripts parallèles sont simples.</span><span class="sxs-lookup"><span data-stu-id="5fac6-320">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="5fac6-321">Expérimentez en **parallèle** pour découvrir où il peut être bénéfique.</span><span class="sxs-lookup"><span data-stu-id="5fac6-321">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="5fac6-322">Le `ForEach-Object -Parallel` jeu de paramètres exécute des blocs de script en parallèle sur des threads de processus distincts.</span><span class="sxs-lookup"><span data-stu-id="5fac6-322">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="5fac6-323">Le `$using:` mot clé permet de passer des références de variable du thread d’appel d’applet de commande à chaque thread de bloc de script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5fac6-323">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="5fac6-324">Étant donné que les blocs de script s’exécutent dans des threads différents, les variables d’objet passées par référence doivent être utilisées en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="5fac6-324">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="5fac6-325">En général, il est possible de lire en toute sécurité des objets référencés qui ne changent pas.</span><span class="sxs-lookup"><span data-stu-id="5fac6-325">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="5fac6-326">Toutefois, si l’état de l’objet est modifié, vous devez utiliser des objets thread-safe, tels que les types .NET **System. collection. concurrent** (Voir l’exemple 11).</span><span class="sxs-lookup"><span data-stu-id="5fac6-326">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="5fac6-327">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="5fac6-327">Related links</span></span>

[<span data-ttu-id="5fac6-328">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-328">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="5fac6-329">Where-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-329">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="5fac6-330">Group-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-330">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="5fac6-331">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-331">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="5fac6-332">New-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-332">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="5fac6-333">Select-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-333">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="5fac6-334">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-334">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="5fac6-335">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="5fac6-335">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
