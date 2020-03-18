---
title: Modification des articles de référence
description: Cet article explique les conditions requises pour modifier les informations de référence sur les cmdlets et les rubriques About_ de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3c6f1b4fc27ca8ece7ec30317daf4ed2a6bc9228
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060324"
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

Les fichiers `About_*` sont maintenant traités par [Pandoc][] et non plus par PlatyPS. Leur mise en forme répond à l’objectif de maximiser la compatibilité dans toutes les versions de PowerShell et avec les outils de publication.

Instructions de mise en forme de base :

- Limitez les lignes à 80 caractères.
- Les blocs de code et les tables sont limités à 76 caractères, car Pandoc ajoute un retrait de quatre espaces lors de la conversion en texte brut.
- Les tables doivent tenir dans 76 caractères.
  - Ajoutez manuellement des retours à la ligne au contenu des cellules.
  - Utilisez des caractères `|` ouvrants et fermants sur chaque ligne.
  - Vous trouverez un exemple fonctionnel dans [about_Comparison_Operators][about-example].
- Si vous utilisez les caractères spéciaux Pandoc `\`, `$` et `<` :
  - Dans un en-tête : ils doivent être placés dans une séquence d’échappement précédée d’un caractère `\` ou entre accents graves (`` ` ``)
  - Dans un paragraphe : ils doivent être placés dans un morceau de code. Par exemple :

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

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
[about-example]: https://github.com/MicrosoftDocs/PowerShell-Docs/reference/5.1/Microsoft.PowerShell.Core/About/about_Comparison_Operators.md
[Pandoc]: https://pandoc.org
