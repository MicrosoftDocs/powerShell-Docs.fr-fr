---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 7794fc8814364d3ee62b0dece787aa0213dc4ff3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203741"
---
# <span data-ttu-id="c06d3-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c06d3-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="c06d3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c06d3-104">SYNOPSIS</span></span>
<span data-ttu-id="c06d3-105">Lie des clés à des fonctions de gestionnaire de clés définies par l’utilisateur ou PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c06d3-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="c06d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c06d3-106">SYNTAX</span></span>

### <span data-ttu-id="c06d3-107">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="c06d3-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="c06d3-108">Fonction</span><span class="sxs-lookup"><span data-stu-id="c06d3-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="c06d3-109">Description</span><span class="sxs-lookup"><span data-stu-id="c06d3-109">DESCRIPTION</span></span>

<span data-ttu-id="c06d3-110">L' `Set-PSReadLineKeyHandler` applet de commande personnalise le résultat lorsqu’une touche ou une séquence de touches est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="c06d3-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="c06d3-111">Avec les combinaisons de touches définies par l’utilisateur, vous pouvez effectuer pratiquement tout ce qui est possible à partir d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c06d3-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="c06d3-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c06d3-112">EXAMPLES</span></span>

### <span data-ttu-id="c06d3-113">Exemple 1 : lier la touche de direction à une fonction</span><span class="sxs-lookup"><span data-stu-id="c06d3-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="c06d3-114">Cette commande lie la touche de direction haut à la fonction **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="c06d3-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="c06d3-115">Cette fonction recherche les lignes de commande dans l’historique des commandes qui commencent par le contenu actuel de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c06d3-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="c06d3-116">Exemple 2 : lier une clé à un bloc de script</span><span class="sxs-lookup"><span data-stu-id="c06d3-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="c06d3-117">Cet exemple montre comment une clé unique peut être utilisée pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="c06d3-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="c06d3-118">La commande lie la clé `Ctrl+B` à un bloc de script qui efface la ligne, insère le mot « Build », puis accepte la ligne.</span><span class="sxs-lookup"><span data-stu-id="c06d3-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="c06d3-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c06d3-119">PARAMETERS</span></span>

### <span data-ttu-id="c06d3-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="c06d3-120">-BriefDescription</span></span>

<span data-ttu-id="c06d3-121">Brève description de la combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="c06d3-121">A brief description of the key binding.</span></span> <span data-ttu-id="c06d3-122">Cette description est affichée par l' `Get-PSReadLineKeyHandler` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c06d3-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c06d3-123">-Corde</span><span class="sxs-lookup"><span data-stu-id="c06d3-123">-Chord</span></span>

<span data-ttu-id="c06d3-124">Clé ou séquence de clés à lier à une fonction ou à un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="c06d3-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="c06d3-125">Utilisez une chaîne unique pour spécifier une seule liaison.</span><span class="sxs-lookup"><span data-stu-id="c06d3-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="c06d3-126">Si la liaison est une séquence de clés, séparez les clés par une virgule, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c06d3-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

<span data-ttu-id="c06d3-127">Ce paramètre accepte un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c06d3-127">This parameter accepts an array of strings.</span></span> <span data-ttu-id="c06d3-128">Chaque chaîne est une liaison distincte, et non une séquence de clés pour une seule liaison.</span><span class="sxs-lookup"><span data-stu-id="c06d3-128">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c06d3-129">Description</span><span class="sxs-lookup"><span data-stu-id="c06d3-129">-Description</span></span>

<span data-ttu-id="c06d3-130">Spécifie une description plus détaillée de la combinaison de touches qui est visible dans la sortie de l’applet de commande `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="c06d3-130">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c06d3-131">-Fonction</span><span class="sxs-lookup"><span data-stu-id="c06d3-131">-Function</span></span>

<span data-ttu-id="c06d3-132">Spécifie le nom d’un gestionnaire de clés existant fourni par PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c06d3-132">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="c06d3-133">Ce paramètre vous permet de relier des liaisons de clés existantes ou de lier un gestionnaire qui est actuellement indépendant.</span><span class="sxs-lookup"><span data-stu-id="c06d3-133">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c06d3-134">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="c06d3-134">-ScriptBlock</span></span>

<span data-ttu-id="c06d3-135">Spécifie une valeur de bloc de script à exécuter lorsque le segment est entré.</span><span class="sxs-lookup"><span data-stu-id="c06d3-135">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="c06d3-136">PSReadLine transmet un ou deux paramètres à ce bloc de script.</span><span class="sxs-lookup"><span data-stu-id="c06d3-136">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="c06d3-137">Le premier paramètre est un objet **ConsoleKeyInfo** représentant la touche enfoncée.</span><span class="sxs-lookup"><span data-stu-id="c06d3-137">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="c06d3-138">Le deuxième argument peut être n’importe quel objet en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="c06d3-138">The second argument can be any object depending on the context.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c06d3-139">-ViMode</span><span class="sxs-lookup"><span data-stu-id="c06d3-139">-ViMode</span></span>

<span data-ttu-id="c06d3-140">Spécifiez le mode VI auquel la liaison s’applique.</span><span class="sxs-lookup"><span data-stu-id="c06d3-140">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="c06d3-141">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="c06d3-141">Valid values are:</span></span>

- <span data-ttu-id="c06d3-142">Insérer</span><span class="sxs-lookup"><span data-stu-id="c06d3-142">Insert</span></span>
- <span data-ttu-id="c06d3-143">Commande</span><span class="sxs-lookup"><span data-stu-id="c06d3-143">Command</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c06d3-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c06d3-144">CommonParameters</span></span>

<span data-ttu-id="c06d3-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c06d3-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c06d3-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c06d3-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c06d3-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c06d3-147">INPUTS</span></span>

### <span data-ttu-id="c06d3-148">Aucun</span><span class="sxs-lookup"><span data-stu-id="c06d3-148">None</span></span>

<span data-ttu-id="c06d3-149">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c06d3-149">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="c06d3-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c06d3-150">OUTPUTS</span></span>

### <span data-ttu-id="c06d3-151">Aucun</span><span class="sxs-lookup"><span data-stu-id="c06d3-151">None</span></span>

<span data-ttu-id="c06d3-152">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c06d3-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c06d3-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c06d3-153">NOTES</span></span>

## <span data-ttu-id="c06d3-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c06d3-154">RELATED LINKS</span></span>

[<span data-ttu-id="c06d3-155">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c06d3-155">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="c06d3-156">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c06d3-156">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="c06d3-157">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c06d3-157">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="c06d3-158">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c06d3-158">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
