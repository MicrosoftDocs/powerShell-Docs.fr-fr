---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: e98de608630a59ff77ca701876986ffb29780a4a
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "99603673"
---
# <span data-ttu-id="8708c-102">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="8708c-102">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="8708c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8708c-103">SYNOPSIS</span></span>

<span data-ttu-id="8708c-104">Inscrit un finaliseur d’argument personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8708c-104">Registers a custom argument completer.</span></span>

## <span data-ttu-id="8708c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8708c-105">SYNTAX</span></span>

### <span data-ttu-id="8708c-106">NativeSet</span><span class="sxs-lookup"><span data-stu-id="8708c-106">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="8708c-107">PowerShellSet</span><span class="sxs-lookup"><span data-stu-id="8708c-107">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="8708c-108">Description</span><span class="sxs-lookup"><span data-stu-id="8708c-108">DESCRIPTION</span></span>

<span data-ttu-id="8708c-109">L' `Register-ArgumentCompleter` applet de commande inscrit un finaliseur d’argument personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8708c-109">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="8708c-110">Un argument Complete vous permet de fournir une saisie semi-automatique par tabulation dynamique, au moment de l’exécution pour toute commande que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="8708c-110">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="8708c-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8708c-111">EXAMPLES</span></span>

### <span data-ttu-id="8708c-112">Exemple 1 : inscrire un finaliseur d’argument personnalisé</span><span class="sxs-lookup"><span data-stu-id="8708c-112">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="8708c-113">L’exemple suivant inscrit un argument Complete pour le paramètre **ID** de l’applet de commande `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="8708c-113">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

<span data-ttu-id="8708c-114">La première commande crée un bloc de script qui prend les paramètres requis qui sont transmis quand l’utilisateur appuie sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez la description du paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="8708c-114">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="8708c-115">Dans le bloc de script, les valeurs disponibles pour **ID** sont extraites à l’aide de l’applet de commande `Get-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="8708c-115">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="8708c-116">La propriété **ID** de chaque fuseau horaire est dirigée vers l' `Where-Object` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8708c-116">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="8708c-117">L' `Where-Object` applet de commande filtre tous les ID qui ne commencent pas par la valeur fournie par `$wordToComplete` , qui représente le texte que l’utilisateur a tapé avant d’appuyer sur la touche <kbd>Tab</kbd>. Les ID filtrés sont dirigés vers l’applet de commande `ForEach-Object` qui englobe chaque valeur entre guillemets, si la valeur contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="8708c-117">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `ForEach-Object` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="8708c-118">La deuxième commande inscrit l’argument completer en passant le scriptblock, l’ID **ParameterName**  et le **CommandName** `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="8708c-118">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="8708c-119">Exemple 2 : ajouter des détails à vos valeurs de saisie semi-automatique par tabulation</span><span class="sxs-lookup"><span data-stu-id="8708c-119">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="8708c-120">L’exemple suivant remplace la saisie semi-automatique par tabulation pour le paramètre **Name** de l’applet de commande `Stop-Service` et retourne uniquement les services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8708c-120">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

<span data-ttu-id="8708c-121">La première commande crée un bloc de script qui prend les paramètres requis qui sont transmis quand l’utilisateur appuie sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez la description du paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="8708c-121">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="8708c-122">Dans le bloc de script, la première commande récupère tous les services en cours d’exécution à l’aide de l’applet de commande `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="8708c-122">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="8708c-123">Les services sont dirigés vers l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="8708c-123">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="8708c-124">L' `ForEach-Object` applet de commande crée un nouvel objet [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) et le remplit avec le nom du service actuel (représenté par la variable de pipeline `$_.Name` ).</span><span class="sxs-lookup"><span data-stu-id="8708c-124">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="8708c-125">L’objet **CompletionResult** vous permet de fournir des détails supplémentaires à chaque valeur retournée :</span><span class="sxs-lookup"><span data-stu-id="8708c-125">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="8708c-126">**completionText** (String) : texte à utiliser comme résultat de la saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="8708c-126">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="8708c-127">Il s’agit de la valeur envoyée à la commande.</span><span class="sxs-lookup"><span data-stu-id="8708c-127">This is the value sent to the command.</span></span>
- <span data-ttu-id="8708c-128">**listItemText** (String) : texte à afficher dans une liste, par exemple lorsque l’utilisateur appuie sur <kbd>CTRL</kbd> + <kbd>Space</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8708c-128">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="8708c-129">Cela est utilisé pour l’affichage uniquement et n’est pas passé à la commande quand elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8708c-129">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="8708c-130">**ResultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) : type de résultat de la saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="8708c-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="8708c-131">**info-bulle** (String) : texte de l’info-bulle contenant les détails à afficher à propos de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8708c-131">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="8708c-132">Cela est visible lorsque l’utilisateur sélectionne un élément après avoir appuyé sur <kbd>CTRL</kbd> + <kbd>Space</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8708c-132">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="8708c-133">La dernière commande montre que les services arrêtés peuvent toujours être passés manuellement à l' `Stop-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8708c-133">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="8708c-134">La saisie semi-automatique par tabulation est le seul aspect affecté.</span><span class="sxs-lookup"><span data-stu-id="8708c-134">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="8708c-135">Exemple 3 : inscrire un finaliseur d’argument natif personnalisé</span><span class="sxs-lookup"><span data-stu-id="8708c-135">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="8708c-136">Vous pouvez utiliser le paramètre **Native** pour fournir la saisie semi-automatique par tabulation pour une commande native.</span><span class="sxs-lookup"><span data-stu-id="8708c-136">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="8708c-137">L’exemple suivant ajoute la saisie semi-automatique par tabulation pour l' `dotnet` interface de ligne de commande (CLI).</span><span class="sxs-lookup"><span data-stu-id="8708c-137">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="8708c-138">La `dotnet complete` commande est disponible uniquement dans la version 2,0 et les versions ultérieures de l’interface CLI dotnet.</span><span class="sxs-lookup"><span data-stu-id="8708c-138">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="8708c-139">La première commande crée un bloc de script qui prend les paramètres requis qui sont transmis quand l’utilisateur appuie sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez la description du paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="8708c-139">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="8708c-140">Dans le bloc de script, la `dotnet complete` commande est utilisée pour effectuer la saisie semi-automatique via la touche Tab.</span><span class="sxs-lookup"><span data-stu-id="8708c-140">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="8708c-141">Les résultats sont dirigés vers l’applet de commande `ForEach-Object` qui utilise la **nouvelle** méthode statique de la classe [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) pour créer un nouvel objet **CompletionResult** pour chaque valeur.</span><span class="sxs-lookup"><span data-stu-id="8708c-141">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="8708c-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8708c-142">PARAMETERS</span></span>

### <span data-ttu-id="8708c-143">-CommandName</span><span class="sxs-lookup"><span data-stu-id="8708c-143">-CommandName</span></span>

<span data-ttu-id="8708c-144">Spécifie le nom des commandes sous la forme d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="8708c-144">Specifies the name of the commands as an array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8708c-145">-Natif</span><span class="sxs-lookup"><span data-stu-id="8708c-145">-Native</span></span>

<span data-ttu-id="8708c-146">Indique que l’argument Complete est destiné à une commande Native où PowerShell ne peut pas terminer les noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8708c-146">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8708c-147">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="8708c-147">-ParameterName</span></span>

<span data-ttu-id="8708c-148">Spécifie le nom du paramètre dont l’argument est terminé.</span><span class="sxs-lookup"><span data-stu-id="8708c-148">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="8708c-149">Le nom de paramètre spécifié ne peut pas être une valeur énumérée, telle que le paramètre **ForegroundColor** de l’applet de commande `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="8708c-149">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="8708c-150">Pour plus d’informations sur les enums, consultez [about_Enum](./About/about_Enum.md).</span><span class="sxs-lookup"><span data-stu-id="8708c-150">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8708c-151">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="8708c-151">-ScriptBlock</span></span>

<span data-ttu-id="8708c-152">Spécifie les commandes à exécuter pour effectuer la saisie semi-automatique via la touche Tab.</span><span class="sxs-lookup"><span data-stu-id="8708c-152">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="8708c-153">Le bloc de script que vous fournissez doit retourner les valeurs qui complètent l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8708c-153">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="8708c-154">Le bloc de script doit dérouler les valeurs à l’aide du pipeline ( `ForEach-Object` , `Where-Object` , etc.) ou d’une autre méthode appropriée.</span><span class="sxs-lookup"><span data-stu-id="8708c-154">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="8708c-155">Le retour d’un tableau de valeurs amène PowerShell à traiter l’intégralité du tableau comme **une** valeur de saisie semi-automatique de tabulation.</span><span class="sxs-lookup"><span data-stu-id="8708c-155">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="8708c-156">Le bloc de script doit accepter les paramètres suivants dans l’ordre indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8708c-156">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="8708c-157">Les noms des paramètres ne sont pas importants, car PowerShell passe les valeurs par position.</span><span class="sxs-lookup"><span data-stu-id="8708c-157">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="8708c-158">`$commandName` (Position 0)-ce paramètre est défini sur le nom de la commande pour laquelle le bloc de script fournit la saisie semi-automatique par tabulation.</span><span class="sxs-lookup"><span data-stu-id="8708c-158">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="8708c-159">`$parameterName` (Position 1)-ce paramètre est défini sur le paramètre dont la valeur nécessite la saisie semi-automatique par tabulation.</span><span class="sxs-lookup"><span data-stu-id="8708c-159">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="8708c-160">`$wordToComplete` (Position 2)-ce paramètre est défini sur la valeur que l’utilisateur a fournie avant d’appuyer sur la touche <kbd>Tab</kbd>. Votre bloc de script doit utiliser cette valeur pour déterminer les valeurs de saisie semi-automatique de l’onglet.</span><span class="sxs-lookup"><span data-stu-id="8708c-160">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="8708c-161">`$commandAst` (Position 3)-ce paramètre est défini sur l’arborescence de syntaxe abstraite (AST) pour la ligne d’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="8708c-161">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="8708c-162">Pour plus d’informations, consultez la [classe AST](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="8708c-162">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="8708c-163">`$fakeBoundParameters` (Position 4)-ce paramètre est défini sur une valeur Hashtable contenant le `$PSBoundParameters` pour l’applet de commande, avant que l’utilisateur ait appuyé sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8708c-163">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="8708c-164">Lorsque vous spécifiez le paramètre **Native** , le bloc de script doit prendre les paramètres suivants dans l’ordre spécifié.</span><span class="sxs-lookup"><span data-stu-id="8708c-164">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="8708c-165">Les noms des paramètres ne sont pas importants, car PowerShell passe les valeurs par position.</span><span class="sxs-lookup"><span data-stu-id="8708c-165">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="8708c-166">`$wordToComplete` (Position 0)-ce paramètre est défini sur la valeur que l’utilisateur a fournie avant d’appuyer sur la touche <kbd>Tab</kbd>. Votre bloc de script doit utiliser cette valeur pour déterminer les valeurs de saisie semi-automatique de l’onglet.</span><span class="sxs-lookup"><span data-stu-id="8708c-166">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="8708c-167">`$commandAst` (Position 1)-ce paramètre est défini sur l’arborescence de syntaxe abstraite (AST) pour la ligne d’entrée actuelle.</span><span class="sxs-lookup"><span data-stu-id="8708c-167">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="8708c-168">Pour plus d’informations, consultez la [classe AST](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="8708c-168">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="8708c-169">`$cursorPosition` (Position 2)-ce paramètre est défini sur la position du curseur lorsque l’utilisateur a appuyé sur la touche <kbd>Tab</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8708c-169">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="8708c-170">Vous pouvez également fournir un **ArgumentCompleter** en tant qu’attribut de paramètre.</span><span class="sxs-lookup"><span data-stu-id="8708c-170">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="8708c-171">Pour plus d’informations, consultez [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8708c-171">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8708c-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8708c-172">CommonParameters</span></span>

<span data-ttu-id="8708c-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8708c-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8708c-174">Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="8708c-174">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8708c-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8708c-175">INPUTS</span></span>

### <span data-ttu-id="8708c-176">None</span><span class="sxs-lookup"><span data-stu-id="8708c-176">None</span></span>

<span data-ttu-id="8708c-177">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8708c-177">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="8708c-178">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8708c-178">OUTPUTS</span></span>

### <span data-ttu-id="8708c-179">None</span><span class="sxs-lookup"><span data-stu-id="8708c-179">None</span></span>

<span data-ttu-id="8708c-180">Cette applet de commande ne retourne pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="8708c-180">This cmdlet returns no output.</span></span>

## <span data-ttu-id="8708c-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8708c-181">NOTES</span></span>

## <span data-ttu-id="8708c-182">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8708c-182">RELATED LINKS</span></span>

