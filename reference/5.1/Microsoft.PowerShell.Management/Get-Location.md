---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 647424d8148cad8830235abc7b238b79b552c4fb
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206070"
---
# <span data-ttu-id="3c57c-103">Get-Location</span><span class="sxs-lookup"><span data-stu-id="3c57c-103">Get-Location</span></span>

## <span data-ttu-id="3c57c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3c57c-104">SYNOPSIS</span></span>
<span data-ttu-id="3c57c-105">Obtient des informations sur l'emplacement de travail actif ou une pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="3c57c-105">Gets information about the current working location or a location stack.</span></span>

## <span data-ttu-id="3c57c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c57c-106">SYNTAX</span></span>

### <span data-ttu-id="3c57c-107">Emplacement (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3c57c-107">Location (Default)</span></span>

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="3c57c-108">Pile</span><span class="sxs-lookup"><span data-stu-id="3c57c-108">Stack</span></span>

```
Get-Location [-Stack] [-StackName <String[]>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="3c57c-109">Description</span><span class="sxs-lookup"><span data-stu-id="3c57c-109">DESCRIPTION</span></span>

<span data-ttu-id="3c57c-110">L' `Get-Location` applet de commande obtient un objet qui représente le répertoire actif, similaire à la commande du répertoire de travail d’impression (PWD).</span><span class="sxs-lookup"><span data-stu-id="3c57c-110">The `Get-Location` cmdlet gets an object that represents the current directory, much like the print working directory (pwd) command.</span></span>

<span data-ttu-id="3c57c-111">Quand vous passez d’un lecteur PowerShell à un autre, PowerShell conserve votre emplacement sur chaque lecteur.</span><span class="sxs-lookup"><span data-stu-id="3c57c-111">When you move between PowerShell drives, PowerShell retains your location in each drive.</span></span> <span data-ttu-id="3c57c-112">Vous pouvez utiliser cette applet de commande pour rechercher votre emplacement sur chaque lecteur.</span><span class="sxs-lookup"><span data-stu-id="3c57c-112">You can use this cmdlet to find your location in each drive.</span></span>

<span data-ttu-id="3c57c-113">Vous pouvez utiliser cette applet de commande pour obtenir le répertoire actif au moment de l’exécution et l’utiliser dans des fonctions et des scripts, par exemple dans une fonction qui affiche le répertoire actif dans l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c57c-113">You can use this cmdlet to get the current directory at run time and use it in functions and scripts, such as in a function that displays the current directory in the PowerShell prompt.</span></span>

<span data-ttu-id="3c57c-114">Vous pouvez également utiliser cette applet de commande pour afficher les emplacements dans une pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="3c57c-114">You can also use this cmdlet to display the locations in a location stack.</span></span> <span data-ttu-id="3c57c-115">Pour plus d’informations, consultez les remarques et les descriptions des paramètres **Stack** et **StackName** .</span><span class="sxs-lookup"><span data-stu-id="3c57c-115">For more information, see the Notes and the descriptions of the **Stack** and **StackName** parameters.</span></span>

## <span data-ttu-id="3c57c-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3c57c-116">EXAMPLES</span></span>

### <span data-ttu-id="3c57c-117">Exemple 1 : afficher l’emplacement actuel de votre lecteur</span><span class="sxs-lookup"><span data-stu-id="3c57c-117">Example 1: Display your current drive location</span></span>

<span data-ttu-id="3c57c-118">Cette commande affiche votre emplacement dans le lecteur PowerShell actuel.</span><span class="sxs-lookup"><span data-stu-id="3c57c-118">This command displays your location in the current PowerShell drive.</span></span>

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="3c57c-119">Par exemple, si vous êtes dans le `Windows` répertoire du `C:` lecteur, le chemin d’accès à ce répertoire est affiché.</span><span class="sxs-lookup"><span data-stu-id="3c57c-119">For instance, if you are in the `Windows` directory of the `C:` drive, it displays the path to that directory.</span></span>

### <span data-ttu-id="3c57c-120">Exemple 2 : afficher votre emplacement actuel pour des lecteurs différents</span><span class="sxs-lookup"><span data-stu-id="3c57c-120">Example 2: Display your current location for different drives</span></span>

<span data-ttu-id="3c57c-121">Cet exemple illustre l’utilisation de `Get-Location` pour afficher votre emplacement actuel dans différents lecteurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c57c-121">This example demonstrates the use of `Get-Location` to display your current location in different PowerShell drives.</span></span> <span data-ttu-id="3c57c-122">`Set-Location` est utilisé pour remplacer l’emplacement par plusieurs chemins différents sur différents PSDrives.</span><span class="sxs-lookup"><span data-stu-id="3c57c-122">`Set-Location` is used to change the location to several different paths on different PSDrives.</span></span>

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### <span data-ttu-id="3c57c-123">Exemple 3 : récupération d’emplacements à l’aide de piles</span><span class="sxs-lookup"><span data-stu-id="3c57c-123">Example 3: Get locations using stacks</span></span>

<span data-ttu-id="3c57c-124">Cet exemple montre comment utiliser les paramètres **Stack** et **StackName** de `Get-Location` pour répertorier les emplacements dans la pile d’emplacements active et les autres piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="3c57c-124">This example shows how to use the **Stack** and **StackName** parameters of `Get-Location` to list the locations in the current location stack and alternate location stacks.</span></span>

<span data-ttu-id="3c57c-125">L' `Push-Location` applet de commande est utilisée pour passer à trois emplacements différents.</span><span class="sxs-lookup"><span data-stu-id="3c57c-125">The `Push-Location` cmdlet is used to change into three different locations.</span></span> <span data-ttu-id="3c57c-126">La troisième commande Push utilise un nom de pile différent.</span><span class="sxs-lookup"><span data-stu-id="3c57c-126">The third push uses a different stack name.</span></span> <span data-ttu-id="3c57c-127">Le paramètre **Stack** de `Get-Location` affiche le contenu de la pile par défaut.</span><span class="sxs-lookup"><span data-stu-id="3c57c-127">The **Stack** parameter of `Get-Location` displays the contents of the default stack.</span></span> <span data-ttu-id="3c57c-128">Le paramètre **StackName** de `Get-Location` affiche le contenu de la pile nommée `Stack2` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-128">The **StackName** parameter of `Get-Location` displays the contents of the stack named `Stack2`.</span></span>

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### <span data-ttu-id="3c57c-129">Exemple 4 : personnaliser l’invite de commandes PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c57c-129">Example 4: Customize the PowerShell prompt</span></span>

<span data-ttu-id="3c57c-130">Cet exemple montre comment personnaliser l’invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c57c-130">This example shows how to customize the PowerShell prompt.</span></span>

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

<span data-ttu-id="3c57c-131">La fonction qui définit l’invite comprend une `Get-Location` commande, qui est exécutée quand l’invite s’affiche dans la console.</span><span class="sxs-lookup"><span data-stu-id="3c57c-131">The function that defines the prompt includes a `Get-Location` command, which is run whenever the prompt appears in the console.</span></span>

<span data-ttu-id="3c57c-132">Le format de l’invite PowerShell par défaut est défini par une fonction spéciale nommée `prompt` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-132">The format of the default PowerShell prompt is defined by a special function named `prompt`.</span></span> <span data-ttu-id="3c57c-133">Vous pouvez modifier l’invite dans votre console en créant une nouvelle fonction nommée `prompt` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-133">You can change the prompt in your console by creating a new function named `prompt`.</span></span>

<span data-ttu-id="3c57c-134">Pour afficher la fonction d’invite active, tapez la commande suivante : `Get-Content Function:\prompt`</span><span class="sxs-lookup"><span data-stu-id="3c57c-134">To see the current prompt function, type the following command: `Get-Content Function:\prompt`</span></span>

## <span data-ttu-id="3c57c-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c57c-135">PARAMETERS</span></span>

### <span data-ttu-id="3c57c-136">-PSDrive</span><span class="sxs-lookup"><span data-stu-id="3c57c-136">-PSDrive</span></span>

<span data-ttu-id="3c57c-137">Obtient l’emplacement actuel dans le lecteur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="3c57c-137">Gets the current location in the specified PowerShell drive.</span></span>

<span data-ttu-id="3c57c-138">Par exemple, si vous êtes dans le `Cert:` lecteur, vous pouvez utiliser ce paramètre pour rechercher votre emplacement actuel dans le `C:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="3c57c-138">For instance, if you are in the `Cert:` drive, you can use this parameter to find your current location in the `C:` drive.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3c57c-139">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="3c57c-139">-PSProvider</span></span>

<span data-ttu-id="3c57c-140">Obtient l’emplacement actuel sur le lecteur pris en charge par le fournisseur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="3c57c-140">Gets the current location in the drive supported by the specified PowerShell provider.</span></span>
<span data-ttu-id="3c57c-141">Si le fournisseur spécifié prend en charge plusieurs lecteurs, cette applet de commande retourne l’emplacement sur le lecteur le plus récemment utilisé.</span><span class="sxs-lookup"><span data-stu-id="3c57c-141">If the specified provider supports more than one drive, this cmdlet returns the location on the most recently accessed drive.</span></span>

<span data-ttu-id="3c57c-142">Par exemple, si vous êtes dans le `C:` lecteur, vous pouvez utiliser ce paramètre pour rechercher votre emplacement actuel dans les lecteurs du fournisseur de **registre** PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c57c-142">For example, if you are in the `C:` drive, you can use this parameter to find your current location in the drives of the PowerShell **Registry** provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3c57c-143">-Pile</span><span class="sxs-lookup"><span data-stu-id="3c57c-143">-Stack</span></span>

<span data-ttu-id="3c57c-144">Indique que cette applet de commande affiche les emplacements ajoutés à la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="3c57c-144">Indicates that this cmdlet displays the locations added to the current location stack.</span></span> <span data-ttu-id="3c57c-145">Vous pouvez ajouter des emplacements à des piles à l’aide de l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-145">You can add locations to stacks by using the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="3c57c-146">Pour afficher les emplacements dans une autre pile d’emplacements, utilisez le paramètre **StackName** .</span><span class="sxs-lookup"><span data-stu-id="3c57c-146">To display the locations in a different location stack, use the **StackName** parameter.</span></span> <span data-ttu-id="3c57c-147">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="3c57c-147">For information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c57c-148">-StackName</span><span class="sxs-lookup"><span data-stu-id="3c57c-148">-StackName</span></span>

<span data-ttu-id="3c57c-149">Spécifie, sous la forme d’un tableau de chaînes, les piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="3c57c-149">Specifies, as a string array, the named location stacks.</span></span> <span data-ttu-id="3c57c-150">Entrez un ou plusieurs noms de pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="3c57c-150">Enter one or more location stack names.</span></span>

<span data-ttu-id="3c57c-151">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** .</span><span class="sxs-lookup"><span data-stu-id="3c57c-151">To display the locations in the current location stack, use the **Stack** parameter.</span></span> <span data-ttu-id="3c57c-152">Pour faire d’une pile d’emplacements la pile d’emplacements active, utilisez l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-152">To make a location stack the current location stack, use the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="3c57c-153">Cette applet de commande ne peut pas afficher les emplacements dans la pile par défaut sans nom, sauf s’il s’agit de la pile active.</span><span class="sxs-lookup"><span data-stu-id="3c57c-153">This cmdlet cannot display the locations in the unnamed default stack unless it is the current stack.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3c57c-154">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="3c57c-154">-UseTransaction</span></span>
<span data-ttu-id="3c57c-155">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="3c57c-155">Includes the command in the active transaction.</span></span>
<span data-ttu-id="3c57c-156">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="3c57c-156">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="3c57c-157">Pour plus d’informations, consultez about_transactions.</span><span class="sxs-lookup"><span data-stu-id="3c57c-157">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c57c-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c57c-158">CommonParameters</span></span>

<span data-ttu-id="3c57c-159">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c57c-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c57c-160">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3c57c-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c57c-161">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3c57c-161">INPUTS</span></span>

### <span data-ttu-id="3c57c-162">Aucun</span><span class="sxs-lookup"><span data-stu-id="3c57c-162">None</span></span>

<span data-ttu-id="3c57c-163">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3c57c-163">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3c57c-164">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3c57c-164">OUTPUTS</span></span>

### <span data-ttu-id="3c57c-165">System. Management. Automation. PathInfo ou System. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="3c57c-165">System.Management.Automation.PathInfo or System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="3c57c-166">Si vous utilisez les paramètres **Stack** ou **StackName** , cette applet de commande retourne un objet **PathInfoStack** .</span><span class="sxs-lookup"><span data-stu-id="3c57c-166">If you use the **Stack** or **StackName** parameters, this cmdlet returns a **PathInfoStack** object.</span></span> <span data-ttu-id="3c57c-167">Sinon, elle retourne un objet **PathInfo** .</span><span class="sxs-lookup"><span data-stu-id="3c57c-167">Otherwise, it returns a **PathInfo** object.</span></span>

## <span data-ttu-id="3c57c-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3c57c-168">NOTES</span></span>

<span data-ttu-id="3c57c-169">PowerShell prend en charge plusieurs instances d’exécution par processus.</span><span class="sxs-lookup"><span data-stu-id="3c57c-169">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="3c57c-170">Chaque instance d’exécution a son propre _répertoire actif_ .</span><span class="sxs-lookup"><span data-stu-id="3c57c-170">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="3c57c-171">Ce n’est pas le même que `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-171">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="3c57c-172">Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.</span><span class="sxs-lookup"><span data-stu-id="3c57c-172">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>
<span data-ttu-id="3c57c-173">L' `Get-Location` applet de commande retourne le répertoire actif de l’instance d’exécution PowerShell actuelle.</span><span class="sxs-lookup"><span data-stu-id="3c57c-173">The `Get-Location` cmdlet returns the current directory of the current PowerShell runspace.</span></span>

<span data-ttu-id="3c57c-174">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3c57c-174">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="3c57c-175">Pour répertorier les fournisseurs dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-175">To list the providers in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="3c57c-176">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3c57c-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="3c57c-177">Les modes d’interaction entre les paramètres **PSProvider** , **PSDrive** , **Stack** et **StackName** dépendent du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3c57c-177">The ways that the **PSProvider** , **PSDrive** , **Stack** , and **StackName** parameters interact depends on the provider.</span></span> <span data-ttu-id="3c57c-178">Certaines combinaisons provoquent des erreurs, par exemple la spécification d'un lecteur et d'un fournisseur qui n'expose pas ce lecteur.</span><span class="sxs-lookup"><span data-stu-id="3c57c-178">Some combinations will result in errors, such as specifying both a drive and a provider that does not expose that drive.</span></span> <span data-ttu-id="3c57c-179">Si aucun paramètre n’est spécifié, cette applet de commande retourne l’objet **PathInfo** pour le fournisseur qui contient l’emplacement de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="3c57c-179">If no parameters are specified, this cmdlet returns the **PathInfo** object for the provider that contains the current working location.</span></span>

<span data-ttu-id="3c57c-180">Une pile est une liste de dernier sorti, premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.</span><span class="sxs-lookup"><span data-stu-id="3c57c-180">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span> <span data-ttu-id="3c57c-181">Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="3c57c-181">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="3c57c-182">PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="3c57c-182">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="3c57c-183">PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="3c57c-183">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="3c57c-184">Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="3c57c-184">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="3c57c-185">Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="3c57c-185">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="3c57c-186">Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande PowerShell comme suit.</span><span class="sxs-lookup"><span data-stu-id="3c57c-186">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows.</span></span>

- <span data-ttu-id="3c57c-187">Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-187">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="3c57c-188">Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-188">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="3c57c-189">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-189">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="3c57c-190">Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-190">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="3c57c-191">Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-191">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span>
  <span data-ttu-id="3c57c-192">Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.</span><span class="sxs-lookup"><span data-stu-id="3c57c-192">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="3c57c-193">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="3c57c-193">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="3c57c-194">La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.</span><span class="sxs-lookup"><span data-stu-id="3c57c-194">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="3c57c-195">Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser cette applet de commande pour afficher les emplacements dans la pile sans nom.</span><span class="sxs-lookup"><span data-stu-id="3c57c-195">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use this cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="3c57c-196">Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="3c57c-196">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="3c57c-197">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3c57c-197">RELATED LINKS</span></span>

[<span data-ttu-id="3c57c-198">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="3c57c-198">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="3c57c-199">Push-Location</span><span class="sxs-lookup"><span data-stu-id="3c57c-199">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="3c57c-200">Set-Location</span><span class="sxs-lookup"><span data-stu-id="3c57c-200">Set-Location</span></span>](Set-Location.md)
