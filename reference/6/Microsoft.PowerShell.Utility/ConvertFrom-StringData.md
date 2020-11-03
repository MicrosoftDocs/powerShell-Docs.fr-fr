---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: 8ffb7a33bb1b4b5409c48445b88a8eb58f9b93b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204702"
---
# <span data-ttu-id="39202-103">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="39202-103">ConvertFrom-StringData</span></span>

## <span data-ttu-id="39202-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="39202-104">SYNOPSIS</span></span>
<span data-ttu-id="39202-105">Convertit une chaîne contenant une ou plusieurs paires clé/valeur en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-105">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="39202-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="39202-106">SYNTAX</span></span>

### <span data-ttu-id="39202-107">Tous</span><span class="sxs-lookup"><span data-stu-id="39202-107">All</span></span>

```
ConvertFrom-StringData [-StringData] <String> [<CommonParameters>]
```

## <span data-ttu-id="39202-108">Description</span><span class="sxs-lookup"><span data-stu-id="39202-108">DESCRIPTION</span></span>

<span data-ttu-id="39202-109">L' `ConvertFrom-StringData` applet de commande convertit une chaîne qui contient une ou plusieurs paires clé/valeur en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-109">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="39202-110">Étant donné que chaque paire clé-valeur doit se trouver sur une ligne distincte, les chaînes sont souvent utilisées comme format d’entrée.</span><span class="sxs-lookup"><span data-stu-id="39202-110">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="39202-111">Par défaut, la **clé** doit être séparée de la **valeur** par un caractère signe égal ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="39202-111">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="39202-112">L' `ConvertFrom-StringData` applet de commande est considérée comme une applet de commande sécurisée qui peut être utilisée dans la `DATA` section d’un script ou d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="39202-112">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="39202-113">Lorsqu’il est utilisé dans une `DATA` section, le contenu de la chaîne doit se conformer aux règles d’une section de données.</span><span class="sxs-lookup"><span data-stu-id="39202-113">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="39202-114">Pour plus d’informations, consultez [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span><span class="sxs-lookup"><span data-stu-id="39202-114">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="39202-115">`ConvertFrom-StringData` prend en charge les séquences de caractères d’échappement qui sont autorisées par les outils de traduction automatique conventionnels.</span><span class="sxs-lookup"><span data-stu-id="39202-115">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="39202-116">Autrement dit, l’applet de commande peut interpréter les barres obliques inverses ( `\` ) comme des caractères d’échappement dans les données de chaîne à l’aide de la [méthode Regex. Unescape](/dotnet/api/system.text.regularexpressions.regex.unescape), au lieu du caractère de \` soulignement () PowerShell qui signalerait normalement la fin d’une ligne dans un script.</span><span class="sxs-lookup"><span data-stu-id="39202-116">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="39202-117">À l'intérieur de la chaîne « ici-même », le caractère de guillemet inversé ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="39202-117">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="39202-118">Vous pouvez également conserver une barre oblique inverse littérale dans vos résultats en l’plaçant dans une séquence d’échappement avec une barre oblique inverse précédente, comme suit : `\\` .</span><span class="sxs-lookup"><span data-stu-id="39202-118">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="39202-119">Les caractères de barre oblique inverse sans séquence d'échappement, comme celles qui sont couramment utilisées dans les chemins d'accès, peuvent apparaître comme des séquences d'échappement non autorisées dans vos résultats.</span><span class="sxs-lookup"><span data-stu-id="39202-119">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

## <span data-ttu-id="39202-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="39202-120">EXAMPLES</span></span>

### <span data-ttu-id="39202-121">Exemple 1 : convertir une chaîne « here » entre guillemets simples en une table de hachage</span><span class="sxs-lookup"><span data-stu-id="39202-121">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="39202-122">Cet exemple convertit une chaîne « ici- » en une seule citation de messages utilisateur en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-122">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="39202-123">Dans une chaîne entre guillemets simples, les variables ne sont pas remplacées par les valeurs et les expressions ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="39202-123">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="39202-124">L' `ConvertFrom-StringData` applet de commande convertit la valeur de la `$Here` variable en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-124">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### <span data-ttu-id="39202-125">Exemple 2 : convertir une chaîne here contenant un commentaire</span><span class="sxs-lookup"><span data-stu-id="39202-125">Example 2: Convert a here-string containing a comment</span></span>

<span data-ttu-id="39202-126">Cet exemple convertit une chaîne « here » qui contient un commentaire et plusieurs paires clé-valeur en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-126">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

<span data-ttu-id="39202-127">La valeur du paramètre **StringData** est une chaîne ici, au lieu d’une variable qui contient une chaîne ici.</span><span class="sxs-lookup"><span data-stu-id="39202-127">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="39202-128">Les deux formats sont valides.</span><span class="sxs-lookup"><span data-stu-id="39202-128">Either format is valid.</span></span> <span data-ttu-id="39202-129">La chaîne « ici-même » contient un commentaire sur une des chaînes.</span><span class="sxs-lookup"><span data-stu-id="39202-129">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="39202-130">`ConvertFrom-StringData` ignore les commentaires sur une seule ligne, mais le `#` caractère doit être le premier caractère autre qu’un espace blanc sur la ligne.</span><span class="sxs-lookup"><span data-stu-id="39202-130">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="39202-131">Tous les caractères de la ligne après `#` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="39202-131">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="39202-132">Exemple 3 : convertir une chaîne en une table de hachage</span><span class="sxs-lookup"><span data-stu-id="39202-132">Example 3: Convert a string to a hash table</span></span>

<span data-ttu-id="39202-133">Cet exemple convertit une chaîne entre guillemets standard (pas une chaîne ici) en une table de hachage et l’enregistre dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="39202-133">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

<span data-ttu-id="39202-134">Pour satisfaire la condition selon laquelle chaque paire clé-valeur doit se trouver sur une ligne distincte, la chaîne utilise le caractère de saut de ligne de PowerShell ( \` n) pour séparer les paires.</span><span class="sxs-lookup"><span data-stu-id="39202-134">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="39202-135">Exemple 4 : utiliser ConvertFrom-StringData dans la section de données d’un script</span><span class="sxs-lookup"><span data-stu-id="39202-135">Example 4: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="39202-136">Cet exemple montre une `ConvertFrom-StringData` commande utilisée dans la section Data d’un script.</span><span class="sxs-lookup"><span data-stu-id="39202-136">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="39202-137">Les instructions sous la section DATA affichent le texte à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="39202-137">The statements below the DATA section display the text to the user.</span></span>

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

<span data-ttu-id="39202-138">Comme le texte comprend des noms de variables, il doit figurer dans une chaîne entre guillemets simples pour que les variables soient interprétées littéralement et non pas développées.</span><span class="sxs-lookup"><span data-stu-id="39202-138">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="39202-139">Les variables ne sont pas autorisées dans la section **Data** .</span><span class="sxs-lookup"><span data-stu-id="39202-139">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="39202-140">Exemple 5 : utiliser l’opérateur de pipeline pour passer une chaîne</span><span class="sxs-lookup"><span data-stu-id="39202-140">Example 5: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="39202-141">Cet exemple montre que vous pouvez utiliser un opérateur de pipeline ( `|` ) pour envoyer une chaîne à `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="39202-141">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="39202-142">La valeur de la `$Here` variable est dirigée vers `ConvertFrom-StringData` et le résultat dans la `$Hash` variable.</span><span class="sxs-lookup"><span data-stu-id="39202-142">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### <span data-ttu-id="39202-143">Exemple 6 : utiliser des caractères d’échappement pour ajouter de nouvelles lignes et retourner des caractères</span><span class="sxs-lookup"><span data-stu-id="39202-143">Example 6: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="39202-144">Cet exemple illustre l’utilisation de caractères d’échappement pour créer des lignes et retourner des caractères dans les données sources.</span><span class="sxs-lookup"><span data-stu-id="39202-144">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="39202-145">La séquence `\n` d’échappement est utilisée pour créer de nouvelles lignes au sein d’un bloc de texte associé à un nom ou à un élément dans la table de hachage résultante.</span><span class="sxs-lookup"><span data-stu-id="39202-145">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### <span data-ttu-id="39202-146">Exemple 7 : utiliser le caractère d’échappement barre oblique inverse pour restituer correctement un chemin d’accès de fichier</span><span class="sxs-lookup"><span data-stu-id="39202-146">Example 7: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="39202-147">Cet exemple montre comment utiliser le caractère d’échappement barre oblique inverse dans les données de chaîne pour permettre le rendu correct d’un chemin d’accès de fichier dans la table de hachage résultante `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="39202-147">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="39202-148">La double barre oblique inverse fait que les caractères de barre oblique inverse littérale s'affichent correctement dans la sortie de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-148">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="39202-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="39202-149">PARAMETERS</span></span>

### <span data-ttu-id="39202-150">-StringData</span><span class="sxs-lookup"><span data-stu-id="39202-150">-StringData</span></span>

<span data-ttu-id="39202-151">Spécifie la chaîne à convertir.</span><span class="sxs-lookup"><span data-stu-id="39202-151">Specifies the string to be converted.</span></span> <span data-ttu-id="39202-152">Vous pouvez utiliser ce paramètre ou diriger une chaîne vers `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="39202-152">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="39202-153">Le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="39202-153">The parameter name is optional.</span></span>

<span data-ttu-id="39202-154">La valeur de ce paramètre doit être une chaîne qui contient une ou plusieurs paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="39202-154">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="39202-155">Chaque paire clé-valeur doit se trouver sur une ligne distincte, ou chaque paire doit être séparée par des caractères de saut de ligne ( \` n).</span><span class="sxs-lookup"><span data-stu-id="39202-155">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="39202-156">Vous pouvez inclure des commentaires dans la chaîne, mais les commentaires ne peuvent pas se trouver sur la même ligne qu’une paire clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="39202-156">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="39202-157">`ConvertFrom-StringData` ignore les commentaires sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="39202-157">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="39202-158">Le `#` caractère doit être le premier caractère autre qu’un espace blanc sur la ligne.</span><span class="sxs-lookup"><span data-stu-id="39202-158">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="39202-159">Tous les caractères de la ligne après `#` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="39202-159">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="39202-160">Les commentaires ne sont pas inclus dans la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="39202-160">The comments are not included in the hash table.</span></span>

<span data-ttu-id="39202-161">Une chaîne ici est une chaîne composée d’une ou de plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="39202-161">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="39202-162">Les guillemets dans la chaîne ici sont interprétés littéralement comme faisant partie des données de chaîne.</span><span class="sxs-lookup"><span data-stu-id="39202-162">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="39202-163">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="39202-163">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="39202-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="39202-164">CommonParameters</span></span>

<span data-ttu-id="39202-165">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="39202-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="39202-166">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="39202-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="39202-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="39202-167">INPUTS</span></span>

### <span data-ttu-id="39202-168">System.String</span><span class="sxs-lookup"><span data-stu-id="39202-168">System.String</span></span>

<span data-ttu-id="39202-169">Vous pouvez diriger une chaîne contenant une paire clé-valeur vers `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="39202-169">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="39202-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="39202-170">OUTPUTS</span></span>

### <span data-ttu-id="39202-171">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="39202-171">System.Collections.Hashtable</span></span>

<span data-ttu-id="39202-172">Cette applet de commande retourne une table de hachage qu’elle crée à partir des paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="39202-172">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="39202-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="39202-173">NOTES</span></span>

<span data-ttu-id="39202-174">Une chaîne « ici-même » est une chaîne composée d'une ou plusieurs lignes, dans laquelle les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="39202-174">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="39202-175">Cette applet de commande peut être utile dans les scripts qui affichent des messages utilisateur dans plusieurs langues parlées.</span><span class="sxs-lookup"><span data-stu-id="39202-175">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="39202-176">Vous pouvez utiliser les tables de hachage de type dictionnaire pour isoler les chaînes de texte du code, comme dans des fichiers de ressources, et pour mettre en forme les chaînes de texte pour qu'elles soient utilisables dans des outils de traduction.</span><span class="sxs-lookup"><span data-stu-id="39202-176">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="39202-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="39202-177">RELATED LINKS</span></span>
