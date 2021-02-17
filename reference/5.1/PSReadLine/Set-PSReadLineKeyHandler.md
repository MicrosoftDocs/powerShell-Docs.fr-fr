---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadline
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 220b38f51afab619a57473be27b1139b878eb7e9
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563222"
---
# <span data-ttu-id="f43fd-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="f43fd-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="f43fd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f43fd-104">SYNOPSIS</span></span>
<span data-ttu-id="f43fd-105">Lie des clés à des fonctions de gestionnaire de clés définies par l’utilisateur ou PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="f43fd-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="f43fd-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f43fd-106">SYNTAX</span></span>

### <span data-ttu-id="f43fd-107">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="f43fd-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="f43fd-108">Fonction</span><span class="sxs-lookup"><span data-stu-id="f43fd-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="f43fd-109">Description</span><span class="sxs-lookup"><span data-stu-id="f43fd-109">DESCRIPTION</span></span>

<span data-ttu-id="f43fd-110">L' `Set-PSReadLineKeyHandler` applet de commande personnalise le résultat lorsqu’une touche ou une séquence de touches est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="f43fd-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="f43fd-111">Avec les combinaisons de touches définies par l’utilisateur, vous pouvez effectuer pratiquement tout ce qui est possible à partir d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f43fd-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="f43fd-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f43fd-112">EXAMPLES</span></span>

### <span data-ttu-id="f43fd-113">Exemple 1 : lier la touche de direction à une fonction</span><span class="sxs-lookup"><span data-stu-id="f43fd-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="f43fd-114">Cette commande lie la touche de direction haut à la fonction **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="f43fd-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="f43fd-115">Cette fonction recherche les lignes de commande dans l’historique des commandes qui commencent par le contenu actuel de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f43fd-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="f43fd-116">Exemple 2 : lier une clé à un bloc de script</span><span class="sxs-lookup"><span data-stu-id="f43fd-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="f43fd-117">Cet exemple montre comment une clé unique peut être utilisée pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="f43fd-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="f43fd-118">La commande lie la clé `Ctrl+B` à un bloc de script qui efface la ligne, insère le mot « Build », puis accepte la ligne.</span><span class="sxs-lookup"><span data-stu-id="f43fd-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="f43fd-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f43fd-119">PARAMETERS</span></span>

### <span data-ttu-id="f43fd-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="f43fd-120">-BriefDescription</span></span>

<span data-ttu-id="f43fd-121">Brève description de la combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="f43fd-121">A brief description of the key binding.</span></span> <span data-ttu-id="f43fd-122">Cette description est affichée par l' `Get-PSReadLineKeyHandler` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f43fd-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="f43fd-123">-Corde</span><span class="sxs-lookup"><span data-stu-id="f43fd-123">-Chord</span></span>

<span data-ttu-id="f43fd-124">Clé ou séquence de clés à lier à une fonction ou à un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f43fd-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="f43fd-125">Utilisez une chaîne unique pour spécifier une seule liaison.</span><span class="sxs-lookup"><span data-stu-id="f43fd-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="f43fd-126">Si la liaison est une séquence de clés, séparez les clés par une virgule, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f43fd-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

> [!NOTE]
> <span data-ttu-id="f43fd-127">À partir de PSReadLine 2.0.0, le paramètre **corde** respecte la **casse**.</span><span class="sxs-lookup"><span data-stu-id="f43fd-127">As of PSReadLine 2.0.0, the **Chord** parameter is **case-sensitive**.</span></span> <span data-ttu-id="f43fd-128">Cela signifie `Ctrl+X` qu' `Ctrl+x` elle créera des liaisons différentes.</span><span class="sxs-lookup"><span data-stu-id="f43fd-128">Meaning, `Ctrl+X` and `Ctrl+x` will create different bindings.</span></span>

<span data-ttu-id="f43fd-129">Ce paramètre accepte un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="f43fd-129">This parameter accepts an array of strings.</span></span> <span data-ttu-id="f43fd-130">Chaque chaîne est une liaison distincte, et non une séquence de clés pour une seule liaison.</span><span class="sxs-lookup"><span data-stu-id="f43fd-130">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="f43fd-131">Description</span><span class="sxs-lookup"><span data-stu-id="f43fd-131">-Description</span></span>

<span data-ttu-id="f43fd-132">Spécifie une description plus détaillée de la combinaison de touches qui est visible dans la sortie de l’applet de commande `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="f43fd-132">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="f43fd-133">-Fonction</span><span class="sxs-lookup"><span data-stu-id="f43fd-133">-Function</span></span>

<span data-ttu-id="f43fd-134">Spécifie le nom d’un gestionnaire de clés existant fourni par PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="f43fd-134">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="f43fd-135">Ce paramètre vous permet de relier des liaisons de clés existantes ou de lier un gestionnaire qui est actuellement indépendant.</span><span class="sxs-lookup"><span data-stu-id="f43fd-135">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

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

### <span data-ttu-id="f43fd-136">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="f43fd-136">-ScriptBlock</span></span>

<span data-ttu-id="f43fd-137">Spécifie une valeur de bloc de script à exécuter lorsque le segment est entré.</span><span class="sxs-lookup"><span data-stu-id="f43fd-137">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="f43fd-138">PSReadLine transmet un ou deux paramètres à ce bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f43fd-138">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="f43fd-139">Le premier paramètre est un objet **ConsoleKeyInfo** représentant la touche enfoncée.</span><span class="sxs-lookup"><span data-stu-id="f43fd-139">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="f43fd-140">Le deuxième argument peut être n’importe quel objet en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="f43fd-140">The second argument can be any object depending on the context.</span></span>

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

### <span data-ttu-id="f43fd-141">-ViMode</span><span class="sxs-lookup"><span data-stu-id="f43fd-141">-ViMode</span></span>

<span data-ttu-id="f43fd-142">Spécifiez le mode VI auquel la liaison s’applique.</span><span class="sxs-lookup"><span data-stu-id="f43fd-142">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="f43fd-143">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="f43fd-143">Valid values are:</span></span>

- <span data-ttu-id="f43fd-144">Insérer</span><span class="sxs-lookup"><span data-stu-id="f43fd-144">Insert</span></span>
- <span data-ttu-id="f43fd-145">Commande</span><span class="sxs-lookup"><span data-stu-id="f43fd-145">Command</span></span>

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

### <span data-ttu-id="f43fd-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f43fd-146">CommonParameters</span></span>

<span data-ttu-id="f43fd-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f43fd-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f43fd-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f43fd-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f43fd-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f43fd-149">INPUTS</span></span>

### <span data-ttu-id="f43fd-150">None</span><span class="sxs-lookup"><span data-stu-id="f43fd-150">None</span></span>

<span data-ttu-id="f43fd-151">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f43fd-151">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="f43fd-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f43fd-152">OUTPUTS</span></span>

### <span data-ttu-id="f43fd-153">None</span><span class="sxs-lookup"><span data-stu-id="f43fd-153">None</span></span>

<span data-ttu-id="f43fd-154">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="f43fd-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f43fd-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f43fd-155">NOTES</span></span>

## <span data-ttu-id="f43fd-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f43fd-156">RELATED LINKS</span></span>

[<span data-ttu-id="f43fd-157">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="f43fd-157">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="f43fd-158">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="f43fd-158">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="f43fd-159">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="f43fd-159">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="f43fd-160">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="f43fd-160">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
