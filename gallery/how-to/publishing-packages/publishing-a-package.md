---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Création et publication d’un élément
ms.openlocfilehash: 70696535a3bf540ff75a2dc43bca80cb1adf8f45
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677815"
---
# <a name="creating-and-publishing-an-item"></a>Création et publication d’un élément

PowerShell Gallery est l’emplacement auquel publier et partager des modules PowerShell stables, des scripts et des ressources DSC avec l’ensemble de la communauté des utilisateurs PowerShell.

Cet article décrit les mécanismes et les principales étapes de la préparation d’un script ou d’un module, et sa publication dans PowerShell Gallery. Nous vous encourageons vivement à consulter les [instructions de publication](../../concepts/publishing-guidelines.md) pour comprendre comment vous assurer que les éléments que vous publiez seront plus largement acceptés par les utilisateurs de PowerShell Gallery.

Voici les conditions minimales requises pour publier un élément sur PowerShell Gallery :

- Disposer d’un compte de galerie PowerShell et d’une clé d’API associée
- Vérifiez que les métadonnées requises se trouvent dans votre élément
- Utiliser les outils de prévalidation pour garantir que votre élément est prêt à être publié
- Publier l’élément à l’aide des commandes Publish-Module et Publish-Script de PowerShell Gallery
- Répondre aux questions ou des commentaires sur votre élément

PowerShell Gallery accepte les modules PowerShell et les scripts PowerShell. Lorsque nous faisons référence à des scripts, nous entendons un script PowerShell qui est un fichier unique et ne fait pas partie d’un module plus vaste.

## <a name="powershell-gallery-account-and-api-key"></a>Compte et clé d’API pour PowerShell Gallery

Consultez [Création d’un compte PowerShell Gallery](/powershell/gallery/how-to/publishing-packages/creating-an-account) pour savoir comment configurer votre compte de PowerShell Gallery.

Une fois que vous avez créé un compte, vous pouvez obtenir la clé d’API nécessaire pour publier un élément. Une fois que vous vous connectez avec le compte, votre nom d’utilisateur s’affichera en haut des pages de PowerShell Gallery au lieu du Registre. Cliquer sur votre nom d’utilisateur vous redirigera vers la page Mon compte, où vous trouverez la clé d’API.

Remarque : La clé d’API doivent être traitée de façon aussi sécurisée que votre connexion et le mot de passe.
Avec cette clé, vous,ou toute autre personne pouvez mettre à jour n’importe quel élément que vous possédez dans PowerShell Gallery.
Nous vous recommandons de mettre à jour la clé régulièrement, ce que vous pouvez faire à l’aide de la fonction Réinitialiser la clé sur la page Mon compte.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Métadonnées requises pour les articles publiés sur PowerShell Gallery

PowerShell Gallery fournit des informations aux utilisateurs de la galerie tirées des champs de métadonnées qui sont inclus dans le manifeste de module ou du script. Créer ou modifier des éléments pour la publication dans PowerShell Gallery a un petit ensemble de d’exigences pour les informations fournies dans le manifeste de l’élément.
Nous vous encourageons vivement de consulter la section de métadonnées d’élément des [instructions de publication](../../concepts/publishing-guidelines.md) pour apprendre à fournir les meilleures informations aux utilisateurs avec vos éléments.

Les applets de commande [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) et [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) créent le modèle de manifeste pour vous, avec des espaces réservés pour tous les éléments du manifeste.

Les deux manifestes ont deux sections qui sont importantes pour la publication, la zone données de clé primaire et PSData de PrivateData. Les données de clé primaire dans un manifeste de module PowerShell sont tout en dehors de la section PrivateData. Le jeu de clés primaires est lié à la version de PowerShell en cours d’utilisation et la non-définition n’est donc pas pris en charge. PrivateData prend en charge l’ajout de nouvelles clés, aussi les éléments spécifiques à PowerShell Gallery se trouvent dans PSData.


Les éléments de manifeste les plus importants à remplir pour les éléments à publier dans PowerShell Gallery sont les suivants :

- Nom du script ou du module - Ces valeurs sont extraites des noms des .PS1 dans le script, ou du .PSD1 pour un module.
- Version - il s’agit d’une clé primaire requise, le format doit suivre les instructions SemVer. Pour plus d’informations, voir meilleures pratiques.
- Auteur - Ceci est une clé primaire requise et contient le nom à associer à l’élément.
Voir auteurs et propriétaires ci-dessous.
- Description - il s’agit d’une clé primaire requise, utilisée pour expliquer brièvement ce que fait cet élément et les conditions requises pour son utilisation
- ProjectURI - il s’agit d’un champ URI fortement recommandé dans PSData qui fournit un lien vers un référentiel Github ou un emplacement similaire où vous effectuez le développement sur l’élément
- Balises : il est recommandé de baliser votre package en fonction de sa compatibilité avec des éditions PS et plateformes. Pour plus d’informations, consultez les [instructions de publication](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Les Auteurs et Propriétaires d’éléments de PowerShell Gallery sont des concepts connexes, mais ils ne correspondent pas toujours. Les propriétaires d’élément sont des utilisateurs avec des comptes PowerShell Gallery qui sont autorisés à mettre à jour l’élément. Il peut y avoir de nombreux propriétaires qui peuvent mettre à jour n’importe quel élément. Le propriétaire est uniquement disponible à partir de PowerShell Gallery et est perdu si l’élément est copié d’un système à un autre. Auteur est une chaîne qui se trouve dans les données de manifeste, et fait donc toujours partie de l’élément. Les recommandations pour les éléments des produits Microsoft sont :

- Avoir plusieurs propriétaires, dont au moins un porte le nom de l’équipe qui produit l’élément ;
- Avoir un auteur avec un nom d’équipe connu (par exemple, Équipe du kit de développement (SDK) logiciel Azure), ou Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Prévalider votre élément

Il existe certains outils que vous devez exécuter sur votre code avant de publier votre élément dans PowerShell Gallery :

- [L’analyseur de script PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), qui se trouve dans PowerShell Gallery
- Pour les modules, Test-ModuleManifest, qui fait partie de PowerShell
- Pour les scripts, Test-ScriptFileInfo, qui est proposé avec PowerShell Get

[L’analyseur de script PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) est un outil d’analyse de code statique qui analyse votre code pour vous assurer qu’il répond aux consignes de base en matière de codage pour PowerShell. Cet outil identifie les problèmes courants et critiques dans votre code, et doit être exécuté régulièrement pendant le développement pour vous aider à préparer votre élément pour la publication. L’analyseur de script PowerShell fournit la liste des problèmes identifiés en tant qu’erreurs, avertissements et informations. Toutes les erreurs doivent être traitées avant de publier dans PowerShell Gallery. Les avertissements doivent être passés en revue, et la plupart doivent être traités. L’analyseur de script PowerShell est exécuté chaque fois qu’un article est publié ou mis à jour dans PowerShell Gallery. L’équipe des opérations de PowerShell Gallery contacte les propriétaires de l’élément pour corriger les erreurs qui ont été identifiées.

Si les informations de manifeste dans votre élément ne peuvent pas être lues par l’infrastructure de PowerShell Gallery, vous ne pourrez pas publier.
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) intercepte les problèmes courants qui rendraient le module inutilisable lorsqu’il est installé. Il doit être exécuté pour chaque module avant sa publication dans PowerShell Gallery.

De même, [Test-ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) valide les métadonnées dans un script et doit être exécuté sur chaque script (publié séparément à partir d’un module) avant sa publication dans PowerShell Gallery.


## <a name="publishing-items"></a>Publication d’éléments

Vous devez utiliser [Publish-Script](/powershell/module/PowerShellGet/publish-script) ou [Publish-Module](/powershell/module/PowerShellGet/publish-module) pour publier des éléments dans la PowerShell Gallery. Ces commandes requièrent :

- Le chemin d’accès à l’élément que vous allez publier. Pour un module, utilisez le dossier nommé pour votre module. Si vous spécifiez un dossier qui contient plusieurs versions du même module, vous devez spécifier RequiredVersion.
- Une clé de l’API Nuget. Il s’agit de la clé d’API qui se trouve sur la page Mon compte dans PowerShell Gallery.

La plupart des autres options de la ligne de commande doivent se trouver dans les données de manifeste pour l’élément que vous publiez, il ne devrait donc pas être nécessaire de les spécifier dans la commande.

Pour éviter les erreurs, il est fortement recommandé d’essayer les commandes avec -Whatif -Verbose avant la publication. Cela vous fera gagner beaucoup de temps, car vous devez mettre à jour le numéro de version dans la section du manifeste de l’élément chaque fois que vous publiez dans PowerShell Gallery.

Exemples serait :

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -Whatif -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose`

Examinez la sortie avec soin et si vous ne voyez aucune erreur ou avertissement, répétez la commande sans -Whatif.

Tous les éléments qui sont publiés dans PowerShell Gallery font l’objet d’une analyse antivirus et sont analysés à l’aide de l’analyseur de script PowerShell. Les problèmes qui surviennent à ce moment-là sont envoyés à l’éditeur pour résolution.

Une fois que vous avez publié un élément dans PowerShell Gallery, vous devez consulter les commentaires sur votre élément.

- Veillez à surveiller l’adresse de messagerie associée au compte utilisé pour publier. Les utilisateurs et l’équipe des opérations de PowerShell Gallery fournissent des commentaires via ce compte, y compris sur les problèmes de la PSSA ou des analyses antivirus. Si le compte de messagerie n’est pas valide, ou si des problèmes graves sont signalés pour le compte sans être résolus pendant un certain temps, les éléments peuvent être considérés comme abandonnés et être supprimés de PowerShell Gallery comme décrit dans nos [conditions d’utilisation](https://www.powershellgallery.com/policies/Terms).
- Nous vous recommandons de vous abonner aux commentaires pour chaque élément de PowerShell Gallery que vous publiez. Cela vous permet d’être averti si quelqu’un publie des commentaires sur vos éléments dans PowerShell Gallery. Cela est facultatif, car cela nécessite la création d’un compte avec LiveFyre.
