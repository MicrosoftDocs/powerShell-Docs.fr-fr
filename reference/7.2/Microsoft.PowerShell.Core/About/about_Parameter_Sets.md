---
description: Décrit comment définir et utiliser des jeux de paramètres dans les fonctions avancées.
ms.date: 02/11/2020
title: about_Parameter_Sets
ms.openlocfilehash: 405ef1c70b49f703f17a9e76f899a9643cc065bc
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "99595910"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="f8490-103">À propos des jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="f8490-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="f8490-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="f8490-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f8490-105">Décrit comment définir et utiliser des jeux de paramètres dans les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="f8490-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="f8490-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="f8490-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="f8490-107">PowerShell utilise des jeux de paramètres pour vous permettre d’écrire une fonction unique qui peut effectuer différentes actions pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="f8490-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="f8490-108">Les jeux de paramètres vous permettent d’exposer des paramètres différents à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f8490-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="f8490-109">Et pour retourner des informations différentes en fonction des paramètres spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f8490-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="f8490-110">Spécifications du jeu de paramètres</span><span class="sxs-lookup"><span data-stu-id="f8490-110">Parameter set requirements</span></span>

<span data-ttu-id="f8490-111">Les exigences suivantes s’appliquent à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="f8490-112">Chaque jeu de paramètres doit avoir une combinaison unique de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-112">Each parameter set must have a unique combination of parameters.</span></span> <span data-ttu-id="f8490-113">Si possible, au moins l’un des paramètres uniques doit être un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f8490-113">If possible, at least one of the unique parameters should be a mandatory parameter.</span></span>

- <span data-ttu-id="f8490-114">Un jeu de paramètres qui contient plusieurs paramètres positionnels doit définir des positions uniques pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="f8490-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="f8490-115">Deux paramètres positionnels ne peuvent pas spécifier la même position.</span><span class="sxs-lookup"><span data-stu-id="f8490-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="f8490-116">Un seul paramètre d’un ensemble peut déclarer le `ValueFromPipeline` mot clé avec la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="f8490-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="f8490-117">Plusieurs paramètres peuvent définir le `ValueFromPipelineByPropertyName` mot clé avec la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="f8490-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="f8490-118">Si aucun jeu de paramètres n’est spécifié pour un paramètre, le paramètre appartient à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="f8490-119">Il existe une limite de 32 jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="f8490-120">Jeux de paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="f8490-120">Default parameter sets</span></span>

<span data-ttu-id="f8490-121">Lorsque plusieurs jeux de paramètres sont définis, le `DefaultParameterSetName` mot clé de l’attribut **CmdletBinding** spécifie le jeu de paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="f8490-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="f8490-122">PowerShell utilise le jeu de paramètres par défaut lorsqu’il ne peut pas déterminer le jeu de paramètres à utiliser en fonction des informations fournies à la commande.</span><span class="sxs-lookup"><span data-stu-id="f8490-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="f8490-123">Pour plus d’informations sur l’attribut **CmdletBinding** , consultez [about_Functions_CmdletBindingAttribute](about_functions_cmdletbindingattribute.md).</span><span class="sxs-lookup"><span data-stu-id="f8490-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="f8490-124">Déclarer des jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="f8490-124">Declaring parameter sets</span></span>

<span data-ttu-id="f8490-125">Pour créer un jeu de paramètres, vous devez spécifier le `ParameterSetName` mot clé de l’attribut de **paramètre** pour chaque paramètre dans le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="f8490-126">Pour les paramètres appartenant à plusieurs jeux de paramètres, ajoutez un attribut de **paramètre** pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="f8490-127">L’attribut **Parameter** vous permet de définir le paramètre différemment pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="f8490-128">Par exemple, vous pouvez définir un paramètre comme obligatoire dans un jeu et facultatif dans un autre.</span><span class="sxs-lookup"><span data-stu-id="f8490-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="f8490-129">Toutefois, chaque jeu de paramètres doit contenir au moins un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="f8490-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="f8490-130">Les paramètres qui n’ont pas de nom de jeu de paramètres attribué appartiennent à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="f8490-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8490-131">Example</span></span>

<span data-ttu-id="f8490-132">L’exemple de fonction suivant compte le nombre de lignes, de caractères et de mots dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f8490-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="f8490-133">À l’aide de paramètres, vous pouvez spécifier les valeurs à renvoyer et les fichiers que vous souhaitez mesurer.</span><span class="sxs-lookup"><span data-stu-id="f8490-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="f8490-134">Quatre jeux de paramètres sont définis :</span><span class="sxs-lookup"><span data-stu-id="f8490-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="f8490-135">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="f8490-135">Path</span></span>
- <span data-ttu-id="f8490-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="f8490-136">PathAll</span></span>
- <span data-ttu-id="f8490-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f8490-137">LiteralPath</span></span>
- <span data-ttu-id="f8490-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="f8490-138">LiteralPathAll</span></span>

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

<span data-ttu-id="f8490-139">Chaque jeu de paramètres doit avoir un paramètre unique ou une combinaison unique de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="f8490-140">Les `Path` `PathAll` jeux de paramètres et sont très similaires, mais le paramètre **All** est unique pour le `PathAll` jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="f8490-141">Il en va de même pour `LiteralPath` les `LiteralPathAll` jeux de paramètres et.</span><span class="sxs-lookup"><span data-stu-id="f8490-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="f8490-142">Bien que les paramètres `PathAll` et `LiteralPathAll` soient définis tous les deux avec le paramètre **All** , les paramètres **path** et **LiteralPath** les différencient.</span><span class="sxs-lookup"><span data-stu-id="f8490-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="f8490-143">Utilisez `Get-Command -Syntax` affiche la syntaxe de chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="f8490-144">Toutefois, il n’affiche pas le nom du jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="f8490-145">L’exemple suivant montre les paramètres qui peuvent être utilisés dans chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-145">The following example shows which parameters can be used in each parameter set.</span></span>

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a><span data-ttu-id="f8490-146">Jeux de paramètres en action</span><span class="sxs-lookup"><span data-stu-id="f8490-146">Parameter sets in action</span></span>

<span data-ttu-id="f8490-147">Dans cet exemple, nous utilisons le `PathAll` jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f8490-147">In this example, we are using the `PathAll` parameter set.</span></span>

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```

