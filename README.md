---
ms.openlocfilehash: f46b14e44c32ce31b4da1a14580fe03564bf9946
ms.sourcegitcommit: 0e18be0a2869beaa711ba3eca7a8a15514e5e962
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91899264"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Code de conduite Microsoft Open Source

Ce projet a adopté le [Code de conduite Open Source de Microsoft](https://opensource.microsoft.com/codeofconduct/). Pour plus d’informations, consultez le [Forum Aux Questions sur le Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/) ou contactez [opencode@microsoft.com](mailto:opencode@microsoft.com) si vous avez d’autres questions ou des commentaires.

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>État de la build

|          Branche active          |           Branche de mise en lots            |
| :---------------------------- | :---------------------------------- |
| [![live-badge][]][live-badge] | [![staging-badge][]][staging-badge] |

## <a name="powershell-documentation"></a>Documentation de PowerShell

Bienvenue dans le dépôt PowerShell-Docs, qui héberge la documentation officielle de PowerShell.

## <a name="repository-structure"></a>Structure du dépôt

La liste suivante décrit les principaux dossiers de ce dépôt.

- `.github` - contient les paramètres de configuration utilisés par GitHub pour ce dépôt
- `.vscode` - contient les paramètres de configuration et les extensions recommandées pour Visual Studio Code (VS Code)
- `assets` - contient les fichiers téléchargeables liés dans la documentation
- `reference` - contient la documentation publiée sur [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/). Cela comprend à la fois les informations de référence et le contenu conceptuel.
  - `5.1` - contient les informations de référence sur les applets de commande et les rubriques relatives à PowerShell 5.1
  - `6` - contient les informations de référence sur les applets de commande et les rubriques relatives à PowerShell 6
  - `7.0` - contient les informations de référence sur les applets de commande et les rubriques relatives à PowerShell 7.0
  - `7.1` - contient les informations de référence sur les applets de commande et les rubriques relatives à PowerShell 7.1
  - `bread` - contient la table des matières à explorer à l’aide de la barre de navigation
  - `docs-conceptual` - contient les articles conceptuels qui sont publiés sur le site Docs. En général, la structure de dossiers reflète la table des matières.
  - `mapping` - contient la configuration de mappage de version utilisée par le système de génération
  - `media` - contient les fichiers image utilisés dans la documentation. Des dossiers multimédias se trouvent dans l’ensemble du contenu `docs-conceptual`. Pour plus d’informations sur l’utilisation des images dans la documentation, consultez le Guide du contributeur.
  - `module` - contient la source markdown pour la page de navigateur de module
- `tests` - contient les tests Pester utilisés par le système de génération
- `tools` - contient d’autres outils utilisés par le système de génération

> REMARQUE : Le contenu de référence (dans les dossiers numérotés) est utilisé pour créer les pages web sur le site Docs, ainsi que l’aide modifiable utilisée par PowerShell.
> Les articles du dossier `docs-conceptual` sont uniquement publiés sur le site web Docs.

## <a name="contributing"></a>Contribution

Les contributions publiques sont les bienvenues dans ce dépôt via des [demandes de tirage](https://help.github.com/articles/using-pull-requests/) (pull request) dans la branche _intermédiaire_.
Notez qu’avant de pouvoir accepter votre demande de tirage, vous devez signer notre [contrat de licence Contribution](https://cla.microsoft.com/). Vous n’avez à le faire qu’une seule fois.

Pour plus d’informations sur la contribution, lisez notre [guide du contributeur](https://aka.ms/PSDocsContributor). Le guide du contributeur contient des informations détaillées sur la manière de contribuer à la documentation, les outils, ainsi que sur les exigences concernant le style et la mise en forme. Utilisez les modèles « Issue » et « Pull Request » afin que la documentation soit cohérente entre les versions.

## <a name="licenses"></a>Licences

Il existe deux fichiers de licence pour ce projet. La licence MIT s’applique au code contenu dans ce dépôt. La licence Creative Commons s’applique à la documentation.
