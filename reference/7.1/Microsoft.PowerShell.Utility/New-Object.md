---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3c34022c84c26ee0d8395fc589e8d1da957979b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204985"
---
# New-Object

## SYNOPSIS
Crée une instance d'un objet Microsoft .NET Framework ou COM.

## SYNTAX

### NET (par défaut)

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### Com

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## Description

L' `New-Object` applet de commande crée une instance d’un .NET Framework ou d’un objet com.

Vous pouvez spécifier le type d'une classe .NET Framework ou un ProgID d'un objet COM. Par défaut, vous tapez le nom complet d'une classe .NET Framework et l'applet de commande retourne une référence à une instance de cette classe. Pour créer une instance d’un objet COM, utilisez le paramètre **ComObject** et spécifiez le ProgID de l’objet comme valeur.

## EXEMPLES

### Exemple 1 : créer un objet System. version

Cet exemple crée un objet **System. version** à l’aide de la chaîne « 1.2.3.4 » comme constructeur.

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### Exemple 2 : créer un objet COM Internet Explorer

Cet exemple crée deux instances de l’objet COM qui représente l’application Internet Explorer. La première instance utilise la table de hachage des paramètres de **propriété** pour appeler la méthode **Navigate2** et définir la propriété **visible** de l’objet sur `$True` pour rendre l’application visible.
La deuxième instance obtient les mêmes résultats avec des commandes individuelles.

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### Exemple 3 : utiliser le paramètre strict pour générer une erreur sans fin d’achèvement

Cet exemple montre que l’ajout du paramètre **strict** fait que l' `New-Object` applet de commande génère une erreur sans fin d’achèvement lorsque l’objet com utilise un assembly d’interopérabilité.

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### Exemple 4 : créer un objet COM pour gérer le bureau Windows

Cet exemple illustre comment créer et utiliser un objet COM pour gérer votre Bureau Windows.

La première commande utilise le paramètre **ComObject** de l' `New-Object` applet de commande pour créer un objet com avec le ProgID **Shell. application** . Elle stocke l’objet résultant dans la `$ObjShell` variable. La deuxième commande dirige la `$ObjShell` variable vers l' `Get-Member` applet de commande, qui affiche les propriétés et les méthodes de l’objet com. Parmi les méthodes, citons la méthode **ToggleDesktop** . La troisième commande appelle la méthode **ToggleDesktop** de l'objet pour réduire les fenêtres ouvertes sur votre Bureau.

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### Exemple 5 : passer plusieurs arguments à un constructeur

Cet exemple montre comment créer un objet avec un constructeur qui accepte plusieurs paramètres. Les paramètres doivent être placés dans un tableau lors de l’utilisation du paramètre **argumentlist** .

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

PowerShell lie chaque membre du tableau à un paramètre du constructeur.

> [!NOTE]
> Cet exemple utilise la projection de paramètres pour une meilleure lisibilité. Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

### Exemple 6 : appel d’un constructeur qui accepte un tableau en tant que paramètre unique

Cet exemple montre comment créer un objet avec un constructeur qui accepte un paramètre qui est un tableau ou une collection. Le paramètre de tableau doit être placé dans un wrapper à l’intérieur d’un autre tableau.

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

La première tentative de création de l’objet dans cet exemple échoue. PowerShell a tenté de lier les trois membres de `$array` aux paramètres du constructeur, mais le constructeur ne prend pas trois paramètres. L’encapsulation `$array` dans un autre tableau empêche PowerShell de tenter de lier les trois membres de `$array` aux paramètres du constructeur.

## PARAMETERS

### -ArgumentList

Spécifie un tableau d’arguments à passer au constructeur de la classe .NET Framework. Si le constructeur accepte un seul paramètre qui est un tableau, vous devez encapsuler ce paramètre à l’intérieur d’un autre tableau. Par exemple :

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).

L'alias d' **ArgumentList** est **Args** .

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject

Spécifie l'identificateur programmatique (ProgID) de l'objet COM.

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Définit les valeurs de propriété et appelle les méthodes du nouvel objet.

Entrez une table de hachage dans laquelle les clés sont les noms des propriétés ou des méthodes, et les valeurs sont des valeurs de propriété ou des arguments de méthode. `New-Object` crée l’objet et définit chaque valeur de propriété et appelle chaque méthode dans l’ordre dans lequel elles apparaissent dans la table de hachage.

Si le nouvel objet est dérivé de la classe **PSObject** et que vous spécifiez une propriété qui n’existe pas sur l’objet, `New-Object` ajoute la propriété spécifiée à l’objet en tant que NoteProperty. Si l’objet n’est pas un **PSObject** , la commande génère une erreur sans fin d’achèvement.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

Indique que l’applet de commande génère une erreur sans fin d’achèvement lorsqu’un objet COM que vous tentez de créer utilise un assembly d’interopérabilité. Cette fonctionnalité distingue les objets COM réels des objets .NET Framework avec des wrappers CCW (COM-callable wrapper).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Spécifie le nom complet de la classe .NET Framework. Vous ne pouvez pas spécifier à la fois le paramètre **TypeName** et le paramètre **ComObject** .

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Object

`New-Object` retourne l’objet créé.

## REMARQUES

- `New-Object` fournit les fonctionnalités les plus couramment utilisées de la fonction VBScript CreateObject. Une instruction comme `Set objShell = CreateObject("Shell.Application")` dans VBScript peut être traduite en `$objShell = New-Object -COMObject "Shell.Application"` PowerShell.
- `New-Object` développe les fonctionnalités disponibles dans l’environnement d’exécution de scripts Windows en facilitant l’utilisation des objets .NET Framework à partir de la ligne de commande et dans les scripts.

## LIENS CONNEXES

[about_Object_Creation](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[Compare-Object](Compare-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

