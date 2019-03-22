---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
description: Recommandations pour les éditeurs
title: Instructions et bonnes pratiques de publication PowerShell Gallery
ms.openlocfilehash: 25c359c7acbe7430762a275d8cc4a28f527ec57a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056496"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Instructions et bonnes pratiques de publication PowerShell Gallery

Cette rubrique décrit les étapes recommandées suivies par les équipes Microsoft pour garantir que les packages publiés sur PowerShell Gallery seront largement adoptés et seront sources de valeur ajoutée pour les utilisateurs, en fonction de la manière dont PowerShell Gallery gère les données de manifeste et des nombreux commentaires envoyés par les utilisateurs de PowerShell Gallery.
Les packages publiés suivant ces recommandations ont plus de chances d’être installés, approuvés et plébiscités par les utilisateurs.

Voici des recommandations sur ce qui constitue un bon package PowerShell Gallery, les paramètres de manifeste facultatifs les plus importants, les moyens d’améliorer son code grâce aux commentaires des premiers réviseurs et aux informations fournies par [l’analyseur de script PowerShell](https://aka.ms/psscriptanalyzer), le contrôle de version des modules, la documentation, les tests et les exemples pour apprendre à utiliser le package partagé.
Une grande partie de cette documentation suit les instructions pour publier [des modules de ressources DSC haute qualité](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Pour connaître le mécanisme de publication d’un package sur PowerShell Gallery, voir [Créer et publier un package](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Les commentaires sur ces instructions sont les bienvenus. Si vous avez des commentaires, faites-le-nous savoir dans le [dépôt de notre documentation Github](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Meilleures pratiques pour publier des packages

Les bonnes pratiques suivantes reflètent ce que les utilisateurs d’éléments de PowerShell Gallery jugent important, et sont répertoriées par ordre de priorité nominal.
Les packages qui suivent ces recommandations ont beaucoup plus de chances d’être téléchargés et adoptés par d’autres d’utilisateurs.

- Utiliser PSScriptAnalyzer
- Inclure une documentation et des exemples
- Répondre aux commentaires
- Fournir des modules plutôt que des scripts
- Fournir des liens vers un site de projet
- Baliser votre package avec les plateformes et PSEdition(s) compatibles
- Inclure des tests incluant vos modules
- Inclure et/ou lier les termes du contrat de licence
- Signer votre code
- Suivre les instructions [SemVer](http://semver.org/) pour la gestion de versions
- Utiliser des balises courantes, comme expliqué dans les balises courantes de PowerShell Gallery
- Tester la publication à l’aide d’un dépôt local
- Utiliser PowerShellGet pour publier

Chacun de ces points est brièvement présenté dans les sections ci-dessous.

## <a name="use-psscriptanalyzer"></a>Utiliser PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) est un outil d’analyse de code statique gratuit qui fonctionne sur le code PowerShell.
PSScriptAnalyzer identifie les problèmes les plus courants dans le code PowerShell et fournit souvent une recommandation pour résoudre le problème.
Cet outil est facile à utiliser et classe les problèmes en erreurs (graves, à corriger), avertissements (à examiner et à corriger) et informations (à examiner pour définir de bonnes pratiques).
Tous les packages publiés sur PowerShell Gallery sont analysés avec PSScriptAnalyzer, et toutes les erreurs sont renvoyées au propriétaire, qui devra les corriger.

La meilleure pratique consiste à exécuter `Invoke-ScriptAnalyzer` avec `-Recurse` et un avertissement `-Severity`.

Examinez les résultats et vérifiez que :

- Toutes les erreurs ont été corrigées ou traitées dans votre documentation
- Tous les avertissements ont été examinés et traités le cas échéant

Les utilisateurs qui acquièrent des packages de PowerShell Gallery sont vivement invités à exécuter PSScriptAnalyzer et à examiner toutes les erreurs et tous les avertissements.
Ils contacteront très certainement les propriétaires des packages si PSScriptAnalyzer leur signale une erreur.
S’il existe une raison valable pour que votre package conserve du code identifié comme une erreur, ajoutez ces informations à votre documentation pour éviter d’avoir à répondre plusieurs fois à la même question.

## <a name="include-documentation-and-examples"></a>Inclure une documentation et des exemples

La meilleure façon de s’assurer que les utilisateurs tirent parti de n’importe quel code partagé est de leur fournir une documentation et des exemples.

La documentation est l’élément le plus utile à inclure dans les packages publiés sur PowerShell Gallery.
Les utilisateurs ignorent généralement les packages sans documentation, afin d’éviter d’avoir à lire le code pour comprendre ce que le package représente et comment l’utiliser.
Plusieurs articles expliquent comment ajouter de la documentation à des packages PowerShell, notamment :

- La rubrique [Comment rédiger l’aide sur une applet de commande](https://go.microsoft.com/fwlink/?LinkID=123415)
- La création de l’aide sur une applet de commande est la meilleure approche, qu’il s’agisse d’un script, d’une fonction ou d’une applet de commande PowerShell.
  Pour plus d’informations sur la création de l’aide d’une cmdlet, commencez par [Guide pratique pour écrire l’aide d’une cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415).
  Pour ajouter une aide dans un script, consultez [À propos de l’aide d’un commentaire](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- De nombreux modules incluent également une documentation au format texte, par exemple les fichiers MarkDown.
  Cela peut s’avérer particulièrement utile lorsque Github contient un projet dans lequel le format Markdown est très utilisé.
  La meilleure pratique consiste à utiliser un [format Markdown spécialement adapté à Github](https://help.github.com/categories/writing-on-github/)

Des exemples montrent comment utiliser le package.
De nombreux développeurs préfèrent consulter la documentation pour comprendre comment utiliser un élément.
Les meilleurs exemples montrent un cas d’utilisation basique, un cas d’utilisation réaliste simulé, et le code est bien commenté.
Les exemples pour les modules publiés dans PowerShell Gallery doivent figurer dans le dossier Exemples à la racine du module.

Vous trouverez de bons exemples dans le [module PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) du dossier Examples\RegistryResource.
Quatre exemples de cas d’utilisation sont disponibles avec, en haut de chaque fichier, une brève description des éléments présentés.

## <a name="respond-to-feedback"></a>Répondre aux commentaires

Les propriétaires de packages qui répondent convenablement aux commentaires sont très appréciés de la communauté.
Il est important de répondre aux utilisateurs qui apportent des commentaires constructifs, car ces derniers se montrent suffisamment intéressés par le package pour aider à l’améliorer.

PowerShell Gallery propose deux méthodes pour fournir des commentaires :

- Contacter le propriétaire : les utilisateurs peuvent ainsi envoyer un e-mail au(x) propriétaire(s) du package. Il est important pour ces derniers de surveiller le compte de messagerie utilisé avec les packages PowerShell Gallery et de répondre aux problèmes soulevés. L’un des inconvénients de cette méthode est que seul l’utilisateur et propriétaire verra la communication et il risque donc de répondre plusieurs fois à la même question.
- Commentaires : un champ Commentaire est proposé en bas de la page du package.
  L’avantage de ce système est que les autres utilisateurs peuvent voir les commentaires et les réponses, ce qui réduit le nombre de fois où ils doivent répondre à une même question.
  Il est fortement recommandé aux propriétaires de packages de suivre les commentaires de chaque package.
Consultez la rubrique [Envoi de commentaires via des médias sociaux ou des commentaires](../how-to/working-with-packages/social-media-feedback.md) pour plus d’informations sur la procédure à suivre.

Les propriétaires qui répondent de manière constructive aux commentaires sont appréciés par la communauté.
Utilisez le rapport pour demander plus d’informations, si nécessaire, proposer une solution de contournement, ou indiquer si une mise à jour peut résoudre un problème.

Si vous constatez un comportement inapproprié sur l’un de ces canaux de communication, utilisez la fonctionnalité Signaler un abus de PowerShell Gallery pour contacter les administrateurs.

## <a name="modules-versus-scripts"></a>Différences entre les modules et les scripts

Partager un script avec d’autres utilisateurs est une excellente idée qui leur offre d’autres exemples montrant comment résoudre les problèmes qu’ils peuvent rencontrer.
Le problème est que les scripts de PowerShell Gallery sont des fichiers sans documentation, exemples ou tests distincts.

Les Modules PowerShell ont une structure de dossiers qui permet d’inclure plusieurs dossiers et fichiers dans le package.
La structure du module permet d’inclure les autres packages que nous avons présentés parmi les meilleures pratiques : aide sur la cmdlet, documentation, exemples et tests.
Le principal inconvénient est qu’un script situé à l’intérieur d’un module doit être exposé et utilisé en tant que fonction.
Pour plus d’informations sur la création d’un module, voir [Écrire un module Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Il existe des situations où un script fournit une meilleure expérience à l’utilisateur, en particulier avec les configurations DSC.
Pour les configurations DSC, la meilleure solution consiste à publier la configuration en tant que script avec un module connexe contenant les documents, les exemples et les tests.
Le script répertorie le module connexe à l’aide de RequiredModules = @(nom du module).
Cette approche peut être utilisée avec n’importe quel script.

Les scripts autonomes qui suivent les bonnes pratiques apportent une vraie valeur à d’autres utilisateurs.
Il est vivement recommandé de fournir une documentation basée sur des commentaires ainsi qu’un lien vers un site de projet lorsque vous publiez un script dans PowerShell Gallery.

## <a name="provide-a-link-to-a-project-site"></a>Fournir un lien vers un site de projet

C’est sur le Site de projets que l’éditeur peut interagir directement avec les utilisateurs de ses packages PowerShell Gallery.
Les utilisateurs préfèrent les packages qui possèdent un Site de projets, car c’est pour eux le moyen d’obtenir plus facilement des informations sur les packages.
De nombreux packages de PowerShell Gallery sont développés sur GitHub, tandis que d’autres sont fournis par des organisations qui possèdent une présence web dédiée.
Dans les deux cas, il s’agit d’un site de projet.

L’ajout d’un lien s’effectue en incluant ProjectURI dans la section PSData du manifeste, comme suit :

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Lorsqu’un ProjectURI est indiqué, PowerShell Gallery inclut un lien vers le Site de projets sur le côté gauche de la page du package.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Baliser votre package avec les plateformes et PSEdition(s) compatibles

Utilisez les balises suivantes pour montrer aux utilisateurs quels packages fonctionneront correctement avec leur environnement :

- PSEdition_Desktop : packages compatibles avec Windows PowerShell
- PSEdition_Core : packages compatibles avec PowerShell Core
- Windows : packages compatibles avec le système d’exploitation Windows
- Linux : packages compatibles avec les systèmes d’exploitation Linux
- MacOS : packages compatibles avec le système d’exploitation Mac

## <a name="include-tests"></a>Inclure des tests

Il est important de proposer aux utilisateurs des tests avec un code open source car cela leur fournit des garanties sur le contenu que vous validez ainsi que des informations sur le fonctionne de votre code. Cela permet également aux utilisateurs de s’assurer qu’ils ne bloquent pas votre fonctionnalité d’origine lorsqu’ils modifient votre code pour l’adapter à leur environnement.

Il est fortement recommandé d’écrire des tests qui tirent parti de l’infrastructure de test Pester, qui a été spécialement conçue pour PowerShell.
Pester est disponible dans [GitHub](https://github.com/Pester/Pester), dans [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/), et est inclut avec Windows 10, Windows Server 2016, WMF 5.0 et WMF 5.1.

Le [site du projet Pester dans GitHub](https://github.com/Pester/Pester) comprend une bonne documentation sur l’écriture de tests de Pester, du démarrage aux bonnes pratiques.

Les cibles pour la couverture de test sont appelées dans la [documentation du module de ressources haute qualité](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), avec une recommandation de couverture du code de test de 70 %.

## <a name="include-andor-link-to-license-terms"></a>Inclure et/ou lier les termes du contrat de licence

Tous les packages publiés sur PowerShell Gallery doivent spécifier les termes du contrat de licence ou être liés par la licence incluse dans les [Conditions d’utilisation](https://www.powershellgallery.com/policies/Terms), sous « Annexe A ».
La meilleure approche pour spécifier une autre licence consiste à fournir un lien vers la licence à l’aide de LicenseURI dans PSData.
Vous trouverez un exemple dans la rubrique de Champs de manifeste recommandés.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Signer votre code

La signature du code offre aux utilisateurs le niveau le plus élevé d’assurance concernant l’éditeur du package, et leur garantit que la copie du code qu’ils acquièrent correspond exactement à ce que ce dernier a publié.
Pour en savoir plus sur la signature du code en général, voir [Introduction à la signature du code](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell prend en charge la validation de la signature du code via deux approches :

- Signature des fichiers de script
- Signature d’un module par un catalogue

La signature des fichiers PowerShell est une approche parfaitement établie pour garantir que le code en cours d’exécution a été produit par une source fiable et n’a pas été modifié.
Pour plus d’informations sur la façon de signer des fichiers de script PowerShell, voir la rubrique [À propose de la signature](/powershell/module/microsoft.powershell.core/about/about_signing).
Pour résumer, une signature peut être ajoutée à tout fichier .PS1 validé par PowerShell lorsque le script est chargé.
PowerShell peut être contraint à utiliser les applets de commande de la [stratégie d’exécution](/powershell/module/microsoft.powershell.core/about/about_execution_policies) pour forcer l’utilisation de scripts signés.

La signature de modules par un catalogue est une fonctionnalité ajoutée à la version 5.1 de PowerShell.
La signature d’un module est abordée dans la rubrique [Applets de commande de catalogue](/powershell/wmf/5.1/catalog-cmdlets).
Pour résumer, la signature du catalogue s’effectue en créant un fichier de catalogue contenant une valeur de hachage pour chaque fichier dans le module, puis en signant ce fichier.
Les cmdlets PowerShellGet publish-module, install-module, save-module et update-module vérifient la validité de la signature, puis confirment que la valeur de hachage de chaque package correspond à ce qui figure dans le catalogue.
Si une version précédente du module est installée sur le système, l’applet de commande install-module confirmera que l’autorité de signature de la nouvelle version correspond à ce qui a été précédemment installé.
La signature du catalogue complète mais ne remplace pas la signature des fichiers de script. PowerShell ne valide pas les signatures du catalogue lors du chargement du module.

## <a name="follow-semver-guidelines-for-versioning"></a>Suivre les instructions SemVer pour la gestion de versions

[SemVer](http://semver.org/) est une convention publique qui explique comment structurer et changer une version pour faciliter l’interprétation des modifications.
La version de votre package doit être incluse dans les données de manifeste.

- La version doit être structurée sous forme de 3 blocs numériques séparés par des points, par exemple 0.1.1 ou 4.11.192
- Les versions commençant par « 0 » indiquent que le package n’est pas encore prêt pour la mise en production ; le premier numéro doit commencer par « 0 » uniquement s’il s’agit du seul numéro utilisé
- Les modifications dans le premier numéro (1.9.9999 à 2.0.0) indiquent des modifications majeures et importantes entre les versions
- Les modifications du second numéro (1.1 à 1.2) indiquent une évolution des fonctionnalités, par exemple, l’ajout de nouvelles cmdlets à un module
- Les modifications dans le troisième numéro indiquent des modifications mineures, par exemple de nouveaux paramètres, des exemples mis à jour ou de nouveaux tests
- Pour répertorier les versions, PowerShell trie les versions sous forme de chaînes, par conséquent 1.01.0 sera considéré comme étant supérieur à 1.001.0

Comme PowerShell a été créé avant la publication de SemVer, il prend en charge la plupart mais pas tous les éléments de SemVer, en particulier :

- Il ne prend pas en charge les chaînes préliminaires dans les numéros de version. Cela est utile lorsqu’un éditeur souhaite fournir une version préliminaire d’une nouvelle version majeure après avoir fourni une version 1.0.0. Cette opération est prise en charge dans une version ultérieure des applets de commande PowerShell Gallery et PowerShellGet.
- PowerShell et PowerShell Gallery acceptent des chaînes de version contenant 1, 2 et 4 segments. De nombreux modules précédents ne suivaient pas ces instructions, et les versions de produit publiées par Microsoft incluent des informations de build sous forme de blocs à 4 éléments (par exemple 5.1.14393.1066). Du point de vue de la gestion de versions, ces différences sont ignorées.

## <a name="test-using-a-local-repository"></a>Tester à l’aide d’un dépôt local

PowerShell Gallery n’est pas conçu pour être une cible servant à tester le processus de publication.
La meilleure façon de tester le processus de publication de bout en bout dans PowerShell Gallery consiste à configurer et à utiliser votre propre dépôt local.
Vous pouvez effectuer ces opérations de différentes manières, notamment :

- Configurez une instance locale de PowerShell Gallery avec le [projet PS Private Gallery](https://github.com/PowerShell/PSPrivateGallery) dans Github. Ce projet en préversion vous permet de configurer une instance de PowerShell Gallery que vous pouvez contrôler, puis de l’utiliser pour vos tests.
- Configurez un [dépôt Nuget interne](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Cette configuration demande plus de travail mais a l’avantage de valider quelques éléments requis supplémentaires, notamment la validation de l’utilisation d’une clé API et la présence ou non de dépendances dans la cible lors de la publication.
- Configurez un partage de fichiers en tant que « dépôt » de test. Cette configuration est facile, mais comme il s’agit d’un partage de fichiers, les validations indiquées ci-dessus n’existent pas. Un avantage potentiel ici est que le partage de fichiers ne vérifie pas la clé API (obligatoire), donc vous pouvez utiliser la même clé pour publier dans PowerShell Gallery.

Avec l’une de ces solutions, utilisez Register-PSRepository pour définir un nouveau « dépôt », que vous utilisez dans la propriété -Repository pour Publish-Module.

Autre point sur la publication de test : il n’est pas possible de supprimer les packages publiés sur PowerShell Gallery sans l’aide de l’équipe des opérations, qui doit confirmer que rien ne dépend du package en question.
Pour cette raison, nous ne prenons pas en charge PowerShell Gallery comme cible de test. Nous contacterons un éditeur qui assure cette prise en charge.

## <a name="use-powershellget-to-publish"></a>Utiliser PowerShellGet pour publier

Il est fortement recommandé aux éditeurs d’utiliser les applets de commande Publish-Module et Publish-Script avec PowerShell Gallery.
PowerShellGet a été créé pour vous éviter d’avoir à retenir certains détails importants au sujet de l’installation et de la publication sur PowerShell Gallery.
À certaines occasions, les éditeurs ont choisi d’ignorer PowerShellGet pour utiliser le client NuGet ou les applets de commande PackageManagement à la place de Publish-Module.
Il est facile d’oublier certains détails, ce qui donne lieu à diverses demandes de support.

Si, pour une raison quelconque, vous ne pouvez pas utiliser Publish-Module ou Publish-Script, faites-le nous savoir.
Signalez un problème dans le dépôt GitHub de PowerShellGet et dites-nous ce qui vous a amené à opter pour NuGet ou PackageManagement.

## <a name="recommended-workflow"></a>Flux de travail recommandé

L’approche la plus efficace que nous ayons trouvée pour les packages publiés sur PowerShell Gallery est la suivante :

- Effectuer un développement initial dans un site de projet open source. L’équipe PowerShell utilise Github.
- Utiliser les commentaires des réviseurs et l’[analyseur de script Powershell](https://aka.ms/psscriptanalyzer) pour amener le code à un état stable
- Inclure une documentation afin que d’autres utilisateurs puissent profiter de votre travail
- Tester l’action de publication à l’aide d’un dépôt local.
- Publier une version stable ou une version alpha dans PowerShell Gallery, en veillant à inclure la documentation et un lien vers votre site de projet
- Recueillir des commentaires et effectuer une itération sur le code dans votre site de projet, puis publier des mises à jour stables dans PowerShell Gallery
- Ajouter des exemples et des tests Pester à votre projet et votre module
- Décider de signer ou non le code de votre package
- Lorsque vous estimez que le projet est prêt à être utilisé dans un environnement de production, publiez une version 1.0.0 version dans PowerShell Gallery
- Continuer à recueillir des commentaires et effectuer une itération sur votre code en fonction des entrées utilisateur
