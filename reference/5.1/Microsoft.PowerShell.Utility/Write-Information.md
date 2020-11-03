---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: e0f28393c95e2c0703c489d4691edcf883b4cb05
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208437"
---
# <span data-ttu-id="b275e-103">Write-Information</span><span class="sxs-lookup"><span data-stu-id="b275e-103">Write-Information</span></span>

## <span data-ttu-id="b275e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b275e-104">SYNOPSIS</span></span>

<span data-ttu-id="b275e-105">Spécifie la manière dont PowerShell gère les données de flux d’informations pour une commande.</span><span class="sxs-lookup"><span data-stu-id="b275e-105">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="b275e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b275e-106">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="b275e-107">Description</span><span class="sxs-lookup"><span data-stu-id="b275e-107">DESCRIPTION</span></span>

<span data-ttu-id="b275e-108">L' `Write-Information` applet de commande spécifie la manière dont PowerShell gère les données de flux d’informations pour une commande.</span><span class="sxs-lookup"><span data-stu-id="b275e-108">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="b275e-109">Windows PowerShell 5,0 introduit un nouveau flux d’informations structurées.</span><span class="sxs-lookup"><span data-stu-id="b275e-109">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="b275e-110">Vous pouvez utiliser ce flux pour transmettre des données structurées entre un script et ses appelants ou l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="b275e-110">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="b275e-111">`Write-Information` vous permet d’ajouter un message d’information au flux et de spécifier la manière dont PowerShell gère les données de flux d’informations pour une commande.</span><span class="sxs-lookup"><span data-stu-id="b275e-111">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="b275e-112">Les flux d’informations fonctionnent également pour les `PowerShell.Streams` tâches, les travaux et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="b275e-112">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="b275e-113">Le flux d’informations ne suit pas la Convention standard de préfixe de ses messages avec « [nom du flux] : ».</span><span class="sxs-lookup"><span data-stu-id="b275e-113">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="b275e-114">Cela était prévu à des fins de brièveté et de préversion visuelle.</span><span class="sxs-lookup"><span data-stu-id="b275e-114">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="b275e-115">La `$InformationPreference` valeur de la variable de préférence détermine si le message que vous fournissez à `Write-Information` est affiché au point attendu dans l’opération d’un script.</span><span class="sxs-lookup"><span data-stu-id="b275e-115">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="b275e-116">Étant donné que la valeur par défaut de cette variable est `SilentlyContinue` , par défaut, les messages d’information ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="b275e-116">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="b275e-117">Si vous ne souhaitez pas modifier la valeur de `$InformationPreference` , vous pouvez remplacer sa valeur en ajoutant le `InformationAction` paramètre commun à votre commande.</span><span class="sxs-lookup"><span data-stu-id="b275e-117">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="b275e-118">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) et [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b275e-118">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b275e-119">À compter de Windows PowerShell 5,0, `Write-Host` est un wrapper de `Write-Information` ce qui vous permet d’utiliser `Write-Host` pour émettre une sortie vers le flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="b275e-119">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="b275e-120">Cela permet la **capture** ou la **suppression** des données écrites à l’aide de `Write-Host` tout en préservant la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="b275e-120">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="b275e-121">Pour plus d’informations [, consultez Write-Host](Write-Host.md)</span><span class="sxs-lookup"><span data-stu-id="b275e-121">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="b275e-122">`Write-Information` est également une activité de flux de travail prise en charge dans PowerShell 5. x.</span><span class="sxs-lookup"><span data-stu-id="b275e-122">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="b275e-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b275e-123">EXAMPLES</span></span>

### <span data-ttu-id="b275e-124">Exemple 1 : écrire des informations pour obtenir des résultats</span><span class="sxs-lookup"><span data-stu-id="b275e-124">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="b275e-125">Dans cet exemple, vous affichez un message d’information « obtention de vos fonctionnalités ! » après avoir exécuté la `Get-WindowsFeature` commande pour rechercher toutes les fonctionnalités dont la valeur de nom commence par « p ».</span><span class="sxs-lookup"><span data-stu-id="b275e-125">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="b275e-126">Étant donné que la `$InformationPreference` variable est toujours définie sur sa valeur par défaut, `SilentlyContinue` , vous ajoutez le `InformationAction` paramètre pour remplacer la `$InformationPreference` valeur et afficher le message.</span><span class="sxs-lookup"><span data-stu-id="b275e-126">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="b275e-127">La `InformationAction` valeur est continuer, ce qui signifie que votre message s’affiche, mais le script ou la commande se poursuit, s’il n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="b275e-127">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### <span data-ttu-id="b275e-128">Exemple 2 : écrire des informations et les baliser</span><span class="sxs-lookup"><span data-stu-id="b275e-128">Example 2: Write information and tag it</span></span>

<span data-ttu-id="b275e-129">Dans cet exemple, vous utilisez `Write-Information` pour informer les utilisateurs qu’ils doivent exécuter une autre commande une fois qu’ils ont terminé d’exécuter la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="b275e-129">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="b275e-130">L’exemple ajoute les instructions de balise au message d’information.</span><span class="sxs-lookup"><span data-stu-id="b275e-130">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="b275e-131">Après l’exécution de cette commande, si vous recherchez des messages marqués dans le flux d’informations, le message spécifié ici figure parmi les résultats.</span><span class="sxs-lookup"><span data-stu-id="b275e-131">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### <span data-ttu-id="b275e-132">Exemple 3 : écrire des informations dans un fichier</span><span class="sxs-lookup"><span data-stu-id="b275e-132">Example 3: Write information to a file</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

## <span data-ttu-id="b275e-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b275e-133">PARAMETERS</span></span>

### <span data-ttu-id="b275e-134">-MessageData</span><span class="sxs-lookup"><span data-stu-id="b275e-134">-MessageData</span></span>

<span data-ttu-id="b275e-135">Spécifie un message d’information que vous souhaitez afficher aux utilisateurs lorsqu’ils exécutent un script ou une commande.</span><span class="sxs-lookup"><span data-stu-id="b275e-135">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="b275e-136">Pour de meilleurs résultats, mettez le message d’information entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="b275e-136">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b275e-137">-Tags</span><span class="sxs-lookup"><span data-stu-id="b275e-137">-Tags</span></span>

<span data-ttu-id="b275e-138">Spécifie une chaîne simple que vous pouvez utiliser pour trier et filtrer les messages que vous avez ajoutés au flux d’informations avec `Write-Information` .</span><span class="sxs-lookup"><span data-stu-id="b275e-138">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="b275e-139">Ce paramètre fonctionne de la même façon que le paramètre **Tags** dans `New-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="b275e-139">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b275e-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b275e-140">CommonParameters</span></span>

<span data-ttu-id="b275e-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b275e-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b275e-142">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b275e-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b275e-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b275e-143">INPUTS</span></span>

### <span data-ttu-id="b275e-144">Aucun</span><span class="sxs-lookup"><span data-stu-id="b275e-144">None</span></span>

<span data-ttu-id="b275e-145">`Write-Information` n’accepte pas les entrées dirigées.</span><span class="sxs-lookup"><span data-stu-id="b275e-145">`Write-Information` does not accept piped input.</span></span>

## <span data-ttu-id="b275e-146">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b275e-146">OUTPUTS</span></span>

### <span data-ttu-id="b275e-147">System. Management. Automation. InformationRecord</span><span class="sxs-lookup"><span data-stu-id="b275e-147">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="b275e-148">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b275e-148">NOTES</span></span>

## <span data-ttu-id="b275e-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b275e-149">RELATED LINKS</span></span>

[<span data-ttu-id="b275e-150">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="b275e-150">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="b275e-151">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b275e-151">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="b275e-152">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b275e-152">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="b275e-153">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="b275e-153">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="b275e-154">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b275e-154">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="b275e-155">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="b275e-155">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="b275e-156">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b275e-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b275e-157">Write-Information</span><span class="sxs-lookup"><span data-stu-id="b275e-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="b275e-158">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="b275e-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="b275e-159">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="b275e-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="b275e-160">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="b275e-160">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="b275e-161">Write-Output</span><span class="sxs-lookup"><span data-stu-id="b275e-161">Write-Output</span></span>](Write-Output.md)
