---
description: Décrit comment utiliser des méthodes pour effectuer des actions sur des objets dans PowerShell.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: b099dcecd3dbd713a7ade3d17194f27324fe2b3c
ms.sourcegitcommit: 15f759ca68d17acecab46b52250298d4f2037c4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103575591"
---
# <a name="about-methods"></a>À propos des méthodes

## <a name="short-description"></a>Description courte
Décrit comment utiliser des méthodes pour effectuer des actions sur des objets dans PowerShell.

## <a name="long-description"></a>Description longue

PowerShell utilise des objets pour représenter les éléments dans les magasins de données ou l’état de l’ordinateur. Par exemple, les objets FileInfo représentent les fichiers des lecteurs du système de fichiers et les objets ProcessInfo représentent les processus sur l’ordinateur.

Les objets ont des propriétés, qui stockent des données sur l’objet et des méthodes qui vous permettent de modifier l’objet.

Une « méthode » est un ensemble d’instructions qui spécifient une action que vous pouvez effectuer sur l’objet. Par exemple, l' `FileInfo` objet comprend la `CopyTo` méthode qui copie le fichier que l' `FileInfo` objet représente.

Pour récupérer les méthodes de n’importe quel objet, utilisez l’applet de commande `Get-Member` . Utilisez sa propriété **MemberType** avec la valeur « Method ». La commande suivante obtient les méthodes des objets processus.

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

Pour exécuter ou « appeler » une méthode d’un objet, tapez un point (.), le nom de la méthode et un jeu de parenthèses « () ». Si la méthode a des arguments, placez les valeurs d’argument à l’intérieur des parenthèses. Les parenthèses sont obligatoires pour chaque appel de méthode, même s’il n’y a pas d’arguments. Si la méthode accepte plusieurs arguments, ceux-ci doivent être séparés par des virgules.

Par exemple, la commande suivante appelle la méthode Kill des processus pour terminer le processus du bloc-notes sur l’ordinateur.

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

Cet exemple peut être réduit en combinant les instructions ci-dessus.

```powershell
(Get-Process Notepad).Kill()
```

La `Get-Process` commande est placée entre parenthèses pour s’assurer qu’elle s’exécute avant l’appel de la méthode Kill. La `Kill` méthode est ensuite appelée sur l’objet retourné `Process` .

Une autre méthode très utile est la `Replace` méthode de chaînes. La `Replace` méthode remplace le texte dans une chaîne. Dans l’exemple ci-dessous, le point (.) peut être placé immédiatement après le guillemet de fin de la chaîne.

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

Comme indiqué dans les exemples précédents, vous pouvez appeler une méthode sur un objet que vous avez obtenu à l’aide d’une commande, d’un objet dans une variable ou de tout ce qui produit un objet (par exemple, une chaîne entre guillemets).

À compter de PowerShell 4,0, l’appel de méthode à l’aide de noms de méthodes dynamiques est pris en charge.

## <a name="learning-about-methods"></a>En savoir plus sur les méthodes

Pour rechercher les définitions des méthodes d’un objet, accédez à la rubrique d’aide relative au type d’objet et recherchez sa page de méthodes. Par exemple, la page suivante décrit les méthodes de traitement des objets [System. Diagnostics. Process](/dotnet/api/system.diagnostics.process#methods).

Pour déterminer les arguments d’une méthode, examinez la définition de la méthode, qui est semblable au diagramme de syntaxe d’une applet de commande PowerShell.

Une définition de méthode peut avoir une ou plusieurs signatures de méthode, qui sont similaires aux jeux de paramètres des applets de commande PowerShell. Les signatures affichent tous les formats de commandes valides pour appeler la méthode.

Par exemple, la `CopyTo` méthode de la `FileInfo` classe contient les deux signatures de méthode suivantes :

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

La première signature de méthode prend le nom de fichier de destination (et un chemin d’accès). L’exemple suivant utilise la première `CopyTo` méthode pour copier le `Final.txt` fichier dans le `C:\Bin` répertoire.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> Contrairement au mode d' _argument_ de PowerShell, les méthodes d’objet s’exécutent en mode _expression_ , qui est un transfert vers le .NET Framework sur lequel PowerShell est basé. En mode _expression_ , les arguments **bareword** (chaînes sans guillemets) ne sont pas autorisés. Vous pouvez voir cette différence lorsque vous utilisez un chemin d’accès en tant que paramètre, par opposition au chemin d’accès en tant qu’argument. Pour plus d’informations sur les modes d’analyse, consultez [about_Parsing](about_Parsing.md)

La deuxième signature de méthode accepte un nom de fichier de destination et une valeur booléenne qui détermine si le fichier de destination doit être remplacé, s’il existe déjà.

L’exemple suivant utilise la deuxième `CopyTo` méthode pour copier le `Final.txt` fichier dans le `C:\Bin` répertoire, et pour remplacer les fichiers existants.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

## <a name="methods-of-scalar-objects-and-collections"></a>Méthodes d’objets scalaires et de collections

Les méthodes d’un objet (« scalaire ») d’un type particulier sont souvent différentes des méthodes d’une collection d’objets du même type.

Par exemple, chaque processus a une `Kill` méthode, mais une collection de processus n’a pas de méthode Kill.

À compter de PowerShell 3,0, PowerShell tente d’éviter les erreurs de script qui résultent des différentes méthodes d’objets scalaires et de collections.

Si vous envoyez une collection, mais que vous demandez une méthode qui existe uniquement sur des objets (« scalaires ») uniques, PowerShell appelle la méthode sur chaque objet de la collection.

Si la méthode existe sur les objets individuels et sur la collection, seule la méthode de la collection est appelée.

Cette fonctionnalité fonctionne également sur les propriétés des collections et des objets scalaires. Pour plus d’informations, consultez [about_Properties](about_Properties.md).

### <a name="examples"></a>Exemples

L’exemple suivant exécute la méthode **Kill** des objets de processus individuels dans une collection d’objets.

La première commande démarre trois instances du processus Notepad. `Get-Process` Obtient les trois instances du processus Notepad et les enregistre dans la `$p` variable.

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

La commande suivante exécute la méthode **Kill** sur les trois processus de la `$p` variable. Cette commande fonctionne même si une collection de processus n’a pas de `Kill` méthode.

```powershell
$p.Kill()
Get-Process Notepad
```

La `Get-Process` commande confirme que la `Kill` méthode a fonctionné.

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

Cet exemple est fonctionnellement équivalent à l’utilisation de l' `Foreach-Object` applet de commande pour exécuter la méthode sur chaque objet de la collection.

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a>Méthodes ForEach et where

À compter de PowerShell 4,0, le filtrage de collection à l’aide d’une syntaxe de méthode est pris en charge. Cela permet d’utiliser deux nouvelles méthodes pour traiter les collections `ForEach` et `Where` .

Vous pouvez en savoir plus sur ces méthodes dans [about_arrays](about_arrays.md)

## <a name="calling-a-specific-method-when-multiple-overloads-exist"></a>Appel d’une méthode spécifique quand plusieurs surcharges existent

Considérez le scénario suivant lors de l’appel de méthodes .NET. Si une méthode prend un objet mais a une surcharge via une interface qui prend un type plus spécifique, PowerShell choisit la méthode qui accepte l’objet, sauf si vous effectuez un cast explicite vers cette interface.

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

Dans cet exemple, la surcharge la plus spécifique `object` de la méthode **bar** a été choisie.

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

Dans cet exemple, nous castons la méthode en interface **IFoo** pour sélectionner la surcharge plus spécifique de la méthode de la **barre** .

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="using-net-methods-that-take-filesystem-paths"></a>Utilisation des méthodes .NET qui prennent des chemins d’accès de système de fichiers

PowerShell prend en charge plusieurs instances d’exécution par processus. Chaque instance d’exécution a son propre _répertoire actif_. Ce n’est pas le même que le répertoire de travail du processus en cours : `[System.Environment]::CurrentDirectory` .

Les méthodes .NET utilisent le répertoire de travail du processus. Les applets de commande PowerShell utilisent l’emplacement d’instance d’exécution. En outre, les méthodes .NET fonctionnent uniquement avec les chemins d’accès de système de fichiers natifs, pas les objets de chemin d’accès PowerShell. Pour utiliser des chemins d’accès PowerShell avec des méthodes .NET, vous devez résoudre le chemin d’accès à un chemin d’accès natif du système de fichiers avant de le passer à la méthode .NET.

## <a name="see-also"></a>Voir aussi

[about_Objects](about_Objects.md)

[about_Properties](about_Properties.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)
