---
title: Processus de gestion des problèmes
description: Cet article explique comment l’équipe PowerShell-Docs gère les problèmes.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 56f0ea5b4c5c700db8fdd0b16e3ce1c4040a43dc
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354590"
---
# <a name="how-we-manage-issues"></a>Processus de gestion des problèmes

Cet article explique comment nous gérons les problèmes dans le référentiel PowerShell-Docs. Cet article est conçu pour servir d’aide-mémoire aux membres de l’équipe PowerShell-Docs. Il est publié ici dans un souci de transparence des processus pour nos contributeurs publics.

## <a name="sources-of-issues"></a>Sources des problèmes

- Contributeurs de la communauté
- Contributeurs internes
- Transcriptions de commentaires provenant des réseaux sociaux
- Commentaires envoyés par le biais du formulaire de commentaires sur Docs

## <a name="response-time-targets"></a>Objectifs de temps de réponse

- Triage : 5 jours ouvrés
- Correction ou modification : pas d’objectif particulier, le plus rapidement possible

### <a name="labeling--milestones"></a>Étiquetage et jalons

#### <a name="label-types"></a>Types d’étiquettes

|Préfixe  | Description                                                         |
|------- | --------------------------------------------------------------------|
|Domaine    | Permet d’indiquer sur quelle partie de PowerShell ou de Docs porte le problème.<br>Utile aux propriétaires de fonctionnalités pour trouver les problèmes relatifs à leur fonctionnalité.|
|Pri     | Permet d’indiquer le niveau de priorité du problème. Plage de valeurs : 0-4.        |
|Problème   | Permet de classer le type de commentaires relatifs au problème.                     |
|Révision  | Permet d’indiquer que le problème exige une vérification supplémentaire de la part de l’équipe.              |
|Statut  | Permet d’indiquer l’état de l’élément de travail.                        |
|En attente | Permet d’indiquer que nous attendons quelque chose.                   |

#### <a name="milestones"></a>Milestones

Les problèmes et demandes de tirage doivent être marqués du jalon correspondant. Si le problème ne porte pas sur une version spécifique, aucun jalon n’est utilisé. Les problèmes liés aux demandes de tirage Docs et portant sur des modifications qui n’ont pas encore été fusionnées dans le codebase PowerShell doivent comporter le jalon **Future** (À venir). Une fois la modification du code fusionnée, remplacez la valeur du jalon par la version correspondante.

|    Jalon     |                    Description                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | Éléments de travail entre la version 6.0 et la version 6.2.x de PowerShell |
| 7.0.0            | Éléments de travail liés à la version 7.0 de PowerShell               |
| 7.1.0            | Éléments de travail liés à la version 7.1 de PowerShell               |
| À l’avenir           | Éléments de travail d’une future version de PowerShell          |
| PSReadline-vNext | Éléments de travail d’une future version de PSReadline          |

## <a name="triage-process"></a>Processus de triage

L’équipe PowerShell-Docs se réunit une fois par semaine pour discuter des problèmes ajoutés depuis la dernière réunion. Un problème est considéré comme trié lorsque des étiquettes ont été attribuées ou qu’un propriétaire a été affecté. Les membres de l’équipe PowerShell-Docs sont encouragés à examiner les problèmes quotidiennement et à les trier au fur et à mesure qu’ils arrivent. La réunion de triage hebdomadaire peut alors permettre de discuter des nouveaux problèmes plus en détail si nécessaire.

### <a name="misplaced-product-feedback"></a>Commentaires produits mal placés

- Entrez un commentaire pour le client indiquant qu’il s’agit de commentaires sur le produit et fournissez un lien vers le canal de commentaires correspondant.
- Facultatif : Copiez le problème à l’emplacement de commentaires sur le produit correspondant, ajoutez un lien vers l’élément copié, puis fermez le problème. NE copiez PAS les problèmes sur UserVoice.

  | Ensemble de documents    | URL de commentaires sur le produit                                           |
  | --------- | -------------------------------------------------------------- |
  | developer | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | dsc       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | galerie   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | jea       | `https://github.com/powershell/jea/issues/new`                 |
  | reference | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | wmf       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

### <a name="support-requests"></a>Demandes de support

- Si la question de support est simple, répondez-y poliment et fermez le problème.
- Si la question est plus compliquée ou que le demandeur répond par d’autres questions, redirigez-le vers des forums et des canaux de support. Texte suggéré pour la redirection vers des forums :

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a>Violation du code de conduite

- Modifiez le problème de façon à supprimer tout contenu choquant si nécessaire.
- Entrez un commentaire indiquant que le problème est indésirable, fermez le problème, puis verrouillez-le pour éviter d’autres commentaires.
- Chaque événement de ce type doit être abordé dans le triage hebdomadaire pour déterminer si une action supplémentaire est nécessaire (envoi d’un rapport à GitHub ou au service juridique de Microsoft).
