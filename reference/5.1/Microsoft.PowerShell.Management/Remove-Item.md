---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 18bf42e4378ce561fb24a3c3d5191ebf38a0ea20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203562"
---
# Remove-Item

## SYNOPSIS
Supprime les éléments spécifiés.

## SYNTAX

### Chemin d’accès (par défaut)

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Recurse]
 [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String[]>]
 [<CommonParameters>]
```

### LiteralPath

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Recurse]
 [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String[]>]
 [<CommonParameters>]
```

## Description

L' `Remove-Item` applet de commande supprime un ou plusieurs éléments. Étant donné qu’il est pris en charge par de nombreux fournisseurs, il peut supprimer de nombreux types d’éléments différents, y compris des fichiers, des dossiers, des clés de Registre, des variables, des alias et des fonctions.

## EXEMPLES

### Exemple 1 : supprimer les fichiers qui ont une extension de nom de fichier

Cet exemple supprime tous les fichiers dont le nom contient un point ( `.` ) du `C:\Test` dossier. Étant donné que la commande spécifie un point, la commande ne supprime pas les dossiers ou les fichiers qui n’ont pas d’extension de nom de fichier.

```powershell
Remove-Item C:\Test\*.*
```

### Exemple 2 : supprimer certains fichiers de document dans un dossier

Cet exemple supprime du dossier actif tous les fichiers qui ont une `.doc` extension de nom de fichier et un nom qui n’inclut pas `*1*` .

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

Elle utilise le caractère générique ( `*` ) pour spécifier le contenu du dossier actif. Elle utilise les paramètres **include** et **Exclude** pour spécifier les fichiers à supprimer.

### Exemple 3 : supprimer les fichiers masqués et en lecture seule

Cette commande supprime un fichier qui est à la fois *masqué* et *en lecture seule* .

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

Elle utilise le paramètre **path** pour spécifier le fichier. Elle utilise le paramètre **force** pour la supprimer. Sans **force** , vous ne pouvez pas supprimer les fichiers _cachés_ ou _en lecture seule_ .

### Exemple 4 : supprimer des fichiers dans des sous-dossiers de manière récursive

Cette commande supprime de manière récursive tous les fichiers CSV dans le dossier actif et tous les sous-dossiers.

Étant donné que le paramètre **recurse** dans `Remove-Item` présente un problème connu, la commande de cet exemple utilise `Get-ChildItem` pour obtenir les fichiers souhaités, puis utilise l’opérateur de pipeline pour les passer à `Remove-Item` .

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

Dans la `Get-ChildItem` commande, **path** a la valeur ( `*` ), qui représente le contenu du dossier actif. Elle utilise **include** pour spécifier le type de fichier CSV et utilise **recurse** pour rendre la récupération récursive. Si vous essayez de spécifier le type de fichier, par exemple `-Path *.csv` , l’applet de commande interprète l’objet de la recherche comme étant un fichier qui n’a pas d’élément enfant, et **recurse** échoue.

### Exemple 5 : supprimer les sous-clés de manière récursive

Cette commande supprime la clé de Registre « OldApp » et toutes ses sous-clés et valeurs. Elle utilise `Remove-Item` pour supprimer la clé. Le chemin d’accès est spécifié, mais le nom de paramètre facultatif ( **path** ) est omis.

Le paramètre **recurse** supprime tout le contenu de la clé « OldApp » de manière récursive. Si la clé contient des sous-clés et que vous omettez le paramètre **recurse** , vous êtes invité à confirmer que vous souhaitez supprimer le contenu de la clé.

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### Exemple 6 : suppression de fichiers avec des caractères spéciaux

L’exemple suivant montre comment supprimer des fichiers qui contiennent des caractères spéciaux, tels que des crochets ou des parenthèses.

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### Exemple 7 : supprimer un flux de données de remplacement

Cet exemple montre comment utiliser le paramètre dynamique **Stream** de l' `Remove-Item` applet de commande pour supprimer un autre flux de données. Le paramètre Stream est introduit dans Windows PowerShell 3,0.

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

Le **Stream** paramètre Stream `Get-Item` obtient le flux de **zone. identificateur** du `Copy-Script.ps1` fichier. `Remove-Item` utilise le paramètre **Stream** pour supprimer le flux de **zone. identifier** du fichier. Enfin, l' `Get-Item` applet de commande indique que le flux de **zone. identifier** a été supprimé.

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.
> Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

### -Filter

Spécifie un filtre pour qualifier le paramètre **path** . Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres. Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Force l’applet de commande à supprimer des éléments qui ne peuvent pas être modifiés autrement, tels que des fichiers cachés ou en lecture seule ou des alias ou des variables en lecture seule. L’applet de commande ne peut pas modifier des alias ou variables constants.
L'implémentation est différente d'un fournisseur à l'autre. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md). Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.

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

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` . Les caractères génériques sont autorisés. Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie un chemin d’accès aux éléments en cours de suppression.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Recurse

Indique que cette applet de commande supprime les éléments aux emplacements spécifiés et dans tous les éléments enfants des emplacements.

Lorsqu’il est utilisé avec le paramètre **include** , le paramètre **recurse** peut ne pas supprimer tous les sous-dossiers ou tous les éléments enfants. Il s'agit d'un problème connu. Pour résoudre ce problème, essayez de suivre les résultats de la `Get-ChildItem -Recurse` commande `Remove-Item` , comme décrit dans l’exemple 4 de cette rubrique.

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

### -Stream

Le paramètre **Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Remove-Item` .
Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Vous pouvez utiliser `Remove-Item` pour supprimer un flux de données de remplacement. Elle ne constitue cependant pas un moyen recommandé pour éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d'Internet. Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -UseTransaction

Inclut la commande dans la transaction active.
Ce paramètre est uniquement valide au cours d’une transaction.
Pour plus d’informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande. Pour plus d’informations, consultez les articles suivants :

- [about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

L' `Remove-Item` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

Lorsque vous essayez de supprimer un dossier qui contient des éléments sans utiliser le paramètre **recurse** , l’applet de commande vous invite à confirmer. L’utilisation `-Confirm:$false` de ne supprime pas l’invite. C'est la procédure normale.

## LIENS CONNEXES

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)
