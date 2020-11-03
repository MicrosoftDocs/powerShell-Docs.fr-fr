---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 95601a4f5f42700c4de7d6ad721ee898b22bab84
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206106"
---
# Select-String

## SYNOPSIS
Recherche du texte dans des chaînes et des fichiers.

## SYNTAX

### Fichier (par défaut)

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### Object

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFile

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

## Description

L' `Select-String` applet de commande recherche des modèles de texte et de texte dans les chaînes et les fichiers d’entrée. Vous pouvez utiliser `Select-String` similaire à **grep** dans UNIX ou **findstr.exe** dans Windows.

`Select-String` est basé sur des lignes de texte. Par défaut, `Select-String` recherche la première correspondance dans chaque ligne et, pour chaque correspondance, elle affiche le nom du fichier, le numéro de ligne et tout le texte de la ligne contenant la correspondance. Vous pouvez vous demander `Select-String` de Rechercher plusieurs correspondances par ligne, d’afficher du texte avant et après la correspondance, ou d’afficher une valeur booléenne (true ou false) qui indique si une correspondance est trouvée.

`Select-String` utilise la correspondance d’expression régulière, mais elle peut également effectuer une correspondance qui recherche le texte que vous spécifiez dans l’entrée.

`Select-String` peut afficher toutes les correspondances de texte ou les arrêter après la première correspondance dans chaque fichier d’entrée.
`Select-String` peut être utilisé pour afficher tout le texte qui ne correspond pas au modèle spécifié.

Vous pouvez également spécifier que `Select-String` doit attendre un encodage de caractères particulier, par exemple lors de la recherche de fichiers de texte Unicode. `Select-String` utilise la marque d’ordre d’octet (BOM) pour détecter le format d’encodage du fichier. Si le fichier n’a pas de nomenclature, il suppose que l’encodage est UTF8.

## EXEMPLES

### Exemple 1 : Rechercher une correspondance respectant la casse

Cet exemple fait une correspondance sensible à la casse du texte qui a été envoyé dans le pipeline à l’applet de commande `Select-String` .

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

Les chaînes de texte **Hello** et **Hello** sont envoyées par le pipeline à l’applet de commande `Select-String` .
`Select-String` utilise le paramètre **pattern** pour spécifier **Hello** . Le paramètre **CaseSensitive** spécifie que le cas doit correspondre uniquement au modèle majuscule. **SimpleMatch** est un paramètre facultatif qui spécifie que la chaîne dans le modèle n’est pas interprétée comme une expression régulière.
`Select-String` affiche **Hello** dans la console PowerShell.

### Exemple 2 : Rechercher des correspondances dans des fichiers texte

Cette commande effectue une recherche dans tous les fichiers avec l' `.txt` extension de nom de fichier dans le répertoire actif. La sortie affiche les lignes dans les fichiers qui incluent la chaîne spécifiée.

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

Dans cet exemple, `Get-Alias` et `Get-Command` sont utilisés avec l' `Out-File` applet de commande pour créer deux fichiers texte dans le répertoire actif, **Alias.txt** et **Command.txt** .

`Select-String` utilise le paramètre **path** avec le `*` caractère générique astérisque () pour rechercher dans tous les fichiers du répertoire actif l’extension de nom de fichier `.txt` . Le paramètre **pattern** spécifie le texte à mettre en correspondance avec la fonction **obtient-** . `Select-String` affiche la sortie dans la console PowerShell. Le nom de fichier et le numéro de ligne précèdent chaque ligne de contenu qui contient une correspondance pour le paramètre de **modèle** .

### Exemple 3 : Rechercher une correspondance de modèle

Dans cet exemple, plusieurs fichiers sont recherchés pour trouver des correspondances pour le modèle spécifié. Le modèle utilise un quantificateur d’expression régulière. Pour plus d’informations, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

L' `Select-String` applet de commande utilise deux paramètres, **path** et **pattern** . Le paramètre **path** utilise la variable `$PSHOME` qui spécifie le répertoire PowerShell. Le reste du chemin d’accès comprend le sous-répertoire en **-US** et spécifie chaque `*.txt` fichier dans le répertoire. Le paramètre **pattern** spécifie de faire correspondre un point d’interrogation ( `?` ) dans chaque fichier. Une barre oblique inverse ( `\` ) est utilisée comme caractère d’échappement et est nécessaire parce que le point d’interrogation ( `?` ) est un quantificateur d’expression régulière. `Select-String` affiche la sortie dans la console PowerShell. Le nom de fichier et le numéro de ligne précèdent chaque ligne de contenu qui contient une correspondance pour le paramètre de **modèle** .

### Exemple 4 : utiliser Select-String dans une fonction

Cet exemple crée une fonction pour rechercher un modèle dans les fichiers d’aide PowerShell. Pour cet exemple, la fonction existe uniquement dans la session PowerShell. Une fois la session PowerShell fermée, la fonction est supprimée. Pour plus d’informations, consultez [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:2:   about_ActivityCommonParameters
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:31:  see about_WorkflowCommonParameters.
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:33:  about_CommonParameters.
```

La fonction est créée sur la ligne de commande PowerShell. La `Function` commande utilise le nom **Search-Help** . Appuyez sur **entrée** pour commencer à ajouter des instructions à la fonction. À partir de l' `>>` invite, ajoutez chaque instruction et appuyez sur **entrée** comme indiqué dans l’exemple. Une fois le crochet fermant ajouté, vous êtes redirigé vers une invite PowerShell.

La fonction contient deux commandes. La `$PSHelp` variable stocke le chemin d’accès aux fichiers d’aide PowerShell. `$PSHOME` est le répertoire d’installation de PowerShell avec le sous **-répertoire en-US** qui spécifie chaque `*.txt` fichier dans le répertoire.

La `Select-String` commande dans la fonction utilise les paramètres **path** et **pattern** . Le paramètre **path** utilise la `$PSHelp` variable pour récupérer le chemin d’accès. Le paramètre **pattern** utilise la chaîne **about_** comme critère de recherche.

Pour exécuter la fonction, tapez `Search-Help` . La commande de la fonction `Select-String` affiche la sortie dans la console PowerShell.

### Exemple 5 : Rechercher une chaîne dans un journal des événements Windows

Cet exemple recherche une chaîne dans un journal des événements Windows. La variable `$_` représente l’objet actuel dans le pipeline. Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

L' `Get-WinEvent` applet de commande utilise le paramètre **logname** pour spécifier le journal des applications. Le paramètre **MaxEvents** obtient les événements les plus récents 50 du journal. Le contenu du journal est stocké dans la variable nommée `$Events` .

La `$Events` variable est envoyée dans le pipeline à l’applet de commande `Select-String` . `Select-String` utilise le paramètre **InputObject** . La `$_` variable représente l’objet actuel et `message` est une propriété de l’événement. Le paramètre de **modèle** importe **la chaîne et** recherche des correspondances dans `$_.message` . `Select-String` affiche la sortie dans la console PowerShell.

### Exemple 6 : Rechercher une chaîne dans les sous-répertoires

Cet exemple recherche une chaîne de texte spécifique dans un répertoire et tous ses sous-répertoires.

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

`Get-ChildItem` utilise le paramètre **path** pour spécifier **C:\Windows\System32 \* . txt** . Le paramètre **recurse** comprend les sous-répertoires. Les objets sont envoyés dans le pipeline à `Select-String` .

`Select-String` utilise le paramètre **pattern** et spécifie la chaîne **Microsoft** . Le paramètre **CaseSensitive** est utilisé pour faire correspondre la casse exacte de la chaîne. `Select-String` affiche la sortie dans la console PowerShell.

> [!NOTE]
> Selon vos autorisations, vous pouvez voir des messages d' **accès refusé** dans la sortie.

### Exemple 7 : Rechercher des chaînes qui ne correspondent pas à un modèle

Cet exemple montre comment exclure des lignes de données qui ne correspondent pas à un modèle.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

L' `Get-Command` applet de commande envoie des objets dans le pipeline au `Out-File` pour créer le fichier **Command.txt** dans le répertoire actif. `Select-String` utilise le paramètre **path** pour spécifier le fichier **Command.txt** . Le paramètre **pattern** spécifie la **valeur** **obtenue** et définie comme modèle de recherche. Le paramètre **NotMatch** exclut les résultats de l' **extraction** et de la **définition** .
`Select-String` affiche la sortie dans la console PowerShell qui n’inclut pas l' **extraction** ou la **définition** .

### Exemple 8 : Rechercher des lignes avant et après une correspondance

Cet exemple montre comment récupérer les lignes avant et après le modèle correspondant.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:1186:Cmdlet          Get-CmsMessage            3.0.0.0    Microsoft.PowerShell.Security
  Command.txt:1187:Cmdlet          Get-Command               3.0.0.0    Microsoft.PowerShell.Core
> Command.txt:1188:Cmdlet          Get-ComputerInfo          3.1.0.0    Microsoft.PowerShell.Management
> Command.txt:1189:Cmdlet          Get-ComputerRestorePoint  3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1190:Cmdlet          Get-Content               3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1191:Cmdlet          Get-ControlPanelItem      3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1192:Cmdlet          Get-Counter               3.0.0.0    Microsoft.PowerShell.Diagnostics
```

L' `Get-Command` applet de commande envoie des objets dans le pipeline au `Out-File` pour créer le fichier **Command.txt** dans le répertoire actif. `Select-String` utilise le paramètre **path** pour spécifier le fichier **Command.txt** . Le paramètre **pattern** spécifie le modèle de recherche **« -Computer »** . Le paramètre **Context** utilise deux valeurs, avant et après, et marque les correspondances de modèle dans la sortie avec un chevron ( `>` ). Le paramètre **Context** génère les deux lignes avant le premier Matching pattern et trois lignes après le dernier modèle match.

### Exemple 9 : Rechercher toutes les correspondances de modèle

Cet exemple montre comment le paramètre **AllMatches** recherche chaque correspondance de modèle dans une ligne de texte. Par défaut, `Select-String` recherche uniquement la première occurrence d’un modèle dans une ligne de texte. Cet exemple utilise des propriétés d’objet qui se trouvent dans l’applet de commande `Get-Member` .

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:5:    Describes the parameters that Windows PowerShell
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:9:    Windows PowerShell Workflow adds the activity common

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

2073

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

2200
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** . Le paramètre **path** utilise la variable `$PSHOME` qui spécifie le répertoire PowerShell. Le reste du chemin d’accès comprend le sous-répertoire en **-US** et spécifie chaque `*.txt` fichier dans le répertoire. Les `Get-ChildItem` objets sont stockés dans la `$A` variable. La `$A` variable est envoyée dans le pipeline à l’applet de commande `Select-String` . `Select-String` utilise le paramètre **pattern** pour rechercher la chaîne **PowerShell** dans chaque fichier.

À partir de la ligne de commande PowerShell, le contenu de la `$A` variable est affiché. Il y a une ligne qui contient deux occurrences de la chaîne **PowerShell** .

La `$A.Matches` propriété répertorie la première occurrence du modèle **PowerShell** sur chaque ligne.

La `$A.Matches.Length` propriété compte la première occurrence du modèle **PowerShell** sur chaque ligne.

La `$B` variable utilise les mêmes `Get-ChildItem` applets de commande et `Select-String` , mais ajoute le paramètre **AllMatches** . **AllMatches** recherche chaque occurrence du modèle **PowerShell** sur chaque ligne. Les objets stockés dans les `$A` `$B` variables et sont identiques.

La `$B.Matches.Length` propriété augmente, car pour chaque ligne, chaque occurrence du modèle **PowerShell** est comptée.

## PARAMETERS

### -AllMatches

Indique que l’applet de commande recherche plusieurs correspondances dans chaque ligne de texte. Sans ce paramètre, `Select-String` recherche uniquement la première correspondance dans chaque ligne de texte.

Lorsque `Select-String` trouve plusieurs correspondances dans une ligne de texte, il n’émet toujours qu’un seul objet **MatchInfo** pour la ligne, mais la propriété **matches** de l’objet contient toutes les correspondances.

> [!NOTE]
> Ce paramètre est ignoré lorsqu’il est utilisé en association avec le paramètre **SimpleMatch** . Si vous souhaitez retourner toutes les correspondances et que le modèle que vous recherchez contient des caractères d’expression régulière, vous devez placer ces caractères dans une séquence d’échappement plutôt que d’utiliser **SimpleMatch** . Pour plus d’informations sur les expressions régulières d’échappement, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) .

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

### -CaseSensitive

Indique que l’applet de commande correspond à la casse. Par défaut, les correspondances ne respectent pas la casse.

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

### -Context

Capture le nombre spécifié de lignes avant et après la ligne qui correspond au modèle.

Si vous entrez un nombre comme valeur de ce paramètre, ce nombre détermine le nombre de lignes capturées avant et après la correspondance. Si vous entrez deux nombres comme valeur, le premier nombre détermine le nombre de lignes avant la correspondance, et le deuxième nombre détermine le nombre de lignes après la correspondance. Par exemple : `-Context 2,3`.

Dans l’affichage par défaut, les lignes avec une correspondance sont indiquées par un crochet angulaire à droite ( `>` ) (ASCII 62) dans la première colonne de l’affichage. Les lignes non marquées constituent le contexte.

Le paramètre de **contexte** ne change pas le nombre d’objets générés par `Select-String` .
`Select-String` génère un objet [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) pour chaque correspondance. Le contexte est stocké sous la forme d’un tableau de chaînes dans la propriété de **contexte** de l’objet.

Quand la sortie d’une `Select-String` commande est envoyée au pipeline vers une autre `Select-String` commande, la commande réceptrice recherche uniquement le texte dans la ligne correspondante. La ligne mise en correspondance correspond à la valeur de la propriété **line** de l’objet **MatchInfo** , et non au texte des lignes de contexte. Par conséquent, le paramètre de **contexte** n’est pas valide dans la commande de réception `Select-String` .

Lorsque le contexte comprend une correspondance, l’objet **MatchInfo** pour chaque correspondance comprend toutes les lignes de contexte, mais les lignes qui se chevauchent n’apparaissent qu’une seule fois dans l’affichage.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `default`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii` Utilise le jeu de caractères ASCII (7 bits).
- `bigendianunicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).
- `oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.
- `unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7` Utilise UTF-7.
- `utf8` Utilise UTF-8.
- `utf32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

Exclure les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Inclut les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

Spécifie le texte à rechercher. Entrez une variable contenant le texte, ou tapez une commande ou une expression qui obtient le texte.

L’utilisation du paramètre **InputObject** n’est pas identique à l’envoi de chaînes vers le pipeline dans le pipeline `Select-String` .

Lorsque vous dirigez plusieurs chaînes vers l’applet de commande `Select-String` , celle-ci recherche le texte spécifié dans chaque chaîne et retourne chaque chaîne qui contient le texte recherché.

Quand vous utilisez le paramètre **InputObject** pour envoyer une collection de chaînes, `Select-String` traite la collection comme une chaîne combinée unique. `Select-String` retourne les chaînes en tant qu’unité si le texte recherché est trouvé dans une chaîne.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -List

Seule la première instance du texte correspondant est retournée à partir de chaque fichier d’entrée. Il s’agit de la méthode la plus efficace pour récupérer une liste de fichiers dont le contenu correspond à l’expression régulière.

Par défaut, `Select-String` retourne un objet **MatchInfo** pour chaque correspondance trouvée.

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

Spécifie le chemin d'accès aux fichiers où effectuer la recherche. La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement. Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NotMatch

Le paramètre **NotMatch** recherche le texte qui ne correspond pas au modèle spécifié.

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

Spécifie le chemin d’accès aux fichiers à rechercher. Les caractères génériques sont autorisés. L'emplacement par défaut est le répertoire local.

Spécifiez les fichiers dans le répertoire, tels que `log1.txt` , `*.doc` ou `*.*` . Si vous spécifiez seulement un répertoire, la commande échoue.

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Modèle

Spécifie le texte à rechercher sur chaque ligne. La valeur de modèle est traitée comme une expression régulière.

Pour en savoir plus sur les expressions régulières, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

Indique que l’applet de commande retourne une valeur booléenne (true ou false) au lieu d’un objet **MatchInfo** . La valeur est true si le modèle est trouvé ; Sinon, la valeur est false.

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

### -SimpleMatch

Indique que l’applet de commande utilise une correspondance simple plutôt qu’une correspondance d’expression régulière. Dans une correspondance simple, `Select-String` recherche l’entrée pour le texte dans le paramètre **pattern** . Elle n’interprète pas la valeur du paramètre **pattern** comme une instruction d’expression régulière.

En outre, quand **SimpleMatch** est utilisé, la propriété **matches** de l’objet **MatchInfo** retourné est vide.

> [!NOTE]
> Lorsque ce paramètre est utilisé avec le paramètre **AllMatches** , le **AllMatches** est ignoré.

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

Vous pouvez diriger n’importe quel objet ayant une méthode **ToString** vers `Select-String` .

## SORTIES

### Microsoft. PowerShell. Commands. MatchInfo ou System. Boolean

Par défaut, la sortie est un ensemble d’objets **MatchInfo** avec un objet pour chaque correspondance trouvée. Si vous utilisez le paramètre **Quiet** , la sortie est une valeur booléenne indiquant si le modèle a été trouvé.

## REMARQUES

`Select-String` est similaire à **grep** dans UNIX ou **findstr.exe** dans Windows.

L’alias **SLS** pour l' `Select-String` applet de commande a été introduit dans PowerShell 3,0.

> [!NOTE]
> Selon les [verbes approuvés pour les commandes PowerShell](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), le préfixe d’alias officiel pour les `Select-*` applets de commande est `sc` , et non `sl` . Par conséquent, l’alias approprié pour `Select-String` doit être `scs` , et non `sls` . Il s’agit d’une exception à cette règle.

Pour utiliser `Select-String` , tapez le texte que vous souhaitez rechercher comme valeur du paramètre **pattern** . Pour spécifier le texte à rechercher, utilisez les critères suivants :

- Tapez le texte dans une chaîne entre guillemets, puis dirigez-le vers `Select-String` .
- Stockez une chaîne de texte dans une variable, puis spécifiez la variable comme valeur du paramètre **InputObject** .
- Si le texte est stocké dans des fichiers, utilisez le paramètre **path** pour spécifier le chemin d’accès aux fichiers.

Par défaut, `Select-String` interprète la valeur du paramètre **pattern** comme une expression régulière. Pour plus d’informations, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md). Vous pouvez utiliser le paramètre **SimpleMatch** pour remplacer la correspondance d’expression régulière. Le paramètre **SimpleMatch** recherche des instances de la valeur du paramètre **pattern** dans l’entrée.

La sortie par défaut de `Select-String` est un objet **MatchInfo** , qui contient des informations détaillées sur les correspondances. Les informations contenues dans l’objet sont utiles quand vous recherchez du texte dans des fichiers, car les objets **MatchInfo** ont des propriétés telles que **filename** et **line** . Lorsque l’entrée ne provient pas du fichier, la valeur de ces paramètres est **InputStream** .

Si vous n’avez pas besoin des informations contenues dans l’objet **MatchInfo** , utilisez le paramètre **Quiet** . Le paramètre **Quiet** retourne une valeur booléenne (true ou false) pour indiquer s’il a trouvé une correspondance, au lieu d’un objet **MatchInfo** .

Lors `Select-String` de la correspondance d’expressions, utilise la culture actuelle définie pour le système. Pour trouver la culture actuelle, utilisez l' `Get-Culture` applet de commande.

Pour rechercher les propriétés d’un objet **MatchInfo** , tapez la commande suivante :

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## LIENS CONNEXES

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[Get-Alias](Get-Alias.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-Command](../Microsoft.PowerShell.Core/Get-Command.md)

[Get-Member](Get-Member.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Out-File](Out-File.md)
