---
description: Explique les sections de données, qui isolent les chaînes de texte et d’autres données en lecture seule de la logique de script.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: d45339bae42b1131e1dfb9618413a34e250a578e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208070"
---
# <a name="about-data-sections"></a>À propos des sections de données

## <a name="short-description"></a>Description courte
Explique les sections de données, qui isolent les chaînes de texte et d’autres données en lecture seule de la logique de script.

## <a name="long-description"></a>Description longue

Les scripts conçus pour PowerShell peuvent avoir une ou plusieurs sections de données qui contiennent uniquement des données. Vous pouvez inclure une ou plusieurs sections de données dans n’importe quel script, fonction ou fonction avancée. Le contenu de la section de données est limité à un sous-ensemble spécifié du langage de script PowerShell.

La séparation des données de la logique du code facilite l’identification et la gestion de la logique et des données. Elle vous permet d’avoir des fichiers de ressources de chaîne distincts pour le texte, tels que des messages d’erreur et des chaînes d’aide. Il isole également la logique du code, ce qui facilite les tests de sécurité et de validation.

Dans PowerShell, la section des données est utilisée pour prendre en charge l’internationalisation des scripts.
Vous pouvez utiliser les sections de données pour faciliter l’isolation, la localisation et le traitement des chaînes qui seront traduites dans de nombreuses langues d’interface utilisateur (IU).

La section Data est une fonctionnalité PowerShell 2,0. Les scripts avec des sections de données ne s’exécuteront pas dans PowerShell 1,0 sans révision.

### <a name="syntax"></a>Syntaxe

La syntaxe d’une section de données est la suivante :

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

Le mot clé Data est obligatoire. Il ne respecte pas la casse. Le contenu autorisé est limité aux éléments suivants :

- Tous les opérateurs PowerShell, sauf `-match`
- `If``Else`instructions, et `ElseIf`
- Les variables automatiques suivantes : `$PsCulture` , `$PsUICulture` , `$True` , `$False` et `$Null`
- Commentaires
- Pipelines
- Instructions séparées par des points-virgules ( `;` )
- Les littéraux, tels que les suivants :

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

- Applets de commande autorisées dans une section de données. Par défaut, seule l' `ConvertFrom-StringData` applet de commande est autorisée.
- Les applets de commande que vous autorisez dans une section de données à l’aide du `-SupportedCommand` paramètre.

Quand vous utilisez l' `ConvertFrom-StringData` applet de commande dans une section de données, vous pouvez encadrer les paires clé-valeur dans des chaînes à guillemet simple ou entre guillemets ou dans des chaînes à guillemet simple ou à deux guillemets. Toutefois, les chaînes qui contiennent des variables et des sous-expressions doivent être placées entre des chaînes entre guillemets simples ou des chaînes ici à guillemets simples pour que les variables ne soient pas développées et que les sous-expressions ne soient pas exécutables.

### <a name="-supportedcommand"></a>-SupportedCommand

Le `-SupportedCommand` paramètre vous permet d’indiquer qu’une applet de commande ou une fonction génère uniquement des données. Il est conçu pour permettre aux utilisateurs d’inclure des applets de commande et des fonctions dans une section de données qu’ils ont écrites ou testées.

La valeur de `-SupportedCommand` est une liste séparée par des virgules d’un ou plusieurs noms d’applet de commande ou de fonction.

Par exemple, la section de données suivante comprend une applet de commande écrite par l’utilisateur, `Format-XML` , qui met en forme les données d’un fichier XML :

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a>Utilisation d’une section de données

Pour utiliser le contenu d’une section de données, affectez-la à une variable et utilisez la notation de variable pour accéder au contenu.

Par exemple, la section de données suivante contient une `ConvertFrom-StringData` commande qui convertit la chaîne here en une table de hachage. La table de hachage est assignée à la `$TextMsgs` variable.

La `$TextMsgs` variable ne fait pas partie de la section de données.

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

Pour accéder aux clés et aux valeurs de la table de hachage dans `$TextMsgs` , utilisez les commandes suivantes.

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

Vous pouvez également placer le nom de la variable dans la définition de la section de données. Par exemple :

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

Le résultat est le même que dans l’exemple précédent.

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a>Exemples

Chaînes de données simples.

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

Chaînes qui incluent des variables autorisées.

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

Chaîne « here » à guillemet simple qui utilise l' `ConvertFrom-StringData` applet de commande :

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

Chaîne « here » à deux guillemets qui utilise l’applet de commande `ConvertFrom-StringData` :

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

Une section de données qui comprend une applet de commande écrite par l’utilisateur qui génère des données :

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_If](about_If.md)

[about_Operators](about_Operators.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
