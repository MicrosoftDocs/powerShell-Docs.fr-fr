---
description: Décrit les fonctionnalités d’internationalisation de script qui permettent aux scripts d’afficher facilement des messages et des instructions pour les utilisateurs dans leur langue d’interface utilisateur.
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 283ea6788e76b481c912fc5672350efd2e8bafaa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598802"
---
# <a name="about-script-internationalization"></a><span data-ttu-id="cce72-103">À propos de l’internationalisation des scripts</span><span class="sxs-lookup"><span data-stu-id="cce72-103">About Script Internationalization</span></span>

## <a name="short-description"></a><span data-ttu-id="cce72-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="cce72-104">Short Description</span></span>
<span data-ttu-id="cce72-105">Décrit les fonctionnalités d’internationalisation de script qui permettent aux scripts d’afficher facilement des messages et des instructions pour les utilisateurs dans leur langue d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cce72-105">Describes the script internationalization features that make it easy for scripts to display messages and instructions to users in their user interface (UI) language.</span></span>

## <a name="long-description"></a><span data-ttu-id="cce72-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="cce72-106">Long Description</span></span>

<span data-ttu-id="cce72-107">Les fonctionnalités d’internationalisation des scripts PowerShell vous permettent de mieux servir les utilisateurs dans le monde entier en affichant l’aide et les messages utilisateur dans la langue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cce72-107">The PowerShell script internationalization features allow you to better serve users throughout the world by displaying help and user messages in the user's language.</span></span>

<span data-ttu-id="cce72-108">Les fonctionnalités d’internationalisation de script interrogent la culture d’interface utilisateur du système d’exploitation lors de l’exécution, importent les chaînes de texte traduites appropriées et les affichent à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cce72-108">The script internationalization features query the UI culture of the operating system during execution, import the appropriate translated text strings, and display them to the user.</span></span> <span data-ttu-id="cce72-109">La section Data vous permet de stocker des chaînes de texte séparées du code afin qu’elles soient facilement identifiées et extraites.</span><span class="sxs-lookup"><span data-stu-id="cce72-109">The Data section lets you store text strings separate from code so they are easily identified and extracted.</span></span> <span data-ttu-id="cce72-110">Une nouvelle applet de commande `ConvertFrom-StringData` convertit les chaînes de texte en tables de hachage de type dictionnaire pour faciliter la traduction.</span><span class="sxs-lookup"><span data-stu-id="cce72-110">A new cmdlet, `ConvertFrom-StringData`, converts text strings into dictionary-like hash tables to facilitate translation.</span></span>

<span data-ttu-id="cce72-111">Pour prendre en charge le texte d’aide internationale, PowerShell comprend les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="cce72-111">To support international Help text, PowerShell includes the following features:</span></span>

- <span data-ttu-id="cce72-112">Section de données qui sépare les chaînes de texte des instructions de code.</span><span class="sxs-lookup"><span data-stu-id="cce72-112">A Data section that separates text strings from code instructions.</span></span> <span data-ttu-id="cce72-113">Pour plus d’informations sur la section des données, consultez [about_Data_Sections](about_Data_Sections.md).</span><span class="sxs-lookup"><span data-stu-id="cce72-113">For more information about the Data section, see [about_Data_Sections](about_Data_Sections.md).</span></span>

- <span data-ttu-id="cce72-114">Nouvelles variables automatiques, `$PSCulture` et `$PSUICulture` .</span><span class="sxs-lookup"><span data-stu-id="cce72-114">New automatic variables, `$PSCulture` and `$PSUICulture`.</span></span> <span data-ttu-id="cce72-115">`$PSCulture` stocke le nom de la langue de l’interface utilisateur utilisée sur le système pour les éléments tels que la date, l’heure et la devise.</span><span class="sxs-lookup"><span data-stu-id="cce72-115">`$PSCulture` stores the name of the UI language used on the system for elements such as the date, time, and currency.</span></span> <span data-ttu-id="cce72-116">La `$PSUICulture` variable stocke le nom de la langue de l’interface utilisateur utilisée sur le système pour les éléments d’interface utilisateur tels que les menus et les chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="cce72-116">The `$PSUICulture` variable stores the name of the UI language used on the system for user interface elements such as menus and text strings.</span></span>

- <span data-ttu-id="cce72-117">Une applet de commande, `ConvertFrom-StringData` , qui convertit les chaînes de texte en tables de hachage de type dictionnaire pour faciliter la traduction.</span><span class="sxs-lookup"><span data-stu-id="cce72-117">A cmdlet, `ConvertFrom-StringData`, that converts text strings into dictionary-like hash tables to facilitate translation.</span></span> <span data-ttu-id="cce72-118">Pour plus d’informations, consultez [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span><span class="sxs-lookup"><span data-stu-id="cce72-118">For more information, see [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span></span>

- <span data-ttu-id="cce72-119">Nouveau type de fichier, `.psd1` , qui stocke les chaînes de texte traduites.</span><span class="sxs-lookup"><span data-stu-id="cce72-119">A new file type, `.psd1`, that stores translated text strings.</span></span> <span data-ttu-id="cce72-120">Les `.psd1` fichiers sont stockés dans des sous-répertoires spécifiques à la langue du répertoire du script.</span><span class="sxs-lookup"><span data-stu-id="cce72-120">The `.psd1` files are stored in language-specific subdirectories of the script directory.</span></span>

- <span data-ttu-id="cce72-121">Une applet de commande, `Import-LocalizedData` , qui importe les chaînes de texte traduites pour un langage spécifié dans un script au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cce72-121">A cmdlet, `Import-LocalizedData`, that imports translated text strings for a specified language into a script at runtime.</span></span> <span data-ttu-id="cce72-122">Cette applet de commande reconnaît et importe des chaînes dans n’importe quel langage pris en charge par Windows.</span><span class="sxs-lookup"><span data-stu-id="cce72-122">This cmdlet recognizes and imports strings in any Windows-supported language.</span></span> <span data-ttu-id="cce72-123">Pour plus d’informations [, consultez Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span><span class="sxs-lookup"><span data-stu-id="cce72-123">For more information see [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span></span>

### <a name="the-data-section-storing-default-strings"></a><span data-ttu-id="cce72-124">La section Data : stockage de chaînes par défaut</span><span class="sxs-lookup"><span data-stu-id="cce72-124">The Data Section: Storing Default Strings</span></span>

<span data-ttu-id="cce72-125">Utilisez une section de données dans le script pour stocker les chaînes de texte dans la langue par défaut.</span><span class="sxs-lookup"><span data-stu-id="cce72-125">Use a Data section in the script to store the text strings in the default language.</span></span> <span data-ttu-id="cce72-126">Réorganisez les chaînes dans des paires clé/valeur dans une chaîne ici.</span><span class="sxs-lookup"><span data-stu-id="cce72-126">Arrange the strings in key/value pairs in a here-string.</span></span> <span data-ttu-id="cce72-127">Chaque paire clé/valeur doit se trouver sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="cce72-127">Each key/value pair must be on a separate line.</span></span> <span data-ttu-id="cce72-128">Si vous incluez des commentaires, les commentaires doivent se trouver sur des lignes distinctes.</span><span class="sxs-lookup"><span data-stu-id="cce72-128">If you include comments, the comments must be on separate lines.</span></span>

<span data-ttu-id="cce72-129">L' `ConvertFrom-StringData` applet de commande convertit les paires clé/valeur dans la chaîne here en une table de hachage de type dictionnaire qui est stockée dans la valeur de la variable de la section de données.</span><span class="sxs-lookup"><span data-stu-id="cce72-129">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a dictionary-like hash table that is stored in the value of the Data section variable.</span></span>

<span data-ttu-id="cce72-130">Dans l’exemple suivant, la section de données du `World.ps1` script comprend le jeu d’États de English-United (en-US) des messages d’invite pour un script.</span><span class="sxs-lookup"><span data-stu-id="cce72-130">In the following example, the Data section of the `World.ps1` script includes the English-United States (en-US) set of prompt messages for a script.</span></span> <span data-ttu-id="cce72-131">L' `ConvertFrom-StringData` applet de commande convertit les chaînes en une table de hachage et les stocke dans la `$msgtable` variable.</span><span class="sxs-lookup"><span data-stu-id="cce72-131">The `ConvertFrom-StringData` cmdlet converts the strings into a hash table and stores them in the `$msgtable` variable.</span></span>

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

<span data-ttu-id="cce72-132">Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="cce72-132">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

### <a name="psd1-files-storing-translated-strings"></a><span data-ttu-id="cce72-133">Fichiers PSD1 : stockage de chaînes traduites</span><span class="sxs-lookup"><span data-stu-id="cce72-133">PSD1 Files: Storing Translated Strings</span></span>

<span data-ttu-id="cce72-134">Enregistrez les messages de script pour chaque langue de l’interface utilisateur dans des fichiers texte distincts portant le même nom que le script et l' `.psd1` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="cce72-134">Save the script messages for each UI language in separate text files with the same name as the script and the `.psd1` file name extension.</span></span> <span data-ttu-id="cce72-135">Stockez les fichiers dans les sous-répertoires du répertoire de script avec des noms de cultures au format suivant :</span><span class="sxs-lookup"><span data-stu-id="cce72-135">Store the files in subdirectories of the script directory with names of cultures in the following format:</span></span>

`<language>-<region>`

<span data-ttu-id="cce72-136">Exemples : de-DE, ar-SA et zh-Hans</span><span class="sxs-lookup"><span data-stu-id="cce72-136">Examples: de-DE, ar-SA, and zh-Hans</span></span>

<span data-ttu-id="cce72-137">Par exemple, si le `World.ps1` script est stocké dans le `C:\Scripts` répertoire, vous devez créer une structure de répertoires de fichiers qui ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="cce72-137">For example, if the `World.ps1` script is stored in the `C:\Scripts` directory, you would create a file directory structure that resembles the following:</span></span>

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

<span data-ttu-id="cce72-138">Le `World.psd1` fichier dans le sous-répertoire du répertoire de script peut inclure l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="cce72-138">The `World.psd1` file in the de-DE subdirectory of the script directory might include the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

<span data-ttu-id="cce72-139">De même, le `World.psd1` fichier dans le sous-répertoire ar-sa du répertoire de script peut inclure l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="cce72-139">Similarly, the `World.psd1` file in the ar-SA subdirectory of the script directory might includes the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a><span data-ttu-id="cce72-140">Import-LocalizedData : récupération dynamique des chaînes traduites</span><span class="sxs-lookup"><span data-stu-id="cce72-140">Import-LocalizedData: Dynamic Retrieval of Translated Strings</span></span>

<span data-ttu-id="cce72-141">Pour récupérer les chaînes dans la langue de l’interface utilisateur de l’utilisateur actuel, utilisez l’applet de commande `Import-LocalizedData` .</span><span class="sxs-lookup"><span data-stu-id="cce72-141">To retrieve the strings in the UI language of the current user, use the `Import-LocalizedData` cmdlet.</span></span>

<span data-ttu-id="cce72-142">`Import-LocalizedData` recherche la valeur de la `$PSUICulture` variable automatique et importe le contenu des `<script-name>.psd1` fichiers dans le sous-répertoire qui correspond à la `$PSUICulture` valeur.</span><span class="sxs-lookup"><span data-stu-id="cce72-142">`Import-LocalizedData` finds the value of the `$PSUICulture` automatic variable and imports the content of the `<script-name>.psd1` files in the subdirectory that matches the `$PSUICulture` value.</span></span> <span data-ttu-id="cce72-143">Ensuite, il enregistre le contenu importé dans la variable spécifiée par la valeur du paramètre **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="cce72-143">Then, it saves the imported content in the variable specified by the value of the **BindingVariable** parameter.</span></span>

```powershell
Import-LocalizedData -BindingVariable msgTable
```

<span data-ttu-id="cce72-144">Par exemple, si la `Import-LocalizedData` commande apparaît dans le `C:\Scripts\World.ps1` script et que la valeur de `$PSUICulture` est « AR-sa », `Import-LocalizedData` recherche le fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="cce72-144">For example, if the `Import-LocalizedData` command appears in the `C:\Scripts\World.ps1` script and the value of `$PSUICulture` is "ar-SA", `Import-LocalizedData` finds the following file:</span></span>

`C:\Scripts\ar-SA\World.psd1`

<span data-ttu-id="cce72-145">Ensuite, il importe les chaînes de texte arabe du fichier dans la `$msgTable` variable, en remplaçant les chaînes par défaut qui peuvent être définies dans la section de données du `World.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="cce72-145">Then, it imports the Arabic text strings from the file into the `$msgTable` variable, replacing any default strings that might be defined in the Data section of the `World.ps1` script.</span></span>

<span data-ttu-id="cce72-146">Par conséquent, lorsque le script utilise la `$msgTable` variable pour afficher des messages utilisateur, les messages s’affichent en arabe.</span><span class="sxs-lookup"><span data-stu-id="cce72-146">As a result, when the script uses the `$msgTable` variable to display user messages, the messages are displayed in Arabic.</span></span>

<span data-ttu-id="cce72-147">Par exemple, le script suivant affiche le message « Veuillez entrer votre nom d’utilisateur » en arabe :</span><span class="sxs-lookup"><span data-stu-id="cce72-147">For example, the following script displays the "Please enter your user name" message in Arabic:</span></span>

```powershell
if (!($username)) { $msgTable.promptMsg }
```

<span data-ttu-id="cce72-148">Si `Import-LocalizedData` ne peut pas trouver un `.psd1` fichier qui correspond à la valeur de `$PSUIculture` , la valeur de `$msgTable` n’est pas remplacée et l’appel à `$msgTable.promptMsg` affiche les chaînes en-US de secours.</span><span class="sxs-lookup"><span data-stu-id="cce72-148">If `Import-LocalizedData` cannot find a `.psd1` file that matches the value of `$PSUIculture`, the value of `$msgTable` is not replaced, and the call to `$msgTable.promptMsg` displays the fallback en-US strings.</span></span>

## <a name="examples"></a><span data-ttu-id="cce72-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="cce72-149">Examples</span></span>

<span data-ttu-id="cce72-150">Cet exemple montre comment les fonctionnalités d’internationalisation de script sont utilisées dans un script pour afficher un jour de la semaine aux utilisateurs dans la langue définie sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cce72-150">This example shows how the script internationalization features are used in a script to display a day of the week to users in the language that is set on the computer.</span></span>

<span data-ttu-id="cce72-151">Voici la liste complète des Sample1.ps1 fichier de script.</span><span class="sxs-lookup"><span data-stu-id="cce72-151">The following is a complete listing of the Sample1.ps1 script file.</span></span>

<span data-ttu-id="cce72-152">Le script commence par une section de données nommée Day ($Day) qui contient une `ConvertFrom-StringData` commande.</span><span class="sxs-lookup"><span data-stu-id="cce72-152">The script begins with a Data section named Day ($Day) that contains a `ConvertFrom-StringData` command.</span></span> <span data-ttu-id="cce72-153">L’expression soumise à `ConvertFrom-StringData` est une chaîne « here » qui contient les noms de jours dans la culture d’interface utilisateur par défaut, en-US, dans les paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="cce72-153">The expression submitted to `ConvertFrom-StringData` is a here-string that contains the day names in the default UI culture, en-US, in key/value pairs.</span></span> <span data-ttu-id="cce72-154">L' `ConvertFrom-StringData` applet de commande convertit les paires clé/valeur dans la chaîne here en une table de hachage, puis l’enregistre dans la valeur de la `$Day` variable.</span><span class="sxs-lookup"><span data-stu-id="cce72-154">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a hash table and then saves it in the value of the `$Day` variable.</span></span>

<span data-ttu-id="cce72-155">La `Import-LocalizedData` commande importe le contenu du `.psd1` fichier dans le répertoire qui correspond à la valeur de la `$PSUICulture` variable automatique, puis l’enregistre dans la `$Day` variable, en remplaçant les valeurs de `$Day` qui sont définies dans la section de données.</span><span class="sxs-lookup"><span data-stu-id="cce72-155">The `Import-LocalizedData` command imports the contents of the `.psd1` file in the directory that matches the value of the `$PSUICulture` automatic variable and then saves it in the `$Day` variable, replacing the values of `$Day` that are defined in the Data section.</span></span>

<span data-ttu-id="cce72-156">Les commandes restantes chargent les chaînes dans un tableau et les affichent.</span><span class="sxs-lookup"><span data-stu-id="cce72-156">The remaining commands load the strings into an array and display them.</span></span>

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

<span data-ttu-id="cce72-157">Les `.psd1` fichiers qui prennent en charge le script sont enregistrés dans des sous-répertoires du répertoire de script dont les noms correspondent aux `$PSUICulture` valeurs.</span><span class="sxs-lookup"><span data-stu-id="cce72-157">The `.psd1` files that support the script are saved in subdirectories of the script directory with names that match the `$PSUICulture` values.</span></span>

<span data-ttu-id="cce72-158">Voici une liste complète des éléments suivants `.\de-DE\sample1.psd1` :</span><span class="sxs-lookup"><span data-stu-id="cce72-158">The following is a complete listing of `.\de-DE\sample1.psd1`:</span></span>

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

<span data-ttu-id="cce72-159">Par conséquent, lorsque vous exécutez Sample.ps1 sur un système sur lequel la valeur de `$PSUICulture` est de-de, la sortie du script est la suivante :</span><span class="sxs-lookup"><span data-stu-id="cce72-159">As a result, when you run Sample.ps1 on a system on which the value of `$PSUICulture` is de-DE, the output of the script is:</span></span>

```Output
Heute ist Freitag
```

## <a name="see-also"></a><span data-ttu-id="cce72-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cce72-160">See also</span></span>

- [<span data-ttu-id="cce72-161">about_Data_Sections</span><span class="sxs-lookup"><span data-stu-id="cce72-161">about_Data_Sections</span></span>](about_Data_Sections.md)
- [<span data-ttu-id="cce72-162">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="cce72-162">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="cce72-163">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="cce72-163">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="cce72-164">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="cce72-164">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="cce72-165">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="cce72-165">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [<span data-ttu-id="cce72-166">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="cce72-166">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

