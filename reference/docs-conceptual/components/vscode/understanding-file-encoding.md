---
title: Présentation de l’encodage de fichier dans VSCode et PowerShell
description: Configurer l’encodage du fichier dans VSCode et PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251471"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Présentation de l’encodage de fichier dans VSCode et PowerShell

Lorsque vous utilisez Visual Studio Code pour créer et modifier des scripts PowerShell, il est important que vos fichiers sont enregistrés à l’aide du format d’encodage de caractères approprié.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Quel est l’encodage de fichier et pourquoi est-il important ?

VSCode gère l’interface entre un humain chaînes de saisie de caractères dans une mémoire tampon et les blocs de lecture/écriture d’octets pour le système de fichiers. Quand VSCode enregistre un fichier, il utilise un codage de texte à le faire.

De même, lorsque PowerShell exécute un script il doit convertir les octets dans un fichier de caractères à reconstruire le fichier dans un programme de PowerShell. VSCode écrit le fichier et PowerShell lit le fichier, ils doivent utiliser le même système d’encodage. Ce processus de l’analyse d’un script PowerShell se déroule : *octets* -> *caractères* -> *jetons*  ->   *arborescence de syntaxe abstraite* -> *exécution*.

VSCode et PowerShell sont installés avec une configuration d’encodage par défaut. Toutefois, l’encodage par défaut utilisée par PowerShell a changé avec la version de PowerShell Core (v6.x). Pour vous assurer de ne pose aucun problème à l’aide de PowerShell ou l’extension PowerShell dans VSCode, vous devez configurer vos paramètres VSCode et PowerShell correctement.

## <a name="common-causes-of-encoding-issues"></a>Causes courantes des problèmes de codage

Encodage problèmes lors de l’encodage de VSCode ou votre fichier de script ne correspond pas à l’encodage attendu de PowerShell. Il n’existe aucun moyen de PowerShell pour déterminer automatiquement l’encodage du fichier.

Vous êtes plus susceptible d’avoir des problèmes de codage lorsque vous utilisez des caractères pas dans le [jeu de caractères ASCII 7 bits](https://ascii.cl/). Par exemple :

- Les caractères de latin accentués (`É`, `ü`)
- Caractères non latins comme cyrillique (`Д`, `Ц`)
- Henri chinois (`脚`, `本`)

Causes courantes de problèmes de codage sont :

- Les encodages de VSCode et PowerShell n’ont pas été modifiés à partir de leurs valeurs par défaut. Pour PowerShell 5.1 et version antérieure, la valeur par défaut l’encodage est différent à partir de VSCode.
- Un autre éditeur a ouvert et remplacé le fichier dans un nouvel encodage. Cela se produit souvent avec l’environnement ISE.
- Le fichier est extrait dans le contrôle de source dans un encodage différent à partir de quel VSCode ou de PowerShell attend. Cela peut se produire lorsque collaborateurs utilisent éditeurs avec différentes configurations d’encodage.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Comment savoir quand vous avez des problèmes de codage

Une erreur d’encodage souvent présente eux-mêmes comme des erreurs dans les scripts d’analyse. Si vous trouvez des séquences de caractères étranges dans votre script, cela peut être le problème. Dans l’exemple ci-dessous, un tiret demi-cadratin (`–`) s’affiche en tant que les caractères `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Ce problème se produit parce que VSCode encode le caractère `–` en UTF-8 en tant que les octets `0xE2 0x80 0x93`.
Lorsque ces octets sont décodées en tant que Windows-1252, elles sont interprétées comme les caractères `â€“`.

Certaines séquences de caractères étranges qui peuvent apparaître sont les suivantes :

- `â€“` au lieu de `–`
- `â€”` au lieu de `—`
- `Ã„2` au lieu de `Ä`
- `Â` au lieu de ` ` (espace insécable)
- `Ã©` au lieu de `é`

Portée de main [référence](https://www.i18nqa.com/debug/utf8-debug.html) répertorie les modèles courants qui indiquent un problème de codage UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Comment l’extension PowerShell dans VSCode interagit avec les encodages

L’extension PowerShell interagit avec des scripts dans une de plusieurs façons :

1. Lorsque les scripts sont modifiés dans VSCode, le contenu est envoyé par VSCode à l’extension. Le [protocole de serveur de langage][] impose que ce contenu est transféré en UTF-8. Par conséquent, il n’est pas possible pour l’extension obtenir l’encodage incorrect.
2. Lorsque les scripts sont exécutées directement dans la Console intégrée, ils sont lus à partir du fichier par PowerShell directement. Encodage de Tf PowerShell diffère de VSCode, quelque chose peut mal se passer ici.
3. Lorsqu’un script qui est ouvert dans VSCode fait référence à un autre script qui n’est pas ouvert dans VSCode, l’extension revient au chargement de contenu de ce script à partir du système de fichiers. L’extension PowerShell par défaut de l’encodage UTF-8, mais utilise [marque d’ordre d’octet][], ou BOM, détection permet de sélectionner l’encodage correct.

Le problème se produit lorsqu’en supposant que l’encodage des formats de sans BOM (comme [UTF-8][] sans BOM et [Windows-1252][]).
L’extension PowerShell par défaut est UTF-8. L’extension ne peut pas modifier les paramètres d’encodage de VSCode.
Pour plus d’informations, consultez [émettre #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Choix de l’encodage de droite

Divers systèmes et applications peuvent utiliser différents codages :

- Dans .NET Standard, sur le web et dans le monde de Linux, UTF-8 est désormais l’encodage dominant.
- De nombreuses applications .NET Framework utilisent [UTF-16][]. Pour des raisons historiques, il est parfois appelé « Unicode », un terme qui fait référence à une large [standard](https://en.wikipedia.org/wiki/Unicode) incluant UTF-8 et UTF-16.
- Sur Windows, de nombreuses applications natives qui sont antérieurs à Unicode continuent à utiliser Windows-1252 par défaut.

Les codages Unicode ont également le concept d’un ordre d’octet (BOM) de marquer. Nomenclatures se produisent au début du texte pour indiquer un décodeur le codage à l’aide de texte. Pour les encodages multi-octets, la nomenclature indique également [endianness](https://en.wikipedia.org/wiki/Endianness) du codage. Nomenclatures sont conçus pour être des octets qui se produisent rarement dans le texte non-Unicode, ce qui permet une estimation raisonnable que texte est au format Unicode lorsqu’un BOM est présent.

Nomenclatures sont facultatives et leur adoption n’est pas aussi populaire dans le monde de Linux, car une convention fiable d’UTF-8 est utilisée partout. La plupart des applications Linux supposent que l’entrée de texte est encodée en UTF-8. Tandis que de nombreuses applications Linux reconnaît et gère correctement une nomenclature, un nombre ne le faites pas, ce qui conduit à des artefacts dans le texte manipulé avec ces applications.

**Par conséquent** :

- Si vous travaillez principalement avec les applications Windows et Windows PowerShell, vous devez préférer un encodage comme UTF-8 avec BOM ou UTF-16.
- Si vous travaillez sur plusieurs plateformes, vous devez préférer UTF-8 avec BOM.
- Si vous travaillez principalement dans les contextes associés à Linux, vous devez préférer UTF-8 sans BOM.
- Windows-1252 et latin-1 sont essentiellement des encodages hérités que vous ne devez pas si possible.
  Toutefois, certaines applications Windows plus anciens peuvent dépendre les.
- Il est également important de noter que la signature de script est [dépendant du codage](https://github.com/PowerShell/PowerShell/issues/3466), ce qui signifie qu’une modification de codage sur un script signé nécessitera la nouvelle signature.

## <a name="configuring-vscode"></a>Configuration de VSCode

De VSCode encodage par défaut est UTF-8 sans BOM.

Pour définir [VSCode du codage][], accédez aux paramètres VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) et définissez le `"files.encoding"` paramètre :

```json
"files.encoding": "utf8bom"
```

Certaines valeurs possibles sont :

- `utf8`: [UTF-8] sans BOM
- `utf8bom`: [UTF-8] avec BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Vous devez obtenir une liste déroulante pour cela dans la vue de l’interface graphique utilisateur, ou d’afficher des saisies semi-automatiques pour celui-ci dans le JSON.

Vous pouvez également ajouter les éléments suivants pour détecter automatiquement lorsque cela est possible d’encodage :

```json
"files.autoGuessEncoding": true
```

Si vous ne souhaitez pas ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations de langage. Créer un paramètre spécifique à la langue en plaçant des paramètres dans un `[<language-name>]` champ. Par exemple :

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configuration de PowerShell

De PowerShell encodage par défaut varie en fonction de la version :

- Dans PowerShell 6 et versions ultérieures, l’encodage par défaut est UTF-8 sans BOM sur toutes les plateformes.
- Dans Windows PowerShell, l’encodage par défaut est généralement Windows-1252, une extension de [latin-1][], également appelée ISO 8859-1.

Dans PowerShell 5 et versions ultérieures, vous pouvez trouver votre encodage par défaut avec ce :

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Ce qui suit [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) peut être utilisée pour déterminer quel encodage votre session PowerShell déduit pour un script sans une nomenclature.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

Il est possible de configurer PowerShell pour utiliser un encodage donné plus généralement à l’aide de paramètres de profil. Voir les articles suivants :

- [@mklement0]de [réponses sur l’encodage de PowerShell sur StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]de [billet de blog sur le traitement d’entrée sans BOM UTF-8 dans PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Il n’est pas possible de forcer PowerShell à utiliser un codage d’entrée spécifique. PowerShell 5.1 et en dessous de la valeur par défaut pour Windows-1252 encodage lorsqu’il n’existe aucune nomenclature. Pour des raisons de l’interopérabilité, il est préférable enregistrer des scripts dans un format Unicode avec une nomenclature.

> [!IMPORTANT]
> N’importe quel outil que vous avez ce tactile PowerShell scripts peuvent être affectées par vos options de codage ou ré-encoder vos scripts à un autre encodage.

### <a name="existing-scripts"></a>Scripts existants

Scripts déjà sur le système de fichiers peut-être à ré-encoder à votre nouvel encodage choisi. Dans la barre en bas de VSCode, vous verrez l’étiquette UTF-8. Cliquez dessus pour ouvrir la barre d’action et sélectionnez **enregistrer avec encodage**. Vous pouvez maintenant choisir un nouvel encodage pour ce fichier. Consultez [VSCode du codage][] pour obtenir des instructions complètes.

Si vous avez besoin de ré-encoder plusieurs fichiers, vous pouvez utiliser le script suivant :

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>Environnement d'écriture de scripts intégré (ISE) de PowerShell

Si vous modifiez également les scripts à l’aide de PowerShell ISE, vous devez synchroniser vos paramètres d’encodage il.

L’environnement ISE doit respecter une nomenclature, mais il est également possible d’utiliser la réflexion pour [l’encodage de jeu](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Notez que cela n’aurait pas rendues persistantes entre les startups.

### <a name="source-control-software"></a>Logiciel de contrôle de code source

Certains outils de contrôle source, tels que git, ignorent les encodages ; GIT suit uniquement les octets.
Autres, telles que TFS ou Mercurial, ne peuvent pas. Même certains outils git s’appuient sur le texte de décodage.

C’est le cas, assurez-vous que vous :

- Configurer l’encodage dans votre contrôle de code source pour correspondre à votre configuration de VSCode de texte.
- Vérifiez que tous vos fichiers sont archivés dans le contrôle de code source dans l’encodage approprié.
- Méfiez-vous des modifications apportées à l’encodage reçu via le contrôle de code source. Un signe de clé de ce est une comparaison qui indique des modifications, mais où rien ne semble avoir été modifié (car les octets ont mais caractères n’ont pas).

### <a name="collaborators-environments"></a>Environnements de collaborateurs

En haut de la configuration de contrôle de code source, assurez-vous que vous n’ont pas les paramètres qui remplacent votre encodage par ré-encodage fichiers PowerShell pour vos collaborateurs sur les fichiers que vous partagez.

### <a name="other-programs"></a>Autres programmes

Tout autre programme qui lit ou écrit un script PowerShell peut ré-encoder.

Quelques exemples :

- Utilisation du Presse-papiers pour copier et coller un script. Cela est courant dans les scénarios tels que :
  - Copie d’un script dans une machine virtuelle
  - Copie d’un script en dehors d’un e-mail ou une page Web
  - Copie d’un script dans ou hors d’un document Microsoft Word ou PowerPoint
- Autres éditeurs de texte, tel que :
  - Bloc-notes
  - Vim
  - N’importe quel autre éditeur de script PowerShell
- Texte de l’édition des utilitaires, tels que :
  - `Get-Content`/`Set-Content`/`Out-File`
  - Opérateurs de redirection de PowerShell comme `>` et `>>`
  - `sed`/`awk`
- Fichiers programmes de transfert, telles que :
  - Un navigateur web, lors du téléchargement des scripts
  - Un partage de fichiers

Certains de ces outils traitent en octets plutôt que texte, mais d’autres offrent des configurations d’encodage. Dans les cas où vous devez configurer un encodage, vous devez rendre identique à votre éditeur de codage pour éviter ces problèmes.

## <a name="other-resources-on-encoding-in-powershell"></a>Autres ressources sur l’encodage dans PowerShell

Il existe quelques autres billets intéressantes sur l’encodage et la configuration d’encodage dans PowerShell qui méritent d’être une lecture :

- [@mklement0]de [résumé de l’encodage PowerShell sur StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Numéros précédents ouvert sur vscode-PowerShell pour l’encodage des problèmes :
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Classique *Joel sur les logiciels* le sujet Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Encodage dans .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marque d’ordre d’octet]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocole de serveur de langage]: https://microsoft.github.io/language-server-protocol/
[VSCode du codage]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support