---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: c2a9af56c395409fd08c3126d36126a171ff7ec7
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205865"
---
# <span data-ttu-id="b03e4-103">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="b03e4-103">Pop-Location</span></span>

## <span data-ttu-id="b03e4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b03e4-104">SYNOPSIS</span></span>
<span data-ttu-id="b03e4-105">Définit l'emplacement actuel sur le dernier emplacement placé sur la pile.</span><span class="sxs-lookup"><span data-stu-id="b03e4-105">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="b03e4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b03e4-106">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="b03e4-107">Description</span><span class="sxs-lookup"><span data-stu-id="b03e4-107">DESCRIPTION</span></span>

<span data-ttu-id="b03e4-108">L' `Pop-Location` applet de commande modifie l’emplacement actuel à l’emplacement le plus récemment déplacé vers la pile à l’aide de l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-108">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="b03e4-109">Vous pouvez extraire un emplacement à partir de la pile par défaut ou d’une pile que vous créez à l’aide d’une `Push-Location` commande.</span><span class="sxs-lookup"><span data-stu-id="b03e4-109">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="b03e4-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b03e4-110">EXAMPLES</span></span>

### <span data-ttu-id="b03e4-111">Exemple 1 : passer à l’emplacement le plus récent</span><span class="sxs-lookup"><span data-stu-id="b03e4-111">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="b03e4-112">Cette commande définit l'emplacement sur le dernier emplacement ajouté à la pile active.</span><span class="sxs-lookup"><span data-stu-id="b03e4-112">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="b03e4-113">Exemple 2 : passer à l’emplacement le plus récent dans une pile nommée</span><span class="sxs-lookup"><span data-stu-id="b03e4-113">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="b03e4-114">Cette commande définit l'emplacement sur le dernier emplacement ajouté à la pile d'emplacements Stack2.</span><span class="sxs-lookup"><span data-stu-id="b03e4-114">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="b03e4-115">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="b03e4-115">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="b03e4-116">Exemple 3 : passer d’un emplacement à un autre pour différents fournisseurs</span><span class="sxs-lookup"><span data-stu-id="b03e4-116">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="b03e4-117">Ces commandes utilisent les `Push-Location` applets de commande et `Pop-Location` pour se déplacer entre les emplacements pris en charge par les différents fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b03e4-117">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="b03e4-118">Les commandes utilisent l' `pushd` alias pour `Push-Location` et l' `popd` alias de `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-118">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="b03e4-119">La première commande transmet l’emplacement du système de fichiers actuel sur la pile et se déplace vers le lecteur HKLM pris en charge par le fournisseur de Registre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b03e4-119">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="b03e4-120">La deuxième commande transmet l’emplacement du Registre à la pile et se déplace vers un emplacement pris en charge par le fournisseur de certificats PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b03e4-120">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="b03e4-121">Les deux dernières commandes extraient ces emplacements de la pile.</span><span class="sxs-lookup"><span data-stu-id="b03e4-121">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="b03e4-122">La première `popd` commande retourne au lecteur du Registre, et la deuxième commande retourne au lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b03e4-122">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="b03e4-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b03e4-123">PARAMETERS</span></span>

### <span data-ttu-id="b03e4-124">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b03e4-124">-PassThru</span></span>

<span data-ttu-id="b03e4-125">Passe un objet qui représente l’emplacement au pipeline.</span><span class="sxs-lookup"><span data-stu-id="b03e4-125">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="b03e4-126">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="b03e4-126">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b03e4-127">-StackName</span><span class="sxs-lookup"><span data-stu-id="b03e4-127">-StackName</span></span>

<span data-ttu-id="b03e4-128">Spécifie la pile d'emplacements à partir de laquelle l'emplacement est extrait.</span><span class="sxs-lookup"><span data-stu-id="b03e4-128">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="b03e4-129">Entrez un nom de pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="b03e4-129">Enter a location stack name.</span></span>

<span data-ttu-id="b03e4-130">Sans ce paramètre, exécute `Pop-Location` un pop sur un emplacement de la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="b03e4-130">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="b03e4-131">Par défaut, la pile d’emplacements active est la pile d’emplacements par défaut sans nom que PowerShell crée.</span><span class="sxs-lookup"><span data-stu-id="b03e4-131">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="b03e4-132">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-132">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="b03e4-133">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="b03e4-133">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="b03e4-134">`Pop-Location` Impossible de dépiler un emplacement à partir de la pile par défaut sans nom, sauf s’il s’agit de la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="b03e4-134">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b03e4-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b03e4-135">CommonParameters</span></span>

<span data-ttu-id="b03e4-136">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b03e4-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b03e4-137">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b03e4-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b03e4-138">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b03e4-138">INPUTS</span></span>

### <span data-ttu-id="b03e4-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="b03e4-139">None</span></span>

<span data-ttu-id="b03e4-140">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b03e4-140">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b03e4-141">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b03e4-141">OUTPUTS</span></span>

### <span data-ttu-id="b03e4-142">Aucun, System. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="b03e4-142">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="b03e4-143">Cette applet de commande génère un objet **System. Management. Automation. PathInfo** qui représente l’emplacement, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="b03e4-143">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="b03e4-144">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b03e4-144">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b03e4-145">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b03e4-145">NOTES</span></span>

<span data-ttu-id="b03e4-146">PowerShell prend en charge plusieurs instances d’exécution par processus.</span><span class="sxs-lookup"><span data-stu-id="b03e4-146">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="b03e4-147">Chaque instance d’exécution a son propre _répertoire actif_ .</span><span class="sxs-lookup"><span data-stu-id="b03e4-147">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="b03e4-148">Ce n’est pas le même que `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-148">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="b03e4-149">Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.</span><span class="sxs-lookup"><span data-stu-id="b03e4-149">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="b03e4-150">Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="b03e4-150">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="b03e4-151">Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="b03e4-151">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="b03e4-152">Une pile est une liste de dernier et premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.</span><span class="sxs-lookup"><span data-stu-id="b03e4-152">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="b03e4-153">Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="b03e4-153">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="b03e4-154">PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="b03e4-154">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="b03e4-155">PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="b03e4-155">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="b03e4-156">Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="b03e4-156">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="b03e4-157">Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="b03e4-157">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="b03e4-158">Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande PowerShell comme suit :</span><span class="sxs-lookup"><span data-stu-id="b03e4-158">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="b03e4-159">Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-159">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="b03e4-160">Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-160">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="b03e4-161">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-161">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="b03e4-162">Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-162">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="b03e4-163">Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-163">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="b03e4-164">Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.</span><span class="sxs-lookup"><span data-stu-id="b03e4-164">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="b03e4-165">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-165">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="b03e4-166">La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.</span><span class="sxs-lookup"><span data-stu-id="b03e4-166">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="b03e4-167">Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom.</span><span class="sxs-lookup"><span data-stu-id="b03e4-167">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="b03e4-168">Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$Null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="b03e4-168">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="b03e4-169">Vous pouvez également faire référence à `Pop-Location` par son alias intégré, `popd` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-169">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="b03e4-170">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="b03e4-170">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="b03e4-171">`Pop-Location` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="b03e4-171">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b03e4-172">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b03e4-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="b03e4-173">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="b03e4-173">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b03e4-174">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b03e4-174">RELATED LINKS</span></span>

[<span data-ttu-id="b03e4-175">Get-Location</span><span class="sxs-lookup"><span data-stu-id="b03e4-175">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="b03e4-176">Push-Location</span><span class="sxs-lookup"><span data-stu-id="b03e4-176">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="b03e4-177">Set-Location</span><span class="sxs-lookup"><span data-stu-id="b03e4-177">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="b03e4-178">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="b03e4-178">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="b03e4-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b03e4-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
