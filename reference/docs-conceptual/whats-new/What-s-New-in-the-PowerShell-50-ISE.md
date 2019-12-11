---
ms.date: 09/06/2019
keywords: powershell,applet de commande
title: Nouveautés de PowerShell 5.0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416633"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Nouveauté de Windows PowerShell 5.0 ISE

Cette rubrique décrit les fonctionnalités nouvelles et mises à jour qui ont été introduites dans la version 5.0 de l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell.

> [!NOTE]
> L’environnement ISE PowerShell ne fait plus partie du développement de fonctionnalités actif. En tant que composant d’expédition de Windows, il continue d’être officiellement pris en charge pour la sécurité et les correctifs de maintenance de haute priorité.
> Nous n’avons actuellement aucun projet de supprimer l’environnement ISE de Windows.
>
> Il n’existe aucune prise en charge pour l’environnement ISE dans PowerShell v6 et versions ultérieures. Les utilisateurs cherchant à remplacer l’environnement ISE doivent utiliser [Visual Studio Code](https://code.visualstudio.com/) avec [l’extension PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="feature-description"></a>Description de la fonctionnalité

Windows PowerShell ISE est une application hôte qui permet d’écrire, d’exécuter et de tester des scripts et des modules dans un environnement graphique et intuitif. Ses fonctionnalités clés, telles que la coloration de syntaxe, la saisie automatique par tabulation, le débogage visuel, la compatibilité avec Unicode et l’aide contextuelle, fournissent une riche expérience d’écriture de scripts.

Pour plus d'informations, consultez [Présentation de Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

Le tableau suivant répertorie les fonctionnalités nouvelles et modifiées pour cette version de Windows PowerShell ISE dans Windows PowerShell.

## <a name="intellisense"></a>Intellisense

> Ajoutés dans ISE 3.0

IntelliSense est une fonctionnalité d’assistance de saisie semi-automatique qui fait partie de Windows PowerShell ISE.
Au fur et à mesure de la saisie, IntelliSense affiche des menus interactifs suggérant des applets de commande, des paramètres, des valeurs de paramètre, des fichiers ou des dossiers potentiellement appropriés.

**Quels avantages cette modification procure-t-elle ?**

L’ajout d’IntelliSense facilite la découverte d’applets de commande et de syntaxe quand vous utilisez Windows PowerShell ISE pour créer des scripts. Vous pouvez également utiliser Windows PowerShell ISE pour apprendre le fonctionnement de Windows PowerShell quand vous créez des scripts.

**En quoi le fonctionnement est-il différent ?**

Quand vous tapez des applets de commande dans Windows PowerShell ISE, un menu déroulant interactif s’affiche, dans lequel vous pouvez parcourir et sélectionner les commandes appropriées.

## <a name="snippets"></a>Extraits de code

> Ajoutés dans ISE 3.0

Les *extraits de code* sont de courtes sections de code Windows PowerShell que vous pouvez insérer dans les scripts que vous créez dans Windows PowerShell ISE. Windows PowerShell ISE est fourni avec un ensemble par défaut d’extraits de code. Vous pouvez ajouter des extraits de code en utilisant l’applet de commande `New-Snippet` tout en travaillant dans Windows PowerShell ISE.

**Quels avantages cette modification procure-t-elle ?**

Les extraits de code vous permettent d’assembler et de créer rapidement des scripts pour automatiser votre environnement.

**En quoi le fonctionnement est-il différent ?**

Pour utiliser des extraits de code dans Windows PowerShell 3.0 ou version ultérieure, dans le menu **Modifier**, cliquez sur **Démarrer les extraits** ou appuyez sur <kbd>Ctrl</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Outils complémentaires

> Ajout dans PowerShell 3.0

Windows PowerShell ISE prend désormais en charge les outils complémentaires à l’aide du modèle objet. Ces outils complémentaires sont des contrôles Windows Presentation Foundation (WPF) qui s’affichent sous la forme d’un volet vertical ou horizontal dans la console. Plusieurs outils complémentaires dans un volet sont affichés sous la forme d’un contrôle à onglets. Vous pouvez également ajouter ou supprimer des outils complémentaires produits par des éditeurs non-Microsoft. Pour plus d’informations, consultez [Objectif du modèle objet de script Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**Quels avantages cette modification procure-t-elle ?**

Les modules complémentaires vous permettent d’étendre et de personnaliser Windows PowerShell ISE avec des outils pouvant améliorer votre expérience de création de scripts ou ajouter des fonctionnalités.

**En quoi le fonctionnement est-il différent ?**

Windows PowerShell ISE 3.0 et versions ultérieures sont fournis avec le module complémentaire **Commandes**. Le module complémentaire **Commandes** permet de parcourir les applets de commande et d’accéder à l’aide sur les applets de commande, conjointement avec les volets **Script** et **Console**.

D’autres modules complémentaires sont accessibles via la commande **Ouvrir le site web des outils additionnels** du menu **Modules complémentaires**.

## <a name="restart-manager-and-auto-save"></a>Gestionnaire de démarrage et enregistrement automatique

> Ajout dans PowerShell 3.0

Désormais, Windows PowerShell ISE enregistre automatiquement vos scripts ouverts toutes les deux minutes dans un emplacement distinct. Lorsque Windows PowerShell ISE redémarre après un incident ou une panne inattendue, il récupère les scripts qui étaient ouverts dans la dernière session, même si les scripts n’ont pas été enregistrés.

Pour modifier l’intervalle d’enregistrement automatique, exécutez la commande suivante dans le volet de la console : `$psise.Options.AutoSaveMinuteInterval`.

**Quels avantages cette modification procure-t-elle ?**

Vous pouvez désormais travailler dans Windows PowerShell ISE, en sachant que vos scripts ouverts seront automatiquement enregistrés.

**En quoi le fonctionnement est-il différent ?**

Windows PowerShell ISE 2.0 n’enregistre pas automatiquement les scripts.

## <a name="most-recently-used-list"></a>Liste Utilisé(s) récemment

> Ajout dans PowerShell 3.0

Windows PowerShell ISE offre désormais une liste des derniers fichiers utilisés. Quand vous ouvrez un fichier dans Windows PowerShell ISE, celui-ci est ajouté à cette liste dans le menu **Fichier**.

Pour modifier le nombre par défaut de fichiers répertoriés dans la liste des derniers fichiers utilisés, exécutez la commande suivante dans le volet de la console : `$psise.Options.MruCount`.

**Quels avantages cette modification procure-t-elle ?**

Vous pouvez désormais utiliser la liste des derniers fichiers utilisés pour accéder facilement aux fichiers que vous utilisez fréquemment.

**En quoi le fonctionnement est-il différent ?**

Windows PowerShell ISE 2.0 n’offre pas de liste des derniers fichiers utilisés.

## <a name="console-pane"></a>Volet de la console

> Ajout dans PowerShell 3.0

Les volets de commande et de sortie distincts qui étaient disponibles dans la première version de Windows PowerShell ISE ont été combinés en un volet de console unique. Le volet de la console est similaire dans sa fonction et son apparence à une console Windows PowerShell standard, mais il inclut les améliorations ci-dessous :

- Coloration de la syntaxe pour le texte d’entrée (pas le texte de sortie), incluant la syntaxe XML
- Intellisense
- Accolades correspondantes
- Indication des erreurs
- Prise en charge complète d’Unicode
- Aide contextuelle accessible via la touche <kbd>F1</kbd>
- Fonctionnalité Show-Command contextuelle accessible via <kbd>Ctrl</kbd>+<kbd>F1</kbd>
- Scripts complexes et prise en charge de la saisie de droite à gauche
- Prise en charge des polices
- Zoom
- Modes de sélection de ligne et de sélection de bloc
- Préservation du contenu saisi dans la ligne de commande lorsque vous appuyez sur la touche <kbd>Haut</kbd> pour afficher l’historique dans la console

**Quels avantages cette modification procure-t-elle ?**

L’apport de ces modifications au volet de la console offre une expérience de création de scripts plus cohérente avec l’interface de la console.

**En quoi le fonctionnement est-il différent ?**

Windows PowerShell ISE 2.0 offre des volets de commande et de sortie distincts.

## <a name="command-line-switches"></a>Commutateurs de ligne de commande

> Ajout dans PowerShell 3.0

Si vous démarrez Windows PowerShell ISE à partir de la ligne de commande (en tapant **Powershell_ise.exe**), vous pouvez ajouter les nouveaux commutateurs de ligne de commande suivants.

- `-NoProfile` : démarre Windows PowerShell ISE sans exécuter `$profile`
- `-Help` : affiche une fenêtre d’aide
- `-mta` : démarre Windows PowerShell ISE en mode multithread cloisonné. Le mode d’opération par défaut pour Windows PowerShell ISE est un mode à thread unique cloisonné, ou `-sta`.

**Quels avantages cette modification procure-t-elle ?**

L’ajout de ces commutateurs de ligne de commande permet de contrôler l’environnement dans lequel Windows PowerShell ISE s’exécute.

**En quoi le fonctionnement est-il différent ?**

Windows PowerShell ISE 2.0 ne reconnaît pas ces commutateurs de ligne de commande.

## <a name="new-editor-features"></a>Nouvelles fonctionnalités de l’éditeur

> Ajout dans PowerShell 3.0

Les autres fonctionnalités d’édition de Windows PowerShell ISE sont les suivantes :

- **Coloration de la syntaxe XML** : Windows PowerShell ISE colore désormais la syntaxe XML de la même façon que la syntaxe Windows PowerShell.
- **Correspondance d’accolade** : Windows PowerShell ISE inclut des fonctions de correspondance et de mise en surbrillance des accolades, utilisables comme suit : par exemple, la commande **Accéder à Match** ou la combinaison de touches <kbd>Ctrl</kbd>+<kbd>]</kbd> permettent de localiser l’accolade fermante, si une accolade ouvrante est sélectionnée.
- **Mode Plan** Le volet Script prend en charge le mode Plan qui permet de réduire ou de développer des sections de code en cliquant sur les signes plus ou moins dans la marge gauche. Vous pouvez utiliser des accolades ou les balises `#region` et `#endregion` pour marquer le début ou la fin d’une section réductible. Pour développer ou réduire toutes les régions, appuyez sur <kbd>Ctrl</kbd>+<kbd>M</kbd>.
- **Édition du texte par glisser-déplacer** - Désormais, Windows PowerShell ISE prend en charge l’édition de texte par glisser-déplacer. Vous pouvez sélectionner un bloc de texte et faire glisser ce texte vers un autre emplacement dans l’éditeur ou la console afin de le déplacer. Si vous maintenez la touche <kbd>Ctrl</kbd> enfoncée pendant que vous faites glisser le texte sélectionné, lorsque vous relâchez le bouton de la souris, le texte est copié dans le nouvel emplacement. Dans cette version de Windows PowerShell ISE, quand vous glissez-déplacez un fichier vers Windows PowerShell ISE, ce dernier ouvre le fichier.
- **Affichage des erreurs d’analyse** - Les erreurs d’analyse sont indiquées par des soulignements rouges. Lorsque vous pointez sur une erreur indiquée, le texte d’info-bulle affiche le problème détecté dans le code.
- **Zoom** - Le pourcentage de zoom du contenu de la console peut être défini à l’aide du curseur de zoom (dans le coin inférieur droit de la fenêtre Windows PowerShell ISE) ou en tapant la commande `$psise.options.Zoom`dans le volet de la console.
- **Copie et collage de texte enrichi** - La copie dans le Presse-papiers dans Windows PowerShell ISE préserve les informations de police, de taille et de couleur de la sélection d’origine.
- **Sélection de bloc** - Vous pouvez sélectionner un bloc de texte en maintenant la touche <kbd>Alt</kbd> enfoncée tout en sélectionnant du texte dans le volet Script à l’aide de la souris, ou en appuyant sur <kbd>Alt</kbd>+<kbd>Maj</kbd>+<kbd>Flèche</kbd>.

**Quels avantages cette modification procure-t-elle ?**

Les fonctionnalités d’édition supplémentaires renforcent la cohérence et la puissance de l’environnement d’édition.

**En quoi le fonctionnement est-il différent ?**

Ces améliorations des fonctionnalités d’édition ne figuraient pas dans Windows PowerShell ISE 2.0.

## <a name="new-help-viewer-window"></a>Nouvelle fenêtre de visionneuse d’aide

> Ajout dans PowerShell 3.0

Si vous appuyez sur <kbd>F1</kbd> quand le curseur est dans une applet de commande ou si une partie d’une applet de commande est en surbrillance, la nouvelle visionneuse d’aide ouvre une aide contextuelle sur l’applet de commande en surbrillance. Pour afficher les rubriques d’aide **conceptuelle** de Windows PowerShell, tapez `operators` dans le volet de la console, puis appuyez sur <kbd>F1</kbd>.

Avant d’utiliser cette fonctionnalité, téléchargez la dernière version des rubriques d’aide de Windows PowerShell à partir du site web de Microsoft. La méthode la plus simple pour télécharger les rubriques d’aide consiste à exécuter l’applet de commande `Update-Help` dans le volet de la console durant l’exécution de Windows PowerShell ISE en tant qu’administrateur.

Vous pouvez modifier l’emplacement dans lequel la touche <kbd>F1</kbd> recherche de l’aide. Dans le menu **Outils**/**Options**, sous l’onglet **Paramètres généraux**, sous **Autres paramètres**, vous pouvez cocher ou décocher la case **Utiliser le contenu de l’aide locale au lieu du contenu en ligne**. Si la case à cocher est activée, le client recherche de l’aide sur l’applet de commande dans l’aide téléchargée figurant dans le dossier modules. Si la case à cocher est désactivée, le client recherche de l’aide en ligne.

**Quels avantages cette modification procure-t-elle ?**

L’aide contextuelle accessible sans quitter votre applet de commande ou script actifs vous permet de bénéficier d’une expérience d’apprentissage intégrée.

**En quoi le fonctionnement est-il différent ?**

Dans les versions précédentes de Windows PowerShell ISE, l’appui sur la touche <kbd>F1</kbd> ouvrait le fichier d’aide sur l’ordinateur local. Dans Windows PowerShell ISE 3.0 et versions ultérieures, une fenêtre s’ouvre, affichant l’aide sur l’applet de commande, qui est consultable et configurable. Cette expérience d’aide est une nouveauté pour Windows PowerShell ISE 3.0, et l’aide actualisable est une nouveauté pour Windows PowerShell 3.0.

## <a name="show-command-cmdlet"></a>Applet de commande Show-Command

> Ajout dans PowerShell 3.0

L’applet de commande `Show-Command` permet de composer ou d’exécuter une applet de commande ou une fonction en remplissant un formulaire graphique. Le formulaire permet aux utilisateurs d’utiliser Windows PowerShell dans un environnement graphique.
`Show-Command` permet également aux créateurs de scripts chevronnés de créer une interface utilisateur graphique rapide basée sur Windows PowerShell.

**Quels avantages cette modification procure-t-elle ?**

En utilisant `Show-Command` dans vos scripts Windows PowerShell, vous pouvez fournir à vos utilisateurs un environnement graphique familier. `Show-Command` peut également faciliter l’apprentissage de Windows PowerShell pour des utilisateurs débutants.

**En quoi le fonctionnement est-il différent ?**

`Show-Command` est nouveau dans Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur l’utilisation de Windows PowerShell ISE, consultez [Explorer l’environnement d’écriture de scripts intégré de Windows PowerShell](../components/ise/exploring-the-windows-powershell-ise.md).
