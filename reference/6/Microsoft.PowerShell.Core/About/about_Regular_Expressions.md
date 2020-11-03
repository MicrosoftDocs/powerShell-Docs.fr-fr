---
description: Décrit les expressions régulières dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 6112c63b6d0c1018b56df85ec6ae919a0285ffc3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206941"
---
# <a name="about-regular-expressions"></a>À propos des expressions régulières

## <a name="short-description"></a>Description courte
Décrit les expressions régulières dans PowerShell.

## <a name="long-description"></a>Description longue

> [!NOTE]
> Cet article vous montrera la syntaxe et les méthodes d’utilisation des expressions régulières dans PowerShell, mais pas toutes les syntaxes. Pour obtenir une référence plus complète, consultez le [langage des expressions régulières-aide-mémoire](/dotnet/standard/base-types/regular-expression-language-quick-reference).

Une expression régulière est un modèle utilisé pour faire correspondre du texte. Il peut être constitué de caractères littéraux, d’opérateurs et d’autres constructions.

Cet article décrit la syntaxe des expressions régulières dans PowerShell. PowerShell possède plusieurs opérateurs et applets de commande qui utilisent des expressions régulières. Pour plus d’informations sur la syntaxe et l’utilisation, consultez les liens ci-dessous.

- [Select-String](xref:Microsoft.PowerShell.Utility.Select-String)
- [-match et-Replace, opérateurs](about_Comparison_Operators.md)
- [-Split](about_Split.md)
- [Switch, instruction avec l’option-Regex](about_Switch.md)

Par défaut, les expressions régulières PowerShell ne respectent pas la casse. Chaque méthode présentée ci-dessus a une façon différente de forcer le respect de la casse.

|       Méthode       |                      Respect de la casse                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | utiliser le `-CaseSensitive` commutateur                                |
| Instruction `switch` | Utilisez l' `-casesensitive` option                            |
| opérateurs          | préfixe avec **'c'** ( `-cmatch` , `-csplit` ou `-creplace` ) |

### <a name="character-literals"></a>Littéraux de caractère

Une expression régulière peut être un caractère littéral ou une chaîne. L’expression fait en sorte que le moteur corresponde exactement au texte spécifié.

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a>Classes de caractères

Tandis que les littéraux de caractère fonctionnent si vous connaissez le modèle exact, les classes de caractères vous permettent d’être moins spécifiques.

#### <a name="character-groups"></a>Groupes de caractères

`[character group]` vous permet de faire correspondre un nombre quelconque de caractères une seule fois, tandis que `[^character group]` ne fait correspondre que les caractères qui ne sont pas dans le groupe.

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

Si votre liste de caractères à faire correspondre comprend le trait d’Union ( `-` ), il doit se trouver au début ou à la fin de la liste pour le distinguer d’une expression de plage de caractères.

#### <a name="character-ranges"></a>Plages de caractères

Un modèle peut également être une plage de caractères. Les caractères peuvent être alphabétiques `[A-Z]` , numériques `[0-9]` ou même en ASCII `[ -~]` (tous les caractères imprimables).

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a>Nombres

La `\d` classe de caractères correspond à n’importe quel chiffre décimal. Inversement, `\D` correspond à n’importe quel chiffre non décimal.

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a>Caractères alphabétiques

La `\w` classe de caractères correspond à n’importe quel caractère de mot `[a-zA-Z_0-9]` . Pour qu’il corresponde à n’importe quel caractère autre qu’un mot, utilisez `\W` .

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a>Caractères génériques

Le point ( `.` ) est un caractère générique dans les expressions régulières. Elle correspond à n’importe quel caractère, à l’exception d’un saut de ligne ( `\n` ).

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a>Espace blanc

L’espace blanc est mis en correspondance à l’aide de la `\s` classe de caractères. Tout caractère autre qu’un espace est mis en correspondance à l’aide de `\S` . Les espaces littéraux `' '` peuvent également être utilisés.

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a>Quantificateurs

Les quantificateurs contrôlent le nombre d’instances de chaque élément qui doivent être présentes dans la chaîne d’entrée.

Voici quelques-uns des quantificateurs disponibles dans PowerShell :

| Quantificateur |                Description                |
| ---------- | ----------------------------------------- |
| `*`        | Zéro, une ou plusieurs fois.                       |
| `+`        | Une ou plusieurs fois.                        |
| `?`        | Zéro ou une fois.                         |
| `{n,m}`    | Au moins `n` , mais pas plus de `m` fois. |

L’astérisque ( `*` ) correspond zéro fois ou plus à l’élément précédent. Le résultat est que même une chaîne d’entrée sans l’élément serait une correspondance.

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

Le signe plus ( `+` ) correspond une ou plusieurs fois à l’élément précédent.

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

Le point d’interrogation `?` correspond zéro ou une fois à l’élément précédent. Comme pour `*` les astérisques, elle correspond même aux chaînes où l’élément est absent.

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

Le `{n, m}` quantificateur peut être utilisé de plusieurs façons différentes pour permettre un contrôle granulaire sur le quantificateur. Le deuxième élément `m` et la virgule `,` sont facultatifs.

| Quantificateur |                Description                 |
| ---------- | ------------------------------------------ |
| `{n}`      | Correspond exactement au `n` nombre de fois.         |
| `{n,}`     | Faire correspondre au moins le `n` nombre de fois.        |
| `{n,m}`    | Mise en correspondance entre `n` et `m` nombre de fois. |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a>Ancres

Les ancres vous permettent de faire en sorte qu’une correspondance réussisse ou échoue en fonction de la position des correspondances dans la chaîne d’entrée.

Les deux ancres couramment utilisées sont `^` et `$` . Le signe insertion `^` correspond au début d’une chaîne, et `$` , qui correspond à la fin d’une chaîne. Les ancres vous permettent de faire correspondre votre texte à une position spécifique tout en ignorant les caractères indésirables.

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> Lors de la définition d’une expression régulière contenant une `$` ancre, veillez à placer l’expression régulière à l’aide de guillemets simples ( `'` ) au lieu de guillemets doubles ( `"` ), sinon PowerShell développera l’expression en tant que variable.

Lorsque vous utilisez des ancres dans PowerShell, vous devez comprendre la différence entre **Singleline** et les options d’expression régulière **multilignes** .

- **Multiligne** : le mode multiligne force `^` et `$` correspond à la fin de chaque ligne au lieu du début et de la fin de la chaîne d’entrée.
- **Singleline** : le mode Singleline traite la chaîne d’entrée comme un **Singleline** .
  Elle force le `.` caractère à correspondre à chaque caractère (y compris les nouvelles lignes), au lieu de faire correspondre tous les caractères à l’exception du saut de ligne `\n` .

Pour en savoir plus sur ces options et leur utilisation, consultez le [langage des expressions régulières-aide-mémoire](/dotnet/standard/base-types/regular-expression-language-quick-reference).

### <a name="escaping-characters"></a>Caractères d’échappement

La barre oblique inverse ( `\` ) est utilisée pour échapper les caractères afin qu’ils ne soient pas analysés par le moteur des expressions régulières.

Les caractères suivants sont réservés : `[]().\^$|?*+{}` .

Vous devez placer ces caractères dans une séquence d’échappement dans vos séquences pour les faire correspondre dans vos chaînes d’entrée.

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

Il existe une méthode statique de la classe Regex qui peut échapper du texte à votre place.

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> Cela permet d’échapper tous les caractères d’expression régulière réservés, y compris les barres obliques inverses existantes utilisées dans les classes de caractères. Veillez à l’utiliser uniquement sur la partie de votre modèle que vous devez échapper.

#### <a name="other-character-escapes"></a>Autres caractères d’échappement

Il existe également des caractères d’échappement réservés que vous pouvez utiliser pour faire correspondre les types de caractères spéciaux.

Voici quelques caractères d’échappement couramment utilisés :

|Caractère d’échappement  |Description  |
|---------|---------|
|`\t`|Correspond à une tabulation|
|`\n`|Correspond à un saut de ligne|
|`\r`|Correspond à un retour chariot|

### <a name="groups-captures-and-substitutions"></a>Groupes, captures et substitutions

Les constructions de regroupement séparent une chaîne d’entrée en sous-chaînes qui peuvent être capturées ou ignorées. Les sous-chaînes groupées sont appelées sous-expressions. Par défaut, les sous-expressions sont capturées dans des groupes numérotés, mais vous pouvez également leur attribuer des noms.

Une construction de regroupement est une expression régulière placée entre parenthèses. Tout texte correspondant à l’expression régulière comprise est capturé. L’exemple suivant permet de rompre le texte d’entrée en deux groupes de capture.

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

Utilisez la `$Matches` variable automatique **Hashtable** pour récupérer le texte capturé.
Le texte représentant la correspondance entière est stocké à la clé `0` .

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

Les captures sont stockées dans des clés numériques **entières** qui augmentent de gauche à droite. La capture `1` contient tout le texte jusqu’à ce que le nom d’utilisateur, capture `2` contienne simplement le nom d’utilisateur.

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> La `0` clé est un **entier** . Vous pouvez utiliser n’importe quelle méthode **Hashtable** pour accéder à la valeur stockée.
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a>Captures nommées

Par défaut, les captures sont stockées dans l’ordre numérique croissant, de gauche à droite.
Vous pouvez également assigner un **nom** à un groupe de capture. Ce **nom** devient une clé de la `$Matches` variable automatique **Hashtable** .

À l’intérieur d’un groupe de capture, utilisez `?<keyname>` pour stocker les données capturées sous une clé nommée.

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

L’exemple suivant stocke l’entrée de journal la plus récente dans le journal de sécurité Windows.
L’expression régulière fournie extrait le nom d’utilisateur et le domaine du message et les stocke sous les clés : **N** pour le nom et **D** pour le domaine.

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

Pour plus d’informations, consultez [constructions de regroupement dans les expressions régulières](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

#### <a name="substitutions-in-regular-expressions"></a>Substitutions dans les expressions régulières

L’utilisation des expressions régulières avec l' `-replace` opérateur vous permet de remplacer le texte de manière dynamique à l’aide du texte capturé.

`<input> -replace <original>, <substitute>`

- `<input>`: Chaîne à rechercher
- `<original>`: Expression régulière utilisée pour rechercher la chaîne d’entrée
- `<substitute>`: Expression de substitution d’expression régulière pour remplacer les correspondances trouvées dans la chaîne d’entrée.

> [!NOTE]
> Les `<original>` `<substitute>` opérandes et sont soumis aux règles du moteur des expressions régulières, telles que la séquence d’échappement des caractères.

Les groupes de capture peuvent être référencés dans la `<substitute>` chaîne. La substitution est effectuée en utilisant le `$` caractère qui précède l’identificateur de groupe.

Deux méthodes pour référencer des groupes de capture sont par **numéro** et par **nom** .

- Par **nombre** : les groupes de capture sont numérotés de gauche à droite.

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- Par **nom** , les groupes de capture peuvent également être référencés par nom.

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

L' `$&` expression représente tout le texte mis en correspondance.

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> Étant donné que le `$` caractère est utilisé dans l’extension de chaîne, vous devez utiliser des chaînes littérales avec substitution, ou placer le caractère dans une séquence d’échappement `$` quand vous utilisez des guillemets doubles.
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> En outre, si vous souhaitez que le soit `$` un caractère littéral, utilisez à la `$$` place des caractères d’échappement normaux. Quand vous utilisez des guillemets doubles, échapper toujours toutes les instances de `$` pour éviter une substitution incorrecte.
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

Pour plus d’informations, consultez [substitutions dans les expressions régulières](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Voir aussi

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Operators](about_Operators.md)
