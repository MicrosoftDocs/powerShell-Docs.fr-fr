---
description: Explique comment créer des objets dans PowerShell.
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 72c0d763fe7f3838c8b2ca68930521e24d0e6139
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602913"
---
# <a name="about-object-creation"></a>À propos de la création d’objets

## <a name="short-description"></a>Description courte

Explique comment créer des objets dans PowerShell.

## <a name="long-description"></a>Description longue

Vous pouvez créer des objets dans PowerShell et utiliser les objets que vous créez dans les commandes et les scripts.

Il existe plusieurs façons de créer des objets, cette liste n’est pas définitive :

- [New-Object](xref:Microsoft.PowerShell.Utility.New-Object): crée une instance d’un objet .NET Framework ou d’un objet com.
- [Importation-CSV](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): crée des objets personnalisés (**PSCustomObject**) à partir des éléments définis comme valeurs séparées par des virgules.
- [ConvertFrom-JSON](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): crée des objets personnalisés définis en JavaScript Object Notation (JSON).
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): crée des objets personnalisés définis en tant que paires clé-valeur.
- [Add-type](xref:Microsoft.PowerShell.Utility.Add-Type): vous permet de définir une classe dans votre session PowerShell avec laquelle vous pouvez effectuer une instanciation `New-Object` .
- [New-module](xref:Microsoft.PowerShell.Core.New-Module): le paramètre **AsCustomObject** crée un objet personnalisé que vous définissez à l’aide du bloc de script.
- [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): ajoute des propriétés aux objets existants. Vous pouvez utiliser `Add-Member` pour créer un objet personnalisé à partir d’un type simple, comme `[System.Int32]` .
- [Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): sélectionne des propriétés sur un objet. Vous pouvez utiliser `Select-Object` pour créer des propriétés personnalisées et calculées sur un objet déjà instancié.

Les méthodes supplémentaires suivantes sont traitées dans cet article :

- En appelant le constructeur d’un type à l’aide d’une `new()` méthode statique
- Par Cast tables de hachage des noms de propriété et des valeurs de propriété

## <a name="static-new-method"></a>Méthode static New ()

Tous les types .NET ont une `new()` méthode qui vous permet de construire des instances plus facilement. Vous pouvez également voir tous les constructeurs disponibles pour un type donné.

Pour afficher les constructeurs d’un type, spécifiez le `new` nom de la méthode après le nom de type et appuyez sur `<ENTER>` .

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

À présent, vous pouvez créer un **System. Uri** en spécifiant le constructeur approprié.

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

Vous pouvez utiliser l’exemple suivant pour déterminer les types .NET actuellement chargés pour l’instanciation.

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

Les objets créés à l’aide de la `new()` méthode peuvent ne pas avoir les mêmes propriétés que les objets du même type qui sont créés par les applets de commande PowerShell. Les applets de commande PowerShell, les fournisseurs et le système de type étendu peuvent ajouter des propriétés supplémentaires à l’instance.

Par exemple, le fournisseur FileSystem dans PowerShell ajoute six valeurs **NoteProperty** à l’objet **DirectoryInfo** retourné par `Get-Item` .

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

Lorsque vous créez un objet **DirectoryInfo** directement, il ne possède pas ces six valeurs **NoteProperty** .

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

Pour plus d’informations sur le système de type étendu, consultez [about_Types.ps1XML](about_Types.ps1xml.md).

Cette fonctionnalité a été ajoutée dans PowerShell 5,0

## <a name="create-objects-from-hash-tables"></a>Créer des objets à partir de tables de hachage

Vous pouvez créer un objet à partir d’une table de hachage de propriétés et de valeurs de propriété.

La syntaxe est la suivante :

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

Cette méthode fonctionne uniquement pour les classes qui ont un constructeur sans paramètre. Les propriétés de l’objet doivent être publiques et définissables.

Cette fonctionnalité a été ajoutée dans PowerShell version 3,0

## <a name="create-custom-objects-from-hash-tables"></a>Créer des objets personnalisés à partir de tables de hachage

Les objets personnalisés sont très utiles et sont faciles à créer à l’aide de la méthode de table de hachage. La classe **PSCustomObject** est spécifiquement conçue à cet effet.

Les objets personnalisés sont un excellent moyen de retourner une sortie personnalisée à partir d’une fonction ou d’un script. Cela est plus utile que le renvoi d’une sortie mise en forme qui ne peut pas être reformatée ou redirigée vers d’autres commandes.

Les commandes dans le `Test-Object function` définissent des valeurs de variables, puis utilisent ces valeurs pour créer un objet personnalisé. Vous pouvez voir cet objet en cours d’utilisation dans la section exemple de la rubrique d’aide de l’applet de commande `Update-Help` .

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

La sortie de cette fonction est une collection d’objets personnalisés sous forme de table par défaut.

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

Les utilisateurs peuvent gérer les propriétés des objets personnalisés de la même manière qu’avec les objets standard.

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a>Créer des objets non personnalisés à partir de tables de hachage

Vous pouvez également utiliser des tables de hachage pour créer des objets pour les classes non personnalisées. Lorsque vous créez un objet pour une classe non personnalisée, le nom de type qualifié par un espace de noms est obligatoire, même si vous pouvez omettre un composant d’espace de noms **système** initial.

Par exemple, la commande suivante crée un objet d’option de session.

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

Les exigences de la fonctionnalité de table de hachage, en particulier l’exigence de constructeur sans paramètre, éliminent de nombreuses classes existantes. Toutefois, la plupart des classes d' _options_ PowerShell sont conçues pour fonctionner avec cette fonctionnalité, ainsi que d’autres classes très utiles, telles que la classe **ProcessStartInfo** .

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

Vous pouvez également utiliser la fonctionnalité de table de hachage lors de la définition des valeurs de paramètre. Par exemple, la valeur du paramètre **SessionOption** de `New-PSSession` .
une applet de commande peut être une table de hachage.

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a>Objets génériques

Vous pouvez également créer des objets génériques dans PowerShell. Les génériques sont des classes, des structures, des interfaces et des méthodes qui possèdent des espaces réservés (ou paramètres de type) pour un ou plusieurs des types qu'ils stockent ou utilisent.

L’exemple suivant crée un objet **dictionnaire** .

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

Pour plus d’informations sur les génériques, consultez [génériques dans .net](/dotnet/standard/generics).

## <a name="see-also"></a>Voir aussi

[about_Objects](about_Objects.md)

[about_Methods](about_Methods.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[about_Types.ps1xml](about_Types.ps1xml.md)
