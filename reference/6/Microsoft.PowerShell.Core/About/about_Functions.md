---
description: Décrit comment créer et utiliser des fonctions dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: 4bc921b19951290efd1c8cbe5c8bb014912695f0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207093"
---
# <a name="about-functions"></a>À propos des fonctions

## <a name="short-description"></a>Description courte

Décrit comment créer et utiliser des fonctions dans PowerShell.

## <a name="long-description"></a>Description longue

Une fonction est une liste d’instructions PowerShell qui porte un nom que vous attribuez. Lorsque vous exécutez une fonction, vous tapez le nom de la fonction. Les instructions de la liste sont exécutées comme si vous les aviez tapées à l’invite de commandes.

Les fonctions peuvent être aussi simples que :

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

Une fonction peut également être aussi complexe qu’une applet de commande ou un programme d’application.

Comme les applets de commande, les fonctions peuvent avoir des paramètres. Les paramètres peuvent être des paramètres nommés, positionnels, de commutateur ou dynamiques. Les paramètres de fonction peuvent être lus à partir de la ligne de commande ou du pipeline.

Les fonctions peuvent retourner des valeurs qui peuvent être affichées, affectées à des variables ou passées à d’autres fonctions ou applets de commande. Vous pouvez également spécifier une valeur de retour à l’aide du `return` mot clé. Le `return` mot clé n’affecte pas ou ne supprime pas la sortie retournée par votre fonction. Toutefois, le `return` mot clé quitte la fonction à cette ligne. Pour plus d’informations, consultez [about_Return](about_Return.md).

La liste des instructions de la fonction peut contenir différents types de listes d’instructions avec les mots clés `Begin` , `Process` et `End` . Ces instructions répertorient différemment l’entrée du pipeline.

Un filtre est un type spécial de fonction qui utilise le `Filter` mot clé.

Les fonctions peuvent également agir comme des applets de commande. Vous pouvez créer une fonction qui fonctionne comme une applet de commande sans utiliser la `C#` programmation. Pour plus d’informations, consultez [about_Functions_Advanced](about_Functions_Advanced.md).

## <a name="syntax"></a>Syntaxe

Voici la syntaxe d’une fonction :

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

Une fonction comprend les éléments suivants :

- `Function`Mot clé
- Une étendue (facultatif)
- Un nom que vous sélectionnez
- N’importe quel nombre de paramètres nommés (facultatif)
- Une ou plusieurs commandes PowerShell placées entre accolades `{}`

Pour plus d’informations sur le `Dynamicparam` mot clé et les paramètres dynamiques dans les fonctions, consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

## <a name="simple-functions"></a>Fonctions simples

Les fonctions n’ont pas besoin d’être compliquées pour être utiles. Les fonctions les plus simples ont le format suivant :

```
function <function-name> {statements}
```

Par exemple, la fonction suivante démarre PowerShell avec l’option Exécuter en tant qu’administrateur.

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

Pour utiliser la fonction, tapez : `Start-PSAdmin`

Pour ajouter des instructions à la fonction, tapez chaque instruction sur une ligne distincte ou utilisez un point-virgule `;` pour séparer les instructions.

Par exemple, la fonction suivante recherche tous les `.jpg` fichiers dans les répertoires de l’utilisateur actuel qui ont été modifiés après la date de début.

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

Vous pouvez créer une boîte à outils de petites fonctions utiles. Ajoutez ces fonctions à votre profil PowerShell, comme décrit dans [about_Profiles](about_Profiles.md) et versions ultérieures dans cette rubrique.

## <a name="function-names"></a>Noms de fonction

Vous pouvez assigner n’importe quel nom à une fonction, mais les fonctions que vous partagez avec d’autres utilisateurs doivent suivre les règles d’affectation de noms qui ont été établies pour toutes les commandes PowerShell.

Les noms de fonctions doivent être constitués d’une paire verbe-substantif dans laquelle le verbe identifie l’action exécutée par la fonction et le nom identifie l’élément sur lequel l’applet de commande exécute son action.

Les fonctions doivent utiliser les verbes standard qui ont été approuvés pour toutes les commandes PowerShell. Ces verbes nous aident à faire en sorte que les noms de commande restent simples, cohérents et faciles à comprendre pour les utilisateurs.

Pour plus d’informations sur les verbes PowerShell standard, consultez [verbes approuvés](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) dans le Microsoft docs.

## <a name="functions-with-parameters"></a>Fonctions avec paramètres

Vous pouvez utiliser des paramètres avec des fonctions, y compris des paramètres nommés, des paramètres positionnels, des paramètres de commutateur et des paramètres dynamiques. Pour plus d’informations sur les paramètres dynamiques dans les fonctions, consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

### <a name="named-parameters"></a>paramètres nommés

Vous pouvez définir n’importe quel nombre de paramètres nommés. Vous pouvez inclure une valeur par défaut pour les paramètres nommés, comme décrit plus loin dans cette rubrique.

Vous pouvez définir des paramètres à l’intérieur des accolades à l’aide du `Param` mot clé, comme indiqué dans l’exemple de syntaxe suivant :

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

Vous pouvez également définir des paramètres en dehors des accolades sans le `Param` mot clé, comme indiqué dans l’exemple de syntaxe suivant :

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

Voici un exemple de cette syntaxe alternative.

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

Bien que la première méthode soit préférée, il n’y a aucune différence entre ces deux méthodes.

Lorsque vous exécutez la fonction, la valeur que vous fournissez pour un paramètre est assignée à une variable qui contient le nom du paramètre. La valeur de cette variable peut être utilisée dans la fonction.

L’exemple suivant est une fonction appelée `Get-SmallFiles` . Cette fonction a un `$Size` paramètre. La fonction affiche tous les fichiers qui sont plus petits que la valeur du `$Size` paramètre et exclut les répertoires :

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

Dans la fonction, vous pouvez utiliser la `$Size` variable, qui est le nom défini pour le paramètre.

Pour utiliser cette fonction, tapez la commande suivante :

```powershell
Get-SmallFiles -Size 50
```

Vous pouvez également entrer une valeur pour un paramètre nommé sans le nom du paramètre.
Par exemple, la commande suivante donne le même résultat qu’une commande qui nomme le paramètre **Size** :

```powershell
Get-SmallFiles 50
```

Pour définir une valeur par défaut pour un paramètre, tapez un signe égal et la valeur après le nom du paramètre, comme indiqué dans la variation suivante de l' `Get-SmallFiles` exemple :

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

Si vous tapez `Get-SmallFiles` sans valeur, la fonction assigne 100 à `$size` . Si vous fournissez une valeur, la fonction utilise cette valeur.

Si vous le souhaitez, vous pouvez fournir une courte chaîne d’aide qui décrit la valeur par défaut de votre paramètre, en ajoutant l’attribut **PSDefaultValue** à la description de votre paramètre et en spécifiant la propriété **Help** de **PSDefaultValue** . Pour fournir une chaîne d’aide qui décrit la valeur par défaut (100) du paramètre **Size** dans la `Get-SmallFiles` fonction, ajoutez l’attribut **PSDefaultValue** comme indiqué dans l’exemple suivant.

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

Pour plus d’informations sur la classe d’attributs **PSDefaultValue** , consultez [membres d’attribut PSDefaultValue](/dotnet/api/system.management.automation.psdefaultvalueattribute).

### <a name="positional-parameters"></a>Paramètres positionnels

Un paramètre positionnel est un paramètre sans nom de paramètre. PowerShell utilise l’ordre des valeurs de paramètre pour associer chaque valeur de paramètre à un paramètre dans la fonction.

Lorsque vous utilisez des paramètres positionnels, tapez une ou plusieurs valeurs après le nom de la fonction. Les valeurs de paramètres positionnels sont assignées à la `$args` variable tableau.
La valeur qui suit le nom de la fonction est assignée à la première position dans le `$args` tableau, `$args[0]` .

La `Get-Extension` fonction suivante ajoute l' `.txt` extension de nom de fichier à un nom de fichier que vous fournissez :

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a>Paramètres de commutateur

Un commutateur est un paramètre qui ne requiert pas de valeur. Au lieu de cela, vous tapez le nom de la fonction suivi du nom du paramètre de commutateur.

Pour définir un paramètre de commutateur, spécifiez le type `[switch]` avant le nom du paramètre, comme indiqué dans l’exemple suivant :

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

Quand vous tapez le `On` paramètre de commutateur après le nom de la fonction, la fonction affiche « activer ». Sans le paramètre de commutateur, il affiche « désactiver ».

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

Vous pouvez également assigner une valeur **booléenne** à un commutateur quand vous exécutez la fonction, comme illustré dans l’exemple suivant :

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a>Utilisation de la projection pour représenter les paramètres de commande

Vous pouvez utiliser la projection pour représenter les paramètres d’une commande. Cette fonctionnalité est introduite dans Windows PowerShell 3,0.

Utilisez cette technique dans les fonctions qui appellent des commandes dans la session. Vous n’avez pas besoin de déclarer ou d’énumérer les paramètres de commande, ou de modifier la fonction lorsque les paramètres de commande changent.

L’exemple de fonction suivant appelle l’applet de commande `Get-Command` . La commande utilise `@Args` pour représenter les paramètres de `Get-Command` .

```powershell
function Get-MyCommand { Get-Command @Args }
```

Vous pouvez utiliser tous les paramètres de `Get-Command` lorsque vous appelez la `Get-MyCommand` fonction. Les paramètres et les valeurs de paramètre sont passés à la commande à l’aide de `@Args` .

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

La `@Args` fonctionnalité utilise le `$Args` paramètre Automatic, qui représente les paramètres et les valeurs des applets de commande non déclarés des arguments restants.

Pour plus d’informations sur la projection, consultez [about_Splatting](about_Splatting.md).

## <a name="piping-objects-to-functions"></a>Canalisation des objets vers les fonctions

Toute fonction peut prendre une entrée du pipeline. Vous pouvez contrôler la façon dont une fonction traite l’entrée à partir du pipeline à l’aide de `Begin` `Process` `End` Mots clés, et. L’exemple de syntaxe suivant illustre les trois mots clés :

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

La `Begin` liste d’instructions n’est exécutée qu’une seule fois, au début de la fonction.

> [!IMPORTANT]
> Si votre fonction définit un `Begin` `Process` bloc ou, `End` tout votre code doit résider à l’intérieur de ces blocs. Aucun code n’est reconnu en dehors des blocs si l' *un* des blocs est défini.

La `Process` liste d’instructions s’exécute une fois pour chaque objet dans le pipeline.
Pendant que le `Process` bloc est en cours d’exécution, chaque objet de pipeline est affecté à la `$_` variable automatique, un objet de pipeline à la fois.

Une fois que la fonction a reçu tous les objets dans le pipeline, la `End` liste d’instructions s’exécute une fois. Si aucun `Begin` `Process` mot clé, ou n' `End` est utilisé, toutes les instructions sont traitées comme une `End` liste d’instructions.

La fonction suivante utilise le `Process` mot clé. La fonction affiche des exemples à partir du pipeline :

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

Pour illustrer cette fonction, entrez une liste de nombres séparés par des virgules, comme illustré dans l’exemple suivant :

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

Lorsque vous utilisez une fonction dans un pipeline, les objets transmis à la fonction sont assignés à la `$input` variable automatique. La fonction exécute des instructions avec le `Begin` mot clé avant que des objets proviennent du pipeline. La fonction exécute des instructions avec le `End` mot clé une fois que tous les objets ont été reçus du pipeline.

L’exemple suivant illustre la `$input` variable automatique avec `Begin` les `End` Mots clés et.

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

Si cette fonction est exécutée à l’aide du pipeline, elle affiche les résultats suivants :

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

Lorsque l' `Begin` instruction s’exécute, la fonction n’a pas d’entrée du pipeline. L' `End` instruction s’exécute une fois que la fonction a les valeurs.

Si la fonction a un `Process` mot clé, chaque objet dans `$input` est supprimé de `$input` et assigné à `$_` . L’exemple suivant contient une `Process` liste d’instructions :

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

Dans cet exemple, chaque objet qui est dirigé vers la fonction est envoyé à la `Process` liste d’instructions. Les `Process` instructions s’exécutent sur chaque objet, un objet à la fois. La `$input` variable automatique est vide lorsque la fonction atteint le `End` mot clé.

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

Pour plus d’informations, consultez [utilisation d’énumérateurs](about_Automatic_Variables.md#using-enumerators)

## <a name="filters"></a>Filtres

Un filtre est un type de fonction qui s’exécute sur chaque objet dans le pipeline. Un filtre ressemble à une fonction avec toutes ses instructions dans un `Process` bloc.

La syntaxe d’un filtre est la suivante :

```
filter [<scope:>]<name> {<statement list>}
```

Le filtre suivant prend les entrées de journal du pipeline, puis affiche l’entrée entière ou uniquement la partie message de l’entrée :

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a>Portée de la fonction

Une fonction existe dans l’étendue dans laquelle elle a été créée.

Si une fonction fait partie d’un script, la fonction est disponible pour les instructions de ce script. Par défaut, une fonction dans un script n’est pas disponible à l’invite de commandes.

Vous pouvez spécifier l’étendue d’une fonction. Par exemple, la fonction est ajoutée à la portée globale dans l’exemple suivant :

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

Quand une fonction est dans la portée globale, vous pouvez utiliser la fonction dans des scripts, dans des fonctions et sur la ligne de commande.

Les fonctions créent normalement une étendue. Les éléments créés dans une fonction, tels que les variables, existent uniquement dans l’étendue de la fonction.

Pour plus d’informations sur l’étendue dans PowerShell, consultez [about_Scopes](about_Scopes.md).

## <a name="finding-and-managing-functions-using-the-function-drive"></a>Recherche et gestion des fonctions à l’aide du lecteur function :

Toutes les fonctions et tous les filtres de PowerShell sont automatiquement stockés dans le `Function:` lecteur. Ce lecteur est exposé par le fournisseur de **fonctions** PowerShell.

Lorsque vous faites référence au `Function:` lecteur, tapez deux-points après la **fonction** , comme vous le feriez pour référencer le `C` `D` lecteur ou d’un ordinateur.

La commande suivante affiche toutes les fonctions dans la session active de PowerShell :

```powershell
Get-ChildItem function:
```

Les commandes de la fonction sont stockées sous la forme d’un bloc de script dans la propriété de définition de la fonction. Par exemple, pour afficher les commandes dans la fonction d’aide fournie avec PowerShell, tapez :

```powershell
(Get-ChildItem function:help).Definition
```

Vous pouvez également utiliser la syntaxe suivante.

```powershell
$function:help
```

Pour plus d’informations sur le `Function:` lecteur, consultez la rubrique d’aide pour le fournisseur de **fonctions** . Tapez `Get-Help Function`.

## <a name="reusing-functions-in-new-sessions"></a>Réutilisation des fonctions dans les nouvelles sessions

Quand vous tapez une fonction à l’invite de commandes PowerShell, la fonction devient partie intégrante de la session active. Elle est disponible jusqu’à la fin de la session.

Pour utiliser votre fonction dans toutes les sessions PowerShell, ajoutez la fonction à votre profil PowerShell. Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).

Vous pouvez également enregistrer votre fonction dans un fichier de script PowerShell. Tapez votre fonction dans un fichier texte, puis enregistrez le fichier avec l' `.ps1` extension de nom de fichier.

## <a name="writing-help-for-functions"></a>Écriture de l’aide pour les fonctions

L' `Get-Help` applet de commande obtient de l’aide pour les fonctions, ainsi que pour les applets de commande, les fournisseurs et les scripts. Pour obtenir de l’aide pour une fonction, tapez `Get-Help` suivi du nom de la fonction.

Par exemple, pour obtenir de l’aide pour la `Get-MyDisks` fonction, tapez :

```powershell
Get-Help Get-MyDisks
```

Vous pouvez écrire l’aide d’une fonction à l’aide de l’une des deux méthodes suivantes :

- Aide Comment-Based pour les fonctions

  Créez une rubrique d’aide en utilisant des mots clés spéciaux dans les commentaires. Pour créer une aide basée sur des commentaires pour une fonction, les commentaires doivent être placés au début ou à la fin du corps de la fonction ou sur les lignes qui précèdent le mot clé function. Pour plus d’informations sur l’aide basée sur les commentaires, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).

- Aide XML-Based pour les fonctions

  Créez une rubrique d’aide XML, telle que le type qui est généralement créé pour les applets de commande. L’aide XML est requise si vous localisez des rubriques d’aide dans plusieurs langues.

  Pour associer la fonction à la rubrique d’aide basée sur XML, utilisez le `.ExternalHelp` mot clé d’aide basée sur des commentaires. Sans ce mot clé, `Get-Help` la rubrique d’aide de la fonction est introuvable et les appels à `Get-Help` pour la fonction retournent uniquement l’aide générée automatiquement.

  Pour plus d’informations sur le `ExternalHelp` mot clé, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md). Pour plus d’informations sur l’aide XML, consultez [Comment écrire l’aide sur les applets](https://go.microsoft.com/fwlink/?LinkID=123415) de commande dans MSDN Library.

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Parameters](about_Parameters.md)

[about_Profiles](about_Profiles.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Function_provider](about_Function_provider.md)
