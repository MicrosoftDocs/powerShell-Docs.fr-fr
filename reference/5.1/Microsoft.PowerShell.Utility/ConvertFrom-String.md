---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206185"
---
# <span data-ttu-id="34d65-103">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="34d65-103">ConvertFrom-String</span></span>

## <span data-ttu-id="34d65-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="34d65-104">SYNOPSIS</span></span>
<span data-ttu-id="34d65-105">Extrait et analyse les propriétés structurées à partir du contenu de chaîne.</span><span class="sxs-lookup"><span data-stu-id="34d65-105">Extracts and parses structured properties from string content.</span></span>

## <span data-ttu-id="34d65-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34d65-106">SYNTAX</span></span>

### <span data-ttu-id="34d65-107">ByDelimiter (par défaut)</span><span class="sxs-lookup"><span data-stu-id="34d65-107">ByDelimiter (Default)</span></span>

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="34d65-108">TemplateParsing</span><span class="sxs-lookup"><span data-stu-id="34d65-108">TemplateParsing</span></span>

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="34d65-109">Description</span><span class="sxs-lookup"><span data-stu-id="34d65-109">DESCRIPTION</span></span>

<span data-ttu-id="34d65-110">L’applet de commande **ConvertFrom-String** extrait et analyse les propriétés structurées à partir du contenu de chaîne.</span><span class="sxs-lookup"><span data-stu-id="34d65-110">The **ConvertFrom-String** cmdlet extracts and parses structured properties from string content.</span></span>
<span data-ttu-id="34d65-111">Cette applet de commande génère un objet en analysant du texte à partir d’un flux de texte traditionnel.</span><span class="sxs-lookup"><span data-stu-id="34d65-111">This cmdlet generates an object by parsing text from a traditional text stream.</span></span>
<span data-ttu-id="34d65-112">Pour chaque chaîne dans le pipeline, l’applet de commande fractionne l’entrée par un délimiteur ou une expression d’analyse, puis assigne des noms de propriété à chacun des éléments fractionnés résultants.</span><span class="sxs-lookup"><span data-stu-id="34d65-112">For each string in the pipeline, the cmdlet splits the input by either a delimiter or a parse expression, and then assigns property names to each of the resulting split elements.</span></span>
<span data-ttu-id="34d65-113">Vous pouvez fournir ces noms de propriétés. Si vous ne le faites pas, ils sont automatiquement générés pour vous.</span><span class="sxs-lookup"><span data-stu-id="34d65-113">You can provide these property names; if you do not, they are automatically generated for you.</span></span>

<span data-ttu-id="34d65-114">Le jeu de paramètres par défaut de l’applet de commande, **ByDelimiter** , se divise exactement par le délimiteur d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="34d65-114">The cmdlet's default parameter set, **ByDelimiter** , splits exactly on the regular expression delimiter.</span></span>
<span data-ttu-id="34d65-115">Il n’effectue pas de correspondance de guillemets ou de délimiteurs dans le cadre de l’applet de commande `Import-Csv` .</span><span class="sxs-lookup"><span data-stu-id="34d65-115">It does not perform quote matching or delimiter escaping as the `Import-Csv` cmdlet does.</span></span>

<span data-ttu-id="34d65-116">Le jeu de paramètres alternatif de l’applet de commande, **TemplateParsing** , génère des éléments à partir des groupes capturés par une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="34d65-116">The cmdlet's alternate parameter set, **TemplateParsing** , generates elements from the groups that are captured by a regular expression.</span></span> <span data-ttu-id="34d65-117">Pour plus d’informations sur les expressions régulières, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="34d65-117">For more information on regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

<span data-ttu-id="34d65-118">Cette applet de commande prend en charge deux modes : l’analyse de base délimitée et l’analyse basée sur les exemples générées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="34d65-118">This cmdlet supports two modes: basic delimited parsing, and automatically-generated, example-driven parsing.</span></span>

<span data-ttu-id="34d65-119">Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants.</span><span class="sxs-lookup"><span data-stu-id="34d65-119">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="34d65-120">Vous pouvez personnaliser le délimiteur en canalisant les `ConvertFrom-String` résultats dans l’une des `Format-*` applets de commande, ou vous pouvez utiliser le paramètre **Delimiter** .</span><span class="sxs-lookup"><span data-stu-id="34d65-120">You can customize the delimiter by piping the `ConvertFrom-String` results into one of the `Format-*` cmdlets, or you can use the **Delimiter** parameter.</span></span>

<span data-ttu-id="34d65-121">L’applet de commande prend également en charge l’analyse générée automatiquement, basée sur des exemples, basée sur le [FlashExtract, la recherche effectuée par Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span><span class="sxs-lookup"><span data-stu-id="34d65-121">The cmdlet also supports automatically-generated, example-driven parsing based on the [FlashExtract, research work by Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span></span>

## <span data-ttu-id="34d65-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="34d65-122">EXAMPLES</span></span>

### <span data-ttu-id="34d65-123">Exemple 1 : générer un objet avec des noms de propriétés par défaut</span><span class="sxs-lookup"><span data-stu-id="34d65-123">Example 1: Generate an object with default property names</span></span>

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

<span data-ttu-id="34d65-124">Cette commande génère un objet avec des noms de propriétés par défaut, **P1** et **P2** .</span><span class="sxs-lookup"><span data-stu-id="34d65-124">This command generates an object with default property names, **P1** and **P2** .</span></span>

### <span data-ttu-id="34d65-125">Exemple 1A : découverte de l’objet généré</span><span class="sxs-lookup"><span data-stu-id="34d65-125">Example 1A: Get to know the generated object</span></span>

<span data-ttu-id="34d65-126">Cette commande génère un objet avec les propriétés **P1** , **P2** ; par défaut, les deux propriétés sont de type **chaîne** .</span><span class="sxs-lookup"><span data-stu-id="34d65-126">This command generates one object with properties **P1** , **P2** ; both properties are of **String** type, by default.</span></span>

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### <span data-ttu-id="34d65-127">Exemple 2 : générer un objet avec des noms de propriétés par défaut à l’aide d’un délimiteur</span><span class="sxs-lookup"><span data-stu-id="34d65-127">Example 2: Generate an object with default property names using a delimiter</span></span>

<span data-ttu-id="34d65-128">Cette commande génère un objet avec un domaine et un nom d’utilisateur en utilisant la barre oblique inverse ( `\` ) comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="34d65-128">This command generates an object with a domain and username using the backslash (`\`) as the delimiter.</span></span> <span data-ttu-id="34d65-129">La barre oblique inverse doit être placée dans une séquence d’échappement avec une autre barre oblique inverse lors de l’utilisation d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="34d65-129">The backslash character must be escaped with another backslash when using regular expressions.</span></span>

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### <span data-ttu-id="34d65-130">Exemple 3 : générer un objet qui contient deux propriétés nommées</span><span class="sxs-lookup"><span data-stu-id="34d65-130">Example 3: Generate an object that contains two named properties</span></span>

<span data-ttu-id="34d65-131">L’exemple suivant crée des objets à partir de Windows héberge des entrées de fichier.</span><span class="sxs-lookup"><span data-stu-id="34d65-131">The following example creates objects from Windows hosts file entries.</span></span>

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

<span data-ttu-id="34d65-132">L' `Get-Content` applet de commande stocke le contenu d’un fichier d’hôtes Windows dans `$content` .</span><span class="sxs-lookup"><span data-stu-id="34d65-132">The `Get-Content` cmdlet stores the content of a Windows hosts file in `$content`.</span></span> <span data-ttu-id="34d65-133">La deuxième commande supprime tous les commentaires au début du fichier hosts à l’aide d’une expression régulière qui correspond à une ligne qui ne commence pas par ( `#` ).</span><span class="sxs-lookup"><span data-stu-id="34d65-133">The second command removes any comments at the beginning of the hosts file using a regular expression that matches any line that does not start with (`#`).</span></span> <span data-ttu-id="34d65-134">La dernière commande convertit le texte restant en objets avec les propriétés **Server** et **IP** .</span><span class="sxs-lookup"><span data-stu-id="34d65-134">The last command converts the remaining text into objects with **Server** and **IP** properties.</span></span>

### <span data-ttu-id="34d65-135">Exemple 4 : utilisez une expression comme valeur du paramètre TemplateContent, puis enregistrez les résultats dans une variable.</span><span class="sxs-lookup"><span data-stu-id="34d65-135">Example 4: Use an expression as the value of the TemplateContent parameter, save the results in a variable.</span></span>

<span data-ttu-id="34d65-136">Cette commande utilise une expression comme valeur du paramètre **TemplateContent** .</span><span class="sxs-lookup"><span data-stu-id="34d65-136">This command uses an expression as the value of the **TemplateContent** parameter.</span></span>
<span data-ttu-id="34d65-137">L’expression est enregistrée dans une variable pour des raisons de simplicité.</span><span class="sxs-lookup"><span data-stu-id="34d65-137">The expression is saved in a variable for simplicity.</span></span>
<span data-ttu-id="34d65-138">Windows PowerShell comprend maintenant que la chaîne utilisée sur le pipeline `ConvertFrom-String` possède trois propriétés :</span><span class="sxs-lookup"><span data-stu-id="34d65-138">Windows PowerShell understands now that the string that is used on the pipeline to `ConvertFrom-String` has three properties:</span></span>

- <span data-ttu-id="34d65-139">**Nom**</span><span class="sxs-lookup"><span data-stu-id="34d65-139">**Name**</span></span>
- <span data-ttu-id="34d65-140">**phone**</span><span class="sxs-lookup"><span data-stu-id="34d65-140">**phone**</span></span>
- <span data-ttu-id="34d65-141">**vieillissement**</span><span class="sxs-lookup"><span data-stu-id="34d65-141">**age**</span></span>

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

<span data-ttu-id="34d65-142">Chaque ligne de l’entrée est évaluée par les correspondances d’échantillon.</span><span class="sxs-lookup"><span data-stu-id="34d65-142">Each line in the input is evaluated by the sample matches.</span></span> <span data-ttu-id="34d65-143">Si la ligne correspond aux exemples fournis dans le modèle, les valeurs sont extraites et transmises à la variable de sortie.</span><span class="sxs-lookup"><span data-stu-id="34d65-143">If the line matches the examples given in the pattern, values are extracted and passed to the output variable.</span></span>

<span data-ttu-id="34d65-144">Les exemples de données, `$template` , fournissent deux formats de téléphone différents :</span><span class="sxs-lookup"><span data-stu-id="34d65-144">The sample data, `$template`, provides two different phone formats:</span></span>

- `425-123-6789`
- `(206) 987-4321`

<span data-ttu-id="34d65-145">Les exemples de données fournissent également deux formats d’âge différents :</span><span class="sxs-lookup"><span data-stu-id="34d65-145">The sample data also provides two different age formats:</span></span>

- `6`
- `12`

<span data-ttu-id="34d65-146">Cela implique que les téléphones comme `(206) 987 4321` ne seront pas reconnus, car il n’y a pas d’exemple de données correspondant à ce modèle, car il n’y a pas de trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="34d65-146">This implies that phones like `(206) 987 4321` will not be recognized, because there's no sample data that matches that pattern because there are no hyphens.</span></span>

### <span data-ttu-id="34d65-147">Exemple 5 : spécification des types de données pour les propriétés générées</span><span class="sxs-lookup"><span data-stu-id="34d65-147">Example 5: Specifying data types to the generated properties</span></span>

<span data-ttu-id="34d65-148">Il s’agit du même exemple que l’exemple 4, ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="34d65-148">This is the same example as Example 4, above.</span></span>
<span data-ttu-id="34d65-149">La différence est que la chaîne de modèle comprend un type de données pour chaque propriété souhaitée.</span><span class="sxs-lookup"><span data-stu-id="34d65-149">The difference is that the pattern string includes a data type for each desired property.</span></span>

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

<span data-ttu-id="34d65-150">L' `Get-Member` applet de commande est utilisée pour indiquer que la propriété **Age** est un entier.</span><span class="sxs-lookup"><span data-stu-id="34d65-150">The `Get-Member` cmdlet is used to show that the **age** property is an integer.</span></span>

## <span data-ttu-id="34d65-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34d65-151">PARAMETERS</span></span>

### <span data-ttu-id="34d65-152">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="34d65-152">-Delimiter</span></span>

<span data-ttu-id="34d65-153">Spécifie une expression régulière qui identifie la limite entre les éléments.</span><span class="sxs-lookup"><span data-stu-id="34d65-153">Specifies a regular expression that identifies the boundary between elements.</span></span>
<span data-ttu-id="34d65-154">Les éléments créés par le fractionnement deviennent des propriétés dans l’objet résultant.</span><span class="sxs-lookup"><span data-stu-id="34d65-154">Elements that are created by the split become properties in the resulting object.</span></span>
<span data-ttu-id="34d65-155">Le délimiteur est finalement utilisé dans un appel à la méthode **Split** du type `[System.Text.RegularExpressions.RegularExpression]` .</span><span class="sxs-lookup"><span data-stu-id="34d65-155">The delimiter is ultimately used in a call to the **Split** method of the type `[System.Text.RegularExpressions.RegularExpression]`.</span></span>

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34d65-156">-Paramètre includeextent</span><span class="sxs-lookup"><span data-stu-id="34d65-156">-IncludeExtent</span></span>

<span data-ttu-id="34d65-157">Indique que cette applet de commande comprend une propriété de texte d’étendue qui est supprimée par défaut.</span><span class="sxs-lookup"><span data-stu-id="34d65-157">Indicates that this cmdlet includes an extent text property that is removed by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34d65-158">-InputObject</span><span class="sxs-lookup"><span data-stu-id="34d65-158">-InputObject</span></span>

<span data-ttu-id="34d65-159">Spécifie les chaînes reçues du pipeline, ou une variable qui contient un objet String.</span><span class="sxs-lookup"><span data-stu-id="34d65-159">Specifies strings received from the pipeline, or a variable that contains a string object.</span></span>

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

### <span data-ttu-id="34d65-160">-PropertyNames</span><span class="sxs-lookup"><span data-stu-id="34d65-160">-PropertyNames</span></span>

<span data-ttu-id="34d65-161">Spécifie un tableau de noms de propriétés auquel assigner des valeurs de fractionnement dans l’objet résultant.</span><span class="sxs-lookup"><span data-stu-id="34d65-161">Specifies an array of property names to which to assign split values in the resulting object.</span></span>
<span data-ttu-id="34d65-162">Chaque ligne de texte que vous fractionnez ou analysez génère des éléments qui représentent des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="34d65-162">Every line of text that you split or parse generates elements that represent property values.</span></span>
<span data-ttu-id="34d65-163">Si l’élément est le résultat d’un groupe de capture et que ce groupe de capture est nommé (par exemple, `(?<name>)` ou `(?'name')` ), le nom de ce groupe de capture est assigné à la propriété.</span><span class="sxs-lookup"><span data-stu-id="34d65-163">If the element is the result of a capture group, and that capture group is named (for example, `(?<name>)` or `(?'name')` ), then the name of that capture group is assigned to the property.</span></span>

<span data-ttu-id="34d65-164">Si vous fournissez des éléments dans le tableau **PropertyName** , ces noms sont assignés à des propriétés qui n’ont pas encore été nommées.</span><span class="sxs-lookup"><span data-stu-id="34d65-164">If you provide any elements in the **PropertyName** array, those names are assigned to properties that have not yet been named.</span></span>

<span data-ttu-id="34d65-165">Si vous fournissez plus de noms de propriétés qu’il n’y a de champs, PowerShell ignore les noms de propriété supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="34d65-165">If you provide more property names than there are fields, PowerShell ignores the extra property names.</span></span> <span data-ttu-id="34d65-166">Si vous ne spécifiez pas un nombre de noms de propriété suffisant pour nommer tous les champs, PowerShell attribue automatiquement des noms de propriété numériques à toutes les propriétés qui ne sont pas nommées : **P1** , **P2** , etc.</span><span class="sxs-lookup"><span data-stu-id="34d65-166">If you do not specify enough property names to name all fields, PowerShell automatically assigns numerical property names to any properties that are not named: **P1** , **P2** , etc.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34d65-167">-TemplateContent</span><span class="sxs-lookup"><span data-stu-id="34d65-167">-TemplateContent</span></span>

<span data-ttu-id="34d65-168">Spécifie une expression ou une expression enregistrée en tant que variable, qui décrit les propriétés auxquelles cette applet de commande affecte des chaînes.</span><span class="sxs-lookup"><span data-stu-id="34d65-168">Specifies an expression, or an expression saved as a variable, that describes the properties to which this cmdlet assigns strings.</span></span> <span data-ttu-id="34d65-169">La syntaxe d’une spécification de champ de modèle est la suivante : `{[optional-typecast]<name>:<example-value>}` .</span><span class="sxs-lookup"><span data-stu-id="34d65-169">The syntax of a template field specification is the following: `{[optional-typecast]<name>:<example-value>}`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34d65-170">-TemplateFile</span><span class="sxs-lookup"><span data-stu-id="34d65-170">-TemplateFile</span></span>

<span data-ttu-id="34d65-171">Spécifie un fichier, sous la forme d’un tableau, qui contient un modèle pour l’analyse souhaitée de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="34d65-171">Specifies a file, as an array, that contains a template for the desired parsing of the string.</span></span>
<span data-ttu-id="34d65-172">Dans le fichier de modèle, les propriétés et leurs valeurs sont placées entre crochets, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="34d65-172">In the template file, properties and their values are enclosed in brackets, as shown below.</span></span>
<span data-ttu-id="34d65-173">Si une propriété, telle que la propriété **nom** et les autres propriétés qui lui sont associées, apparaît plusieurs fois, vous pouvez ajouter un astérisque ( `*` ) pour indiquer que cela génère plusieurs enregistrements.</span><span class="sxs-lookup"><span data-stu-id="34d65-173">If a property, such as the **Name** property and its associated other properties, appears multiple times, you can add an asterisk (`*`) to indicate that this results in multiple records.</span></span> <span data-ttu-id="34d65-174">Cela évite l’extraction de plusieurs propriétés dans un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="34d65-174">This avoids extracting multiple properties into a single record.</span></span>

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34d65-175">-UpdateTemplate</span><span class="sxs-lookup"><span data-stu-id="34d65-175">-UpdateTemplate</span></span>

<span data-ttu-id="34d65-176">Indique que cette applet de commande enregistre les résultats d’un algorithme d’apprentissage dans un commentaire dans le fichier de modèle.</span><span class="sxs-lookup"><span data-stu-id="34d65-176">Indicates that this cmdlet saves the results of a learning algorithm into a comment in the template file.</span></span>
<span data-ttu-id="34d65-177">Le processus d’apprentissage de l’algorithme est ainsi plus rapide.</span><span class="sxs-lookup"><span data-stu-id="34d65-177">This makes the algorithm learning process faster.</span></span>
<span data-ttu-id="34d65-178">Pour utiliser ce paramètre, vous devez également spécifier un fichier de modèle avec le paramètre **TemplateFile** .</span><span class="sxs-lookup"><span data-stu-id="34d65-178">To use this parameter, you must also specify a template file with the **TemplateFile** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34d65-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34d65-179">CommonParameters</span></span>

<span data-ttu-id="34d65-180">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="34d65-180">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="34d65-181">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="34d65-181">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="34d65-182">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="34d65-182">INPUTS</span></span>

### <span data-ttu-id="34d65-183">System.String</span><span class="sxs-lookup"><span data-stu-id="34d65-183">System.String</span></span>

## <span data-ttu-id="34d65-184">SORTIES</span><span class="sxs-lookup"><span data-stu-id="34d65-184">OUTPUTS</span></span>

## <span data-ttu-id="34d65-185">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="34d65-185">NOTES</span></span>

## <span data-ttu-id="34d65-186">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="34d65-186">RELATED LINKS</span></span>

[<span data-ttu-id="34d65-187">ConvertFrom-String : analyse de texte basée sur des exemples</span><span class="sxs-lookup"><span data-stu-id="34d65-187">ConvertFrom-String: Example-based text parsing</span></span>](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[<span data-ttu-id="34d65-188">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="34d65-188">ConvertFrom-StringData</span></span>](ConvertFrom-StringData.md)

[<span data-ttu-id="34d65-189">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="34d65-189">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="34d65-190">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="34d65-190">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
