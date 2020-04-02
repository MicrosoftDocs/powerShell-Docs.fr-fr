---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: FAQ PowerShell Gallery
ms.openlocfilehash: 035681e108e1a3e05fe5d659d527ae1ad1c64cf4
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500591"
---
# <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

## <a name="what-is-a-powershell-module"></a>Qu’est-ce qu’un module PowerShell ?

Un module PowerShell est un package réutilisable contenant des fonctionnalités PowerShell. Tous les éléments de PowerShell (fonctions, variables, ressources DSC, etc.) peuvent être empaquetés dans des modules. En règle générale, les modules sont des dossiers qui contiennent des types spécifiques de fichiers stockés dans un chemin spécifique. Il existe différents types de modules PowerShell.

## <a name="what-is-a-powershell-script"></a>Qu’est-ce qu’un script PowerShell ?

Un script PowerShell est une série de commandes qui sont stockées dans un fichier .ps1 pour permettre la réutilisation et le partage. Les workflows PowerShell sont également des scripts PowerShell, qui présentent une série de tâches et donnent le séquencement de ces tâches. Pour plus d’informations, visitez le site [Présentation du workflow Windows PowerShell](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>En quoi les scripts PowerShell sont-ils différents des modules PowerShell ?

Les modules conviennent généralement mieux pour le partage, mais nous allons permettre le partage de scripts pour que vous puissiez facilement fournir des workflows et des scripts à la communauté. Pour plus d’informations, voir les blogs suivants :

- [Don’t Write Scripts, Write PowerShell Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Understanding PowerShell Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Comment puis-je publier dans PowerShell Gallery ?

Vous devez inscrire un compte dans PowerShell Gallery avant de pouvoir y publier des packages. En effet, la publication de packages nécessite un NuGetApiKey, qui est fourni lors de l’inscription. Pour vous inscrire, utilisez votre compte personnel, professionnel ou scolaire pour vous connecter à PowerShell Gallery. Un processus d’inscription à usage unique est nécessaire quand vous vous connectez pour la première fois.
Votre NuGetApiKey est ensuite disponible dans la page de votre profil.

Une fois que vous êtes inscrit dans PowerShell Gallery, utilisez les applets de commande [Publish-Module][] ou [Publish-Script][] pour y publier votre package. Pour plus d’informations sur l’exécution de ces applets de commande, examinez l’onglet Publier ou lisez la documentation sur [Publish-Module][] et [Publish-Script][].

**Il est inutile de s’inscrire ou de se connecter à PowerShell Gallery pour installer ou enregistrer des packages.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>J’ai reçu un message de type « Échec du traitement de la demande. La clé API spécifiée n’est pas valide ou n’est pas autorisée à accéder au package spécifié ». Le serveur distant a retourné une erreur : « (403) Interdit. » Erreur quand j’ai essayé de publier un package dans PowerShell Gallery. Qu'est-ce que cela signifie ?

Cette erreur peut se produire pour les raisons suivantes :

- **La clé d’API spécifiée n’est pas valide.** Vérifiez que vous avez spécifié la clé API valide à partir de votre compte. Pour obtenir votre clé API, examinez la page de votre profil.
- **Le nom du package spécifié ne vous appartient pas.** Si vous avez vérifié que votre clé API est correcte, il existe peut-être déjà un package portant le même nom que celui que vous essayez d’utiliser. Le package peut avoir été retiré de la liste par le propriétaire, auquel cas il n’apparaît dans aucun résultat de recherche. Pour déterminer si un package portant le même nom existe déjà, ouvrez un navigateur et accédez à la page de détails du package : `https://www.powershellgallery.com/packages/<packageName>`. Par exemple, un accès direct à `https://www.powershellgallery.com/packages/pester` vous dirige vers la page de détails du module Pester, qu’il soit répertorié ou non. Si un package avec un nom en conflit existe déjà et n’est pas répertorié, vous pouvez :
  - sélectionner un autre nom pour votre package ;
  - contacter les propriétaires du package existant.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Pourquoi ne puis-je pas me connecter avec mon compte personnel, alors que cela était possible hier ?

Gardez à l’esprit que votre compte de galerie n’intègre pas les modifications apportées à votre alias d’e-mail principal.
Pour plus d’informations, voir [Gérer les alias liés à votre compte Microsoft](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Pourquoi ne puis-je pas afficher tous les packages de la galerie quand je coche toutes les cases de catégorie sous l’onglet Packages ?

En cochant une case de catégorie, vous indiquez « J’aimerais voir tous les packages de cette catégorie. » Seuls les packages dans les catégories sélectionnées s’affichent. De même, si vous cochez toutes les cases de catégorie, vous indiquez « J’aimerais voir tous les packages dans n’importe quelle catégorie. » Toutefois, comme certains packages de la galerie n’appartiennent à aucune des catégories répertoriées, ils n’apparaissent pas dans les résultats. Pour afficher tous les packages de la galerie, décochez toutes les catégories, ou sélectionnez à nouveau l’onglet Packages.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Quelles sont les conditions requises pour publier un module dans PowerShell Gallery ?

Tout type de module PowerShell (modules de script, modules binaires ou modules de manifeste) peut être publié dans la galerie. Pour publier un module, PowerShellGet doit connaître quelques détails le concernant : version, description, auteur et mode de licence. Ces informations sont lues lors du processus de publication à partir du fichier *manifeste de module* (.psd1) ou de la valeur du paramètre **LicenseUri** de l’applet de commande [Publish-Module][]. Tous les modules publiés dans PowerShell Gallery doivent avoir des manifestes de module. Tout module qui inclut les informations suivantes dans son manifeste peut être publié dans PowerShell Gallery :

- Version
- Description
- Auteur
- URI vers les termes du contrat de licence du module, dans le cadre de la section **PrivateData** du manifeste ou dans le paramètre **LicenseUri** de l’applet de commande [Publish-Module][].

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Comment créer un manifeste de module correctement mis en forme ?

La façon la plus simple de créer un manifeste de module consiste à exécuter l’applet de commande [New-ModuleManifest][]. Dans PowerShell 5.0 ou version ultérieure, New-ModuleManifest génère un manifeste de module correctement mis en forme avec des champs vides pour les métadonnées utiles comme **ProjectUri**, **LicenseUri** et **Tags**. Il suffit de remplir les champs vides ou d’utiliser le manifeste généré comme un exemple de mise en forme correcte.

Pour vérifier que tous les champs de métadonnées obligatoires ont été correctement remplis, utilisez l’applet de commande [Test-ModuleManifest][].

Pour mettre à jour les champs de fichier manifeste de module, utilisez l’applet de commande [Update-ModuleManifest][].

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Quelles sont les conditions requises pour publier un script dans PowerShell Gallery ?

Tout type de script PowerShell (scripts ou workflows) peut être publié dans la galerie. Pour publier un script, PowerShellGet doit connaître quelques détails le concernant : version, description, auteur et mode de licence. Ces informations sont lues lors du processus de publication à partir de la section *PSScriptInfo* du fichier de script ou de la valeur du paramètre **LicenseUri** de l’applet de commande [Publish-Script][]. Tous les scripts publiés dans PowerShell Gallery doivent avoir des informations de métadonnées. Tout script qui inclut les informations suivantes dans sa section PSScriptInfo peut être publié dans PowerShell Gallery :

- Version
- Description
- Auteur
- URI vers les termes du contrat de licence du script, dans la section **PSScriptInfo** du script ou dans le paramètre **LicenseUri** de l’applet de commande [Publish-Script][].

## <a name="how-do-i-search"></a>Comment effectuer des recherches ?

Tapez ce que vous recherchez dans la zone de texte. Par exemple, si vous souhaitez rechercher les modules qui sont liés à SQL Azure, tapez simplement « sql azure ». Notre moteur de recherche recherche ces mots clés dans tous les packages publiés, dont les titres, les descriptions et les métadonnées. Ensuite, selon un score de qualité pondéré, il affiche les correspondances les plus proches. Vous pouvez également effectuer des recherches par champ spécifique à l’aide de la syntaxe field:"value" dans la requête de recherche pour les champs suivants :

- Balises
- Fonctions
- Applets de commande
- DscResources
- PowerShellVersion

Ainsi, par exemple, quand vous recherchez PowerShellVersion:"2.0", seuls les résultats qui sont compatibles avec PowerShellVersion 2.0 (selon leur manifeste de module/script) sont affichés.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Comment créer un fichier de script correctement mis en forme ?

La façon la plus simple de créer un fichier de script correctement mis en forme consiste à exécuter l’applet de commande [New-ScriptFileInfo][]. Dans PowerShell 5.0, New-ScriptFileInfo génère un fichier de script correctement mis en forme avec des champs vides pour les métadonnées utiles comme **ProjectUri**, **LicenseUri** et **Tags**. Il suffit de remplir les champs vides ou d’utiliser le fichier de script généré comme un exemple de mise en forme correcte.

Pour vérifier que tous les champs de métadonnées obligatoires ont été correctement remplis, utilisez l’applet de commande [Test-ScriptFileInfo][].

Pour mettre à jour les champs de métadonnées de script, utilisez l’applet de commande [Update-ScriptFileInfo][].

## <a name="what-other-types-of-powershell-modules-exist"></a>Quels autres types de modules PowerShell existent ?

Le terme module PowerShell fait également référence aux fichiers qui implémentent les fonctionnalités réelles. Les fichiers de module de script (.psm1) contiennent du code PowerShell. Les fichiers de module binaire (.dll) contiennent du code compilé.

Voici une illustration possible : le dossier qui encapsule le module est le dossier du module. Le dossier de module peut contenir un manifeste de module (.psd1) qui décrit le contenu du dossier. Les fichiers qui sont en réalité mis à contribution sont les fichiers de module de script (.psm1) et les fichiers de module binaire (.dll). Les ressources DSC sont situées dans un sous-dossier spécifique et sont implémentées en tant que fichiers de module de script ou fichiers de module binaire.

Tous les modules dans PowerShell Gallery contiennent des manifestes de module, et la plupart de ces modules contiennent des fichiers de module de script ou des fichiers de module binaire. Le terme module peut prêter à confusion en raison de ces différentes significations. Sauf spécification contraire, toutes les utilisations du mot module dans cette page font référence au dossier du module contenant ces fichiers.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Quelle est la relation entre PackageManagement et PowerShellGet ? (Réponse générale)

PackageManagement est une interface commune permettant de travailler avec n’importe quel gestionnaire de package. Finalement, qu’il s’agisse de modules PowerShell, de MSI, de RubyGems, de packages NuGet ou de modules Perl, vous devez pouvoir utiliser des commandes de PackageManagement (Find-Package et Install-Package) pour les rechercher et les installer. Pour cela, PackageManagement dispose d’un fournisseur de package pour chaque gestionnaire de package qui s’intègre à PackageManagement. Les fournisseurs effectuent l’intégralité du travail réel ; ils extraient le contenu des référentiels et l’installent en local. Souvent, les fournisseurs de package enveloppent simplement les outils du gestionnaire de package existants pour un type de package donné.

PowerShellGet est le gestionnaire de package pour les packages PowerShell. Il existe un fournisseur de package PSModule qui expose les fonctionnalités PowerShellGet via PackageManagement. Pour cette raison, vous pouvez exécuter [Install-Module][] ou Install-Package -Provider PSModule pour installer un module à partir de PowerShell Gallery. Certaines fonctionnalités PowerShellGet, dont [Update-Module][] et [Publish-Module][], ne sont pas accessibles via les commandes PackageManagement.

En résumé, PowerShellGet a pour unique objectif de réussir une expérience de gestion des packages pour le contenu PowerShell. PackageManagement se concentre sur l’exposition de toutes les expériences de gestion des packages via un ensemble général d’outils. Si cette réponse ne vous satisfait pas, vous en trouverez une plus détaillée à la fin de ce document, dans la section **Quelle est la relation réelle entre PackageManagement et PowerShellGet ?** .

Pour plus d’informations, visitez la [page de projet PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Quelle est la relation entre NuGet et PowerShellGet ?

PowerShell Gallery est une version modifiée de la [galerie NuGet](https://www.nuget.org/).
PowerShellGet emploie le fournisseur NuGet pour utiliser les référentiels NuGet, comme PowerShell Gallery.

Vous pouvez utiliser PowerShellGet sur n’importe quel partage de fichiers ou référentiel NuGet valide. Vous devez simplement ajouter le référentiel en exécutant l’applet de commande [Register-PSRepository][].

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Est-ce que cela signifie que je peux employer NuGet.exe pour utiliser PowerShell Gallery ?

Oui.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Quelle est la relation réelle entre PackageManagement et PowerShellGet ? (Détails techniques)

Du point de vue de l’implémentation, PowerShellGet exploite intensément l’infrastructure PackageManagement.

Dans la couche d’applet de commande PowerShell, [Install-Module][] est en fait un simple wrapper autour de `Install-Package -Provider PSModule`.

Dans la couche de fournisseur de package PackageManagement, le fournisseur de package PSModule appelle en fait d’autres fournisseurs de package PackageManagement. Par exemple, quand vous utilisez des galeries NuGet (telles que PowerShell Gallery), le fournisseur de package PSModule utilise le fournisseur de package NuGet pour travailler avec le référentiel.

![Architecture PowerShellGet](media/faqs/powershellgetArchitecture.png)

Figure 1 : Architecture PowerShellGet

## <a name="what-is-required-to-run-powershellget"></a>Éléments nécessaires pour exécuter PowerShellGet

En général, nous recommandons de choisir la dernière version du module PowerShellGet (notez qu’il requiert .NET 4.5).

Le module **PowerShellGet** nécessite **PowerShell 3.0 ou ultérieur**.

Par conséquent, **PowerShellGet** nécessite l’un des systèmes d’exploitation suivants :

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Entreprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** nécessite également .NET Framework 4.5 ou ultérieur. Vous pouvez installer .NET Framework 4.5 ou ultérieur à partir [d’ici](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Est-il possible de réserver les noms des packages qui doivent être publiés à l’avenir ?

Il n’est pas possible de réserver des noms de packages. Si vous pensez qu’un package existant a pris le nom qui convient mieux à votre package, essayez de [contacter le propriétaire du package](./how-to/working-with-packages/contacting-package-owners.md).
Si vous n’obtenez pas de réponse au bout de quelques semaines, vous pouvez contacter le support technique et l’équipe PowerShell Gallery examinera la question.

## <a name="how-do-i-claim-ownership-for-packages"></a>Comment puis-je revendiquer la propriété de packages ?

Pour plus d’informations, consultez [Gestion des propriétaires de packages sur PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md).

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Comment faire face au propriétaire d’un package qui ne respecte pas la licence de mon package ?

Nous encourageons la communauté PowerShell à collaborer pour résoudre les conflits pouvant survenir entre les propriétaires de tous les packages. Nous avons élaboré une [procédure de résolution des litiges](./how-to/getting-support/dispute-resolution.md) que nous vous demandons de suivre avant toute intervention des administrateurs de PowerShellGallery.com.

<!-- link references-->
[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/PowerShellGet/Update-ModuleManifest
[Install-Module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publish-Module]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
