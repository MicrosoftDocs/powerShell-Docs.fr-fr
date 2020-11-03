---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: f26fc996b7fd029ed5994432080e51a1d83ec20e
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205969"
---
# <span data-ttu-id="4f9bd-103">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="4f9bd-103">Format-Wide</span></span>

## <span data-ttu-id="4f9bd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4f9bd-104">SYNOPSIS</span></span>
<span data-ttu-id="4f9bd-105">Met en forme des objets en tant que tableau large affichant une seule propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-105">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="4f9bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f9bd-106">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="4f9bd-107">Description</span><span class="sxs-lookup"><span data-stu-id="4f9bd-107">DESCRIPTION</span></span>

<span data-ttu-id="4f9bd-108">L' `Format-Wide` applet de commande met en forme les objets sous la forme d’un tableau étendu qui n’affiche qu’une seule propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-108">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="4f9bd-109">Vous pouvez utiliser le paramètre **Property** pour déterminer la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-109">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="4f9bd-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4f9bd-110">EXAMPLES</span></span>

### <span data-ttu-id="4f9bd-111">Exemple 1 : mettre en forme les noms des fichiers dans le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="4f9bd-111">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="4f9bd-112">Cette commande affiche les noms des fichiers du répertoire actif sous forme de trois colonnes à l'écran.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-112">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="4f9bd-113">L'applet de commande Get-ChildItem obtient les objets représentant chaque fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-113">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="4f9bd-114">L’opérateur de pipeline (|) passe les objets fichier via le pipeline à `Format-Wide` , qui les met en forme pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-114">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="4f9bd-115">Le paramètre **Column** spécifie le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-115">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="4f9bd-116">Exemple 2 : mettre en forme les noms des clés de Registre</span><span class="sxs-lookup"><span data-stu-id="4f9bd-116">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="4f9bd-117">Cette commande affiche les noms des clés de Registre de la clé HKEY_CURRENT_USER\Software\Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-117">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="4f9bd-118">L'applet de commande Get-ChildItem obtient les objets représentant les clés.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-118">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="4f9bd-119">Le chemin d’accès est spécifié sous la forme HKCU :, l’un des lecteurs exposés par le fournisseur de Registre PowerShell, suivi du chemin d’accès de la clé.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-119">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="4f9bd-120">L’opérateur de pipeline (|) passe les objets de clé de Registre à `Format-Wide` , qui les formate pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-120">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="4f9bd-121">Le paramètre **Property** spécifie le nom de la propriété et le paramètre **AutoSize** ajuste les colonnes pour améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-121">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="4f9bd-122">Exemple 3 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="4f9bd-122">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="4f9bd-123">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-123">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="4f9bd-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f9bd-124">PARAMETERS</span></span>

### <span data-ttu-id="4f9bd-125">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="4f9bd-125">-AutoSize</span></span>

<span data-ttu-id="4f9bd-126">Ajuste la taille et le nombre de colonnes en fonction de la largeur des données.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-126">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="4f9bd-127">Par défaut, la vue détermine la taille et le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-127">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="4f9bd-128">Vous ne pouvez pas utiliser les paramètres **AutoSize** et **Column** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-128">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="4f9bd-129">-Colonne</span><span class="sxs-lookup"><span data-stu-id="4f9bd-129">-Column</span></span>

<span data-ttu-id="4f9bd-130">Spécifie le nombre de colonnes dans l'affichage.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-130">Specifies the number of columns in the display.</span></span> <span data-ttu-id="4f9bd-131">Vous ne pouvez pas utiliser les paramètres **AutoSize** et **Column** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-131">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f9bd-132">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="4f9bd-132">-DisplayError</span></span>

<span data-ttu-id="4f9bd-133">Affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-133">Displays errors at the command line.</span></span> <span data-ttu-id="4f9bd-134">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Wide` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-134">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="4f9bd-135">-Développer</span><span class="sxs-lookup"><span data-stu-id="4f9bd-135">-Expand</span></span>

<span data-ttu-id="4f9bd-136">Met en forme l'objet de collection, ainsi que les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-136">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="4f9bd-137">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l'interface ICollection (System.Collections).</span><span class="sxs-lookup"><span data-stu-id="4f9bd-137">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="4f9bd-138">La valeur par défaut est **EnumOnly** .</span><span class="sxs-lookup"><span data-stu-id="4f9bd-138">The default value is **EnumOnly** .</span></span>

<span data-ttu-id="4f9bd-139">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="4f9bd-139">Valid values are:</span></span>

- <span data-ttu-id="4f9bd-140">EnumOnly : affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-140">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="4f9bd-141">CoreOnly : affiche les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-141">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="4f9bd-142">Both : affiche les propriétés de l’objet de collection et les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-142">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f9bd-143">-Force</span><span class="sxs-lookup"><span data-stu-id="4f9bd-143">-Force</span></span>

<span data-ttu-id="4f9bd-144">Indique que cette applet de commande remplace les restrictions qui empêchent la commande de s’exécuter correctement, de sorte que les modifications ne compromettent pas la sécurité.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-144">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="4f9bd-145">Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-145">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="4f9bd-146">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="4f9bd-146">-GroupBy</span></span>

<span data-ttu-id="4f9bd-147">Formate la sortie dans des groupes basés sur une valeur ou propriété partagée.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-147">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="4f9bd-148">Entrez une expression ou une propriété de la sortie.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-148">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="4f9bd-149">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-149">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="4f9bd-150">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-150">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="4f9bd-151">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="4f9bd-151">Valid key-value pairs are:</span></span>

- <span data-ttu-id="4f9bd-152">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="4f9bd-152">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="4f9bd-153">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="4f9bd-153">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="4f9bd-154">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="4f9bd-154">FormatString - `<string>`</span></span>

<span data-ttu-id="4f9bd-155">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="4f9bd-155">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f9bd-156">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4f9bd-156">-InputObject</span></span>

<span data-ttu-id="4f9bd-157">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-157">Specifies the objects to format.</span></span> <span data-ttu-id="4f9bd-158">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f9bd-159">-Propriété</span><span class="sxs-lookup"><span data-stu-id="4f9bd-159">-Property</span></span>

<span data-ttu-id="4f9bd-160">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-160">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="4f9bd-161">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-161">Wildcards are permitted.</span></span>

<span data-ttu-id="4f9bd-162">Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-162">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="4f9bd-163">Le nom de paramètre « Property » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-163">The parameter name "Property" is optional.</span></span> <span data-ttu-id="4f9bd-164">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-164">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="4f9bd-165">La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-165">The value of the **Property** parameter can be a new calculated property.The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="4f9bd-166">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="4f9bd-166">Valid key-value pairs are:</span></span>

- <span data-ttu-id="4f9bd-167">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="4f9bd-167">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="4f9bd-168">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="4f9bd-168">FormatString - `<string>`</span></span>

<span data-ttu-id="4f9bd-169">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="4f9bd-169">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4f9bd-170">-ShowError</span><span class="sxs-lookup"><span data-stu-id="4f9bd-170">-ShowError</span></span>

<span data-ttu-id="4f9bd-171">Envoie les erreurs via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-171">Sends errors through the pipeline.</span></span> <span data-ttu-id="4f9bd-172">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Wide` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-172">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="4f9bd-173">-Afficher</span><span class="sxs-lookup"><span data-stu-id="4f9bd-173">-View</span></span>

<span data-ttu-id="4f9bd-174">Spécifie le nom d’un autre format de table ou d’une autre vue.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-174">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="4f9bd-175">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f9bd-176">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f9bd-176">CommonParameters</span></span>

<span data-ttu-id="4f9bd-177">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-177">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f9bd-178">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f9bd-178">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f9bd-179">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4f9bd-179">INPUTS</span></span>

### <span data-ttu-id="4f9bd-180">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4f9bd-180">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4f9bd-181">Vous pouvez diriger n’importe quel objet vers `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="4f9bd-181">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="4f9bd-182">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4f9bd-182">OUTPUTS</span></span>

### <span data-ttu-id="4f9bd-183">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="4f9bd-183">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="4f9bd-184">`Format-Wide` retourne les objets de format représentant la table.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-184">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="4f9bd-185">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4f9bd-185">NOTES</span></span>

<span data-ttu-id="4f9bd-186">Vous pouvez également faire référence à `Format-Wide` par son alias intégré, `fw` .</span><span class="sxs-lookup"><span data-stu-id="4f9bd-186">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="4f9bd-187">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="4f9bd-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="4f9bd-188">Le paramètre **GroupBy** suppose que les objets sont triés.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-188">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="4f9bd-189">Utilisez `Sort-Object` avant `Format-Custom` d’utiliser pour regrouper les objets.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-189">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="4f9bd-190">Le paramètre **View** vous permet de spécifier un autre format pour la table.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-190">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="4f9bd-191">Vous pouvez utiliser les affichages définis dans les `*.format.PS1XML` fichiers du répertoire PowerShell ou vous pouvez créer vos propres affichages dans de nouveaux fichiers ps1xml et utiliser l' `Update-FormatData` applet de commande pour les inclure dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-191">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="4f9bd-192">L’autre vue pour le paramètre **View** doit utiliser le format de table ; Si ce n’est pas le cas, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-192">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="4f9bd-193">Si l’autre vue est une liste, utilisez `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="4f9bd-193">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="4f9bd-194">Si l'autre vue n'est ni une liste ni une table, utilisez Format-Custom.</span><span class="sxs-lookup"><span data-stu-id="4f9bd-194">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="4f9bd-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4f9bd-195">RELATED LINKS</span></span>

[<span data-ttu-id="4f9bd-196">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="4f9bd-196">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="4f9bd-197">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="4f9bd-197">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="4f9bd-198">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="4f9bd-198">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="4f9bd-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="4f9bd-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="4f9bd-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="4f9bd-200">Format-Table</span></span>](Format-Table.md)
