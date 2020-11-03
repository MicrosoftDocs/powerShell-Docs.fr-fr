---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206230"
---
# <span data-ttu-id="ddf5f-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-103">ForEach-Object</span></span>

## <span data-ttu-id="ddf5f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ddf5f-104">SYNOPSIS</span></span>
<span data-ttu-id="ddf5f-105">Effectue une opération sur chaque élément d'une collection d'objets d'entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="ddf5f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ddf5f-106">SYNTAX</span></span>

### <span data-ttu-id="ddf5f-107">ScriptBlockSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ddf5f-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ddf5f-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="ddf5f-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ddf5f-109">Description</span><span class="sxs-lookup"><span data-stu-id="ddf5f-109">DESCRIPTION</span></span>

<span data-ttu-id="ddf5f-110">L' `ForEach-Object` applet de commande effectue une opération sur chaque élément d’une collection d’objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="ddf5f-111">Les objets d’entrée peuvent être dirigés vers l’applet de commande ou spécifiés à l’aide du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="ddf5f-112">À compter de Windows PowerShell 3,0, il existe deux façons de construire une `ForEach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="ddf5f-113">**Bloc de script** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-113">**Script block** .</span></span> <span data-ttu-id="ddf5f-114">Vous pouvez utiliser un bloc de script pour spécifier l'opération.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="ddf5f-115">Dans le bloc de script, utilisez la `$_` variable pour représenter l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="ddf5f-116">Le bloc de script est la valeur du paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="ddf5f-117">Le bloc de script peut contenir n’importe quel script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="ddf5f-118">Par exemple, la commande suivante obtient la valeur de la propriété **ProcessName** de chaque processus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="ddf5f-119">`ForEach-Object` prend en charge les `begin` `process` blocs, et `end` comme décrit dans [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="ddf5f-120">Les blocs de script s’exécutent dans la portée de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="ddf5f-121">Par conséquent, les blocs ont accès aux variables dans cette portée et peuvent créer de nouvelles variables qui persistent dans cette portée une fois l’applet de commande terminée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="ddf5f-122">**Instruction Operation** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-122">**Operation statement** .</span></span> <span data-ttu-id="ddf5f-123">Vous pouvez également écrire une instruction d’opération, qui est bien plus similaire à un langage naturel.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="ddf5f-124">Vous pouvez utiliser l'instruction d'opération pour spécifier une valeur de propriété ou appeler une méthode.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="ddf5f-125">Les instructions d'opération ont été introduites dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="ddf5f-126">Par exemple, la commande suivante obtient également la valeur de la propriété **ProcessName** de chaque processus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

## <span data-ttu-id="ddf5f-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ddf5f-127">EXAMPLES</span></span>

### <span data-ttu-id="ddf5f-128">Exemple 1 : diviser des entiers dans un tableau</span><span class="sxs-lookup"><span data-stu-id="ddf5f-128">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="ddf5f-129">Cet exemple prend un tableau de trois entiers et divise chacun d’eux par 1024.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-129">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="ddf5f-130">Exemple 2 : obtenir la longueur de tous les fichiers d’un répertoire</span><span class="sxs-lookup"><span data-stu-id="ddf5f-130">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="ddf5f-131">Cet exemple traite les fichiers et les répertoires dans le répertoire d’installation de PowerShell `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-131">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="ddf5f-132">Si l’objet n’est pas un répertoire, le bloc de script obtient le nom du fichier, divise la valeur de sa propriété **Length** par 1024 et ajoute un espace ("") pour le séparer de l’entrée suivante.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-132">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="ddf5f-133">L’applet de commande utilise la propriété **PSISContainer** pour déterminer si un objet est un répertoire.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-133">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="ddf5f-134">Exemple 3 : utiliser les événements système les plus récents</span><span class="sxs-lookup"><span data-stu-id="ddf5f-134">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="ddf5f-135">Cet exemple écrit les événements les plus récents 1000 du journal des événements système dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-135">This example write the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="ddf5f-136">L’heure actuelle est affichée avant et après le traitement des événements.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-136">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="ddf5f-137">`Get-EventLog` Obtient les 1000 événements les plus récents du journal des événements système et les stocke dans la `$Events` variable.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-137">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="ddf5f-138">`$Events` est ensuite redirigé vers l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-138">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="ddf5f-139">Le paramètre **Begin** affiche la date et l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-139">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="ddf5f-140">Ensuite, le paramètre **Process** utilise l' `Out-File` applet de commande pour créer un fichier texte nommé events.txt et stocke la propriété message de chacun des événements dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-140">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="ddf5f-141">Enfin, le paramètre **End** est utilisé pour afficher la date et l'heure une fois l'ensemble du traitement terminé.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-141">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="ddf5f-142">Exemple 4 : modifier la valeur d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="ddf5f-142">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="ddf5f-143">Cet exemple modifie la valeur de l’entrée de Registre **remotePath** dans toutes les sous-clés sous la `HKCU:\Network` clé en texte en majuscules.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-143">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="ddf5f-144">Vous pouvez utiliser ce format pour modifier la forme ou le contenu d'une valeur d'entrée de Registre.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-144">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="ddf5f-145">Chaque sous-clé de la clé **Network** représente un lecteur réseau mappé qui se reconnectera à l'ouverture de session.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-145">Each subkey in the **Network** key represents a mapped network drive that will reconnect at logon.</span></span>
<span data-ttu-id="ddf5f-146">L'entrée **RemotePath** contient le chemin d'accès UNC du lecteur connecté.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-146">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="ddf5f-147">Par exemple, si vous mappez le lecteur E : à `\\Server\Share` , il y aura une sous-clé **e** de `HKCU:\Network` et la valeur de l’entrée de Registre **remotePath** dans la sous-clé **e** est `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-147">For example, if you map the E: drive to `\\Server\Share`, there will be an **E** subkey of `HKCU:\Network` and the value of the **RemotePath** registry entry in the **E** subkey is `\\Server\Share`.</span></span>

<span data-ttu-id="ddf5f-148">La commande utilise l' `Get-ItemProperty` applet de commande pour récupérer toutes les sous-clés de la clé **réseau** et l’applet de commande `Set-ItemProperty` pour modifier la valeur de l’entrée de Registre **remotePath** dans chaque clé.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-148">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="ddf5f-149">Dans la `Set-ItemProperty` commande, le chemin d’accès est la valeur de la propriété **PSPath** de la clé de registre.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-149">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="ddf5f-150">Il s’agit d’une propriété de l’objet Microsoft .NET Framework qui représente la clé de Registre, et non une entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-150">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="ddf5f-151">La commande utilise la méthode **ToUpper ()** de la valeur **remotePath** , qui est une chaîne (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-151">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="ddf5f-152">Étant donné que `Set-ItemProperty` modifie la propriété de chaque clé, l’applet de commande `ForEach-Object` est nécessaire pour accéder à la propriété.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-152">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="ddf5f-153">Exemple 5 : utiliser la variable automatique $Null</span><span class="sxs-lookup"><span data-stu-id="ddf5f-153">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="ddf5f-154">Cet exemple montre l’effet de la fonction de canalisation de la `$Null` variable automatique à l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-154">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="ddf5f-155">Étant donné que PowerShell traite NULL comme un espace réservé explicite, l’applet de commande `ForEach-Object` génère une valeur pour `$Null` , comme c’est le cas pour les autres objets que vous dirigez vers celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-155">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="ddf5f-156">Exemple 6 : récupérer des valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="ddf5f-156">Example 6: Get property values</span></span>

<span data-ttu-id="ddf5f-157">Cet exemple obtient la valeur de la propriété **path** de tous les modules PowerShell installés à l’aide du paramètre **MemberName** de l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-157">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="ddf5f-158">La deuxième commande est équivalente à la première.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-158">The second command is equivalent to the first.</span></span> <span data-ttu-id="ddf5f-159">Elle utilise l' `Foreach` alias de l' `ForEach-Object` applet de commande et omet le nom du paramètre **MemberName** , qui est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-159">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="ddf5f-160">L' `ForEach-Object` applet de commande est très utile pour obtenir des valeurs de propriété, car elle obtient la valeur sans modifier le type, contrairement aux applets de commande **format** ou à l’applet de commande `Select-Object` , qui modifient le type de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-160">The `ForEach-Object` cmdlet is very useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="ddf5f-161">Exemple 7 : fractionner les noms de modules en noms de composants</span><span class="sxs-lookup"><span data-stu-id="ddf5f-161">Example 7: Split module names into component names</span></span>

<span data-ttu-id="ddf5f-162">Cet exemple illustre trois façons de fractionner deux noms de module séparés par des points en leurs noms de composants.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-162">This examples shows three ways to split two dot-separated module names into their component names.</span></span>

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

<span data-ttu-id="ddf5f-163">Elles appellent la méthode **Split** de chaînes.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-163">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="ddf5f-164">Les trois commandes utilisent une syntaxe différente, mais elles sont équivalentes et interchangeables.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-164">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="ddf5f-165">La première commande utilise la syntaxe traditionnelle, qui comprend un bloc de script et l’opérateur d’objet en cours `$_` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-165">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="ddf5f-166">Elle utilise la syntaxe à point pour spécifier la méthode et des parenthèses pour encadrer l'argument délimiteur.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-166">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="ddf5f-167">La deuxième commande utilise le paramètre **MemberName** pour spécifier la méthode **Split** et le paramètre **ArgumentName** pour identifier le point (« . ») comme délimiteur de fractionnement.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-167">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="ddf5f-168">La troisième commande utilise l’alias **foreach** de l' `ForEach-Object` applet de commande et omet les noms des paramètres **MemberName** et **argumentlist** , qui sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-168">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="ddf5f-169">Exemple 8 : utilisation de ForEach-Object avec deux blocs de script</span><span class="sxs-lookup"><span data-stu-id="ddf5f-169">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="ddf5f-170">Dans cet exemple, nous passons deux blocs de script positionnels.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-170">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="ddf5f-171">Tous les blocs de script sont liés au paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-171">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="ddf5f-172">Toutefois, elles sont traitées comme si elles avaient été passées aux paramètres **Begin** et **Process** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-172">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="ddf5f-173">Exemple 9 : utilisation de ForEach-Object avec plus de deux blocs de script</span><span class="sxs-lookup"><span data-stu-id="ddf5f-173">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="ddf5f-174">Dans cet exemple, nous passons deux blocs de script positionnels.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-174">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="ddf5f-175">Tous les blocs de script sont liés au paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-175">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="ddf5f-176">Toutefois, elles sont traitées comme si elles avaient été passées aux paramètres **Begin** , **Process** et **end** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-176">However, they are treated as if they had been passed to the **Begin** , **Process** , and **End** parameters.</span></span>

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
> <span data-ttu-id="ddf5f-177">Le premier bloc de script est toujours mappé au `begin` bloc, le dernier bloc est mappé au `end` bloc et les blocs entre sont tous mappés au `process` bloc.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-177">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="ddf5f-178">Exemple 10 : exécuter plusieurs blocs de script pour chaque élément de pipeline</span><span class="sxs-lookup"><span data-stu-id="ddf5f-178">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="ddf5f-179">Comme indiqué dans l’exemple précédent, plusieurs blocs de script passés à l’aide du paramètre **Process** sont mappés aux paramètres **Begin** et **end** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-179">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="ddf5f-180">Pour éviter ce mappage, vous devez fournir des valeurs explicites pour les paramètres de **début** et de **fin** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-180">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

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

## <span data-ttu-id="ddf5f-181">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ddf5f-181">PARAMETERS</span></span>

### <span data-ttu-id="ddf5f-182">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="ddf5f-182">-ArgumentList</span></span>

<span data-ttu-id="ddf5f-183">Spécifie un tableau d’arguments pour un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-183">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="ddf5f-184">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-184">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="ddf5f-185">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-185">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ddf5f-186">-Début</span><span class="sxs-lookup"><span data-stu-id="ddf5f-186">-Begin</span></span>

<span data-ttu-id="ddf5f-187">Spécifie un bloc de script qui s’exécute avant que cette applet de commande traite tous les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-187">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="ddf5f-188">Ce bloc de script n’est exécuté qu’une seule fois pour l’ensemble du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-188">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="ddf5f-189">Pour plus d’informations sur le `begin` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-189">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="ddf5f-190">-Fin</span><span class="sxs-lookup"><span data-stu-id="ddf5f-190">-End</span></span>

<span data-ttu-id="ddf5f-191">Spécifie un bloc de script qui s’exécute après que cette applet de commande a traité tous les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-191">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="ddf5f-192">Ce bloc de script n’est exécuté qu’une seule fois pour l’ensemble du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-192">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="ddf5f-193">Pour plus d’informations sur le `end` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-193">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="ddf5f-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ddf5f-194">-InputObject</span></span>

<span data-ttu-id="ddf5f-195">Spécifie les objets d'entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-195">Specifies the input objects.</span></span> <span data-ttu-id="ddf5f-196">`ForEach-Object` exécute le bloc de script ou l’instruction d’opération sur chaque objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-196">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="ddf5f-197">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-197">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="ddf5f-198">Quand vous utilisez le paramètre **InputObject** avec `ForEach-Object` , au lieu de rediriger les résultats de la commande vers `ForEach-Object` , la valeur **InputObject** est traitée comme un objet unique.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-198">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="ddf5f-199">Cela est vrai même si la valeur est une collection qui est le résultat d’une commande, telle que `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-199">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="ddf5f-200">Étant donné que **InputObject** ne peut pas retourner des propriétés individuelles d’un tableau ou d’une collection d’objets, il est recommandé, si vous utilisez, `ForEach-Object` d’effectuer des opérations sur une collection d’objets pour les objets qui ont des valeurs spécifiques dans les propriétés définies, `ForEach-Object` comme indiqué dans les exemples de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-200">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="ddf5f-201">-MemberName</span><span class="sxs-lookup"><span data-stu-id="ddf5f-201">-MemberName</span></span>

<span data-ttu-id="ddf5f-202">Spécifie la propriété à obtenir ou la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-202">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="ddf5f-203">Les caractères génériques sont autorisés, mais ne fonctionnent que si la chaîne résultante correspond à une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-203">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="ddf5f-204">Si, par exemple, vous exécutez `Get-Process | ForEach -MemberName *Name` , et que plusieurs membres existent avec un nom qui contient le nom de la chaîne, comme les propriétés **ProcessName** et **Name** , la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-204">If, for example, you run `Get-Process | ForEach -MemberName *Name`, and more than one member exists with a name that contains the string Name, such as the **ProcessName** and **Name** properties, the command fails.</span></span>

<span data-ttu-id="ddf5f-205">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ddf5f-206">-Processus</span><span class="sxs-lookup"><span data-stu-id="ddf5f-206">-Process</span></span>

<span data-ttu-id="ddf5f-207">Spécifie l'opération qui est effectuée sur chaque objet d'entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-207">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="ddf5f-208">Ce bloc de script est exécuté pour chaque objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-208">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="ddf5f-209">Pour plus d’informations sur le `process` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-209">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="ddf5f-210">Lorsque vous fournissez plusieurs blocs de script au paramètre **Process** , le premier bloc de script est toujours mappé au `begin` bloc.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-210">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="ddf5f-211">S’il n’y a que deux blocs de script, le deuxième bloc est mappé au `process` bloc.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-211">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="ddf5f-212">S’il existe trois blocs de script ou plus, le premier bloc de script est toujours mappé au `begin` bloc, le dernier bloc est mappé au `end` bloc et les blocs entre sont tous mappés au `process` bloc.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-212">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

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

### <span data-ttu-id="ddf5f-213">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="ddf5f-213">-RemainingScripts</span></span>

<span data-ttu-id="ddf5f-214">Spécifie tous les blocs de script qui ne sont pas pris par le paramètre **Process** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-214">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="ddf5f-215">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ddf5f-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ddf5f-216">-Confirm</span></span>

<span data-ttu-id="ddf5f-217">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-217">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ddf5f-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ddf5f-218">-WhatIf</span></span>

<span data-ttu-id="ddf5f-219">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-219">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ddf5f-220">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-220">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ddf5f-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ddf5f-221">CommonParameters</span></span>

<span data-ttu-id="ddf5f-222">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ddf5f-223">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ddf5f-224">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ddf5f-224">INPUTS</span></span>

### <span data-ttu-id="ddf5f-225">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="ddf5f-225">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="ddf5f-226">Vous pouvez diriger n’importe quel objet vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-226">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="ddf5f-227">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ddf5f-227">OUTPUTS</span></span>

### <span data-ttu-id="ddf5f-228">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="ddf5f-228">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="ddf5f-229">Cette applet de commande retourne les objets qui sont déterminés par l’entrée.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-229">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="ddf5f-230">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ddf5f-230">NOTES</span></span>

- <span data-ttu-id="ddf5f-231">L' `ForEach-Object` applet de commande fonctionne très bien comme l’instruction **foreach** , sauf que vous ne pouvez pas diriger d’entrée vers une instruction **foreach** .</span><span class="sxs-lookup"><span data-stu-id="ddf5f-231">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="ddf5f-232">Pour plus d’informations sur l’instruction **foreach** , consultez [about_Foreach](./About/about_Foreach.md).</span><span class="sxs-lookup"><span data-stu-id="ddf5f-232">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="ddf5f-233">À partir de PowerShell 4,0, `Where` les `ForEach` méthodes et ont été ajoutées pour être utilisées avec les collections.</span><span class="sxs-lookup"><span data-stu-id="ddf5f-233">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="ddf5f-234">Vous pouvez en savoir plus sur ces nouvelles méthodes ici [about_Arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="ddf5f-234">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="ddf5f-235">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ddf5f-235">RELATED LINKS</span></span>

[<span data-ttu-id="ddf5f-236">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-236">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="ddf5f-237">Where-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-237">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="ddf5f-238">Group-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-238">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="ddf5f-239">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-239">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="ddf5f-240">New-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-240">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="ddf5f-241">Select-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-241">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="ddf5f-242">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-242">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="ddf5f-243">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="ddf5f-243">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
