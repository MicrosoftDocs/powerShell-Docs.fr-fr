---
title: Modification des articles de référence
description: Cet article explique les conditions requises pour modifier les informations de référence sur les cmdlets et les rubriques About_ de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624769"
---
# <a name="editing-reference-articles"></a>Modification des articles de référence

Les articles de référence sur les cmdlets présentent une structure spécifique. La structure est définie par [PlatyPS][].
PlatyPS génère l’aide des cmdlets pour les modules PowerShell en Markdown. Après la modification des fichiers Markdown, PlatyPS permet de créer les fichiers d’aide MAML utilisés par la cmdlet `Get-Help`.

PlatyPS possède un schéma codé en dur pour les informations de référence sur les cmdlets écrites dans le code. Le document [platyPS.schema.md][] tente de décrire cette structure. Les violations de schéma entraînent des erreurs de build que vous devez corriger pour que votre contribution puisse être acceptée.

## <a name="general-guidelines"></a>Recommandations générales

- Ne supprimez aucune des structures d’en-tête. PlatyPS attend un ensemble spécifique d’en-têtes.
- Les en-têtes **Type d’entrée** et **Type de sortie** doivent avoir un type. Si la cmdlet ne prend pas d’entrée ou ne retourne pas de valeur, utilisez la valeur `None`.
- Les blocs de code délimités ne sont autorisés que dans la section [Exemples](#structuring-examples).
- Les morceaux de code inline peuvent être utilisés dans n’importe quel paragraphe.

## <a name="formatting-about_-files"></a>Mise en forme des fichiers About_

Les fichiers `About_*` sont écrits dans Markdown mais sont fournis en tant que fichiers texte bruts. Nous utilisons [Pandoc][] pour convertir Markdown en texte brut. Leur mise en forme répond à l’objectif de maximiser la compatibilité dans toutes les versions de PowerShell et avec les outils de publication.

Instructions de mise en forme de base :

- Limitez les lignes à 80 caractères. Pandoc met en retrait certains blocs Markdown, de sorte que ces blocs doivent être ajustés.
  - Les blocs de code sont limités à 76 caractères
  - Les tables sont limitées à 76 caractères
  - Les citations (et les alertes) sont limitées à 78 caractères

- Si vous utilisez les méta-caractères spéciaux Pandoc `\`, `$` et `<`
  - Dans un en-tête : ils doivent être placés dans une séquence d’échappement précédée d’un caractère `\` ou dans des morceaux de code entre accents graves (`` ` ``)
  - Dans un paragraphe : ils doivent être placés dans un morceau de code. Par exemple :

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- Les tables doivent tenir dans 76 caractères.
  - Ajoutez manuellement des retours à la ligne au contenu des cellules.
  - Utilisez des caractères `|` ouvrants et fermants sur chaque ligne.
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
    > La limite de 76 colonnes s’applique uniquement aux rubriques `About_*`. Vous pouvez utiliser des colonnes larges dans les articles de référence sur les cmdlets ou conceptuelles.

## <a name="structuring-examples"></a>Structuration des exemples

Dans le schéma PlatyPS, l’en-tête **EXEMPLES** est un en-tête H2 et chaque exemple est un en-tête H3.

Le schéma ne permet pas de séparer les blocs de code par des paragraphes dans un exemple. Voici le schéma pris en charge :

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Numérotez chaque exemple et ajoutez un titre court.

Par exemple :

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>Exemple 1 : Récupérer les cmdlets, les fonctions et les alias

Cette commande permet d’obtenir les cmdlets, fonctions et alias PowerShell installés sur l’ordinateur.

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>Exemple 2 : Récupérer les commandes de la session active

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>Étapes suivantes

[Liste de contrôle éditoriale](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
