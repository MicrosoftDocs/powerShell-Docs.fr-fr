---
description: Décrit comment utiliser les propriétés d’objet dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: d4d3cd93e6b177e80d85315f125c647219fc4a45
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208305"
---
# <a name="about-properties"></a>À propos des propriétés

## <a name="short-description"></a>Description courte
Décrit comment utiliser les propriétés d’objet dans PowerShell.

## <a name="long-description"></a>Description longue

PowerShell utilise des collections d’informations structurées appelées objets pour représenter les éléments des magasins de données ou l’état de l’ordinateur. En général, vous travaillez avec des objets qui font partie de l’infrastructure Microsoft .NET, mais vous pouvez également créer des objets personnalisés dans PowerShell.

L’association entre un élément et son objet est très proche. Lorsque vous modifiez un objet, vous modifiez généralement l’élément qu’il représente. Par exemple, lorsque vous recevez un fichier dans PowerShell, vous n’avez pas le fichier réel. Au lieu de cela, vous recevez un objet FileInfo qui représente le fichier. Lorsque vous modifiez l’objet FileInfo, le fichier change également.

La plupart des objets ont des propriétés. Les propriétés sont les données associées à un objet. Les différents types d’objets ont des propriétés différentes. Par exemple, un objet FileInfo, qui représente un fichier, a une propriété **IsReadOnly** qui contient $true si le fichier est l’attribut en lecture seule et $false si ce n’est pas le cas.
Un objet DirectoryInfo, qui représente un répertoire du système de fichiers, possède une propriété parente qui contient le chemin d’accès au répertoire parent.

### <a name="object-properties"></a>Propriétés de l’objet

Pour récupérer les propriétés d’un objet, utilisez l' `Get-Member` applet de commande. Par exemple, pour obtenir les propriétés d’un objet **FileInfo** , utilisez l' `Get-ChildItem` applet de commande pour obtenir l’objet FileInfo qui représente un fichier. Utilisez ensuite un opérateur de pipeline (&#124;) pour envoyer l’objet **FileInfo** à `Get-Member` . La commande suivante obtient le fichier PowerShell.exe et l’envoie à `Get-Member` .
La \$ variable automatique pshome contient le chemin d’accès du répertoire d’installation de PowerShell.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

La sortie de la commande répertorie les membres de l’objet **FileInfo** .
Les membres incluent à la fois les propriétés et les méthodes. Lorsque vous travaillez dans PowerShell, vous avez accès à tous les membres des objets.

Pour obtenir uniquement les propriétés d’un objet et non les méthodes, utilisez le paramètre MemberType de l' `Get-Member` applet de commande avec la valeur « Property », comme indiqué dans l’exemple suivant.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

Une fois que vous avez trouvé les propriétés, vous pouvez les utiliser dans vos commandes PowerShell.

## <a name="property-values"></a>Valeurs de propriétés

Bien que chaque objet d’un type spécifique ait les mêmes propriétés, les valeurs de ces propriétés décrivent l’objet particulier. Par exemple, chaque objet FileInfo a une propriété CreationTime, mais la valeur de cette propriété diffère pour chaque fichier.

La méthode la plus courante pour récupérer les valeurs des propriétés d’un objet consiste à utiliser la méthode point. Tapez une référence à l’objet, telle qu’une variable qui contient l’objet ou une commande qui obtient l’objet. Ensuite, tapez un point (.) suivi du nom de la propriété.

Par exemple, la commande suivante affiche la valeur de la propriété CreationTime du fichier PowerShell.exe. La `Get-ChildItem` commande retourne un objet FileInfo qui représente le fichier PowerShell.exe. La commande est placée entre parenthèses pour s’assurer qu’elle est exécutée avant l’accès à toutes les propriétés. La `Get-ChildItem` commande est suivie d’un point et du nom de la propriété CreationTime, comme suit :

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

Vous pouvez également enregistrer un objet dans une variable, puis obtenir ses propriétés à l’aide de la méthode point, comme indiqué dans l’exemple suivant :

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

Vous pouvez également utiliser les `Select-Object` applets de commande et `Format-List` pour afficher les valeurs de propriété d’un objet. `Select-Object` et `Format-List` ont chacun un paramètre de **propriété** . Vous pouvez utiliser le paramètre **Property** pour spécifier une ou plusieurs propriétés et leurs valeurs. Vous pouvez utiliser le caractère générique ( \* ) pour représenter toutes les propriétés.

Par exemple, la commande suivante affiche les valeurs de toutes les propriétés du fichier PowerShell.exe.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a>Propriétés statiques

Vous pouvez utiliser les propriétés statiques des classes .NET dans PowerShell. Les propriétés statiques sont des propriétés de classe, contrairement aux propriétés standard, qui sont des propriétés d’un objet.

Pour récupérer les propriétés statiques d’une classe, utilisez le paramètre static de l’applet de commande Get-Member.

Par exemple, la commande suivante obtient les propriétés statiques de la `System.DateTime` classe.

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

Pour obtenir la valeur d’une propriété statique, utilisez la syntaxe suivante.

```
[<ClassName>]::<Property>
```

Par exemple, la commande suivante obtient la valeur de la propriété statique UtcNow de la `System.DateTime` classe.

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a>Propriétés des collections et des objets scalaires

Les propriétés d’un objet (« scalaire ») d’un type particulier sont souvent différentes des propriétés d’une collection d’objets du même type.
Par exemple, chaque service possède la propriété **DisplayName** , mais une collection de services n’a pas de propriété **DisplayName** .

La commande suivante obtient la valeur de la propriété **DisplayName** du service « audiosrv ».

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

À compter de PowerShell 3,0, PowerShell tente d’éviter les erreurs de script qui résultent des propriétés différentes des collections et des objets scalaires. La même commande retourne la valeur de la propriété **DisplayName** de chaque service `Get-Service` retourné par.

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

Lorsque vous envoyez un regroupement, mais que vous demandez une propriété qui existe uniquement sur des objets (« scalaires ») uniques, PowerShell retourne la valeur de cette propriété pour chaque objet de la collection.

Toutes les collections ont une propriété **Count** qui retourne le nombre d’objets présents dans la collection.

```powershell
(Get-Service).Count
```

```output
176
```

À compter de PowerShell 3,0, si vous demandez la propriété Count ou length des objets zéro ou un objet, PowerShell retourne la valeur correcte.

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

Si une propriété existe sur les objets individuels et sur la collection, seule la propriété de la collection est retournée.

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

Cette fonctionnalité fonctionne également sur les méthodes des objets scalaires et des collections. Pour plus d’informations, consultez [about_methods](about_methods.md).

## <a name="see-also"></a>Voir aussi

[about_Methods](about_Methods.md)

[about_Objects](about_Objects.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

