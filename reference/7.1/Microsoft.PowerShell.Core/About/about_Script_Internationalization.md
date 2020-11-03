---
description: Décrit les fonctionnalités d’internationalisation de script qui permettent aux scripts d’afficher facilement des messages et des instructions pour les utilisateurs dans leur langue d’interface utilisateur.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 9506500c8e689933a5826504c344a949eb24a53b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208234"
---
# <a name="about-script-internationalization"></a>À propos de l’internationalisation des scripts

## <a name="short-description"></a>Description courte
Décrit les fonctionnalités d’internationalisation de script qui permettent aux scripts d’afficher facilement des messages et des instructions pour les utilisateurs dans leur langue d’interface utilisateur.

## <a name="long-description"></a>Description longue

Les fonctionnalités d’internationalisation des scripts PowerShell vous permettent de mieux servir les utilisateurs dans le monde entier en affichant l’aide et les messages utilisateur dans la langue de l’utilisateur.

Les fonctionnalités d’internationalisation de script interrogent la culture d’interface utilisateur du système d’exploitation lors de l’exécution, importent les chaînes de texte traduites appropriées et les affichent à l’utilisateur. La section Data vous permet de stocker des chaînes de texte séparées du code afin qu’elles soient facilement identifiées et extraites. Une nouvelle applet de commande `ConvertFrom-StringData` convertit les chaînes de texte en tables de hachage de type dictionnaire pour faciliter la traduction.

Pour prendre en charge le texte d’aide internationale, PowerShell comprend les fonctionnalités suivantes :

- Section de données qui sépare les chaînes de texte des instructions de code. Pour plus d’informations sur la section des données, consultez [about_Data_Sections](about_Data_Sections.md).

- Nouvelles variables automatiques, `$PSCulture` et `$PSUICulture` . `$PSCulture` stocke le nom de la langue de l’interface utilisateur utilisée sur le système pour les éléments tels que la date, l’heure et la devise. La `$PSUICulture` variable stocke le nom de la langue de l’interface utilisateur utilisée sur le système pour les éléments d’interface utilisateur tels que les menus et les chaînes de texte.

- Une applet de commande, `ConvertFrom-StringData` , qui convertit les chaînes de texte en tables de hachage de type dictionnaire pour faciliter la traduction. Pour plus d’informations, consultez [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).

- Nouveau type de fichier, `.psd1` , qui stocke les chaînes de texte traduites. Les `.psd1` fichiers sont stockés dans des sous-répertoires spécifiques à la langue du répertoire du script.

- Une applet de commande, `Import-LocalizedData` , qui importe les chaînes de texte traduites pour un langage spécifié dans un script au moment de l’exécution. Cette applet de commande reconnaît et importe des chaînes dans n’importe quel langage pris en charge par Windows. Pour plus d’informations [, consultez Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).

### <a name="the-data-section-storing-default-strings"></a>La section Data : stockage de chaînes par défaut

Utilisez une section de données dans le script pour stocker les chaînes de texte dans la langue par défaut. Réorganisez les chaînes dans des paires clé/valeur dans une chaîne ici. Chaque paire clé/valeur doit se trouver sur une ligne distincte. Si vous incluez des commentaires, les commentaires doivent se trouver sur des lignes distinctes.

L' `ConvertFrom-StringData` applet de commande convertit les paires clé/valeur dans la chaîne here en une table de hachage de type dictionnaire qui est stockée dans la valeur de la variable de la section de données.

Dans l’exemple suivant, la section de données du `World.ps1` script comprend le jeu d’États de English-United (en-US) des messages d’invite pour un script. L' `ConvertFrom-StringData` applet de commande convertit les chaînes en une table de hachage et les stocke dans la `$msgtable` variable.

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

Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](about_Quoting_Rules.md).

### <a name="psd1-files-storing-translated-strings"></a>Fichiers PSD1 : stockage de chaînes traduites

Enregistrez les messages de script pour chaque langue de l’interface utilisateur dans des fichiers texte distincts portant le même nom que le script et l' `.psd1` extension de nom de fichier. Stockez les fichiers dans les sous-répertoires du répertoire de script avec des noms de cultures au format suivant :

`<language>-<region>`

Exemples : de-DE, ar-SA et zh-Hans

Par exemple, si le `World.ps1` script est stocké dans le `C:\Scripts` répertoire, vous devez créer une structure de répertoires de fichiers qui ressemble à ce qui suit :

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

Le `World.psd1` fichier dans le sous-répertoire du répertoire de script peut inclure l’instruction suivante :

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

De même, le `World.psd1` fichier dans le sous-répertoire ar-sa du répertoire de script peut inclure l’instruction suivante :

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a>Import-LocalizedData : récupération dynamique des chaînes traduites

Pour récupérer les chaînes dans la langue de l’interface utilisateur de l’utilisateur actuel, utilisez l’applet de commande `Import-LocalizedData` .

`Import-LocalizedData` recherche la valeur de la `$PSUICulture` variable automatique et importe le contenu des `<script-name>.psd1` fichiers dans le sous-répertoire qui correspond à la `$PSUICulture` valeur. Ensuite, il enregistre le contenu importé dans la variable spécifiée par la valeur du paramètre **BindingVariable** .

```powershell
Import-LocalizedData -BindingVariable msgTable
```

Par exemple, si la `Import-LocalizedData` commande apparaît dans le `C:\Scripts\World.ps1` script et que la valeur de `$PSUICulture` est « AR-sa », `Import-LocalizedData` recherche le fichier suivant :

`C:\Scripts\ar-SA\World.psd1`

Ensuite, il importe les chaînes de texte arabe du fichier dans la `$msgTable` variable, en remplaçant les chaînes par défaut qui peuvent être définies dans la section de données du `World.ps1` script.

Par conséquent, lorsque le script utilise la `$msgTable` variable pour afficher des messages utilisateur, les messages s’affichent en arabe.

Par exemple, le script suivant affiche le message « Veuillez entrer votre nom d’utilisateur » en arabe :

```powershell
if (!($username)) { $msgTable.promptMsg }
```

Si `Import-LocalizedData` ne peut pas trouver un `.psd1` fichier qui correspond à la valeur de `$PSUIculture` , la valeur de `$msgTable` n’est pas remplacée et l’appel à `$msgTable.promptMsg` affiche les chaînes en-US de secours.

## <a name="examples"></a>Exemples

Cet exemple montre comment les fonctionnalités d’internationalisation de script sont utilisées dans un script pour afficher un jour de la semaine aux utilisateurs dans la langue définie sur l’ordinateur.

Voici la liste complète des Sample1.ps1 fichier de script.

Le script commence par une section de données nommée Day ($Day) qui contient une `ConvertFrom-StringData` commande. L’expression soumise à `ConvertFrom-StringData` est une chaîne « here » qui contient les noms de jours dans la culture d’interface utilisateur par défaut, en-US, dans les paires clé/valeur. L' `ConvertFrom-StringData` applet de commande convertit les paires clé/valeur dans la chaîne here en une table de hachage, puis l’enregistre dans la valeur de la `$Day` variable.

La `Import-LocalizedData` commande importe le contenu du `.psd1` fichier dans le répertoire qui correspond à la valeur de la `$PSUICulture` variable automatique, puis l’enregistre dans la `$Day` variable, en remplaçant les valeurs de `$Day` qui sont définies dans la section de données.

Les commandes restantes chargent les chaînes dans un tableau et les affichent.

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

Les `.psd1` fichiers qui prennent en charge le script sont enregistrés dans des sous-répertoires du répertoire de script dont les noms correspondent aux `$PSUICulture` valeurs.

Voici une liste complète des éléments suivants `.\de-DE\sample1.psd1` :

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

Par conséquent, lorsque vous exécutez Sample.ps1 sur un système sur lequel la valeur de `$PSUICulture` est de-de, la sortie du script est la suivante :

```Output
Heute ist Freitag
```

## <a name="see-also"></a>Voir aussi

- [about_Data_Sections](about_Data_Sections.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

