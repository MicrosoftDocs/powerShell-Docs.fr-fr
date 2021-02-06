---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 18c168e894989fea8b26fe000a624f91d7345332
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603484"
---
# <span data-ttu-id="fcd98-102">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="fcd98-102">Write-Warning</span></span>

## <span data-ttu-id="fcd98-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fcd98-103">SYNOPSIS</span></span>
<span data-ttu-id="fcd98-104">Écrit un message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="fcd98-104">Writes a warning message.</span></span>

## <span data-ttu-id="fcd98-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="fcd98-105">SYNTAX</span></span>

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="fcd98-106">Description</span><span class="sxs-lookup"><span data-stu-id="fcd98-106">DESCRIPTION</span></span>

<span data-ttu-id="fcd98-107">L' `Write-Warning` applet de commande écrit un message d’avertissement sur l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcd98-107">The `Write-Warning` cmdlet writes a warning message to the PowerShell host.</span></span> <span data-ttu-id="fcd98-108">La réponse à l’avertissement dépend de la valeur de la variable de l’utilisateur `$WarningPreference` et de l’utilisation du paramètre commun **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="fcd98-108">The response to the warning depends on the value of the user's `$WarningPreference` variable and the use of the **WarningAction** common parameter.</span></span>

## <span data-ttu-id="fcd98-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fcd98-109">EXAMPLES</span></span>

### <span data-ttu-id="fcd98-110">Exemple 1 : écrire un message d’avertissement</span><span class="sxs-lookup"><span data-stu-id="fcd98-110">Example 1: Write a warning message</span></span>

<span data-ttu-id="fcd98-111">Cette commande affiche le message « AVERTISSEMENT : il s’agit uniquement d’un avertissement de test ».</span><span class="sxs-lookup"><span data-stu-id="fcd98-111">This command displays the message "WARNING: This is only a test warning."</span></span>

```powershell
Write-Warning "This is only a test warning."
```

### <span data-ttu-id="fcd98-112">Exemple 2 : passer une chaîne à Write-Warning</span><span class="sxs-lookup"><span data-stu-id="fcd98-112">Example 2: Pass a string to Write-Warning</span></span>

<span data-ttu-id="fcd98-113">Cette commande montre que vous pouvez utiliser un opérateur de pipeline ( `|` ) pour envoyer une chaîne à `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="fcd98-113">This command shows that you can use a pipeline operator (`|`) to send a string to `Write-Warning`.</span></span>
<span data-ttu-id="fcd98-114">Vous pouvez enregistrer la chaîne dans une variable, comme indiqué dans cette commande, ou diriger la chaîne directement vers `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="fcd98-114">You can save the string in a variable, as shown in this command, or pipe the string directly to `Write-Warning`.</span></span>

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### <span data-ttu-id="fcd98-115">Exemple 3 : définir la variable $WarningPreference et écrire un avertissement</span><span class="sxs-lookup"><span data-stu-id="fcd98-115">Example 3: Set the $WarningPreference variable and write a warning</span></span>

<span data-ttu-id="fcd98-116">Cet exemple montre l’effet de la valeur de la `$WarningPreference` variable sur une `Write-Warning` commande.</span><span class="sxs-lookup"><span data-stu-id="fcd98-116">This example shows the effect of the value of the `$WarningPreference` variable on a `Write-Warning` command.</span></span>

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

<span data-ttu-id="fcd98-117">La première commande affiche la valeur par défaut de la `$WarningPreference` variable, qui est `Continue` .</span><span class="sxs-lookup"><span data-stu-id="fcd98-117">The first command displays the default value of the `$WarningPreference` variable, which is `Continue`.</span></span> <span data-ttu-id="fcd98-118">Par conséquent, lorsque vous écrivez un avertissement, le message d'avertissement s'affiche et l'exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="fcd98-118">As a result, when you write a warning, the warning message is displayed and execution continues.</span></span>

<span data-ttu-id="fcd98-119">Lorsque vous modifiez la valeur de la `$WarningPreference` variable, l’effet de la `Write-Warning` commande change de nouveau.</span><span class="sxs-lookup"><span data-stu-id="fcd98-119">When you change the value of the `$WarningPreference` variable, the effect of the `Write-Warning` command changes again.</span></span> <span data-ttu-id="fcd98-120">`SilentlyContinue`La valeur supprime l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="fcd98-120">A value of `SilentlyContinue` suppresses the warning.</span></span> <span data-ttu-id="fcd98-121">`Stop`La valeur affiche l’avertissement et arrête l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="fcd98-121">A value of `Stop` displays the warning and then stops execution of the command.</span></span>

<span data-ttu-id="fcd98-122">Pour plus d’informations sur la `$WarningPreference` variable, consultez [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="fcd98-122">For more information about the `$WarningPreference` variable, see [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="fcd98-123">Exemple 4 : définir le paramètre WarningAction et écrire un avertissement</span><span class="sxs-lookup"><span data-stu-id="fcd98-123">Example 4: Set the WarningAction parameter and write a warning</span></span>

<span data-ttu-id="fcd98-124">Cet exemple montre l’effet du paramètre commun **WarningAction** sur une `Write-Warning` commande.</span><span class="sxs-lookup"><span data-stu-id="fcd98-124">This example shows the effect of the **WarningAction** common parameter on a `Write-Warning` command.</span></span> <span data-ttu-id="fcd98-125">Vous pouvez utiliser le paramètre commun **WarningAction** avec n’importe quelle applet de commande pour déterminer comment PowerShell répond aux avertissements résultant de cette commande.</span><span class="sxs-lookup"><span data-stu-id="fcd98-125">You can use the **WarningAction** common parameter with any cmdlet to determine how PowerShell responds to warnings resulting from that command.</span></span> <span data-ttu-id="fcd98-126">Le paramètre commun **WarningAction** remplace la valeur du `$WarningPreference` seul pour cette commande particulière.</span><span class="sxs-lookup"><span data-stu-id="fcd98-126">The **WarningAction** common parameter overrides the value of the `$WarningPreference` only for that particular command.</span></span>

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="fcd98-127">Cette commande utilise l' `Write-Warning` applet de commande pour afficher un avertissement.</span><span class="sxs-lookup"><span data-stu-id="fcd98-127">This command uses the `Write-Warning` cmdlet to display a warning.</span></span> <span data-ttu-id="fcd98-128">Le paramètre commun **WarningAction** avec la valeur inquire indique au système d’inviter l’utilisateur lorsque la commande affiche un avertissement.</span><span class="sxs-lookup"><span data-stu-id="fcd98-128">The **WarningAction** common parameter with a value of Inquire directs the system to prompt the user when the command displays a warning.</span></span>

<span data-ttu-id="fcd98-129">Pour plus d’informations sur le paramètre commun **WarningAction** , consultez [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="fcd98-129">For more information about the **WarningAction** common parameter, see [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fcd98-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fcd98-130">PARAMETERS</span></span>

### <span data-ttu-id="fcd98-131">-Message</span><span class="sxs-lookup"><span data-stu-id="fcd98-131">-Message</span></span>
<span data-ttu-id="fcd98-132">Spécifie le message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="fcd98-132">Specifies the warning message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fcd98-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fcd98-133">CommonParameters</span></span>

<span data-ttu-id="fcd98-134">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fcd98-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fcd98-135">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fcd98-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fcd98-136">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fcd98-136">INPUTS</span></span>

### <span data-ttu-id="fcd98-137">System.String</span><span class="sxs-lookup"><span data-stu-id="fcd98-137">System.String</span></span>

<span data-ttu-id="fcd98-138">Vous pouvez diriger une chaîne qui contient l’avertissement vers `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="fcd98-138">You can pipe a string that contains the warning to `Write-Warning`.</span></span>

## <span data-ttu-id="fcd98-139">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fcd98-139">OUTPUTS</span></span>

### <span data-ttu-id="fcd98-140">None</span><span class="sxs-lookup"><span data-stu-id="fcd98-140">None</span></span>

<span data-ttu-id="fcd98-141">`Write-Warning` écrit uniquement dans le flux d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="fcd98-141">`Write-Warning` writes only to the warning stream.</span></span> <span data-ttu-id="fcd98-142">Aucune autre sortie n'est générée.</span><span class="sxs-lookup"><span data-stu-id="fcd98-142">It does not generate any other output.</span></span>

## <span data-ttu-id="fcd98-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fcd98-143">NOTES</span></span>

<span data-ttu-id="fcd98-144">La valeur par défaut de la `$WarningPreference` variable est `Continue` , qui affiche l’avertissement et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="fcd98-144">The default value for the `$WarningPreference` variable is `Continue`, which displays the warning and then continues executing the command.</span></span> <span data-ttu-id="fcd98-145">Pour déterminer les valeurs valides d’une variable de préférence, par exemple `$WarningPreference` , définissez-la sur une chaîne de caractères aléatoires, telle que « ABC ».</span><span class="sxs-lookup"><span data-stu-id="fcd98-145">To determine valid values for a preference variable such as `$WarningPreference`, set it to a string of random characters, such as "abc".</span></span> <span data-ttu-id="fcd98-146">Le message d’erreur résultant répertorie les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="fcd98-146">The resulting error message lists the valid values.</span></span>

## <span data-ttu-id="fcd98-147">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fcd98-147">RELATED LINKS</span></span>

[<span data-ttu-id="fcd98-148">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="fcd98-148">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="fcd98-149">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="fcd98-149">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="fcd98-150">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="fcd98-150">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="fcd98-151">Write-Error</span><span class="sxs-lookup"><span data-stu-id="fcd98-151">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="fcd98-152">Write-Host</span><span class="sxs-lookup"><span data-stu-id="fcd98-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="fcd98-153">Write-Information</span><span class="sxs-lookup"><span data-stu-id="fcd98-153">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="fcd98-154">Write-Output</span><span class="sxs-lookup"><span data-stu-id="fcd98-154">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="fcd98-155">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="fcd98-155">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="fcd98-156">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="fcd98-156">Write-Verbose</span></span>](Write-Verbose.md)
