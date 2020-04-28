---
title: Guide de style pour la documentation PowerShell
description: Cet article présente les règles de style pour l’écriture de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 90dc93d608440ce7388614b552c0cd873a385cd9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624786"
---
# <a name="powershell-docs-style-guide"></a>Guide de style pour la documentation PowerShell

Cet article donne des conseils de style propres au contenu PowerShell-Docs, qui s’appuient sur les informations présentées dans la [Vue d’ensemble](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Terminologie des produits

Il existe plusieurs variantes de PowerShell.

- **PowerShell** : terme par défaut. Nous considérons la version 7 et les versions ultérieures de PowerShell comme le vrai PowerShell, à ce jour et à l’avenir.
- **PowerShell Core** : PowerShell reposant sur .NET Core. L’utilisation du terme **Core** doit être limitée aux cas où il est nécessaire de le différencier de Windows PowerShell.
- **Windows PowerShell** : PowerShell reposant sur .NET Framework. Windows PowerShell est fourni uniquement sur Windows et requiert l’infrastructure complète.

  En général, les références à « Windows PowerShell » dans la documentation peuvent être remplacées par « PowerShell ».
  « Windows PowerShell » doit être utilisé lorsque l’on aborde le comportement spécifique à « Windows PowerShell ».

Produits connexes

- **Visual Studio Code (VS Code)** : il s’agit de l’éditeur open source et gratuit de Microsoft. Lors de la première mention, le nom complet doit être utilisé. Après cela, vous pouvez utiliser **VS Code**. N’utilisez pas « VSCode ».
- **Extension PowerShell pour Visual Studio Code** : l’extension active VS Code dans l’IDE préféré pour PowerShell. Lors de la première mention, le nom complet doit être utilisé. Après cela, vous pouvez utiliser **Extension PowerShell**.
- **Azure PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer les services Azure.
- **Azure Stack PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer la solution cloud hybride de Microsoft.

## <a name="markdown-specifics"></a>Spécificités de Markdown

Microsoft Open Publishing System (OPS), qui nous permet de créer notre documentation, utilise [markdig][] pour traiter les documents Markdown. Markdig analyse les documents suivant les règles de la dernière spécification [CommonMark][].

La nouvelle spécification CommonMark est plus stricte sur la construction de certains éléments Markdown. Portez une attention particulière aux informations fournies dans ce document.

### <a name="blank-lines-spaces-and-tabs"></a>Lignes vides, espaces et tabulations

Les lignes vides signalent également la fin d’un bloc en Markdown. Il doit y avoir un seul espace entre les blocs Markdown de différents types (par exemple, entre un paragraphe et une liste ou un en-tête).

Supprimez les lignes vides en double. S’il existe plusieurs lignes vides, elles s’affichent comme une seule ligne vide en HTML ; il n’y a donc pas d’intérêt à en insérer plusieurs. Plusieurs lignes vides au sein d’un bloc de code rompent le bloc de code.

Supprimez les espaces supplémentaires à la fin des lignes.

> [!NOTE]
> L’espacement est significatif en Markdown. Utilisez toujours des espaces plutôt que des tabulations fixes. Les espaces de fin peuvent modifier le rendu Markdown.

### <a name="titles-and-headings"></a>Titres et en-têtes

Utilisez uniquement des [en-têtes ATX][atx] (de style #, par opposition aux en-têtes de style `=` ou `-`).

- Seule la première lettre des phrases, des noms propres, des titres et des en-têtes doit être en majuscule.
- Il doit y avoir un seul espace entre le `#` et la première lettre du titre.
- Les en-têtes doivent être délimités par une seule ligne vide.
- Un document ne peut contenir qu’un seul titre H1.
- Les niveaux d’en-têtes doivent se suivre par incréments de un, sans qu’un niveau soit ignoré.
- N’utilisez pas de balises de type gras ou autre dans les en-têtes.

### <a name="limit-line-length-to-100-characters"></a>Limiter la longueur de ligne à 100 caractères

Cette règle s’applique aux articles conceptuels et aux informations de référence sur les cmdlets. Le fait de limiter la longueur de ligne améliore la lisibilité des différences et de l’historique de Git. Elle permet également aux autres rédacteurs d’apporter plus facilement leur contribution.

Utilisez l’extension [Reflow Markdown][reflow] dans Visual Studio Code pour ajuster dynamiquement les paragraphes en fonction de la longueur de ligne prescrite.

Les rubriques About_ sont limitées à 80 caractères. Pour plus d’informations, consultez [Modification des articles de référence](./editing-cmdlet-ref.md#formatting-about_-files).

### <a name="lists"></a>Listes

Si votre liste contient plusieurs phrases ou paragraphes, utilisez de préférence un en-tête de sous-niveau plutôt qu’une liste.

Les listes doivent être délimitées par une seule ligne vide.

#### <a name="unordered-lists"></a>Listes non triées

Les éléments de liste ne doivent pas se terminer par un point, sauf s’ils contiennent plusieurs phrases. Utilisez le caractère de trait d’union (`-`) comme puce pour les éléments de liste afin d’éviter toute confusion avec les balises de type gras ou en italique qui utilisent l’astérisque [`*`]. Pour inclure un paragraphe ou d’autres éléments sous un élément de puce, insérez un saut de ligne et alignez le retrait avec le premier caractère après la puce.

Par exemple :

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

Voici une liste qui contient des sous-éléments sous un élément de puce.

- Premier élément de puce

  Phrase expliquant la première puce.

  - Élément de puce de niveau inférieur

    Phrase expliquant la puce de niveau inférieur.

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

Où `alt text` est une brève description de l’image et `<folder path>` le chemin relatif de l’image. Le texte de remplacement est nécessaire pour les lecteurs d’écran des personnes déficientes visuelles. Il est également utile en cas de bogue du site empêchant le rendu de l’image.

Les images doivent être stockées dans un dossier `media/<article-name>` à l’intérieur du dossier contenant l’article.
Elles ne doivent pas être partagées entre les articles. Créez un dossier correspondant au nom de fichier de votre article dans le dossier `media`. Copiez les images de cet article dans ce nouveau dossier. Si une image est utilisée par plusieurs articles, chaque dossier d’image doit comporter une copie de ce fichier image. Cette pratique permet d’éviter que la modification d’une image dans un article n’affecte un autre article.

Sont pris en charge les types de fichiers images suivants : `*.png`, `*.gif`, `*.jpeg`, `*.jpg` et `*.svg`.

### <a name="markdown-extensions-supported-by-open-publishing"></a>Extensions Markdown prises en charge par Open Publishing

[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contient des outils qui gèrent des fonctionnalités propres à notre système de publication. Les alertes sont une extension Markdown permettant de créer des citations qui s’affichent sur docs.microsoft.com avec des couleurs et des icônes différentes selon l’importance du contenu. Sont pris en charge les types d’alertes suivants :

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

Ces alertes se présentent ainsi sur docs.microsoft.com :

Bloc Note

> [!NOTE]
> Informations que l’utilisateur devrait remarquer même en parcourant rapidement le document.

Bloc Conseil

> [!TIP]
> Informations facultatives visant à aider l’utilisateur à gagner en efficacité.

Bloc Important

> [!IMPORTANT]
> Informations essentielles nécessaires à la réussite de l’utilisateur.

Bloc Attention

> [!CAUTION]
> Conséquences négatives potentielles d’une action.

Bloc Avertissement

> [!WARNING]
> Conséquences dangereuses certaines d’une action.

### <a name="hyperlinks"></a>Liens hypertexte

- Les liens hypertexte doivent utiliser la syntaxe Markdown `[friendlyname](url-or-path)`
- Les liens doivent utiliser le protocole HTTPS dans la mesure du possible.
- Les liens doivent avoir un nom convivial, généralement le titre de la rubrique liée.
- Tous les éléments de la section « liens connexes » en bas de la page doivent contenir des liens hypertexte.
- N’utilisez pas d’accents graves ou de balises de type gras ou autre à l’intérieur des crochets d’un lien hypertexte.
- Les URL brutes peuvent être utilisées lorsque vous parlez d’un URI spécifique. L’URI doit être placé entre des accents graves. Par exemple :

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a>Liens vers d’autres contenus

Il existe deux types de liens hypertextes pris en charge par le système de publication :

Un **lien URL** peut être un chemin d’URL relatif à la racine de docs.microsoft.com. ou une URL absolue comportant la syntaxe complète de l’URL Par exemple : `https:/github.com/MicrosoftDocs/PowerShell-Docs`

- Utilisez des liens URL pour établir un lien vers du contenu extérieur à PowerShell-Docs ou entre des informations de référence sur les cmdlets et des articles conceptuels dans PowerShell-Docs. Le moyen le plus simple de créer un lien relatif consiste à copier l’URL dans votre navigateur, puis à supprimer `https://docs.microsoft.com/en-us` de la valeur que vous collez dans Markdown.
- Ne pas inclure de paramètres régionaux dans les URL sur les propriétés Microsoft (par exemple, supprimer `/en-us` dans l’URL).
- Supprimez les paramètres de requête inutiles de l’URL, sauf si vous avez besoin de créer un lien vers une version spécifique d’un article. Exemples :
  - `?view=powershell-5.1` : utilisé pour établir un lien vers une version spécifique de PowerShell
  - `?redirectedfrom=MSDN` : ajouté à l’URL lorsque vous êtes redirigé depuis un ancien article vers son nouvel emplacement
- Toutes les URL de sites web externes doivent utiliser le protocole HTTPS, sauf si ce n’est pas valide pour le site cible.

Un **lien de fichier** est utilisé pour établir un lien d’un article de référence à un autre, ou d’un article conceptuel à un autre. Si vous avez besoin de créer un lien vers un article de référence pour une version spécifique de PowerShell, vous devez utiliser un lien URL.

- Les liens de fichiers contiennent un chemin de fichier relatif (par exemple, `../folder/file.md`).
- Tous les chemins de fichiers utilisent des barres obliques (`/`).

La liaison profonde est autorisée à la fois sur les liens d’URL et de fichiers. Ajoutez l’ancre à la fin du chemin d’accès cible.
Par exemple :

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Pour plus d’informations, consultez [Utiliser des liens dans la documentation](https://docs.microsoft.com/contribute/how-to-write-links).

## <a name="formatting-command-syntax-elements"></a>Mise en forme des éléments de syntaxe de commande

- Utilisez toujours le nom complet pour les cmdlets et les paramètres. Évitez d’utiliser des alias à moins qu’il ne s’agisse spécifiquement d’une démonstration des alias.

- Les noms de propriété, de paramètre, d’objet, de type, les noms de classes, les méthodes de classe doivent être en **gras**.
  - Les valeurs des propriétés et des paramètres doivent être encapsulées entre des accents graves (`` ` ``).
  - Quand vous faites référence à des types à l’aide du style entre crochets, utilisez des accents graves. Par exemple : `[System.Io.FileInfo]`

- Les mots clés de langage, les noms d’applet de commande, les fonctions, les variables, les fichiers EXE natifs, les chemins de fichiers et les exemples de syntaxe Inline doivent être encapsulés entre des accents graves (`` ` ``).

  Par exemple :

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - En cas de référence à un paramètre par son nom, ce nom doit être en **gras**. Pour illustrer l’utilisation d’un paramètre avec le préfixe de trait d’union, ce paramètre doit être placé entre accents graves. Par exemple :

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - Pour montrer l’utilisation d’une commande externe, l’exemple doit être placé entre accents graves.
    Incluez toujours l’extension de fichier dans la commande native. Par exemple :

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    L’inclusion de l’extension de fichier garantit que la commande correcte est exécutée conformément à la priorité des commandes de PowerShell.

- Lorsque vous écrivez un article conceptuel (par opposition à du contenu de référence), la première instance du nom d’une cmdlet doit comporter un lien hypertexte vers la documentation de la cmdlet. N’utilisez pas d’accents graves ou de balises de type gras ou autre à l’intérieur des crochets d’un lien hypertexte.

  Par exemple :

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Pour plus d’informations, consultez la section [Liens hypertextes](#hyperlinks) de cet article.

## <a name="markdown-for-code-samples"></a>Markdown pour les exemples de code

Markdown prend en charge deux styles de code différents :

- Le **code inline**, marqué par un seul caractère accent grave (`` ` ``). et utilisé au sein d’un paragraphe plutôt que comme bloc autonome ;
- les **blocs de code**, blocs de plusieurs lignes délimités par des chaînes constituées de trois accents graves (`` ``` ``) éventuellement suivis d’une étiquette de langage qui permet la coloration syntaxique du contenu du bloc de code.

Tous les blocs de code doivent être délimités N’utilisez jamais la mise en retrait pour les blocs de code. Markdown autorise ce modèle, mais il peut être problématique et doit être évité.

Un bloc de code est une ou plusieurs lignes de code entourées d’une limite de code de trois caractères accent grave (`` ``` ``).
Les délimiteurs de code doivent se trouver sur leur propre ligne avant et après l’exemple de code. Le marqueur de début du bloc de code peut éventuellement comporter une étiquette de langage. Microsoft Open Publishing System (OPS) utilise l’étiquette de langage pour gérer la fonctionnalité de coloration syntaxique.

Pour obtenir la liste complète des balises de langage prises en charge, consultez [Blocs de code délimités](/contribute/code-in-docs#fenced-code-blocks) dans le Guide du contributeur centralisé.

OPS ajoute également un bouton **Copier** qui permet de copier le contenu du bloc de code dans le Presse-papiers, et ainsi de coller rapidement le code dans un script pour tester l’exemple de code. Toutefois, les exemples de notre documentation ne sont pas tous destinés à être exécutés tels quels. Certains blocs de code sont de simples illustrations d’un concept de PowerShell.

Trois types de blocs de code sont utilisés dans notre documentation :

1. Blocs de syntaxe
1. Exemples servant d’illustration
1. Exemples exécutables

### <a name="syntax-code-blocks"></a>Blocs de code syntaxiques

Les blocs de code de syntaxe sont utilisés pour décrire la structure syntaxique d’une commande. N’utilisez pas de balise de langage sur la limite du code. Cet exemple illustre tous les paramètres possibles de la cmdlet `Get-Command`.

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

### <a name="illustrative-examples"></a>Exemples servant d’illustration

Certains exemples servent d’illustration pour expliquer un concept de PowerShell. Ils ne sont pas destinés à être copiés dans le Presse-papiers pour être exécutés. Ils sont couramment utilisés pour des exemples simples et faciles à taper et à comprendre. Le bloc de code peut inclure l’invite PowerShell et l’exemple de sortie.

Voici un exemple simple illustrant les opérateurs de comparaison de PowerShell. Il n’est pas attendu du lecteur qu’il copie et exécute cet exemple.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
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

Les exemples complexes ou destinés à être copiés et exécutés doivent utiliser le balisage de style bloc suivant :

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

La sortie affichée par les commandes PowerShell doit être placée dans un bloc de code **Output** pour empêcher la coloration syntaxique. Par exemple :

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

L’étiquette de code **Output** n’est pas un « langage » officiel pris en charge par le système de coloration syntaxique.
Elle est toutefois utile, car OPS ajoute l’étiquette « Output » (« Sortie ») au cadre de la zone de code sur la page web. La zone de code « Output » ne présente pas de coloration syntaxique.

## <a name="coding-style-rules"></a>Règles de style de codage

### <a name="avoid-line-continuation-in-code-samples"></a>Éviter la continuation de ligne dans les exemples de code

Évitez d’utiliser des caractères de continuation de ligne (`` ` ``) dans les exemples de code PowerShell. Ils sont difficiles à voir et peuvent poser problème en présence d’espaces supplémentaires à la fin de la ligne.

- Utilisez la projection PowerShell pour réduire la longueur de ligne des cmdlets comportant de nombreux paramètres.
- Tirez parti des possibilités naturelles de saut de ligne de PowerShell, comme après les caractères barre verticale (`|`), les accolades ouvrantes, les parenthèses et les crochets.

### <a name="avoid-using-powershell-prompts-in-examples"></a>Éviter d’utiliser les invites PowerShell dans les exemples

Il est déconseillé d’utiliser la chaîne d’invite, qui doit être limitée aux scénarios destinés à illustrer l’usage de la ligne de commande. Pour la plupart de ces exemples, la chaîne d’invite doit être `PS>`. Cette invite est indépendante des indicateurs propres au système d’exploitation.

Les invites sont requises pour les exemples illustrant des commandes qui modifient l’invite ou lorsque le chemin affiché est significatif pour le scénario illustré. L’exemple suivant montre comment l’invite change lorsque le fournisseur de registre est utilisé.

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

### <a name="do-not-use-aliases-in-examples"></a>Ne pas utiliser d’alias dans les exemples

Utilisez toujours le nom complet de toutes les cmdlets et de tous les paramètres, sauf si vous parlez spécifiquement de l’alias. Les noms des cmdlets et des paramètres doivent être des noms utilisant la casse Pascal correcte.

### <a name="using-parameters-in-examples"></a>Utiliser des paramètres dans les exemples

Évitez d’utiliser des paramètres positionnels. En général, vous devez toujours inclure le nom du paramètre dans l’exemple, même s’il s’agit d’un paramètre positionnel. Cela réduit le risque de confusion dans les exemples.

## <a name="next-steps"></a>Étapes suivantes

[Modification des informations de référence sur les cmdlets](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
