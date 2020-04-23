---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Suppression d’objets du pipeline Where Object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737183"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="452c5-103">Suppression d’objets du pipeline (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="452c5-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="452c5-104">Dans PowerShell, vous générez et transmettez souvent à un pipeline plus d’objets que souhaité.</span><span class="sxs-lookup"><span data-stu-id="452c5-104">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="452c5-105">Vous pouvez spécifier les propriétés d’objets particuliers à afficher à l’aide des cmdlets `Format-*`, mais cela ne résout pas le problème de la suppression d’objets entiers de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="452c5-105">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="452c5-106">Il se peut que vous souhaitiez filtrer des objets avant la fin d’un pipeline afin de pouvoir effectuer des actions uniquement sur un sous-ensemble des objets générés initialement.</span><span class="sxs-lookup"><span data-stu-id="452c5-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="452c5-107">PowerShell inclut une cmdlet `Where-Object` qui permet de tester chaque objet dans le pipeline et de le transmettre dans le pipeline uniquement s’il répond à une condition de test particulière.</span><span class="sxs-lookup"><span data-stu-id="452c5-107">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="452c5-108">Les objets qui ne passent pas le test sont supprimés du pipeline.</span><span class="sxs-lookup"><span data-stu-id="452c5-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="452c5-109">Vous fournissez la condition de test comme valeur du paramètre **FilterScript**.</span><span class="sxs-lookup"><span data-stu-id="452c5-109">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="452c5-110">Exécution de tests simples avec l’applet de commande Where-objet</span><span class="sxs-lookup"><span data-stu-id="452c5-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="452c5-111">La valeur de **FilterScript** est un *bloc de script* : une ou plusieurs commandes PowerShell entourées d’accolades (`{}`) qui prend la valeur true ou false.</span><span class="sxs-lookup"><span data-stu-id="452c5-111">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="452c5-112">Ces blocs de script peuvent être très simples, mais leur création nécessite de connaître un autre concept de PowerShell, à savoir les opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="452c5-112">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="452c5-113">Un opérateur de comparaison compare les éléments figurant de part et d’autre de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="452c5-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="452c5-114">Les opérateurs de comparaison commencent par un caractère (`-`) suivi d’un nom.</span><span class="sxs-lookup"><span data-stu-id="452c5-114">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="452c5-115">Les opérateurs de comparaison de base fonctionnent sur pratiquement tout type d’objet.</span><span class="sxs-lookup"><span data-stu-id="452c5-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="452c5-116">Certains opérateurs de comparaison plus avancés fonctionnent uniquement sur du texte ou des tableaux.</span><span class="sxs-lookup"><span data-stu-id="452c5-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="452c5-117">Par défaut, lorsque vous travaillez sur du texte, les opérateurs de comparaison PowerShell ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="452c5-117">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="452c5-118">En raison de considérations liées à l’analyse, les symboles tels que `<`,`>` et `=` ne sont pas utilisés comme opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="452c5-118">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="452c5-119">Au lieu de cela, les opérateurs de comparaison sont constitués de lettres.</span><span class="sxs-lookup"><span data-stu-id="452c5-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="452c5-120">Les opérateurs de comparaison de base sont répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="452c5-120">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="452c5-121">Opérateur de comparaison</span><span class="sxs-lookup"><span data-stu-id="452c5-121">Comparison Operator</span></span> |                  <span data-ttu-id="452c5-122">Signification</span><span class="sxs-lookup"><span data-stu-id="452c5-122">Meaning</span></span>                   |    <span data-ttu-id="452c5-123">Exemple (retourne true)</span><span class="sxs-lookup"><span data-stu-id="452c5-123">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="452c5-124">-eq</span><span class="sxs-lookup"><span data-stu-id="452c5-124">-eq</span></span>                 | <span data-ttu-id="452c5-125">Est égal à</span><span class="sxs-lookup"><span data-stu-id="452c5-125">is equal to</span></span>                                | <span data-ttu-id="452c5-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="452c5-126">1 -eq 1</span></span>                      |
| <span data-ttu-id="452c5-127">-ne</span><span class="sxs-lookup"><span data-stu-id="452c5-127">-ne</span></span>                 | <span data-ttu-id="452c5-128">N’est pas égal à</span><span class="sxs-lookup"><span data-stu-id="452c5-128">Is not equal to</span></span>                            | <span data-ttu-id="452c5-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="452c5-129">1 -ne 2</span></span>                      |
| <span data-ttu-id="452c5-130">-lt</span><span class="sxs-lookup"><span data-stu-id="452c5-130">-lt</span></span>                 | <span data-ttu-id="452c5-131">Est inférieur à</span><span class="sxs-lookup"><span data-stu-id="452c5-131">Is less than</span></span>                               | <span data-ttu-id="452c5-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="452c5-132">1 -lt 2</span></span>                      |
| <span data-ttu-id="452c5-133">-le</span><span class="sxs-lookup"><span data-stu-id="452c5-133">-le</span></span>                 | <span data-ttu-id="452c5-134">Est inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="452c5-134">Is less than or equal to</span></span>                   | <span data-ttu-id="452c5-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="452c5-135">1 -le 2</span></span>                      |
| <span data-ttu-id="452c5-136">-gt</span><span class="sxs-lookup"><span data-stu-id="452c5-136">-gt</span></span>                 | <span data-ttu-id="452c5-137">Est supérieur à</span><span class="sxs-lookup"><span data-stu-id="452c5-137">Is greater than</span></span>                            | <span data-ttu-id="452c5-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="452c5-138">2 -gt 1</span></span>                      |
| <span data-ttu-id="452c5-139">-ge</span><span class="sxs-lookup"><span data-stu-id="452c5-139">-ge</span></span>                 | <span data-ttu-id="452c5-140">Est supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="452c5-140">Is greater than or equal to</span></span>                | <span data-ttu-id="452c5-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="452c5-141">2 -ge 1</span></span>                      |
| <span data-ttu-id="452c5-142">-like</span><span class="sxs-lookup"><span data-stu-id="452c5-142">-like</span></span>               | <span data-ttu-id="452c5-143">Est comme (comparaison générique pour le texte)</span><span class="sxs-lookup"><span data-stu-id="452c5-143">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="452c5-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="452c5-144">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="452c5-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="452c5-145">-notlike</span></span>            | <span data-ttu-id="452c5-146">N’est pas comme (comparaison générique pour le texte)</span><span class="sxs-lookup"><span data-stu-id="452c5-146">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="452c5-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="452c5-147">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="452c5-148">-contains</span><span class="sxs-lookup"><span data-stu-id="452c5-148">-contains</span></span>           | <span data-ttu-id="452c5-149">Contient</span><span class="sxs-lookup"><span data-stu-id="452c5-149">Contains</span></span>                                   | <span data-ttu-id="452c5-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="452c5-150">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="452c5-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="452c5-151">-notcontains</span></span>        | <span data-ttu-id="452c5-152">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="452c5-152">Does not contain</span></span>                           | <span data-ttu-id="452c5-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="452c5-153">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="452c5-154">Les blocs de script `Where-Object` utilisent la variable spéciale `$_` pour faire référence à l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="452c5-154">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="452c5-155">Voici un exemple de son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="452c5-155">Here is an example of how it works.</span></span> <span data-ttu-id="452c5-156">Si vous avez une liste de nombres et souhaitez retourner uniquement ceux dont la valeur est inférieure à 3, vous pouvez utiliser `Where-Object` pour filtrer les nombres en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="452c5-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="452c5-157">Filtrage basé sur les propriétés de l’objet</span><span class="sxs-lookup"><span data-stu-id="452c5-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="452c5-158">Comme `$_` fait référence à l’objet de pipeline actif, nous pouvons accéder à ses propriétés pour nos tests.</span><span class="sxs-lookup"><span data-stu-id="452c5-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="452c5-159">Par exemple, nous pouvons examiner la classe **Win32_SystemDriver** dans WMI.</span><span class="sxs-lookup"><span data-stu-id="452c5-159">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="452c5-160">Il peut y avoir des centaines de pilotes système sur un système particulier, mais il se peut que vous vous intéressiez uniquement à certains pilotes, par exemple, à ceux qui sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="452c5-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="452c5-161">Pour la classe **Win32_SystemDriver** la propriété appropriée est **État**.</span><span class="sxs-lookup"><span data-stu-id="452c5-161">For the **Win32_SystemDriver** class the relevant property is **State**.</span></span> <span data-ttu-id="452c5-162">Vous pouvez filtrer les pilotes du système afin de sélectionner uniquement ceux qui sont en cours d’exécution, en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="452c5-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="452c5-163">Cela génère toujours une longue liste.</span><span class="sxs-lookup"><span data-stu-id="452c5-163">This still produces a long list.</span></span> <span data-ttu-id="452c5-164">Il se peut que vouliez filtrer afin de sélectionner uniquement les pilotes configurés pour démarrer automatiquement, en testant également la valeur **StartMode** :</span><span class="sxs-lookup"><span data-stu-id="452c5-164">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="452c5-165">Cela produit un grand nombre d’informations dont nous n’avons plus besoin, car nous savons que les pilotes sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="452c5-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="452c5-166">En fait, les seules informations dont nous ayons probablement besoin à ce stade sont le nom et le nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="452c5-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="452c5-167">La commande suivante inclut uniquement ces deux propriétés, de sorte que la sortie est beaucoup plus simple :</span><span class="sxs-lookup"><span data-stu-id="452c5-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="452c5-168">Il existe deux éléments `Where-Object` dans la commande ci-dessus, mais ils peuvent être exprimés en un seul élément `Where-Object` à l’aide de l’opérateur logique `-and` comme suit :</span><span class="sxs-lookup"><span data-stu-id="452c5-168">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="452c5-169">Les opérateurs logiques standards sont répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="452c5-169">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="452c5-170">Opérateur logique</span><span class="sxs-lookup"><span data-stu-id="452c5-170">Logical Operator</span></span> |                 <span data-ttu-id="452c5-171">Signification</span><span class="sxs-lookup"><span data-stu-id="452c5-171">Meaning</span></span>                  |  <span data-ttu-id="452c5-172">Exemple (retourne true)</span><span class="sxs-lookup"><span data-stu-id="452c5-172">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="452c5-173">-and</span><span class="sxs-lookup"><span data-stu-id="452c5-173">-and</span></span>             | <span data-ttu-id="452c5-174">Opérateur logique et ; true si les deux côtés sont vrais</span><span class="sxs-lookup"><span data-stu-id="452c5-174">Logical and; true if both sides are true</span></span> | <span data-ttu-id="452c5-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="452c5-175">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="452c5-176">-or</span><span class="sxs-lookup"><span data-stu-id="452c5-176">-or</span></span>              | <span data-ttu-id="452c5-177">Opérateur logique ou ; true si l’un des côtés est vrai</span><span class="sxs-lookup"><span data-stu-id="452c5-177">Logical or; true if either side is true</span></span>  | <span data-ttu-id="452c5-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="452c5-178">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="452c5-179">-not</span><span class="sxs-lookup"><span data-stu-id="452c5-179">-not</span></span>             | <span data-ttu-id="452c5-180">Opérateur logique non ; inverse les valeurs true et false</span><span class="sxs-lookup"><span data-stu-id="452c5-180">Logical not; reverses true and false</span></span>     | <span data-ttu-id="452c5-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="452c5-181">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="452c5-182">Opérateur logique non ; inverse les valeurs true et false</span><span class="sxs-lookup"><span data-stu-id="452c5-182">Logical not; reverses true and false</span></span>     | <span data-ttu-id="452c5-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="452c5-183">\!(1 -eq 2)</span></span>              |
