---
title: Guide pratique pour créer un module binaire de bibliothèque standard
description: La bibliothèque standard PowerShell nous permet de créer des modules multiplateformes qui fonctionnent à la fois dans PowerShell Core et avec Windows PowerShell 5.1.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ff6a49f70a3fb77f5a30cc909d53bb77b3cd7d43
ms.sourcegitcommit: 8c01e56f0c10ff2637955dc892ea78432d563a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88702743"
---
# <a name="how-to-create-a-standard-library-binary-module"></a>Guide pratique pour créer un module binaire de bibliothèque standard

J’ai récemment eu une idée pour le module que je voulais implémenter en tant que module binaire. Je dois encore en créer une en utilisant la [bibliothèque standard PowerShell][], donc cela semblait être une bonne opportunité. J’ai utilisé le guide [Création d’un module binaire multiplateforme][] pour créer ce module sans rencontrer d’obstacles.
Nous allons parcourir ce même processus, auquel j’ajouterai quelques commentaires.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu. Consultez son blog sur [PowerShellExplained.com][].

## <a name="what-is-the-powershell-standard-library"></a>Qu’est-ce que la bibliothèque standard PowerShell ?

La bibliothèque standard PowerShell nous permet de créer des modules multiplateformes qui fonctionnent à la fois dans PowerShell Core et avec Windows PowerShell 5.1 (ou 3.0).

## <a name="planning-our-module"></a>Planification de notre module

Le plan pour ce module est de créer un dossier `src` pour le code C# et de structurer le reste comme je le ferais pour un module de script. Ceci inclut l’utilisation d’un script de génération pour compiler tous les éléments dans un dossier `output`. La structure des dossiers se présente comme ceci :

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a>Mise en route

J’utilise normalement un modèle Plaster, mais mon modèle actuel ne prend pas encore en charge les modules binaires. Ce n’est pas un gros problème. Je vais cette fois le créer manuellement.

Je dois d’abord créer le dossier, puis le dépôt Git. J’utilise `$module` comme espace réservé pour le nom du module. Vous pourrez ainsi réutiliser ces exemples plus facilement si nécessaire.

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

Je crée ensuite les dossiers de niveau racine.

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a>Configuration du module binaire

Cet article est principalement consacré au module binaire et c’est donc là que nous allons commencer. Cette section utilise des exemples provenant du guide [Création d’un module binaire multiplateforme][]. Consultez ce guide si vous avez besoin de plus de détails ou si vous rencontrez des problèmes.

Nous voulons d’abord vérifier la version du [SDK .NET Core][] que nous avons installée. J’utilise 2.1.4, mais vous devez avoir 2.0.0 ou ultérieur avant de continuer.

```powershell
PS> dotnet --version
2.1.4
```

Je travaille dans le dossier `src` pour cette section.

```powershell
Set-Location 'src'
```

Avec la commande dotnet, créez une bibliothèque de classes.

```powershell
dotnet new classlib --name $module
```

Ceci a créé le projet de bibliothèque dans un sous-dossier, mais je ne veux pas ce niveau supplémentaire d’imbrication. Je vais déplacer ces fichiers au niveau immédiatement supérieur.

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

Définissez la version du SDK .NET Core pour le projet. J’ai le SDK 2.1 : je vais donc spécifier 2.1.0.
Utilisez 2.0.0 si vous utilisez le SDK 2.0.

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

Ajoutez le [package NuGet][] de la bibliothèque standard PowerShell au projet. Veillez à utiliser la version la plus récente disponible pour le niveau de compatibilité dont vous avez besoin. Je devrais utiliser par défaut la dernière version, mais je ne pense pas que ce module utilise des fonctionnalités plus récentes que celles de PowerShell 3.0.

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

Nous devrions avoir un dossier src qui se présente comme ceci :

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

Nous sommes maintenant prêts à ajouter notre propre code au projet.

### <a name="building-a-binary-cmdlet"></a>Création d’une applet de commande binaire

Nous devons mettre à jour `src\Class1.cs` pour qu’il contienne cette applet de commande de démarrage :

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

Renommez le fichier pour qu’il corresponde au nom de la classe.

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

Nous pouvons ensuite générer notre module.

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

Nous pouvons appeler `Import-Module` sur la nouvelle DLL pour charger notre nouvelle applet de commande.

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

Si l’importation échoue sur votre système, essayez en effectuant une mise à jour de .NET vers la version 4.7.1 ou ultérieur. Le guide [Création d’un module binaire multiplateforme][] contient plus de détails sur la prise en charge de .NET et la compatibilité des versions antérieures de .NET.

### <a name="module-manifest"></a>Manifeste du module

Nous pouvons importer la DLL et avoir un module qui fonctionne. Je vais continuer et créer un manifeste du module. Nous avons besoin du manifeste si nous voulons publier ultérieurement sur PSGallery.

À partir de la racine de notre projet, nous pouvons exécuter cette commande pour créer le manifeste du module dont nous avons besoin.

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

Je vais également créer un module racine vide pour les fonctions PowerShell futures.

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

Ceci me permet de mélanger des fonctions PowerShell normales et des applets de commande binaires dans le même projet.

### <a name="building-the-full-module"></a>Génération du module complet

Je compile tout ensemble dans un dossier de sortie. Pour cela, nous devons créer un script de génération. Je devrais normalement l’ajouter à un script `Invoke-Build`, mais pour cet exemple, nous pouvons procéder plus simplement. Ajoutez ceci à un fichier `build.ps1` à la racine du projet.

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

Ces commandes génèrent notre DLL et la placent dans notre dossier `output\$module\bin`. Elles copient ensuite les autres fichiers du module à leur emplacement de destination.

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

À ce stade, nous pouvons importer notre module avec le fichier psd1.

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

À partir de là, nous pouvons déposer le dossier `.\Output\$module` dans notre répertoire `$env:PSModulePath` : il charge alors automatiquement notre commande chaque fois que nous en avons besoin.

### <a name="update-dotnet-new-psmodule"></a>Mise à jour : Nouveau PSModule pour dotnet

J’ai appris que l’outil `dotnet` avait un modèle `PSModule`.

Toutes les étapes décrites ci-dessus restent valides, mais ce modèle fait l’économie de beaucoup d’entre elles. Il s’agit d’un modèle relativement nouveau qui continue de s’améliorer. Attendez-vous donc à ce qu’il évolue encore.

Voici comment vous installez et comment vous utilisez le modèle PSModule.

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

Ce modèle minimaliste ajoute le SDK .NET et la bibliothèque standard PowerShell, et il crée un exemple de classe dans le projet. Vous pouvez le générer et l’exécuter immédiatement.

## <a name="important-details"></a>Détails importants

Pour terminer cet article, voici quelques autres détails qui méritent d’être mentionnés.

### <a name="unloading-dlls"></a>Déchargement des DLL

Une fois qu’un module binaire est chargé, vous ne pouvez pas réellement le décharger. Le fichier DLL est verrouillé tant que vous ne le déchargez pas. Ce peut être ennuyeux pendant le développement, car quand vous apportez une modification et que vous voulez le générer, le fichier est souvent verrouillé. La seule méthode fiable pour résoudre cela est de fermer la session PowerShell qui a chargé la DLL.

### <a name="vs-code-reload-window-action"></a>Action de la fenêtre de rechargement de VS Code

J’effectue la plupart de mon travail de développement PowerShell dans [Code Visual Studio][]. Quand je travaille sur un module binaire (ou un module avec des classes), j’ai l’habitude de recharger VS Code chaque fois que je lance une génération.
<kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> fait apparaître la fenêtre de commande et `Reload Window` est toujours en haut de ma liste.

### <a name="nested-powershell-sessions"></a>Sessions PowerShell imbriquées

Une autre option est d’avoir une bonne couverture de test de Pester. Vous pouvez ensuite ajuster le script build.ps1 pour démarrer une nouvelle session PowerShell, effectuer la génération, exécuter les tests et fermer la session.

### <a name="updating-installed-modules"></a>Mise à jour des modules installés

Ce verrouillage peut être ennuyeux quand vous essayez de mettre à jour votre module installé localement. Si une session l’a chargé, vous devez la trouver et la fermer. Ce n’est pas vraiment un problème lors de l’installation à partir de PSGallery, car la gestion de versions du module place le nouveau dans un dossier différent.

Vous pouvez configurer une PSGallery locale et publier sur celle-ci dans le cadre de votre génération. Effectuez ensuite votre installation locale à partir de cette PSGallery. Cela peut sembler être beaucoup de travail, mais ce peut être en fait aussi simple que démarrer un conteneur Docker. Je décris un moyen de faire cela dans mon billet [Utilisation d’un serveur NuGet pour un PSRepository][].

## <a name="why-binary-modules"></a>Pourquoi des modules binaires ?

Je viens de décrire directement comment créer un module binaire et je n’ai pas expliqué pourquoi vous voulez en faire un. En réalité, vous écrivez du code C#, et vous donnez un accès facile aux applets de commande et aux fonctions PowerShell. C’est la raison principale pour laquelle je ne suis pas passé plus tôt aux modules binaires.

Cependant, si vous créez un module qui ne dépend pas d’un grand nombre d’autres commandes PowerShell, l’avantage en termes de performances peut être significatif. En passant à C#, vous vous affranchissez de la charge ajoutée par PowerShell. PowerShell a été optimisé pour l’administrateur et non pas pour l’ordinateur, et ceci ajoute une petite surcharge.

Dans mon entreprise, nous avons un processus critique qui effectue beaucoup de travail avec JSON et des tables de hachage. Nous avons optimisé le code PowerShell autant que possible, mais l’exécution de ce traitement durait encore 12 minutes. Le module contenait déjà beaucoup de code PowerShell de style C#. Ceci a rendu la conversion en module binaire propre et facile à faire. Notre conversion a réduit la durée d’exécution de ce traitement de 12 minutes à moins de 4 minutes.

### <a name="hybrid-modules"></a>Modules hybrides

Vous pouvez combiner des applets de commande binaires avec des fonctions avancées PowerShell. C’est exactement ce que je fais dans ce guide. Vous pouvez prendre tout ce que vous savez sur les modules de script : tout s’applique de la même façon.
Le fichier `psm1` vide que j’ai créé aujourd’hui est là seulement pour vous permettre d’y placer ultérieurement d’autres fonctions PowerShell.

Presque toutes les applets de commande compilées que nous avons créées étaient initialement des fonctions PowerShell. Tous nos modules binaires sont véritablement des modules hybrides.

### <a name="build-scripts"></a>Scripts de génération

J’ai veillé ici à ce que le script de génération reste simple. J’utilise généralement un long script `Invoke-Build` dans le cadre de mon pipeline CI/CD. Il en fait beaucoup plus, comme exécuter des tests Pester, exécuter PSScriptAnalyzer, gérer les versions et publier sur PSGallery. Une fois que j’ai commencé à utiliser un script de génération pour mes modules, j’ai pu trouver un grand nombre de choses à y ajouter.

## <a name="final-thoughts"></a>Réflexions finales

Les modules binaires sont faciles à créer. Je n’ai pas touché à la syntaxe C# pour la création d’une applet de commande, mais il y a beaucoup de documentation sur celle-ci dans le [Windows PowerShell SDK][]. Il est tout à fait intéressant d’expérimenter cela comme un tremplin vers du C# plus complexe.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Bibliothèque standard PowerShell]: https://github.com/PowerShell/PowerShellStandard
[Création d’un module binaire multiplateforme]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[SDK .NET Core]: https://www.microsoft.com/net/download/core
[Utilisation d’un serveur NuGet pour un PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[Code Visual Studio]: https://code.visualstudio.com
[Package NuGet]: https://www.nuget.org/packages/PowerShellStandard.Library/
