---
title: Tout ce que vous avez toujours voulu savoir sur ShouldProcess
description: ShouldProcess est une fonctionnalité importante qui est souvent négligée. Les paramètres WhatIf et Confirm facilitent l’ajout à vos fonctions.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 4f11ad84f5c89423fe56cfe438ed3cb1587ce59e
ms.sourcegitcommit: be1df0bf757d734975a9aa021727608a396059ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616044"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="372ed-104">Tout ce que vous avez toujours voulu savoir sur ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="372ed-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="372ed-105">Les fonctions PowerShell disposent de plusieurs fonctionnalités qui améliorent de façon considérable la manière dont les utilisateurs interagissent avec ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="372ed-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="372ed-106">Une fonctionnalité importante souvent négligée est la prise en charge de `-WhatIf` et `-Confirm`, et il est facile de l’ajouter à vos fonctions.</span><span class="sxs-lookup"><span data-stu-id="372ed-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="372ed-107">Dans cet article, nous explorons en détail l’implémentation de cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="372ed-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="372ed-108">La [version d’origine][] de cet article est apparue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="372ed-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="372ed-109">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous.</span><span class="sxs-lookup"><span data-stu-id="372ed-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="372ed-110">Consultez son blog à l’adresse [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="372ed-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="372ed-111">Il s’agit d’une fonctionnalité simple que vous pouvez activer dans vos fonctions pour fournir un filet de sécurité aux utilisateurs qui en ont besoin.</span><span class="sxs-lookup"><span data-stu-id="372ed-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="372ed-112">Il n’y a rien de plus effrayant que d’exécuter une commande dont vous savez qu’elle peut être dangereuse la première fois.</span><span class="sxs-lookup"><span data-stu-id="372ed-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="372ed-113">L’option permettant de l’exécuter avec `-WhatIf` peut faire une grande différence.</span><span class="sxs-lookup"><span data-stu-id="372ed-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="372ed-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="372ed-114">CommonParameters</span></span>

<span data-ttu-id="372ed-115">Avant de nous pencher sur l’implémentation de ces [paramètres communs][], je souhaite examiner rapidement la manière dont ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="372ed-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="372ed-116">Utilisation de -WhatIf</span><span class="sxs-lookup"><span data-stu-id="372ed-116">Using -WhatIf</span></span>

<span data-ttu-id="372ed-117">Quand une commande prend en charge le paramètre `-WhatIf`, cela vous permet de voir ce que la commande aurait fait au lieu d’apporter des modifications.</span><span class="sxs-lookup"><span data-stu-id="372ed-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="372ed-118">C’est un bon moyen de tester l’impact d’une commande, en particulier avant d’exécuter une action destructrice.</span><span class="sxs-lookup"><span data-stu-id="372ed-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="372ed-119">Si la commande implémente correctement `ShouldProcess`, elle doit vous montrer toutes les modifications qu’elle aurait effectué.</span><span class="sxs-lookup"><span data-stu-id="372ed-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="372ed-120">Voici un exemple d’utilisation d’un caractère générique pour supprimer plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="372ed-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="372ed-121">Utilisation de -Confirm</span><span class="sxs-lookup"><span data-stu-id="372ed-121">Using -Confirm</span></span>

<span data-ttu-id="372ed-122">Les commandes qui prennent en charge `-WhatIf` prennent également en charge `-Confirm`.</span><span class="sxs-lookup"><span data-stu-id="372ed-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="372ed-123">Cela vous donne la possibilité de confirmer une action avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="372ed-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="372ed-124">Dans ce cas, vous avez plusieurs options qui vous permettent de continuer, d’ignorer une modification ou d’arrêter le script.</span><span class="sxs-lookup"><span data-stu-id="372ed-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="372ed-125">L’invite d’aide décrit chacune de ces options.</span><span class="sxs-lookup"><span data-stu-id="372ed-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="372ed-126">Localisation</span><span class="sxs-lookup"><span data-stu-id="372ed-126">Localization</span></span>

<span data-ttu-id="372ed-127">Cette invite est localisée dans PowerShell afin que la langue change en fonction de la langue de votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="372ed-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="372ed-128">C’est une autre chose que PowerShell gère pour vous.</span><span class="sxs-lookup"><span data-stu-id="372ed-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="372ed-129">Paramètres de commutateur</span><span class="sxs-lookup"><span data-stu-id="372ed-129">Switch parameters</span></span>

<span data-ttu-id="372ed-130">Passons rapidement en revue les façons de passer une valeur à un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="372ed-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="372ed-131">La raison principale pour laquelle je m’y intéresse est que vous souhaitez souvent passer des valeurs de paramètre à des fonctions que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="372ed-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="372ed-132">La première approche est une syntaxe de paramètre spécifique qui peut être utilisée pour tous les paramètres, mais elle est principalement utilisée pour les paramètres de commutateur.</span><span class="sxs-lookup"><span data-stu-id="372ed-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="372ed-133">Vous spécifiez un signe deux-points pour joindre une valeur au paramètre.</span><span class="sxs-lookup"><span data-stu-id="372ed-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="372ed-134">Vous pouvez faire de même avec une variable.</span><span class="sxs-lookup"><span data-stu-id="372ed-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="372ed-135">La deuxième approche consiste à utiliser une table de hachage pour représenter la valeur sous forme de « splatte ».</span><span class="sxs-lookup"><span data-stu-id="372ed-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="372ed-136">Si vous débutez avec les tables de hachage ou la projection (splatting), j’ai écrit un autre article qui couvre [tout ce que vous souhaitiez savoir sur les tables de hachage][].</span><span class="sxs-lookup"><span data-stu-id="372ed-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="372ed-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="372ed-137">SupportsShouldProcess</span></span>

<span data-ttu-id="372ed-138">La première étape pour activer la prise en charge de `-WhatIf` et `-Confirm` consiste à spécifier `SupportsShouldProcess` dans `CmdletBinding` de votre fonction.</span><span class="sxs-lookup"><span data-stu-id="372ed-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="372ed-139">En spécifiant `SupportsShouldProcess` de cette manière, nous pouvons maintenant appeler notre fonction avec `-WhatIf` (ou `-Confirm`).</span><span class="sxs-lookup"><span data-stu-id="372ed-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="372ed-140">Notez que je n’ai pas créé de paramètre appelé `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="372ed-141">La spécification de `SupportsShouldProcess` le crée automatiquement pour nous.</span><span class="sxs-lookup"><span data-stu-id="372ed-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="372ed-142">Lorsque nous spécifions le paramètre `-WhatIf` sur `Test-ShouldProcess`, certaines choses que nous appelons effectuent également un traitement `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="372ed-143">Faire confiance mais vérifier</span><span class="sxs-lookup"><span data-stu-id="372ed-143">Trust but verify</span></span>

<span data-ttu-id="372ed-144">Il existe a un danger ici de croire que tout ce que vous appelez hérite des valeurs `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="372ed-145">Pour le reste des exemples, je vais supposer que cela ne fonctionne pas et je vais être très explicite lors de l’appel à d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="372ed-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="372ed-146">Je vous recommande d’en faire de même.</span><span class="sxs-lookup"><span data-stu-id="372ed-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIfPreference
}
```

<span data-ttu-id="372ed-147">Je reviendrai sur les nuances plus tard une fois que vous aurez une meilleure compréhension de tous les éléments en jeu.</span><span class="sxs-lookup"><span data-stu-id="372ed-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="372ed-148">$PSCmdlet.ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="372ed-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="372ed-149">La méthode qui vous permet d’implémenter `SupportsShouldProcess` est `$PSCmdlet.ShouldProcess`.</span><span class="sxs-lookup"><span data-stu-id="372ed-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="372ed-150">Vous appelez `$PSCmdlet.ShouldProcess(...)` pour voir si vous devez traiter une certaine logique et que PowerShell s’occupe du reste.</span><span class="sxs-lookup"><span data-stu-id="372ed-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="372ed-151">Commençons avec un exemple :</span><span class="sxs-lookup"><span data-stu-id="372ed-151">Let's start with an example:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

<span data-ttu-id="372ed-152">L’appel à `$PSCmdlet.ShouldProcess($file.name)` vérifie le `-WhatIf` (et le paramètre `-Confirm`), puis le gère en conséquence.</span><span class="sxs-lookup"><span data-stu-id="372ed-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="372ed-153">Le `-WhatIf` oblige `ShouldProcess` à générer une description de la modification et à retourner `$false` :</span><span class="sxs-lookup"><span data-stu-id="372ed-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="372ed-154">Un appel à l’aide de `-Confirm` interrompt le script et invite l’utilisateur à continuer.</span><span class="sxs-lookup"><span data-stu-id="372ed-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="372ed-155">Il retourne `$true` si l’utilisateur a sélectionné `Y`.</span><span class="sxs-lookup"><span data-stu-id="372ed-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="372ed-156">Une fonctionnalité extraordinaire de `$PSCmdlet.ShouldProcess` est qu’elle sert aussi de sortie détaillée.</span><span class="sxs-lookup"><span data-stu-id="372ed-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="372ed-157">J’utilise souvent cela lors de l’implémentation de `ShouldProcess`.</span><span class="sxs-lookup"><span data-stu-id="372ed-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="372ed-158">Surcharges</span><span class="sxs-lookup"><span data-stu-id="372ed-158">Overloads</span></span>

<span data-ttu-id="372ed-159">Il existe plusieurs surcharges différentes pour `$PSCmdlet.ShouldProcess` avec des paramètres différents pour la personnalisation des messages.</span><span class="sxs-lookup"><span data-stu-id="372ed-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="372ed-160">Nous avons déjà vu la première dans l’exemple ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="372ed-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="372ed-161">Examinons-la de plus près.</span><span class="sxs-lookup"><span data-stu-id="372ed-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="372ed-162">Cela produit une sortie qui comprend à la fois le nom de la fonction et la cible (valeur du paramètre).</span><span class="sxs-lookup"><span data-stu-id="372ed-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="372ed-163">La spécification d’un deuxième paramètre comme l’opération utilise la valeur de l’opération au lieu du nom de la fonction dans le message.</span><span class="sxs-lookup"><span data-stu-id="372ed-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="372ed-164">L’option suivante consiste à spécifier trois paramètres pour personnaliser entièrement le message.</span><span class="sxs-lookup"><span data-stu-id="372ed-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="372ed-165">Lorsque trois paramètres sont utilisés, le premier est le message entier.</span><span class="sxs-lookup"><span data-stu-id="372ed-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="372ed-166">Les deux autres paramètres sont toujours utilisés dans la sortie du message `-Confirm`.</span><span class="sxs-lookup"><span data-stu-id="372ed-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="372ed-167">Référence de paramètre rapide</span><span class="sxs-lookup"><span data-stu-id="372ed-167">Quick parameter reference</span></span>

<span data-ttu-id="372ed-168">Au cas où vous liriez ceci uniquement pour savoir quels paramètres utiliser, voici une référence rapide indiquant comment les paramètres modifient le message dans les différents scénarios de `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="372ed-169">J’ai tendance à utiliser le scénario avec deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="372ed-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="372ed-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="372ed-170">ShouldProcessReason</span></span>

<span data-ttu-id="372ed-171">Il existe une quatrième surcharge qui est plus avancée que les autres.</span><span class="sxs-lookup"><span data-stu-id="372ed-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="372ed-172">Elle vous permet d’obtenir la raison pour laquelle `ShouldProcess` a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="372ed-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="372ed-173">Je l’ajoute ici pour des raisons d’exhaustivité, car nous pouvons simplement vérifier si `$WhatIfPreference` est `$true` à la place.</span><span class="sxs-lookup"><span data-stu-id="372ed-173">I'm only adding this here for completeness because we can just check if `$WhatIfPreference` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="372ed-174">Nous devons passer la variable `$reason` dans le quatrième paramètre en tant que variable de référence avec `[ref]`.</span><span class="sxs-lookup"><span data-stu-id="372ed-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="372ed-175">`ShouldProcess` remplit `$reason` avec la valeur `None` ou `WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="372ed-176">Je n’ai pas dit que cela était utile et je n’ai jamais eu de raison de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="372ed-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="372ed-177">Où placer l’élément ?</span><span class="sxs-lookup"><span data-stu-id="372ed-177">Where to place it</span></span>

<span data-ttu-id="372ed-178">Vous utilisez `ShouldProcess` pour rendre vos scripts plus sûrs.</span><span class="sxs-lookup"><span data-stu-id="372ed-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="372ed-179">Vous l’utilisez donc lorsque vos scripts effectuent des modifications.</span><span class="sxs-lookup"><span data-stu-id="372ed-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="372ed-180">J’aime placer l’appel à `$PSCmdlet.ShouldProcess` aussi proche que possible de la modification.</span><span class="sxs-lookup"><span data-stu-id="372ed-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="372ed-181">Si je traite une collection d’éléments, je l’appelle pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="372ed-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="372ed-182">L’appel est donc placé à l’intérieur de la boucle foreach.</span><span class="sxs-lookup"><span data-stu-id="372ed-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="372ed-183">La raison pour laquelle je place `ShouldProcess` près de la modification est que je souhaite exécuter autant de code que possible lorsque `-WhatIf` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="372ed-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="372ed-184">Je souhaite que l’installation et la validation s’exécutent si possible de façon à ce que l’utilisateur soit en mesure de voir ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="372ed-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="372ed-185">J’aime également utiliser cela dans mes tests Pester qui valident mes projets.</span><span class="sxs-lookup"><span data-stu-id="372ed-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="372ed-186">Si j’ai une logique difficile à simuler dans Pester, je peux souvent l’encapsuler dans `ShouldProcess` et l’appeler avec `-WhatIf` dans mes tests.</span><span class="sxs-lookup"><span data-stu-id="372ed-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="372ed-187">Il vaut mieux tester une partie de votre code plutôt que de ne rien tester du tout.</span><span class="sxs-lookup"><span data-stu-id="372ed-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="372ed-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="372ed-188">$WhatIfPreference</span></span>

<span data-ttu-id="372ed-189">La première variable de préférence que nous avons est `$WhatIfPreference`.</span><span class="sxs-lookup"><span data-stu-id="372ed-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="372ed-190">Elle est `$false` par défaut.</span><span class="sxs-lookup"><span data-stu-id="372ed-190">This is `$false` by default.</span></span> <span data-ttu-id="372ed-191">Si vous la définissez sur `$true`, votre fonction s’exécute comme si vous aviez spécifié `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="372ed-192">Si vous définissez cela dans votre session, toutes les commandes effectuent l’exécution de `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="372ed-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="372ed-193">Lorsque vous appelez une fonction avec `-WhatIf`, la valeur de `$WhatIfPreference` est définie sur `$true` à l’intérieur de l’étendue de votre fonction.</span><span class="sxs-lookup"><span data-stu-id="372ed-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="372ed-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="372ed-194">ConfirmImpact</span></span>

<span data-ttu-id="372ed-195">La plupart de mes exemples s’appliquent à `-WhatIf` mais tout fonctionne également avec `-Confirm` pour inviter l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="372ed-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="372ed-196">Vous pouvez définir le `ConfirmImpact` de la fonction sur la valeur High (Élevé) et cela invite l’utilisateur comme s’il était appelé avec `-Confirm`.</span><span class="sxs-lookup"><span data-stu-id="372ed-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="372ed-197">Cet appel à `Test-ShouldProcess` effectue l’action `-Confirm` en raison de l’impact `High`.</span><span class="sxs-lookup"><span data-stu-id="372ed-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="372ed-198">Le problème évident est que cela est désormais plus difficile à utiliser dans d’autres scripts sans inviter l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="372ed-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="372ed-199">Dans ce cas, nous pouvons transmettre un `$false` à `-Confirm` pour supprimer l’invite.</span><span class="sxs-lookup"><span data-stu-id="372ed-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="372ed-200">Je vais vous expliquer comment ajouter la prise en charge de `-Force` dans une section ultérieure.</span><span class="sxs-lookup"><span data-stu-id="372ed-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="372ed-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="372ed-201">$ConfirmPreference</span></span>

<span data-ttu-id="372ed-202">`$ConfirmPreference` est une variable automatique qui contrôle quand `ConfirmImpact` vous demande de confirmer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="372ed-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="372ed-203">Voici les valeurs possibles pour `$ConfirmPreference` et `ConfirmImpact`.</span><span class="sxs-lookup"><span data-stu-id="372ed-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="372ed-204">Avec ces valeurs, vous pouvez spécifier différents niveaux d’impact pour chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="372ed-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="372ed-205">Si vous avez `$ConfirmPreference` défini sur une valeur supérieure à `ConfirmImpact`, vous n’êtes pas invité à confirmer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="372ed-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="372ed-206">Par défaut, `$ConfirmPreference` est défini sur `High` et `ConfirmImpact` est `Medium`.</span><span class="sxs-lookup"><span data-stu-id="372ed-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="372ed-207">Si vous souhaitez que votre fonction invite automatiquement l’utilisateur, définissez votre `ConfirmImpact` sur `High`.</span><span class="sxs-lookup"><span data-stu-id="372ed-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="372ed-208">Sinon, affectez-lui la valeur `Medium` si elle est destructive et utilisez `Low` si la commande est toujours exécutée sans risque en production.</span><span class="sxs-lookup"><span data-stu-id="372ed-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="372ed-209">Si vous la définissez sur `none`, cela n’affiche pas d’invite même si `-Confirm` a été spécifié (mais vous bénéficiez toujours de la prise en charge de `-WhatIf`).</span><span class="sxs-lookup"><span data-stu-id="372ed-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="372ed-210">Lorsque vous appelez une fonction avec `-Confirm`, la valeur de `$ConfirmPreference` est définie sur `Low` à l’intérieur de l’étendue de votre fonction.</span><span class="sxs-lookup"><span data-stu-id="372ed-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="372ed-211">Suppression des invites de confirmation imbriquées</span><span class="sxs-lookup"><span data-stu-id="372ed-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="372ed-212">`$ConfirmPreference` peut être récupéré par les fonctions que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="372ed-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="372ed-213">Cela peut créer des scénarios où vous ajoutez une invite de confirmation et la fonction que vous appelez invite également l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="372ed-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="372ed-214">En général, je spécifie `-Confirm:$false` sur les commandes que j’appelle lorsque j’ai déjà traité l’invite.</span><span class="sxs-lookup"><span data-stu-id="372ed-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

<span data-ttu-id="372ed-215">Cela nous ramène à un avertissement antérieur : Il existe des nuances en ce qui concerne le moment où `-WhatIf` n’est pas passé à une fonction et lorsque `-Confirm` passe à une fonction.</span><span class="sxs-lookup"><span data-stu-id="372ed-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="372ed-216">Je promets d’y revenir plus tard.</span><span class="sxs-lookup"><span data-stu-id="372ed-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="372ed-217">$PSCmdlet.ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="372ed-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="372ed-218">Si vous avez besoin de plus de contrôle que `ShouldProcess` ne fournit, vous pouvez déclencher l’invite directement avec `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="372ed-219">`ShouldContinue` ignore `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference` et `-WhatIf`, car il affiche une invite à chaque fois qu’il est exécuté.</span><span class="sxs-lookup"><span data-stu-id="372ed-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="372ed-220">Au premier regard, il est facile de confondre `ShouldProcess` et `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="372ed-221">J’ai tendance à me souvenir d’utiliser `ShouldProcess`, car le paramètre est appelé `SupportsShouldProcess` dans `CmdletBinding`.</span><span class="sxs-lookup"><span data-stu-id="372ed-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="372ed-222">Vous devriez utiliser `ShouldProcess` dans presque tous les scénarios.</span><span class="sxs-lookup"><span data-stu-id="372ed-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="372ed-223">C’est pourquoi j’ai d’abord parlé de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="372ed-223">That is why I covered that method first.</span></span>

<span data-ttu-id="372ed-224">Examinons `ShouldContinue` en action.</span><span class="sxs-lookup"><span data-stu-id="372ed-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="372ed-225">Cela nous offre une invite plus simple avec moins d’options.</span><span class="sxs-lookup"><span data-stu-id="372ed-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="372ed-226">Le problème majeur avec `ShouldContinue` est qu’il faut que l’utilisateur l’exécute de manière interactive, car il affiche toujours une invite pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="372ed-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="372ed-227">Vous devez toujours créer des outils qui peuvent être utilisés par d’autres scripts.</span><span class="sxs-lookup"><span data-stu-id="372ed-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="372ed-228">Pour ce faire, vous devez implémenter `-Force`.</span><span class="sxs-lookup"><span data-stu-id="372ed-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="372ed-229">Je reviendrai sur cette idée plus tard.</span><span class="sxs-lookup"><span data-stu-id="372ed-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="372ed-230">Oui pour tout</span><span class="sxs-lookup"><span data-stu-id="372ed-230">Yes to all</span></span>

<span data-ttu-id="372ed-231">Cette opération est gérée automatiquement avec `ShouldProcess` mais nous devons effectuer un peu plus de travail pour `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="372ed-232">Il existe une deuxième surcharge de méthode où nous devons passer quelques valeurs par référence pour contrôler la logique.</span><span class="sxs-lookup"><span data-stu-id="372ed-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

<span data-ttu-id="372ed-233">J’ai ajouté une boucle `foreach` et une collection pour la montrer en action.</span><span class="sxs-lookup"><span data-stu-id="372ed-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="372ed-234">J’ai extrait l’appel `ShouldContinue` de l’instruction `if` pour la rendre plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="372ed-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="372ed-235">L’appel d’une méthode avec quatre paramètres commence à devenir un peu brouillon, mais j’ai essayé de le rendre aussi propre que possible.</span><span class="sxs-lookup"><span data-stu-id="372ed-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="372ed-236">Implémentation de -Force</span><span class="sxs-lookup"><span data-stu-id="372ed-236">Implementing -Force</span></span>

<span data-ttu-id="372ed-237">`ShouldProcess` et `ShouldContinue` doivent implémenter `-Force` de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="372ed-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="372ed-238">L’astuce pour ces implémentations est que `ShouldProcess` doit toujours être exécuté, mais `ShouldContinue` ne doit pas être exécuté si `-Force` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="372ed-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="372ed-239">ShouldProcess -Force</span><span class="sxs-lookup"><span data-stu-id="372ed-239">ShouldProcess -Force</span></span>

<span data-ttu-id="372ed-240">Si vous définissez votre `ConfirmImpact` sur `high`, la première chose que vos utilisateurs vont essayer de faire est de le supprimer avec `-Force`.</span><span class="sxs-lookup"><span data-stu-id="372ed-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="372ed-241">Enfin, c’est la première chose que je ferais.</span><span class="sxs-lookup"><span data-stu-id="372ed-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="372ed-242">Si vous vous souvenez de la section `ConfirmImpact`, ils doivent en fait l’appeler comme suit :</span><span class="sxs-lookup"><span data-stu-id="372ed-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="372ed-243">Tout le monde ne réalise pas que cela doit être fait et que `-Force` ne supprime pas `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-243">Not everyone realizes they need to do that and `-Force` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="372ed-244">Nous devons donc implémenter `-Force` pour le bien de nos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="372ed-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="372ed-245">Jetez un coup d’œil à cet exemple complet ici :</span><span class="sxs-lookup"><span data-stu-id="372ed-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="372ed-246">Nous ajoutons notre propre commutateur `-Force` en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="372ed-246">We add our own `-Force` switch as a parameter.</span></span> <span data-ttu-id="372ed-247">Le paramètre `-Confirm` est automatiquement ajouté lors de l’utilisation de `SupportsShouldProcess` dans `CmdletBinding`.</span><span class="sxs-lookup"><span data-stu-id="372ed-247">The `-Confirm` parameter is automatically added when using `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="372ed-248">Pleins feux sur la logique `-Force` ici :</span><span class="sxs-lookup"><span data-stu-id="372ed-248">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="372ed-249">Si l’utilisateur spécifie `-Force`, nous voulons supprimer l’invite de confirmation, sauf s’il spécifie également `-Confirm`.</span><span class="sxs-lookup"><span data-stu-id="372ed-249">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="372ed-250">Cela permet à un utilisateur de forcer une modification, tout en confirmant la modification.</span><span class="sxs-lookup"><span data-stu-id="372ed-250">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="372ed-251">Ensuite, nous définissons `$ConfirmPreference` dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="372ed-251">Then we set `$ConfirmPreference` in the local scope.</span></span> <span data-ttu-id="372ed-252">À présent, l’utilisation du paramètre `-Force` attribue temporairement la valeur None à `$ConfirmPreference`, ce qui désactive l’invite de confirmation.</span><span class="sxs-lookup"><span data-stu-id="372ed-252">Now, using the `-Force` parameter temporarily sets the `$ConfirmPreference` to none, disabling prompt for confirmation.</span></span>

```powershell
if ($Force -or $PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="372ed-253">Si quelqu’un spécifie à la fois `-Force` et `-WhatIf`, `-WhatIf` doit être prioritaire.</span><span class="sxs-lookup"><span data-stu-id="372ed-253">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="372ed-254">Cette approche conserve le traitement `-WhatIf`, car `ShouldProcess` est toujours exécuté.</span><span class="sxs-lookup"><span data-stu-id="372ed-254">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="372ed-255">N’ajoutez pas de vérification pour la valeur `$Force` à l’intérieur de l’instruction `if` avec `ShouldProcess`.</span><span class="sxs-lookup"><span data-stu-id="372ed-255">Do not add a check for the `$Force` value inside the `if` statement with the `ShouldProcess`.</span></span> <span data-ttu-id="372ed-256">C’est un anti-modèle pour ce scénario spécifique, même si c’est ce que je vous montrerai dans la section suivante pour `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-256">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="372ed-257">ShouldContinue -Force</span><span class="sxs-lookup"><span data-stu-id="372ed-257">ShouldContinue -Force</span></span>

<span data-ttu-id="372ed-258">Il s’agit de la méthode correcte pour implémenter `-Force` avec `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-258">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="372ed-259">En plaçant `$Force` à gauche de l’opérateur `-or`, il est évalué en premier.</span><span class="sxs-lookup"><span data-stu-id="372ed-259">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="372ed-260">Le fait de l’écrire de cette manière court-circuite l’exécution de l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="372ed-260">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="372ed-261">Si `$force` est `$true`, `ShouldContinue` n’est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="372ed-261">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="372ed-262">Nous n’avons pas à nous soucier de `-Confirm` ou `-WhatIf` dans ce scénario, car ils ne sont pas pris en charge par `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-262">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="372ed-263">C’est la raison pour laquelle cela doit être géré différemment de `ShouldProcess`.</span><span class="sxs-lookup"><span data-stu-id="372ed-263">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="372ed-264">Problèmes d’étendue</span><span class="sxs-lookup"><span data-stu-id="372ed-264">Scope issues</span></span>

<span data-ttu-id="372ed-265">L’utilisation de `-WhatIf` et `-Confirm` est censée s’appliquer à tout ce qui se trouve dans vos fonctions et tout ce qu’elles appellent.</span><span class="sxs-lookup"><span data-stu-id="372ed-265">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="372ed-266">Pour ce faire, `$WhatIfPreference` est défini sur `$true` ou `$ConfirmPreference` est défini sur `Low` dans l’étendue locale de la fonction.</span><span class="sxs-lookup"><span data-stu-id="372ed-266">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="372ed-267">Lorsque vous appelez une autre fonction, les appels à `ShouldProcess` utilisent ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="372ed-267">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="372ed-268">La plupart du temps, cela fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="372ed-268">This actually works correctly most of the time.</span></span> <span data-ttu-id="372ed-269">Chaque fois que vous appelez une cmdlet ou une fonction intégrée dans la même étendue, cela fonctionne.</span><span class="sxs-lookup"><span data-stu-id="372ed-269">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="372ed-270">Cela fonctionne également lorsque vous appelez un script ou une fonction dans un module de script à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="372ed-270">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="372ed-271">Le scénario spécifique où cela ne fonctionne pas est lorsqu’un script ou un module de script appelle une fonction dans un autre module de script.</span><span class="sxs-lookup"><span data-stu-id="372ed-271">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="372ed-272">Cela peut ne pas sembler être un problème majeur, mais la plupart des modules que vous créez ou extrayez de PSGallery sont des modules de script.</span><span class="sxs-lookup"><span data-stu-id="372ed-272">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="372ed-273">Le problème principal est que les modules de script n’héritent pas des valeurs de `$WhatIfPreference` ou `$ConfirmPreference` (et plusieurs autres) lorsqu’ils sont appelés à partir de fonctions dans d’autres modules de script.</span><span class="sxs-lookup"><span data-stu-id="372ed-273">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="372ed-274">La meilleure façon de résumer ceci en règle générale est que cela fonctionne correctement pour les modules binaires et qu’il ne faut pas penser que cela fonctionne pour les modules de script.</span><span class="sxs-lookup"><span data-stu-id="372ed-274">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="372ed-275">Si vous n’êtes pas sûr, testez-le ou supposez simplement que cela ne fonctionne pas correctement.</span><span class="sxs-lookup"><span data-stu-id="372ed-275">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="372ed-276">Personnellement, je pense que c’est très dangereux, car cela crée des scénarios dans lesquels vous ajoutez la prise en charge de `-WhatIf` à plusieurs modules qui fonctionnent correctement de manière isolée, mais qui ne fonctionnent pas correctement lorsqu’ils s’appellent l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="372ed-276">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="372ed-277">Un RFC GitHub travaille à la résolution de ce problème.</span><span class="sxs-lookup"><span data-stu-id="372ed-277">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="372ed-278">Pour plus d’informations, consultez [Propager les préférences d’exécution au-delà de l’étendue du module de script][RFC].</span><span class="sxs-lookup"><span data-stu-id="372ed-278">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="372ed-279">Conclusion</span><span class="sxs-lookup"><span data-stu-id="372ed-279">In closing</span></span>

<span data-ttu-id="372ed-280">Je dois rechercher comment utiliser `ShouldProcess` à chaque fois que j’ai besoin de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="372ed-280">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="372ed-281">Il m’a fallu beaucoup de temps pour distinguer `ShouldProcess` de `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="372ed-281">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="372ed-282">Je dois presque toujours rechercher les paramètres à utiliser.</span><span class="sxs-lookup"><span data-stu-id="372ed-282">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="372ed-283">Donc, ne vous inquiétez pas si vous vous trompez de temps à autre.</span><span class="sxs-lookup"><span data-stu-id="372ed-283">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="372ed-284">Cet article est disponible lorsque vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="372ed-284">This article will be here when you need it.</span></span> <span data-ttu-id="372ed-285">Je suis sûr d’y faire souvent référence moi-même.</span><span class="sxs-lookup"><span data-stu-id="372ed-285">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="372ed-286">Si vous avez aimé cette publication, veuillez nous faire part de vos commentaires sur Twitter en utilisant le lien ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="372ed-286">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="372ed-287">J’aime obtenir l’avis de ceux qui retirent de la valeur de mon contenu.</span><span class="sxs-lookup"><span data-stu-id="372ed-287">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[version d’origine]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[paramètres communs]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[tout ce que vous souhaitiez savoir sur les tables de hachage]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
