---
description: Décrit la `Prompt` fonction et montre comment créer une fonction personnalisée `Prompt` .
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3887df636c3ad486a4dbe72fffdc8acd92d2b3e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598964"
---
# <a name="about-prompts"></a><span data-ttu-id="adaa0-103">À propos des invites</span><span class="sxs-lookup"><span data-stu-id="adaa0-103">About Prompts</span></span>

## <a name="short-description"></a><span data-ttu-id="adaa0-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="adaa0-104">Short description</span></span>
<span data-ttu-id="adaa0-105">Décrit la `Prompt` fonction et montre comment créer une fonction personnalisée `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="adaa0-105">Describes the `Prompt` function and demonstrates how to create a custom `Prompt` function.</span></span>

## <a name="long-description"></a><span data-ttu-id="adaa0-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="adaa0-106">Long description</span></span>

<span data-ttu-id="adaa0-107">L’invite de commandes PowerShell indique que PowerShell est prêt à exécuter une commande :</span><span class="sxs-lookup"><span data-stu-id="adaa0-107">The PowerShell command prompt indicates that PowerShell is ready to run a command:</span></span>

```
PS C:\>
```

<span data-ttu-id="adaa0-108">L’invite PowerShell est déterminée par la `Prompt` fonction intégrée.</span><span class="sxs-lookup"><span data-stu-id="adaa0-108">The PowerShell prompt is determined by the built-in `Prompt` function.</span></span> <span data-ttu-id="adaa0-109">Vous pouvez personnaliser l’invite en créant votre propre `Prompt` fonction et en l’enregistrant dans votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adaa0-109">You can customize the prompt by creating your own `Prompt` function and saving it in your PowerShell profile.</span></span>

## <a name="about-the-prompt-function"></a><span data-ttu-id="adaa0-110">À propos de la fonction prompt</span><span class="sxs-lookup"><span data-stu-id="adaa0-110">About the Prompt function</span></span>

<span data-ttu-id="adaa0-111">La `Prompt` fonction détermine l’apparence de l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adaa0-111">The `Prompt` function determines the appearance of the PowerShell prompt.</span></span>
<span data-ttu-id="adaa0-112">PowerShell est fourni avec une fonction intégrée `Prompt` , mais vous pouvez la remplacer en définissant votre propre `Prompt` fonction.</span><span class="sxs-lookup"><span data-stu-id="adaa0-112">PowerShell comes with a built-in `Prompt` function, but you can override it by defining your own `Prompt` function.</span></span>

<span data-ttu-id="adaa0-113">La `Prompt` fonction a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="adaa0-113">The `Prompt` function has the following syntax:</span></span>

```powershell
function Prompt { <function-body> }
```

<span data-ttu-id="adaa0-114">La `Prompt` fonction doit retourner un objet.</span><span class="sxs-lookup"><span data-stu-id="adaa0-114">The `Prompt` function must return an object.</span></span> <span data-ttu-id="adaa0-115">Il est recommandé de retourner une chaîne ou un objet mis en forme en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="adaa0-115">As a best practice, return a string or an object that is formatted as a string.</span></span> <span data-ttu-id="adaa0-116">La longueur maximale recommandée est de 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="adaa0-116">The maximum recommended length is 80 characters.</span></span>

<span data-ttu-id="adaa0-117">Par exemple, la `Prompt` fonction suivante retourne une chaîne « Hello, World » suivie d’un chevron droit ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="adaa0-117">For example, the following `Prompt` function returns a "Hello, World" string followed by a  right angle bracket (`>`).</span></span>

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a><span data-ttu-id="adaa0-118">Obtention de la fonction prompt</span><span class="sxs-lookup"><span data-stu-id="adaa0-118">Getting the Prompt function</span></span>

<span data-ttu-id="adaa0-119">Pour accéder à la `Prompt` fonction, utilisez l' `Get-Command` applet de commande ou utilisez l' `Get-Item` applet de commande dans le lecteur de la fonction.</span><span class="sxs-lookup"><span data-stu-id="adaa0-119">To get the `Prompt` function, use the `Get-Command` cmdlet or use the `Get-Item` cmdlet in the Function drive.</span></span>

<span data-ttu-id="adaa0-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="adaa0-120">For example:</span></span>

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

<span data-ttu-id="adaa0-121">Pour récupérer le script qui définit la valeur de l’invite, utilisez la méthode point pour récupérer la propriété **scriptblock** de la `Prompt` fonction.</span><span class="sxs-lookup"><span data-stu-id="adaa0-121">To get the script that sets the value of the prompt, use the dot method to get the **ScriptBlock** property of the `Prompt` function.</span></span>

<span data-ttu-id="adaa0-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="adaa0-122">For example:</span></span>

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

<span data-ttu-id="adaa0-123">Comme toutes les fonctions, la `Prompt` fonction est stockée dans le `Function:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="adaa0-123">Like all functions, the `Prompt` function is stored in the `Function:` drive.</span></span>
<span data-ttu-id="adaa0-124">Pour afficher le script qui crée la `Prompt` fonction active, tapez :</span><span class="sxs-lookup"><span data-stu-id="adaa0-124">To display the script that creates the current `Prompt` function, type:</span></span>

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a><span data-ttu-id="adaa0-125">Invite par défaut</span><span class="sxs-lookup"><span data-stu-id="adaa0-125">The default prompt</span></span>

<span data-ttu-id="adaa0-126">L’invite par défaut s’affiche uniquement lorsque la `Prompt` fonction génère une erreur ou ne retourne pas d’objet.</span><span class="sxs-lookup"><span data-stu-id="adaa0-126">The default prompt appears only when the `Prompt` function generates an error or does not return an object.</span></span>

<span data-ttu-id="adaa0-127">L’invite PowerShell par défaut est :</span><span class="sxs-lookup"><span data-stu-id="adaa0-127">The default PowerShell prompt is:</span></span>

```
PS>
```

<span data-ttu-id="adaa0-128">Par exemple, la commande suivante affecte `Prompt` à la fonction la valeur `$null` , qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="adaa0-128">For example, the following command sets the `Prompt` function to `$null`, which is invalid.</span></span> <span data-ttu-id="adaa0-129">Par conséquent, l’invite par défaut s’affiche.</span><span class="sxs-lookup"><span data-stu-id="adaa0-129">As a result, the default prompt appears.</span></span>

```powershell
PS C:\> function prompt {$null}
PS>
```

<span data-ttu-id="adaa0-130">Étant donné que PowerShell est fourni avec une invite intégrée, vous ne voyez généralement pas l’invite par défaut.</span><span class="sxs-lookup"><span data-stu-id="adaa0-130">Because PowerShell comes with a built-in prompt, you usually do not see the default prompt.</span></span>

### <a name="built-in-prompt"></a><span data-ttu-id="adaa0-131">Invite intégrée</span><span class="sxs-lookup"><span data-stu-id="adaa0-131">Built-in prompt</span></span>

<span data-ttu-id="adaa0-132">PowerShell intègre une `Prompt` fonction intégrée.</span><span class="sxs-lookup"><span data-stu-id="adaa0-132">PowerShell includes a built-in `Prompt` function.</span></span>

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="adaa0-133">La fonction utilise l' `Test-Path` applet de commande pour déterminer si la `$PSDebugContext` variable automatique est remplie.</span><span class="sxs-lookup"><span data-stu-id="adaa0-133">The function uses the `Test-Path` cmdlet to determine whether the `$PSDebugContext` automatic variable is populated.</span></span> <span data-ttu-id="adaa0-134">Si `$PSDebugContext` est rempli, vous êtes en mode de débogage, et `[DBG]:` est ajouté à l’invite, comme suit :</span><span class="sxs-lookup"><span data-stu-id="adaa0-134">If `$PSDebugContext` is populated, you are in debugging mode, and `[DBG]:` is added to the prompt, as follows:</span></span>

```Output
[DBG]: PS C:\ps-test>
```

<span data-ttu-id="adaa0-135">Si `$PSDebugContext` n’est pas rempli, la fonction ajoute `PS` à l’invite.</span><span class="sxs-lookup"><span data-stu-id="adaa0-135">If `$PSDebugContext` is not populated, the function adds `PS` to the prompt.</span></span>
<span data-ttu-id="adaa0-136">Et, la fonction utilise l' `Get-Location` applet de commande pour récupérer l’emplacement du répertoire du système de fichiers actuel.</span><span class="sxs-lookup"><span data-stu-id="adaa0-136">And, the function uses the `Get-Location` cmdlet to get the current file system directory location.</span></span> <span data-ttu-id="adaa0-137">Ensuite, elle ajoute un chevron droit ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="adaa0-137">Then, it adds a right angle bracket (`>`).</span></span>

<span data-ttu-id="adaa0-138">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="adaa0-138">For example:</span></span>

```Output
PS C:\ps-test>
```

<span data-ttu-id="adaa0-139">Si vous êtes dans une invite imbriquée, la fonction ajoute deux chevrons ( `>>` ) à l’invite.</span><span class="sxs-lookup"><span data-stu-id="adaa0-139">If you are in a nested prompt, the function adds two angle brackets (`>>`) to the prompt.</span></span> <span data-ttu-id="adaa0-140">(Vous êtes dans une invite imbriquée si la valeur de la `$NestedPromptLevel` variable automatique est supérieure à 1.)</span><span class="sxs-lookup"><span data-stu-id="adaa0-140">(You are in a nested prompt if the value of the `$NestedPromptLevel` automatic variable is greater than 1.)</span></span>

<span data-ttu-id="adaa0-141">Par exemple, lorsque vous effectuez un débogage dans une invite imbriquée, l’invite ressemble à l’invite suivante :</span><span class="sxs-lookup"><span data-stu-id="adaa0-141">For example, when you are debugging in a nested prompt, the prompt resembles the following prompt:</span></span>

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a><span data-ttu-id="adaa0-142">Modifications apportées à l’invite</span><span class="sxs-lookup"><span data-stu-id="adaa0-142">Changes to the prompt</span></span>

<span data-ttu-id="adaa0-143">L' `Enter-PSSession` applet de commande ajoute le nom de l’ordinateur distant à la `Prompt` fonction active.</span><span class="sxs-lookup"><span data-stu-id="adaa0-143">The `Enter-PSSession` cmdlet prepends the name of the remote computer to the current `Prompt` function.</span></span> <span data-ttu-id="adaa0-144">Lorsque vous utilisez l' `Enter-PSSession` applet de commande pour démarrer une session avec un ordinateur distant, l’invite de commandes change pour inclure le nom de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="adaa0-144">When you use the `Enter-PSSession` cmdlet to start a session with a remote computer, the command prompt changes to include the name of the remote computer.</span></span> <span data-ttu-id="adaa0-145">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="adaa0-145">For example:</span></span>

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

<span data-ttu-id="adaa0-146">D’autres applications hôtes PowerShell et autres shells peuvent avoir leurs propres invites de commandes personnalisées.</span><span class="sxs-lookup"><span data-stu-id="adaa0-146">Other PowerShell host applications and alternate shells might have their own custom command prompts.</span></span>

<span data-ttu-id="adaa0-147">Pour plus d’informations sur `$PSDebugContext` les `$NestedPromptLevel` variables automatiques et, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="adaa0-147">For more information about the `$PSDebugContext` and `$NestedPromptLevel` automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

### <a name="how-to-customize-the-prompt"></a><span data-ttu-id="adaa0-148">Comment personnaliser l’invite</span><span class="sxs-lookup"><span data-stu-id="adaa0-148">How to customize the prompt</span></span>

<span data-ttu-id="adaa0-149">Pour personnaliser l’invite, écrivez une nouvelle `Prompt` fonction.</span><span class="sxs-lookup"><span data-stu-id="adaa0-149">To customize the prompt, write a new `Prompt` function.</span></span> <span data-ttu-id="adaa0-150">La fonction n’étant pas protégée, vous pouvez la remplacer.</span><span class="sxs-lookup"><span data-stu-id="adaa0-150">The function is not protected, so you can overwrite it.</span></span>

<span data-ttu-id="adaa0-151">Pour écrire une `Prompt` fonction, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="adaa0-151">To write a `Prompt` function, type the following:</span></span>

```powershell
function prompt { }
```

<span data-ttu-id="adaa0-152">Puis, entre les accolades, entrez les commandes ou la chaîne qui crée votre invite.</span><span class="sxs-lookup"><span data-stu-id="adaa0-152">Then, between the braces, enter the commands or the string that creates your prompt.</span></span>

<span data-ttu-id="adaa0-153">Par exemple, l’invite suivante comprend le nom de votre ordinateur :</span><span class="sxs-lookup"><span data-stu-id="adaa0-153">For example, the following prompt includes your computer name:</span></span>

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

<span data-ttu-id="adaa0-154">Sur l’ordinateur Serveur01, l’invite de commandes ressemble à l’invite suivante :</span><span class="sxs-lookup"><span data-stu-id="adaa0-154">On the Server01 computer, the prompt resembles the following prompt:</span></span>

```Output
PS [Server01] >
```

<span data-ttu-id="adaa0-155">La `Prompt` fonction suivante contient la date et l’heure actuelles :</span><span class="sxs-lookup"><span data-stu-id="adaa0-155">The following `Prompt` function includes the current date and time:</span></span>

```powershell
function prompt {"$(Get-Date)> "}
```

<span data-ttu-id="adaa0-156">L’invite ressemble à l’invite suivante :</span><span class="sxs-lookup"><span data-stu-id="adaa0-156">The prompt resembles the following prompt:</span></span>

```Output
03/15/2012 17:49:47>
```

<span data-ttu-id="adaa0-157">Vous pouvez également modifier la fonction par défaut `Prompt` :</span><span class="sxs-lookup"><span data-stu-id="adaa0-157">You can also change the default `Prompt` function:</span></span>

<span data-ttu-id="adaa0-158">Par exemple, la fonction modifiée suivante `Prompt` ajoute `[ADMIN]:` à l’invite PowerShell intégrée lorsque PowerShell est ouvert à l’aide de l’option **exécuter en tant qu’administrateur** :</span><span class="sxs-lookup"><span data-stu-id="adaa0-158">For example, the following modified `Prompt` function adds `[ADMIN]:` to the built-in PowerShell prompt when PowerShell is opened by using the **Run as administrator** option:</span></span>

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="adaa0-159">Lorsque vous démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** , une invite semblable à la suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="adaa0-159">When you start PowerShell by using the **Run as administrator** option, a prompt that resembles the following prompt appears:</span></span>

```Output
[ADMIN]: PS C:\ps-test>
```

<span data-ttu-id="adaa0-160">La `Prompt` fonction suivante affiche l’ID d’historique de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="adaa0-160">The following `Prompt` function displays the history ID of the next command.</span></span> <span data-ttu-id="adaa0-161">Pour afficher l’historique des commandes, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="adaa0-161">To view the command history, use the `Get-History` cmdlet.</span></span>

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

<span data-ttu-id="adaa0-162">L’invite suivante utilise les `Write-Host` applets de commande et `Get-Random` pour créer une invite qui modifie la couleur de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="adaa0-162">The following prompt uses the `Write-Host` and `Get-Random` cmdlets to create a prompt that changes color randomly.</span></span> <span data-ttu-id="adaa0-163">Étant donné que `Write-Host` écrit dans l’application hôte actuelle, mais ne retourne pas d’objet, cette fonction comprend une `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="adaa0-163">Because `Write-Host` writes to the current host application but does not return an object, this function includes a `Return` statement.</span></span> <span data-ttu-id="adaa0-164">Sans lui, PowerShell utilise l’invite par défaut, `PS>` .</span><span class="sxs-lookup"><span data-stu-id="adaa0-164">Without it, PowerShell uses the default prompt, `PS>`.</span></span>

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a><span data-ttu-id="adaa0-165">Enregistrement de la fonction prompt</span><span class="sxs-lookup"><span data-stu-id="adaa0-165">Saving the Prompt function</span></span>

<span data-ttu-id="adaa0-166">Comme toute fonction, la `Prompt` fonction existe uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="adaa0-166">Like any function, the `Prompt` function exists only in the current session.</span></span> <span data-ttu-id="adaa0-167">Pour enregistrer la `Prompt` fonction pour des sessions ultérieures, ajoutez-la à vos profils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adaa0-167">To save the `Prompt` function for future sessions, add it to your PowerShell profiles.</span></span> <span data-ttu-id="adaa0-168">Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="adaa0-168">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="adaa0-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adaa0-169">See also</span></span>

[<span data-ttu-id="adaa0-170">Get-Location</span><span class="sxs-lookup"><span data-stu-id="adaa0-170">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)

[<span data-ttu-id="adaa0-171">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="adaa0-171">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="adaa0-172">Get-History</span><span class="sxs-lookup"><span data-stu-id="adaa0-172">Get-History</span></span>](xref:Microsoft.PowerShell.Core.Get-History)

[<span data-ttu-id="adaa0-173">Get-Random</span><span class="sxs-lookup"><span data-stu-id="adaa0-173">Get-Random</span></span>](xref:Microsoft.PowerShell.Utility.Get-Random)

[<span data-ttu-id="adaa0-174">Write-Host</span><span class="sxs-lookup"><span data-stu-id="adaa0-174">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)

[<span data-ttu-id="adaa0-175">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="adaa0-175">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="adaa0-176">about_Functions</span><span class="sxs-lookup"><span data-stu-id="adaa0-176">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="adaa0-177">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="adaa0-177">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="adaa0-178">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="adaa0-178">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="adaa0-179">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="adaa0-179">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

