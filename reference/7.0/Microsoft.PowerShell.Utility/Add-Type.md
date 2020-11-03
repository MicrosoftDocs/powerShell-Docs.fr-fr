---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: cbf211f4ae5262255a74fa7fb97d2493202d71fa
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206234"
---
# Add-Type

## SYNOPSIS
Ajoute une classe Microsoft .NET Core à une session PowerShell.

## SYNTAX

### FromSource (par défaut)

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromMember

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromPath

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromLiteralPath

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromAssemblyName

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## Description

L' `Add-Type` applet de commande vous permet de définir une classe de base Microsoft .net dans votre session PowerShell. Vous pouvez ensuite instancier des objets, à l’aide de l’applet de commande `New-Object` , et utiliser les objets comme vous le feriez pour n’importe quel objet .net core. Si vous ajoutez une `Add-Type` commande à votre profil PowerShell, la classe est disponible dans toutes les sessions PowerShell.

Vous pouvez spécifier le type en désignant un assembly existant ou des fichiers de code source. Par ailleurs, vous pouvez spécifier le code source inline ou enregistré dans une variable. Vous pouvez même spécifier uniquement une méthode et `Add-Type` définit et génère la classe. Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell. Si vous spécifiez le code source, `Add-Type` compile le code source spécifié et génère un assembly en mémoire qui contient les nouveaux types .net core.

Vous pouvez utiliser les paramètres de `Add-Type` pour spécifier un autre langage et un autre compilateur, C# est l’option par défaut, les options du compilateur, les dépendances de l’assembly, l’espace de noms de la classe, les noms du type et l’assembly résultant.

À compter de PowerShell 7, `Add-Type` ne compile pas un type si un type portant le même nom existe déjà. Recherche également les `Add-Type` assemblys dans un `ref` dossier sous le dossier qui contient `pwsh.dll` .

## EXEMPLES

### Exemple 1 : ajouter un type .NET à une session

Cet exemple ajoute la classe **BasicTest** à la session en spécifiant le code source stocké dans une variable. La classe **BasicTest** est utilisée pour ajouter des entiers, créer un objet et multiplier des entiers.

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

La `$Source` variable stocke le code source de la classe. Le type a une méthode statique appelée `Add` et une méthode non statique appelée `Multiply` .

L' `Add-Type` applet de commande ajoute la classe à la session. Comme il utilise le code source en ligne, la commande utilise le paramètre **TypeDefinition** pour spécifier le code dans la `$Source` variable.

La `Add` méthode statique de la classe **BasicTest** utilise les caractères double deux-points ( `::` ) pour spécifier un membre statique de la classe. Les entiers sont ajoutés et la somme est affichée.

L' `New-Object` applet de commande instancie une instance de la classe **BasicTest** . Elle enregistre le nouvel objet dans la `$BasicTestObject` variable.

`$BasicTestObject` utilise la `Multiply` méthode. Les entiers sont multipliés et le produit est affiché.

### Exemple 2 : examiner un type ajouté

Cet exemple utilise l' `Get-Member` applet de commande pour examiner les objets `Add-Type` créés par les `New-Object` applets de commande et dans l' **exemple 1** .

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

L' `Get-Member` applet de commande obtient le type et les membres de la classe **BasicTest** qui ont `Add-Type` été ajoutés à la session. La `Get-Member` commande révèle qu’il s’agit d’un objet **System. RuntimeType** , dérivé de la classe **System. Object** .

Le `Get-Member` paramètre **static** obtient les propriétés et les méthodes statiques de la classe **BasicTest** . La sortie indique que la `Add` méthode est incluse.

L' `Get-Member` applet de commande obtient les membres de l’objet stocké dans la `$BasicTestObject` variable.
`$BasicTestObject` a été créé à l’aide de l' `New-Object` applet de commande avec la classe **BasicTest** . La sortie révèle que la valeur de la `$BasicTestObject` variable est une instance de la classe **BasicTest** et qu’elle comprend un membre appelé `Multiply` .

### Exemple 3 : ajouter des types à partir d’un assembly

Cet exemple ajoute les classes de l' `NJsonSchema.dll` assembly à la session active.

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

`Set-Location` utilise le paramètre **path** pour spécifier la `$PSHOME` variable. La variable référence le répertoire d’installation de PowerShell dans lequel se trouve le fichier DLL.

La `$AccType` variable stocke un objet créé avec l’applet de commande `Add-Type` . `Add-Type` utilise le paramètre **AssemblyName** pour spécifier le nom de l’assembly. Le `*` caractère générique astérisque () vous permet d’accéder à l’assembly approprié même si vous n’êtes pas sûr de son nom ou de son orthographe. Le paramètre **PassThru** génère des objets qui représentent les classes ajoutées à la session.

### Exemple 4 : appeler des API Windows natives

Cet exemple montre comment appeler des API Windows natives dans PowerShell. `Add-Type` utilise le mécanisme d’appel de code non managé (P/Invoke) pour appeler une fonction dans `User32.dll` à partir de PowerShell. Cet exemple fonctionne uniquement sur les ordinateurs exécutant le système d’exploitation Windows.

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

La `$Signature` variable stocke la signature C# de la `ShowWindowAsync` fonction. Pour vous assurer que la méthode résultante est visible dans une session PowerShell, le `public` mot clé a été ajouté à la signature standard. Pour plus d’informations, consultez [fonction ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync).

La `$ShowWindowAsync` variable stocke l’objet créé par le `Add-Type` paramètre **PassThru** .
L' `Add-Type` applet de commande ajoute la `ShowWindowAsync` fonction à la session PowerShell en tant que méthode statique. La commande utilise le paramètre **MemberDefinition** pour spécifier la définition de méthode enregistrée dans la `$Signature` variable. La commande utilise les paramètres **Name** et **Namespace** pour spécifier le nom et l'espace de noms de la classe. Le paramètre **PassThru** génère un objet qui représente les types.

La nouvelle `ShowWindowAsync` méthode statique est utilisée dans les commandes pour réduire et restaurer la console PowerShell. La méthode accepte deux paramètres : le handle de fenêtre et un entier qui spécifie le mode d’affichage de la fenêtre.

Pour réduire la console PowerShell, `ShowWindowAsync` utilise l' `Get-Process` applet de commande avec la `$PID` variable automatique pour recevoir le processus qui héberge la session PowerShell active. Elle utilise ensuite la propriété **MainWindowHandle** du processus actuel et la valeur `2` , qui représente la `SW_MINIMIZE` valeur.

Pour restaurer la fenêtre, `ShowWindowAsync` utilise la valeur `4` pour la position de la fenêtre, qui représente la `SW_RESTORE` valeur.

Pour agrandir la fenêtre, utilisez la valeur de `3` qui est représentée par `SW_MAXIMIZE` .

## PARAMETERS

### -AssemblyName

Spécifie le nom d'un assembly qui inclut les types. `Add-Type` prend les types de l’assembly spécifié. Ce paramètre est obligatoire lorsque vous créez des types basés sur un nom d’assembly.

Entrez le nom complet ou simple, également appelé « nom partiel », d’un assembly. Les caractères génériques sont autorisés dans le nom de l'assembly. Si vous entrez un nom simple ou partiel, `Add-Type` le résout en nom complet, puis utilise le nom complet pour charger l’assembly.

Ce paramètre n’accepte pas de chemin d’accès ou de nom de fichier. Pour entrer le chemin d’accès au fichier de bibliothèque de liens dynamiques (DLL) de l’assembly, utilisez le paramètre **path** .

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompilerOptions

Spécifie les options du compilateur de code source. Ces options sont envoyées au compilateur sans révision.

Ce paramètre vous permet de demander au compilateur de générer un fichier exécutable, d’incorporer des ressources ou de définir des options de ligne de commande, telles que l' `/unsafe` option.

Vous ne pouvez pas utiliser les paramètres **CompilerOptions** et **ReferencedAssemblies** dans la même commande.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWarnings

Ignore les avertissements du compilateur. Utilisez ce paramètre pour empêcher `Add-Type` de gérer les avertissements du compilateur comme des erreurs.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Langage

Spécifie la langue utilisée dans le code source. La valeur acceptable pour ce paramètre est **CSharp** .

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types. Contrairement à **path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberDefinition

Spécifie les nouvelles propriétés ou méthodes de la classe. `Add-Type` génère le code de modèle qui est requis pour prendre en charge les propriétés ou les méthodes.

Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom de la classe à créer. Ce paramètre est obligatoire durant la génération d'un type à partir d'une définition de membre.

Le nom de type et l'espace de noms doivent être uniques au sein d'une session. Vous ne pouvez pas décharger un type ni le modifier.
Pour modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.
Sinon, la commande échoue.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms

Spécifie un espace de noms pour le type.

Si ce paramètre n’est pas inclus dans la commande, le type est créé dans l’espace de noms **Microsoft. PowerShell. Commands. AddType. AutogeneratedTypes** . Si le paramètre est inclus dans la commande avec une valeur de chaîne vide ou une valeur de `$Null` , le type est généré dans l’espace de noms global.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAssembly

Génère un fichier DLL pour l'assembly ayant le nom spécifié à l'emplacement approprié. Entrez un chemin d’accès et un nom de fichier facultatifs. Les caractères génériques sont autorisés. Par défaut, `Add-Type` génère l’assembly uniquement en mémoire.

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -OutputType

Spécifie le type de sortie de l'assembly de sortie. Par défaut, aucun type de sortie n'est spécifié. Ce paramètre est valide uniquement quand un assembly de sortie est spécifié dans la commande. Pour plus d’informations sur les valeurs, consultez [énumération OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype).

Les valeurs acceptables pour ce paramètre sont les suivantes :

- ConsoleApplication
- Bibliothèque
- Fichier WindowsApplication

> [!IMPORTANT]
> Les `ConsoleApplication` `WindowsApplication` valeurs et ne produisent pas de sortie de travail et ne doivent pas être utilisées.

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet **System.Runtime** qui représente les types ajoutés. Par défaut, cette applet de commande ne génère pas de sortie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.

Si vous envoyez des fichiers de code source, `Add-Type` compile le code dans les fichiers et crée un assembly en mémoire des types. L’extension de fichier spécifiée dans la valeur de **path** détermine le compilateur utilisé par `Add-Type` .

Si vous envoyez un fichier d’assembly, `Add-Type` utilise les types de l’assembly. Pour spécifier un assembly en mémoire ou le Global Assembly Cache, utilisez le paramètre **AssemblyName** .

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferencedAssemblies

Spécifie les assemblys dont dépend le type. Par défaut, `Add-Type` `System.dll` les références et `System.Management.Automation.dll` . Les assemblys que vous spécifiez à l'aide de ce paramètre sont référencés en plus des assemblys par défaut.

À compter de PowerShell 6, **ReferencedAssemblies** n’inclut pas les assemblys .NET par défaut. Vous devez inclure une référence spécifique à celles-ci dans la valeur transmise à ce paramètre.

Vous ne pouvez pas utiliser les paramètres **CompilerOptions** et **ReferencedAssemblies** dans la même commande.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeDefinition

Spécifie le code source qui contient les définitions de type. Entrez le code source dans une chaîne ou une chaîne here-string, ou entrez une variable qui contient le code source. Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).

Incluez une déclaration d'espace de noms dans votre définition de type. Si vous omettez la déclaration d'espace de noms, votre type risque d'avoir le même nom qu'un autre type ou que le raccourci d'un autre type, ce qui entraînera un remplacement involontaire. Par exemple, si vous définissez un type appelé **exception** , les scripts qui utilisent une **exception** comme raccourci pour **System. exception** échoueront.

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UsingNamespace

Spécifie les autres espaces de noms nécessaires pour la classe. C’est très similaire au mot clé C#, `Using` .

Par défaut, `Add-Type` fait référence à l’espace de noms **System** . Lorsque le paramètre **MemberDefinition** est utilisé, `Add-Type` fait également référence à l’espace de noms **System. Runtime. InteropServices** par défaut. Les espaces de noms que vous ajoutez à l'aide du paramètre **UsingNamespace** sont référencés en plus des espaces de noms par défaut.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Add-Type` .

## SORTIES

### None ou System. type

Quand vous utilisez le paramètre **PassThru** , `Add-Type` retourne un objet **System. type** qui représente le nouveau type. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Les types que vous ajoutez existent uniquement dans la session active. Pour utiliser les types dans toutes les sessions, ajoutez-les à votre profil PowerShell. Pour plus d’informations sur le profil, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

Les noms de types et les espaces de noms doivent être uniques au sein d’une session. Vous ne pouvez pas décharger un type ni le modifier. Si vous avez besoin de modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.
Sinon, la commande échoue.

Dans Windows PowerShell (version 5,1 et versions antérieures), vous devez utiliser `Add-Type` pour tout ce qui n’est pas déjà chargé. En règle générale, cela s’applique aux assemblys figurant dans le global assembly cache (GAC).
Dans PowerShell 6 et versions ultérieures, il n’y a aucun GAC, de sorte que PowerShell installe ses propres assemblys dans `$PSHome` .
Ces assemblys sont automatiquement chargés à la demande. il n’est donc pas nécessaire d’utiliser `Add-Type` pour les charger. Toutefois, l’utilisation de `Add-Type` est toujours autorisée pour permettre aux scripts d’être implicitement compatibles avec n’importe quelle version de PowerShell.

Les assemblys dans le GAC peuvent être chargés par nom de type, plutôt que par chemin d’accès. Le chargement d’assemblys à partir d’un chemin d’accès arbitraire requiert `Add-Type` , car ces assemblys ne peuvent pas être chargés automatiquement.

## LIENS CONNEXES

[about_Profiles](../Microsoft.PowerShell.Core/About/about_profiles.md)

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Add-Member](Add-Member.md)

[New-Object](New-Object.md)

[OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[Appel de code non managé (P/Invoke)](/dotnet/standard/native-interop/pinvoke)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
