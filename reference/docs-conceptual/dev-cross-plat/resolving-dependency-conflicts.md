---
title: Résolution des conflits de dépendances d’assembly de module PowerShell
description: Lors de l’écriture d’un module PowerShell binaire en C#, il est naturel de prendre des dépendances envers d’autres packages ou bibliothèques afin de fournir des fonctionnalités.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 536bcfd1ced536faccde0d6c5bc483cdaf31ce68
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87775178"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a>Résolution des conflits de dépendances d’assembly de module PowerShell

Lors de l’écriture d’un module PowerShell binaire en C#, il est naturel de prendre des dépendances envers d’autres packages ou bibliothèques afin de fournir des fonctionnalités. Le recours à des dépendances envers d’autres bibliothèques est souhaitable pour la réutilisation du code. PowerShell charge toujours les assemblys dans le même contexte. Cela pose des problèmes lorsque les dépendances d’un module sont en conflit avec des DLL déjà chargées, et peut empêcher l’utilisation de deux modules autrement non associés dans la même session PowerShell.

Lorsque ce problème se produit, un message d’erreur semblable à celui-ci s’affiche :

![Message d’erreur de conflit de chargement d’assembly](./media/resolving-dependency-conflicts/moduleconflict.png)

Cet article examine pourquoi les conflits de dépendances se produisent dans PowerShell, et présente différentes manières d’atténuer les problèmes de conflit de dépendances. Même si vous n’êtes pas auteur de module, vous trouverez dans cet article quelques astuces qui pourront vous aider en cas de conflit de dépendances dans les modules que vous utilisez.

## <a name="why-do-dependency-conflicts-occur"></a>Pourquoi les conflits de dépendances se produisent-ils ?

Dans .NET, les conflits de dépendances se produisent lorsque deux versions du même assembly sont chargées dans le même _contexte de chargement d’assembly_. Ce terme signifie des choses légèrement différentes sur différentes plateformes .NET ; nous y reviendrons [plus loin](#powershell-and-net). Ce conflit est un problème courant qui se produit dans tout logiciel où des dépendances avec version sont utilisées. Étant donné qu’il n’existe pas de solution simple et que de nombreux frameworks de résolution de dépendance essaient de résoudre le problème de différentes façons, cette situation est souvent appelée « enfer des dépendances ».

Les problèmes de conflits sont accrus par le fait qu’un projet ne dépend presque jamais délibérément ou directement de deux versions de la même dépendance. Au lieu de cela, le projet a deux dépendances (ou plus) qui nécessitent chacune une version différente de la même dépendance.

Par exemple, imaginez que votre application .NET, `DuckBuilder`, intègre deux dépendances afin d’exécuter des parties de ses fonctionnalités et ressemble à ceci :

![Deux dépendances de DuckBuilder reposent sur des versions différentes de Newtonsoft.Json](./media/resolving-dependency-conflicts/dep-conflict.jpg)

`Contoso.ZipTools` et `Fabrikam.FileHelpers` dépendant tous deux de différentes versions de `Newtonsoft.Json`, il peut y avoir un conflit de dépendances en fonction de la façon dont chaque dépendance est chargée.

### <a name="conflicting-with-powershells-dependencies"></a>Conflits avec les dépendances de PowerShell

Dans PowerShell, le problème de conflit de dépendances est accru car les modules PowerShell et les dépendances propres à PowerShell sont chargés dans le même contexte partagé. Cela signifie que le moteur PowerShell et tous les modules PowerShell chargés ne doivent pas avoir de dépendances en conflit. `Newtonsoft.Json` offre un exemple classique :

![Le module FictionalTools dépend d’une version plus récente de Newtonsoft.Json que PowerShell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

Dans cet exemple, le module `FictionalTools` dépend de la version `12.0.3` de `Newtonsoft.Json`, qui est une version plus récente de `Newtonsoft.Json` que la version `11.0.2` fournie dans l’exemple PowerShell.

> [!NOTE]
> Il s’agit uniquement d’un exemple ; PowerShell 7 est actuellement fourni avec `Newtonsoft.Json 12.0.3`.

Étant donné que le module dépend d’une version plus récente de l’assembly, il n’acceptera pas la version que PowerShell a déjà chargée. Toutefois, comme PowerShell a déjà chargé une version de l’assembly, le module ne peut pas charger sa propre version à l’aide du mécanisme de chargement conventionnel.

### <a name="conflicting-with-another-modules-dependencies"></a>Conflits avec les dépendances d’un autre module

Un autre scénario courant dans PowerShell est le chargement d’un module qui dépend d’une version d’un assembly, puis le chargement d’un autre module qui dépend d’une version différente de cet assembly.

Cela ressemble souvent à ceci :

![Deux modules PowerShell nécessitent des versions différentes de la dépendance Microsoft.Extensions.Logging](./media/resolving-dependency-conflicts/mod-conflict.jpg)

Dans ce cas, le module `FictionalTools` nécessite une version plus récente de `Microsoft.Extensions.Logging` que le module `FilesystemManager`.

Imaginez que ces modules chargent leurs dépendances en plaçant les assemblys de dépendances dans le même répertoire que l’assembly de module racine. Cela permet à .NET de les charger implicitement par nom. Si nous exécutons PowerShell 7 (sur .NET Core 3.1), nous pouvons charger et exécuter `FictionalTools`, puis charger et exécuter `FilesystemManager` sans problème. Toutefois, dans une nouvelle session, si nous chargeons et exécutons `FilesystemManager`, puis chargeons `FictionalTools`, nous recevons une `FileLoadException` à partir de la commande `FictionalTools`, car elle nécessite une version plus récente de `Microsoft.Extensions.Logging` que celle qui est chargée.
`FictionalTools` ne peut pas charger la version requise, car un assembly du même nom a déjà été chargé.

## <a name="powershell-and-net"></a>PowerShell et .NET

PowerShell s’exécute sur la plateforme .NET. .NET est en définitive responsable de la résolution et du chargement des dépendances d’assemblys. Nous devons donc comprendre comment .NET opère ici afin de comprendre les conflits de dépendances.

Nous devons également gérer le fait que différentes versions de PowerShell s’exécutent sur différentes implémentations de .NET. En général, PowerShell 5.1 et versions antérieures s’exécutent sur le .NET Framework, tandis que PowerShell 6 et versions ultérieures s’exécutent sur .NET Core. Ces deux implémentations de .NET chargent et gèrent les assemblys différemment.
Cela signifie que la résolution des conflits de dépendances peut varier en fonction de la plateforme .NET sous-jacente.

### <a name="assembly-load-contexts"></a>Contextes de chargement d’assembly

Dans .NET, un _contexte de chargement d’assembly_ (ALC, Assembly Load Context) est un espace de noms de runtime dans lequel des assemblys sont chargés. Les noms des assemblys doivent être uniques. Ce concept permet aux assemblys d’être résolus de manière unique par nom dans chaque ALC.

### <a name="assembly-reference-loading-in-net"></a>Chargement des références d’assembly dans .NET

La sémantique du chargement d’assembly dépend à la fois de l’implémentation .NET (.NET Core ou .NET Framework) et de l’API .NET utilisée pour charger un assembly particulier. Plutôt que d’entrer ici dans les détails, nous vous invitons à consulter les liens fournis dans la section [Lectures supplémentaires](#further-reading), qui expliquent en détail le fonctionnement du chargement d’assembly .NET dans chaque implémentation .NET.

Dans cet article, nous allons faire référence aux mécanismes suivants :

- Chargement d’assembly implicite (`Assembly.Load(AssemblyName)`), lorsque .NET essaie de charger un assembly par nom à partir d’une référence d’assembly statique dans du code .NET
- `Assembly.LoadFrom()`, une API de chargement orientée plug-in qui ajoute des gestionnaires pour résoudre les dépendances de la DLL chargée. Cette méthode est susceptible de ne pas résoudre les dépendances comme nous le souhaitons
- `Assembly.LoadFile()`, une API de chargement de base censée charger uniquement l’assembly demandé, et qui ne gère pas de dépendances

### <a name="differences-in-net-framework-vs-net-core"></a>Différences entre le .NET Framework et .NET Core

Le fonctionnement de ces API a changé de manière subtile entre .NET Core et le .NET Framework. Il est donc utile de consulter les [liens](#further-reading) proposés. Il convient surtout de remarquer que les contextes de chargement d’assembly et d’autres mécanismes de résolution d’assembly ont changé entre le .NET Framework et .NET Core.

En particulier, le .NET Framework dispose des fonctionnalités suivantes :

- Le Global Assembly Cache, pour la résolution d’assembly à l’échelle de la machine
- Des domaines d’application, qui opèrent comme des bacs à sable en mode in-process pour l’isolation d’assembly, mais présentent également une couche de sérialisation à gérer
- Un modèle de contexte de chargement d’assembly limité, expliqué en détail [ici](/dotnet/framework/deployment/best-practices-for-assembly-loading), qui a un ensemble fixe de contextes de chargement d’assembly, chacun avec son propre comportement :
  - Le contexte de chargement par défaut, où les assemblys sont chargés par défaut
  - Le contexte de chargement source, pour le chargement manuel des assemblys au moment de l’exécution
  - Le contexte de réflexion uniquement, pour le chargement sécurisé d’assemblys afin de lire leurs métadonnées sans les exécuter
  - Le mystérieux vide dans lequel résident les assemblys chargés avec `Assembly.LoadFile(string path)` et `Assembly.Load(byte[] asmBytes)`

.NET Core (et .NET 5+) a remplacé cette complexité par un modèle plus simple :

- Aucun Global Assembly Cache. Les applications apportent toutes leurs propres dépendances. Cela supprime un facteur externe pour la résolution des dépendances dans les applications, ce qui rend la résolution des dépendances plus reproductible.
  PowerShell, en tant qu’hôte de plug-in, complique légèrement cela pour les modules. Ses dépendances dans `$PSHOME` sont partagées avec tous les modules
- Un seul domaine d’application et aucune possibilité d’en créer de nouveaux. Le concept Domaine d’application est conservé dans .NET Core uniquement pour être l’état global du processus .NET
- Un nouveau modèle de contexte de chargement d’assembly extensible. La résolution d’assembly peut être limitée à un espace de noms en la plaçant dans un nouvel ALC. Les processus .NET Core commencent par un ALC unique par défaut dans lequel tous les assemblys sont chargés (à l’exception de ceux chargés avec `Assembly.LoadFile(string)` et `Assembly.Load(byte[])`), mais le processus peut créer et définir ses propres ALC personnalisés avec sa propre logique de chargement. Lorsqu’un assembly est chargé, le premier ALC dans lequel il est chargé est responsable de la résolution de ses dépendances. Cela permet d’implémenter de puissants mécanismes de chargement de plug-ins .NET

Dans les deux implémentations, les assemblys sont chargés tardivement. Cela signifie qu’ils sont chargés lorsqu’une méthode nécessitant leur type est exécutée pour la première fois.

Voici par exemple deux versions du même code qui chargent une dépendance à différents moments.

La première charge toujours sa dépendance lorsque `Program.GetRange()` est appelée, car la référence de dépendance est présente lexicalement dans la méthode :

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

La seconde charge sa dépendance uniquement si le paramètre `limit` est supérieur ou égal à 20, en raison de l’indirection interne via une méthode :

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

Il s’agit d’une bonne pratique, car elle réduit la mémoire et les E/S de système de fichiers, et utilise plus efficacement les ressources. Malheureusement, l’un des effets secondaires est que nous ne savons pas que le chargement de l’assembly a échoué tant que nous n’avons pas atteint le chemin du code qui tente de charger l’assembly.

Cela peut également créer une condition de minutage pour les conflits de chargement d’assembly. Si deux parties du même programme tentent de charger différentes versions du même assembly, la version chargée dépend du chemin du code exécuté en premier.

Pour PowerShell, cela signifie que les facteurs suivants peuvent affecter un conflit de chargement d’assembly :

- Quel a été le module chargé en premier ?
- Le chemin du code qui utilise la bibliothèque de dépendances a-t-il été exécuté ?
- PowerShell charge-t-il une dépendance en conflit au démarrage ou uniquement sous certains chemins du code ?

## <a name="quick-fixes-and-their-limitations"></a>Correctifs rapides et limitations

Dans certains cas, il est possible d’effectuer de petits ajustements sur votre module et de résoudre les problèmes avec un minimum d’effort. Toutefois, ces solutions ont tendance à présenter des inconvénients. Même si elles peuvent s’appliquer à votre module, elles ne fonctionneront pas pour chaque module.

### <a name="change-your-dependency-version"></a>Changer votre version de dépendance

Le moyen le plus simple d’éviter les conflits de dépendance consiste à s’accorder sur une dépendance. Cela peut être possible dans les cas suivants :

- Votre conflit concerne une dépendance directe de votre module et vous contrôlez la version
- Votre conflit concerne une dépendance indirecte, mais vous pouvez configurer vos dépendances directes de façon à utiliser une version de dépendance indirecte exploitable
- Vous connaissez la version en conflit et vous pouvez vous fier à ce qu’elle ne change pas

Le package `Newtonsoft.Json` est un bon exemple de ce dernier scénario. Il s’agit d’une dépendance de PowerShell 6 et versions ultérieures, et il n’est pas utilisé dans Windows PowerShell. Cela signifie qu’un moyen simple de résoudre les conflits de gestion de versions consiste à cibler la version la plus basse de `Newtonsoft.Json` sur les versions de PowerShell que vous souhaitez cibler.

Par exemple, PowerShell 6.2.6 et PowerShell 7.0.2 utilisent actuellement `Newtonsoft.Json` version 12.0.3. Ainsi, pour créer un module ciblant Windows PowerShell, PowerShell 6 et PowerShell 7, vous devez cibler `Newtonsoft.Json 12.0.3` en tant que dépendance et l’inclure dans votre module intégré. Quand le module est chargé dans PowerShell 6 ou 7, le propre assembly `Newtonsoft.Json` de PowerShell est déjà chargé. En outre, puisqu’il s’agit au moins de la version requise pour votre module, la résolution réussit. Dans Windows PowerShell, l’assembly n’est pas encore présent dans PowerShell. Il est donc chargé à partir de votre dossier de module.

En général, lorsque vous ciblez un package PowerShell concret, comme `Microsoft.PowerShell.Sdk` ou `System.Management.Automation`, NuGet doit être en mesure de résoudre les bonnes versions de dépendance requises. Cibler à la fois Windows PowerShell et PowerShell 6+ devient plus difficile, car vous devez choisir entre le ciblage de plusieurs frameworks ou de `PowerShellStandard.Library`.

Voici quelques cas où l’épinglage sur une version de dépendance commune ne fonctionnera pas :

- Le conflit concerne une dépendance indirecte, et aucune de vos dépendances ne peut être configurée pour utiliser une version commune
- L’autre version de dépendance est susceptible de changer souvent. Par conséquent, le fait de se fixer sur une version commune n’est qu’un correctif à court terme

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a>Ajouter un gestionnaire d’événements AssemblyResolve pour créer une redirection de liaison dynamique

Parfois, la modification de votre propre version de dépendance n’est pas possible ou est trop difficile. Une autre option consiste à configurer une redirection de liaison dynamique en inscrivant un gestionnaire d’événements pour l’événement `AssemblyResolve`.

Comme avec une redirection de liaison statique, l’objectif est de forcer tous les consommateurs d’une dépendance à utiliser le même assembly. Vous interceptez les appels de chargement de la dépendance et les redirigez toujours vers la version souhaitée.

Cela ressemble un peu à ce qui suit :

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

Techniquement, vous pouvez inscrire un scriptblock dans PowerShell afin de gérer un événement `AssemblyResolve`, mais :

- Un événement `AssemblyResolve` peut être déclenché sur n’importe quel thread, ce que PowerShell ne pourra pas gérer
- Même lorsque les événements sont gérés sur le bon thread, les concepts de portée de PowerShell signifient que le scriptblck du gestionnaire d’événements doit être écrit avec soin afin de ne pas dépendre de variables définies en dehors.

Il existe des situations où la redirection vers une version commune ne fonctionnera pas :

- Lorsque la dépendance a apporté des changements cassants entre les versions, ou lorsque le code dépendant s’appuie sur une fonctionnalité non disponible dans la version vers laquelle vous redirigez
- Lorsque votre module n’est pas chargé avant la dépendance en conflit. Si vous inscrivez un gestionnaire d’événements `AssemblyResolve` après le chargement de la dépendance, il ne sera jamais déclenché. Si vous essayez d’éviter les conflits de dépendances avec un autre module, cela peut poser un problème, étant donné que l’autre module peut être chargé en premier

### <a name="use-the-dependency-out-of-process"></a>Utiliser la dépendance hors processus

Cette solution concerne davantage les utilisateurs de module que les auteurs de module. Elle convient lorsque vous êtes confronté à un module qui ne fonctionne pas en raison d’un conflit de dépendance existant.

Les conflits de dépendances se produisent car deux versions du même assembly sont chargées dans le même processus .NET. Une solution simple consiste à les charger dans des processus différents, à condition que vous puissiez toujours utiliser les fonctionnalités des deux processus ensemble.

Dans PowerShell, il existe plusieurs façons d’y parvenir :

- Appeler PowerShell en tant que sous-processus

  Un moyen simple d’exécuter une commande PowerShell en dehors du processus actuel consiste à démarrer un nouveau processus PowerShell directement avec l’appel de commande :

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  La limitation principale ici est que la restructuration du résultat peut être plus délicate ou plus sujette aux erreurs que d’autres options.

- Système de travail PowerShell

  Le système de travail PowerShell exécute également des commandes hors processus, en envoyant des commandes à un nouveau processus PowerShell et en retournant les résultats :

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  Dans ce cas, vous devez simplement vous assurer que les variables et l’état sont transmis correctement.

  Le système de travail peut également être un peu lourd quand vous exécutez des commandes de petite taille.

- Communication à distance PowerShell

  Lorsqu’elle est disponible, la communication à distance PowerShell peut être un moyen pratique d’exécuter des commandes hors processus. Avec elle, vous pouvez créer une nouvelle **PSSession** dans un nouveau processus, appeler ses commandes via la communication à distance PowerShell, puis utiliser les résultats localement avec les autres modules contenant les dépendances en conflit.

  Voici un exemple :

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- Communication à distance implicite vers Windows PowerShell

  Dans PowerShell 7, une autre option consiste à utiliser l’indicateur `-UseWindowsPowerShell` sur `Import-Module`. Cela permet d’importer le module par le biais d’une session de communication à distance locale dans Windows PowerShell :

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  Sachez toutefois que les modules peuvent ne pas fonctionner avec Windows PowerShell ou fonctionner différemment.

#### <a name="when-out-of-process-invocation-should-not-be-used"></a>Quand ne faut-il pas utiliser l’appel hors processus ?

En tant qu’auteur de module, l’appel de commande hors processus est difficile à intégrer dans un module et peut présenter des cas litigieux susceptibles de provoquer des problèmes. En particulier, la communication à distance et les travaux peuvent ne pas être disponibles dans tous les environnements où votre module doit fonctionner. Toutefois, le principe général consistant à déplacer l’implémentation hors processus et à permettre au module PowerShell d’être un client allégé peut toujours s’appliquer.

En tant qu’utilisateur de module, il existe des cas où l’appel hors processus ne fonctionnera pas :

- Lorsque la communication à distance PowerShell n’est pas disponible car vous n’avez pas les privilèges nécessaires pour l’utiliser ou elle n’est pas activée
- Lorsqu’un type .NET particulier doit être généré en tant qu’entrée d’une méthode ou d’une autre commande.
  Les commandes qui s’exécutent via la communication à distance PowerShell émettent des objets désérialisés plutôt que des objets .NET fortement typés. Cela signifie que les appels de méthode et les API fortement typées ne fonctionnent pas avec la sortie des commandes importées via la communication à distance

## <a name="more-robust-solutions"></a>Solutions plus robustes

Avec toutes les solutions précédentes, certains scénarios et modules ne fonctionnent pas. Elles ont toutefois l’avantage d’être relativement simples à implémenter correctement. Les solutions suivantes sont plus robustes, mais leur implémentation correcte nécessite davantage d’efforts et elles peuvent introduire des bogues subtils si elles ne sont pas écrites avec précaution.

### <a name="loading-through-net-core-assembly-load-contexts"></a>Chargement par le biais de contextes de chargement d’assembly .NET Core

Les [contextes de chargement d’assembly](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALC) en tant qu’API implémentable ont été introduits dans .NET Core 1.0 afin de répondre spécifiquement à la nécessité de charger plusieurs versions du même assembly dans le même runtime.

Dans .NET Core et .NET 5, ils offrent la solution la plus fiable au problème de chargement des versions conflictuelles d’un assembly. Toutefois, les ALC personnalisés ne sont pas disponibles dans le .NET Framework. Cela signifie que cette solution fonctionne uniquement dans PowerShell 6 et versions ultérieures.

Actuellement, le meilleur exemple d’utilisation d’un ALC pour l’isolation des dépendances dans PowerShell se trouve dans PowerShell Editor Services, le serveur de langage pour l’extension PowerShell pour Visual Studio Code. Un [ALC est utilisé](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) pour empêcher que les propres dépendances de PowerShell Editor Services entrent en conflit avec celles des modules PowerShell.

L’implémentation de l’isolation des dépendances de module avec un ALC est conceptuellement difficile, mais nous allons examiner un exemple minimal. Imaginez que nous avons un module simple destiné uniquement à fonctionner dans PowerShell 7.
Le code source est organisé comme suit :

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

L’implémentation de l’applet de commande ressemble à ceci :

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

Le manifeste (très simplifié) ressemble à ceci :

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

Et le `csproj` ressemble à ceci :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

Lorsque nous générons ce module, la sortie générée présente la disposition suivante :

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

Dans cet exemple, notre problème se trouve dans l’assembly `Shared.Dependency.dll`, qui est notre dépendance en conflit imaginaire. Il s’agit de la dépendance que nous devons placer derrière un ALC afin de pouvoir utiliser la version propre au module.

Nous devons remanier le module afin que :

- Les dépendances de module soient uniquement chargées dans notre ALC personnalisé, et non dans l’ALC de PowerShell, afin qu’il ne puisse y avoir aucun conflit. De plus, à mesure que nous ajoutons des dépendances à notre projet, nous ne souhaitons pas ajouter continuellement du code pour que le chargement continue à fonctionner. Au lieu de cela, nous souhaitons avoir une logique de résolution de dépendance générique et réutilisable.
- Le chargement du module fonctionne toujours normalement dans PowerShell. Les applets de commande et autres types requis par le système de module PowerShell sont définis dans le propre ALC de PowerShell.

Pour répondre à ces deux exigences, nous devons diviser notre module en deux assemblys :

- Un assembly d’applet de commande, `AlcModule.Cmdlets.dll`, qui contient les définitions de tous les types dont le système de module de PowerShell a besoin pour charger correctement notre module. À savoir, toutes les implémentations de la classe de base `Cmdlet` et la classe qui implémente `IModuleAssemblyInitializer`, qui configure le gestionnaire d’événements pour `AssemblyLoadContext.Default.Resolving` afin de charger correctement `AlcModule.Engine.dll` par le biais de notre ALC personnalisé. Comme PowerShell 7 masque délibérément les types définis dans les assemblys chargés dans d’autres ALC, tous les types qui sont censés être exposés publiquement à PowerShell doivent également être définis ici. Pour finir, notre définition d’ALC personnalisée doit être définie dans cet assembly. À part cela, le moins de code possible doit résider dans cet assembly.
- Un assembly de moteur, `AlcModule.Engine.dll`, qui gère l’implémentation réelle du module.
  Ses types sont disponibles dans l’ALC PowerShell, mais il sera initialement chargé par le biais de notre ALC personnalisé. Ses dépendances sont chargées uniquement dans l’ALC personnalisé. Il assume en fait le rôle de _pont_ entre les deux ALC.

Avec ce concept de pont, notre nouvelle disposition d’assembly ressemble à ceci :

![Diagramme représentant AlcModule.Engine.dll assumant le rôle de pont entre les deux ALC](./media/resolving-dependency-conflicts/alc-diagram.jpg)

Pour nous assurer que la logique de sondage de dépendance de l’ALC par défaut ne résout pas les dépendances pour un chargement dans l’ALC personnalisé, nous devons séparer ces deux parties du module dans des répertoires différents. La nouvelle disposition de module présente la structure suivante :

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

Pour voir comment l’implémentation change, nous allons commencer par l’implémentation de `AlcModule.Engine.dll` :

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

Il s’agit d’un conteneur simple pour la dépendance, `Shared.Dependency.dll`, mais vous devez le considérer comme l’API .NET pour votre fonctionnalité que les applets de commande dans l’autre assembly encapsulent pour PowerShell.

L’applet de commande dans `AlcModule.Cmdlets.dll` se présente comme suit :

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

À ce stade, si nous chargeons **AlcModule** et exécutons `Test-AlcModule`, nous obtenons une `FileNotFoundException` lorsque l’ALC par défaut tente de charger `Alc.Engine.dll` pour exécuter `EndProcessing()`. C’est bien, car cela signifie que l’ALC par défaut ne peut pas trouver les dépendances que nous souhaitons masquer.

À présent, nous devons ajouter du code à `AlcModule.Cmdlets.dll` afin qu’elle sache comment résoudre `AlcModule.Engine.dll`. Tout d’abord, nous devons définir notre ALC personnalisé qui résoudra les assemblys à partir du répertoire `Dependencies` de notre module :

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _depdendencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                s_dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

Nous devons ensuite associer notre ALC personnalisé à l’événement `Resolving` de l’ALC par défaut, qui est la version d’ALC de l’événement `AssemblyResolve` sur les domaines d’application. Cet événement est déclenché pour rechercher `AlcModule.Engine.dll` lorsque `EndProcessing()` est appelée.

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

Avec la nouvelle implémentation, examinez la séquence d’appels qui se produit lorsque le module est chargé et que `Test-AlcModule` est exécutée :

![Diagramme de séquence des appels avec utilisation de l’ALC personnalisé pour charger les dépendances](./media/resolving-dependency-conflicts/alc-sequence.png)

Voici quelques points intéressants :

- L’`IModuleAssemblyInitializer` est exécuté en premier lorsque le module est chargé et définit l’événement `Resolving`.
- Nous ne chargeons les dépendances que lorsque `Test-AlcModule` est exécuté et que sa méthode `EndProcessing()` est appelée.
- Lorsque `EndProcessing()` est appelée, l’ALC par défaut ne parvient pas à trouver `AlcModule.Engine.dll` et il déclenche l’événement `Resolving`.
- Notre gestionnaire d’événements raccorde l’ALC personnalisé à l’ALC par défaut, et charge uniquement `AlcModule.Engine.dll`.
- Lorsque `AlcEngine.Use()` est appelée dans `AlcModule.Engine.dll`, l’ALC personnalisé intervient afin de résoudre `Shared.Dependency.dll`. Plus précisément, il charge toujours _notre_ `Shared.Dependency.dll`, car il n’entre jamais en conflit avec quoi que ce soit dans l’ALC par défaut et ne recherche que dans notre répertoire `Dependencies`.

En assemblant l’implémentation, la nouvelle disposition du code source ressemble à ceci :

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

AlcModule.Cmdlets.csproj ressemble à ceci :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

AlcModule.Engine.csproj ressemble à ceci :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

Ainsi, lorsque nous créons le module, notre stratégie est la suivante :

- Générer `AlcModule.Engine`
- Générer `AlcModule.Cmdlets`
- Copier tout le contenu de `AlcModule.Engine` dans le répertoire `Dependencies` et nous souvenir de ce que nous avons copié
- Copier tout le contenu de `AlcModule.Cmdlets` qui n’était pas dans `AlcModule.Engine` dans le répertoire du module de base

La disposition du module étant ici si cruciale pour la séparation des dépendances, voici un script de génération à utiliser à partir de la racine source :

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

Nous disposons finalement d’une approche générale d’utilisation d’un contexte de chargement d’assembly pour isoler les dépendances de notre module qui reste robuste avec le temps, à mesure que d’autres dépendances sont ajoutées.

Pour obtenir un exemple plus détaillé, accédez à ce [dépôt GitHub](https://github.com/rjmholt/ModuleDependencyIsolationExample). Cet exemple montre comment migrer un module afin qu’il utilise un ALC, tout en veillant à ce qu’il reste opérationnel dans le .NET Framework. Il montre également comment utiliser .NET Standard et PowerShell standard pour simplifier l’implémentation de base.

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a>Gestionnaire de résolution d’assembly pour le chargement côte à côte avec `Assembly.LoadFile()`

Une autre méthode, peut-être plus simple, pour accomplir le chargement d’assembly côte à côte consiste à raccorder un événement `AssemblyResolve` à `Assembly.LoadFile()`. L’utilisation de `Assembly.LoadFile()` présente l’avantage d’être la solution la plus simple à implémenter, et de fonctionner avec .NET Core et le .NET Framework.

Pour illustrer cela, jetons un coup d’œil à un exemple d’implémentation qui combine des idées de notre exemple de redirection de liaison dynamique et l’exemple de contexte de chargement d’assembly ci-dessus.

Ce module, que nous appellerons **LoadFileModule**, a une commande triviale `Test-LoadFile [-Path] <path>`. Il prend une dépendance envers l’assembly `CsvHelper` (version 15.0.5).

Comme avec le module ALC, nous devons tout d’abord fractionner le module en deux parties.

La première partie effectue l’implémentation réelle, `LoadFileModule.Engine` :

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

La deuxième partie est ce que PowerShell charge directement, `LoadFileModule.Cmdlets`. Nous adoptons une stratégie similaire à celle du module ALC, où nous isolons les dépendances dans un répertoire distinct, mais cette fois-ci nous chargeons tous les assemblys avec un événement de résolution plutôt que simplement `LoadFileModule.Engine.dll`.

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

Pour finir, la disposition du module est également similaire au module ALC :

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

Une fois cette structure en place, **LoadFileModule** prend désormais en charge le chargement aux côtés d’autres modules avec une dépendance envers **CsvHelper**.

Étant donné que notre gestionnaire s’applique à **tous** les événements `AssemblyResolve` du domaine d’application, nous devons effectuer ici des choix de conception spécifiques :

- Pour réduire la fenêtre pendant laquelle notre événement peut interférer avec un autre chargement, nous ne commençons à gérer le chargement des dépendances générales qu’après le chargement de `LoadFileModule.Engine.dll`.
- Nous envoyons `LoadFileModule.Engine.dll` dans le répertoire Dependencies, afin qu’il soit chargé par un appel à `LoadFile()` plutôt que par PowerShell. Cela signifie que ses propres chargements de dépendances déclenchent toujours un événement `AssemblyResolve`, même si un autre `CsvHelper.dll` (par exemple) est chargé dans PowerShell.
  Cela nous donne l’opportunité de trouver la dépendance correcte.
- Comme nous devons uniquement résoudre les dépendances propres à notre module, nous sommes obligés de coder un dictionnaire de noms et de versions de dépendances dans notre gestionnaire. Dans notre cas particulier, il serait possible d’utiliser la propriété `ResolveEventArgs.RequestingAssembly` pour déterminer si `CsvHelper` est demandé par notre module. Mais cela ne fonctionne pas pour les dépendances de dépendances, par exemple si `CsvHelper` lui-même a déclenché un événement `AssemblyResolve`. Il existe d’autres méthodes plus compliquées pour effectuer cette opération, telles que la comparaison des assemblys demandés aux métadonnées des assemblys dans le répertoire `Dependencies`. Toutefois, dans cet exemple nous avons rendu cette vérification plus explicite afin de mettre en évidence le problème et de simplifier l’exemple.

Il s’agit de la principale différence entre la stratégie `LoadFile()` et la stratégie ALC : l’événement `AssemblyResolve` doit traiter toutes les charges dans le domaine d’application, et il est par conséquent beaucoup plus difficile d’éviter que notre résolution des dépendances ne s’entremêle avec d’autres modules. Toutefois, l’absence d’ALC dans le .NET Framework rend cette option intéressante.

### <a name="custom-application-domains"></a>Domaines d’application personnalisés

La dernière option (et la plus extrême) pour l’isolation d’assembly consiste à utiliser des domaines d’application personnalisés.
Les domaines d’application (utilisés au pluriel) sont uniquement disponibles dans le .NET Framework. Ils servent à fournir une isolation in-process entre les parties d’une application .NET. L’une des utilisations consiste à isoler les charges d’assembly les unes des autres au sein du même processus.

Toutefois, les domaines d’application sont des limites de sérialisation. Les objets d’un domaine d’application ne peuvent pas être référencés et utilisés directement par les objets d’un autre domaine d’application. Vous pouvez contourner ce problème en implémentant `MarshalByRefObject`. Toutefois, lorsque vous ne contrôlez pas les types, comme c’est souvent le cas avec les dépendances, il n’est pas possible de forcer une implémentation ici. La seule solution consiste à apporter des modifications architecturales importantes. La limite de sérialisation a également de sérieuses implications en matière de performances.

Étant donné que les domaines d’application présentent cette limitation sérieuse, sont compliqués à implémenter et ne fonctionnent que dans le .NET Framework, nous ne fournirons aucun exemple de la façon dont vous pouvez les utiliser ici. Bien qu’ils méritent d’être mentionnés en tant que possibilité, leur utilisation n’est pas recommandée.

Si vous souhaitez essayer d’utiliser un domaine d’application personnalisé, les liens suivants peuvent vous aider :

- [Documentation conceptuelle sur les domaines d’application](/dotnet/framework/app-domains/application-domains)
- [Exemples d’utilisation de domaines d’application](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a>Solutions aux conflits de dépendances qui ne fonctionnent pas pour PowerShell

Pour finir, nous allons aborder certaines possibilités qui peuvent sembler prometteuses lors de l’examen des conflits de dépendances .NET dans .NET, mais qui ne fonctionnent généralement pas pour PowerShell.

Ces solutions ont comme thème commun le fait qu’il s’agit de modifications apportées aux configurations de déploiement pour un environnement dans lequel vous contrôlez l’application et éventuellement toute la machine. Elles sont orientées vers des scénarios tels que des serveurs web et d’autres applications déployées dans des environnements de serveur, où l’environnement est destiné à héberger l’application et peut être configuré par l’utilisateur du déploiement. Elles ont également tendance à être très orientées vers le .NET Framework, ce qui signifie qu’elles ne fonctionnent pas avec PowerShell 6 ou version ultérieure.

Si vous savez que votre module est utilisé uniquement dans des environnements Windows PowerShell 5.1 que vous contrôlez entièrement, certaines d’entre elles peuvent être des options envisageables. Toutefois, en règle générale, **les modules ne doivent pas modifier l’état global de la machine comme ceci**. Cela peut rompre des configurations qui provoquent des problèmes dans `powershell.exe`, d’autres modules ou d’autres applications dépendantes qui entraînent l’échec inattendu de votre module.

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a>Redirection de liaison statique avec app.config pour forcer l’utilisation de la même version de dépendance

Les applications .NET Framework peuvent tirer parti d’un fichier `app.config` pour configurer de façon déclarative certains comportements de l’application. Il est possible d’écrire une entrée `app.config` qui configure la liaison d’assembly de façon à rediriger le chargement d’assembly vers une version particulière.

Avec PowerShell, cela pose deux problèmes :

- .NET Core ne prend pas en charge `app.config`. Par conséquent, cette solution s’applique uniquement à `powershell.exe`
- `powershell.exe` est une application partagée qui réside dans le répertoire `System32` Il est probable que votre module ne pourra pas modifier son contenu sur de nombreux systèmes. Même s’il le peut, la modification du fichier `app.config` risque d’invalider une configuration existante ou d’affecter le chargement d’autres modules

### <a name="setting-codebase-with-appconfig"></a>Définition de `codebase` avec app.config

Pour les mêmes raisons, la configuration du paramètre `codebase` dans `app.config` échouera dans les modules PowerShell.

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a>Installation de dépendances dans le Global Assembly Cache (GAC)

Une autre façon de résoudre les conflits de version de dépendance dans le .NET Framework consiste à installer les dépendances dans le GAC, afin que différentes versions puissent être chargées côte à côte à partir du GAC.

Là encore, pour les modules PowerShell, les principaux problèmes sont les suivants :

- Puisque le GAC s’applique uniquement au .NET Framework, cela n’est d’aucune aide dans PowerShell 6 et versions ultérieures.
- L’installation d’assemblys dans le GAC est une modification de l’état global de la machine susceptible d’avoir des effets secondaires dans d’autres applications ou modules. Elle peut également être difficile à accomplir correctement, même si votre module dispose des privilèges d’accès requis. Toute erreur peut provoquer des problèmes sérieux à l’échelle de la machine dans d’autres applications .NET.

## <a name="further-reading"></a>Informations supplémentaires

Il existe de nombreux articles qui traitent des conflits de dépendances de version d’assembly .NET. En voici une sélection :

- [.NET : Assemblys dans .NET](/dotnet/standard/assembly/)
- [.NET Core : Algorithme de chargement d’assembly managé](/dotnet/core/dependency-loading/loading-managed)
- [.NET Core : Comprendre System.Runtime.Loader.AssemblyLoadContext](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [.NET Core : Discussion relative aux solutions de chargement d’assemblys côte à côte](https://github.com/dotnet/runtime/issues/13471)
- [.NET Framework : Redirection des versions d’assemblys](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [.NET Framework : Bonnes pratiques pour le chargement d’assembly](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [.NET Framework : Méthode de localisation des assemblys par le runtime](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [.NET Framework : Résoudre les chargements d’assemblys](/dotnet/standard/assembly/resolve-loads)
- [StackOverflow : Assembly binding redirect, how and why?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why) (Redirection de liaison d’assembly, comment et pourquoi ?)
- [PowerShell : Discussion relative à l’implémentation d’AssemblyLoadContexts](https://github.com/PowerShell/PowerShell/issues/11571)
- [PowerShell : `Assembly.LoadFile()` ne se charge pas dans l’AssemblyLoadContext par défaut](https://github.com/PowerShell/PowerShell/issues/12052)
- [Rick Strahl : When does a .NET assembly dependency get loaded?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded) (Quand une dépendance d’assembly .NET est-elle chargée ?)
- [Jon Skeet : Summary of versioning in .NET](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/) (Récapitulatif de la gestion de versions dans .NET)
- [Nate McMaster : Deep dive into .NET Core primitives](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/) (Immersion dans les primitives .NET Core)
