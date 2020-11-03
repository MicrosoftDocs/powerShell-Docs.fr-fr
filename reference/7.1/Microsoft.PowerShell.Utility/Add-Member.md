---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 1c07d79af1516becff86a0706906fa6ddfe03ab8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205217"
---
# Add-Member

## SYNOPSIS
Ajoute des propriétés et des méthodes personnalisées à une instance d’un objet PowerShell.

## SYNTAX

### TypeNameSet (par défaut)

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### NotePropertyMultiMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### NotePropertySingleMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### PEL

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## Description

L' `Add-Member` applet de commande vous permet d’ajouter des membres (propriétés et méthodes) à une instance d’un objet PowerShell. Par exemple, vous pouvez ajouter un membre NoteProperty qui contient une description de l’objet ou un membre **ScriptMethod** qui exécute un script pour modifier l’objet.

Pour utiliser `Add-Member` , redirigez l’objet vers `Add-Member` ou utilisez le paramètre **InputObject** pour spécifier l’objet.

Le paramètre **MemberType** indique le type de membre que vous souhaitez ajouter. Le paramètre **Name** attribue un nom au nouveau membre et le paramètre **value** définit la valeur du membre.

Les propriétés et méthodes que vous ajoutez le sont uniquement à l'instance spécifique de l'objet spécifié. `Add-Member` ne modifie pas le type de l’objet. Pour créer un nouveau type d’objet, utilisez l’applet de commande `Add-Type` .

Vous pouvez également utiliser l' `Export-Clixml` applet de commande pour enregistrer l’instance de l’objet, y compris les membres supplémentaires, dans un fichier. Vous pouvez ensuite utiliser l' `Import-Clixml` applet de commande pour recréer l’instance de l’objet à partir des informations stockées dans le fichier exporté.

À compter de Windows PowerShell 3,0, `Add-Member` dispose de nouvelles fonctionnalités qui facilitent l’ajout de propriétés de note aux objets.
Vous pouvez utiliser les paramètres **NotePropertyName** et **NotePropertyValue** pour définir une propriété de note ou le paramètre **NotePropertyMembers** , qui utilise une table de hachage des noms et valeurs des propriétés de note.

Par ailleurs, à compter de Windows PowerShell 3.0, le paramètre **PassThru** , qui génère un objet de sortie, est moins utile. `Add-Member` Ajoute désormais les nouveaux membres directement à l’objet d’entrée de plus de types. Pour plus d'informations, consultez la description du paramètre **PassThru** .

## EXEMPLES

### Exemple 1 : ajouter une propriété de note à un PSObject

L’exemple suivant ajoute une propriété de note **Status** avec la valeur « Done » à l’objet **FileInfo** qui représente le `Test.txt` fichier.

La première commande utilise l' `Get-ChildItem` applet de commande pour obtenir un objet **FileInfo** représentant le `Test.txt` fichier. Elle l’enregistre dans la `$a` variable.

La deuxième commande ajoute la propriété de note à l’objet dans `$a` .

La troisième commande utilise la notation par points pour récupérer la valeur de la propriété **Status** de l’objet dans `$a` . Comme le montre la sortie, la valeur est « done ».

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### Exemple 2 : ajouter une propriété d’alias à un PSObject

L’exemple suivant ajoute une propriété d’alias de **taille** à l’objet qui représente le `Test.txt` fichier. La nouvelle propriété est un alias de la propriété **Length** .

La première commande utilise l' `Get-ChildItem` applet de commande pour récupérer l' `Test.txt` objet **FileInfo** .

La deuxième commande ajoute la propriété **Size** alias.
La troisième commande utilise la notation par points pour récupérer la valeur de la nouvelle propriété **Size** .

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### Exemple 3 : ajouter une propriété de note StringUse à une chaîne

Cet exemple ajoute la propriété de note **StringUse** à une chaîne.
Étant donné que `Add-Member` ne peut pas ajouter de types aux objets d’entrée de **chaîne** , vous pouvez spécifier le paramètre **PassThru** pour générer un objet de sortie. La dernière commande de l'exemple affiche la nouvelle propriété.

Cet exemple utilise le paramètre **NotePropertyMembers** . La valeur du paramètre **NotePropertyMembers** est une table de hachage. La clé est le nom de la propriété de note, **StringUse** , et la valeur est la valeur de la propriété de note, **Display** .

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### Exemple 4 : ajouter une méthode de script à un objet FileInfo

Cet exemple ajoute la méthode de script **SizeInMB** à un objet **FileInfo** qui calcule la taille du fichier au mégaoctet le plus proche. La deuxième commande crée un **scriptblock** qui utilise la méthode statique **Round** du `[math]` type pour arrondir la taille du fichier à la deuxième décimale.

Le paramètre de **valeur** utilise également la `$This` variable automatique, qui représente l’objet actuel. La `$This` variable est valide uniquement dans les blocs de script qui définissent de nouvelles propriétés et méthodes.

La dernière commande utilise la notation par points pour appeler la nouvelle méthode de script **SizeInMB** sur l’objet dans la `$A` variable.

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### Exemple 5 : copier toutes les propriétés d’un objet vers un autre

Cette fonction copie toutes les propriétés d'un objet dans un autre objet.

La `foreach` boucle utilise l' `Get-Member` applet de commande pour récupérer chacune des propriétés de l’objet **from** . Les commandes de la `foreach` boucle sont exécutées en série sur chacune des propriétés.

La `Add-Member` commande ajoute la propriété de l’objet **from** à l’objet **to** en tant **que NoteProperty** . La valeur est copiée à l’aide du paramètre **value** . Elle utilise le paramètre **force** pour ajouter des membres avec le même nom de membre.

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### Exemple 6 : créer un objet personnalisé

Cet exemple crée un objet personnalisé de **ressource** .

L' `New-Object` applet de commande crée un **PSObject** . L’exemple enregistre le **PSObject** dans la `$Asset` variable.

La deuxième commande utilise l' `[ordered]` accélérateur de type pour créer un dictionnaire ordonné de noms et de valeurs. La commande enregistre le résultat dans la `$D` variable.

La troisième commande utilise le paramètre **NotePropertyMembers** de l' `Add-Member` applet de commande pour ajouter le dictionnaire dans la `$D` variable au **PSObject** .
La propriété **TypeName** assigne un nouveau nom, **Asset** , au **PSObject** .

La dernière commande envoie le nouvel objet **Asset** à l' `Get-Member` applet de commande. La sortie indique que l’objet a un nom de type de **ressource** et les propriétés de note que nous avons définies dans le dictionnaire trié.

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## PARAMETERS

### -Force

Indique que cette applet de commande ajoute un nouveau membre même si l’objet a un membre personnalisé portant le même nom.
Vous ne pouvez pas utiliser le paramètre **force** pour remplacer un membre standard d’un type.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l'objet auquel le nouveau membre est ajouté.
Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

Spécifie le type du membre à ajouter.
Ce paramètre est obligatoire.
Les valeurs valides pour ce paramètre sont :

- NoteProperty
- AliasProperty
- ScriptProperty
- CodeProperty
- ScriptMethod
- CodeMethod

Pour plus d’informations sur ces valeurs, consultez [PSMemberTypes, énumération](/dotnet/api/system.management.automation.psmembertypes) dans MSDN Library.

Certains objets n'ont pas chaque type de membre.
Si vous spécifiez un type de membre que l’objet n’a pas, PowerShell retourne une erreur.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom du membre que cette applet de commande ajoute.

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyMembers

Spécifie une table de hachage ou un dictionnaire ordonné de valeurs et de noms de la propriété de note.
Tapez une table de hachage ou un dictionnaire dans lequel les clés sont les noms des propriétés de note et les valeurs sont celles des propriétés de note.

Pour plus d’informations sur les tables de hachage et les dictionnaires ordonnés dans PowerShell, consultez [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyName

Spécifie le nom de la propriété de note.

Utilisez ce paramètre avec le paramètre **NotePropertyValue** .
Ce paramètre est facultatif.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyValue

Spécifie la valeur de la propriété de note.

Utilisez ce paramètre avec le paramètre **NotePropertyName** .
Ce paramètre est facultatif.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez.
Par défaut, cette applet de commande ne génère aucun résultat.

Pour la plupart des objets, `Add-Member` ajoute les nouveaux membres à l’objet d’entrée.
Toutefois, lorsque l’objet d’entrée est une chaîne, `Add-Member` ne peut pas ajouter le membre à l’objet d’entrée.
Pour ces objets, utilisez le paramètre **PassThru** pour créer un objet de sortie.

Dans Windows PowerShell 2,0, les `Add-Member` membres ont été ajoutés uniquement au wrapper **PSObject** d’objets, et non à l’objet.
Utilisez le paramètre **PassThru** pour créer un objet de sortie pour tout objet ayant un wrapper **PSObject** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

Spécifie des informations supplémentaires facultatives sur les membres **AliasProperty** , **ScriptProperty** , **CodeProperty** ou **CodeMethod** .

S’il est utilisé lors de l’ajout d’un **AliasProperty** , ce paramètre doit être un type de données.
Une conversion vers le type de données spécifié est ajoutée à la valeur de **AliasProperty** .

Par exemple, si vous ajoutez un **AliasProperty** qui fournit un autre nom pour une propriété de type chaîne, vous pouvez également spécifier un paramètre **SecondValue** de **System. Int32** pour indiquer que la valeur de cette propriété de chaîne doit être convertie en entier quand vous y accédez à l’aide du **AliasProperty** correspondant.

Vous pouvez utiliser le paramètre **SecondValue** pour spécifier un **scriptblock** supplémentaire lors de l’ajout d’un membre **ScriptProperty** . Le premier **scriptblock** , spécifié dans le paramètre **value** , est utilisé pour obtenir la valeur d’une variable. Le deuxième **scriptblock** , spécifié dans le paramètre **SecondValue** , est utilisé pour définir la valeur d’une variable.

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

Spécifie la valeur initiale du membre ajouté.
Si vous ajoutez un membre **AliasProperty** , **CodeProperty** , **ScriptProperty** ou **CodeMethod** , vous pouvez fournir des informations supplémentaires facultatives à l’aide du paramètre **SecondValue** .

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Spécifie un nom pour le type.

Quand le type est une classe dans l’espace de noms **système** ou un type qui a un accélérateur de type, vous pouvez entrer le nom abrégé du type. Sinon, le nom de type complet est obligatoire.
Ce paramètre est effectif uniquement lorsque l' **InputObject** est un **PSObject** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger tout type d’objet vers cette applet de commande.

## SORTIES

### None ou System. Object

Quand vous utilisez le paramètre **PassThru** , cette applet de commande retourne l’objet qui vient d’être étendu.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Vous pouvez ajouter des membres uniquement aux objets **PSObject** . Pour déterminer si un objet est un objet **PSObject** , utilisez l' `-is` opérateur.

Par exemple, pour tester un objet stocké dans la `$obj` variable, tapez `$obj -is [PSObject]` .

Les noms des paramètres **MemberType** , **Name** , **value** et **SecondValue** sont facultatifs.
Si vous omettez les noms de paramètres, les valeurs des paramètres sans nom doivent apparaître dans cet ordre : **MemberType** , **Name** , **value** et **SecondValue** .

Si vous incluez les noms de paramètres, les paramètres peuvent apparaître dans tout ordre.

Vous pouvez utiliser la `$this` variable Automatic dans des blocs de script qui définissent les valeurs des nouvelles propriétés et méthodes.
La `$this` variable fait référence à l’instance de l’objet auquel les propriétés et les méthodes sont ajoutées. Pour plus d’informations sur la `$this` variable, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

## LIENS CONNEXES

[Export-Clixml](Export-Clixml.md)

[Get-Member](Get-Member.md)

[Import-Clixml](Import-Clixml.md)

[New-Object](New-Object.md)

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

