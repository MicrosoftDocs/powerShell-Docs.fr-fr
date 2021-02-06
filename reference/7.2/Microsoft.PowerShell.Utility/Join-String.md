---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: f737c8025f9fda3611a44177bd19e928f596d0aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597747"
---
# Join-String

## SYNOPSIS
Combine des objets du pipeline en une chaîne unique.

## SYNTAXE

### Valeur par défaut (par défaut)

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### SingleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### DoubleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### Format

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## Description

L' `Join-String` applet de commande joint, ou combine, le texte des objets de pipeline dans une chaîne unique.

Si aucun paramètre n’est spécifié, les objets de pipeline sont convertis en une chaîne et joints au séparateur par défaut `$OFS` .

En spécifiant un nom de propriété, la valeur de la propriété est convertie en une chaîne et jointe à une chaîne.

Au lieu d’un nom de propriété, un bloc de script peut être utilisé. Le résultat du bloc de script est converti en chaîne avant d’être joint pour former le résultat. Il peut soit combiner le texte de la propriété d’un objet, soit le résultat de l’objet qui a été converti en chaîne.

Cette applet de commande a été introduite dans PowerShell 6,2.

## EXEMPLES

### Exemple 1 : joindre des noms de répertoires

<!-- markdownlint-disable MD038 -->
Cet exemple joint des noms de répertoires, encapsule la sortie entre des guillemets doubles et sépare les noms de répertoires par une virgule et un espace ( `, ` ). La sortie est un objet String.

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

`Get-ChildItem` utilise le paramètre **Directory** pour obtenir tous les noms de répertoires du `C:\` lecteur.
Les objets sont envoyés dans le pipeline à `Join-String` . Le paramètre **Property** spécifie les noms de répertoire. Le paramètre **DoubleQuote** encapsule les noms de répertoires avec des guillemets doubles.
Le paramètre **separator** spécifie d’utiliser une virgule et un espace ( `, ` ) pour séparer les noms de répertoire.

Les `Get-ChildItem` objets sont **System. IO. DirectoryInfo** et `Join-String` convertissent les objets en **System. String**.

### Exemple 2 : utiliser une sous-chaîne de propriété pour joindre des noms de répertoire

Cet exemple utilise une méthode de sous-chaîne pour obtenir les quatre premières lettres des noms de répertoires, encapsule la sortie en guillemets simples et sépare les noms de répertoires par un point-virgule ( `;` ).

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

`Get-ChildItem` utilise le paramètre **Directory** pour obtenir tous les noms de répertoires du `C:\` lecteur.
Les objets sont envoyés dans le pipeline à `Join-String` .

Le bloc de script de paramètre de **propriété** utilise la variable automatique ( `$_` ) pour spécifier la propriété **Name** de chaque objet SUBSTRING. La sous-chaîne obtient les quatre premières lettres de chaque nom de répertoire. La sous-chaîne spécifie les positions de début et de fin des caractères. Le paramètre **SingleQuote** encapsule les noms de répertoires avec des guillemets simples. Le paramètre **separator** spécifie l’utilisation d’un point-virgule ( `;` ) pour séparer les noms de répertoire.

Pour plus d’informations sur les variables automatiques et les sous-chaînes, consultez [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) et [SUBSTRING](/dotnet/api/system.string.substring).

### Exemple 3 : afficher la sortie de jointure sur une ligne distincte

Cet exemple joint des noms de service à chaque service sur une ligne distincte et mis en retrait par un onglet.

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

`Get-Service` utilise le paramètre **Name** avec pour spécifier les services qui commencent par `se*` . L’astérisque ( `*` ) est un caractère générique pour n’importe quel caractère.

Les objets sont envoyés dans le pipeline à `Join-String` qui utilise le paramètre **Property** pour spécifier les noms de service. Le paramètre **separator** spécifie trois caractères spéciaux qui représentent un retour chariot ( `` `r `` ), un saut de ligne ( `` `n `` ) et un onglet ( `` `t `` ). Le **OutputPrefix** insère une étiquette **services :** avec une nouvelle ligne et un nouvel onglet avant la première ligne de la sortie.

Pour plus d’informations sur les caractères spéciaux, consultez [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).

### Exemple 4 : créer une définition de classe à partir d’un objet

Cet exemple génère une définition de classe PowerShell en utilisant un objet existant comme modèle.

Cet exemple de code utilise la projection pour réduire la longueur de ligne et améliorer la lisibilité. Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## PARAMETERS

### -DoubleQuote

Encapsule la valeur de chaîne de chaque objet de pipeline entre guillemets doubles.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatString

Chaîne de format qui spécifie la façon dont chaque élément doit être mis en forme.

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie le texte à joindre. Entrez une variable qui contient le texte, ou tapez une commande ou une expression qui obtient les objets à joindre aux chaînes.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputPrefix

Texte inséré avant la chaîne de sortie. La chaîne peut contenir des caractères spéciaux tels que les retours chariot ( `` `r `` ), les sauts de ligne ( `` `n `` ) et les tabulations ( `` `t `` ).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputSuffix

Texte ajouté à la chaîne de sortie. La chaîne peut contenir des caractères spéciaux tels que les retours chariot ( `` `r `` ), les sauts de ligne ( `` `n `` ) et les tabulations ( `` `t `` ).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Nom d’une propriété, ou expression de propriété, qui projetera l’objet de pipeline en texte.

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Séparateur

Texte ou caractères tels qu’une virgule ou un point-virgule inséré entre le texte de chaque objet de pipeline.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SingleQuote

Encapsule la valeur de chaîne de chaque objet de pipeline entre guillemets simples.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément. Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

## SORTIES

### System.String

## REMARQUES

## LIENS CONNEXES

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)

[Sous-chaîne](/dotnet/api/system.string.substring)

