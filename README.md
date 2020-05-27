---
ms.openlocfilehash: 0d91230aa063e58106b35a4ada1d577f316f8f27
ms.sourcegitcommit: c752ae8d0fa47eaaf3c5eae2a5a770f06c63921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840990"
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

Bienvenue dans le référentiel de documents de PowerShell, qui héberge la documentation officielle de PowerShell.

## <a name="repository-structure"></a>Structure du dépôt

Chacun des dossiers de premier niveau suivants dans ce référentiel contient un ensemble de documents qui sont publiés dans [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/reference/](https://docs.microsoft.com/powershell/scripting/) correspond aux sujets conceptuels et à la référence de module PowerShell dans les versions 5.1, 6.0 et 7.0. Ce contenu est également la source de contenu d’aide récupéré par la cmdlet `Get-Help`.
  - [docs-conceptual/](https://docs.microsoft.com/powershell) : ce dossier contient la documentation conceptuelle et les jeux de documents suivants :
    - [developer/](https://docs.microsoft.com/powershell/scripting/developer/) correspond à la documentation du SDK PowerShell (migrée depuis MSDN).
    - [dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) correspond à la fonctionnalité de configuration d’état souhaité.
    - [gallery/](https://docs.microsoft.com/powershell/scripting/gallery) correspond à la [PowerShell Gallery](https://www.powershellgallery.com/)
    - [jea/](https://docs.microsoft.com/powershell/scripting/learn/remoting/jea/overview) correspond à la fonctionnalité JEA (Just Enough Administration)
    - [wmf/](https://docs.microsoft.com/powershell/scripting/windows-powershell/wmf/overview) contient les notes de publication pour Windows Management Framework, le package utilisé pour distribuer les nouvelles versions de PowerShell aux versions antérieures de Windows.

## <a name="contributing"></a>Contribution

Nous fusionnons activement les contributions dans ce dépôt via des [demandes Pull](https://help.github.com/articles/using-pull-requests/) dans la branche de _préproduction_.
Notez qu’avant d’envoyer une demande Pull, vous devez signer un [contrat de licence de contribution](https://cla.microsoft.com/) pour garantir que la communauté est libre d’utiliser vos envois.

Pour plus d’informations sur la contribution, lisez notre [guide du contributeur](https://docs.microsoft.com/powershell/scripting/community/contributing/overview).
Le guide du contributeur contient des informations détaillées sur la manière de contribuer à la documentation, les outils, ainsi que sur les exigences concernant le style et la mise en forme. Utilisez les modèles « Issue » et « Pull Request » afin que la documentation soit cohérente entre les versions.

## <a name="licenses"></a>Licences

Il existe deux fichiers de licence pour ce projet. La licence MIT s’applique au code contenu dans ce dépôt. La licence Creative Commons s’applique à la documentation.
