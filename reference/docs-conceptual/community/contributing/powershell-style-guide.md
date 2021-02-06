---
title: Guide de style pour la documentation PowerShell
description: Cet article présente les règles de style pour l’écriture de la documentation de PowerShell.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99598548"
---
# <a name="powershell-docs-style-guide"></a>Guide de style pour la documentation PowerShell

Cet article donne des conseils de style propres au contenu PowerShell-Docs, Il s’appuie sur les informations présentées dans la [vue d’ensemble](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Terminologie des produits

Il existe plusieurs variantes de PowerShell.

- **PowerShell** : terme par défaut. Nous considérons PowerShell 7 et les versions ultérieures comme un véritable PowerShell.
- **PowerShell Core** : PowerShell reposant sur .NET Core. L’utilisation du terme **Core** doit être limitée aux cas où il est nécessaire de le différencier de Windows PowerShell.
- **Windows PowerShell** : PowerShell reposant sur .NET Framework. Windows PowerShell est fourni uniquement sur Windows et requiert l’infrastructure complète.

  En général, les références à « Windows PowerShell » dans la documentation peuvent être remplacées par _PowerShell_.
  « Windows PowerShell » doit être utilisé lorsque le comportement spécifique à _Windows PowerShell_ est abordé.

Produits connexes

- **Visual Studio code (vs code)** : il s’agit de l’éditeur libre et open source de Microsoft. Lors de la première mention, le nom complet doit être utilisé. Après cela, vous pouvez utiliser **VS Code**. N’utilisez pas « VSCode ».
- **Extension PowerShell pour Visual Studio Code** : l’extension active VS Code dans l’IDE préféré pour PowerShell. Lors de la première mention, le nom complet doit être utilisé. Après cela, vous pouvez utiliser **Extension PowerShell**.
- **Azure PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer les services Azure.
- **Azure Stack PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer la solution cloud hybride de Microsoft.

## <a name="markdown-specifics"></a>Spécificités de Markdown

Microsoft Open Publishing System (OPS), qui nous permet de créer notre documentation, utilise [markdig][] pour traiter les documents Markdown. Markdig analyse les documents suivant les règles de la dernière spécification [CommonMark][].

La nouvelle spécification CommonMark est plus stricte sur la construction de certains éléments Markdown. Portez une attention particulière aux informations fournies dans ce document.

### <a name="blank-lines-spaces-and-tabs"></a>Lignes vides, espaces et tabulations

Les lignes vides signalent également la fin d’un bloc en Markdown. Il doit y avoir un seul espace entre les blocs Markdown de différents types (par exemple, entre un paragraphe et une liste ou un en-tête).

Plusieurs lignes vides consécutives sont rendues sous la forme d’une seule ligne vide en HTML. Ils n’ont aucun effet.
Dans un bloc de code, les lignes vides consécutives rompent le bloc de code.

Supprimez les espaces supplémentaires à la fin des lignes.

> [!NOTE]
> L’espacement est significatif en Markdown. Utilisez toujours des espaces plutôt que des tabulations fixes. Les espaces de fin peuvent modifier le rendu Markdown.

### <a name="titles-and-headings"></a>Titres et en-têtes

Utilisez uniquement des [en-têtes ATX][atx] (de style #, par opposition aux en-têtes de style `=` ou `-`).

- Seule la première lettre des phrases, des noms propres, des titres et des en-têtes doit être en majuscule.
- Il doit y avoir un seul espace entre le `#` et la première lettre du titre.
- Les en-têtes doivent être délimités par une seule ligne vide.
- Un document ne peut contenir qu’un seul titre H1.
- Les niveaux d’en-têtes doivent se suivre par incréments de un, Ne pas ignorer les niveaux
- N’utilisez pas le balisage gras ou autre dans les en-têtes

### <a name="limit-line-length-to-100-characters"></a>Limiter la longueur de ligne à 100 caractères

Cette règle s’applique aux articles conceptuels et aux informations de référence sur les cmdlets. Le fait de limiter la longueur de ligne améliore la lisibilité des différences et de l’historique de Git. Elle permet également aux autres rédacteurs d’apporter plus facilement leur contribution.

Utilisez l’extension [Reflow Markdown][reflow] dans Visual Studio Code pour ajuster dynamiquement les paragraphes en fonction de la longueur de ligne prescrite.

Les rubriques About_ sont limitées à 80 caractères. Pour plus d’informations, consultez [mise en forme des fichiers de about_](#formatting-about_-files).

### <a name="lists"></a>Listes

Si votre liste contient plusieurs phrases ou paragraphes, envisagez d’utiliser un en-tête de sous-niveau plutôt qu’une liste.

Les listes doivent être délimitées par une seule ligne vide.

#### <a name="unordered-lists"></a>Listes non triées

Ne terminez pas les éléments de liste par un point, sauf s’ils contiennent plusieurs phrases. Utilisez le caractère de trait d’union (`-`) comme puce pour les éléments de liste afin d’éviter toute confusion avec les balises de type gras ou en italique qui utilisent l’astérisque [`*`]. Pour inclure un paragraphe ou d’autres éléments sous un élément de puce, insérez un saut de ligne et alignez le retrait avec le premier caractère après la puce.

Par exemple :

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

Il s’agit d’une liste qui contient des éléments enfants sous un élément de puce.

- Premier élément de puce

  Phrase expliquant la première puce.

  - Élément de puce enfant

    Phrase expliquant la puce enfant.

- Deuxième élément de puce
- Troisième élément de puce

#### <a name="ordered-lists"></a>Listes triées

Pour inclure un paragraphe ou d’autres éléments sous un élément numéroté, alignez le retrait avec le premier caractère après le numéro d’élément. Tous les éléments d’une liste numérotée doivent utiliser le numéro `1.` sans incrémentation. Le rendu Markdown incrémente automatiquement la valeur, ce qui permet de réorganiser plus facilement les éléments et standardise la mise en retrait du contenu subordonné.

Par exemple :

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

Le Markdown résultant est rendu de la façon suivante :

1. Pour le premier élément, insérez un seul espace après le 1. Les phrases longues doivent comporter un retour automatique à la ligne et être alignées avec le premier caractère après le marqueur de liste numérotée.

   Pour inclure un deuxième élément (comme celui-ci), insérez un saut de ligne après le premier et alignez les mises en retrait. Le retrait du deuxième élément doit être aligné avec le premier caractère après le marqueur de liste numérotée. Pour les éléments à un seul chiffre, comme celui-ci, la mise en retrait s’effectue vers la colonne 4. Pour les éléments à deux chiffres, par exemple le numéro d’élément 10, elle s’effectue vers la colonne 5.

1. L’élément numéroté suivant commence ici.

### <a name="images"></a>Images

Voici la syntaxe permettant d’inclure une image :

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

Où `alt text` est une brève description de l’image et `<folder path>` le chemin relatif de l’image. Le texte de remplacement est nécessaire pour les lecteurs d’écran des personnes déficientes visuelles.

Les images doivent être stockées dans un `media/<article-name>` dossier dans le dossier contenant l’article.
Ne partagez pas d’images entre des articles. Créez un dossier qui correspond au nom de fichier de votre article sous le dossier `media`. Copiez les images pour cet article dans ce nouveau dossier. Si une image est utilisée par plusieurs articles, chaque dossier d’images doit avoir une copie de ce fichier d’image. Cette pratique permet d’éviter que la modification d’une image dans un article affecte un autre article.

Les types de fichiers image suivants sont pris en charge : `*.png` , `*.gif` , `*.jpeg` , `*.jpg` , `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Extensions Markdown prises en charge par Open Publishing

Le [Pack de création Microsoft docs](/contribute/how-to-write-docs-auth-pack) contient des outils qui prennent en charge des fonctionnalités propres à notre système de publication. Les alertes sont une extension de démarque pour créer des citations qui s’affichent sur docs.microsoft.com avec des couleurs et des icônes qui mettent en évidence l’importance du contenu. Les types d’alerte suivants sont pris en charge :

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

Ces alertes ressemblent à ceci sur docs.microsoft.com :

Bloc de note

> [!NOTE]
> Information the user should notice even if skimming.

Bloc Tip

> [!TIP]
> Optional information to help a user be more successful.

Bloc important

> [!IMPORTANT]
> Essential information required for user success.

AVERTISSEMENT-bloc

> [!CAUTION]
> Negative potential consequences of an action.

Bloc d’avertissement

> [!WARNING]
> Certaines conséquences dangereuses d’une action.

### <a name="hyperlinks"></a>Liens hypertexte

- Les liens hypertexte doivent utiliser la syntaxe de la démarque `[friendlyname](url-or-path)` . Les [références de liens][linkref] sont prises en charge.
- Le système de publication prend en charge trois types de liens :
  - Liens URL
  - Liens de fichiers
  - Liens de références croisées
- Les liens vers d’autres articles sur docs.microsoft.com doivent être des chemins d’accès relatifs au site
- Toutes les URL vers des sites Web externes doivent utiliser le protocole HTTPs, sauf si elles ne sont pas valides pour le site cible.
- Les liens doivent avoir un nom convivial, généralement le titre de l’article lié
- Tous les éléments de la section _liens connexes_ en bas doivent être liés par un lien hypertexte
- N’utilisez pas les surcycles, le gras ou tout autre balisage à l’intérieur des crochets d’un lien hypertexte.
- Les URL complètes peuvent être utilisées lorsque vous documentez un URI spécifique. L’URI doit être placé entre les battements. Par exemple :

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a>Liaison à d’autres contenus sur docs.microsoft.com

- Les **liens URL** vers d’autres articles sur docs.Microsoft.com doivent être des chemins d’accès relatifs au site. La façon la plus simple de créer un lien relatif consiste à copier l’URL à partir de votre navigateur, puis `https://docs.microsoft.com/en-us` à supprimer de la valeur que vous collez dans démarque. N’incluez pas de paramètres régionaux dans les URL sur les propriétés Microsoft (supprimer `/en-us` de l’URL). Supprimez les paramètres de requête inutiles de l’URL. Exemples à supprimer :

  - `?view=powershell-5.1` -utilisé pour établir une liaison à une version spécifique de PowerShell
  - `?redirectedfrom=MSDN` -ajouté à l’URL lorsque vous êtes Redirigé depuis un ancien article vers son nouvel emplacement

  Si vous avez besoin de créer un lien vers une version spécifique d’un document, vous devez ajouter le `&preserve_view=true` paramètre à la chaîne de requête. Par exemple : `?view=powershell-5.1&preserve_view=true`

- Un **lien de fichier** est utilisé pour lier un article de référence à un autre, ou d’un article conceptuel à un autre. Si vous avez besoin de créer un lien vers un article de référence pour une version spécifique de PowerShell, vous devez utiliser un lien URL.

  - Les liens de fichiers contiennent un chemin de fichier relatif (par exemple : `../folder/file.md` )
  - Tous les chemins d’accès aux fichiers utilisent des barres obliques ( `/` )

- Les **liens de références croisées** sont une fonctionnalité spéciale prise en charge par le système de publication. Vous pouvez utiliser des liens de référence croisée dans des articles conceptuels pour établir un lien vers l’API .NET ou une référence d’applet de commande.

  Pour obtenir des liens vers des informations de référence sur les API .NET, consultez [utiliser les liens dans la documentation](/contribute/how-to-write-links#xref-cross-reference-links) du Guide du contributeur central.

  Le format des liens vers la référence d’applet de commande est le suivant : `xref:<module-name>.<cmdlet-name>` . Par exemple, pour établir un lien vers l' `Get-Content` applet de commande dans le module **Microsoft. PowerShell. Management** .

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

La liaison profonde est autorisée à la fois sur les liens d’URL et de fichiers. Ajoutez l’ancre à la fin du chemin d’accès cible.
Par exemple :

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Pour plus d’informations, consultez [utiliser des liens dans la documentation](/contribute/how-to-write-links).

## <a name="formatting-command-syntax-elements"></a>Mise en forme des éléments de la syntaxe des commandes

- Utilisez toujours le nom complet pour les applets de commande et les paramètres. Évitez d’utiliser des alias à moins que vous ne démontrant spécifiquement l’alias.

- La propriété, le paramètre, l’objet, les noms de types, les noms de classes, les méthodes de classe doivent être en **gras**.
  - Les valeurs des propriétés et des paramètres doivent être encapsulées dans les battements ( `` ` `` ).
  - Quand vous faites référence à des types à l’aide du style entre crochets, utilisez des battements. Par exemple : `[System.Io.FileInfo]`

- Les mots clés de langage, les noms d’applet de commande, les fonctions, les variables, les fichiers exe natifs, les chemins de fichiers et les exemples de syntaxe Inline doivent être encapsulés dans les caractères de soulignement ( `` ` `` ).

  Par exemple :

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - Quand vous faites référence à un paramètre par son nom, le nom doit être en **gras**. Lors de l’illustration de l’utilisation d’un paramètre avec le préfixe de trait d’union, le paramètre doit être entouré d’accents graves. Par exemple :

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - Quand vous montrez un exemple d’utilisation d’une commande externe, l’exemple doit être entouré d’accents graves.
    Incluez toujours l’extension de fichier dans la commande native. Par exemple :

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    L’inclusion de l’extension de fichier garantit que la commande correcte est exécutée en fonction de la priorité des commandes de PowerShell.

- Lors de l’écriture d’un article conceptuel (par opposition au contenu des informations de référence), la première occurrence du nom d’une applet de commande doit avoir un lien hypertexte vers la documentation de l’applet de commande. N’utilisez pas les surcycles, le gras ou tout autre balisage à l’intérieur des crochets d’un lien hypertexte.

  Par exemple :

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Pour plus d’informations, consultez la section [liens hypertexte](#hyperlinks) de cet article.

## <a name="markdown-for-code-samples"></a>Démarque pour les exemples de code

Markdown prend en charge deux styles de code différents :

- **Étendues de code (Inline)** -marquées d’un seul caractère de soulignement ( `` ` `` ). Utilisé dans un paragraphe plutôt qu’en tant que bloc autonome.
- **Blocs de code** : bloc à plusieurs lignes entouré de chaînes triple-Tick ( `` ``` `` ). Les blocs de code peuvent également avoir une étiquette de langue après les battements. L’étiquette de langage active la mise en surbrillance de la syntaxe pour le contenu du bloc de code.

Tous les blocs de code doivent être entourés d’une délimitation de code. N’utilisez jamais la mise en retrait pour les blocs de code. La démarque autorise ce modèle, mais elle peut être problématique et doit être évitée.

Un bloc de code est une ou plusieurs lignes de code entourées d’une délimitation de code triple-Tick ( `` ``` `` ).
Les marqueurs de délimitation de code doivent se trouver sur leur propre ligne avant et après l’exemple de code. Le marqueur au début du bloc de code peut avoir une étiquette de langage facultative. Le système de publication OPS de Microsoft utilise l’étiquette de langage pour prendre en charge la fonctionnalité de mise en surbrillance de la syntaxe.

Pour obtenir la liste complète des balises de langue prises en charge, consultez [blocs de code](/contribute/code-in-docs#fenced-code-blocks) délimités dans le Guide du contributeur centralisé.

OPS ajoute également un bouton de **Copie** qui copie le contenu du bloc de code dans le Presse-papiers. Cela vous permet de coller rapidement le code dans un script pour tester l’exemple de code. Toutefois, tous les exemples de notre documentation ne sont pas destinés à être exécutés en l’absence. Certains blocs de code sont des illustrations simples d’un concept PowerShell.

Il existe trois types de blocs de code utilisés dans notre documentation :

1. Blocs de syntaxe
1. Exemples servant d’illustration
1. Exemples exécutables

### <a name="syntax-code-blocks"></a>Blocs de code de syntaxe

Les blocs de code de syntaxe sont utilisés pour décrire la structure syntaxique d’une commande. N’utilisez pas de balise de langue sur la clôture du code. Cet exemple illustre tous les paramètres possibles de l’applet de commande `Get-Command`.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

Cet exemple décrit l’instruction `for` en termes généralisés :

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Exemples illustratifs

Des exemples illustratifs sont utilisés pour expliquer un concept PowerShell. Elles ne sont pas destinées à être copiées dans le presse-papiers pour être exécutées. Celles-ci sont le plus souvent utilisées pour des exemples simples faciles à saisir et faciles à comprendre. Le bloc de code peut inclure l’invite PowerShell et l’exemple de sortie.

Voici un exemple simple illustrant les opérateurs de comparaison PowerShell. Dans ce cas, nous ne prévoyons pas que le lecteur copie cet exemple et l’exécute.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>Exemples exécutables

Les exemples complexes, ou des exemples destinés à être copiés et exécutés, doivent utiliser le balisage de style bloc suivant :

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

La sortie affichée par les commandes PowerShell doit être placée dans un bloc de code **Output** (Sortie) pour empêcher la mise en surbrillance de la syntaxe. Par exemple :

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

L’étiquette du code de **sortie** n’est pas une « langue » officielle prise en charge par le système de mise en surbrillance de syntaxe.
Toutefois, cette étiquette est utile, car OPS ajoute l’étiquette « sortie » au cadre de la zone de code sur la page Web. La zone de code « sortie » n’a pas de mise en surbrillance syntaxique.

## <a name="coding-style-rules"></a>Règles de style pour le code

### <a name="avoid-line-continuation-in-code-samples"></a>Éviter les continuations de ligne dans les exemples de code

Évitez d’utiliser les caractères de continuation de ligne (`` ` ``) dans les exemples de code PowerShell. Ils sont difficiles à voir et peuvent provoquer des problèmes s’il existe des espaces supplémentaires à la fin de la ligne.

- Utilisez la projection PowerShell pour réduire la longueur de ligne des applets de commande qui ont plusieurs paramètres.
- Tirez parti des opportunités de saut de ligne naturel de PowerShell, comme après les caractères de barre verticale () `|` , les accolades ouvrantes ( `{` ), les parenthèses ( `(` ) et les crochets ( `[` ).

### <a name="avoid-using-powershell-prompts-in-examples"></a>Évitez d’utiliser les invites PowerShell dans les exemples.

L’utilisation de la chaîne d’invite est déconseillée et doit être limitée aux scénarios qui sont destinés à illustrer l’utilisation de la ligne de commande. Pour la plupart de ces exemples, la chaîne d’invite doit être `PS>` . Cette invite est indépendante des indicateurs spécifiques au système d’exploitation.

Les invites sont requises dans des exemples pour illustrer les commandes qui modifient l’invite ou lorsque le chemin d’accès affiché est significatif pour le scénario. L’exemple suivant montre comment l’invite change lors de l’utilisation du fournisseur de Registre.

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="dont-use-aliases-in-examples"></a>N’utilisez pas d’alias dans des exemples

Utilisez le nom complet de l’ensemble des applets de commande et des paramètres, sauf si vous documentez spécifiquement l’alias.
Les noms des applets de commande et des paramètres doivent utiliser les noms appropriés [en respectant la casse][] .

### <a name="using-parameters-in-examples"></a>Utilisation de paramètres dans les exemples

Évitez d’utiliser des paramètres positionnels En général, vous devez toujours inclure le nom du paramètre dans un exemple, même si le paramètre est positionnel. Ceci réduit le risque de confusion dans vos exemples.

## <a name="formatting-cmdlet-reference-articles"></a>Articles de référence sur les applets de commande mise en forme

Les articles de référence sur les applets de commande ont une structure spécifique. Cette structure est définie par [PlatyPS][].
PlatyPS génère l’aide de l’applet de commande pour les modules PowerShell dans la démarque. Une fois les fichiers Markdown modifiés, PlatyPS est utilisé pour créer les fichiers d’aide MAML utilisés par l’applet de commande `Get-Help`.

PlatyPS un schéma codé en dur pour les informations de référence des applets de commande qui sont écrites dans le code. Le document [platyPS.schema.md][] décrit cette structure. Les violations du schéma entraînent des erreurs de génération, qui doivent être corrigées avant que nous puissions accepter votre contribution.

- Ne supprimez pas les structures d’en-tête ATX. PlatyPS attend un ensemble spécifique d’en-têtes.
- Les en-têtes **Input type** et **Output type** doivent avoir un type. Si l’applet de commande ne prend pas d’entrée ou ne retourne pas de valeur, utilisez la valeur `None` .
- Les étendues de code inline peuvent être utilisées dans n’importe quel paragraphe.
- Les blocs de code délimités sont autorisés uniquement dans la section **exemples** .

Dans le schéma PlatyPS, des **exemples** sont un en-tête H2. Chaque exemple est un en-tête H3. Dans un exemple, le schéma n’autorise pas la séparation des blocs de code par des paragraphes. Le schéma autorise la structure suivante :

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Numérotez chaque exemple et ajoutez un titre court.

Par exemple :

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a>Mise en forme des fichiers About_

`About_*` les fichiers sont écrits dans la démarque mais sont fournis en tant que fichiers texte bruts. Nous utilisons [pandoc][] pour convertir la démarque en texte brut. `About_*` les fichiers sont mis en forme pour une meilleure compatibilité dans toutes les versions de PowerShell et avec les outils de publication.

Instructions de mise en forme de base :

- Limiter les lignes normales à 80 caractères
- Les blocs de code sont limités à 76 caractères
- Citations (et les alertes) sont des 78 caractères limités
- Quand vous utilisez ces méta-caractères spéciaux `\` , `$` , et `<` :
  - Dans un en-tête, ces caractères doivent être placés dans une séquence d’échappement à l’aide d’un `\` caractère de début ou placés entre des étendues de code à l’aide des battements ( `` ` `` )
  - Dans un paragraphe, ces caractères doivent être placés dans des étendues de code. Par exemple :

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- Les tables doivent tenir dans 76 caractères
  - Renvoyez manuellement à la ligne le contenu des cellules sur plusieurs lignes
  - Utilisez des caractères `|` d’ouverture et de fermeture sur chaque ligne
  - L’exemple suivant montre comment construire correctement une table qui contient des informations qui s’encapsulent sur plusieurs lignes dans une cellule.

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > La limitation de 76 colonnes s’applique uniquement aux `About_*` rubriques. Vous pouvez utiliser des colonnes larges dans des Articles de référence conceptuelles ou d’applets de commande.

## <a name="next-steps"></a>Étapes suivantes

[Liste de contrôle éditoriale](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Casse Pascal]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
