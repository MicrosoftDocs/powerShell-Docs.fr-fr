---
description: Décrit comment les variables stockent des valeurs qui peuvent être utilisées dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 0865afe69f5f1774e90d2d2dc5827d628cab0f6a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206697"
---
# <a name="about-variables"></a><span data-ttu-id="ee8d8-104">À propos des variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-104">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="ee8d8-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="ee8d8-105">Short description</span></span>

<span data-ttu-id="ee8d8-106">Décrit comment les variables stockent des valeurs qui peuvent être utilisées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-106">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ee8d8-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="ee8d8-107">Long description</span></span>

<span data-ttu-id="ee8d8-108">Vous pouvez stocker tous les types de valeurs dans les variables PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-108">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="ee8d8-109">Par exemple, stockez les résultats des commandes et stockez les éléments utilisés dans les commandes et les expressions, telles que les noms, les chemins d’accès, les paramètres et les valeurs.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-109">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="ee8d8-110">Une variable est une unité de mémoire dans laquelle les valeurs sont stockées.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-110">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="ee8d8-111">Dans PowerShell, les variables sont représentées par des chaînes de texte qui commencent par un signe dollar ( `$` ), telles que `$a` , `$process` ou `$my_var` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-111">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="ee8d8-112">Les noms de variable ne respectent pas la casse et peuvent inclure des espaces et des caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-112">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="ee8d8-113">Toutefois, les noms de variables qui contiennent des caractères spéciaux et des espaces sont difficiles à utiliser et doivent être évités.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-113">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="ee8d8-114">Pour plus d’informations, consultez [noms de variables qui contiennent des caractères spéciaux](#variable-names-that-include-special-characters).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-114">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="ee8d8-115">Il existe différents types de variables dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-115">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="ee8d8-116">Variables créées par l’utilisateur : les variables créées par l’utilisateur sont créées et gérées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-116">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="ee8d8-117">Par défaut, les variables que vous créez au niveau de la ligne de commande PowerShell existent uniquement lorsque la fenêtre PowerShell est ouverte.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-117">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="ee8d8-118">Une fois la fenêtre PowerShell fermée, les variables sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-118">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="ee8d8-119">Pour enregistrer une variable, ajoutez-la à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-119">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="ee8d8-120">Vous pouvez également créer des variables dans des scripts avec une portée globale, de script ou locale.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-120">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="ee8d8-121">Variables automatiques : les variables automatiques stockent l’état de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-121">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="ee8d8-122">Ces variables sont créées par PowerShell et PowerShell modifie leurs valeurs selon les besoins afin de conserver leur exactitude.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-122">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="ee8d8-123">Les utilisateurs ne peuvent pas modifier la valeur de ces variables.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-123">Users can't change the value of these variables.</span></span> <span data-ttu-id="ee8d8-124">Par exemple, la `$PSHOME` variable stocke le chemin d’accès au répertoire d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-124">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="ee8d8-125">Pour plus d’informations, une liste et une description des variables automatiques, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-125">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="ee8d8-126">Variables de préférence : les variables de préférence stockent les préférences utilisateur pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-126">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="ee8d8-127">Ces variables sont créées par PowerShell et sont remplies avec les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-127">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="ee8d8-128">Les utilisateurs peuvent modifier les valeurs de ces variables.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-128">Users can change the values of these variables.</span></span> <span data-ttu-id="ee8d8-129">Par exemple, la `$MaximumHistoryCount` variable détermine le nombre maximal d’entrées dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-129">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="ee8d8-130">Pour plus d’informations, une liste et une description des variables de préférence, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-130">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="ee8d8-131">Utilisation de variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-131">Working with variables</span></span>

<span data-ttu-id="ee8d8-132">Pour créer une variable, utilisez une instruction d’assignation pour assigner une valeur à la variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-132">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="ee8d8-133">Vous n’avez pas besoin de déclarer la variable avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-133">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="ee8d8-134">La valeur par défaut de toutes les variables est `$null` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-134">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="ee8d8-135">Pour obtenir la liste de toutes les variables de votre session PowerShell, tapez `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-135">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="ee8d8-136">Les noms de variables s’affichent sans le signe dollar ( `$` ) qui est utilisé pour référencer des variables.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-136">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="ee8d8-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-137">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="ee8d8-138">Les variables sont utiles pour stocker les résultats des commandes.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-138">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="ee8d8-139">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-139">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="ee8d8-140">Pour afficher la valeur d’une variable, tapez le nom de la variable, précédé d’un signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-140">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="ee8d8-141">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-141">For example:</span></span>

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

<span data-ttu-id="ee8d8-142">Pour modifier la valeur d’une variable, assignez une nouvelle valeur à la variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-142">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="ee8d8-143">Les exemples suivants affichent la valeur de la `$MyVariable` variable, modifient la valeur de la variable, puis affiche la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-143">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

<span data-ttu-id="ee8d8-144">Pour supprimer la valeur d’une variable, utilisez l' `Clear-Variable` applet de commande ou remplacez la valeur par `$null` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-144">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="ee8d8-145">Pour supprimer la variable, utilisez [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) ou [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-145">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="ee8d8-146">Types de variable</span><span class="sxs-lookup"><span data-stu-id="ee8d8-146">Types of variables</span></span>

<span data-ttu-id="ee8d8-147">Vous pouvez stocker n’importe quel type d’objet dans une variable, y compris des entiers, des chaînes, des tableaux et des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-147">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="ee8d8-148">Et, objets qui représentent des processus, des services, des journaux des événements et des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-148">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="ee8d8-149">Les variables PowerShell sont faiblement typées, ce qui signifie qu’elles ne sont pas limitées à un type particulier d’objet.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-149">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="ee8d8-150">Une variable unique peut même contenir une collection ou un tableau de différents types d’objets en même temps.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-150">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="ee8d8-151">Le type de données d’une variable est déterminé par les types .NET des valeurs de la variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-151">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="ee8d8-152">Pour afficher le type d’objet d’une variable, utilisez la valeur de l' [élément obtenir un membre](xref:Microsoft.PowerShell.Utility.Get-Member).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-152">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="ee8d8-153">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-153">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="ee8d8-154">Vous pouvez utiliser un attribut de type et une notation cast pour vous assurer qu’une variable peut contenir uniquement des types d’objets ou des objets spécifiques qui peuvent être convertis en ce type.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-154">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="ee8d8-155">Si vous essayez d’assigner une valeur d’un autre type, PowerShell tente de convertir la valeur en son type.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-155">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="ee8d8-156">Si le type ne peut pas être converti, l’instruction d’assignation échoue.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-156">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="ee8d8-157">Pour utiliser la notation Cast, entrez un nom de type, placé entre parenthèses, avant le nom de la variable (sur le côté gauche de l’instruction d’assignation).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-157">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="ee8d8-158">L’exemple suivant crée une `$number` variable qui ne peut contenir que des entiers, une `$words` variable qui ne peut contenir que des chaînes et une `$dates` variable qui ne peut contenir que des objets **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-158">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="ee8d8-159">Utilisation de variables dans des commandes et des expressions</span><span class="sxs-lookup"><span data-stu-id="ee8d8-159">Using variables in commands and expressions</span></span>

<span data-ttu-id="ee8d8-160">Pour utiliser une variable dans une commande ou une expression, tapez le nom de la variable, précédé du signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-160">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="ee8d8-161">Si le nom de la variable et le signe dollar ne sont pas placés entre guillemets, ou s’ils sont placés entre guillemets doubles ( `"` ), la valeur de la variable est utilisée dans la commande ou l’expression.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-161">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="ee8d8-162">Si le nom de la variable et le signe dollar sont placés entre guillemets simples ( `'` ), le nom de la variable est utilisé dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-162">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="ee8d8-163">Pour plus d’informations sur l’utilisation des guillemets dans PowerShell, consultez [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-163">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="ee8d8-164">Cet exemple obtient la valeur de la `$PROFILE` variable, qui est le chemin d’accès au fichier de profil utilisateur PowerShell dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-164">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="ee8d8-165">Dans cet exemple, deux commandes qui permettent d’ouvrir le profil PowerShell dans **notepad.exe** sont affichées.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-165">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe** .</span></span> <span data-ttu-id="ee8d8-166">L’exemple avec des marques à guillemet double ( `"` ) utilise la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-166">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="ee8d8-167">Les exemples suivants utilisent des marques à guillemet simple ( `'` ) qui traitent la variable comme du texte littéral.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-167">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="ee8d8-168">Noms de variables qui contiennent des caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="ee8d8-168">Variable names that include special characters</span></span>

<span data-ttu-id="ee8d8-169">Les noms de variables commencent par un `$` signe dollar () et peuvent inclure des caractères alphanumériques et des caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-169">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="ee8d8-170">La longueur du nom de la variable n’est limitée que par la mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-170">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="ee8d8-171">La meilleure pratique est que les noms de variables incluent uniquement des caractères alphanumériques et le caractère de soulignement ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-171">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="ee8d8-172">Les noms de variables qui incluent des espaces et d’autres caractères spéciaux sont difficiles à utiliser et doivent être évités.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-172">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="ee8d8-173">Les noms de variables alphanumériques peuvent contenir les caractères suivants :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-173">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="ee8d8-174">Caractères Unicode de ces catégories : **lu** , **ll** , **lt** , **LM** , **Lo** ou **ND** .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-174">Unicode characters from these categories: **Lu** , **Ll** , **Lt** , **Lm** , **Lo** , or **Nd** .</span></span>
- <span data-ttu-id="ee8d8-175">Caractère de soulignement ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-175">Underscore (`_`) character.</span></span>
- <span data-ttu-id="ee8d8-176">Point d’interrogation ( `?` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-176">Question mark (`?`) character.</span></span>

<span data-ttu-id="ee8d8-177">La liste suivante contient les descriptions des catégories Unicode.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-177">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="ee8d8-178">Pour plus d’informations, consultez [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-178">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="ee8d8-179">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="ee8d8-179">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="ee8d8-180">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="ee8d8-180">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="ee8d8-181">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="ee8d8-181">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="ee8d8-182">**LM** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="ee8d8-182">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="ee8d8-183">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="ee8d8-183">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="ee8d8-184">**ND** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="ee8d8-184">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="ee8d8-185">Pour créer ou afficher un nom de variable qui comprend des espaces ou des caractères spéciaux, placez le nom de la variable entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-185">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="ee8d8-186">Les accolades redirigent PowerShell pour interpréter les caractères du nom de la variable comme des littéraux.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-186">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="ee8d8-187">Les noms de variable de caractères spéciaux peuvent contenir les caractères suivants :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-187">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="ee8d8-188">N’importe quel caractère Unicode, avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-188">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="ee8d8-189">Caractère d’accolade fermante ( `}` ) (U + 007D).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-189">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="ee8d8-190">`` ` ``Caractère de soulignement () (U + 0060).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-190">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="ee8d8-191">L’accent est utilisé pour échapper les caractères Unicode afin qu’ils soient traités comme des littéraux.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-191">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="ee8d8-192">PowerShell a des variables réservées telles que `$$` ,, `$?` `$^` et `$_` qui contiennent des caractères alphanumériques et spéciaux.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-192">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="ee8d8-193">Pour plus d’informations, consultez [about_Automatic_Variables](about_automatic_variables.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-193">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="ee8d8-194">Par exemple, la commande suivante crée la variable nommée `save-items` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-194">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="ee8d8-195">Les accolades ( `{}` ) sont nécessaires, car le nom de la variable comprend un caractère spécial de trait d’Union ( `-` ).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-195">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="ee8d8-196">La commande suivante obtient les éléments enfants dans le répertoire qui est représenté par la `ProgramFiles(x86)` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-196">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="ee8d8-197">Pour faire référence à un nom de variable qui comprend des accolades, placez le nom de la variable entre accolades et utilisez le caractère d’échappement pour échapper les accolades.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-197">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="ee8d8-198">Par exemple, pour créer une variable nommée `this{value}is` type :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-198">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="ee8d8-199">Variables et portée</span><span class="sxs-lookup"><span data-stu-id="ee8d8-199">Variables and scope</span></span>

<span data-ttu-id="ee8d8-200">Par défaut, les variables sont uniquement disponibles dans l’étendue dans laquelle elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-200">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="ee8d8-201">Par exemple, une variable que vous créez dans une fonction est disponible uniquement dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-201">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="ee8d8-202">Une variable que vous créez dans un script est uniquement disponible dans le script.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-202">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="ee8d8-203">Si vous pointez la source du script, la variable est ajoutée à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-203">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="ee8d8-204">Pour plus d’informations, consultez [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-204">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="ee8d8-205">Vous pouvez utiliser un modificateur d’étendue pour modifier l’étendue par défaut de la variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-205">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="ee8d8-206">L’expression suivante crée une variable nommée `Computers` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-206">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="ee8d8-207">La variable a une portée globale, même lorsqu’elle est créée dans un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-207">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="ee8d8-208">Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-208">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="ee8d8-209">Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-209">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="ee8d8-210">Enregistrement de variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-210">Saving variables</span></span>

<span data-ttu-id="ee8d8-211">Les variables que vous créez sont disponibles uniquement dans la session dans laquelle vous les créez.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-211">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="ee8d8-212">Ils sont perdus quand vous fermez votre session.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-212">They're lost when you close your session.</span></span>

<span data-ttu-id="ee8d8-213">Pour créer la variable dans chaque session PowerShell que vous démarrez, ajoutez la variable à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-213">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="ee8d8-214">Par exemple, pour modifier la valeur de la `$VerbosePreference` variable dans chaque session PowerShell, ajoutez la commande suivante à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-214">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="ee8d8-215">Vous pouvez ajouter cette commande à votre profil PowerShell en ouvrant le `$PROFILE` fichier dans un éditeur de texte, tel que **notepad.exe** .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-215">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe** .</span></span> <span data-ttu-id="ee8d8-216">Pour plus d’informations sur les profils PowerShell, voir [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ee8d8-216">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="ee8d8-217">Le lecteur variable :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-217">The Variable: drive</span></span>

<span data-ttu-id="ee8d8-218">Le fournisseur de variables PowerShell crée un `Variable:` lecteur qui ressemble à un lecteur du système de fichiers, mais il contient les variables de votre session et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-218">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="ee8d8-219">Pour passer au `Variable:` lecteur, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-219">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="ee8d8-220">Pour répertorier les éléments et les variables dans le `Variable:` lecteur, utilisez les `Get-Item` applets de commande ou `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-220">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="ee8d8-221">Pour obtenir la valeur d’une variable particulière, utilisez la notation du système de fichiers pour spécifier le nom du lecteur et le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-221">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="ee8d8-222">Par exemple, pour obtenir la `$PSCulture` variable automatique, utilisez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-222">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="ee8d8-223">Pour afficher plus d’informations sur le `Variable:` lecteur et le fournisseur de variable PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-223">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="ee8d8-224">Syntaxe de variable avec chemins d’accès de fournisseur</span><span class="sxs-lookup"><span data-stu-id="ee8d8-224">Variable syntax with provider paths</span></span>

<span data-ttu-id="ee8d8-225">Vous pouvez préfixer un chemin d’accès de fournisseur avec le signe dollar ( `$` ) et accéder au contenu de n’importe quel fournisseur qui implémente l’interface [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) .</span><span class="sxs-lookup"><span data-stu-id="ee8d8-225">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="ee8d8-226">Les fournisseurs PowerShell intégrés suivants prennent en charge cette notation :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-226">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="ee8d8-227">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="ee8d8-227">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="ee8d8-228">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="ee8d8-228">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="ee8d8-229">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="ee8d8-229">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="ee8d8-230">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="ee8d8-230">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="ee8d8-231">Applets de commande de variable</span><span class="sxs-lookup"><span data-stu-id="ee8d8-231">The variable cmdlets</span></span>

<span data-ttu-id="ee8d8-232">PowerShell comprend un ensemble d’applets de commande conçues pour gérer des variables.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-232">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="ee8d8-233">Pour répertorier les applets de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-233">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="ee8d8-234">Pour obtenir de l’aide pour une applet de commande spécifique, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee8d8-234">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="ee8d8-235">Nom de l'applet de commande</span><span class="sxs-lookup"><span data-stu-id="ee8d8-235">Cmdlet Name</span></span>       | <span data-ttu-id="ee8d8-236">Description</span><span class="sxs-lookup"><span data-stu-id="ee8d8-236">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="ee8d8-237">Supprime la valeur d'une variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-237">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="ee8d8-238">Obtient les variables dans la console active.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-238">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="ee8d8-239">Crée une variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-239">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="ee8d8-240">Supprime une variable et sa valeur.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-240">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="ee8d8-241">Modifie la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="ee8d8-241">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="ee8d8-242">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee8d8-242">See also</span></span>

[<span data-ttu-id="ee8d8-243">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-243">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="ee8d8-244">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-244">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="ee8d8-245">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-245">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="ee8d8-246">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ee8d8-246">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="ee8d8-247">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="ee8d8-247">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="ee8d8-248">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="ee8d8-248">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="ee8d8-249">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="ee8d8-249">about_Remote_Variables</span></span>](about_Remote_Variables.md)

