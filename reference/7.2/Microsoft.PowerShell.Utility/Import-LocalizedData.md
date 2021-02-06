---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: fa5de857b70ec05d30c42fbf8e51a9411d823018
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595724"
---
# <span data-ttu-id="2e48d-102">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="2e48d-102">Import-LocalizedData</span></span>

## <span data-ttu-id="2e48d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2e48d-103">SYNOPSIS</span></span>
<span data-ttu-id="2e48d-104">Importe les données propres au langage dans les scripts et les fonctions basés sur la culture d'interface utilisateur sélectionnée pour le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="2e48d-104">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="2e48d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2e48d-105">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2e48d-106">Description</span><span class="sxs-lookup"><span data-stu-id="2e48d-106">DESCRIPTION</span></span>

<span data-ttu-id="2e48d-107">L' `Import-LocalizedData` applet de commande récupère dynamiquement les chaînes d’un sous-répertoire dont le nom correspond à la langue de l’interface utilisateur définie pour l’utilisateur actuel du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="2e48d-107">The `Import-LocalizedData` cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span> <span data-ttu-id="2e48d-108">Il est conçu pour permettre aux scripts d'afficher les messages de l'utilisateur dans la langue de l'interface utilisateur sélectionnée par l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2e48d-108">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="2e48d-109">`Import-LocalizedData` importe des données à partir de `.psd1` fichiers dans des sous-répertoires spécifiques au langage du répertoire de script et les enregistre dans une variable locale spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-109">`Import-LocalizedData` imports data from `.psd1` files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span> <span data-ttu-id="2e48d-110">L’applet de commande sélectionne le sous-répertoire et le fichier en fonction de la valeur de la `$PSUICulture` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="2e48d-110">The cmdlet selects the subdirectory and file based on the value of the `$PSUICulture` automatic variable.</span></span> <span data-ttu-id="2e48d-111">Lorsque vous utilisez la variable locale du script pour afficher un message de l'utilisateur, le message s'affiche dans la langue d'interface utilisateur de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e48d-111">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="2e48d-112">Vous pouvez utiliser les paramètres de `Import-LocalizedData` pour spécifier une autre culture d’interface utilisateur, un chemin d’accès et un nom de fichier, pour ajouter des commandes prises en charge et pour supprimer le message d’erreur qui s’affiche si les `.psd1` fichiers sont introuvables.</span><span class="sxs-lookup"><span data-stu-id="2e48d-112">You can use the parameters of `Import-LocalizedData` to specify an alternate UI culture, path, and filename, to add supported commands, and to suppress the error message that appears if the `.psd1` files are not found.</span></span>

<span data-ttu-id="2e48d-113">L' `Import-LocalizedData` applet de commande prend en charge l’initiative de script d’internationalisation introduite dans Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="2e48d-113">The `Import-LocalizedData` cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="2e48d-114">Cette initiative vise à mieux servir les utilisateurs dans le monde entier en permettant aux scripts d'afficher facilement les messages de l'utilisateur dans la langue de l'interface utilisateur de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2e48d-114">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span> <span data-ttu-id="2e48d-115">Pour plus d’informations sur ce sujet et sur le format des `.psd1` fichiers, consultez [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="2e48d-115">For more information about this and about the format of the `.psd1` files, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="2e48d-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2e48d-116">EXAMPLES</span></span>

### <span data-ttu-id="2e48d-117">Exemple 1 : importer des chaînes de texte</span><span class="sxs-lookup"><span data-stu-id="2e48d-117">Example 1: Import text strings</span></span>

<span data-ttu-id="2e48d-118">Cet exemple importe les chaînes de texte dans la `$Messages` variable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-118">This example imports text strings into the `$Messages` variable.</span></span> <span data-ttu-id="2e48d-119">Elle utilise les valeurs par défaut de tous les autres paramètres de l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-119">It uses the default values of all other cmdlet parameters.</span></span>

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="2e48d-120">Si la commande est incluse dans le script Archives.ps1 dans le `C:\Test` répertoire et que la valeur de la `$PsUICulture` variable automatique est zh-CN, `Import-LocalizedData` importe le `Archives.psd1` fichier dans le `C:\test\zh-CN` répertoire dans la `$Messages` variable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-120">If the command is included in the Archives.ps1 script in the `C:\Test` directory, and the value of the `$PsUICulture` automatic variable is zh-CN, `Import-LocalizedData` imports the `Archives.psd1` file in the `C:\test\zh-CN` directory into the `$Messages` variable.</span></span>

### <span data-ttu-id="2e48d-121">Exemple 2 : importer des chaînes de données localisées</span><span class="sxs-lookup"><span data-stu-id="2e48d-121">Example 2: Import localized data strings</span></span>

<span data-ttu-id="2e48d-122">Cet exemple est exécuté sur la ligne de commande et non pas dans un script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-122">This example is run at the command line not in a script.</span></span> <span data-ttu-id="2e48d-123">Elle obtient les chaînes de données localisées du fichier Test.psd1 et les affiche au niveau de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-123">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span> <span data-ttu-id="2e48d-124">Étant donné que la commande n'est pas utilisée dans un script, le paramètre **FileName** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e48d-124">Because the command is not used in a script, the **FileName** parameter is required.</span></span> <span data-ttu-id="2e48d-125">La commande utilise le paramètre **UICulture** pour spécifier la culture en-US.</span><span class="sxs-lookup"><span data-stu-id="2e48d-125">The command uses the **UICulture** parameter to specify the en-US culture.</span></span>

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="2e48d-126">`Import-LocalizedData` retourne une table de hachage qui contient les chaînes de données localisées.</span><span class="sxs-lookup"><span data-stu-id="2e48d-126">`Import-LocalizedData` returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="2e48d-127">Exemple 3 : importer des chaînes de culture d’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="2e48d-127">Example 3: Import UI culture strings</span></span>

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="2e48d-128">Cette commande importe les chaînes de texte dans la `$MsgTbl` variable d’un script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-128">This command imports text strings into the `$MsgTbl` variable of a script.</span></span>

<span data-ttu-id="2e48d-129">Elle utilise le paramètre **UICulture** pour demander à l’applet de commande d’importer des données à partir du `Simple.psd1` fichier dans le `ar-SA` sous-répertoire de `C:\Data\Localized` .</span><span class="sxs-lookup"><span data-stu-id="2e48d-129">It uses the **UICulture** parameter to direct the cmdlet to import data from the `Simple.psd1` file in the `ar-SA` subdirectory of `C:\Data\Localized`.</span></span>

### <span data-ttu-id="2e48d-130">Exemple 4 : importer des données localisées dans un script</span><span class="sxs-lookup"><span data-stu-id="2e48d-130">Example 4: Import localized data into a script</span></span>

<span data-ttu-id="2e48d-131">Cet exemple montre comment utiliser les données localisées dans un script simple.</span><span class="sxs-lookup"><span data-stu-id="2e48d-131">This example shows how to use localized data in a simple script.</span></span>

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="2e48d-132">La première partie de l’exemple illustre le contenu du `Test.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="2e48d-132">The first part of the example shows the contents of the `Test.psd1` file.</span></span> <span data-ttu-id="2e48d-133">Elle contient une `ConvertFrom-StringData` commande qui convertit une série de chaînes de texte nommées en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="2e48d-133">It contains a `ConvertFrom-StringData` command that converts a series of named text strings into a hash table.</span></span> <span data-ttu-id="2e48d-134">Le `Test.psd1` fichier se trouve dans le sous-répertoire en-US du `C:\Test` répertoire qui contient le script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-134">The `Test.psd1` file is located in the en-US subdirectory of the `C:\Test` directory that contains the script.</span></span>

<span data-ttu-id="2e48d-135">La deuxième partie de l’exemple illustre le contenu du `Test.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-135">The second part of the example shows the contents of the `Test.ps1` script.</span></span> <span data-ttu-id="2e48d-136">Elle contient une `Import-LocalizedData` commande qui importe les données à partir du `.psd1` fichier correspondant dans la `$Messages` variable et une `Write-Host` commande qui écrit l’un des messages de la variable dans le `$Messages` programme hôte.</span><span class="sxs-lookup"><span data-stu-id="2e48d-136">It contains an `Import-LocalizedData` command that imports the data from the matching `.psd1` file into the `$Messages` variable and a `Write-Host` command that writes one of the messages in the `$Messages` variable to the host program.</span></span>

<span data-ttu-id="2e48d-137">La dernière partie de l'exemple exécute le script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-137">The last part of the example runs the script.</span></span> <span data-ttu-id="2e48d-138">La sortie montre qu'il affiche le message correct de l'utilisateur dans la langue de l'interface utilisateur définie pour l'utilisateur actuel du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="2e48d-138">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="2e48d-139">Exemple 5 : remplacer les chaînes de texte par défaut dans un script</span><span class="sxs-lookup"><span data-stu-id="2e48d-139">Example 5: Replace default text strings in a script</span></span>

<span data-ttu-id="2e48d-140">Cet exemple montre comment utiliser `Import-LocalizedData` pour remplacer les chaînes de texte par défaut définies dans la section Data d’un script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-140">This example shows how to use `Import-LocalizedData` to replace default text strings defined in the DATA section of a script.</span></span>

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="2e48d-141">Dans cet exemple, la section de données du script TestScript.ps1 contient une `ConvertFrom-StringData` commande qui convertit le contenu de la section de données en une table de hachage et stocke dans la valeur de la `$UserMessages` variable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-141">In this example, the DATA section of the TestScript.ps1 script contains a `ConvertFrom-StringData` command that converts the contents of the DATA section to a hash table and stores in the value of the `$UserMessages` variable.</span></span>

<span data-ttu-id="2e48d-142">Le script comprend également une `Import-LocalizedData` commande qui importe une table de hachage des chaînes de texte traduites à partir du fichier TestScript.psd1 dans le sous-répertoire spécifié par la valeur de la `$PsUICulture` variable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-142">The script also includes an `Import-LocalizedData` command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the `$PsUICulture` variable.</span></span> <span data-ttu-id="2e48d-143">Si la commande trouve le `.psd1` fichier, elle enregistre les chaînes traduites à partir du fichier dans la valeur de la même `$UserMessages` variable, en remplaçant la table de hachage enregistrée par la logique de la section de données.</span><span class="sxs-lookup"><span data-stu-id="2e48d-143">If the command finds the `.psd1` file, it saves the translated strings from the file in the value of the same `$UserMessages` variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="2e48d-144">La troisième commande affiche le premier message de la `$UserMessages` variable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-144">The third command displays the first message in the `$UserMessages` variable.</span></span>

<span data-ttu-id="2e48d-145">Si la `Import-LocalizedData` commande trouve un `.psd1` fichier pour la `$PsUICulture` langue, la valeur de la `$UserMessages` variable contient les chaînes de texte traduites.</span><span class="sxs-lookup"><span data-stu-id="2e48d-145">If the `Import-LocalizedData` command finds a `.psd1` file for the `$PsUICulture` language, the value of the `$UserMessages` variable contains the translated text strings.</span></span> <span data-ttu-id="2e48d-146">Si la commande échoue pour une raison quelconque, la commande affiche les chaînes de texte par défaut définies dans la section DATA du script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-146">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="2e48d-147">Exemple 6 : supprimer les messages d’erreur si la culture de l’interface utilisateur est introuvable</span><span class="sxs-lookup"><span data-stu-id="2e48d-147">Example 6: Suppress error messages if the UI culture is not found</span></span>

<span data-ttu-id="2e48d-148">Cet exemple montre comment supprimer les messages d’erreur qui s’affichent lorsque `Import-LocalizedData` ne trouve pas les répertoires qui correspondent à la culture de l’interface utilisateur de l’utilisateur ou ne parvient pas à trouver un `.psd1` fichier pour le script dans ces répertoires.</span><span class="sxs-lookup"><span data-stu-id="2e48d-148">This example shows how to suppress the error messages that appear when `Import-LocalizedData` cannot find the directories that match the user's UI culture or cannot find a `.psd1` file for the script in those directories.</span></span>

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="2e48d-149">Vous pouvez utiliser le paramètre commun **ErrorAction** avec la valeur SilentlyContinue pour supprimer le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="2e48d-149">You can use the **ErrorAction** common parameter with a value of SilentlyContinue to suppress the error message.</span></span> <span data-ttu-id="2e48d-150">Cela s’avère particulièrement utile lorsque vous avez fourni des messages utilisateur dans une langue par défaut ou de secours, et qu’aucun message d’erreur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2e48d-150">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="2e48d-151">Cet exemple compare deux scripts, `Day1.ps1` et Day2.ps1, qui incluent une `Import-LocalizedData` commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-151">This example compares two scripts, `Day1.ps1` and Day2.ps1, that include an `Import-LocalizedData` command.</span></span> <span data-ttu-id="2e48d-152">Les scripts sont identiques, sauf que Day2 utilise le paramètre commun **ErrorAction** avec la valeur `SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="2e48d-152">The scripts are identical, except that Day2 uses the **ErrorAction** common parameter with a value of `SilentlyContinue`.</span></span>

<span data-ttu-id="2e48d-153">L’exemple de sortie montre les résultats de l’exécution des scripts lorsque la culture de l’interface utilisateur est définie sur `fr-BE` et qu’il n’existe aucun fichier ou répertoire correspondant pour cette culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e48d-153">The sample output shows the results of running both scripts when the UI culture is set to `fr-BE` and there are no matching files or directories for that UI culture.</span></span> <span data-ttu-id="2e48d-154">`Day1.ps1` affiche un message d’erreur et une sortie en anglais.</span><span class="sxs-lookup"><span data-stu-id="2e48d-154">`Day1.ps1` displays an error message and English output.</span></span> <span data-ttu-id="2e48d-155">`Day2.ps1` affiche simplement la sortie en anglais.</span><span class="sxs-lookup"><span data-stu-id="2e48d-155">`Day2.ps1` just displays the English output.</span></span>

## <span data-ttu-id="2e48d-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e48d-156">PARAMETERS</span></span>

### <span data-ttu-id="2e48d-157">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="2e48d-157">-BaseDirectory</span></span>

<span data-ttu-id="2e48d-158">Spécifie le répertoire de base où `.psd1` se trouvent les fichiers.</span><span class="sxs-lookup"><span data-stu-id="2e48d-158">Specifies the base directory where the `.psd1` files are located.</span></span> <span data-ttu-id="2e48d-159">La valeur par défaut est le répertoire où se trouve le script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-159">The default is the directory where the script is located.</span></span> <span data-ttu-id="2e48d-160">`Import-LocalizedData` recherche le `.psd1` fichier du script dans un sous-répertoire spécifique au langage du répertoire de base.</span><span class="sxs-lookup"><span data-stu-id="2e48d-160">`Import-LocalizedData` searches for the `.psd1` file for the script in a language-specific subdirectory of the base directory.</span></span>

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

### <span data-ttu-id="2e48d-161">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="2e48d-161">-BindingVariable</span></span>

<span data-ttu-id="2e48d-162">Spécifie la variable dans laquelle les chaînes de texte sont importées.</span><span class="sxs-lookup"><span data-stu-id="2e48d-162">Specifies the variable into which the text strings are imported.</span></span> <span data-ttu-id="2e48d-163">Entrez un nom de variable sans le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="2e48d-163">Enter a variable name without a dollar sign (`$`).</span></span>

<span data-ttu-id="2e48d-164">Dans Windows PowerShell 2.0, ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e48d-164">In Windows PowerShell 2.0, this parameter is required.</span></span> <span data-ttu-id="2e48d-165">Dans Windows PowerShell 3.0, ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2e48d-165">In Windows PowerShell 3.0, this parameter is optional.</span></span> <span data-ttu-id="2e48d-166">Si vous omettez ce paramètre, `Import-LocalizedData` retourne une table de hachage des chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="2e48d-166">If you omit this parameter, `Import-LocalizedData` returns a hash table of the text strings.</span></span> <span data-ttu-id="2e48d-167">La table de hachage est passée dans le pipeline ou affichée sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-167">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="2e48d-168">Lorsque `Import-LocalizedData` vous utilisez pour remplacer les chaînes de texte par défaut spécifiées dans la section de données d’un script, assignez la section de données à une variable et entrez le nom de la variable de la section de données dans la valeur du paramètre **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="2e48d-168">When using `Import-LocalizedData` to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the **BindingVariable** parameter.</span></span> <span data-ttu-id="2e48d-169">Ensuite, lorsque `Import-LocalizedData` enregistre le contenu importé dans **BindingVariable**, les données importées remplacent les chaînes de texte par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e48d-169">Then, when `Import-LocalizedData` saves the imported content in the **BindingVariable**, the imported data will replace the default text strings.</span></span> <span data-ttu-id="2e48d-170">Si vous ne spécifiez pas de chaînes de texte par défaut, vous pouvez sélectionner n'importe quel nom de variable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-170">If you are not specifying default text strings, you can select any variable name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e48d-171">Nom de fichier</span><span class="sxs-lookup"><span data-stu-id="2e48d-171">-FileName</span></span>

<span data-ttu-id="2e48d-172">Spécifie le nom du fichier de données ( `.psd1)` à importer.</span><span class="sxs-lookup"><span data-stu-id="2e48d-172">Specifies the name of the data file (`.psd1)` to be imported.</span></span> <span data-ttu-id="2e48d-173">Entrez un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2e48d-173">Enter a file name.</span></span> <span data-ttu-id="2e48d-174">Vous pouvez spécifier un nom de fichier qui n’inclut pas son `.psd1` extension de nom de fichier, ou vous pouvez spécifier le nom de fichier, y compris l' `.psd1` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2e48d-174">You can specify a file name that does not include its `.psd1` file name extension, or you can specify the file name including the `.psd1` file name extension.</span></span> <span data-ttu-id="2e48d-175">Les fichiers de données doivent être enregistrés au format Unicode ou UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2e48d-175">Data files should be saved as Unicode or UTF-8.</span></span>

<span data-ttu-id="2e48d-176">Le paramètre **filename** est obligatoire lorsque `Import-LocalizedData` n’est pas utilisé dans un script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-176">The **FileName** parameter is required when `Import-LocalizedData` is not used in a script.</span></span>
<span data-ttu-id="2e48d-177">Sinon, le paramètre est facultatif et la valeur par défaut est le nom de base du script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-177">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span> <span data-ttu-id="2e48d-178">Vous pouvez utiliser ce paramètre pour demander `Import-LocalizedData` à de rechercher un `.psd1` fichier différent.</span><span class="sxs-lookup"><span data-stu-id="2e48d-178">You can use this parameter to direct `Import-LocalizedData` to search for a different `.psd1` file.</span></span>

<span data-ttu-id="2e48d-179">Par exemple, si le **nom de fichier est omis** et que le nom du script est FindFiles.ps1, `Import-LocalizedData` recherche le fichier de données FindFiles.psd1.</span><span class="sxs-lookup"><span data-stu-id="2e48d-179">For example, if the **FileName** is omitted and the script name is FindFiles.ps1, `Import-LocalizedData` searches for the FindFiles.psd1 data file.</span></span>

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

### <span data-ttu-id="2e48d-180">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="2e48d-180">-SupportedCommand</span></span>

<span data-ttu-id="2e48d-181">Spécifie les applets de commande et les fonctions qui génèrent uniquement des données.</span><span class="sxs-lookup"><span data-stu-id="2e48d-181">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="2e48d-182">Utilisez ce paramètre pour inclure les applets de commande et les fonctions que vous avez écrites ou testées.</span><span class="sxs-lookup"><span data-stu-id="2e48d-182">Use this parameter to include cmdlets and functions that you have written or tested.</span></span> <span data-ttu-id="2e48d-183">Pour plus d’informations, consultez [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="2e48d-183">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e48d-184">-UICulture</span><span class="sxs-lookup"><span data-stu-id="2e48d-184">-UICulture</span></span>

<span data-ttu-id="2e48d-185">Spécifie une autre culture d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e48d-185">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="2e48d-186">La valeur par défaut est la valeur de la `$PsUICulture` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="2e48d-186">The default is the value of the `$PsUICulture` automatic variable.</span></span>
<span data-ttu-id="2e48d-187">Entrez une culture d’interface utilisateur au `<language>-<region>` format, telle que `en-US` , `de-DE` ou `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="2e48d-187">Enter a UI culture in `<language>-<region>` format, such as `en-US`, `de-DE`, or `ar-SA`.</span></span>

<span data-ttu-id="2e48d-188">La valeur du paramètre **UICulture** détermine le sous-répertoire spécifique au langage (dans le répertoire de base) à partir duquel `Import-LocalizedData` obtient le `.psd1` fichier du script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-188">The value of the **UICulture** parameter determines the language-specific subdirectory (within the base directory) from which `Import-LocalizedData` gets the `.psd1` file for the script.</span></span>

<span data-ttu-id="2e48d-189">L’applet de commande recherche un sous-répertoire portant le même nom que la valeur du paramètre **UICulture** ou de la `$PsUICulture` variable automatique, par exemple `de-DE` ou `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="2e48d-189">The cmdlet searches for a subdirectory with the same name as the value of the **UICulture** parameter or the `$PsUICulture` automatic variable, such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="2e48d-190">S’il ne trouve pas le répertoire ou si le répertoire ne contient pas de `.psd1` fichier pour le script, il recherche un sous-répertoire avec le nom du code de langue, tel que de ou ar.</span><span class="sxs-lookup"><span data-stu-id="2e48d-190">If it cannot find the directory, or the directory does not contain a `.psd1` file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="2e48d-191">S’il ne peut pas trouver le sous-répertoire ou le `.psd1` fichier, la commande échoue et les données sont affichées dans la langue par défaut spécifiée dans le script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-191">If it cannot find the subdirectory or `.psd1` file, the command fails and the data is displayed in the default language specified in the script.</span></span>

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

### <span data-ttu-id="2e48d-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e48d-192">CommonParameters</span></span>

<span data-ttu-id="2e48d-193">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e48d-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e48d-194">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2e48d-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e48d-195">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2e48d-195">INPUTS</span></span>

### <span data-ttu-id="2e48d-196">None</span><span class="sxs-lookup"><span data-stu-id="2e48d-196">None</span></span>

<span data-ttu-id="2e48d-197">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-197">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="2e48d-198">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2e48d-198">OUTPUTS</span></span>

### <span data-ttu-id="2e48d-199">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="2e48d-199">System.Collections.Hashtable</span></span>

<span data-ttu-id="2e48d-200">`Import-LocalizedData` enregistre la table de hachage dans la variable spécifiée par la valeur du paramètre **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="2e48d-200">`Import-LocalizedData` saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="2e48d-201">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2e48d-201">NOTES</span></span>

- <span data-ttu-id="2e48d-202">Avant d’utiliser `Import-LocalizedData` , Localisez vos messages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e48d-202">Before using `Import-LocalizedData`, localize your user messages.</span></span> <span data-ttu-id="2e48d-203">Mettez en forme les messages pour chaque paramètre régional (culture d’interface utilisateur) dans une table de hachage de paires clé-valeur et enregistrez la table de hachage dans un fichier portant le même nom que le script et une `.psd1` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2e48d-203">Format the messages for each locale (UI culture) in a hash table of key-value pairs, and save the hash table in a file with the same name as the script and a `.psd1` file name extension.</span></span> <span data-ttu-id="2e48d-204">Créez un répertoire sous le répertoire de scripts pour chaque culture d’interface utilisateur prise en charge, puis enregistrez le `.psd1` fichier pour chaque culture d’interface utilisateur dans le répertoire avec le nom de la culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e48d-204">Create a directory under the script directory for each supported UI culture, and then save the `.psd1` file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="2e48d-205">Par exemple, localisez vos messages utilisateur pour les paramètres régionaux fr-FR et mettez-les en forme dans une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="2e48d-205">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
  <span data-ttu-id="2e48d-206">Enregistrez la table de hachage dans un `<ScriptName>.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="2e48d-206">Save the hash table in a `<ScriptName>.psd1` file.</span></span> <span data-ttu-id="2e48d-207">Créez ensuite un sous `de-DE` -répertoire sous le répertoire de scripts, puis enregistrez le `<ScriptName\>.psd1` fichier allemand dans le `de-DE` sous-répertoire.</span><span class="sxs-lookup"><span data-stu-id="2e48d-207">Then create a `de-DE` subdirectory under the script directory, and save the German `<ScriptName\>.psd1` file in the `de-DE` subdirectory.</span></span>
  <span data-ttu-id="2e48d-208">Répétez l'opération pour chacun des paramètres régionaux pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2e48d-208">Repeat this method for each locale that you support.</span></span>

- <span data-ttu-id="2e48d-209">`Import-LocalizedData` effectue une recherche structurée des messages utilisateur localisés pour un script.</span><span class="sxs-lookup"><span data-stu-id="2e48d-209">`Import-LocalizedData` performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="2e48d-210">`Import-LocalizedData` commence la recherche dans le répertoire où se trouve le fichier de script (ou la valeur du paramètre **baseDirectory** ).</span><span class="sxs-lookup"><span data-stu-id="2e48d-210">`Import-LocalizedData` begins the search in the directory where the script file is located (or the value of the **BaseDirectory** parameter).</span></span> <span data-ttu-id="2e48d-211">Il recherche ensuite dans le répertoire de base un sous-répertoire portant le même nom que la valeur de la `$PsUICulture` variable (ou la valeur du paramètre **UICulture** ), par exemple `de-DE` ou `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="2e48d-211">It then searches within the base directory for a subdirectory with the same name as the value of the `$PsUICulture` variable (or the value of the **UICulture** parameter), such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="2e48d-212">Il recherche ensuite dans ce sous-répertoire un `.psd1` fichier portant le même nom que le script (ou la valeur du paramètre **filename** ).</span><span class="sxs-lookup"><span data-stu-id="2e48d-212">Then, it searches in that subdirectory for a `.psd1` file with the same name as the script (or the value of the **FileName** parameter).</span></span>

  <span data-ttu-id="2e48d-213">Si `Import-LocalizedData` ne peut pas trouver un sous-répertoire avec le nom de la culture de l’interface utilisateur, ou si le sous-répertoire ne contient pas de `.psd1` fichier pour le script, il recherche un `.psd1` fichier pour le script dans un sous-répertoire avec le nom du code de langue, par exemple de ou ar.</span><span class="sxs-lookup"><span data-stu-id="2e48d-213">If `Import-LocalizedData` cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a `.psd1` file for the script, it searches for a `.psd1` file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="2e48d-214">S’il ne peut pas trouver le sous-répertoire ou le `.psd1` fichier, la commande échoue, les données sont affichées dans la langue par défaut dans le script et un message d’erreur s’affiche, expliquant que les données n’ont pas pu être importées.</span><span class="sxs-lookup"><span data-stu-id="2e48d-214">If it cannot find the subdirectory or `.psd1` file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span> <span data-ttu-id="2e48d-215">Pour supprimer le message et échouer correctement, utilisez le paramètre commun **ErrorAction** avec la valeur SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="2e48d-215">To suppress the message and fail gracefully, use the **ErrorAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="2e48d-216">Si `Import-LocalizedData` recherche le sous-répertoire et le `.psd1` fichier, il importe la table de hachage des messages utilisateur dans la valeur du paramètre **BindingVariable** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="2e48d-216">If `Import-LocalizedData` finds the subdirectory and the `.psd1` file, it imports the hash table of user messages into the value of the **BindingVariable** parameter in the command.</span></span> <span data-ttu-id="2e48d-217">Ensuite, lorsque vous affichez un message à partir de la table de hachage de la variable, le message localisé apparaît.</span><span class="sxs-lookup"><span data-stu-id="2e48d-217">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="2e48d-218">Pour plus d’informations, consultez [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="2e48d-218">For more information, see [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="2e48d-219">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2e48d-219">RELATED LINKS</span></span>

[<span data-ttu-id="2e48d-220">Write-Host</span><span class="sxs-lookup"><span data-stu-id="2e48d-220">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="2e48d-221">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="2e48d-221">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)

