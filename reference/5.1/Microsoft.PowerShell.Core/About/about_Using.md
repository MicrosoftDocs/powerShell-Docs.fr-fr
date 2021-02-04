---
description: Vous permet d’indiquer les espaces de noms qui sont utilisés dans la session.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 2a02ff32b110d369c080dde695a8fc2369b1a5e2
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98619888"
---
# <a name="about-using"></a>À propos de l’utilisation de

## <a name="short-description"></a>DESCRIPTION COURTE
Vous permet d’indiquer les espaces de noms qui sont utilisés dans la session.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L' `using` instruction vous permet de spécifier les espaces de noms qui sont utilisés dans la session. L’ajout d’espaces de noms simplifie l’utilisation des classes et membres .NET et vous permet d’importer des classes à partir de modules de script et d’assemblys.

Les `using` instructions doivent précéder toutes les autres instructions dans un script ou un module. Aucune instruction sans commentaire ne peut le précéder, y compris les paramètres.

L' `using` instruction ne doit pas contenir de variables.

L' `using` instruction ne doit pas être confondue avec le `using:` modificateur de portée pour les variables. Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).

## <a name="namespace-syntax"></a>Syntaxe d’espace de noms

Pour spécifier des espaces de noms .NET à partir desquels résoudre les types :

```
using namespace <.NET-namespace>
```

La spécification d’un espace de noms facilite la référence des types par leurs noms courts.

## <a name="module-syntax"></a>Syntaxe de module

Pour charger des classes à partir d’un module PowerShell :

```
using module <module-name>
```

La valeur de `<module-name>` peut être un nom de module, une spécification de module complète ou un chemin d’accès à un fichier de module.

Lorsque `<module-name>` est un chemin d’accès, le chemin d’accès peut être complet ou relatif. Un chemin d’accès relatif est résolu par rapport au script qui contient l’instruction using.

Quand `<module-name>` est un nom ou une spécification de module, PowerShell recherche le module spécifié dans le **PSModulePath** .

Une spécification de module est une table de hachage qui contient les clés suivantes.

- `ModuleName` - **Obligatoire** Spécifie le nom du module.
- `GUID` - **Facultatif** Spécifie le GUID du module.
- Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous. Ces clés ne peuvent pas être utilisées ensemble.
  - `ModuleVersion` -Spécifie une version minimale acceptable du module.
  - `RequiredVersion` -Spécifie une version exacte et obligatoire du module.
  - `MaximumVersion` -Spécifie la version maximale acceptable du module.

L' `using module` instruction importe des classes à partir du module racine ( `ModuleToProcess` ) d’un module de script ou d’un module binaire. Elle n’importe pas régulièrement les classes définies dans les modules imbriqués ou les classes définies dans les scripts qui sont insérés dans le module. Les classes que vous souhaitez mettre à la disposition des utilisateurs en dehors du module doivent être définies dans le module racine.

Lors du développement d’un module de script, il est courant d’apporter des modifications au code, puis de charger la nouvelle version du module en utilisant `Import-Module` avec le paramètre **force** . Cela ne fonctionne que pour les modifications apportées aux fonctions du module racine uniquement. `Import-Module` ne recharge pas les modules imbriqués. En outre, il n’existe aucun moyen de charger les classes mises à jour.

Pour vous assurer que vous exécutez la version la plus récente, vous devez décharger le module à l’aide de l’applet de commande `Remove-Module` . `Remove-Module` supprime le module racine, tous les modules imbriqués et toutes les classes définies dans les modules. Vous pouvez ensuite recharger le module et les classes à l’aide `Import-Module` de et de l' `using module` instruction.

## <a name="assembly-syntax"></a>Syntaxe d’assembly

Pour précharger des types à partir d’un assembly .NET :

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

Le chargement d’un assembly précharge les types .NET de cet assembly dans un script au moment de l’analyse. Cela vous permet de créer de nouvelles classes PowerShell qui utilisent des types de l’assembly préchargé.

Dans Windows PowerShell 5,1, vous pouvez charger l’assembly à l’aide d’un nom de chemin d’accès ou d’un nom. Lorsque vous utilisez le nom, PowerShell recherche l’assembly associé dans le global assembly cache (GAC) .NET.

Si vous ne créez pas de nouvelles classes PowerShell, utilisez `Add-Type` plutôt l’applet de commande. Pour plus d’informations, consultez [Add-type](xref:Microsoft.PowerShell.Utility.Add-Type).

## <a name="examples"></a>Exemples

### <a name="example-1---add-namespaces-for-typename-resolution"></a>Exemple 1 : ajouter des espaces de noms pour la résolution TypeName

Le script suivant obtient le hachage de chiffrement pour la chaîne « Hello World ».

Notez comment `using namespace System.Text` et `using namespace System.IO` simplifient les références à `[UnicodeEncoding]` dans `System.Text` et `[Stream]` et à `[MemoryStream]` dans `System.IO` .

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a>Exemple 2 : charger des classes à partir d’un module de script

Dans cet exemple, nous disposons d’un module de script PowerShell nommé **CardGames** qui définit les classes suivantes :

- **CardGames. Deck**
- **CardGames. carte**

`Import-Module` et l' `#requires` instruction importent uniquement les fonctions de module, les alias et les variables, comme défini par le module. Les classes ne sont pas importées. La `using module` commande importe le module et charge également les définitions de classe.

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a>Exemple 3 : charger des classes à partir d’un assembly

Cet exemple charge un assembly afin que ses classes puissent être utilisées pour créer de nouvelles classes PowerShell. Le script suivant crée une nouvelle classe PowerShell dérivée de la classe **DirectoryContext** .

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
