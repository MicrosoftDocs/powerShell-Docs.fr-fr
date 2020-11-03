---
description: PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de PSReadLine
ms.openlocfilehash: 890f8e92172f2d492b6b817b558d4f25c70e8949
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206561"
---
# <a name="psreadline"></a>PSReadLine

## <a name="about_psreadline"></a>about_PSReadLine

## <a name="short-description"></a>DESCRIPTION COURTE

PSReadLine fournit une expérience d’édition de ligne de commande améliorée dans la console PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

PSReadLine 2,0 fournit une expérience d’édition de ligne de commande puissante pour la console PowerShell. Elle offre les possibilités suivantes :

- Coloration de la syntaxe de la ligne de commande
- Indication visuelle des erreurs de syntaxe
- Une meilleure expérience multi-ligne (modification et historique)
- Combinaisons de touches personnalisables
- Modes cmd et Emacs
- Nombreuses options de configuration
- Saisie semi-automatique du style bash (facultatif en mode cmd, par défaut en mode emacs)
- Emacs-Yank/Kill-Ring
- Mouvement « mot » basé sur un jeton PowerShell et Kill

Les fonctions suivantes sont disponibles dans la classe **[Microsoft. PowerShell. PSConsoleReadLine]** .

> [!NOTE]
> À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté. Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran. Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement. Vous pouvez charger le module manuellement, si nécessaire.

## <a name="basic-editing-functions"></a>Fonctions d’édition de base

### <a name="abort"></a>Abandon

Annuler l’action en cours, par exemple, recherche de l’historique incrémentiel.

- Emacs- `<Ctrl+g>`

### <a name="acceptandgetnext"></a>AcceptAndGetNext

Tentative d’exécution de l’entrée en cours. Si elle peut être exécutée (par exemple, AcceptLine), rappelez l’élément suivant de l’historique la prochaine fois que ReadLine est appelé.

- Emacs- `<Ctrl+o>`

### <a name="acceptline"></a>AcceptLine

Tentative d’exécution de l’entrée en cours. Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.

- Cmd `<Enter>`
- Emacs- `<Enter>`
- Mode d’insertion VI : `<Enter>`

### <a name="addline"></a>AddLine

L’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle. Cela est utile pour entrer une entrée multiligne sous la forme d’une commande unique, même lorsqu’une seule ligne est complète en entrée.

- Cmd `<Shift+Enter>`
- Emacs- `<Shift+Enter>`
- Mode d’insertion VI : `<Shift+Enter>`
- Mode de commande VI : `<Shift+Enter>`

### <a name="backwarddeletechar"></a>BackwardDeleteChar

Supprimez le caractère avant le curseur.

- Cmd : `<Backspace>` , `<Ctrl+h>`
- Emacs : `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`
- Mode d’insertion VI : `<Backspace>`
- Mode de commande VI : `<X>` , `<d,h>`

### <a name="backwarddeleteline"></a>BackwardDeleteLine

Comme BackwardKillLine-supprime le texte du point jusqu’au début de la ligne, mais ne place pas le texte supprimé dans l’anneau d’arrêt.

- Cmd `<Ctrl+Home>`
- Mode d’insertion VI : `<Ctrl+u>` , `<Ctrl+Home>`
- Mode de commande VI : `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`

### <a name="backwarddeleteword"></a>BackwardDeleteWord

Supprime le mot précédent.

- Mode de commande VI : `<Ctrl+w>` , `<d,b>`

### <a name="backwardkillline"></a>BackwardKillLine

Effacez l’entrée à partir du début de l’entrée jusqu’au curseur. Le texte effacé est placé dans le Kill-Ring.

- Emacs- `<Ctrl+u>` , `<Ctrl+x,Backspace>`

### <a name="backwardkillword"></a>BackwardKillWord

Efface l’entrée du début du mot actuel jusqu’au curseur. Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur. Le texte effacé est placé dans le Kill-Ring.

- Cmd `<Ctrl+Backspace>`
- Emacs- `<Alt+Backspace>` , `<Escape,Backspace>`
- Mode d’insertion VI : `<Ctrl+Backspace>`
- Mode de commande VI : `<Ctrl+Backspace>`

### <a name="cancelline"></a>CancelLine

Annule l’entrée actuelle, en laissant l’entrée à l’écran, mais retourne à l’hôte afin que l’invite soit de nouveau évaluée.

- Mode d’insertion VI : `<Ctrl+c>`
- Mode de commande VI : `<Ctrl+c>`

### <a name="copy"></a>Copier

Copier la région sélectionnée dans le presse-papiers du système. Si aucune région n’est sélectionnée, copiez la ligne entière.

- Cmd `<Ctrl+C>`

### <a name="copyorcancelline"></a>CopyOrCancelLine

Si le texte est sélectionné, copiez-le dans le presse-papiers, sinon, annulez la ligne.

- Cmd `<Ctrl+c>`
- Emacs- `<Ctrl+c>`

### <a name="cut"></a>Couper

Supprimer la zone sélectionnée en plaçant le texte supprimé dans le presse-papiers du système.

- Cmd `<Ctrl+x>`

### <a name="deletechar"></a>DeleteChar

Supprimez le caractère sous le curseur.

- Cmd `<Delete>`
- Emacs- `<Delete>`
- Mode d’insertion VI : `<Delete>`
- Mode de commande VI : `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`

### <a name="deletecharorexit"></a>DeleteCharOrExit

Supprimez le caractère sous le curseur, ou si la ligne est vide, quittez le processus.

- Emacs- `<Ctrl+d>`

### <a name="deleteendofword"></a>DeleteEndOfWord

Supprimer à la fin du mot.

- Mode de commande VI : `<d,e>`

### <a name="deleteline"></a>DeleteLine

Supprime la ligne active, en activant l’annulation.

- Mode de commande VI : `<d,d>`

### <a name="deletelinetofirstchar"></a>DeleteLineToFirstChar

Supprime le texte du curseur jusqu’au premier caractère non vide de la ligne.

- Mode de commande VI : `<d,^>`

### <a name="deletetoend"></a>DeleteToEnd

Supprimer à la fin de la ligne.

- Mode de commande VI : `<D>` , `<d,$>`

### <a name="deleteword"></a>DeleteWord

Supprimer le mot suivant.

- Mode de commande VI : `<d,w>`

### <a name="forwarddeleteline"></a>ForwardDeleteLine

Comme ForwardKillLine-supprime le texte du point jusqu’à la fin de la ligne, mais ne place pas le texte supprimé dans l’anneau Kill.

- Cmd `<Ctrl+End>`
- Mode d’insertion VI : `<Ctrl+End>`
- Mode de commande VI : `<Ctrl+End>`

### <a name="insertlineabove"></a>InsertLineAbove

Une nouvelle ligne vide est créée au-dessus de la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active. Le curseur se déplace au début de la nouvelle ligne.

- Cmd `<Ctrl+Enter>`

### <a name="insertlinebelow"></a>InsertLineBelow

Une nouvelle ligne vide est créée sous la ligne active, quel que soit l’endroit où se trouve le curseur sur la ligne active. Le curseur se déplace au début de la nouvelle ligne.

- Cmd `<Shift+Ctrl+Enter>`

### <a name="invertcase"></a>InvertCase

Inverser la casse du caractère actuel et passer au suivant.

- Mode de commande VI : `<~>`

### <a name="killline"></a>KillLine

Effacez l’entrée du curseur jusqu’à la fin de l’entrée. Le texte effacé est placé dans le Kill-Ring.

- Emacs- `<Ctrl+k>`

### <a name="killregion"></a>KillRegion

Supprimer le texte situé entre le curseur et la marque.

- La fonction est indépendante.

### <a name="killword"></a>KillWord

Efface l’entrée du curseur jusqu’à la fin du mot actuel. Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant. Le texte effacé est placé dans le Kill-Ring.

- Cmd `<Ctrl+Delete>`
- Emacs- `<Alt+d>` , `<Escape,d>`
- Mode d’insertion VI : `<Ctrl+Delete>`
- Mode de commande VI : `<Ctrl+Delete>`

### <a name="paste"></a>Coller

Collez le texte à partir du presse-papiers du système.

- Cmd : `<Ctrl+v>` , `<Shift+Insert>`
- Mode d’insertion VI : `<Ctrl+v>`
- Mode de commande VI : `<Ctrl+v>`

> [!IMPORTANT]
> Lors de l’utilisation de la fonction **Paste** , le contenu entier de la mémoire tampon du presse-papiers est collé dans la mémoire tampon d’entrée de PSReadLine. La mémoire tampon d’entrée est ensuite transmise à l’analyseur PowerShell. L’entrée collée à l’aide de la méthode de collage **avec le bouton droit** de la console de l’application de console est copiée dans la mémoire tampon d’entrée un caractère à la fois. La mémoire tampon d’entrée est transmise à l’analyseur lorsqu’un caractère de saut de ligne est copié. Par conséquent, l’entrée est analysée une ligne à la fois. La différence entre les méthodes de collage entraîne un comportement d’exécution différent.

### <a name="pasteafter"></a>PasteAfter

Collez le presse-papiers après le curseur, en déplaçant le curseur à la fin du texte collé.

- Mode de commande VI : `<p>`

### <a name="pastebefore"></a>PasteBefore

Collez le presse-papiers avant le curseur, en déplaçant le curseur à la fin du texte collé.

- Mode de commande VI : `<P>`

### <a name="prependandaccept"></a>PrependAndAccept

Faites précéder un' # 'et acceptez la ligne.

- Mode de commande VI : `<#>`

### <a name="redo"></a>Rétablir

Annule une annulation.

- Cmd `<Ctrl+y>`
- Mode d’insertion VI : `<Ctrl+y>`
- Mode de commande VI : `<Ctrl+y>`

### <a name="repeatlastcommand"></a>RepeatLastCommand

Répète la dernière modification de texte.

- Mode de commande VI : `<.>`

### <a name="revertline"></a>RevertLine

Rétablit toutes les entrées de l’entrée actuelle.

- Cmd `<Escape>`
- Emacs- `<Alt+r>` , `<Escape,r>`

### <a name="shellbackwardkillword"></a>ShellBackwardKillWord

Efface l’entrée du début du mot actuel jusqu’au curseur. Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur. Le texte effacé est placé dans le Kill-Ring.

La fonction est indépendante.

### <a name="shellkillword"></a>ShellKillWord

Efface l’entrée du curseur jusqu’à la fin du mot actuel. Si le curseur se trouve entre des mots, l’entrée est effacée du curseur jusqu’à la fin du mot suivant. Le texte effacé est placé dans le Kill-Ring.

La fonction est indépendante.

### <a name="swapcharacters"></a>SwapCharacters

Permuter le caractère actuel et celui qui le précèdent.

- Emacs- `<Ctrl+t>`
- Mode d’insertion VI : `<Ctrl+t>`
- Mode de commande VI : `<Ctrl+t>`

### <a name="undo"></a>Annuler

Annuler une modification précédente.

- Cmd `<Ctrl+z>`
- Emacs- `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`
- Mode d’insertion VI : `<Ctrl+z>`
- Mode de commande VI : `<Ctrl+z>` , `<u>`

### <a name="undoall"></a>UndoAll

Annule toutes les modifications précédentes pour la ligne.

- Mode de commande VI : `<U>`

### <a name="unixwordrubout"></a>UnixWordRubout

Efface l’entrée du début du mot actuel jusqu’au curseur. Si le curseur se trouve entre des mots, l’entrée est effacée du début du mot précédent au curseur. Le texte effacé est placé dans le Kill-Ring.

- Emacs- `<Ctrl+w>`

### <a name="validateandacceptline"></a>ValidateAndAcceptLine

Tentative d’exécution de l’entrée en cours. Si l’entrée actuelle est incomplète (par exemple, il manque une parenthèse fermante, un crochet ou un guillemet, l’invite de continuation est affichée sur la ligne suivante et PSReadLine attend que les clés modifient l’entrée actuelle.

- Emacs- `<Ctrl+m>`

### <a name="viacceptline"></a>ViAcceptLine

Acceptez la ligne et passez en mode insertion.

- Mode de commande VI : `<Enter>`

### <a name="viacceptlineorexit"></a>ViAcceptLineOrExit

Comme DeleteCharOrExit en mode emacs, mais accepte la ligne au lieu de supprimer un caractère.

- Mode d’insertion VI : `<Ctrl+d>`
- Mode de commande VI : `<Ctrl+d>`

### <a name="viappendline"></a>ViAppendLine

Une nouvelle ligne est insérée au-dessous de la ligne active.

- Mode de commande VI : `<o>`

### <a name="vibackwarddeleteglob"></a>ViBackwardDeleteGlob

Supprime le mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.

- Mode de commande VI : `<d,B>`

### <a name="vibackwardglob"></a>ViBackwardGlob

Déplace le curseur au début du mot précédent, en utilisant uniquement des espaces blancs comme délimiteurs.

- Mode de commande VI : `<B>`

### <a name="videletebrace"></a>ViDeleteBrace

Recherchez l’accolade correspondante, la parenthèse ou le crochet, et supprimez tout le contenu dans, y compris l’accolade.

- Mode de commande VI : `<d,%>`

### <a name="videleteendofglob"></a>ViDeleteEndOfGlob

Supprimer à la fin du mot.

- Mode de commande VI : `<d,E>`

### <a name="videleteglob"></a>ViDeleteGlob

Supprime la glob suivante (mot blanc délimité par des espaces).

- Mode de commande VI : `<d,W>`

### <a name="videletetobeforechar"></a>ViDeleteToBeforeChar

Supprime jusqu’au caractère donné.

- Mode de commande VI : `<d,t>`

### <a name="videletetobeforecharbackward"></a>ViDeleteToBeforeCharBackward

Supprime jusqu’au caractère donné.

- Mode de commande VI : `<d,T>`

### <a name="videletetochar"></a>ViDeleteToChar

Supprime jusqu’au caractère donné.

- Mode de commande VI : `<d,f>`

### <a name="videletetocharbackward"></a>ViDeleteToCharBackward

Supprime vers l’arrière jusqu’au caractère donné.

- Mode de commande VI : `<d,F>`

### <a name="viinsertatbegining"></a>ViInsertAtBegining

Basculez en mode insertion et positionnez le curseur au début de la ligne.

- Mode de commande VI : `<I>`

### <a name="viinsertatend"></a>ViInsertAtEnd

Basculez en mode insertion et positionnez le curseur à la fin de la ligne.

- Mode de commande VI : `<A>`

### <a name="viinsertline"></a>ViInsertLine

Une nouvelle ligne est insérée au-dessus de la ligne active.

- Mode de commande VI : `<O>`

### <a name="viinsertwithappend"></a>ViInsertWithAppend

Ajouter à partir de la position de la ligne active.

- Mode de commande VI : `<a>`

### <a name="viinsertwithdelete"></a>ViInsertWithDelete

Supprimez le caractère actuel et basculez en mode insertion.

- Mode de commande VI : `<s>`

### <a name="vijoinlines"></a>ViJoinLines

Joint la ligne active et la ligne suivante.

- Mode de commande VI : `<J>`

### <a name="vireplaceline"></a>ViReplaceLine

Effacez l’intégralité de la ligne de commande.

- Mode de commande VI : `<S>` , `<c,c>`

### <a name="vireplacetobeforechar"></a>ViReplaceToBeforeChar

Remplace jusqu’au caractère donné.

- Mode de commande VI : `<c,t>`

### <a name="vireplacetobeforecharbackward"></a>ViReplaceToBeforeCharBackward

Remplace jusqu’au caractère donné.

- Mode de commande VI : `<c,T>`

### <a name="vireplacetochar"></a>ViReplaceToChar

Supprime jusqu’au caractère donné.

- Mode de commande VI : `<c,f>`

### <a name="vireplacetocharbackward"></a>ViReplaceToCharBackward

Remplace jusqu’au caractère donné.

- Mode de commande VI : `<c,F>`

### <a name="viyankbeginningofline"></a>ViYankBeginningOfLine

Yank entre le début de la mémoire tampon et le curseur.

- Mode de commande VI : `<y,0>`

### <a name="viyankendofglob"></a>ViYankEndOfGlob

Yank du curseur jusqu’à la fin du ou des mots.

- Mode de commande VI : `<y,E>`

### <a name="viyankendofword"></a>ViYankEndOfWord

Yank du curseur jusqu’à la fin du ou des mots.

- Mode de commande VI : `<y,e>`

### <a name="viyankleft"></a>ViYankLeft

Yank caractère (s) à gauche du curseur.

- Mode de commande VI : `<y,h>`

### <a name="viyankline"></a>ViYankLine

Yank la mémoire tampon entière.

- Mode de commande VI : `<y,y>`

### <a name="viyanknextglob"></a>ViYankNextGlob

Yank à partir d’un curseur jusqu’au début du ou des mots suivants.

- Mode de commande VI : `<y,W>`

### <a name="viyanknextword"></a>ViYankNextWord

Yank le ou les mots après le curseur.

- Mode de commande VI : `<y,w>`

### <a name="viyankpercent"></a>ViYankPercent

Yank à/à partir de l’accolade correspondante.

- Mode de commande VI : `<y,%>`

### <a name="viyankpreviousglob"></a>ViYankPreviousGlob

Yank entre le début du ou des mots et le curseur.

- Mode de commande VI : `<y,B>`

### <a name="viyankpreviousword"></a>ViYankPreviousWord

Yank le ou les mots avant le curseur.

- Mode de commande VI : `<y,b>`

### <a name="viyankright"></a>ViYankRight

Yank caractère (s) situé sous et à droite du curseur.

- Mode de commande VI : `<y,l>` , `<y,Space>`

### <a name="viyanktoendofline"></a>ViYankToEndOfLine

Yank du curseur jusqu’à la fin de la mémoire tampon.

- Mode de commande VI : `<y,$>`

### <a name="viyanktofirstchar"></a>ViYankToFirstChar

Yank du premier caractère autre qu’un espace blanc au curseur.

- Mode de commande VI : `<y,^>`

### <a name="yank"></a>Yank

Ajoutez le texte le plus récemment supprimé à l’entrée.

- Emacs- `<Ctrl+y>`

### <a name="yanklastarg"></a>YankLastArg

Yank le dernier argument de la ligne d’historique précédente. Avec un argument, la première fois qu’il est appelé, se comporte comme YankNthArg. Si elle est appelée plusieurs fois, elle itère au sein de l’historique et ARG définit la direction (négatif inverse la direction).

- Cmd `<Alt+.>`
- Emacs : `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`

### <a name="yankntharg"></a>YankNthArg

Yank le premier argument (après la commande) à partir de la ligne précédente de l’historique.
Avec un argument, Yank le nième argument (à partir de 0), si l’argument est négatif, commencez par le dernier argument.

- Emacs- `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`

### <a name="yankpop"></a>YankPop

Si l’opération précédente était Yank ou YankPop, remplacez le texte précédemment extrait par le texte supprimé suivant de l’instruction KILL-Ring.

- Emacs- `<Alt+y>` , `<Escape,y>`

## <a name="cursor-movement-functions"></a>Fonctions de déplacement de curseur

### <a name="backwardchar"></a>BackwardChar

Déplacer le curseur d’un caractère vers la gauche. Cela peut déplacer le curseur vers la ligne précédente de l’entrée multiligne.

- Cmd `<LeftArrow>`
- Emacs- `<LeftArrow>` , `<Ctrl+b>`
- Mode d’insertion VI : `<LeftArrow>`
- Mode de commande VI : `<LeftArrow>` , `<Backspace>` , `<h>`

### <a name="backwardword"></a>BackwardWord

Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent. Les limites de mots sont définies par un jeu de caractères configurable.

- Cmd `<Ctrl+LeftArrow>`
- Emacs- `<Alt+b>` , `<Escape,b>`
- Mode d’insertion VI : `<Ctrl+LeftArrow>`
- Mode de commande VI : `<Ctrl+LeftArrow>`

### <a name="beginningofline"></a>BeginningOfLine

Si l’entrée comporte plusieurs lignes, se déplacer au début de la ligne active ou, le cas échéant, au début de la ligne, se déplacer au début de l’entrée. Si l’entrée comporte une seule ligne, accédez au début de l’entrée.

- Cmd `<Home>`
- Emacs- `<Home>` , `<Ctrl+a>`
- Mode d’insertion VI : `<Home>`
- Mode de commande VI : `<Home>`

### <a name="endofline"></a>EndOfLine

Si l’entrée comporte plusieurs lignes, passez à la fin de la ligne active ou, si elle se trouve déjà à la fin de la ligne, à la fin de l’entrée. Si l’entrée comporte une seule ligne, passez à la fin de l’entrée.

- Cmd `<End>`
- Emacs- `<End>` , `<Ctrl+e>`
- Mode d’insertion VI : `<End>`

### <a name="forwardchar"></a>ForwardChar

Déplacer le curseur d’un caractère vers la droite. Cela peut déplacer le curseur à la ligne suivante de l’entrée multiligne.

- Cmd `<RightArrow>`
- Emacs- `<RightArrow>` , `<Ctrl+f>`
- Mode d’insertion VI : `<RightArrow>`
- Mode de commande VI : `<RightArrow>` , `<Space>` , `<l>`

### <a name="forwardword"></a>ForwardWord

Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant. Les limites de mots sont définies par un jeu de caractères configurable.

- Emacs- `<Alt+f>` , `<Escape,f>`

### <a name="gotobrace"></a>GotoBrace

Atteindre l’accolade correspondante, les parenthèses ou les crochets.

- Cmd `<Ctrl+]>`
- Mode d’insertion VI : `<Ctrl+]>`
- Mode de commande VI : `<Ctrl+]>`

### <a name="gotocolumn"></a>GotoColumn

Accédez à la colonne indiquée par arg.

- Mode de commande VI : `<|>`

### <a name="gotofirstnonblankofline"></a>GotoFirstNonBlankOfLine

Placez le curseur sur le premier caractère non vide de la ligne.

- Mode de commande VI : `<^>`

### <a name="movetoendofline"></a>MoveToEndOfLine

Placez le curseur à la fin de l’entrée.

- Mode de commande VI : `<End>` , `<$>`

### <a name="nextline"></a>NextLine

Déplacer le curseur sur la ligne suivante.

- La fonction est indépendante.

### <a name="nextword"></a>NextWord

Déplacer le curseur vers l’avant jusqu’au début du mot suivant. Les limites de mots sont définies par un jeu de caractères configurable.

- Cmd `<Ctrl+RightArrow>`
- Mode d’insertion VI : `<Ctrl+RightArrow>`
- Mode de commande VI : `<Ctrl+RightArrow>`

### <a name="nextwordend"></a>NextWordEnd

Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant. Les limites de mots sont définies par un jeu de caractères configurable.

- Mode de commande VI : `<e>`

### <a name="previousline"></a>PreviousLine

Placez le curseur sur la ligne précédente.

- La fonction est indépendante.

### <a name="shellbackwardword"></a>ShellBackwardWord

Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent. Les limites de mots sont définies par les jetons PowerShell.

- La fonction est indépendante.

### <a name="shellforwardword"></a>ShellForwardWord

Déplacer le curseur vers l’avant jusqu’au début du mot suivant. Les limites de mots sont définies par les jetons PowerShell.

- La fonction est indépendante.

### <a name="shellnextword"></a>ShellNextWord

Déplacer le curseur vers l’avant jusqu’à la fin du mot actuel, ou si entre les mots, à la fin du mot suivant. Les limites de mots sont définies par les jetons PowerShell.

- La fonction est indépendante.

### <a name="vibackwardword"></a>ViBackwardWord

Ramener le curseur au début du mot actuel, ou si entre les mots, le début du mot précédent. Les limites de mots sont définies par un jeu de caractères configurable.

- Mode de commande VI : `<b>`

### <a name="viendofglob"></a>ViEndOfGlob

Déplace le curseur à la fin du mot, en utilisant uniquement des espaces blancs comme délimiteurs.

- Mode de commande VI : `<E>`

### <a name="viendofpreviousglob"></a>ViEndOfPreviousGlob

Passe à la fin du mot précédent, en utilisant uniquement un espace blanc comme délimiteur de mot.

- La fonction est indépendante.

### <a name="vigotobrace"></a>ViGotoBrace

Semblable à GotoBrace, mais est basé sur un caractère et non sur un jeton.

- Mode de commande VI : `<%>`

### <a name="vinextglob"></a>ViNextGlob

Passe au mot suivant, en utilisant uniquement un espace blanc comme délimiteur de mot.

- Mode de commande VI : `<W>`

### <a name="vinextword"></a>ViNextWord

Déplacer le curseur vers l’avant jusqu’au début du mot suivant. Les limites de mots sont définies par un jeu de caractères configurable.

- Mode de commande VI : `<w>`

## <a name="history-functions"></a>Fonctions d’historique

### <a name="beginningofhistory"></a>BeginningOfHistory

Accéder au premier élément de l’historique.

- Emacs- `<Alt+`<>`

### <a name="clearhistory"></a>ClearHistory

Efface l’historique dans PSReadLine. Cela n’affecte pas l’historique PowerShell.

- Cmd `<Alt+F7>`

### <a name="endofhistory"></a>EndOfHistory

Accéder au dernier élément (l’entrée en cours) dans l’historique.

- Emacs- `<Alt+>>`

### <a name="forwardsearchhistory"></a>ForwardSearchHistory

Effectuer une recherche incrémentielle par progression dans l’historique.

- Cmd `<Ctrl+s>`
- Emacs- `<Ctrl+s>`

### <a name="historysearchbackward"></a>HistorySearchBackward

Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.

- Cmd `<F8>`

### <a name="historysearchforward"></a>HistorySearchForward

Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine qui correspond aux caractères entre le début et l’entrée et le curseur.

- Cmd `<Shift+F8>`

### <a name="nexthistory"></a>NextHistory

Remplacez l’entrée actuelle par l’élément « Next » de l’historique PSReadLine.

- Cmd `<DownArrow>`
- Emacs- `<DownArrow>` , `<Ctrl+n>`
- Mode d’insertion VI : `<DownArrow>`
- Mode de commande VI : `<DownArrow>` , `<j>` , `<+>`

### <a name="previoushistory"></a>PreviousHistory

Remplacez l’entrée actuelle par l’élément « Previous » de l’historique PSReadLine.

- Cmd `<UpArrow>`
- Emacs- `<UpArrow>` , `<Ctrl+p>`
- Mode d’insertion VI : `<UpArrow>`
- Mode de commande VI : `<UpArrow>` , `<k>` , `<->`

### <a name="reversesearchhistory"></a>ReverseSearchHistory

Effectuer une recherche incrémentielle incrémentielle dans l’historique.

- Cmd `<Ctrl+r>`
- Emacs- `<Ctrl+r>`

### <a name="visearchhistorybackward"></a>ViSearchHistoryBackward

Demande une chaîne de recherche et lance la recherche sur AcceptLine.

- Mode d’insertion VI : `<Ctrl+r>`
- Mode de commande VI : `</>` , `<Ctrl+r>`

## <a name="completion-functions"></a>Fonctions d’achèvement

### <a name="complete"></a>Terminé

Tentative d’exécution de l’opération sur le texte entourant le curseur. S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation. Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.

- Emacs- `<Tab>`

### <a name="menucomplete"></a>MenuComplete

Tentative d’exécution de l’opération sur le texte entourant le curseur. S’il existe plusieurs saisies semi-automatiques possibles, le plus long préfixe non ambigu est utilisé pour la finalisation. Si vous essayez de terminer la saisie semi-automatique la plus longue, une liste des saisies semi-automatiques possibles s’affiche.

- Cmd `<Ctrl+Space>`
- Emacs- `<Ctrl+Space>`

### <a name="possiblecompletions"></a>PossibleCompletions

Affiche la liste des saisies semi-automatiques possibles.

- Emacs- `<Alt+=>`
- Mode d’insertion VI : `<Ctrl+Space>`
- Mode de commande VI : `<Ctrl+Space>`

### <a name="tabcompletenext"></a>TabCompleteNext

Tente de terminer le texte entourant le curseur avec la prochaine saisie semi-automatique disponible.

- Cmd `<Tab>`
- Mode de commande VI : `<Tab>`

### <a name="tabcompleteprevious"></a>TabCompletePrevious

Tente de terminer le texte entourant le curseur avec l’achèvement disponible précédent.

- Cmd `<Shift+Tab>`
- Mode de commande VI : `<Shift+Tab>`

### <a name="vitabcompletenext"></a>ViTabCompleteNext

Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompleteNext.

- Mode d’insertion VI : `<Tab>`

### <a name="vitabcompleteprevious"></a>ViTabCompletePrevious

Met fin au groupe d’édition actuel, si nécessaire, et appelle TabCompletePrevious.

- Mode d’insertion VI : `<Shift+Tab>`

## <a name="miscellaneous-functions"></a>Fonctions diverses

### <a name="capturescreen"></a>CaptureScreen

Démarrer la capture d’écran interactive-flèches haut et bas sélectionnez lignes, entrez copie le texte sélectionné dans le presse-papiers en tant que texte et html.

- La fonction est indépendante.

### <a name="clearscreen"></a>ClearScreen

Effacez l’écran et dessinez la ligne active en haut de l’écran.

- Cmd `<Ctrl+l>`
- Emacs- `<Ctrl+l>`
- Mode d’insertion VI : `<Ctrl+l>`
- Mode de commande VI : `<Ctrl+l>`

### <a name="digitargument"></a>DigitArgument

Démarrez un nouvel argument digit à passer à d’autres fonctions.

- Cmd : `<Alt+0>` ,,,,, `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`
- Emacs-,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` , `<Alt+9>` , `<Alt+->`
- Mode de commande VI : `<0>` , `<1>` ,, `<2>` `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`

### <a name="invokeprompt"></a>InvokePrompt

Efface l’invite en cours et appelle la fonction prompt pour réafficher l’invite. Utile pour les gestionnaires de clés personnalisés qui changent d’État, par exemple modifier le répertoire actif.

- La fonction est indépendante.

### <a name="scrolldisplaydown"></a>ScrollDisplayDown

Faites défiler l’écran vers le volet d’affichage.

- Cmd `<PageDown>`
- Emacs- `<PageDown>`

### <a name="scrolldisplaydownline"></a>ScrollDisplayDownLine

Faites défiler l’affichage d’une ligne vers le dessous.

- Cmd `<Ctrl+PageDown>`
- Emacs- `<Ctrl+PageDown>`

### <a name="scrolldisplaytocursor"></a>ScrollDisplayToCursor

Faites défiler l’affichage jusqu’au curseur.

- Emacs- `<Ctrl+End>`

### <a name="scrolldisplaytop"></a>ScrollDisplayTop

Faites défiler l’affichage vers le haut.

- Emacs- `<Ctrl+Home>`

### <a name="scrolldisplayup"></a>ScrollDisplayUp

Faites défiler l’écran afficher vers le haut.

- Cmd `<PageUp>`
- Emacs- `<PageUp>`

### <a name="scrolldisplayupline"></a>ScrollDisplayUpLine

Faites défiler l’affichage d’une ligne vers le haut.

- Cmd `<Ctrl+PageUp>`
- Emacs- `<Ctrl+PageUp>`

### <a name="selfinsert"></a>SelfInsert

Insérez la clé.

- La fonction est indépendante.

### <a name="showkeybindings"></a>ShowKeyBindings

Affiche toutes les clés liées.

- Cmd `<Ctrl+Alt+?>`
- Emacs- `<Ctrl+Alt+?>`
- Mode d’insertion VI : `<Ctrl+Alt+?>`

### <a name="vicommandmode"></a>ViCommandMode

Basculez le mode d’opération actuel de Vi-Insert à VI-Command.

- Mode d’insertion VI : `<Escape>`

### <a name="vidigitargumentinchord"></a>ViDigitArgumentInChord

Démarrez un nouvel argument digit à passer à d’autres fonctions dans l’un des cordes de VI.

- La fonction est indépendante.

### <a name="vieditvisually"></a>ViEditVisually

Modifiez la ligne de commande dans un éditeur de texte spécifié par $env : EDITOR ou $env : VISUAL.

- Emacs- `<Ctrl+x,Ctrl+e>`
- Mode de commande VI : `<v>`

### <a name="viexit"></a>ViExit

Quitte l’interpréteur de commandes.

- La fonction est indépendante.

### <a name="viinsertmode"></a>ViInsertMode

Basculez en mode insertion.

- Mode de commande VI : `<i>`

### <a name="whatiskey"></a>WhatIsKey

Lisez une clé et dites-moi à quoi la clé est liée.

- Cmd `<Alt+?>`
- Emacs- `<Alt+?>`

## <a name="selection-functions"></a>Fonctions de sélection

### <a name="exchangepointandmark"></a>ExchangePointAndMark

Le curseur est placé à l’emplacement de la marque et la marque est déplacée vers l’emplacement du curseur.

- Emacs- `<Ctrl+x,Ctrl+x>`

### <a name="selectall"></a>SelectAll

Sélectionnez la ligne entière.

- Cmd `<Ctrl+a>`

### <a name="selectbackwardchar"></a>SelectBackwardChar

Ajustez la sélection actuelle pour inclure le caractère précédent.

- Cmd `<Shift+LeftArrow>`
- Emacs- `<Shift+LeftArrow>`

### <a name="selectbackwardsline"></a>SelectBackwardsLine

Ajustez la sélection actuelle à inclure à partir du curseur jusqu’au début de la ligne.

- Cmd `<Shift+Home>`
- Emacs- `<Shift+Home>`

### <a name="selectbackwardword"></a>SelectBackwardWord

Ajustez la sélection actuelle pour inclure le mot précédent.

- Cmd `<Shift+Ctrl+LeftArrow>`
- Emacs- `<Alt+B>`

### <a name="selectforwardchar"></a>SelectForwardChar

Ajustez la sélection actuelle pour inclure le caractère suivant.

- Cmd `<Shift+RightArrow>`
- Emacs- `<Shift+RightArrow>`

### <a name="selectforwardword"></a>SelectForwardWord

Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ForwardWord.

- Emacs- `<Alt+F>`

### <a name="selectline"></a>SelectLine

Ajustez la sélection actuelle à inclure à partir du curseur jusqu’à la fin de la ligne.

- Cmd `<Shift+End>`
- Emacs- `<Shift+End>`

### <a name="selectnextword"></a>SelectNextWord

Ajustez la sélection actuelle pour inclure le mot suivant.

- Cmd `<Shift+Ctrl+RightArrow>`

### <a name="selectshellbackwardword"></a>SelectShellBackwardWord

Ajustez la sélection actuelle pour inclure le mot précédent à l’aide de ShellBackwardWord.

- La fonction est indépendante.

### <a name="selectshellforwardword"></a>SelectShellForwardWord

Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellForwardWord.

- La fonction est indépendante.

### <a name="selectshellnextword"></a>SelectShellNextWord

Ajustez la sélection actuelle pour inclure le mot suivant à l’aide de ShellNextWord.

- La fonction est indépendante.

### <a name="setmark"></a>SetMark

Marquez l’emplacement actuel du curseur pour une utilisation dans une commande d’édition suivante.

- Emacs- `<Ctrl+`>`

## <a name="search-functions"></a>Fonctions de recherche

### <a name="charactersearch"></a>CharacterSearch

Lisez un caractère et recherchez l’occurrence suivante de ce caractère.
Si un argument est spécifié, effectuez une recherche vers l’avant (ou vers l’arrière si négatif) pour la nième occurrence.

- Cmd `<F3>`
- Emacs- `<Ctrl+]>`
- Mode d’insertion VI : `<F3>`
- Mode de commande VI : `<F3>`

### <a name="charactersearchbackward"></a>CharacterSearchBackward

Lisez un caractère et recherchez l’occurrence suivante de ce caractère. Si un argument est spécifié, effectuez une recherche vers l’arrière (ou vers l’avant si négatif) pour la nième occurrence.

- Cmd `<Shift+F3>`
- Emacs- `<Ctrl+Alt+]>`
- Mode d’insertion VI : `<Shift+F3>`
- Mode de commande VI : `<Shift+F3>`

### <a name="repeatlastcharsearch"></a>RepeatLastCharSearch

Répète la dernière recherche de caractères enregistrée.

- Mode de commande VI : `<;>`

### <a name="repeatlastcharsearchbackwards"></a>RepeatLastCharSearchBackwards

Répète la dernière recherche de caractères enregistrée, mais dans la direction opposée.

- Mode de commande VI : `<,>`

### <a name="repeatsearch"></a>RepeatSearch

Répétez la dernière recherche dans la même direction que précédemment.

- Mode de commande VI : `<n>`

### <a name="repeatsearchbackward"></a>RepeatSearchBackward

Répétez la dernière recherche dans la même direction que précédemment.

- Mode de commande VI : `<N>`

### <a name="searchchar"></a>SearchChar

Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère. Il s’agit de la fonctionnalité’t'.

- Mode de commande VI : `<f>`

### <a name="searchcharbackward"></a>SearchCharBackward

Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère. Il s’agit de la fonctionnalité’t'.

- Mode de commande VI : `<F>`

### <a name="searchcharbackwardwithbackoff"></a>SearchCharBackwardWithBackoff

Lisez le caractère suivant, puis recherchez-le, en accédant à l’arrière, puis en annulant un caractère. Il s’agit de la fonctionnalité’t'.

- Mode de commande VI : `<T>`

### <a name="searchcharwithbackoff"></a>SearchCharWithBackoff

Lisez le caractère suivant, puis recherchez-le, à l’avenir, puis annulez un caractère. Il s’agit de la fonctionnalité’t'.

- Mode de commande VI : `<t>`

### <a name="searchforward"></a>SearchForward

Demande une chaîne de recherche et lance la recherche sur AcceptLine.

- Mode d’insertion VI : `<Ctrl+s>`
- Mode de commande VI : `<?>` , `<Ctrl+s>`

## <a name="custom-key-bindings"></a>Combinaisons de touches personnalisées

PSReadLine prend en charge les combinaisons de touches personnalisées à l’aide de l’applet de commande `Set-PSReadLineKeyHandler` . La plupart des combinaisons de touches personnalisées appellent l’une des fonctions ci-dessus, par exemple

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

Vous pouvez lier un ScriptBlock à une clé. Le ScriptBlock peut faire à peu près tout ce que vous voulez. Voici quelques exemples utiles :

- modifier la ligne de commande
- ouverture d’une nouvelle fenêtre (par exemple, aide)
- modifier les répertoires sans modifier la ligne de commande

Le ScriptBlock reçoit deux arguments :

- `$key` -Objet **[ConsoleKeyInfo]** qui est la clé qui a déclenché la liaison personnalisée. Si vous liez le même ScriptBlock à plusieurs clés et que vous devez effectuer des actions différentes en fonction de la clé, vous pouvez vérifier $key. De nombreuses liaisons personnalisées ignorent cet argument.

- `$arg` : Argument arbitraire. Le plus souvent, il s’agit d’un argument entier que l’utilisateur passe à partir des combinaisons de touches DigitArgument. Si votre liaison n’accepte pas d’arguments, il est raisonnable d’ignorer cet argument.

Jetons un coup d’œil à un exemple qui ajoute une ligne de commande à l’historique sans l’exécuter. Cela est utile lorsque vous vous rendez compte que vous avez oublié d’effectuer une opération, mais que vous ne voulez pas entrer à nouveau la ligne de commande que vous avez déjà entrée.

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

Vous pouvez voir beaucoup plus d’exemples dans le fichier `SamplePSReadLineProfile.ps1` qui est installé dans le dossier du module PSReadLine.

La plupart des combinaisons de touches utilisent des fonctions d’assistance pour la modification de la ligne de commande.
Ces API sont documentées dans la section suivante.

## <a name="custom-key-binding-support-apis"></a>API de prise en charge de la liaison de clé personnalisée

Les fonctions suivantes sont publiques dans Microsoft. PowerShell. PSConsoleReadLine, mais ne peuvent pas être directement liées à une clé. La plupart sont utiles dans les combinaisons de touches personnalisées.

```csharp
void AddToHistory(string command)
```

Ajoutez une ligne de commande à l’historique sans l’exécuter.

```csharp
void ClearKillRing()
```

Effacez le point d’arrêt.  Cela est principalement utilisé pour les tests.

```csharp
void Delete(int start, int length)
```

Supprimer les caractères de longueur du début.  Cette opération prend en charge les opérations d’annulation et de rétablissement.

```csharp
void Ding()
```

Effectuez l’action Ding en fonction des préférences de l’utilisateur.

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

Ces deux fonctions récupèrent des informations utiles sur l’état actuel de la mémoire tampon d’entrée.  La première est plus couramment utilisée dans les cas simples.  Le second est utilisé si votre liaison fait une opération plus avancée avec l’AST.

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

Cette fonction est utilisée par Get-PSReadLineKeyHandler et n’est probablement pas utile dans une combinaison de touches personnalisée.

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

Cette fonction est utilisée par Get-PSReadLineOption et n’est probablement pas trop utile dans une liaison de clé personnalisée.

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

Si aucune sélection n’est effectuée sur la ligne de commande,-1 est retourné à la fois en début et en longueur. Si une sélection est effectuée sur la ligne de commande, le début et la longueur de la sélection sont retournés.

```csharp
void Insert(char c)
void Insert(string s)
```

Insérez un caractère ou une chaîne au niveau du curseur.  Cette opération prend en charge les opérations d’annulation et de rétablissement.

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

Il s’agit du point d’entrée principal de PSReadLine. Comme il ne prend pas en charge la récursivité, il n’est pas utile dans une liaison de clé personnalisée.

```csharp
void RemoveKeyHandler(string[] key)
```

Cette fonction est utilisée par Remove-PSReadLineKeyHandler et n’est probablement pas trop utile dans une liaison de clé personnalisée.

```csharp
void Replace(int start, int length, string replacement)
```

Remplacez une partie de l’entrée. Cette opération prend en charge les opérations d’annulation et de rétablissement. C’est préférable à Delete, suivi de Insert, car il est traité comme une action unique pour Undo.

```csharp
void SetCursorPosition(int cursor)
```

Déplacer le curseur vers l’offset donné. Le déplacement du curseur n’est pas suivi pour l’annulation.

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

Cette fonction est une méthode d’assistance utilisée par l’applet de commande Set-PSReadLineOption, mais peut être utile pour une combinaison de touches personnalisée qui souhaite modifier temporairement un paramètre.

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

Cette méthode d’assistance est utilisée pour les liaisons personnalisées qui respectent DigitArgument. Un appel classique ressemble à ce qui suit.

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a>REMARQUE

### <a name="powershell-compatibility"></a>COMPATIBILITÉ AVEC POWERSHELL

PSReadLine nécessite PowerShell 3,0, ou une version plus récente, et l’hôte de la console. Il ne fonctionne pas dans PowerShell ISE. Elle fonctionne dans la console de Visual Studio Code.

### <a name="command-history"></a>HISTORIQUE DES COMMANDES

PSReadLine gère un fichier d’historique contenant toutes les commandes et données que vous avez entrées à partir de la ligne de commande. Cela peut contenir des données sensibles, y compris des mots de passe. Par exemple, si vous utilisez l’applet de commande, `ConvertTo-SecureString` le mot de passe est enregistré dans le fichier d’historique sous forme de texte brut. Les fichiers d’historique sont un fichier nommé `$($host.Name)_history.txt` . Sur les systèmes Windows, le fichier d’historique est stocké à l’adresse `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` . Sur les systèmes non-Windows, les fichiers d’historique sont stockés dans `$env:XDG_DATA_HOME/powershell/PSReadLine` ou `$env:HOME/.local/share/powershell/PSReadLine` .

### <a name="feedback--contributing-to-psreadline"></a>Commentaires & contribution à PSReadLine

[PSReadLine sur GitHub](https://github.com/PowerShell/PSReadLine)

N’hésitez pas à envoyer une demande de tirage ou à envoyer des commentaires sur la page GitHub.

## <a name="see-also"></a>VOIR AUSSI

PSReadLine est fortement influencé par la bibliothèque GNU [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) .
