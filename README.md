# <a name="microsoft-open-source-code-of-conduct"></a>Code de conduite Microsoft Open Source

Ce projet a adopté le [Code de conduite Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/).
Pour plus d’informations, consultez le [Forum Aux Questions sur le Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/) ou contactez [opencode@microsoft.com](mailto:opencode@microsoft.com) si vous avez d’autres questions ou des commentaires.

[![État de la build](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>Documentation de PowerShell

Bienvenue dans le référentiel de documents de PowerShell, qui héberge la documentation officielle de PowerShell.

## <a name="repository-structure"></a>Structure du dépôt

Chacun des dossiers de premier niveau suivants dans ce référentiel contient un ensemble de documents qui sont publiés dans [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/Developer/](https://docs.microsoft.com/powershell/developer/) est le futur site de la documentation du kit de développement logiciel (SDK) PowerShell.
  - Nous sommes en train de migrer ce contenu à partir de MSDN.
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) correspond à la fonctionnalité de configuration d’état souhaité.
- [/gallery/](https://docs.microsoft.com/powershell/gallery) correspond à la [PowerShell Gallery](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) correspond à la fonctionnalité JEA (Just Enough Administration)
- [/reference/](https://docs.microsoft.com/powershell/scripting/) correspond aux sujets conceptuels et à la référence de module PowerShell dans les versions 3.0, 4.0, 5.0, 5.1 et 6.0.
  - Ce contenu est également la source de contenu d’aide récupéré par l’applet de commande `Get-Help`.
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) contient les notes de publication pour Windows Management Framework, le package utilisé pour distribuer les nouvelles versions de PowerShell aux versions antérieures de Windows.

## <a name="contributing"></a>Contribution

Nous fusionnons activement les contributions dans ce dépôt via une [demande Pull](https://help.github.com/articles/using-pull-requests/) dans la branche de *préproduction*.
Notez qu’avant d’envoyer une demande Pull, vous devez [signer un contrat de licence de contribution](https://cla.microsoft.com/) pour garantir que la communauté est libre d’utiliser vos envois.

Pour plus d’informations sur la contribution, lisez notre [guide du contributeur](CONTRIBUTING.md).
Le guide du contributeur contient des informations détaillées sur la manière de contribuer à la documentation, les outils, ainsi que sur les exigences concernant le style et la mise en forme.
Utilisez les modèles « Issue » et « Pull Request » afin que la documentation soit cohérente entre les versions.

## <a name="licenses"></a>Licences

Il existe deux fichiers de licence pour ce projet.
La licence MIT s’applique au code contenu dans ce dépôt.
La licence Creative Commons s’applique à la documentation.