---
title: Processus de gestion des problèmes
description: Cet article explique comment l’équipe PowerShell-Docs gère les problèmes.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99597518"
---
# <a name="how-we-manage-issues"></a>Processus de gestion des problèmes

Cet article explique comment nous gérons les problèmes dans le référentiel PowerShell-Docs. Cet article est conçu pour servir d’aide-mémoire aux membres de l’équipe PowerShell-Docs. Il est publié ici pour assurer la transparence des processus pour nos contributeurs publics.

## <a name="sources-of-issues"></a>Sources des problèmes

- Contributeurs de la communauté
- Contributeurs internes
- Transcriptions de commentaires provenant des réseaux sociaux
- Commentaires envoyés par le biais du formulaire de commentaires sur Docs

## <a name="response-time-targets"></a>Objectifs de temps de réponse

80% des nouveaux problèmes sont clos dans les 3 jours ouvrables.

- Triage-1 jour ouvrable
- Correction ou modification-10 jours ouvrables

### <a name="labeling--milestones"></a>Étiquetage et jalons

#### <a name="label-types"></a>Types d’étiquettes

|   Type   | Description                                                         |
| -------- | ------------------------------------------------------------------- |
| Domaine     | Permet d’indiquer sur quelle partie de PowerShell ou de Docs porte le problème.<br>Utile aux propriétaires de fonctionnalités pour trouver les problèmes relatifs à leur fonctionnalité. |
| Problème    | Indique le type de problème                                         |
| Priorité | Indique la priorité du problème. Plage de valeurs 0 (haute)-4 (faible)  |
| Statut   | Indique l’état de l’élément de travail ou la raison pour laquelle il a été fermé          |
| Étiquette      | Étiquettes utilisées pour une classification supplémentaire                        |
| En attente  | Indique que nous attendons une personne ou un autre événement         |

#### <a name="milestones"></a>Milestones

Les problèmes et demandes de tirage doivent être marqués du jalon correspondant. Si le problème ne s’applique pas à une version spécifique, aucune étape majeure n’est utilisée. Les problèmes de la fonction PRs et les problèmes liés aux modifications qui n’ont pas encore été fusionnées dans la base de code PowerShell doivent être affectés à la **prochaine** étape majeure. Une fois la modification du code fusionnée, remplacez la valeur du jalon par la version correspondante.

|    Jalon     |                    Description                     |
| ---------------- | -------------------------------------------------- |
| 7.0.0            | Éléments de travail liés à la version 7.0 de PowerShell               |
| 7.1.0            | Éléments de travail liés à la version 7.1 de PowerShell               |
| 7.2.0            | Éléments de travail liés à PowerShell 7,2               |
| À l’avenir           | Éléments de travail d’une future version de PowerShell          |

## <a name="triage-process"></a>Processus de triage

Les membres de l’équipe de documentation PowerShell examinent les problèmes quotidiennement et hiérarchisent les nouveaux problèmes à mesure qu’ils arrivent. L’équipe respecte chaque semaine pour discuter des problèmes qui doivent être triés ou rester non résolus.

### <a name="misplaced-product-feedback"></a>Commentaires produits mal placés

- Entrez un commentaire pour rediriger le client vers le bon canal de commentaires.
- Facultatif : Copiez le problème à l’emplacement de commentaires sur le produit correspondant, ajoutez un lien vers l’élément copié, puis fermez le problème. NE copiez PAS les problèmes sur UserVoice.

  L’emplacement par défaut pour les problèmes PowerShell est [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) .

  Les sujets suivants ont des emplacements différents pour les problèmes :

  | Sujets |                                                     URL de commentaires sur le produit                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | dsc      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | galerie  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | jea      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | wmf      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

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
- Chaque violation doit être discutée dans le triage hebdomadaire pour déterminer la nécessité d’une action supplémentaire (rapport à GitHub ou Microsoft Legal).
