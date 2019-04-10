---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de classes et méthodes statiques
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293110"
---
# <a name="using-static-classes-and-methods"></a>Utilisation de classes et méthodes statiques

Certaines classes de .NET Framework ne peuvent pas être créées à l’aide de l’applet de commande **New-Object**. Par exemple, si vous essayez de créer un objet **System.Environment** ou **System.Math** avec l’applet de commande **New-Object**, vous obtenez les messages d’erreur suivants :

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

Ces erreurs se produisent parce qu’il n’existe aucun moyen de créer un objet à partir de ces classes. Ces classes sont des bibliothèques de référence de méthodes et propriétés qui ne changent pas d’état. Vous n’avez pas besoin de les créer. Vous les utilisez simplement. Les classes et méthodes telles que celles-ci sont appelées *classes statiques*, car elles ne sont pas créées, détruites ou modifiées. Par souci de clarté, nous fournirons des exemples qui utilisent des classes statiques.

## <a name="getting-environment-data-with-systemenvironment"></a>Obtention de données d’environnement avec System.Environment

En règle générale, la première étape de l’utilisation d’un objet dans Windows PowerShell consiste à utiliser l’applet de commande Get-Member pour découvrir les membres qu’il contient. Avec des classes statiques, le processus est un peu différent, car la classe réelle n’est pas un objet.

### <a name="referring-to-the-static-systemenvironment-class"></a>Référence à la classe statique System.Environment

Vous pouvez faire référence à une classe statique en entourant le nom de la classe de crochets. Par exemple, vous pouvez faire référence à la classe **System.Environment** en tapant le nom entre crochets. Cela a pour effet d’afficher des informations de type générique :

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Comme mentionné précédemment, Windows PowerShell ajoute automatiquement « **System.**  » aux noms de type lorsque vous utilisez l’applet de commande **New-Object**. La même chose se produisant en cas d’utilisation d’un nom de type entre crochets, vous pouvez spécifier **\[System.Environment]** en tant que **\[Environment]**.

La classe **System.Environment** contient des informations générales sur l’environnement de travail pour le processus actuel, c’est-à-dire powershell.exe lorsque vous travaillez dans Windows PowerShell.

Si vous essayez d’afficher les détails de cette classe en tapant **\[System.Environment] | Get-Member**, le type d’objet est signalé comme étant **System.RuntimeType**, pas **System.Environment** :

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Pour afficher les membres statiques avec Get-Member, spécifiez le paramètre **Static** paramètre :

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

Nous pouvons désormais sélectionner des propriétés à afficher à partir de System.Environment.

### <a name="displaying-static-properties-of-systemenvironment"></a>Affichage de propriétés statiques de System.Environment

Les propriétés de System.Environment sont également statiques, et doivent être spécifiées d’une autre façon que des propriétés normales. Nous utilisons **::** pour indiquer à Windows PowerShell que nous souhaitons travailler avec une méthode ou propriété statique. Pour afficher la commande utilisée pour lancer Windows PowerShell, nous vérifions la propriété **CommandLine** en tapant ce qui suit :

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Pour vérifier la version du système d’exploitation, affichez la propriété OSVersion en tapant ce qui suit :

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Nous pouvons vérifier si l’ordinateur est en cours d’arrêt en affichant la propriété **HasShutdownStarted** :

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a>Opérations mathématiques avec System.Math

La classe statique System.Math est utile pour effectuer certaines opérations mathématiques. Les membres importants de **System.Math** sont essentiellement des méthodes que nous pouvons afficher à l’aide de l’applet de commande **Get-Member**.

> [!NOTE]
> System.Math dispose de plusieurs méthodes portant le même nom, mais qui se distinguent par le type de leurs paramètres.

Tapez la commande suivante pour répertorier les méthodes de la classe **System.Math**.

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

Cette opération affiche plusieurs méthodes mathématiques. Voici une liste de commandes qui illustrent le fonctionnement de certaines méthodes courantes :

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```