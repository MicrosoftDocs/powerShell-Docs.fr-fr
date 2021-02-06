---
description: Explique les sections de données, qui isolent les chaînes de texte et d’autres données en lecture seule de la logique de script.
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: 1f2a0bae0721bc9adf5b3ba92d5be32d21306a46
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "99596523"
---
# <a name="about-data-sections"></a><span data-ttu-id="19da2-103">À propos des sections de données</span><span class="sxs-lookup"><span data-stu-id="19da2-103">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="19da2-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="19da2-104">Short Description</span></span>
<span data-ttu-id="19da2-105">Explique les sections de données, qui isolent les chaînes de texte et d’autres données en lecture seule de la logique de script.</span><span class="sxs-lookup"><span data-stu-id="19da2-105">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="19da2-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="19da2-106">Long Description</span></span>

<span data-ttu-id="19da2-107">Les scripts conçus pour PowerShell peuvent avoir une ou plusieurs sections de données qui contiennent uniquement des données.</span><span class="sxs-lookup"><span data-stu-id="19da2-107">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="19da2-108">Vous pouvez inclure une ou plusieurs sections de données dans n’importe quel script, fonction ou fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="19da2-108">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="19da2-109">Le contenu de la section de données est limité à un sous-ensemble spécifié du langage de script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19da2-109">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="19da2-110">La séparation des données de la logique du code facilite l’identification et la gestion de la logique et des données.</span><span class="sxs-lookup"><span data-stu-id="19da2-110">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="19da2-111">Elle vous permet d’avoir des fichiers de ressources de chaîne distincts pour le texte, tels que des messages d’erreur et des chaînes d’aide.</span><span class="sxs-lookup"><span data-stu-id="19da2-111">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="19da2-112">Il isole également la logique du code, ce qui facilite les tests de sécurité et de validation.</span><span class="sxs-lookup"><span data-stu-id="19da2-112">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="19da2-113">Dans PowerShell, la section des données est utilisée pour prendre en charge l’internationalisation des scripts.</span><span class="sxs-lookup"><span data-stu-id="19da2-113">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="19da2-114">Vous pouvez utiliser les sections de données pour faciliter l’isolation, la localisation et le traitement des chaînes qui seront traduites dans de nombreuses langues d’interface utilisateur (IU).</span><span class="sxs-lookup"><span data-stu-id="19da2-114">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="19da2-115">La section Data est une fonctionnalité PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="19da2-115">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="19da2-116">Les scripts avec des sections de données ne s’exécuteront pas dans PowerShell 1,0 sans révision.</span><span class="sxs-lookup"><span data-stu-id="19da2-116">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="19da2-117">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19da2-117">Syntax</span></span>

<span data-ttu-id="19da2-118">La syntaxe d’une section de données est la suivante :</span><span class="sxs-lookup"><span data-stu-id="19da2-118">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="19da2-119">Le mot clé Data est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="19da2-119">The Data keyword is required.</span></span> <span data-ttu-id="19da2-120">Il ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="19da2-120">It is not case-sensitive.</span></span> <span data-ttu-id="19da2-121">Le contenu autorisé est limité aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="19da2-121">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="19da2-122">Tous les opérateurs PowerShell, sauf `-match`</span><span class="sxs-lookup"><span data-stu-id="19da2-122">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="19da2-123">`If``Else`instructions, et `ElseIf`</span><span class="sxs-lookup"><span data-stu-id="19da2-123">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="19da2-124">Les variables automatiques suivantes : `$PsCulture` , `$PsUICulture` , `$True` , `$False` et `$Null`</span><span class="sxs-lookup"><span data-stu-id="19da2-124">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="19da2-125">Commentaires</span><span class="sxs-lookup"><span data-stu-id="19da2-125">Comments</span></span>
- <span data-ttu-id="19da2-126">Pipelines</span><span class="sxs-lookup"><span data-stu-id="19da2-126">Pipelines</span></span>
- <span data-ttu-id="19da2-127">Instructions séparées par des points-virgules ( `;` )</span><span class="sxs-lookup"><span data-stu-id="19da2-127">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="19da2-128">Les littéraux, tels que les suivants :</span><span class="sxs-lookup"><span data-stu-id="19da2-128">Literals, such as the following:</span></span>

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- <span data-ttu-id="19da2-129">Applets de commande autorisées dans une section de données.</span><span class="sxs-lookup"><span data-stu-id="19da2-129">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="19da2-130">Par défaut, seule l' `ConvertFrom-StringData` applet de commande est autorisée.</span><span class="sxs-lookup"><span data-stu-id="19da2-130">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="19da2-131">Les applets de commande que vous autorisez dans une section de données à l’aide du `-SupportedCommand` paramètre.</span><span class="sxs-lookup"><span data-stu-id="19da2-131">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="19da2-132">Quand vous utilisez l' `ConvertFrom-StringData` applet de commande dans une section de données, vous pouvez encadrer les paires clé-valeur dans des chaînes à guillemet simple ou entre guillemets ou dans des chaînes à guillemet simple ou à deux guillemets.</span><span class="sxs-lookup"><span data-stu-id="19da2-132">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="19da2-133">Toutefois, les chaînes qui contiennent des variables et des sous-expressions doivent être placées entre des chaînes entre guillemets simples ou des chaînes ici à guillemets simples pour que les variables ne soient pas développées et que les sous-expressions ne soient pas exécutables.</span><span class="sxs-lookup"><span data-stu-id="19da2-133">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="19da2-134">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="19da2-134">-SupportedCommand</span></span>

<span data-ttu-id="19da2-135">Le `-SupportedCommand` paramètre vous permet d’indiquer qu’une applet de commande ou une fonction génère uniquement des données.</span><span class="sxs-lookup"><span data-stu-id="19da2-135">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="19da2-136">Il est conçu pour permettre aux utilisateurs d’inclure des applets de commande et des fonctions dans une section de données qu’ils ont écrites ou testées.</span><span class="sxs-lookup"><span data-stu-id="19da2-136">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="19da2-137">La valeur de `-SupportedCommand` est une liste séparée par des virgules d’un ou plusieurs noms d’applet de commande ou de fonction.</span><span class="sxs-lookup"><span data-stu-id="19da2-137">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="19da2-138">Par exemple, la section de données suivante comprend une applet de commande écrite par l’utilisateur, `Format-Xml` , qui met en forme les données d’un fichier XML :</span><span class="sxs-lookup"><span data-stu-id="19da2-138">For example, the following data section includes a user-written cmdlet, `Format-Xml`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="19da2-139">Utilisation d’une section de données</span><span class="sxs-lookup"><span data-stu-id="19da2-139">Using a Data Section</span></span>

<span data-ttu-id="19da2-140">Pour utiliser le contenu d’une section de données, affectez-la à une variable et utilisez la notation de variable pour accéder au contenu.</span><span class="sxs-lookup"><span data-stu-id="19da2-140">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="19da2-141">Par exemple, la section de données suivante contient une `ConvertFrom-StringData` commande qui convertit la chaîne here en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="19da2-141">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="19da2-142">La table de hachage est assignée à la `$TextMsgs` variable.</span><span class="sxs-lookup"><span data-stu-id="19da2-142">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="19da2-143">La `$TextMsgs` variable ne fait pas partie de la section de données.</span><span class="sxs-lookup"><span data-stu-id="19da2-143">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="19da2-144">Pour accéder aux clés et aux valeurs de la table de hachage dans `$TextMsgs` , utilisez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="19da2-144">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="19da2-145">Vous pouvez également placer le nom de la variable dans la définition de la section de données.</span><span class="sxs-lookup"><span data-stu-id="19da2-145">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="19da2-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="19da2-146">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="19da2-147">Le résultat est le même que dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="19da2-147">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="19da2-148">Exemples</span><span class="sxs-lookup"><span data-stu-id="19da2-148">Examples</span></span>

<span data-ttu-id="19da2-149">Chaînes de données simples.</span><span class="sxs-lookup"><span data-stu-id="19da2-149">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="19da2-150">Chaînes qui incluent des variables autorisées.</span><span class="sxs-lookup"><span data-stu-id="19da2-150">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="19da2-151">Chaîne « here » à guillemet simple qui utilise l' `ConvertFrom-StringData` applet de commande :</span><span class="sxs-lookup"><span data-stu-id="19da2-151">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="19da2-152">Chaîne « here » à deux guillemets qui utilise l’applet de commande `ConvertFrom-StringData` :</span><span class="sxs-lookup"><span data-stu-id="19da2-152">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="19da2-153">Une section de données qui comprend une applet de commande écrite par l’utilisateur qui génère des données :</span><span class="sxs-lookup"><span data-stu-id="19da2-153">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="19da2-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19da2-154">See Also</span></span>

[<span data-ttu-id="19da2-155">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="19da2-155">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="19da2-156">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="19da2-156">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="19da2-157">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="19da2-157">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="19da2-158">about_If</span><span class="sxs-lookup"><span data-stu-id="19da2-158">about_If</span></span>](about_If.md)

[<span data-ttu-id="19da2-159">about_Operators</span><span class="sxs-lookup"><span data-stu-id="19da2-159">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="19da2-160">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="19da2-160">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="19da2-161">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="19da2-161">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="19da2-162">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="19da2-162">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="19da2-163">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="19da2-163">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

