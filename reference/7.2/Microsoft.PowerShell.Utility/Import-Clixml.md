---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 3658ea5eded0fed95a1c9a1ea6e7d84a557e1e36
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597357"
---
# Import-Clixml

## SYNOPSIS
Importe un fichier CLIXML et crée des objets correspondants dans PowerShell.

## SYNTAXE

### ByPath (par défaut)

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### ByLiteralPath

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## Description

L' `Import-Clixml` applet de commande importe un fichier XML Common Language Infrastructure (CLI) avec des données qui représentent Microsoft .net objets Framework et crée les objets PowerShell. Pour plus d’informations sur l’interface CLI, consultez [indépendance du langage](/dotnet/standard/language-independence).

Une utilisation intéressante de `Import-Clixml` sur les ordinateurs Windows consiste à importer des informations d’identification et des chaînes sécurisées exportées en XML sécurisé à l’aide de `Export-Clixml` . Pour obtenir un exemple, consultez l’exemple 2.

`Import-Clixml` utilise la marque d’ordre d’octet (BOM) pour détecter le format d’encodage du fichier. Si le fichier n’a pas de nomenclature, il suppose que l’encodage est UTF8.

## EXEMPLES

### Exemple 1 : importer un fichier sérialisé et recréer un objet

Cet exemple utilise l' `Export-Clixml` applet de commande pour enregistrer une copie sérialisée des informations de processus retournées par `Get-Process` . `Import-Clixml` Récupère le contenu du fichier sérialisé et recrée un objet qui est stocké dans la `$Processes` variable.

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### Exemple 2 : importer un objet d’informations d’identification sécurisé

Dans cet exemple, étant donné les informations d’identification que vous avez stockées dans la `$Credential` variable en exécutant l' `Get-Credential` applet de commande, vous pouvez exécuter l' `Export-Clixml` applet de commande pour enregistrer les informations d’identification sur le disque.

> [!IMPORTANT]
> `Export-Clixml` exporte uniquement les informations d’identification chiffrées sur Windows. Sur les systèmes d’exploitation autres que Windows, tels que macOS et Linux, les informations d’identification sont exportées en texte brut.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

L' `Export-Clixml` applet de commande chiffre les objets d’informations d’identification à l’aide de l' [API de protection des données](/previous-versions/windows/apps/hh464970(v=win.10))Windows.
Le chiffrement garantit que seul votre compte d’utilisateur peut déchiffrer le contenu de l’objet d’informations d’identification. Le `CLIXML` fichier exporté ne peut pas être utilisé sur un autre ordinateur ou un autre utilisateur.

Dans l’exemple, le fichier dans lequel les informations d’identification sont stockées est représenté par `TestScript.ps1.credential` . Remplacez **TestScript** par le nom du script avec lequel vous chargez les informations d’identification.

Vous envoyez l’objet d’informations d’identification dans le pipeline à `Export-Clixml` et l’enregistrez dans le chemin d’accès, `$Credxmlpath` , que vous avez spécifié dans la première commande.

Pour importer automatiquement les informations d’identification dans votre script, exécutez les deux commandes finales. Exécutez `Import-Clixml` pour importer l’objet d’informations d’identification sécurisé dans votre script. Cette importation élimine le risque d’exposer les mots de passe en texte brut dans votre script.

## PARAMETERS

### -First

Obtient uniquement le nombre d’objets spécifié. Entrez le nombre d’objets à obtenir.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTotalCount

Indique le nombre total d’objets dans le jeu de données, suivis des objets sélectionnés. Si l’applet de commande ne peut pas déterminer le nombre total, elle affiche le **nombre total inconnu**. L’entier possède une propriété **Accuracy** qui indique la fiabilité de la valeur du nombre total. La valeur des plages de **précision** allant de `0.0` à `1.0` où `0.0` signifie que l’applet de commande n’a pas pu compter les objets, `1.0` signifie que le nombre est exact et une valeur comprise entre `0.0` et `1.0` indique une estimation de plus en plus fiable.

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

### -LiteralPath

Spécifie le chemin d’accès aux fichiers XML. Contrairement à **path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès aux fichiers XML.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Ignorer

Ignore le nombre spécifié d’objets, puis obtient les objets restants. Entrez le nombre d’objets à ignorer.

```yaml
Type: System.UInt64
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

### System.String

Vous pouvez canaliser une chaîne qui contient un chemin d’accès à `Import-Clixml` .

## SORTIES

### PSObject

`Import-Clixml` retourne les objets qui ont été désérialisés à partir des fichiers XML stockés.

## REMARQUES

Quand vous spécifiez plusieurs valeurs pour un paramètre, séparez-les par des virgules. Par exemple, `<parameter-name> <value1>, <value2>`.

## LIENS CONNEXES

[Export-Clixml](Export-Clixml.md)

[Introduction à la sérialisation XML](/dotnet/standard/serialization/introducing-xml-serialization)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[Stocker en toute sécurité les informations d’identification sur le disque](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[Utiliser PowerShell pour transmettre des informations d’identification à des systèmes hérités](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

