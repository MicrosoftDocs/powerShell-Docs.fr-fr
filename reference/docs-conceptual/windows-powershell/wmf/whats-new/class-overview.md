---
ms.date: 07/29/2020
title: Nouvelles fonctionnalités de langage dans PowerShell 5.0
description: PowerShell 5.0 offre la possibilité de définir des classes et d’autres types définis par l’utilisateur suivant une syntaxe et une sémantique formelles similaires à celles des autres langages de programmation orientés objet.
ms.openlocfilehash: 31ff54ba6f2800a0680c1a2db3832ca97246973d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663313"
---
# <a name="new-language-features-in-powershell-50"></a>Nouvelles fonctionnalités de langage dans PowerShell 5.0

PowerShell 5.0 offre la possibilité de définir des classes et d’autres types définis par l’utilisateur suivant une syntaxe et une sémantique formelles similaires à celles des autres langages de programmation orientés objet. L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.

PowerShell 5.0 offre les nouveaux éléments de langage suivants dans PowerShell :

### <a name="class-keyword"></a>Mot clé classe

Le mot clé `class` définit une nouvelle classe. Il s’agit d’un véritable type .NET Framework. Les membres de la classe sont publics, mais uniquement dans l’étendue du module. Il n’est pas possible de faire référence au nom de type sous forme de chaîne (par exemple, `New-Object` ne fonctionne pas) ou, dans cette version, d’utiliser un littéral de type (par exemple, `[MyClass]`) en dehors du fichier de script ou du module dans lequel la classe est définie.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Mot clé Enum et énumérations

La prise en charge du mot clé `enum` a été ajoutée. Il utilise le saut de ligne comme délimiteur. Il n’est pas possible à l’heure actuelle de définir un énumérateur par lui-même. Vous pouvez en revanche l’initialiser à partir d’un autre enum, comme dans l’exemple suivant. Par ailleurs, le type de base n’est pas spécifiable ; il s’agit toujours de `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Une valeur d’énumérateur doit être une constante au moment de l’analyse. Il ne peut pas s’agir du résultat d’une commande appelée.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Les énumérations prennent en charge les opérations arithmétiques, comme illustré dans l’exemple suivant.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` est maintenant un mot clé véritablement dynamique. PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut **DscResource** .

### <a name="implementingassembly"></a>ImplementingAssembly

Un nouveau champ, **ImplementingAssembly** , a été ajouté à **ModuleInfo** . Elle a comme valeur l’assembly dynamique créé pour un module de script si le script définit des classes, ou l’assembly chargé pour les modules binaires. Il n’est pas défini quand **ModuleType** a la valeur **Manifest** .

La réflexion sur le champ **ImplementingAssembly** découvre des ressources dans un module. Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.

## <a name="further-reading"></a>Informations supplémentaires

- [À propos des classes](/powershell/module/microsoft.powershell.core/about/about_classes)
- [À propos de l’énumération](/powershell/module/microsoft.powershell.core/about/about_enum)
- [À propos des classes et de DSC](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
