---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: f737c8025f9fda3611a44177bd19e928f596d0aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597747"
---
# <span data-ttu-id="4b20a-102">Join-String</span><span class="sxs-lookup"><span data-stu-id="4b20a-102">Join-String</span></span>

## <span data-ttu-id="4b20a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4b20a-103">SYNOPSIS</span></span>
<span data-ttu-id="4b20a-104">Combine des objets du pipeline en une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="4b20a-104">Combines objects from the pipeline into a single string.</span></span>

## <span data-ttu-id="4b20a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4b20a-105">SYNTAX</span></span>

### <span data-ttu-id="4b20a-106">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4b20a-106">Default (Default)</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### <span data-ttu-id="4b20a-107">SingleQuote</span><span class="sxs-lookup"><span data-stu-id="4b20a-107">SingleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="4b20a-108">DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="4b20a-108">DoubleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="4b20a-109">Format</span><span class="sxs-lookup"><span data-stu-id="4b20a-109">Format</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="4b20a-110">Description</span><span class="sxs-lookup"><span data-stu-id="4b20a-110">DESCRIPTION</span></span>

<span data-ttu-id="4b20a-111">L' `Join-String` applet de commande joint, ou combine, le texte des objets de pipeline dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="4b20a-111">The `Join-String` cmdlet joins, or combines, text from pipeline objects into a single string.</span></span>

<span data-ttu-id="4b20a-112">Si aucun paramètre n’est spécifié, les objets de pipeline sont convertis en une chaîne et joints au séparateur par défaut `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="4b20a-112">If no parameters are specified, the pipeline objects are converted to a string and joined with the default separator `$OFS`.</span></span>

<span data-ttu-id="4b20a-113">En spécifiant un nom de propriété, la valeur de la propriété est convertie en une chaîne et jointe à une chaîne.</span><span class="sxs-lookup"><span data-stu-id="4b20a-113">By specifying a property name, the property's value is converted to a string and joined into a string.</span></span>

<span data-ttu-id="4b20a-114">Au lieu d’un nom de propriété, un bloc de script peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="4b20a-114">Instead of a property name, a script block can be used.</span></span> <span data-ttu-id="4b20a-115">Le résultat du bloc de script est converti en chaîne avant d’être joint pour former le résultat.</span><span class="sxs-lookup"><span data-stu-id="4b20a-115">The script block's result is converted to a string before it's joined to form the result.</span></span> <span data-ttu-id="4b20a-116">Il peut soit combiner le texte de la propriété d’un objet, soit le résultat de l’objet qui a été converti en chaîne.</span><span class="sxs-lookup"><span data-stu-id="4b20a-116">It can either combine the text of an object's property or the result of the object that was converted to a string.</span></span>

<span data-ttu-id="4b20a-117">Cette applet de commande a été introduite dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="4b20a-117">This cmdlet was introduced in PowerShell 6.2.</span></span>

## <span data-ttu-id="4b20a-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4b20a-118">EXAMPLES</span></span>

### <span data-ttu-id="4b20a-119">Exemple 1 : joindre des noms de répertoires</span><span class="sxs-lookup"><span data-stu-id="4b20a-119">Example 1: Join directory names</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="4b20a-120">Cet exemple joint des noms de répertoires, encapsule la sortie entre des guillemets doubles et sépare les noms de répertoires par une virgule et un espace ( `, ` ).</span><span class="sxs-lookup"><span data-stu-id="4b20a-120">This example joins directory names, wraps the output in double-quotes, and separates the directory names with a comma and space (`, `).</span></span> <span data-ttu-id="4b20a-121">La sortie est un objet String.</span><span class="sxs-lookup"><span data-stu-id="4b20a-121">The output is a string object.</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

<span data-ttu-id="4b20a-122">`Get-ChildItem` utilise le paramètre **Directory** pour obtenir tous les noms de répertoires du `C:\` lecteur.</span><span class="sxs-lookup"><span data-stu-id="4b20a-122">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="4b20a-123">Les objets sont envoyés dans le pipeline à `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="4b20a-123">The objects are sent down the pipeline to `Join-String`.</span></span> <span data-ttu-id="4b20a-124">Le paramètre **Property** spécifie les noms de répertoire.</span><span class="sxs-lookup"><span data-stu-id="4b20a-124">The **Property** parameter specifies the directory names.</span></span> <span data-ttu-id="4b20a-125">Le paramètre **DoubleQuote** encapsule les noms de répertoires avec des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="4b20a-125">The **DoubleQuote** parameter wraps the directory names with double-quote marks.</span></span>
<span data-ttu-id="4b20a-126">Le paramètre **separator** spécifie d’utiliser une virgule et un espace ( `, ` ) pour séparer les noms de répertoire.</span><span class="sxs-lookup"><span data-stu-id="4b20a-126">The **Separator** parameter specifies to use a comma and space (`, `) to separate the directory names.</span></span>

<span data-ttu-id="4b20a-127">Les `Get-ChildItem` objets sont **System. IO. DirectoryInfo** et `Join-String` convertissent les objets en **System. String**.</span><span class="sxs-lookup"><span data-stu-id="4b20a-127">The `Get-ChildItem` objects are **System.IO.DirectoryInfo** and `Join-String` converts the objects to **System.String**.</span></span>

### <span data-ttu-id="4b20a-128">Exemple 2 : utiliser une sous-chaîne de propriété pour joindre des noms de répertoire</span><span class="sxs-lookup"><span data-stu-id="4b20a-128">Example 2: Use a property substring to join directory names</span></span>

<span data-ttu-id="4b20a-129">Cet exemple utilise une méthode de sous-chaîne pour obtenir les quatre premières lettres des noms de répertoires, encapsule la sortie en guillemets simples et sépare les noms de répertoires par un point-virgule ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="4b20a-129">This example uses a substring method to get the first four letters of directory names, wraps the output in single-quotes, and separates the directory names with a semicolon (`;`).</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

<span data-ttu-id="4b20a-130">`Get-ChildItem` utilise le paramètre **Directory** pour obtenir tous les noms de répertoires du `C:\` lecteur.</span><span class="sxs-lookup"><span data-stu-id="4b20a-130">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="4b20a-131">Les objets sont envoyés dans le pipeline à `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="4b20a-131">The objects are sent down the pipeline to `Join-String`.</span></span>

<span data-ttu-id="4b20a-132">Le bloc de script de paramètre de **propriété** utilise la variable automatique ( `$_` ) pour spécifier la propriété **Name** de chaque objet SUBSTRING.</span><span class="sxs-lookup"><span data-stu-id="4b20a-132">The **Property** parameter script block uses automatic variable (`$_`) to specify each object's **Name** property substring.</span></span> <span data-ttu-id="4b20a-133">La sous-chaîne obtient les quatre premières lettres de chaque nom de répertoire.</span><span class="sxs-lookup"><span data-stu-id="4b20a-133">The substring gets the first four letters of each directory name.</span></span> <span data-ttu-id="4b20a-134">La sous-chaîne spécifie les positions de début et de fin des caractères.</span><span class="sxs-lookup"><span data-stu-id="4b20a-134">The substring specifies the character start and end positions.</span></span> <span data-ttu-id="4b20a-135">Le paramètre **SingleQuote** encapsule les noms de répertoires avec des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4b20a-135">The **SingleQuote** parameter wraps the directory names with single-quote marks.</span></span> <span data-ttu-id="4b20a-136">Le paramètre **separator** spécifie l’utilisation d’un point-virgule ( `;` ) pour séparer les noms de répertoire.</span><span class="sxs-lookup"><span data-stu-id="4b20a-136">The **Separator** parameter specifies to use a semicolon (`;`) to separate the directory names.</span></span>

<span data-ttu-id="4b20a-137">Pour plus d’informations sur les variables automatiques et les sous-chaînes, consultez [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) et [SUBSTRING](/dotnet/api/system.string.substring).</span><span class="sxs-lookup"><span data-stu-id="4b20a-137">For more information about automatic variables and substrings, see [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) and [Substring](/dotnet/api/system.string.substring).</span></span>

### <span data-ttu-id="4b20a-138">Exemple 3 : afficher la sortie de jointure sur une ligne distincte</span><span class="sxs-lookup"><span data-stu-id="4b20a-138">Example 3: Display join output on a separate line</span></span>

<span data-ttu-id="4b20a-139">Cet exemple joint des noms de service à chaque service sur une ligne distincte et mis en retrait par un onglet.</span><span class="sxs-lookup"><span data-stu-id="4b20a-139">This example joins service names with each service on a separate line and indented by a tab.</span></span>

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

<span data-ttu-id="4b20a-140">`Get-Service` utilise le paramètre **Name** avec pour spécifier les services qui commencent par `se*` .</span><span class="sxs-lookup"><span data-stu-id="4b20a-140">`Get-Service` uses the **Name** parameter with to specify services that begin with `se*`.</span></span> <span data-ttu-id="4b20a-141">L’astérisque ( `*` ) est un caractère générique pour n’importe quel caractère.</span><span class="sxs-lookup"><span data-stu-id="4b20a-141">The asterisk (`*`) is a wildcard for any character.</span></span>

<span data-ttu-id="4b20a-142">Les objets sont envoyés dans le pipeline à `Join-String` qui utilise le paramètre **Property** pour spécifier les noms de service.</span><span class="sxs-lookup"><span data-stu-id="4b20a-142">The objects are sent down the pipeline to `Join-String` that uses the **Property** parameter to specify the service names.</span></span> <span data-ttu-id="4b20a-143">Le paramètre **separator** spécifie trois caractères spéciaux qui représentent un retour chariot ( `` `r `` ), un saut de ligne ( `` `n `` ) et un onglet ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="4b20a-143">The **Separator** parameter specifies three special characters that represent a carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span> <span data-ttu-id="4b20a-144">Le **OutputPrefix** insère une étiquette **services :** avec une nouvelle ligne et un nouvel onglet avant la première ligne de la sortie.</span><span class="sxs-lookup"><span data-stu-id="4b20a-144">The **OutputPrefix** inserts a label **Services:** with a new line and tab before the first line of output.</span></span>

<span data-ttu-id="4b20a-145">Pour plus d’informations sur les caractères spéciaux, consultez [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span><span class="sxs-lookup"><span data-stu-id="4b20a-145">For more information about special characters, see [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span></span>

### <span data-ttu-id="4b20a-146">Exemple 4 : créer une définition de classe à partir d’un objet</span><span class="sxs-lookup"><span data-stu-id="4b20a-146">Example 4: Create a class definition from an object</span></span>

<span data-ttu-id="4b20a-147">Cet exemple génère une définition de classe PowerShell en utilisant un objet existant comme modèle.</span><span class="sxs-lookup"><span data-stu-id="4b20a-147">This example generates a PowerShell class definition using an existing object as a template.</span></span>

<span data-ttu-id="4b20a-148">Cet exemple de code utilise la projection pour réduire la longueur de ligne et améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="4b20a-148">This code sample uses splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="4b20a-149">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="4b20a-149">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## <span data-ttu-id="4b20a-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4b20a-150">PARAMETERS</span></span>

### <span data-ttu-id="4b20a-151">-DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="4b20a-151">-DoubleQuote</span></span>

<span data-ttu-id="4b20a-152">Encapsule la valeur de chaîne de chaque objet de pipeline entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="4b20a-152">Wraps the string value of each pipeline object in double-quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-153">-FormatString</span><span class="sxs-lookup"><span data-stu-id="4b20a-153">-FormatString</span></span>

<span data-ttu-id="4b20a-154">Chaîne de format qui spécifie la façon dont chaque élément doit être mis en forme.</span><span class="sxs-lookup"><span data-stu-id="4b20a-154">A format string that specifies how each item should be formatted.</span></span>

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4b20a-155">-InputObject</span></span>

<span data-ttu-id="4b20a-156">Spécifie le texte à joindre.</span><span class="sxs-lookup"><span data-stu-id="4b20a-156">Specifies the text to be joined.</span></span> <span data-ttu-id="4b20a-157">Entrez une variable qui contient le texte, ou tapez une commande ou une expression qui obtient les objets à joindre aux chaînes.</span><span class="sxs-lookup"><span data-stu-id="4b20a-157">Enter a variable that contains the text, or type a command or expression that gets the objects to join into strings.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-158">-OutputPrefix</span><span class="sxs-lookup"><span data-stu-id="4b20a-158">-OutputPrefix</span></span>

<span data-ttu-id="4b20a-159">Texte inséré avant la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="4b20a-159">Text that's inserted before the output string.</span></span> <span data-ttu-id="4b20a-160">La chaîne peut contenir des caractères spéciaux tels que les retours chariot ( `` `r `` ), les sauts de ligne ( `` `n `` ) et les tabulations ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="4b20a-160">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-161">-OutputSuffix</span><span class="sxs-lookup"><span data-stu-id="4b20a-161">-OutputSuffix</span></span>

<span data-ttu-id="4b20a-162">Texte ajouté à la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="4b20a-162">Text that's appended to the output string.</span></span> <span data-ttu-id="4b20a-163">La chaîne peut contenir des caractères spéciaux tels que les retours chariot ( `` `r `` ), les sauts de ligne ( `` `n `` ) et les tabulations ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="4b20a-163">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-164">-Propriété</span><span class="sxs-lookup"><span data-stu-id="4b20a-164">-Property</span></span>

<span data-ttu-id="4b20a-165">Nom d’une propriété, ou expression de propriété, qui projetera l’objet de pipeline en texte.</span><span class="sxs-lookup"><span data-stu-id="4b20a-165">The name of a property, or a property expression, that will project the pipeline object to text.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-166">-Séparateur</span><span class="sxs-lookup"><span data-stu-id="4b20a-166">-Separator</span></span>

<span data-ttu-id="4b20a-167">Texte ou caractères tels qu’une virgule ou un point-virgule inséré entre le texte de chaque objet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4b20a-167">Text or characters such as a comma or semicolon that's inserted between the text for each pipeline object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-168">-SingleQuote</span><span class="sxs-lookup"><span data-stu-id="4b20a-168">-SingleQuote</span></span>

<span data-ttu-id="4b20a-169">Encapsule la valeur de chaîne de chaque objet de pipeline entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4b20a-169">Wraps the string value of each pipeline object in single quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-170">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="4b20a-170">-UseCulture</span></span>

<span data-ttu-id="4b20a-171">Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément.</span><span class="sxs-lookup"><span data-stu-id="4b20a-171">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="4b20a-172">Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="4b20a-172">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b20a-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b20a-173">CommonParameters</span></span>

<span data-ttu-id="4b20a-174">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4b20a-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b20a-175">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4b20a-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b20a-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4b20a-176">INPUTS</span></span>

### <span data-ttu-id="4b20a-177">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4b20a-177">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="4b20a-178">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4b20a-178">OUTPUTS</span></span>

### <span data-ttu-id="4b20a-179">System.String</span><span class="sxs-lookup"><span data-stu-id="4b20a-179">System.String</span></span>

## <span data-ttu-id="4b20a-180">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4b20a-180">NOTES</span></span>

## <span data-ttu-id="4b20a-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4b20a-181">RELATED LINKS</span></span>

[<span data-ttu-id="4b20a-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4b20a-182">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="4b20a-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="4b20a-183">about_Special_Characters</span></span>](..//microsoft.powershell.core/about/about_special_characters.md)

[<span data-ttu-id="4b20a-184">Sous-chaîne</span><span class="sxs-lookup"><span data-stu-id="4b20a-184">Substring</span></span>](/dotnet/api/system.string.substring)

