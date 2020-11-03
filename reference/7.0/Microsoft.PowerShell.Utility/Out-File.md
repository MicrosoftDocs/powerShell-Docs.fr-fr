---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: e7437505bbe5fbbcfb38e9957f75ac45287d9b26
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206306"
---
# Out-File

## SYNOPSIS
Envoie la sortie vers un fichier.

## SYNTAX

### ByPath (par défaut)

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Out-File` applet de commande envoie la sortie vers un fichier. Il utilise implicitement le système de mise en forme de PowerShell pour écrire dans le fichier. Le fichier reçoit la même représentation d’affichage que le terminal. Cela signifie que la sortie peut ne pas être idéale pour le traitement par programme, sauf si tous les objets d’entrée sont des chaînes.
Lorsque vous devez spécifier des paramètres pour la sortie, utilisez `Out-File` plutôt que l’opérateur de redirection ( `>` ). Pour plus d’informations sur la redirection, consultez [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).

## EXEMPLES

### Exemple 1 : envoyer une sortie et créer un fichier

Cet exemple montre comment envoyer une liste des processus de l’ordinateur local à un fichier. Si le fichier n’existe pas, `Out-File` crée le fichier dans le chemin d’accès spécifié.

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local. Les objets **processus** sont envoyés dans le pipeline à l’applet de commande `Out-File` . `Out-File` utilise le paramètre **filePath** et crée un fichier dans le répertoire actif nommé **Process.txt** . La `Get-Content` commande obtient le contenu du fichier et l’affiche dans la console PowerShell.

### Exemple 2 : empêcher le remplacement d’un fichier existant

Cet exemple empêche le remplacement d’un fichier existant. Par défaut, `Out-File` remplace les fichiers existants.

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local. Les objets **processus** sont envoyés dans le pipeline à l’applet de commande `Out-File` . `Out-File` utilise le paramètre **filePath** et tente d’écrire dans un fichier dans le répertoire actif nommé **Process.txt** . Le paramètre **NoClobber** empêche le fichier d’être remplacé et affiche un message indiquant que le fichier existe déjà.

### Exemple 3 : envoyer la sortie vers un fichier au format ASCII

Cet exemple montre comment encoder une sortie avec un type d’encodage spécifique.

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local. Les objets **processus** sont stockés dans la variable, `$Procs` . `Out-File` utilise le paramètre **filePath** et crée un fichier dans le répertoire actif nommé **Process.txt** . Le paramètre **InputObject** passe les objets de processus dans `$Procs` au fichier **Process.txt** . Le paramètre **Encoding** convertit la sortie au format **ASCII** . Le paramètre **Width** limite chaque ligne du fichier à 50 caractères, de sorte que certaines données peuvent être tronquées.

### Exemple 4 : utiliser un fournisseur et envoyer une sortie vers un fichier

Cet exemple montre comment utiliser l' `Out-File` applet de commande lorsque vous n’êtes pas dans un lecteur du fournisseur **FileSystem** . Utilisez l' `Get-PSProvider` applet de commande pour afficher les fournisseurs sur votre ordinateur local. Pour plus d'informations, consultez [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

La `Set-Location` commande utilise le paramètre **path** pour définir l’emplacement actuel sur le fournisseur Registry `Alias:` . L' `Get-Location` applet de commande affiche le chemin d’accès complet de `Alias:` .
`Get-ChildItem` envoie des objets dans le pipeline à l’applet de commande `Out-File` . `Out-File` utilise le paramètre **filePath** pour spécifier le chemin d’accès complet et le nom de fichier de la sortie, **C:\TestDir\AliasNames.txt** . L' `Get-Content` applet de commande utilise le paramètre **path** et affiche le contenu du fichier dans la console PowerShell.

## PARAMETERS

### -Append

Ajoute la sortie à la fin d’un fichier existant.

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

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `utf8NoBOM`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie le chemin d'accès au fichier de sortie.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Remplace l’attribut de lecture seule et remplace un fichier en lecture seule existant. Le paramètre **force** ne remplace pas les restrictions de sécurité.

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

### -InputObject

Spécifie les objets à écrire dans le fichier. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès au fichier de sortie. Le paramètre **LiteralPath** est utilisé exactement tel qu’il est tapé.
Les caractères génériques ne sont pas acceptés. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement. Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoClobber

**NoClobber** empêche le remplacement d’un fichier existant et affiche un message indiquant que le fichier existe déjà. Par défaut, si un fichier existe dans le chemin d’accès spécifié, `Out-File` remplace le fichier sans avertissement.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

Spécifie que le contenu écrit dans le fichier ne se termine pas par un caractère de saut de ligne. Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie. Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie. Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.

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

### -Largeur

Spécifie le nombre de caractères dans chaque ligne de la sortie. Tous les caractères supplémentaires sont tronqués, pas renvoyés à la ligne. Si ce paramètre n’est pas utilisé, la largeur est déterminée par les caractéristiques de l’hôte. La valeur par défaut de la console PowerShell est de 80 caractères.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

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

Vous pouvez diriger n’importe quel objet vers `Out-File` .

## SORTIES

### Aucun

`Out-File` ne génère pas de sortie.

## REMARQUES

Les objets d’entrée sont mis en forme automatiquement comme ils le seraient dans le terminal, mais vous pouvez utiliser une `Format-*` applet de commande pour contrôler explicitement la mise en forme de la sortie dans le fichier. Par exemple : `Get-Date | Format-List | Out-File out.txt`

Pour envoyer la sortie d’une commande PowerShell à l’applet de commande `Out-File` , utilisez le pipeline. Vous pouvez également stocker les données dans une variable et utiliser le paramètre **InputObject** pour passer des données à l' `Out-File` applet de commande.

`Out-File` enregistre les données dans un fichier, mais ne produit pas d’objets de sortie dans le pipeline.

## LIENS CONNEXES

[about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-String](Out-String.md)

[Tee-Object](Tee-Object.md)
