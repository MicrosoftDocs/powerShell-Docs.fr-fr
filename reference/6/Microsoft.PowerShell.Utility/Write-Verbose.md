---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 07289eb2f43a0527ab523a10319777d3ef0e8ddf
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208398"
---
# <span data-ttu-id="96393-103">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="96393-103">Write-Verbose</span></span>

## <span data-ttu-id="96393-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="96393-104">SYNOPSIS</span></span>
<span data-ttu-id="96393-105">Écrit du texte dans le flux de message détaillé.</span><span class="sxs-lookup"><span data-stu-id="96393-105">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="96393-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="96393-106">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="96393-107">Description</span><span class="sxs-lookup"><span data-stu-id="96393-107">DESCRIPTION</span></span>

<span data-ttu-id="96393-108">L' `Write-Verbose` applet de commande écrit du texte dans le flux de message détaillé dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96393-108">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="96393-109">En règle générale, le flux de messages détaillé est utilisé pour fournir des informations plus détaillées sur le traitement des commandes.</span><span class="sxs-lookup"><span data-stu-id="96393-109">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="96393-110">Par défaut, le flux de message détaillé n’est pas affiché, mais vous pouvez l’afficher en modifiant la valeur de la `$VerbosePreference` variable ou en utilisant le paramètre commun **Verbose** dans n’importe quelle commande.</span><span class="sxs-lookup"><span data-stu-id="96393-110">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="96393-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="96393-111">EXAMPLES</span></span>

### <span data-ttu-id="96393-112">Exemple 1 : écrire un message d’État</span><span class="sxs-lookup"><span data-stu-id="96393-112">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="96393-113">Ces commandes utilisent l' `Write-Verbose` applet de commande pour afficher un message d’État.</span><span class="sxs-lookup"><span data-stu-id="96393-113">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="96393-114">Par défaut, le message n'est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="96393-114">By default, the message is not displayed.</span></span>

<span data-ttu-id="96393-115">La deuxième commande utilise le paramètre commun **Verbose** , qui affiche tous les messages détaillés, quelle que soit la valeur de la `$VerbosePreference` variable.</span><span class="sxs-lookup"><span data-stu-id="96393-115">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="96393-116">Exemple 2 : définir $VerbosePreference et écrire un message d’État</span><span class="sxs-lookup"><span data-stu-id="96393-116">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="96393-117">Ces commandes utilisent l' `Write-Verbose` applet de commande pour afficher un message d’État.</span><span class="sxs-lookup"><span data-stu-id="96393-117">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="96393-118">Par défaut, le message n'est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="96393-118">By default, the message is not displayed.</span></span>

<span data-ttu-id="96393-119">La première commande attribue la valeur continue à la `$VerbosePreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="96393-119">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="96393-120">La valeur par défaut, `SilentlyContinue` , supprime les messages détaillés.</span><span class="sxs-lookup"><span data-stu-id="96393-120">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="96393-121">La deuxième commande écrit un message détaillé.</span><span class="sxs-lookup"><span data-stu-id="96393-121">The second command writes a verbose message.</span></span>

## <span data-ttu-id="96393-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="96393-122">PARAMETERS</span></span>

### <span data-ttu-id="96393-123">-Message</span><span class="sxs-lookup"><span data-stu-id="96393-123">-Message</span></span>

<span data-ttu-id="96393-124">Spécifie le message à afficher.</span><span class="sxs-lookup"><span data-stu-id="96393-124">Specifies the message to display.</span></span> <span data-ttu-id="96393-125">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="96393-125">This parameter is required.</span></span> <span data-ttu-id="96393-126">Vous pouvez également diriger une chaîne de message vers `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="96393-126">You can also pipe a message string to `Write-Verbose`.</span></span>

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

### <span data-ttu-id="96393-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96393-127">CommonParameters</span></span>

<span data-ttu-id="96393-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96393-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96393-129">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="96393-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="96393-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="96393-130">INPUTS</span></span>

### <span data-ttu-id="96393-131">System.String</span><span class="sxs-lookup"><span data-stu-id="96393-131">System.String</span></span>

<span data-ttu-id="96393-132">Vous pouvez diriger une chaîne qui contient le message vers `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="96393-132">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="96393-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="96393-133">OUTPUTS</span></span>

### <span data-ttu-id="96393-134">Aucun</span><span class="sxs-lookup"><span data-stu-id="96393-134">None</span></span>

<span data-ttu-id="96393-135">`Write-Verbose` écrit uniquement dans le flux de message détaillé.</span><span class="sxs-lookup"><span data-stu-id="96393-135">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="96393-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="96393-136">NOTES</span></span>

- <span data-ttu-id="96393-137">Les messages détaillés sont retournés uniquement quand la commande utilise le paramètre commun **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="96393-137">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="96393-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="96393-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="96393-139">Dans les tâches en arrière-plan Windows PowerShell et les commandes distantes, la `$VerbosePreference` variable de la session de travail et de la session à distance détermine si le message détaillé est affiché par défaut.</span><span class="sxs-lookup"><span data-stu-id="96393-139">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="96393-140">Pour plus d’informations sur la `$VerbosePreference` variable, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="96393-140">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="96393-141">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="96393-141">RELATED LINKS</span></span>

[<span data-ttu-id="96393-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="96393-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="96393-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="96393-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="96393-144">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="96393-144">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="96393-145">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="96393-145">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="96393-146">Write-Host</span><span class="sxs-lookup"><span data-stu-id="96393-146">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="96393-147">Write-Information</span><span class="sxs-lookup"><span data-stu-id="96393-147">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="96393-148">Write-Output</span><span class="sxs-lookup"><span data-stu-id="96393-148">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="96393-149">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="96393-149">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="96393-150">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="96393-150">Write-Warning</span></span>](Write-Warning.md)
