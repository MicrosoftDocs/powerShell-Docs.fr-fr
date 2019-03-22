---
title: Présentation de l’encodage de fichier dans VSCode et PowerShell
description: Configuration de l’encodage de fichier dans VSCode et PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 73e766832d56a08bd5ef16df11899a0aab0badae
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795112"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Présentation de l’encodage de fichier dans VSCode et PowerShell

Quand vous utilisez Visual Studio Code pour créer et modifier des scripts PowerShell, il est important que vos fichiers soient enregistrés à l’aide du format d’encodage de caractères approprié.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Qu’est-ce que l’encodage de fichier et pourquoi est-il important ?

VSCode gère l’interface entre un utilisateur qui entre des chaînes de caractères dans une mémoire tampon et la lecture/écriture de blocs d’octets dans le système de fichiers. Quand VSCode enregistre un fichier, il utilise un encodage de texte.

De même, quand PowerShell exécute un script, il doit convertir les octets d’un fichier en caractères afin de reconstruire le fichier dans un programme PowerShell. Comme VSCode écrit le fichier et que PowerShell le lit, ils doivent utiliser le même système d’encodage. Ce processus d’analyse d’un script PowerShell est le suivant : *octets* -> *caractères* -> *jetons* ->  *arborescence de syntaxe abstraite* -> *exécution*.

VSCode et PowerShell sont tous deux installés avec une configuration d’encodage par défaut adéquate. Toutefois, l’encodage par défaut utilisée par PowerShell a changé avec la publication de PowerShell Core (v6.x). Pour être sûr de n’avoir aucun problème lors de l’utilisation de PowerShell ou de l’extension PowerShell dans VSCode, vous devez configurer vos paramètres VSCode et PowerShell correctement.

## <a name="common-causes-of-encoding-issues"></a>Causes courantes de problèmes d’encodage

Des problèmes d’encodage se produisent quand l’encodage de VSCode ou de votre fichier de script ne correspond pas à l’encodage attendu par PowerShell. PowerShell ne dispose d’aucun moyen de déterminer automatiquement l’encodage du fichier.

Vous risquez davantage de rencontrer des problèmes d’encodage quand vous utilisez des caractères qui ne figurent pas dans le [jeu de caractères ASCII sept bits](https://ascii.cl/). Par exemple :

- Les caractères latins accentués (`É`, `ü`)
- Les caractères non latins tels que les caractères cyrilliques (`Д`, `Ц`)
- Les caractères chinois (`脚`, `本`)

Les causes courantes des problèmes d’encodage sont les suivantes :

- Les encodages par défaut de VSCode et PowerShell n’ont pas été changés. Pour PowerShell 5.1 et antérieur, l’encodage par défaut est différent de celui de VSCode.
- Un autre éditeur a ouvert et remplacé le fichier dans un nouvel encodage. Cela se produit souvent avec l’environnement ISE.
- Le fichier est archivé dans le contrôle de code source dans un encodage différent de celui attendu par VSCode ou PowerShell. Cela peut se produire quand des collaborateurs utilisent des éditeurs avec différentes configurations d’encodage.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Comment savoir quand vous avez des problèmes d’encodage ?

Souvent, les erreurs d’encodage se présentent sous forme d’erreurs d’analyse dans les scripts. Si vous remarquez des séquences de caractères étranges dans votre script, il peut s’agir de ce type de problème. Dans l’exemple ci-dessous, les caractères `â€“` apparaissent à la place d’un tiret demi-cadratin (`–`) :

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Ce problème se produit car VSCode encode le caractère `–` en UTF-8 en tant qu’octets `0xE2 0x80 0x93`.
Quand ces octets sont décodés au format Windows-1252, ils sont interprétées en tant que caractères `â€“`.

Voici quelques séquences de caractères étranges susceptibles d’apparaître :

<!-- markdownlint-disable MD038 -->
- `â€“` au lieu de `–`
- `â€”` au lieu de `—`
- `Ã„2` au lieu de `Ä`
- `Â` au lieu de ` ` (espace insécable)
- `Ã©` au lieu de `é`
<!-- markdownlint-enable MD038 -->

Cette [référence](https://www.i18nqa.com/debug/utf8-debug.html) très pratique liste les modèles courants qui indiquent un problème d’encodage UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Interaction entre l’extension PowerShell dans VSCode et les encodages

L’extension PowerShell interagit avec les scripts de plusieurs façons :

1. Quand les scripts sont modifiés dans VSCode, le contenu est envoyé par VSCode à l’extension. Le [protocole de serveur de langage][] impose que ce contenu soit transféré en UTF-8. Par conséquent, il n’est pas possible pour l’extension d’obtenir l’encodage incorrect.
2. Quand les scripts sont exécutés directement dans la console intégrée, ils sont lus directement à partir du fichier par PowerShell. Si l’encodage de PowerShell est différent de celui de VSCode, les choses peuvent mal tourner.
3. Quand un script ouvert dans VSCode référence un autre script qui n’est pas ouvert dans VSCode, l’extension charge le contenu de ce script à partir du système de fichiers. L’extension PowerShell utilise par défaut l’encodage UTF-8, mais elle utilise la détection de [marque d’ordre d’octet][] pour sélectionner l’encodage correct.

Le problème se produit en cas d’encodage des formats sans marque d’ordre d’octet (comme [UTF-8][] sans marque d’ordre d’octet et [Windows-1252][]).
L’extension PowerShell utilise par défaut UTF-8. L’extension ne peut pas modifier les paramètres d’encodage de VSCode.
Pour plus d’informations, consultez le [problème n°824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Choix de l’encodage correct

Différents systèmes et applications peuvent utiliser différents encodages :

- Dans .NET Standard, sur le web et dans le monde de Linux, UTF-8 est désormais l’encodage dominant.
- De nombreuses applications .NET Framework utilisent [UTF-16][]. Pour des raisons historiques, cet encodage est parfois appelé « Unicode », un terme qui fait aujourd’hui référence à une [norme](https://en.wikipedia.org/wiki/Unicode) étendue incluant UTF-8 et UTF-16.
- Sur Windows, de nombreuses applications natives qui sont antérieures à Unicode continuent à utiliser Windows-1252 par défaut.

Avec les encodages Unicode, il existe également le concept de marque d’ordre d’octet. Les marques d’ordre d’octet sont présentes au début, et elles indiquent au décodeur l’encodage utilisé par le texte. Pour les encodages multioctets, la marque d’ordre d’octet indique également le [mode Endian](https://en.wikipedia.org/wiki/Endianness) de l’encodage. Les marques d’ordre d’octet sont conçues pour être des octets qui se produisent rarement dans le texte non-Unicode, ce qui permet d’estimer avec une raisonnable certitude que le texte est au format Unicode quand une marque d’ordre d’octet est présente.

Les marques d’ordre d’octet sont facultatives, et leur adoption n’est pas aussi populaire dans le monde de Linux, car une convention fiable d’UTF-8 est utilisée partout. La plupart des applications Linux partent du principe que l’entrée de texte est encodée en UTF-8. Bien que de nombreuses applications Linux reconnaissent et gèrent correctement les marques d’ordre d’octet, toutes ne le font pas, ce qui génère des artefacts dans le texte manipulé avec ces applications.

**Par conséquent** :

- Si vous travaillez principalement avec des applications Windows et Windows PowerShell, vous devez privilégier un encodage comme UTF-8 avec marque d’ordre d’octet ou UTF-16.
- Si vous travaillez sur plusieurs plateformes, vous devez privilégier UTF-8 avec marque d’ordre d’octet.
- Si vous travaillez principalement dans des contextes associés à Linux, vous devez privilégier UTF-8 sans marque d’ordre d’octet.
- Windows-1252 et latin-1 sont essentiellement des encodages hérités que vous devez éviter dans la mesure du possible.
  Toutefois, certaines applications Windows anciennes peuvent en dépendre.
- Il convient également de noter que la signature de script est [dépendante du codage](https://github.com/PowerShell/PowerShell/issues/3466), ce qui signifie qu’un changement de l’encodage sur un script signé nécessitera une nouvelle signature.

## <a name="configuring-vscode"></a>Configuration de VSCode

L’encodage par défaut de VSCode est UTF-8 sans marque d’ordre d’octet.

Pour définir l’[encodage de VSCode][], accédez aux paramètres VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) et définissez le paramètre `"files.encoding"` :

```json
"files.encoding": "utf8bom"
```

Voici quelques valeurs possibles :

- `utf8` : [UTF-8] sans marque d’ordre d’octet
- `utf8bom` : [UTF-8] avec marque d’ordre d’octet
- `utf16le` : Little endian [UTF-16]
- `utf16be` : Big endian [UTF-16]
- `windows1252` : [Windows-1252]

Vous devez obtenir une liste déroulante pour cette option dans la vue de l’interface graphique utilisateur, ou une complétion dans la vue JSON.

Vous pouvez aussi ajouter les éléments suivants pour détecter automatiquement l’encodage quand c’est possible :

```json
"files.autoGuessEncoding": true
```

Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations propres à un langage. Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`. Par exemple :

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configuration de PowerShell

L’encodage par défaut de PowerShell varie en fonction de la version :

- Dans PowerShell 6 et ultérieur, l’encodage par défaut est UTF-8 sans marque d’ordre d’octet sur toutes les plateformes.
- Dans Windows PowerShell, l’encodage par défaut est généralement Windows-1252, une extension de [latin-1][], également appelé ISO 8859-1.

Dans PowerShell 5 et ultérieur, vous pouvez déterminer votre encodage comme suit :

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Vous pouvez utiliser le [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) suivant pour déterminer quel encodage votre session PowerShell déduit pour un script sans marque d’ordre d’octet.

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

Il est possible de configurer PowerShell pour utiliser plus généralement un encodage donné à l’aide de paramètres de profil. Voir les articles suivants :

- La réponse de [@mklement0] concernant l’[encodage PowerShell sur StackOverflow](https://stackoverflow.com/a/40098904).
- Le billet de blog de [@rkeithhill] concernant le [traitement de l’entrée UTF-8 sans marque d’ordre d’octet dans PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Il n’est pas possible de forcer PowerShell à utiliser un encodage d’entrée spécifique. PowerShell 5.1 et antérieur utilisent par défaut l’encodage Windows-1252 quand il n’y a pas de marque d’ordre d’octet. Pour des raisons d’interopérabilité, il est préférable d’enregistrer les scripts dans un format Unicode avec une marque d’ordre d’octet.

> [!IMPORTANT]
> Tout autre outil qui traite des scripts PowerShell est susceptible d’être affecté par vos options d’encodage ou de ré-encoder vos scripts en un autre encodage.

### <a name="existing-scripts"></a>Scripts existants

Vous devrez peut-être réencoder les scripts déjà présents sur le système de fichiers vers votre nouvel encodage choisi. Dans la barre inférieure de VSCode, vous verrez l’étiquette UTF-8. Cliquez dessus pour ouvrir la barre d’action et sélectionnez **Enregistrer avec encodage**. Vous pouvez maintenant choisir un nouvel encodage pour ce fichier. Pour des instructions complètes, consultez [Encodage de VSCode][].

Si vous avez besoin de ré-encoder plusieurs fichiers, vous pouvez utiliser le script suivant :

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>Environnement d'écriture de scripts intégré (ISE) de PowerShell

Si vous modifiez également des scripts à l’aide de PowerShell ISE, vous devez y synchroniser vos paramètres d’encodage.

L’environnement ISE doit respecter une marque d’ordre d’octet, mais il est également possible d’utiliser la réflexion pour [définir l’encodage](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Notez que cela ne serait pas conservé d’un démarrage à un autre.

### <a name="source-control-software"></a>Logiciels de contrôle de code source

Certains outils de contrôle de code source, tels que GIT, ignorent les encodages. GIT ne fait que suivre les octets.
D’autres, tels que TFS ou Mercurial, sont susceptibles de ne pas le faire. Même certains outils GIT s’appuient sur le décodage du texte.

Quand c’est le cas, veillez à :

- Configurer l’encodage du texte dans votre contrôle de code source pour qu’il corresponde à votre configuration de VSCode.
- Vérifier que tous vos fichiers sont archivés dans le contrôle de code source dans l’encodage approprié.
- Méfiez-vous des modifications apportées à l’encodage reçues par le biais du contrôle de code source. Un exemple courant est quand une comparaison indique des changements, mais que rien ne semble avoir été changé (car les octets ont changé, mais pas les caractères).

### <a name="collaborators-environments"></a>Environnements des collaborateurs

En plus de la configuration du contrôle de code source, veillez à ce que vos collaborateurs qui travaillent sur des fichiers que vous partagez n’aient pas de paramètres qui remplacent votre encodage en réencodant les fichiers PowerShell.

### <a name="other-programs"></a>Autres programmes

Tout autre programme qui lit ou écrit un script PowerShell est susceptible de le ré-encoder.

Quelques exemples :

- Utilisation du Presse-papiers pour copier et coller un script. C’est courant dans les scénarios suivants :
  - Copie d’un script dans une machine virtuelle
  - Copie d’un script à partir d’un e-mail ou d’une page web
  - Copie d’un script dans ou à partir d’un document Microsoft Word ou PowerPoint
- Autres éditeurs de texte, tels que :
  - Bloc-notes
  - Vim
  - Tout autre éditeur de script PowerShell
- Utilitaires d’édition de texte, tels que :
  - `Get-Content`/`Set-Content`/`Out-File`
  - Opérateurs de redirection PowerShell comme `>` et `>>`
  - `sed`/`awk`
- Programmes de transfert de fichiers, tels que :
  - Un navigateur web, lors du téléchargement de scripts
  - Un partage de fichiers

Certains de ces outils traitent ses octets plutôt que du texte, mais d’autres offrent des configurations d’encodage. Dans les cas où vous devez configurer un encodage, vous devez faire en sorte qu’il soit identique à celui de votre éditeur afin d’éviter tout problème.

## <a name="other-resources-on-encoding-in-powershell"></a>Autres ressources sur l’encodage dans PowerShell

Il existe quelques autres billets intéressants sur l’encodage et sa configuration dans PowerShell qui méritent une lecture :

- Synthèse de [@mklement0] concernant l’[encodage PowerShell sur StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problèmes précédents ouverts sur vscode-PowerShell concernant l’encodage :
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Article classique de *Joel on Software* concernant Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Encodage dans .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marque d’ordre d’octet]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocole de serveur de langage]: https://microsoft.github.io/language-server-protocol/
[Encodage de VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
