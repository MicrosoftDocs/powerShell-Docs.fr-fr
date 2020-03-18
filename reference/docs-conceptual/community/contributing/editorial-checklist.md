---
title: Liste de contrôle éditoriale
description: Il s’agit d’une liste résumée des règles de modification de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060334"
---
# <a name="editors-checklist"></a>Liste de contrôle de l’éditeur

Il s’agit d’un résumé des règles à appliquer lors de l’écriture de nouveaux articles ou de la mise à jour d’articles existants. Pour des explications détaillées et des exemples de ces règles, consultez les autres articles du Guide du contributeur.

## <a name="metadata"></a>Métadonnées

- `ms.date` : doit être au format **MM/JJ/AAAA**.
  - Modifier la date en cas de mise à jour importante ou factuelle :
    - réorganisation de l’article ;
    - correction d’erreurs factuelles ;
    - ajout de nouvelles informations.
  - Ne pas modifier la date si la mise à jour n’est pas significative :
    - correction de fautes de frappe et de la mise en forme.
- `title` : chaîne unique de 43-59 caractères, espaces compris.
  - Ne pas inclure l’identificateur de site (il est généré automatiquement).
  - Utiliser une majuscule pour le premier mot et les noms propres uniquement.
- `description`: 115-145 caractères espaces compris. Ce résumé s’affiche dans le résultat de la recherche.

## <a name="formatting"></a>Mise en forme

- Éléments de syntaxe avec accent grave qui s’affichent en ligne dans un paragraphe :
  - nom des cmdlets `Verb-Noun` ;
  - variable `$counter` ;
  - exemples syntaxiques `Verb-Noun -Parameter` ;
  - chemins de fichiers `C:\Program Files\PowerShell`, `/usr/bin/pwsh` ;
  - URL qui ne sont pas censées être cliquables dans le document.
- Mettre en gras les noms de propriétés, les valeurs de paramètres, les noms de paramètres, les noms de classes, les noms de modules, les noms d’entités, les noms d’objets et les noms de types.
  - Les caractères gras servent au balisage sémantique et non à l’accentuation.
  - Gras : utiliser des astérisques `**`.
- Italique : utiliser le trait de soulignement `_`.
  - L’italique sert uniquement à l’accentuation et non au balisage sémantique.
- Sauts de ligne à 100 colonnes (ou 80 pour **about_Topics**).
- Pas d’onglets en dur : utiliser uniquement des espaces.
- Pas d’espace de fin sur les lignes.

### <a name="headers"></a>headers

- H1 arrive en premier : un seul H1 par article.
- Utiliser uniquement des [en-têtes ATX](https://github.github.com/gfm/#atx-headings).
- Mettre la première lettre des phrases en majuscule pour les en-têtes.
- N’ignorer aucun niveau : pas de H3 sans H2.
- Profondeur maximale : H3 ou H4.
- Ligne vide avant et après.
- PlatyPS applique des en-têtes spécifiques dans son schéma : n’ajouter ni ne supprimer aucun en-tête.

### <a name="code-blocks"></a>Blocs de code

- Ligne vide avant et après.
- Utiliser des limites de code balisées : **powershell**, **Output** ou tout autre ID de langage adapté.
- Limite non balisée : blocs syntaxiques ou autres shells.
- Placer **Output** dans un bloc de code distinct, sauf pour les exemples simples où le lecteur n’est pas censé utiliser le bouton **Copier**.
- Voir la liste des [langages pris en charge](/contribute/code-in-docs#supported-languages).

### <a name="lists"></a>Listes

- Mise en retrait correcte.
- Ligne vide avant le premier élément et après le dernier.
- Puce : utiliser le trait d’union (`-`) et non l’astérisque (`*`), trop facile à confondre avec l’accentuation.
- Pour les listes numérotées, tous les nombres sont « 1 ».

## <a name="terminology"></a>Terminologie

- PowerShell, Windows PowerShell ou PowerShell Core
- Voir [Terminologie des produits](powershell-style-guide.md#product-terminology).

## <a name="cmdlet-reference-examples"></a>Exemples d’informations de référence sur les cmdlets

- Les informations de référence sur les cmdlets doivent comporter au moins un exemple.
- Les exemples doivent contenir juste assez de code pour illustrer leur usage.
- Syntaxe PowerShell :
  - Utiliser le nom complet des cmdlets et des paramètres, sans alias.
  - Utiliser la projection pour les paramètres lorsque la ligne de commande est trop longue.
  - Éviter autant que possible d’utiliser des accents graves de continuation de ligne.
- Supprimer ou simplifier l’invite PowerShell (`PS>`), sauf si l’exemple l’exige.
- L’exemple d’informations de référence sur les cmdlets doit suivre le schéma PlatyPS suivant :

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- Ne pas placer de paragraphes entre les blocs de code. Tout le contenu descriptif doit venir avant ou après les blocs de code.

## <a name="linking-to-other-documents"></a>Lien vers d’autres documents

- Les liens extérieurs à l’ensemble de documents ou entre informations de référence sur les cmdlets sont conceptuels :
  - Utiliser des URL relatives pour les liens vers docs.microsoft.com (supprimer `https://docs.microsoft.com/en-us`).
  - Ne pas inclure de paramètres régionaux dans les URL sur les propriétés Microsoft (par exemple, supprimer `/en-us` dans l’URL).
  - Toutes les URL de sites web externes doivent utiliser le protocole HTTPS, sauf si ce n’est pas valide pour le site cible.
- Au sein de l’ensemble de documents :
  - Lien vers le chemin d’un fichier (par exemple, `../folder/file.md`).
  - Tous les chemins de fichiers utilisent des barres obliques (`/`).
- Les liens d’images doivent comporter un texte de remplacement unique.
