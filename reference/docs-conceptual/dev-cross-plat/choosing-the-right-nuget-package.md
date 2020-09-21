---
title: Choix du bon package NuGet PowerShell pour votre projet .NET
description: En plus des packages exécutables publiés avec chaque version de PowerShell, l’équipe PowerShell gère plusieurs packages disponibles sur NuGet. Ces packages permettent de cibler PowerShell en tant que plateforme d’API dans .NET.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 39369ed872faa76ad2c41d813da5e0a98cf1c078
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795286"
---
# <a name="choosing-the-right-powershell-nuget-package-for-your-net-project"></a>Choix du bon package NuGet PowerShell pour votre projet .NET

En plus des packages exécutables `pwsh` publiés avec chaque version de PowerShell, l’équipe PowerShell gère plusieurs packages disponibles sur [NuGet][]. Ces packages permettent de cibler PowerShell en tant que plateforme d’API dans .NET.

En tant qu’application .NET qui fournit des API et qui est censée charger des bibliothèques .NET qui implémentent ses propres modules binaires, il est essentiel que PowerShell soit disponible sous la forme d’un package NuGet.

Il existe plusieurs packages NuGet qui fournissent une représentation de la surface d’exposition des API PowerShell. Il n’est pas toujours évident de savoir quel package utiliser avec un projet particulier. Cet article aborde quelques scénarios courants pour les projets .NET ciblant PowerShell et la manière de choisir le package NuGet à cibler pour votre projet .NET orienté PowerShell.

## <a name="hosting-vs-referencing"></a>Hébergement ou référencement

Certains projets .NET cherchent à écrire du code à charger dans un runtime PowerShell préexistant (comme `pwsh`, `powershell.exe`, la console intégrée PowerShell ou ISE), tandis que d’autres souhaitent exécuter PowerShell dans leurs propres applications.

- Le **référencement** correspond à la situation dans laquelle un projet, généralement un module, est destiné à être chargé dans PowerShell.
  Il doit être compilé par rapport aux API que fournit PowerShell pour interagir avec lui, mais l’implémentation de PowerShell est fournie par le processus PowerShell qui le charge. Pour le référencement, un projet peut utiliser des [assemblys de référence][] ou les assemblys de runtime réels en tant que cible de compilation, mais il doit s’assurer de ne publier aucun d’entre eux avec sa build.
- L’**hébergement** correspond à la situation dans laquelle un projet a besoin de sa propre implémentation de PowerShell, généralement parce qu’il s’agit d’une application autonome qui doit exécuter PowerShell. Dans ce cas, les assemblys de référence purs ne peuvent pas être utilisés. Vous devez plutôt faire appel à une implémentation concrète de PowerShell. Une implémentation concrète de PowerShell devant être utilisée, une version spécifique de PowerShell doit être choisie pour l’hébergement ; une application hôte unique ne peut pas cibler plusieurs versions de PowerShell.

### <a name="publishing-projects-that-target-powershell-as-a-reference"></a>Publication de projets ciblant PowerShell en tant que référence

> [!NOTE]
> Nous utilisons le terme **publier** dans cet article pour faire référence à l’exécution de `dotnet publish`, qui place une bibliothèque .NET dans un répertoire avec toutes ses dépendances en vue de son déploiement sur un runtime particulier.

Pour empêcher la publication de dépendances de projet qui sont utilisées uniquement comme cibles de référence de compilation, nous vous recommandons de définir l’[attribut PrivateAssets][] :

```xml
<PackageReference Include="PowerShellStandard.Library" Version="5.1.0.0" PrivateAssets="all" />
```

Si vous oubliez de le faire et que vous utilisez un assembly de référence comme cible, vous risquez de voir des problèmes liés à l’utilisation de l’implémentation par défaut de l’assembly de référence au lieu de l’implémentation réelle. Cela peut prendre la forme d’une `NullReferenceException`, car les assemblys de référence simulent souvent l’API d’implémentation en retournant simplement `null`.

## <a name="key-kinds-of-powershell-targeting-net-projects"></a>Principaux types de projets .NET ciblant PowerShell

Même si une bibliothèque ou une application .NET peut incorporer PowerShell, il existe des scénarios courants qui utilisent les API PowerShell :

- **Implémentation d’un module binaire PowerShell**

  Les modules binaires PowerShell sont des bibliothèques .NET chargées par PowerShell qui doivent implémenter des API PowerShell telles que les types [PSCmdlet][] ou [CmdletProvider][] afin d’exposer les applets de commande ou les fournisseurs, respectivement. Étant donné qu’ils sont chargés, les modules cherchent à se compiler par rapport à des références à PowerShell sans le publier dans leur build. Il est également courant que les modules prennent en charge plusieurs versions et plateformes de PowerShell, idéalement avec un minimum de surcharge d’espace disque, de complexité ou d’implémentation répétée. Pour plus d’informations sur les modules, consultez [À propos des modules][].

- **Implémentation d’un hôte PowerShell**

  Un hôte PowerShell fournit une couche d’interaction pour le runtime PowerShell. Il s’agit d’une forme spécifique d’_hébergement_, où un [PSHost][] est implémenté en tant que nouvelle interface utilisateur pour PowerShell. Par exemple, le ConsoleHost PowerShell fournit une interface utilisateur de terminal pour les exécutables PowerShell, tandis que l’hôte des services de l’éditeur PowerShell et l’hôte ISE fournissent tous deux une interface graphique utilisateur partiellement intégrée à l’éditeur autour de PowerShell. Même s’il est possible de charger un hôte sur un processus PowerShell existant, il est bien plus courant pour une implémentation d’hôte d’agir en tant qu’implémentation PowerShell autonome qui redistribue le moteur PowerShell.

- **Appel de PowerShell à partir d’une autre application .NET**

  Comme pour n’importe quelle application, PowerShell peut être appelé en tant que sous-processus pour exécuter des charges de travail. Toutefois, en tant qu’application .NET, il est également possible d’appeler PowerShell in-process pour obtenir les objets .NET complets à utiliser dans l’application appelante. Il s’agit d’une forme plus générale d’_hébergement_, où l’application contient sa propre implémentation de PowerShell pour une utilisation interne. À titre d’exemple, citons un service ou un démon exécutant PowerShell pour gérer l’état d’une machine ou une application web qui exécute PowerShell à la demande pour effectuer des tâches telles que la gestion des déploiements cloud.

- **Tests unitaires de modules PowerShell à partir de .NET**

  Même si les modules et les autres bibliothèques conçus pour exposer des fonctionnalités à PowerShell doivent être testés à partir de PowerShell (nous vous recommandons [Pester][]), il est parfois nécessaire de soumettre à des tests unitaires les API écrites pour un module PowerShell à partir de .NET. Dans ce cas, le code de module tente de cibler un certain nombre de versions de PowerShell, tandis que les tests doivent l’exécuter sur des implémentations concrètes spécifiques.

## <a name="powershell-nuget-packages-at-a-glance"></a>Packages NuGet PowerShell en un clin d’œil

Dans cet article, nous allons aborder les packages NuGet suivants qui exposent les API PowerShell :

- [PowerShellStandard.Library][] : assembly de référence qui permet de générer un assembly unique pouvant être chargé par plusieurs runtimes PowerShell.
- [Microsoft.PowerShell.SDK][] : permet de cibler et de réhéberger l’ensemble du SDK PowerShell.
- [System.Management.Automation][] : implémentation principale du moteur et du runtime PowerShell, qui peut être utile dans les implémentations hébergées minimales et pour les scénarios de ciblage spécifiques à la version.
- **Assemblys de référence Windows PowerShell** : permettent de cibler et de réhéberger efficacement Windows PowerShell (versions 5.1 et antérieures de PowerShell).

> [!NOTE]
> Le package [NuGet PowerShell][] n’est pas du tout un package de bibliothèques .NET ; il fournit l’implémentation de l’outil global .NET de PowerShell. Il ne doit pas être utilisé par des projets, car il fournit uniquement un exécutable.

## <a name="powershellstandardlibrary"></a>PowerShellStandard.Library

La bibliothèque Standard PowerShell est un assembly de référence qui capture l’intersection des API des versions de PowerShell 7, 6 et 5.1. Elle fournit une surface d’API vérifiée au moment de la compilation vis-à-vis de laquelle effectuer la compilation du code .NET, ce qui permet aux projets .NET de cibler les versions PowerShell 7, 6 et 5.1 sans risquer d’appeler une API absente.

PowerShell Standard est destinée à l’écriture de modules PowerShell ou d’autre code à exécuter uniquement après son chargement dans un processus PowerShell. Étant donné qu’il s’agit d’un assembly de référence, PowerShell Standard ne contient aucune implémentation proprement dite. Elle ne fournit donc aucune fonctionnalité pour les applications autonomes.

### <a name="using-powershell-standard-with-different-net-runtimes"></a>Utilisation de PowerShell Standard avec différents runtimes .NET

PowerShell Standard cible le runtime [.NET Standard 2.0][], runtime de façade conçu pour fournir une surface d’exposition commune partagée par .NET Framework et .NET Core. Cela permet de cibler un seul runtime en vue de produire un assembly unique qui fonctionne avec plusieurs versions de PowerShell, mais les conséquences sont les suivantes :

- Le code PowerShell qui charge le module ou la bibliothèque doit exécuter au minimum .NET 4.6.1 ; .NET 4.6 et .NET 4.5.2 ne prennent pas en charge .NET Standard. Notez qu’une version plus récente de Windows PowerShell ne signifie pas une version plus récente de .NET Framework ; Windows PowerShell 5.1 peut s’exécuter sur .NET 4.5.2.
- Pour utiliser un code PowerShell exécutant .NET Framework 4.7.1 ou une version antérieure, l’implémentation de [NETStandard.Library][] pour .NET 4.6.1 est nécessaire afin de fournir le fichier netstandard.dll et d’autres assemblys shim dans les anciennes versions de .NET Framework.

Les versions 6 et ultérieures de PowerShell fournissent leurs propres assemblys shim pour le transfert de type à partir de .NET Framework 4.6.1 (et versions ultérieures) vers .NET Core. Cela signifie que tant qu’un module utilise uniquement des API qui existent dans .NET Core, les versions 6 et ultérieures de PowerShell peuvent le charger et l’exécuter quand il a été généré pour .NET Framework 4.6.1 (la cible de runtime `net461`).

Ainsi, les modules binaires utilisant PowerShell Standard pour cibler plusieurs versions de PowerShell avec une seule DLL publiée ont deux options :

1. Publication d’un assembly généré pour le runtime cible `net461`. Cela implique les opérations suivantes :
   - Publication du projet pour le runtime `net461`
   - Compilation par rapport au runtime `netstandard2.0` (sans utiliser sa sortie de génération) pour que toutes les API utilisées soient également présentes dans .NET Core.

1. Publication d’un assembly généré pour le runtime cible `netstandard2.0`. Cela implique les opérations suivantes :
   - Publication du projet pour le runtime `netstandard2.0`
   - Prise des dépendances `net461` de NETStandard.Library et copie de ces dernières au point de publication de l’assembly de projet afin que l’assembly soit corrigé avec le transfert de type dans .NET Framework.

Pour générer des modules ou des bibliothèques PowerShell ciblant des versions antérieures de .NET Framework, il peut être préférable de cibler plusieurs runtimes .NET. Cette opération publie un assembly pour chaque runtime cible, et l’assembly approprié doit être chargé au moment du chargement du module (par exemple, avec un petit module psm1 comme module racine).

### <a name="testing-powershell-standard-projects-in-net"></a>Test de projets PowerShell Standard dans .NET

Quand vient l’heure de tester votre module dans des exécuteurs de test .NET comme xUnit, n’oubliez pas que les vérifications au moment de la compilation ne peuvent pas aller plus loin. Vous devez tester votre module sur les plateformes PowerShell appropriées.

Pour tester les API générées par rapport à PowerShell Standard dans .NET, vous devez ajouter `Microsoft.Powershell.SDK` en tant que dépendance de test avec .NET Core (dont la version doit être définie de façon à correspondre à la version de PowerShell souhaitée) et les assemblys de référence Windows PowerShell appropriés avec .NET Framework.

Pour plus d’informations sur PowerShell Standard et son utilisation pour écrire un module binaire qui fonctionne dans plusieurs versions de PowerShell, consultez [ce billet de blog][]. Consultez également le [dépôt PowerShell Standard][] sur GitHub.

## <a name="microsoftpowershellsdk"></a>Microsoft.PowerShell.SDK

`Microsoft.PowerShell.SDK` est un méta-package qui rassemble tous les composants du SDK PowerShell en un package NuGet unique. Une application .NET autonome peut utiliser Microsoft.PowerShell.SDK pour exécuter des fonctionnalités PowerShell arbitraires sans dépendre d’installations ou de bibliothèques PowerShell externes.

> [!NOTE]
> Le SDK PowerShell fait simplement référence à tous les packages de composants qui constituent PowerShell et qui peuvent être utilisés pour le développement .NET avec PowerShell.

Une version de `Microsoft.Powershell.SDK` donnée contient l’implémentation concrète de la même version de l’application PowerShell ; la version 7.0 contient l’implémentation de PowerShell 7.0 et l’exécution de commandes ou de scripts avec elle s’apparente largement à leur exécution dans PowerShell 7.0.

L’exécution de commandes PowerShell à partir du SDK est essentiellement, mais pas totalement, identique à leur exécution à partir de `pwsh`. Par exemple, [Start-Job][], qui dépend de la disponibilité de l’exécutable `pwsh`, ne fonctionne pas avec `Microsoft.Powershell.SDK` par défaut.

Le ciblage de `Microsoft.Powershell.SDK` à partir d’une application .NET vous permet d’effectuer une intégration à tous les assemblys d’implémentation de PowerShell, tels que `System.Management.Automation`, `Microsoft.PowerShell.Management` et d’autres assemblys de module.

La publication d’une application ciblant `Microsoft.Powershell.SDK` inclut tous ces assemblys et toutes les dépendances nécessaires à PowerShell. Elle inclut également d’autres ressources requises par PowerShell dans sa build, telles que les manifestes de module pour les modules `Microsoft.PowerShell.*` et le répertoire `ref` requis par [Add-Type][].

`Microsoft.Powershell.SDK` étant exhaustif, il est idéal pour les opérations suivantes :

- Implémentation d’hôtes PowerShell.
- Exécution de tests xUnit sur les bibliothèques ciblant les assemblys de référence PowerShell.
- Appel de PowerShell in-process à partir d’une application .NET.

`Microsoft.PowerShell.SDK` peut également être utilisé comme cible de référence quand un projet .NET est destiné à être utilisé en tant que module ou bien chargé par PowerShell, mais dépend des API uniquement présentes dans une version particulière de PowerShell. Notez qu’un assembly publié par rapport à une version spécifique de `Microsoft.PowerShell.SDK` ne peut être chargé et utilisé de façon sécurisée que dans cette version de PowerShell. Pour cibler plusieurs versions de PowerShell avec des API spécifiques, plusieurs builds sont nécessaires, chacune ciblant sa propre version de `Microsoft.Powershell.SDK`.

> [!NOTE]
> Le SDK PowerShell n’est disponible que pour les versions 6 et ultérieures de PowerShell. Pour fournir des fonctionnalités équivalentes avec Windows PowerShell, utilisez les assemblys de référence Windows PowerShell décrits ci-dessous.

## <a name="systemmanagementautomation"></a>System.Management.Automation

Le package `System.Management.Automation` est le cœur du SDK PowerShell. Il existe sur NuGet, principalement, en tant que ressource que `Microsoft.Powershell.SDK` peut récupérer. Toutefois, il peut également être utilisé directement comme package pour les scénarios d’hébergement de moindre envergure et les modules de ciblage de version.

Plus précisément, il peut être préférable d’utiliser le package `System.Management.Automation` pour fournir les fonctionnalités PowerShell dans les cas suivants :

- Vous souhaitez uniquement utiliser les fonctionnalités de langage PowerShell (dans l’espace de noms `System.Management.Automation.Language`) comme l’analyseur PowerShell, l’arborescence AST et les API de visiteur de cette arborescence (par exemple, pour l’analyse statique de PowerShell).
- Vous souhaitez uniquement exécuter des commandes spécifiques à partir du module `Microsoft.PowerShell.Core` et pouvez les exécuter dans un état de session créé à l’aide de la méthode de fabrique [CreateDefault2][].

En outre, `System.Management.Automation` est un assembly de référence utile dans les cas suivants :

- Vous souhaitez cibler les API qui sont uniquement présentes dans une version PowerShell spécifique.
- Vous ne dépendez pas de types qui se trouvent en dehors de l’assembly `System.Management.Automation` (par exemple, les types exportés par des applets de commande dans les modules `Microsoft.PowerShell.*`).

## <a name="windows-powershell-reference-assemblies"></a>Assemblys de référence Windows PowerShell

Pour les versions de PowerShell 5.1 et antérieures (Windows PowerShell), il n’existe aucun SDK fournissant une implémentation de PowerShell, puisque l’implémentation de Windows PowerShell fait partie de Windows.

Au lieu de cela, les assemblys de référence Windows PowerShell fournissent des cibles de référence et un moyen de réhéberger Windows PowerShell, agissant de la même façon que le SDK PowerShell pour les versions 6 et ultérieures.

Plutôt que d’être différenciés par version, les assemblys de référence Windows PowerShell ont un package différent pour chaque version de Windows PowerShell :

- [PowerShell 5.1](https://www.nuget.org/packages/Microsoft.PowerShell.5.ReferenceAssemblies/)
- [PowerShell 4](https://www.nuget.org/packages/Microsoft.PowerShell.4.ReferenceAssemblies/)
- [PowerShell 3](https://www.nuget.org/packages/Microsoft.PowerShell.3.ReferenceAssemblies/)

Vous trouverez des informations sur l’utilisation des assemblys de référence Windows PowerShell dans le [SDK Windows PowerShell][].

## <a name="real-world-examples-using-these-nuget-packages"></a>Exemples concrets utilisant ces packages NuGet

Différents projets d’outils PowerShell ciblent différents packages NuGet PowerShell en fonction de leurs besoins. Voici quelques exemples notables.

### <a name="psreadline"></a>PSReadLine

[PSReadLine][], module PowerShell qui fournit une grande partie de l’expérience de console enrichie de PowerShell, cible PowerShell Standard en tant que dépendance plutôt qu’une version de PowerShell spécifique et cible le runtime .NET `net461` dans son [csproj][].

Les versions de PowerShell 6 et ultérieures fournissent leurs propres assemblys shim qui permettent à une DLL ciblant le runtime `net461` de « tout simplement fonctionner » quand elle est chargée (en redirigeant la liaison à la `mscorlib.dll` de .NET Framework vers l’assembly .NET Core approprié).

Cela simplifie considérablement la disposition et la remise des modules de PSReadLine, car PowerShell Standard garantit que seules les API utilisées sont présentes dans PowerShell 5.1, 6 et versions ultérieures, tout en autorisant également le module à être fourni avec un seul assembly.

Toutefois, la cible .NET 4.6.1 signifie que l’exécution de Windows PowerShell sur .NET 4.5.2 et .NET 4.6 n’est pas prise en charge.

### <a name="powershell-editor-services"></a>PowerShell Editor Services

[PowerShell Editor Services][] (PSES) est le back-end de l’[extension PowerShell][] pour [Visual Studio Code][]. En fait, c’est une forme de module PowerShell qui se charge via un exécutable PowerShell et qui prend la main pour réhéberger PowerShell en son sein tout en fournissant des fonctionnalités de protocole de service de langage et d’adaptateur de débogage.

PSES fournit des cibles d’implémentation concrète pour `netcoreapp2.1` afin de cibler les versions de PowerShell 6 et ultérieures (le runtime `netcoreapp3.1` de PowerShell 7 étant à compatibilité descendante) et `net461` afin de cibler Windows PowerShell 5.1, mais la majeure partie de sa logique se trouve dans un deuxième assembly qui cible `netstandard2.0` et PowerShell Standard. Cela lui permet de récupérer les dépendances requises pour les plateformes .NET Core et .NET Framework, tout en simplifiant la plupart du code base derrière une abstraction uniforme.

Étant donné qu’il repose sur PowerShell Standard, PSES nécessite une implémentation de PowerShell au moment de l’exécution pour être testé correctement. Pour ce faire, les tests [xUnit de PSES][] récupèrent `Microsoft.PowerShell.SDK` et `Microsoft.PowerShell.5.ReferenceAssemblies` afin de fournir une implémentation PowerShell dans l’environnement de test.

Comme avec PSReadLine, PSES ne peut pas prendre en charge .NET 4.6 et versions antérieures, mais il [effectue une vérification][] au moment de l’exécution avant d’appeler l’une des API qui pourraient provoquer un plantage sur les runtimes de .NET Framework inférieurs.

### <a name="psscriptanalyzer"></a>PSScriptAnalyzer

[PSScriptAnalyzer][], le linter pour PowerShell, doit cibler des éléments syntaxiques introduits uniquement dans certaines versions de PowerShell. Étant donné que la reconnaissance de ces éléments syntaxiques s’effectue en implémentant un [AstVisitor2][], il n’est pas possible d’utiliser PowerShellStandard et d’implémenter des méthodes de visiteur AST pour des syntaxes PowerShell plus récentes.

Au lieu de cela, PSScriptAnalyzer [cible chaque version de PowerShell][] en tant que configuration de build, et produit une DLL distincte pour chacune d’elles. Cela augmente la taille et la complexité des builds, mais autorise :

- Le ciblage d’API spécifique à la version
- L’implémentation de fonctionnalités spécifiques à la version pratiquement sans coût d’exécution
- La prise en charge totale de Windows PowerShell jusqu’à .NET Framework 4.5.2

## <a name="summary"></a>Résumé

Dans cet article, nous avons listé et abordé les packages NuGet qu’il est possible de cibler lors de l’implémentation d’un projet .NET qui utilise PowerShell ainsi que les raisons qui peuvent vous amener à utiliser tel ou tel.

Si vous êtes directement allé au résumé, voici certaines recommandations générales :

- Les modules **PowerShell** doivent être compilés par rapport à PowerShell Standard s’ils nécessitent uniquement des API communes à différentes versions de PowerShell.
- Les **hôtes et applications** PowerShell qui sont amenés à exécuter PowerShell en interne doivent cibler le SDK PowerShell pour PowerShell versions 6 et ultérieures ou les assemblys de référence Windows PowerShell appropriés pour Windows PowerShell.
- Les modules PowerShell qui nécessitent des **API spécifiques à la version** doivent cibler le SDK PowerShell ou les assemblys de référence de Windows PowerShell pour les versions de PowerShell nécessaires, en les utilisant en tant qu’assemblys de référence (c’est-à-dire en ne publiant pas les dépendances PowerShell).

<!--link references -->

[.NET Standard 2.0]: /dotnet/standard/net-standard
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Add-Type]: /powershell/module/microsoft.powershell.utility/add-type
[AstVisitor2]: /dotnet/api/system.management.automation.language.astvisitor2
[CmdletProvider]: /dotnet/api/system.management.automation.provider.cmdletprovider
[CreateDefault2]: /dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2
[csproj]: https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/PSReadLine.csproj
[Microsoft.PowerShell.SDK]: https://www.nuget.org/packages/Microsoft.PowerShell.SDK/
[NETStandard.Library]: https://www.nuget.org/packages/NETStandard.Library/
[NuGet]: https://www.nuget.org/
[Effectue une vérification]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[Pester]: https://github.com/Pester/Pester
[PowerShell Editor Services]: https://github.com/PowerShell/PowerShellEditorServices/
[Extension PowerShell]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[NuGet PowerShell]: https://www.nuget.org/packages/PowerShell/
[Dépôt PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShellStandard.Library]: https://www.nuget.org/packages/PowerShellStandard.Library/
[PSCmdlet]: /dotnet/api/system.management.automation.pscmdlet
[xUnit de PSES]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSHost]: /dotnet/api/system.management.automation.host.pshost
[Attribut PrivateAssets]: /dotnet/core/tools/csproj#packagereference
[PSReadLine]: https://github.com/PowerShell/PSReadLine
[PSScriptAnalyzer]: https://github.com/powershell/psscriptanalyzer
[Assemblys de référence]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[System.Management.Automation]: https://www.nuget.org/packages/System.Management.Automation/
[Cible chaque version de PowerShell]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[Ce billet de blog]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[Visual Studio Code]: https://code.visualstudio.com/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell
