---
description: Explique comment ajouter des paramètres aux fonctions avancées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 2a5b13475dd648a9f778d23b4089da00351b237c
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "93208910"
---
# <a name="about-functions-advanced-parameters"></a>À propos des paramètres avancés des fonctions

## <a name="short-description"></a>Description courte

Explique comment ajouter des paramètres aux fonctions avancées.

## <a name="long-description"></a>Description longue

Vous pouvez ajouter des paramètres aux fonctions avancées que vous écrivez et utiliser des attributs et des arguments de paramètre pour limiter les valeurs de paramètres que les utilisateurs de fonction envoient avec le paramètre.

Les paramètres que vous ajoutez à votre fonction sont accessibles aux utilisateurs en plus des paramètres communs que PowerShell ajoute automatiquement à toutes les applets de commande et fonctions avancées. Pour plus d’informations sur les paramètres communs de PowerShell, consultez [about_CommonParameters](about_CommonParameters.md).

À compter de PowerShell 3,0, vous pouvez utiliser la projection avec `@Args` pour représenter les paramètres dans une commande. La projection est valide sur les fonctions simples et avancées. Pour plus d’informations, consultez [about_Functions](about_Functions.md) et [about_Splatting](about_Splatting.md).

## <a name="type-conversion-of-parameter-values"></a>Conversion de type de valeurs de paramètre

Quand vous fournissez des chaînes en tant qu’arguments à des paramètres qui attendent un type différent, PowerShell convertit implicitement les chaînes en type de cible de paramètre.
Les fonctions avancées effectuent l’analyse indifférente de la culture des valeurs de paramètre.

En revanche, une conversion dépendante de la culture est effectuée lors de la liaison de paramètre pour les applets de commande compilées.

Dans cet exemple, nous créons une applet de commande et une fonction de script qui prennent un `[datetime]` paramètre. La culture actuelle est modifiée pour utiliser les paramètres allemands.
Une date au format allemand est passée au paramètre.

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

Comme indiqué ci-dessus, les applets de commande utilisent l’analyse dépendante de la culture pour convertir la chaîne.

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

Les fonctions avancées utilisent l’analyse dite indifférente de la culture, ce qui provoque l’erreur suivante.

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a>Paramètres statiques

Les paramètres statiques sont des paramètres qui sont toujours disponibles dans la fonction.
La plupart des paramètres dans les applets de commande et les scripts PowerShell sont des paramètres statiques.

L’exemple suivant illustre la déclaration d’un paramètre **ComputerName** qui présente les caractéristiques suivantes :

- Il est obligatoire (obligatoire).
- Il prend en entrée le pipeline.
- Il prend un tableau de chaînes comme entrée.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>Attributs des paramètres

Cette section décrit les attributs que vous pouvez ajouter aux paramètres de fonction.

Tous les attributs sont facultatifs. Toutefois, si vous omettez l’attribut **CmdletBinding** , pour être reconnu comme une fonction avancée, la fonction doit inclure l’attribut **Parameter** .

Vous pouvez ajouter un ou plusieurs attributs dans chaque déclaration de paramètre. Il n’existe aucune limite quant au nombre d’attributs que vous pouvez ajouter à une déclaration de paramètre.

### <a name="parameter-attribute"></a>Attribut de paramètre

L’attribut **Parameter** est utilisé pour déclarer les attributs des paramètres de fonction.

L’attribut **Parameter** est facultatif et vous pouvez l’omettre si aucun des paramètres de vos fonctions n’a besoin d’attributs. Toutefois, pour être reconnu comme une fonction avancée, plutôt que comme une fonction simple, une fonction doit avoir l’attribut **CmdletBinding** ou l’attribut **Parameter** , ou les deux.

L’attribut **Parameter** possède des arguments qui définissent les caractéristiques du paramètre, par exemple si le paramètre est obligatoire ou facultatif.

Utilisez la syntaxe suivante pour déclarer l’attribut de **paramètre** , un argument et une valeur d’argument. Les parenthèses qui entourent l’argument et sa valeur doivent suivre le **paramètre** sans espace intermédiaire.

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

Utilisez des virgules pour séparer les arguments entre parenthèses. Utilisez la syntaxe suivante pour déclarer deux arguments de l’attribut **Parameter** .

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

Les types d’arguments booléens de l’attribut **Parameter** ont par défaut la **valeur false** en cas d’omission de l’attribut **Parameter** . Définissez la valeur de l’argument sur `$true` ou répertoriez simplement l’argument par nom. Par exemple, les attributs de **paramètre** suivants sont équivalents.

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

Si vous utilisez l’attribut de **paramètre** sans arguments, comme alternative à l’utilisation de l’attribut **CmdletBinding** , les parenthèses qui suivent le nom de l’attribut sont toujours requises.

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>Argument obligatoire

L' `Mandatory` argument indique que le paramètre est obligatoire. Si cet argument n’est pas spécifié, le paramètre est facultatif.

L’exemple suivant déclare le paramètre **ComputerName** . Elle utilise l' `Mandatory` argument pour rendre le paramètre obligatoire.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Argument position

L' `Position` argument détermine si le nom du paramètre est requis lorsque le paramètre est utilisé dans une commande. Lorsqu’une déclaration de paramètre inclut l' `Position` argument, le nom du paramètre peut être omis et PowerShell identifie la valeur du paramètre sans nom par sa position, ou ordre, dans la liste des valeurs de paramètre sans nom dans la commande.

Si l' `Position` argument n’est pas spécifié, le nom du paramètre, ou un alias ou une abréviation de nom de paramètre, doit précéder la valeur de paramètre chaque fois que le paramètre est utilisé dans une commande.

Par défaut, tous les paramètres de fonction sont positionnels. PowerShell attribue des numéros de position aux paramètres dans l’ordre dans lequel les paramètres sont déclarés dans la fonction. Pour désactiver cette fonctionnalité, définissez la valeur de l' `PositionalBinding` argument de l’attribut **CmdletBinding** sur `$False` . L' `Position` argument est prioritaire sur la valeur de l' `PositionalBinding` argument de l’attribut **CmdletBinding** . Pour plus d’informations, consultez `PositionalBinding` dans [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).

La valeur de l' `Position` argument est spécifiée sous la forme d’un entier. Une valeur position égale à **0** représente la première position dans la commande, la valeur position **1** représente la deuxième position dans la commande, et ainsi de suite.

Si une fonction n’a pas de paramètres positionnels, PowerShell affecte des positions à chaque paramètre en fonction de l’ordre dans lequel les paramètres sont déclarés.
Toutefois, il est recommandé de ne pas compter sur cette attribution. Lorsque vous souhaitez que les paramètres soient positionnels, utilisez l' `Position` argument.

L’exemple suivant déclare le paramètre **ComputerName** . Elle utilise l' `Position` argument ayant la valeur **0**. Par conséquent, lorsque `-ComputerName` est omis de la commande, sa valeur doit être la première ou la seule valeur de paramètre sans nom dans la commande.

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>Argument ParameterSetName

L' `ParameterSetName` argument spécifie le jeu de paramètres auquel appartient un paramètre. Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres définis par la fonction. Par conséquent, pour être unique, chaque jeu de paramètres doit avoir au moins un paramètre qui n’est pas membre d’un autre jeu de paramètres.

> [!NOTE]
> Pour une applet de commande ou une fonction, il existe une limite de 32 jeux de paramètres.

L’exemple suivant déclare un paramètre **ComputerName** dans le `Computer` jeu de paramètres, un paramètre **username** dans le `User` jeu de paramètres et un paramètre **Summary** dans les deux jeux de paramètres.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

Vous ne pouvez spécifier qu’une seule `ParameterSetName` valeur dans chaque argument et un seul `ParameterSetName` argument dans chaque attribut de **paramètre** . Pour indiquer qu’un paramètre apparaît dans plusieurs jeux de paramètres, ajoutez des attributs de **paramètres** supplémentaires.

L’exemple suivant ajoute explicitement le paramètre **Summary** aux `Computer` jeux de `User` paramètres et. Le paramètre **Summary** est facultatif dans le `Computer` jeu de paramètres et obligatoire dans le `User` jeu de paramètres.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

Pour plus d’informations sur les jeux de paramètres, consultez [à propos des jeux de paramètres](about_parameter_sets.md).

#### <a name="valuefrompipeline-argument"></a>Argument ValueFromPipeline

L' `ValueFromPipeline` argument indique que le paramètre accepte l’entrée d’un objet Pipeline. Spécifiez cet argument si la fonction accepte la totalité de l’objet, pas seulement une propriété de l’objet.

L’exemple suivant déclare un paramètre **ComputerName** obligatoire et accepte un objet qui est passé à la fonction à partir du pipeline.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>Argument ValueFromPipelineByPropertyName

L' `ValueFromPipelineByPropertyName` argument indique que le paramètre accepte l’entrée d’une propriété d’un objet Pipeline. La propriété de l’objet doit avoir le même nom ou alias que le paramètre.

Par exemple, si la fonction a un paramètre **ComputerName** et que l’objet Redirigé a une propriété **ComputerName** , la valeur de la propriété **ComputerName** est assignée au paramètre **ComputerName** de la fonction.

L’exemple suivant déclare un paramètre **ComputerName** obligatoire et accepte l’entrée de la propriété **ComputerName** de l’objet qui est transmise à la fonction via le pipeline.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de _liaison différée_ sur le paramètre.
>
> Le bloc _de script de liaison différée_ est exécuté automatiquement pendant la **ParameterBinding**. Le résultat est lié au paramètre. La liaison différée ne fonctionne pas pour les paramètres définis en tant que type `ScriptBlock` ou `System.Object` . Le bloc de script est passé _sans_ être appelé.
>
> Vous pouvez en savoir plus sur _les blocs de script de liaison différée_ ici [about_Script_Blocks. MD](about_Script_Blocks.md).

#### <a name="valuefromremainingarguments-argument"></a>Argument ValueFromRemainingArguments

L' `ValueFromRemainingArguments` argument indique que le paramètre accepte toutes les valeurs du paramètre de la commande qui ne sont pas assignées à d’autres paramètres de la fonction.

L’exemple suivant déclare un paramètre de **valeur** obligatoire et un paramètre **restant** qui accepte toutes les valeurs de paramètres restantes soumises à la fonction.

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> Avant PowerShell 6,2, la collection **ValueFromRemainingArguments** était jointe en tant qu’entité unique sous l’index **0**.

#### <a name="helpmessage-argument"></a>Argument HelpMessage

L' `HelpMessage` argument spécifie une chaîne qui contient une brève description du paramètre ou de sa valeur. PowerShell affiche ce message dans l’invite qui s’affiche lorsqu’il manque une valeur de paramètre obligatoire dans une commande. Cet argument n’a aucun effet sur les paramètres facultatifs.

L’exemple suivant déclare un paramètre **ComputerName** obligatoire et un message d’aide qui explique la valeur de paramètre attendue.

S’il n’existe aucune autre syntaxe d' [aide basée sur les commentaires](./about_comment_based_help.md) pour la fonction (par exemple, `.SYNOPSIS` ), ce message s’affiche également dans la `Get-Help` sortie.

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Alias (attribut)

L’attribut **alias** établit un autre nom pour le paramètre.
Il n’existe aucune limite quant au nombre d’alias que vous pouvez assigner à un paramètre.

L’exemple suivant montre une déclaration de paramètre qui ajoute les alias **CN** et **MachineName** au paramètre **ComputerName** obligatoire.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>Attribut SupportsWildcards

L’attribut **SupportsWildcards** est utilisé pour indiquer que le paramètre accepte les valeurs de caractères génériques. L’exemple suivant illustre une déclaration de paramètre pour un paramètre de **chemin d’accès** obligatoire qui prend en charge les valeurs de caractère générique.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

L’utilisation de cet attribut n’active pas automatiquement la prise en charge des caractères génériques. Le développeur d’applets de commande doit implémenter le code pour gérer l’entrée de caractères génériques. Les caractères génériques pris en charge peuvent varier en fonction de l’API ou du fournisseur PowerShell sous-jacent. Pour plus d’informations, consultez [about_Wildcards](about_Wildcards.md).

### <a name="parameter-and-variable-validation-attributes"></a>Attributs de validation des paramètres et des variables

Les attributs de validation dirigent PowerShell pour tester les valeurs de paramètres que les utilisateurs envoient lorsqu’ils appellent la fonction Advanced. Si les valeurs de paramètre échouent au test, une erreur est générée et la fonction n’est pas appelée. La validation de paramètre s’applique uniquement à l’entrée fournie et toutes les autres valeurs telles que les valeurs par défaut ne sont pas validées.

Vous pouvez également utiliser les attributs de validation pour limiter les valeurs que les utilisateurs peuvent spécifier pour les variables. Quand vous utilisez un convertisseur de type avec un attribut de validation, le convertisseur de type doit être défini avant l’attribut.

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>Attribut de validation AllowNull a

L’attribut **AllowNull a** permet à la valeur d’un paramètre obligatoire d’être `$null` . L’exemple suivant déclare un paramètre **ComputerInfo** Hashtable qui peut avoir une valeur **null** .

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> L’attribut **AllowNull a** ne fonctionne pas si le convertisseur de type est défini sur String, car le type chaîne n’accepte pas de valeur null. Vous pouvez utiliser l’attribut **AllowEmptyString** pour ce scénario.

### <a name="allowemptystring-validation-attribute"></a>Attribut de validation AllowEmptyString

L’attribut **AllowEmptyString** permet à la valeur d’un paramètre obligatoire d’être une chaîne vide ( `""` ). L’exemple suivant déclare un paramètre **ComputerName** qui peut avoir une valeur de chaîne vide.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>Attribut de validation AllowEmptyCollection

L’attribut **AllowEmptyCollection** permet à la valeur d’un paramètre obligatoire d’être une collection vide `@()` . L’exemple suivant déclare un paramètre **ComputerName** qui peut avoir une valeur de collection vide.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>Attribut de validation ValidateCount

L’attribut **ValidateCount** spécifie le nombre minimal et maximal de valeurs de paramètre acceptées par un paramètre. PowerShell génère une erreur si le nombre de valeurs de paramètre dans la commande qui appelle la fonction est en dehors de cette plage.

La déclaration de paramètre suivante crée un paramètre **ComputerName** qui prend une à cinq valeurs de paramètre.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>Attribut de validation ValidateLength

L’attribut **ValidateLength** spécifie le nombre minimal et le nombre maximal de caractères dans une valeur de paramètre ou de variable. PowerShell génère une erreur si la longueur d’une valeur spécifiée pour un paramètre ou une variable est en dehors de la plage.

Dans l’exemple suivant, chaque nom d’ordinateur doit comporter un à dix caractères.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

Dans l’exemple suivant, la valeur de la variable `$number` doit être au minimum d’un caractère et comporter un maximum de dix caractères.

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> Dans cet exemple, la valeur de `01` est incluse entre guillemets simples. L’attribut **ValidateLength** n’accepte pas de nombre sans encapsuler les guillemets.

### <a name="validatepattern-validation-attribute"></a>Attribut de validation ValidatePattern

L’attribut **ValidatePattern** spécifie une expression régulière qui est comparée à la valeur du paramètre ou de la variable. PowerShell génère une erreur si la valeur ne correspond pas au modèle d’expression régulière.

Dans l’exemple suivant, la valeur de paramètre doit contenir un nombre à quatre chiffres, et chaque chiffre doit être un nombre zéro à neuf.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

Dans l’exemple suivant, la valeur de la variable `$number` doit être exactement un nombre à quatre chiffres, et chaque chiffre doit être un nombre zéro à neuf.

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>Attribut de validation ValidateRange

L’attribut **ValidateRange** spécifie une plage numérique ou une valeur d’énumération **ValidateRangeKind** pour chaque valeur de paramètre ou de variable.
PowerShell génère une erreur si une valeur est en dehors de cette plage.

L’énumération **ValidateRangeKind** autorise les valeurs suivantes :

- **Positif** : nombre supérieur à zéro.
- **Negative** : nombre inférieur à zéro.
- Non **positif** : nombre inférieur ou égal à zéro.
- Non **négatif** : nombre supérieur ou égal à zéro.

Dans l’exemple suivant, la valeur du paramètre **tentatives** doit être comprise entre zéro et dix.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

Dans l’exemple suivant, la valeur de la variable `$number` doit être comprise entre zéro et dix.

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

Dans l’exemple suivant, la valeur de la variable `$number` doit être supérieure à zéro.

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>Attribut de validation ValidateScript

L’attribut **ValidateScript** spécifie un script utilisé pour valider une valeur de paramètre ou de variable. PowerShell dirige la valeur vers le script et génère une erreur si le script retourne `$false` ou si le script lève une exception.

Lorsque vous utilisez l’attribut **ValidateScript** , la valeur qui est validée est mappée à la `$_` variable. Vous pouvez utiliser la `$_` variable pour faire référence à la valeur dans le script.

Dans l’exemple suivant, la valeur du paramètre **EventDate** doit être supérieure ou égale à la date actuelle.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

Dans l’exemple suivant, la valeur de la variable `$date` doit être supérieure ou égale à la date et à l’heure actuelles.

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> Si vous utilisez **ValidateScript** , vous ne pouvez pas passer une `$null` valeur au paramètre. Lorsque vous transmettez une valeur null, **ValidateScript** ne peut pas valider l’argument.

### <a name="validateset-attribute"></a>Attribut ValidateSet

L’attribut **ValidateSet** spécifie un ensemble de valeurs valides pour un paramètre ou une variable et active la saisie semi-automatique via la touche Tab. PowerShell génère une erreur si la valeur d’un paramètre ou d’une variable ne correspond pas à une valeur de l’ensemble. Dans l’exemple suivant, la valeur du paramètre de **détail** peut uniquement être faible, moyenne ou élevée.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

Dans l’exemple suivant, la valeur de la variable `$flavor` doit être Chocolate, fraise ou vanille.

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

La validation se produit chaque fois que cette variable est assignée même dans le script. Par exemple, le code suivant génère une erreur au moment de l’exécution :

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>Valeurs validateSet dynamiques

Vous pouvez utiliser une **classe** pour générer dynamiquement les valeurs de **ValidateSet** au moment de l’exécution. Dans l’exemple suivant, les valeurs valides pour la variable `$Sound` sont générées à l’aide d’une **classe** nommée **SoundNames** qui recherche les fichiers audio disponibles dans trois chemins de système de fichiers :

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

La `[SoundNames]` classe est ensuite implémentée en tant que valeur **ValidateSet** dynamique comme suit :

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a>Attribut de validation ValidateNotNull

L’attribut **ValidateNotNull** spécifie que la valeur du paramètre ne peut pas être `$null` . PowerShell génère une erreur si la valeur du paramètre est `$null` .

L’attribut **ValidateNotNull** est conçu pour être utilisé lorsque le paramètre est facultatif et que le type n’est pas défini ou possède un convertisseur de type qui ne peut pas convertir implicitement une valeur NULL comme **Object**. Si vous spécifiez un type qui convertit implicitement une valeur null telle qu’une **chaîne** , la valeur null est convertie en une chaîne vide même lors de l’utilisation de l’attribut **ValidateNotNull** . Pour ce scénario, utilisez **ValidateNotNullOrEmpty**

Dans l’exemple suivant, la valeur du paramètre **ID** ne peut pas être `$null` .

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>Attribut de validation ValidateNotNullOrEmpty

L’attribut **ValidateNotNullOrEmpty** spécifie que la valeur du paramètre ne peut pas être `$null` et ne peut pas être une chaîne vide ( `""` ). PowerShell génère une erreur si le paramètre est utilisé dans un appel de fonction, mais que sa valeur est `$null` , une chaîne vide ( `""` ) ou un tableau vide `@()` .

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>Attribut de validation ValidateDrive

L’attribut **ValidateDrive** spécifie que la valeur de paramètre doit représenter le chemin d’accès, qui fait référence à des lecteurs autorisés uniquement. PowerShell génère une erreur si la valeur du paramètre fait référence à des lecteurs autres que le autorisé. L’existence du chemin d’accès, à l’exception du lecteur lui-même, n’est pas vérifiée.

Si vous utilisez un chemin d’accès relatif, le lecteur actif doit figurer dans la liste des lecteurs autorisés.

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>Attribut de validation ValidateUserDrive

L’attribut **ValidateUserDrive** spécifie que la valeur du paramètre doit représenter le chemin d’accès, qui fait référence au `User` lecteur. PowerShell génère une erreur si le chemin d’accès fait référence à un autre lecteur. L’attribut validation vérifie uniquement l’existence de la partie lecteur du chemin d’accès.

Si vous utilisez le chemin d’accès relatif, le lecteur actif doit être `User` .

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

Vous pouvez définir `User` des lecteurs dans des configurations de session d’administration (JEA) juste assez. Pour cet exemple, nous créons le lecteur User :.

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a>Attribut de validation ValidateTrustedData

Cet attribut a été ajouté dans PowerShell 6.1.1.

À ce stade, l’attribut est utilisé en interne par PowerShell lui-même et n’est pas destiné à une utilisation externe.

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’une applet de commande, d’une fonction ou d’un script qui sont disponibles uniquement dans certaines conditions.

Par exemple, plusieurs applets de commande de fournisseur ont des paramètres qui sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur du fournisseur ou dans un chemin d’accès particulier au lecteur du fournisseur. Par exemple, le paramètre d' **encodage** est disponible sur les `Add-Content` `Get-Content` `Set-Content` applets de commande, et uniquement lorsqu’il est utilisé dans un lecteur du système de fichiers.

Vous pouvez également créer un paramètre qui apparaît uniquement lorsqu’un autre paramètre est utilisé dans la commande de fonction ou lorsqu’un autre paramètre a une certaine valeur.

Les paramètres dynamiques peuvent être utiles, mais ils peuvent être utilisés uniquement lorsque cela est nécessaire, car ils peuvent être difficiles à découvrir par les utilisateurs. Pour trouver un paramètre dynamique, l’utilisateur doit se trouver dans le chemin d’accès du fournisseur, utiliser le paramètre **argumentlist** de l’applet de commande `Get-Command` ou utiliser le paramètre **path** de `Get-Help` .

Pour créer un paramètre dynamique pour une fonction ou un script, utilisez le `DynamicParam` mot clé.

La syntaxe est la suivante :

`DynamicParam {<statement-list>}`

Dans la liste instruction, utilisez une `If` instruction pour spécifier les conditions dans lesquelles le paramètre est disponible dans la fonction.

Utilisez l' `New-Object` applet de commande pour créer un objet **System. Management. Automation. RuntimeDefinedParameter** pour représenter le paramètre et spécifier son nom.

Vous pouvez utiliser une `New-Object` commande pour créer un objet **System. Management. Automation. ParameterAttribute** pour représenter les attributs du paramètre, par exemple **obligatoire** , **position** ou **ValueFromPipeline** ou son jeu de paramètres.

L’exemple suivant montre un exemple de fonction avec des paramètres standard nommés **Name** et **path** , ainsi qu’un paramètre dynamique facultatif nommé **DP1**. Le paramètre **DP1** est dans le `PSet1` jeu de paramètres et a un type de `Int32` .
Le paramètre **DP1** est disponible dans la `Get-Sample` fonction uniquement lorsque la valeur du paramètre **path** commence par `HKLM:` , ce qui indique qu’il est utilisé dans le `HKEY_LOCAL_MACHINE` lecteur du Registre.

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

Pour plus d’informations, consultez [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).

## <a name="switch-parameters"></a>Paramètres de commutateur

Les paramètres de commutateur sont des paramètres sans valeur de paramètre. Ils sont efficaces uniquement lorsqu’ils sont utilisés et n’ont qu’un seul effet.

Par exemple, le paramètre **Noprofiler** de **powershell.exe** est un paramètre de commutateur.

Pour créer un paramètre de commutateur dans une fonction, spécifiez le `Switch` type dans la définition de paramètre.

Par exemple :

```powershell
Param([Switch]<ParameterName>)
```

Vous pouvez également utiliser une autre méthode :

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

Les paramètres de commutateur sont faciles à utiliser et sont préférés aux paramètres booléens, qui ont une syntaxe plus difficile.

Par exemple, pour utiliser un paramètre de commutateur, l’utilisateur tape le paramètre dans la commande.

`-IncludeAll`

Pour utiliser un paramètre booléen, l’utilisateur tape le paramètre et une valeur booléenne.

`-IncludeAll:$true`

Lorsque vous créez des paramètres de commutateur, choisissez le nom du paramètre avec soin. Assurez-vous que le nom du paramètre communique l’effet du paramètre à l’utilisateur.
Évitez les termes ambigus, tels que le **filtre** ou le **maximum** qui peut impliquer une valeur, est requis.

## <a name="argumentcompleter-attribute"></a>Attribut ArgumentCompleter

L’attribut **ArgumentCompleter** vous permet d’ajouter des valeurs de saisie semi-automatique par tabulation à un paramètre spécifique. Un attribut **ArgumentCompleter** doit être défini pour chaque paramètre nécessitant la saisie semi-automatique par tabulation. Comme pour **DynamicParameters** , les valeurs disponibles sont calculées au moment de l’exécution lorsque l’utilisateur appuie sur la touche <kbd>Tab</kbd> après le nom du paramètre.

Pour ajouter un attribut **ArgumentCompleter** , vous devez définir un bloc de script qui détermine les valeurs. Le bloc de script doit prendre les paramètres suivants dans l’ordre indiqué ci-dessous. Les noms du paramètre n’ont pas d’importance, car les valeurs sont fournies à l’emplacement.

La syntaxe est la suivante :

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a>Bloc de script ArgumentCompleter

Les paramètres de bloc de script sont définis avec les valeurs suivantes :

- `$commandName` (Position 0)-ce paramètre est défini sur le nom de la commande pour laquelle le bloc de script fournit la saisie semi-automatique par tabulation.
- `$parameterName` (Position 1)-ce paramètre est défini sur le paramètre dont la valeur nécessite la saisie semi-automatique par tabulation.
- `$wordToComplete` (Position 2)-ce paramètre est défini sur la valeur que l’utilisateur a fournie avant d’appuyer sur la touche <kbd>Tab</kbd>. Votre bloc de script doit utiliser cette valeur pour déterminer les valeurs de saisie semi-automatique de l’onglet.
- `$commandAst` (Position 3)-ce paramètre est défini sur l’arborescence de syntaxe abstraite (AST) pour la ligne d’entrée actuelle. Pour plus d’informations, consultez la [classe AST](/dotnet/api/system.management.automation.language.ast).
- `$fakeBoundParameters` (Position 4)-ce paramètre est défini sur une valeur Hashtable contenant le `$PSBoundParameters` pour l’applet de commande, avant que l’utilisateur ait appuyé sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

Le bloc de script **ArgumentCompleter** doit dérouler les valeurs à l’aide du pipeline, tel que `ForEach-Object` , `Where-Object` ou une autre méthode appropriée.
Le retour d’un tableau de valeurs amène PowerShell à traiter l’intégralité du tableau comme **une** valeur de saisie semi-automatique de tabulation.

L’exemple suivant ajoute la saisie semi-automatique via la touche Tab au paramètre **value** . Si seul le paramètre **value** est spécifié, toutes les valeurs possibles, ou arguments, pour **value** sont affichées. Lorsque le paramètre de **type** est spécifié, le paramètre de **valeur** affiche uniquement les valeurs possibles pour ce type.

En outre, l' `-like` opérateur s’assure que si l’utilisateur tape la commande suivante et utilise la saisie semi-automatique via la <kbd>touche Tab</kbd> , seul **Apple** est retourné.

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
