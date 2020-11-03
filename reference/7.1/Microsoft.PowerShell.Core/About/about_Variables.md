---
description: Décrit comment les variables stockent des valeurs qui peuvent être utilisées dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 0865afe69f5f1774e90d2d2dc5827d628cab0f6a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206697"
---
# <a name="about-variables"></a>À propos des variables

## <a name="short-description"></a>Description courte

Décrit comment les variables stockent des valeurs qui peuvent être utilisées dans PowerShell.

## <a name="long-description"></a>Description longue

Vous pouvez stocker tous les types de valeurs dans les variables PowerShell. Par exemple, stockez les résultats des commandes et stockez les éléments utilisés dans les commandes et les expressions, telles que les noms, les chemins d’accès, les paramètres et les valeurs.

Une variable est une unité de mémoire dans laquelle les valeurs sont stockées. Dans PowerShell, les variables sont représentées par des chaînes de texte qui commencent par un signe dollar ( `$` ), telles que `$a` , `$process` ou `$my_var` .

Les noms de variable ne respectent pas la casse et peuvent inclure des espaces et des caractères spéciaux. Toutefois, les noms de variables qui contiennent des caractères spéciaux et des espaces sont difficiles à utiliser et doivent être évités. Pour plus d’informations, consultez [noms de variables qui contiennent des caractères spéciaux](#variable-names-that-include-special-characters).

Il existe différents types de variables dans PowerShell.

- Variables créées par l’utilisateur : les variables créées par l’utilisateur sont créées et gérées par l’utilisateur. Par défaut, les variables que vous créez au niveau de la ligne de commande PowerShell existent uniquement lorsque la fenêtre PowerShell est ouverte. Une fois la fenêtre PowerShell fermée, les variables sont supprimées. Pour enregistrer une variable, ajoutez-la à votre profil PowerShell. Vous pouvez également créer des variables dans des scripts avec une portée globale, de script ou locale.

- Variables automatiques : les variables automatiques stockent l’état de PowerShell. Ces variables sont créées par PowerShell et PowerShell modifie leurs valeurs selon les besoins afin de conserver leur exactitude. Les utilisateurs ne peuvent pas modifier la valeur de ces variables. Par exemple, la `$PSHOME` variable stocke le chemin d’accès au répertoire d’installation de PowerShell.

  Pour plus d’informations, une liste et une description des variables automatiques, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

- Variables de préférence : les variables de préférence stockent les préférences utilisateur pour PowerShell. Ces variables sont créées par PowerShell et sont remplies avec les valeurs par défaut. Les utilisateurs peuvent modifier les valeurs de ces variables. Par exemple, la `$MaximumHistoryCount` variable détermine le nombre maximal d’entrées dans l’historique de session.

  Pour plus d’informations, une liste et une description des variables de préférence, consultez [about_Preference_Variables](about_Preference_Variables.md).

## <a name="working-with-variables"></a>Utilisation de variables

Pour créer une variable, utilisez une instruction d’assignation pour assigner une valeur à la variable. Vous n’avez pas besoin de déclarer la variable avant de l’utiliser. La valeur par défaut de toutes les variables est `$null` .

Pour obtenir la liste de toutes les variables de votre session PowerShell, tapez `Get-Variable` . Les noms de variables s’affichent sans le signe dollar ( `$` ) qui est utilisé pour référencer des variables.

Par exemple :

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

Les variables sont utiles pour stocker les résultats des commandes.

Par exemple :

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

Pour afficher la valeur d’une variable, tapez le nom de la variable, précédé d’un signe dollar ( `$` ).

Par exemple :

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

Pour modifier la valeur d’une variable, assignez une nouvelle valeur à la variable.

Les exemples suivants affichent la valeur de la `$MyVariable` variable, modifient la valeur de la variable, puis affiche la nouvelle valeur.

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

Pour supprimer la valeur d’une variable, utilisez l' `Clear-Variable` applet de commande ou remplacez la valeur par `$null` .

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

Pour supprimer la variable, utilisez [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) ou [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a>Types de variable

Vous pouvez stocker n’importe quel type d’objet dans une variable, y compris des entiers, des chaînes, des tableaux et des tables de hachage. Et, objets qui représentent des processus, des services, des journaux des événements et des ordinateurs.

Les variables PowerShell sont faiblement typées, ce qui signifie qu’elles ne sont pas limitées à un type particulier d’objet. Une variable unique peut même contenir une collection ou un tableau de différents types d’objets en même temps.

Le type de données d’une variable est déterminé par les types .NET des valeurs de la variable. Pour afficher le type d’objet d’une variable, utilisez la valeur de l' [élément obtenir un membre](xref:Microsoft.PowerShell.Utility.Get-Member).

Par exemple :

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

Vous pouvez utiliser un attribut de type et une notation cast pour vous assurer qu’une variable peut contenir uniquement des types d’objets ou des objets spécifiques qui peuvent être convertis en ce type. Si vous essayez d’assigner une valeur d’un autre type, PowerShell tente de convertir la valeur en son type. Si le type ne peut pas être converti, l’instruction d’assignation échoue.

Pour utiliser la notation Cast, entrez un nom de type, placé entre parenthèses, avant le nom de la variable (sur le côté gauche de l’instruction d’assignation). L’exemple suivant crée une `$number` variable qui ne peut contenir que des entiers, une `$words` variable qui ne peut contenir que des chaînes et une `$dates` variable qui ne peut contenir que des objets **DateTime** .

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a>Utilisation de variables dans des commandes et des expressions

Pour utiliser une variable dans une commande ou une expression, tapez le nom de la variable, précédé du signe dollar ( `$` ).

Si le nom de la variable et le signe dollar ne sont pas placés entre guillemets, ou s’ils sont placés entre guillemets doubles ( `"` ), la valeur de la variable est utilisée dans la commande ou l’expression.

Si le nom de la variable et le signe dollar sont placés entre guillemets simples ( `'` ), le nom de la variable est utilisé dans l’expression.

Pour plus d’informations sur l’utilisation des guillemets dans PowerShell, consultez [about_Quoting_Rules](about_Quoting_Rules.md).

Cet exemple obtient la valeur de la `$PROFILE` variable, qui est le chemin d’accès au fichier de profil utilisateur PowerShell dans la console PowerShell.

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

Dans cet exemple, deux commandes qui permettent d’ouvrir le profil PowerShell dans **notepad.exe** sont affichées. L’exemple avec des marques à guillemet double ( `"` ) utilise la valeur de la variable.

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

Les exemples suivants utilisent des marques à guillemet simple ( `'` ) qui traitent la variable comme du texte littéral.

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a>Noms de variables qui contiennent des caractères spéciaux

Les noms de variables commencent par un `$` signe dollar () et peuvent inclure des caractères alphanumériques et des caractères spéciaux. La longueur du nom de la variable n’est limitée que par la mémoire disponible.

La meilleure pratique est que les noms de variables incluent uniquement des caractères alphanumériques et le caractère de soulignement ( `_` ). Les noms de variables qui incluent des espaces et d’autres caractères spéciaux sont difficiles à utiliser et doivent être évités.

Les noms de variables alphanumériques peuvent contenir les caractères suivants :

- Caractères Unicode de ces catégories : **lu** , **ll** , **lt** , **LM** , **Lo** ou **ND** .
- Caractère de soulignement ( `_` ).
- Point d’interrogation ( `?` ).

La liste suivante contient les descriptions des catégories Unicode. Pour plus d’informations, consultez [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).

- **Lu** -UppercaseLetter
- **Ll** -LowercaseLetter
- **Lt** -TitlecaseLetter
- **LM** -ModifierLetter
- **Lo** -OtherLetter
- **ND** -DecimalDigitNumber

Pour créer ou afficher un nom de variable qui comprend des espaces ou des caractères spéciaux, placez le nom de la variable entre accolades ( `{}` ).
Les accolades redirigent PowerShell pour interpréter les caractères du nom de la variable comme des littéraux.

Les noms de variable de caractères spéciaux peuvent contenir les caractères suivants :

- N’importe quel caractère Unicode, avec les exceptions suivantes :
  - Caractère d’accolade fermante ( `}` ) (U + 007D).
  - `` ` ``Caractère de soulignement () (U + 0060). L’accent est utilisé pour échapper les caractères Unicode afin qu’ils soient traités comme des littéraux.

PowerShell a des variables réservées telles que `$$` ,, `$?` `$^` et `$_` qui contiennent des caractères alphanumériques et spéciaux. Pour plus d’informations, consultez [about_Automatic_Variables](about_automatic_variables.md).

Par exemple, la commande suivante crée la variable nommée `save-items` . Les accolades ( `{}` ) sont nécessaires, car le nom de la variable comprend un caractère spécial de trait d’Union ( `-` ).

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

La commande suivante obtient les éléments enfants dans le répertoire qui est représenté par la `ProgramFiles(x86)` variable d’environnement.

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

Pour faire référence à un nom de variable qui comprend des accolades, placez le nom de la variable entre accolades et utilisez le caractère d’échappement pour échapper les accolades. Par exemple, pour créer une variable nommée `this{value}is` type :

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a>Variables et portée

Par défaut, les variables sont uniquement disponibles dans l’étendue dans laquelle elles sont créées.

Par exemple, une variable que vous créez dans une fonction est disponible uniquement dans la fonction. Une variable que vous créez dans un script est uniquement disponible dans le script. Si vous pointez la source du script, la variable est ajoutée à l’étendue actuelle. Pour plus d’informations, consultez [about_Scopes](about_Scopes.md).

Vous pouvez utiliser un modificateur d’étendue pour modifier l’étendue par défaut de la variable. L’expression suivante crée une variable nommée `Computers` . La variable a une portée globale, même lorsqu’elle est créée dans un script ou une fonction.

```powershell
$Global:Computers = "Server01"
```

Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder.

Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).

## <a name="saving-variables"></a>Enregistrement de variables

Les variables que vous créez sont disponibles uniquement dans la session dans laquelle vous les créez. Ils sont perdus quand vous fermez votre session.

Pour créer la variable dans chaque session PowerShell que vous démarrez, ajoutez la variable à votre profil PowerShell.

Par exemple, pour modifier la valeur de la `$VerbosePreference` variable dans chaque session PowerShell, ajoutez la commande suivante à votre profil PowerShell.

```powershell
$VerbosePreference = "Continue"
```

Vous pouvez ajouter cette commande à votre profil PowerShell en ouvrant le `$PROFILE` fichier dans un éditeur de texte, tel que **notepad.exe** . Pour plus d’informations sur les profils PowerShell, voir [about_Profiles](about_Profiles.md).

## <a name="the-variable-drive"></a>Le lecteur variable :

Le fournisseur de variables PowerShell crée un `Variable:` lecteur qui ressemble à un lecteur du système de fichiers, mais il contient les variables de votre session et leurs valeurs.

Pour passer au `Variable:` lecteur, utilisez la commande suivante :

```powershell
Set-Location Variable:
```

Pour répertorier les éléments et les variables dans le `Variable:` lecteur, utilisez les `Get-Item` applets de commande ou `Get-ChildItem` .

```powershell
Get-ChildItem Variable:
```

Pour obtenir la valeur d’une variable particulière, utilisez la notation du système de fichiers pour spécifier le nom du lecteur et le nom de la variable. Par exemple, pour obtenir la `$PSCulture` variable automatique, utilisez la commande suivante.

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

Pour afficher plus d’informations sur le `Variable:` lecteur et le fournisseur de variable PowerShell, tapez :

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a>Syntaxe de variable avec chemins d’accès de fournisseur

Vous pouvez préfixer un chemin d’accès de fournisseur avec le signe dollar ( `$` ) et accéder au contenu de n’importe quel fournisseur qui implémente l’interface [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) .

Les fournisseurs PowerShell intégrés suivants prennent en charge cette notation :

- [about_Environment_Provider](about_Environment_Provider.md)
- [about_Variable_Provider](about_Variable_Provider.md)
- [about_Function_Provider](about_Function_Provider.md)
- [about_Alias_Provider](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a>Applets de commande de variable

PowerShell comprend un ensemble d’applets de commande conçues pour gérer des variables.

Pour répertorier les applets de commande, tapez :

```powershell
Get-Command -Noun Variable
```

Pour obtenir de l’aide pour une applet de commande spécifique, tapez :

```powershell
Get-Help <cmdlet-name>
```

| Nom de l'applet de commande       | Description                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | Supprime la valeur d'une variable.           |
| `Get-Variable`    | Obtient les variables dans la console active. |
| `New-Variable`    | Crée une variable.                    |
| `Remove-Variable` | Supprime une variable et sa valeur.          |
| `Set-Variable`    | Modifie la valeur d’une variable.           |

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Scopes](about_Scopes.md)

[about_Remote_Variables](about_Remote_Variables.md)

