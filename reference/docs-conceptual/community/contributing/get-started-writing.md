---
title: Bien démarrer avec la contribution à la documentation de PowerShell
description: Cet article explique dans les grandes lignes comment bien démarrer en tant que contributeur de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: fdf29feb75abb6592205aaf1726c07a60ce3a924
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81005514"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Bien démarrer avec la contribution à la documentation de PowerShell

Cet article explique dans les grandes lignes comment bien démarrer en tant que contributeur de la documentation de PowerShell.

## <a name="powershell-docs-structure"></a>Structure de PowerShell-Docs

Le [référentiel PowerShell-Docs][psdocs] est divisé en deux groupes de contenu. Les branches Git permettent de gérer la façon dont la documentation est publiée.

### <a name="reference-content"></a>Contenu de référence

Le contenu de référence correspond aux informations de référence sur les cmdlets fournies avec PowerShell.
La [référence][ref] est collectée dans les dossiers de versions (5.1, 6, 7.0 et 7.1). Ce contenu ne comporte les informations de référence que des cmdlets des modules fournis avec PowerShell. Il sert également à créer les informations d’aide affichées par la cmdlet `Get-Help`.

> [!NOTE]
> La table des matières (TOC) du contenu de référence est générée automatiquement par le système de publication. Il n’est pas nécessaire de la mettre à jour.

### <a name="conceptual-content"></a>Contenu conceptuel

La documentation conceptuelle comprend le contenu suivant :

- Notes de publication
- Instructions d’installation
- Exemples de scripts et guides pratiques
- Documentation DSC
- Documentation SDK

La [documentation conceptuelle][conceptual] n’est pas organisée version par version. Tous les articles sont affichés pour chacune des versions de PowerShell. Nous travaillons à la création d’articles propres à chaque version. Lorsque cette fonctionnalité sera disponible dans notre documentation, ce guide sera mis à jour.

> [!NOTE]
> Chaque fois qu’un article conceptuel est ajouté, supprimé ou renommé, la table des matières doit être mise à jour et incluse dans la demande de tirage (pull request).

## <a name="using-git-branches"></a>Utilisation des branches Git

La branche par défaut de PowerShell-Docs est la branche `staging`. Les modifications apportées aux branches de travail sont fusionnées dans la branche `staging` avant la publication. Environ une fois par semaine, la branche `staging` est fusionnée dans la branche `live`. La branche `live` contient le contenu publié sur docs.microsoft.com. Aucune modification ne doit être effectuée directement dans la branche `live`.

Si vous soumettez une modification de la documentation qui s’applique uniquement à une version non publiée de PowerShell, regardez s’il existe une branche pour cette version. Toutes les modifications qui s’appliquent à une version future spécifique doivent porter sur la branche de version. Les branches de version suivent le modèle de nom `release-<version>`.

Avant de commencer les modifications, créez une branche de travail dans votre copie locale du référentiel PowerShell-Docs. Il doit s’agir d’un [clone de votre duplication (fork)][fork]. Veillez à synchroniser votre référentiel local avant de créer votre branche de travail. Celle-ci doit être créée à partir d’une copie à jour de la branche `staging` ou de la branche `release`.

Apportez les modifications que vous souhaitez soumettre suivant le processus de la section [Effectuer une modification][making-changes] du Guide du contributeur central.

### <a name="creating-new-articles"></a>Création d’articles

Vous devez créer un problème GitHub pour chaque document que vous souhaitez ajouter. Recherchez les problèmes existants pour ne pas créer de redondance. Les problèmes affectés à quelqu’un sont considérés comme « en cours ». Si vous souhaitez collaborer sur un problème, contactez la personne à qui il est attribué.

Comme pour le [processus RFC][rfc] PowerShell, le fait de créer un problème avant d’en écrire le contenu permet d’éviter de passer du temps sur un problème qui sera rejeté par l’équipe PowerShell-Docs. Nous pouvons par ailleurs vous consulter concernant l’étendue du contenu et sa place dans la documentation de PowerShell.

### <a name="updating-existing-articles"></a>Mise à jour d’articles existants

Le cas échéant, l’article de référence sur les cmdlets est dupliqué dans toutes les versions de PowerShell. Lorsque vous signalez un problème concernant des informations de référence sur les cmdlets ou un article `About_`, spécifiez les versions concernées par le problème. Le modèle de problème de GitHub comprend une liste de contrôle des versions. Cochez les cases correspondant aux versions du contenu qui sont affectées. Lorsque vous envoyez une modification d’un article pour un problème qui porte sur plusieurs versions du contenu, vous devez appliquer la modification à chacune des versions du fichier.

## <a name="next-steps"></a>Étapes suivantes

Consultez [Envoi d’une demande de tirage](pull-requests.md).

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md