---
title: Contribution à la documentation de PowerShell
description: Cet article décrit les étapes requises pour contribuer à la documentation PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 255b74a75b8412ed509f6da930eb722d54233711
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354401"
---
# <a name="contributing-to-powershell-documentation"></a>Contribution à la documentation de PowerShell

Nous vous remercions de contribuer à la documentation de PowerShell !

Le Guide du contributeur est un ensemble d’articles qui expliquent les outils et les processus que nous utilisons pour créer la documentation de Microsoft. Certains de ces guides comportent des informations communes à tous les ensembles de documentation publiés sur [docs.microsoft.com][docs]. D’autres sont propres à la rédaction de la documentation de PowerShell.

Les articles communs sont disponibles dans notre [Guide du contributeur][contribute] centralisé. Les guides propres à PowerShell sont disponibles ici.

## <a name="ways-to-contribute"></a>Comment contribuer ?

Il existe deux manières d’apporter sa contribution. Les deux nous sont utiles.

- Les [problèmes][file-an-issue] nous aident à identifier les points problématiques et les lacunes de notre documentation. Certains sont difficiles à résoudre et demandent davantage d’investigation et de recherches. Le processus nous permet d’échanger au sujet du problème et d’y apporter une solution satisfaisante.

- Envoyer de nouveaux contenus ou des modifications d’articles existants dans la documentation représente un processus plus complexe. Ci-dessous sont détaillés les outils, les processus et les normes à suivre.

## <a name="prepare-to-make-a-contribution"></a>Préparation de la contribution

Vous devez avoir un compte GitHub. Référez-vous à la liste de contrôle ci-dessous pour connaître les outils et comprendre les processus que nous suivons pour effectuer des contributions.

1. [Inscrivez-vous à GitHub](/contribute/get-started-setup-github).
1. [Installez les outils Git et Markdown](/contribute/get-started-setup-tools).
1. [Installez Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack).
1. [Installez Posh-Git][posh-git] (non obligatoire, mais recommandé).
1. [Configurez un référentiel Git local](/contribute/get-started-setup-local).
1. [Consultez les notions de base de Git et de GitHub](/contribute/git-github-fundamentals).

## <a name="get-started-writing-docs"></a>Commencer à écrire de la documentation

Il existe deux façons de contribuer aux modifications de la documentation :

1. [Modification rapide de documents existants](/contribute/#quick-edits-to-existing-documents) :
   - Corrections mineures, correction de fautes de frappe ou petits ajouts.
1. [Flux de travail GitHub complet pour Docs](/contribute/how-to-write-workflows-major) :
   - Modifications importantes, versions multiples, ajout ou modification d’images ou contribution à de nouveaux articles.

Lisez également la section [Notions de base de la rédaction](/contribute/style-quick-start) du Guide du contributeur centralisé. Une autre excellente ressource est le [Guide de style de rédaction Microsoft][style-guide]. L’objectif de ce guide est d’aider les éditeurs, les rédacteurs techniques, les développeurs, les responsables marketing et tous les autres professionnels des technologies de l’information à écrire du contenu de meilleure qualité.

Les corrections mineures et clarifications de la documentation ainsi que les exemples de code des référentiels publics sont couverts par les [Conditions d’utilisation][terms-of-use] du site docs.microsoft.com.

Suivez le flux de travail GitHub complet lorsque vous apportez des modifications importantes. Si vous n’êtes pas un employé de Microsoft, les modifications significatives génèrent un commentaire dans la demande de tirage (pull request) qui vous demande de soumettre un [Contrat de licence de contribution (CLA)][cla] en ligne. Vous devez remplir le formulaire en ligne pour que nous puissions examiner ou accepter votre demande de tirage.

## <a name="code-of-conduct"></a>Code de conduite

Tous les référentiels comportant des contenus publiés sur docs.microsoft.com ont adopté le [Code de conduite Open Source Microsoft](https://opensource.microsoft.com/codeofconduct/) ou le [Code de conduite .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Pour plus d'informations, consultez la [FAQ du Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/).

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants comportent des informations propres à la documentation de PowerShell. En cas de conflit avec les indications du Guide du contributeur centralisé, nous précisons la façon dont ces règles diffèrent pour le contenu PowerShell.

Consultez les documents suivants :

- [Guide pratique pour signaler un problème](file-an-issue.md)
- [Bien démarrer avec la rédaction de la documentation](get-started-writing.md)
- [Envoi d’une demande de tirage](pull-requests.md)
- [Guide de style PowerShell-Docs](powershell-style-guide.md)
- [Informations de référence sur la modification des cmdlets](editing-cmdlet-ref.md)

Ressources supplémentaires

- [Liste de contrôle éditoriale](editorial-checklist.md)
- [Processus de gestion des problèmes](managing-issues.md)
- [Processus de gestion des demandes de tirage](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
