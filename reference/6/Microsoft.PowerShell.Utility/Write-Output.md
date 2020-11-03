---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 75b046ea6b11be3e4d87ed9db3e011a1f00d6ef5
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208397"
---
# <span data-ttu-id="869c8-103">Write-Output</span><span class="sxs-lookup"><span data-stu-id="869c8-103">Write-Output</span></span>

## <span data-ttu-id="869c8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="869c8-104">SYNOPSIS</span></span>
<span data-ttu-id="869c8-105">Envoie les objets spécifiés à la commande suivante du pipeline.</span><span class="sxs-lookup"><span data-stu-id="869c8-105">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="869c8-106">Si la commande est la dernière commande du pipeline, les objets sont affichés sur la console.</span><span class="sxs-lookup"><span data-stu-id="869c8-106">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="869c8-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="869c8-107">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="869c8-108">Description</span><span class="sxs-lookup"><span data-stu-id="869c8-108">DESCRIPTION</span></span>

<span data-ttu-id="869c8-109">L' `Write-Output` applet de commande envoie l’objet spécifié dans le pipeline vers la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="869c8-109">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="869c8-110">Si la commande est la dernière commande du pipeline, l'objet est affiché sur la console.</span><span class="sxs-lookup"><span data-stu-id="869c8-110">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="869c8-111">`Write-Output` envoie des objets vers le pipeline principal, également appelé « flux de sortie » ou « pipeline de réussite ».</span><span class="sxs-lookup"><span data-stu-id="869c8-111">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="869c8-112">Pour envoyer des objets d'erreur dans le pipeline d'erreur, utilisez Write-Error.</span><span class="sxs-lookup"><span data-stu-id="869c8-112">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="869c8-113">Cette applet de commande est généralement utilisée dans les scripts pour afficher les chaînes et autres objets sur la console.</span><span class="sxs-lookup"><span data-stu-id="869c8-113">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="869c8-114">L’un des alias intégrés pour `Write-Output` est `echo` et similaire aux autres interpréteurs de fonctionnalités qui utilisent `echo` , le comportement par défaut consiste à afficher la sortie à la fin d’un pipeline.</span><span class="sxs-lookup"><span data-stu-id="869c8-114">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="869c8-115">Dans PowerShell, il n’est généralement pas nécessaire d’utiliser l’applet de commande dans les instances où la sortie est affichée par défaut.</span><span class="sxs-lookup"><span data-stu-id="869c8-115">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="869c8-116">Par exemple, `Get-Process | Write-Output` équivaut à `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="869c8-116">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="869c8-117">Ou, `echo "Home directory: $HOME"` peut être écrit `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="869c8-117">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="869c8-118">Par défaut, `Write-Output` énumère les collections fournies à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="869c8-118">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="869c8-119">Toutefois, `Write-Output` peut également être utilisé pour passer des collections dans le pipeline en tant qu’objet unique avec le paramètre **noenumerate** .</span><span class="sxs-lookup"><span data-stu-id="869c8-119">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="869c8-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="869c8-120">EXAMPLES</span></span>

### <span data-ttu-id="869c8-121">Exemple 1 : récupérer des objets et les écrire dans la console</span><span class="sxs-lookup"><span data-stu-id="869c8-121">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="869c8-122">La première commande récupère les processus en cours d’exécution sur l’ordinateur et les stocke dans la `$P` variable.</span><span class="sxs-lookup"><span data-stu-id="869c8-122">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="869c8-123">La deuxième et la troisième commande affichent les objets processus dans `$P` sur la console.</span><span class="sxs-lookup"><span data-stu-id="869c8-123">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="869c8-124">Exemple 2 : passer la sortie à une autre applet de commande</span><span class="sxs-lookup"><span data-stu-id="869c8-124">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="869c8-125">Cette commande dirige la chaîne « test output » vers l' `Get-Member` applet de commande, qui affiche les membres de la classe **System. String** , ce qui démontre que la chaîne a été passée le long du pipeline.</span><span class="sxs-lookup"><span data-stu-id="869c8-125">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="869c8-126">Exemple 3 : supprimer l’énumération dans la sortie</span><span class="sxs-lookup"><span data-stu-id="869c8-126">Example 3: Suppress enumeration in output</span></span>

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

<span data-ttu-id="869c8-127">Cette commande ajoute le paramètre **noenumerate** pour traiter une collection ou un tableau en tant qu’objet unique via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="869c8-127">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="869c8-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="869c8-128">PARAMETERS</span></span>

### <span data-ttu-id="869c8-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="869c8-129">-InputObject</span></span>

<span data-ttu-id="869c8-130">Spécifie les objets à envoyer dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="869c8-130">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="869c8-131">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="869c8-131">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="869c8-132">-Noenumerate</span><span class="sxs-lookup"><span data-stu-id="869c8-132">-NoEnumerate</span></span>

<span data-ttu-id="869c8-133">Par défaut, l' `Write-Output` applet de commande énumère toujours sa sortie.</span><span class="sxs-lookup"><span data-stu-id="869c8-133">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="869c8-134">Le paramètre **noenumerate** supprime le comportement par défaut et empêche l' `Write-Output` énumération de la sortie.</span><span class="sxs-lookup"><span data-stu-id="869c8-134">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="869c8-135">Le paramètre **Noenumerate** n’a aucun effet si la commande est placée entre parenthèses, car les parenthèses forcent l’énumération.</span><span class="sxs-lookup"><span data-stu-id="869c8-135">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="869c8-136">Par exemple, `(Write-Output 1,2,3)` énumère toujours le tableau.</span><span class="sxs-lookup"><span data-stu-id="869c8-136">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!NOTE]
> <span data-ttu-id="869c8-137">Ce commutateur fonctionne correctement avec PowerShell Core 6,2 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="869c8-137">This switch only works correctly with PowerShell Core 6.2 and newer.</span></span> <span data-ttu-id="869c8-138">Dans les versions antérieures de PowerShell Core, la collection est toujours énumérée, même avec l’utilisation de ce commutateur.</span><span class="sxs-lookup"><span data-stu-id="869c8-138">On older versions of PowerShell Core, the collection is still enumerated even with use of this switch.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="869c8-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="869c8-139">CommonParameters</span></span>

<span data-ttu-id="869c8-140">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="869c8-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="869c8-141">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="869c8-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="869c8-142">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="869c8-142">INPUTS</span></span>

### <span data-ttu-id="869c8-143">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="869c8-143">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="869c8-144">Vous pouvez diriger les objets vers `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="869c8-144">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="869c8-145">SORTIES</span><span class="sxs-lookup"><span data-stu-id="869c8-145">OUTPUTS</span></span>

### <span data-ttu-id="869c8-146">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="869c8-146">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="869c8-147">`Write-Output` retourne les objets qui sont envoyés en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="869c8-147">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="869c8-148">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="869c8-148">NOTES</span></span>

## <span data-ttu-id="869c8-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="869c8-149">RELATED LINKS</span></span>

[<span data-ttu-id="869c8-150">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="869c8-150">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="869c8-151">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="869c8-151">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="869c8-152">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="869c8-152">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="869c8-153">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="869c8-153">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="869c8-154">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="869c8-154">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="869c8-155">Write-Host</span><span class="sxs-lookup"><span data-stu-id="869c8-155">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="869c8-156">Write-Information</span><span class="sxs-lookup"><span data-stu-id="869c8-156">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="869c8-157">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="869c8-157">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="869c8-158">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="869c8-158">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="869c8-159">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="869c8-159">Write-Warning</span></span>](Write-Warning.md)
