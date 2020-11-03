---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: dde8e497159e3e9a7bf63010bc12566d68d8de0f
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208502"
---
# <span data-ttu-id="33c2e-103">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="33c2e-103">Write-Warning</span></span>

## <span data-ttu-id="33c2e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="33c2e-104">SYNOPSIS</span></span>
<span data-ttu-id="33c2e-105">Écrit un message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="33c2e-105">Writes a warning message.</span></span>

## <span data-ttu-id="33c2e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33c2e-106">SYNTAX</span></span>

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="33c2e-107">Description</span><span class="sxs-lookup"><span data-stu-id="33c2e-107">DESCRIPTION</span></span>

<span data-ttu-id="33c2e-108">L' `Write-Warning` applet de commande écrit un message d’avertissement sur l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33c2e-108">The `Write-Warning` cmdlet writes a warning message to the PowerShell host.</span></span> <span data-ttu-id="33c2e-109">La réponse à l’avertissement dépend de la valeur de la variable de l’utilisateur `$WarningPreference` et de l’utilisation du paramètre commun **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="33c2e-109">The response to the warning depends on the value of the user's `$WarningPreference` variable and the use of the **WarningAction** common parameter.</span></span>

## <span data-ttu-id="33c2e-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="33c2e-110">EXAMPLES</span></span>

### <span data-ttu-id="33c2e-111">Exemple 1 : écrire un message d’avertissement</span><span class="sxs-lookup"><span data-stu-id="33c2e-111">Example 1: Write a warning message</span></span>

<span data-ttu-id="33c2e-112">Cette commande affiche le message « AVERTISSEMENT : il s’agit uniquement d’un avertissement de test ».</span><span class="sxs-lookup"><span data-stu-id="33c2e-112">This command displays the message "WARNING: This is only a test warning."</span></span>

```powershell
Write-Warning "This is only a test warning."
```

### <span data-ttu-id="33c2e-113">Exemple 2 : passer une chaîne à Write-Warning</span><span class="sxs-lookup"><span data-stu-id="33c2e-113">Example 2: Pass a string to Write-Warning</span></span>

<span data-ttu-id="33c2e-114">Cette commande montre que vous pouvez utiliser un opérateur de pipeline ( `|` ) pour envoyer une chaîne à `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="33c2e-114">This command shows that you can use a pipeline operator (`|`) to send a string to `Write-Warning`.</span></span>
<span data-ttu-id="33c2e-115">Vous pouvez enregistrer la chaîne dans une variable, comme indiqué dans cette commande, ou diriger la chaîne directement vers `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="33c2e-115">You can save the string in a variable, as shown in this command, or pipe the string directly to `Write-Warning`.</span></span>

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### <span data-ttu-id="33c2e-116">Exemple 3 : définir la variable $WarningPreference et écrire un avertissement</span><span class="sxs-lookup"><span data-stu-id="33c2e-116">Example 3: Set the $WarningPreference variable and write a warning</span></span>

<span data-ttu-id="33c2e-117">Cet exemple montre l’effet de la valeur de la `$WarningPreference` variable sur une `Write-Warning` commande.</span><span class="sxs-lookup"><span data-stu-id="33c2e-117">This example shows the effect of the value of the `$WarningPreference` variable on a `Write-Warning` command.</span></span>

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

<span data-ttu-id="33c2e-118">La première commande affiche la valeur par défaut de la `$WarningPreference` variable, qui est `Continue` .</span><span class="sxs-lookup"><span data-stu-id="33c2e-118">The first command displays the default value of the `$WarningPreference` variable, which is `Continue`.</span></span> <span data-ttu-id="33c2e-119">Par conséquent, lorsque vous écrivez un avertissement, le message d'avertissement s'affiche et l'exécution se poursuit.</span><span class="sxs-lookup"><span data-stu-id="33c2e-119">As a result, when you write a warning, the warning message is displayed and execution continues.</span></span>

<span data-ttu-id="33c2e-120">Lorsque vous modifiez la valeur de la `$WarningPreference` variable, l’effet de la `Write-Warning` commande change de nouveau.</span><span class="sxs-lookup"><span data-stu-id="33c2e-120">When you change the value of the `$WarningPreference` variable, the effect of the `Write-Warning` command changes again.</span></span> <span data-ttu-id="33c2e-121">`SilentlyContinue`La valeur supprime l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="33c2e-121">A value of `SilentlyContinue` suppresses the warning.</span></span> <span data-ttu-id="33c2e-122">`Stop`La valeur affiche l’avertissement et arrête l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="33c2e-122">A value of `Stop` displays the warning and then stops execution of the command.</span></span>

<span data-ttu-id="33c2e-123">Pour plus d’informations sur la `$WarningPreference` variable, consultez [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="33c2e-123">For more information about the `$WarningPreference` variable, see [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="33c2e-124">Exemple 4 : définir le paramètre WarningAction et écrire un avertissement</span><span class="sxs-lookup"><span data-stu-id="33c2e-124">Example 4: Set the WarningAction parameter and write a warning</span></span>

<span data-ttu-id="33c2e-125">Cet exemple montre l’effet du paramètre commun **WarningAction** sur une `Write-Warning` commande.</span><span class="sxs-lookup"><span data-stu-id="33c2e-125">This example shows the effect of the **WarningAction** common parameter on a `Write-Warning` command.</span></span> <span data-ttu-id="33c2e-126">Vous pouvez utiliser le paramètre commun **WarningAction** avec n’importe quelle applet de commande pour déterminer comment PowerShell répond aux avertissements résultant de cette commande.</span><span class="sxs-lookup"><span data-stu-id="33c2e-126">You can use the **WarningAction** common parameter with any cmdlet to determine how PowerShell responds to warnings resulting from that command.</span></span> <span data-ttu-id="33c2e-127">Le paramètre commun **WarningAction** remplace la valeur du `$WarningPreference` seul pour cette commande particulière.</span><span class="sxs-lookup"><span data-stu-id="33c2e-127">The **WarningAction** common parameter overrides the value of the `$WarningPreference` only for that particular command.</span></span>

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="33c2e-128">Cette commande utilise l' `Write-Warning` applet de commande pour afficher un avertissement.</span><span class="sxs-lookup"><span data-stu-id="33c2e-128">This command uses the `Write-Warning` cmdlet to display a warning.</span></span> <span data-ttu-id="33c2e-129">Le paramètre commun **WarningAction** avec la valeur inquire indique au système d’inviter l’utilisateur lorsque la commande affiche un avertissement.</span><span class="sxs-lookup"><span data-stu-id="33c2e-129">The **WarningAction** common parameter with a value of Inquire directs the system to prompt the user when the command displays a warning.</span></span>

<span data-ttu-id="33c2e-130">Pour plus d’informations sur le paramètre commun **WarningAction** , consultez [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="33c2e-130">For more information about the **WarningAction** common parameter, see [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="33c2e-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="33c2e-131">PARAMETERS</span></span>

### <span data-ttu-id="33c2e-132">-Message</span><span class="sxs-lookup"><span data-stu-id="33c2e-132">-Message</span></span>
<span data-ttu-id="33c2e-133">Spécifie le message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="33c2e-133">Specifies the warning message.</span></span>

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

### <span data-ttu-id="33c2e-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33c2e-134">CommonParameters</span></span>

<span data-ttu-id="33c2e-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33c2e-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33c2e-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="33c2e-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33c2e-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="33c2e-137">INPUTS</span></span>

### <span data-ttu-id="33c2e-138">System.String</span><span class="sxs-lookup"><span data-stu-id="33c2e-138">System.String</span></span>

<span data-ttu-id="33c2e-139">Vous pouvez diriger une chaîne qui contient l’avertissement vers `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="33c2e-139">You can pipe a string that contains the warning to `Write-Warning`.</span></span>

## <span data-ttu-id="33c2e-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="33c2e-140">OUTPUTS</span></span>

### <span data-ttu-id="33c2e-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="33c2e-141">None</span></span>

<span data-ttu-id="33c2e-142">`Write-Warning` écrit uniquement dans le flux d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="33c2e-142">`Write-Warning` writes only to the warning stream.</span></span> <span data-ttu-id="33c2e-143">Aucune autre sortie n'est générée.</span><span class="sxs-lookup"><span data-stu-id="33c2e-143">It does not generate any other output.</span></span>

## <span data-ttu-id="33c2e-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="33c2e-144">NOTES</span></span>

<span data-ttu-id="33c2e-145">La valeur par défaut de la `$WarningPreference` variable est `Continue` , qui affiche l’avertissement et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="33c2e-145">The default value for the `$WarningPreference` variable is `Continue`, which displays the warning and then continues executing the command.</span></span> <span data-ttu-id="33c2e-146">Pour déterminer les valeurs valides d’une variable de préférence, par exemple `$WarningPreference` , définissez-la sur une chaîne de caractères aléatoires, telle que « ABC ».</span><span class="sxs-lookup"><span data-stu-id="33c2e-146">To determine valid values for a preference variable such as `$WarningPreference`, set it to a string of random characters, such as "abc".</span></span> <span data-ttu-id="33c2e-147">Le message d’erreur résultant répertorie les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="33c2e-147">The resulting error message lists the valid values.</span></span>

## <span data-ttu-id="33c2e-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="33c2e-148">RELATED LINKS</span></span>

[<span data-ttu-id="33c2e-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="33c2e-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="33c2e-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="33c2e-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="33c2e-151">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="33c2e-151">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="33c2e-152">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="33c2e-152">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="33c2e-153">Write-Host</span><span class="sxs-lookup"><span data-stu-id="33c2e-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="33c2e-154">Write-Information</span><span class="sxs-lookup"><span data-stu-id="33c2e-154">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="33c2e-155">Write-Output</span><span class="sxs-lookup"><span data-stu-id="33c2e-155">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="33c2e-156">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="33c2e-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="33c2e-157">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="33c2e-157">Write-Verbose</span></span>](Write-Verbose.md)
