---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: ba61c2d24d85256c55a7409fc368de4407aad5a9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598972"
---
# <span data-ttu-id="4ac9f-102">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="4ac9f-102">Format-Wide</span></span>

## <span data-ttu-id="4ac9f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4ac9f-103">SYNOPSIS</span></span>
<span data-ttu-id="4ac9f-104">Met en forme des objets en tant que tableau large affichant une seule propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-104">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="4ac9f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4ac9f-105">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="4ac9f-106">Description</span><span class="sxs-lookup"><span data-stu-id="4ac9f-106">DESCRIPTION</span></span>

<span data-ttu-id="4ac9f-107">L' `Format-Wide` applet de commande met en forme les objets sous la forme d’un tableau étendu qui n’affiche qu’une seule propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-107">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="4ac9f-108">Vous pouvez utiliser le paramètre **Property** pour déterminer la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-108">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="4ac9f-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4ac9f-109">EXAMPLES</span></span>

### <span data-ttu-id="4ac9f-110">Exemple 1 : mettre en forme les noms des fichiers dans le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="4ac9f-110">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="4ac9f-111">Cette commande affiche les noms des fichiers du répertoire actif sous forme de trois colonnes à l'écran.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-111">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="4ac9f-112">L'applet de commande Get-ChildItem obtient les objets représentant chaque fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-112">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="4ac9f-113">L’opérateur de pipeline (|) passe les objets fichier via le pipeline à `Format-Wide` , qui les met en forme pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-113">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="4ac9f-114">Le paramètre **Column** spécifie le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-114">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="4ac9f-115">Exemple 2 : mettre en forme les noms des clés de Registre</span><span class="sxs-lookup"><span data-stu-id="4ac9f-115">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="4ac9f-116">Cette commande affiche les noms des clés de Registre de la clé HKEY_CURRENT_USER\Software\Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-116">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="4ac9f-117">L'applet de commande Get-ChildItem obtient les objets représentant les clés.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-117">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="4ac9f-118">Le chemin d’accès est spécifié sous la forme HKCU :, l’un des lecteurs exposés par le fournisseur de Registre PowerShell, suivi du chemin d’accès de la clé.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-118">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="4ac9f-119">L’opérateur de pipeline (|) passe les objets de clé de Registre à `Format-Wide` , qui les formate pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-119">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="4ac9f-120">Le paramètre **Property** spécifie le nom de la propriété et le paramètre **AutoSize** ajuste les colonnes pour améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-120">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="4ac9f-121">Exemple 3 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="4ac9f-121">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="4ac9f-122">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-122">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="4ac9f-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4ac9f-123">PARAMETERS</span></span>

### <span data-ttu-id="4ac9f-124">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="4ac9f-124">-AutoSize</span></span>

<span data-ttu-id="4ac9f-125">Ajuste la taille et le nombre de colonnes en fonction de la largeur des données.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-125">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="4ac9f-126">Par défaut, la vue détermine la taille et le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-126">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="4ac9f-127">Vous ne pouvez pas utiliser les paramètres **AutoSize** et **Column** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-127">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="4ac9f-128">-Colonne</span><span class="sxs-lookup"><span data-stu-id="4ac9f-128">-Column</span></span>

<span data-ttu-id="4ac9f-129">Spécifie le nombre de colonnes dans l'affichage.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-129">Specifies the number of columns in the display.</span></span> <span data-ttu-id="4ac9f-130">Vous ne pouvez pas utiliser les paramètres **AutoSize** et **Column** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-130">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="4ac9f-131">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="4ac9f-131">-DisplayError</span></span>

<span data-ttu-id="4ac9f-132">Affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-132">Displays errors at the command line.</span></span> <span data-ttu-id="4ac9f-133">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Wide` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-133">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="4ac9f-134">-Développer</span><span class="sxs-lookup"><span data-stu-id="4ac9f-134">-Expand</span></span>

<span data-ttu-id="4ac9f-135">Met en forme l'objet de collection, ainsi que les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-135">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="4ac9f-136">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l'interface ICollection (System.Collections).</span><span class="sxs-lookup"><span data-stu-id="4ac9f-136">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="4ac9f-137">La valeur par défaut est **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-137">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="4ac9f-138">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="4ac9f-138">Valid values are:</span></span>

- <span data-ttu-id="4ac9f-139">EnumOnly : affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-139">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="4ac9f-140">CoreOnly : affiche les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-140">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="4ac9f-141">Both : affiche les propriétés de l’objet de collection et les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-141">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="4ac9f-142">-Force</span><span class="sxs-lookup"><span data-stu-id="4ac9f-142">-Force</span></span>

<span data-ttu-id="4ac9f-143">Indique que cette applet de commande remplace les restrictions qui empêchent la commande de s’exécuter correctement, de sorte que les modifications ne compromettent pas la sécurité.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-143">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="4ac9f-144">Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-144">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="4ac9f-145">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="4ac9f-145">-GroupBy</span></span>

<span data-ttu-id="4ac9f-146">Formate la sortie dans des groupes basés sur une valeur ou propriété partagée.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-146">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="4ac9f-147">Entrez une expression ou une propriété de la sortie.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-147">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="4ac9f-148">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-148">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="4ac9f-149">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-149">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="4ac9f-150">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="4ac9f-150">Valid key-value pairs are:</span></span>

- <span data-ttu-id="4ac9f-151">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="4ac9f-151">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="4ac9f-152">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="4ac9f-152">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="4ac9f-153">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="4ac9f-153">FormatString - `<string>`</span></span>

<span data-ttu-id="4ac9f-154">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="4ac9f-154">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="4ac9f-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4ac9f-155">-InputObject</span></span>

<span data-ttu-id="4ac9f-156">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-156">Specifies the objects to format.</span></span> <span data-ttu-id="4ac9f-157">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-157">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="4ac9f-158">-Propriété</span><span class="sxs-lookup"><span data-stu-id="4ac9f-158">-Property</span></span>

<span data-ttu-id="4ac9f-159">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-159">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="4ac9f-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-160">Wildcards are permitted.</span></span>

<span data-ttu-id="4ac9f-161">Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-161">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="4ac9f-162">Le nom de paramètre « Property » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-162">The parameter name "Property" is optional.</span></span> <span data-ttu-id="4ac9f-163">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-163">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="4ac9f-164">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-164">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="4ac9f-165">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-165">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="4ac9f-166">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="4ac9f-166">Valid key-value pairs are:</span></span>

- <span data-ttu-id="4ac9f-167">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="4ac9f-167">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="4ac9f-168">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="4ac9f-168">FormatString - `<string>`</span></span>

<span data-ttu-id="4ac9f-169">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="4ac9f-169">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="4ac9f-170">-ShowError</span><span class="sxs-lookup"><span data-stu-id="4ac9f-170">-ShowError</span></span>

<span data-ttu-id="4ac9f-171">Envoie les erreurs via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-171">Sends errors through the pipeline.</span></span> <span data-ttu-id="4ac9f-172">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Wide` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-172">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="4ac9f-173">-Afficher</span><span class="sxs-lookup"><span data-stu-id="4ac9f-173">-View</span></span>

<span data-ttu-id="4ac9f-174">Spécifie le nom d’un autre format de table ou d’une autre vue.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-174">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="4ac9f-175">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="4ac9f-176">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ac9f-176">CommonParameters</span></span>

<span data-ttu-id="4ac9f-177">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-177">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ac9f-178">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4ac9f-178">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4ac9f-179">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4ac9f-179">INPUTS</span></span>

### <span data-ttu-id="4ac9f-180">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4ac9f-180">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4ac9f-181">Vous pouvez diriger n’importe quel objet vers `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="4ac9f-181">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="4ac9f-182">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4ac9f-182">OUTPUTS</span></span>

### <span data-ttu-id="4ac9f-183">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="4ac9f-183">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="4ac9f-184">`Format-Wide` retourne les objets de format représentant la table.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-184">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="4ac9f-185">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4ac9f-185">NOTES</span></span>

<span data-ttu-id="4ac9f-186">Vous pouvez également faire référence à `Format-Wide` par son alias intégré, `fw` .</span><span class="sxs-lookup"><span data-stu-id="4ac9f-186">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="4ac9f-187">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="4ac9f-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="4ac9f-188">Le paramètre **GroupBy** suppose que les objets sont triés.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-188">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="4ac9f-189">Utilisez `Sort-Object` avant `Format-Custom` d’utiliser pour regrouper les objets.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-189">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="4ac9f-190">Le paramètre **View** vous permet de spécifier un autre format pour la table.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-190">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="4ac9f-191">Vous pouvez utiliser les affichages définis dans les `*.format.PS1XML` fichiers du répertoire PowerShell ou vous pouvez créer vos propres affichages dans de nouveaux fichiers ps1xml et utiliser l' `Update-FormatData` applet de commande pour les inclure dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-191">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="4ac9f-192">L’autre vue pour le paramètre **View** doit utiliser le format de table ; Si ce n’est pas le cas, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-192">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="4ac9f-193">Si l’autre vue est une liste, utilisez `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="4ac9f-193">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="4ac9f-194">Si l'autre vue n'est ni une liste ni une table, utilisez Format-Custom.</span><span class="sxs-lookup"><span data-stu-id="4ac9f-194">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="4ac9f-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4ac9f-195">RELATED LINKS</span></span>

[<span data-ttu-id="4ac9f-196">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="4ac9f-196">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="4ac9f-197">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="4ac9f-197">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="4ac9f-198">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="4ac9f-198">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="4ac9f-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="4ac9f-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="4ac9f-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="4ac9f-200">Format-Table</span></span>](Format-Table.md)
