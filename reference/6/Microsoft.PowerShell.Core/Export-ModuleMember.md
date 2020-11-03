---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: ed08e68279b436ea5a3c040729d70990700ebdfa
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204906"
---
# <span data-ttu-id="ee759-103">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="ee759-103">Export-ModuleMember</span></span>

## <span data-ttu-id="ee759-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ee759-104">SYNOPSIS</span></span>
<span data-ttu-id="ee759-105">Spécifie les membres de module exportés.</span><span class="sxs-lookup"><span data-stu-id="ee759-105">Specifies the module members that are exported.</span></span>

## <span data-ttu-id="ee759-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee759-106">SYNTAX</span></span>

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="ee759-107">Description</span><span class="sxs-lookup"><span data-stu-id="ee759-107">DESCRIPTION</span></span>

<span data-ttu-id="ee759-108">L’applet de commande **Export-ModuleMember** spécifie les membres de module exportés à partir d’un fichier de module de script (. psm1), ou à partir d’un module dynamique créé à l’aide de l’applet de commande New-Module.</span><span class="sxs-lookup"><span data-stu-id="ee759-108">The **Export-ModuleMember** cmdlet specifies the module members that are exported from a script module (.psm1) file, or from a dynamic module created by using the New-Module cmdlet.</span></span>
<span data-ttu-id="ee759-109">Les membres de module incluent des applets de commande, des fonctions, des variables et des alias.</span><span class="sxs-lookup"><span data-stu-id="ee759-109">Module members include cmdlets, functions, variables, and aliases.</span></span>
<span data-ttu-id="ee759-110">Cette applet de commande peut être utilisée uniquement dans un fichier de module de script ou un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="ee759-110">This cmdlet can be used only in a script module file or a dynamic module.</span></span>

<span data-ttu-id="ee759-111">Si un module de script n’inclut pas de commande **Export-ModuleMember** , les fonctions et les alias dans le module de script sont exportés, mais les variables ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="ee759-111">If a script module does not include an **Export-ModuleMember** command, the functions and aliases in the script module are exported, but the variables are not.</span></span>
<span data-ttu-id="ee759-112">Quand un module de script comprend des commandes **Export-ModuleMember** , seuls les membres spécifiés dans les commandes **Export-ModuleMember** sont exportés.</span><span class="sxs-lookup"><span data-stu-id="ee759-112">When a script module includes **Export-ModuleMember** commands, only the members specified in the **Export-ModuleMember** commands are exported.</span></span>
<span data-ttu-id="ee759-113">Vous pouvez également utiliser **Export-ModuleMember** pour supprimer ou exporter des membres que le module de script importe à partir d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="ee759-113">You can also use **Export-ModuleMember** to suppress or export members that the script module imports from other modules.</span></span>

<span data-ttu-id="ee759-114">Une commande **Export-ModuleMember** est facultative, mais il s’agit d’une bonne pratique.</span><span class="sxs-lookup"><span data-stu-id="ee759-114">An **Export-ModuleMember** command is optional, but it is a best practice.</span></span>
<span data-ttu-id="ee759-115">Même si la commande confirme les valeurs par défaut, elle illustre l'intention de l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="ee759-115">Even if the command confirms the default values, it demonstrates the intention of the module author.</span></span>

## <span data-ttu-id="ee759-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ee759-116">EXAMPLES</span></span>

### <span data-ttu-id="ee759-117">Exemple 1 : exporter des fonctions et des alias dans un module de script</span><span class="sxs-lookup"><span data-stu-id="ee759-117">Example 1: Export functions and aliases in a script module</span></span>

```powershell
Export-ModuleMember -Function * -Alias *
```

<span data-ttu-id="ee759-118">Cette commande exporte toutes les fonctions et les alias définis dans le module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-118">This command exports all the functions and aliases defined in the script module.</span></span>

### <span data-ttu-id="ee759-119">Exemple 2 : exporter des alias et des fonctions spécifiques</span><span class="sxs-lookup"><span data-stu-id="ee759-119">Example 2: Export specific aliases and functions</span></span>

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

<span data-ttu-id="ee759-120">Cette commande exporte trois alias et trois fonctions définies dans le module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-120">This command exports three aliases and three functions defined in the script module.</span></span>

<span data-ttu-id="ee759-121">Vous pouvez utiliser ce format de commande pour spécifier les noms des membres de module.</span><span class="sxs-lookup"><span data-stu-id="ee759-121">You can use this command format to specify the names of module members.</span></span>

### <span data-ttu-id="ee759-122">Exemple 3 : exporter aucun membre</span><span class="sxs-lookup"><span data-stu-id="ee759-122">Example 3: Export no members</span></span>

```powershell
Export-ModuleMember
```

<span data-ttu-id="ee759-123">Cette commande spécifie qu'aucun membre défini dans le module de script n'est exporté.</span><span class="sxs-lookup"><span data-stu-id="ee759-123">This command specifies that no members defined in the script module are exported.</span></span>

<span data-ttu-id="ee759-124">Cette commande empêche l'exportation des membres du module, mais elle ne masque pas les membres.</span><span class="sxs-lookup"><span data-stu-id="ee759-124">This command prevents the module members from being exported, but it does not hide the members.</span></span>
<span data-ttu-id="ee759-125">Les utilisateurs peuvent lire et copier les membres de module, ou utiliser l'opérateur d'appel (&) pour appeler les membres de module qui ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="ee759-125">Users can read and copy module members or use the call operator (&) to invoke module members that are not exported.</span></span>

### <span data-ttu-id="ee759-126">Exemple 4 : exporter une variable spécifique</span><span class="sxs-lookup"><span data-stu-id="ee759-126">Example 4: Export a specific variable</span></span>

```powershell
Export-ModuleMember -Variable increment
```

<span data-ttu-id="ee759-127">Cette commande exporte uniquement la variable $increment à partir du module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-127">This command exports only the $increment variable from the script module.</span></span>
<span data-ttu-id="ee759-128">Aucun autre membre n'est exporté.</span><span class="sxs-lookup"><span data-stu-id="ee759-128">No other members are exported.</span></span>

<span data-ttu-id="ee759-129">Si vous souhaitez exporter une variable, outre l’exportation des fonctions dans un module, la commande **Export-ModuleMember** doit inclure les noms de toutes les fonctions et le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="ee759-129">If you want to export a variable, in addition to exporting the functions in a module, the **Export-ModuleMember** command must include the names of all of the functions and the name of the variable.</span></span>

### <span data-ttu-id="ee759-130">Exemple 5 : commandes d’exportation multiples</span><span class="sxs-lookup"><span data-stu-id="ee759-130">Example 5: Multiple export commands</span></span>

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

<span data-ttu-id="ee759-131">Ces commandes montrent comment plusieurs commandes **Export-ModuleMember** sont interprétées dans un fichier de module de script (. psm1).</span><span class="sxs-lookup"><span data-stu-id="ee759-131">These commands show how multiple **Export-ModuleMember** commands are interpreted in a script module (.psm1) file.</span></span>

<span data-ttu-id="ee759-132">Ces commandes créent trois fonctions et un alias, puis exportent deux des fonctions et l'alias.</span><span class="sxs-lookup"><span data-stu-id="ee759-132">These commands create three functions and one alias, and then they export two of the functions and the alias.</span></span>

<span data-ttu-id="ee759-133">Sans les commandes **Export-ModuleMember** , les trois fonctions et l’alias seront exportés.</span><span class="sxs-lookup"><span data-stu-id="ee759-133">Without the **Export-ModuleMember** commands, all three of the functions and the alias would be exported.</span></span>
<span data-ttu-id="ee759-134">Avec les commandes **Export-ModuleMember** , seules les fonctions **New-Test** et **Start-test** et l’alias STT sont exportées.</span><span class="sxs-lookup"><span data-stu-id="ee759-134">With the **Export-ModuleMember** commands, only the **New-Test** and **Start-Test** functions and the STT alias are exported.</span></span>

### <span data-ttu-id="ee759-135">Exemple 6 : exporter des membres dans un module dynamique</span><span class="sxs-lookup"><span data-stu-id="ee759-135">Example 6: Export members in a dynamic module</span></span>

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

<span data-ttu-id="ee759-136">Cette commande montre comment utiliser Export-ModuleMember dans un module dynamique créé à l’aide de l’applet **de commande New-module** .</span><span class="sxs-lookup"><span data-stu-id="ee759-136">This command shows how to use Export-ModuleMember in a dynamic module that is created by using the **New-Module** cmdlet.</span></span>

<span data-ttu-id="ee759-137">Dans cet exemple, **Export-ModuleMember** est utilisé pour exporter l’alias Hi et la fonction **sayHello** dans le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="ee759-137">In this example, **Export-ModuleMember** is used to export both the Hi alias and the **SayHello** function in the dynamic module.</span></span>

### <span data-ttu-id="ee759-138">Exemple 7 : déclarer et exporter une fonction dans une seule commande</span><span class="sxs-lookup"><span data-stu-id="ee759-138">Example 7: Declare and export a function in a single command</span></span>

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

<span data-ttu-id="ee759-139">Cet exemple comprend une fonction nommée **Export** qui déclare une fonction ou crée une variable, puis écrit une `Export-ModuleMember` commande pour la fonction ou la variable.</span><span class="sxs-lookup"><span data-stu-id="ee759-139">This example includes a function named **Export** that declares a function or creates a variable, and then writes an `Export-ModuleMember` command for the function or variable.</span></span>
<span data-ttu-id="ee759-140">Cela vous permet de déclarer et d'exporter une fonction ou une variable dans une seule commande.</span><span class="sxs-lookup"><span data-stu-id="ee759-140">This lets you declare and export a function or variable in a single command.</span></span>

<span data-ttu-id="ee759-141">Pour utiliser la fonction d' **exportation** , incluez-la dans votre module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-141">To use the **Export** function, include it in your script module.</span></span>
<span data-ttu-id="ee759-142">Pour exporter une fonction, tapez `Export` avant le mot clé **Function** .</span><span class="sxs-lookup"><span data-stu-id="ee759-142">To export a function, type `Export` before the **Function** keyword.</span></span>

<span data-ttu-id="ee759-143">Pour exporter une variable, utilisez le format suivant pour déclarer la variable et définissez sa valeur :</span><span class="sxs-lookup"><span data-stu-id="ee759-143">To export a variable, use the following format to declare the variable and set its value:</span></span>

`Export variable <variable-name> <value>`

<span data-ttu-id="ee759-144">Les commandes dans l'exemple montrent le format correct.</span><span class="sxs-lookup"><span data-stu-id="ee759-144">The commands in the example show the correct format.</span></span>
<span data-ttu-id="ee759-145">Dans cet exemple, seule la fonction **New-test** et la variable $Interval sont exportées.</span><span class="sxs-lookup"><span data-stu-id="ee759-145">In this example, only the **New-Test** function and the $Interval variable are exported.</span></span>

## <span data-ttu-id="ee759-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee759-146">PARAMETERS</span></span>

### <span data-ttu-id="ee759-147">-Alias</span><span class="sxs-lookup"><span data-stu-id="ee759-147">-Alias</span></span>

<span data-ttu-id="ee759-148">Spécifie les alias qui sont exportés à partir du fichier de module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-148">Specifies the aliases that are exported from the script module file.</span></span>
<span data-ttu-id="ee759-149">Entrez les noms des alias.</span><span class="sxs-lookup"><span data-stu-id="ee759-149">Enter the alias names.</span></span>
<span data-ttu-id="ee759-150">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ee759-150">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ee759-151">-Applet de commande</span><span class="sxs-lookup"><span data-stu-id="ee759-151">-Cmdlet</span></span>

<span data-ttu-id="ee759-152">Spécifie les applets de commande qui sont exportés à partir du fichier de module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-152">Specifies the cmdlets that are exported from the script module file.</span></span>
<span data-ttu-id="ee759-153">Entrez les noms des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="ee759-153">Enter the cmdlet names.</span></span>
<span data-ttu-id="ee759-154">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ee759-154">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ee759-155">Vous ne pouvez pas créer des applets de commande dans un fichier de module de script, mais vous pouvez importer les applets de commande à partir d'un module binaire dans un module de script et les exporter de nouveau à partir du module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-155">You cannot create cmdlets in a script module file, but you can import cmdlets from a binary module into a script module and re-export them from the script module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ee759-156">-Fonction</span><span class="sxs-lookup"><span data-stu-id="ee759-156">-Function</span></span>

<span data-ttu-id="ee759-157">Spécifie les fonctions exportées à partir du fichier de module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-157">Specifies the functions that are exported from the script module file.</span></span>
<span data-ttu-id="ee759-158">Entrez les noms des fonctions.</span><span class="sxs-lookup"><span data-stu-id="ee759-158">Enter the function names.</span></span>
<span data-ttu-id="ee759-159">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ee759-159">Wildcard characters are permitted.</span></span>
<span data-ttu-id="ee759-160">Vous pouvez également diriger les chaînes de nom de fonction vers **Export-ModuleMember** .</span><span class="sxs-lookup"><span data-stu-id="ee759-160">You can also pipe function name strings to **Export-ModuleMember** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ee759-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="ee759-161">-Variable</span></span>

<span data-ttu-id="ee759-162">Spécifie les variables exportées à partir du fichier de module de script.</span><span class="sxs-lookup"><span data-stu-id="ee759-162">Specifies the variables that are exported from the script module file.</span></span>
<span data-ttu-id="ee759-163">Entrez les noms des variables, sans le signe dollar.</span><span class="sxs-lookup"><span data-stu-id="ee759-163">Enter the variable names, without a dollar sign.</span></span>
<span data-ttu-id="ee759-164">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ee759-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ee759-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee759-165">CommonParameters</span></span>

<span data-ttu-id="ee759-166">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee759-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee759-167">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ee759-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee759-168">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ee759-168">INPUTS</span></span>

### <span data-ttu-id="ee759-169">System.String</span><span class="sxs-lookup"><span data-stu-id="ee759-169">System.String</span></span>

<span data-ttu-id="ee759-170">Vous pouvez diriger les chaînes de nom de fonction vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ee759-170">You can pipe function name strings to this cmdlet.</span></span>

## <span data-ttu-id="ee759-171">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ee759-171">OUTPUTS</span></span>

### <span data-ttu-id="ee759-172">Aucun</span><span class="sxs-lookup"><span data-stu-id="ee759-172">None</span></span>

<span data-ttu-id="ee759-173">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ee759-173">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ee759-174">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ee759-174">NOTES</span></span>

* <span data-ttu-id="ee759-175">Pour exclure un membre de la liste des membres exportés, ajoutez une commande **Export-ModuleMember** qui répertorie tous les autres membres mais qui omet le membre que vous souhaitez exclure.</span><span class="sxs-lookup"><span data-stu-id="ee759-175">To exclude a member from the list of exported members, add an **Export-ModuleMember** command that lists all other members but omits the member that you want to exclude.</span></span>

## <span data-ttu-id="ee759-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ee759-176">RELATED LINKS</span></span>

[<span data-ttu-id="ee759-177">Get-Module</span><span class="sxs-lookup"><span data-stu-id="ee759-177">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="ee759-178">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="ee759-178">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="ee759-179">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="ee759-179">Remove-Module</span></span>](Remove-Module.md)
