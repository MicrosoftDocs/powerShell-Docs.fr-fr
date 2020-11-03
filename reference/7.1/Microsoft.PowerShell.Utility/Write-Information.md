---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: 2c6d9a66a7253af4621053a9006730dce856353c
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208469"
---
# <span data-ttu-id="352ff-103">Write-Information</span><span class="sxs-lookup"><span data-stu-id="352ff-103">Write-Information</span></span>

## <span data-ttu-id="352ff-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="352ff-104">SYNOPSIS</span></span>

<span data-ttu-id="352ff-105">Spécifie la manière dont PowerShell gère les données de flux d’informations pour une commande.</span><span class="sxs-lookup"><span data-stu-id="352ff-105">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="352ff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="352ff-106">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="352ff-107">Description</span><span class="sxs-lookup"><span data-stu-id="352ff-107">DESCRIPTION</span></span>

<span data-ttu-id="352ff-108">L' `Write-Information` applet de commande spécifie la manière dont PowerShell gère les données de flux d’informations pour une commande.</span><span class="sxs-lookup"><span data-stu-id="352ff-108">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="352ff-109">Windows PowerShell 5,0 introduit un nouveau flux d’informations structurées.</span><span class="sxs-lookup"><span data-stu-id="352ff-109">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="352ff-110">Vous pouvez utiliser ce flux pour transmettre des données structurées entre un script et ses appelants ou l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="352ff-110">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="352ff-111">`Write-Information` vous permet d’ajouter un message d’information au flux et de spécifier la manière dont PowerShell gère les données de flux d’informations pour une commande.</span><span class="sxs-lookup"><span data-stu-id="352ff-111">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="352ff-112">Les flux d’informations fonctionnent également pour les `PowerShell.Streams` tâches, les travaux et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="352ff-112">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="352ff-113">Le flux d’informations ne suit pas la Convention standard de préfixe de ses messages avec « [nom du flux] : ».</span><span class="sxs-lookup"><span data-stu-id="352ff-113">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="352ff-114">Cela était prévu à des fins de brièveté et de préversion visuelle.</span><span class="sxs-lookup"><span data-stu-id="352ff-114">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="352ff-115">La `$InformationPreference` valeur de la variable de préférence détermine si le message que vous fournissez à `Write-Information` est affiché au point attendu dans l’opération d’un script.</span><span class="sxs-lookup"><span data-stu-id="352ff-115">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="352ff-116">Étant donné que la valeur par défaut de cette variable est `SilentlyContinue` , par défaut, les messages d’information ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="352ff-116">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="352ff-117">Si vous ne souhaitez pas modifier la valeur de `$InformationPreference` , vous pouvez remplacer sa valeur en ajoutant le `InformationAction` paramètre commun à votre commande.</span><span class="sxs-lookup"><span data-stu-id="352ff-117">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="352ff-118">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) et [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="352ff-118">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="352ff-119">À compter de Windows PowerShell 5,0, `Write-Host` est un wrapper de `Write-Information` ce qui vous permet d’utiliser `Write-Host` pour émettre une sortie vers le flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="352ff-119">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="352ff-120">Cela permet la **capture** ou la **suppression** des données écrites à l’aide de `Write-Host` tout en préservant la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="352ff-120">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="352ff-121">Pour plus d’informations [, consultez Write-Host](Write-Host.md)</span><span class="sxs-lookup"><span data-stu-id="352ff-121">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="352ff-122">`Write-Information` est également une activité de flux de travail prise en charge dans PowerShell 5. x.</span><span class="sxs-lookup"><span data-stu-id="352ff-122">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="352ff-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="352ff-123">EXAMPLES</span></span>

### <span data-ttu-id="352ff-124">Exemple 1 : écrire des informations pour obtenir des résultats</span><span class="sxs-lookup"><span data-stu-id="352ff-124">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="352ff-125">Dans cet exemple, vous affichez un message d’information « obtention de vos fonctionnalités ! » après avoir exécuté la `Get-WindowsFeature` commande pour rechercher toutes les fonctionnalités dont la valeur de nom commence par « p ».</span><span class="sxs-lookup"><span data-stu-id="352ff-125">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="352ff-126">Étant donné que la `$InformationPreference` variable est toujours définie sur sa valeur par défaut, `SilentlyContinue` , vous ajoutez le `InformationAction` paramètre pour remplacer la `$InformationPreference` valeur et afficher le message.</span><span class="sxs-lookup"><span data-stu-id="352ff-126">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="352ff-127">La `InformationAction` valeur est continuer, ce qui signifie que votre message s’affiche, mais le script ou la commande se poursuit, s’il n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="352ff-127">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

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

### <span data-ttu-id="352ff-128">Exemple 2 : écrire des informations et les baliser</span><span class="sxs-lookup"><span data-stu-id="352ff-128">Example 2: Write information and tag it</span></span>

<span data-ttu-id="352ff-129">Dans cet exemple, vous utilisez `Write-Information` pour informer les utilisateurs qu’ils doivent exécuter une autre commande une fois qu’ils ont terminé d’exécuter la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="352ff-129">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="352ff-130">L’exemple ajoute les instructions de balise au message d’information.</span><span class="sxs-lookup"><span data-stu-id="352ff-130">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="352ff-131">Après l’exécution de cette commande, si vous recherchez des messages marqués dans le flux d’informations, le message spécifié ici figure parmi les résultats.</span><span class="sxs-lookup"><span data-stu-id="352ff-131">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

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

### <span data-ttu-id="352ff-132">Exemple 3 : écrire des informations dans un fichier</span><span class="sxs-lookup"><span data-stu-id="352ff-132">Example 3: Write information to a file</span></span>

<span data-ttu-id="352ff-133">Dans cet exemple, vous redirigez le flux d’informations de la fonction vers un à `Info.txt` l’aide du code `6>` .</span><span class="sxs-lookup"><span data-stu-id="352ff-133">In this example, you redirect the information stream in the function to a `Info.txt` using the code `6>`.</span></span> <span data-ttu-id="352ff-134">Lorsque vous ouvrez le `Info.txt` fichier, le texte « ici » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="352ff-134">When you open the `Info.txt` file, you see the text, "Here you go."</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### <span data-ttu-id="352ff-135">Exemple 4 : passer un objet pour écrire des informations</span><span class="sxs-lookup"><span data-stu-id="352ff-135">Example 4: Pass object to write information</span></span>

<span data-ttu-id="352ff-136">Dans cet exemple, vous pouvez utiliser `Write-Information` pour écrire les 10 premiers processus d’utilisation du processeur à partir de la `Get-Process` sortie d’objet qui a franchi plusieurs pipelines.</span><span class="sxs-lookup"><span data-stu-id="352ff-136">In this example, you can use `Write-Information` to write the top 10 highest CPU utilization processes from the `Get-Process` object output that has passes through multiple pipelines.</span></span>

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## <span data-ttu-id="352ff-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="352ff-137">PARAMETERS</span></span>

### <span data-ttu-id="352ff-138">-MessageData</span><span class="sxs-lookup"><span data-stu-id="352ff-138">-MessageData</span></span>

<span data-ttu-id="352ff-139">Spécifie un message d’information que vous souhaitez afficher aux utilisateurs lorsqu’ils exécutent un script ou une commande.</span><span class="sxs-lookup"><span data-stu-id="352ff-139">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="352ff-140">Pour de meilleurs résultats, mettez le message d’information entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="352ff-140">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="352ff-141">-Tags</span><span class="sxs-lookup"><span data-stu-id="352ff-141">-Tags</span></span>

<span data-ttu-id="352ff-142">Spécifie une chaîne simple que vous pouvez utiliser pour trier et filtrer les messages que vous avez ajoutés au flux d’informations avec `Write-Information` .</span><span class="sxs-lookup"><span data-stu-id="352ff-142">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="352ff-143">Ce paramètre fonctionne de la même façon que le paramètre **Tags** dans `New-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="352ff-143">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

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

### <span data-ttu-id="352ff-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="352ff-144">CommonParameters</span></span>

<span data-ttu-id="352ff-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="352ff-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="352ff-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="352ff-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="352ff-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="352ff-147">INPUTS</span></span>

### <span data-ttu-id="352ff-148">System.Object</span><span class="sxs-lookup"><span data-stu-id="352ff-148">System.Object</span></span>

<span data-ttu-id="352ff-149">`Write-Information` accepte les objets redirigés à passer au flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="352ff-149">`Write-Information` accepts piped objects to pass to the information stream.</span></span>

## <span data-ttu-id="352ff-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="352ff-150">OUTPUTS</span></span>

### <span data-ttu-id="352ff-151">System. Management. Automation. InformationRecord</span><span class="sxs-lookup"><span data-stu-id="352ff-151">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="352ff-152">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="352ff-152">NOTES</span></span>

## <span data-ttu-id="352ff-153">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="352ff-153">RELATED LINKS</span></span>

[<span data-ttu-id="352ff-154">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="352ff-154">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="352ff-155">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="352ff-155">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="352ff-156">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="352ff-156">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="352ff-157">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="352ff-157">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="352ff-158">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="352ff-158">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="352ff-159">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="352ff-159">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="352ff-160">Write-Host</span><span class="sxs-lookup"><span data-stu-id="352ff-160">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="352ff-161">Write-Information</span><span class="sxs-lookup"><span data-stu-id="352ff-161">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="352ff-162">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="352ff-162">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="352ff-163">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="352ff-163">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="352ff-164">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="352ff-164">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="352ff-165">Write-Output</span><span class="sxs-lookup"><span data-stu-id="352ff-165">Write-Output</span></span>](Write-Output.md)
