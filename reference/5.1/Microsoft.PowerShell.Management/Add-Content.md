---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204093"
---
# Add-Content

## SYNOPSIS
Ajoute le contenu aux éléments spécifiés (ajout de mots à un fichier, par exemple).

## SYNTAX

### Chemin d’accès (par défaut)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## Description

L' `Add-Content` applet de commande ajoute du contenu à un élément ou un fichier spécifié. Vous pouvez spécifier le contenu en le tapant dans la commande ou en spécifiant un objet renfermant le contenu.

Si vous avez besoin de créer des fichiers ou des répertoires pour les exemples suivants, consultez [New-Item](New-Item.md).

## EXEMPLES

### Exemple 1 : ajouter une chaîne à tous les fichiers texte à l’aide d’une exception

Cet exemple ajoute une valeur aux fichiers texte dans le répertoire actif, mais exclut les fichiers en fonction de leur nom de fichier.

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier tous les fichiers. txt dans le répertoire actif. Le paramètre **Exclude** ignore les noms de fichiers qui correspondent au modèle spécifié. Le paramètre **value** spécifie la chaîne de texte qui est écrite dans les fichiers.

Utilisez la valeur [obtenir-content](Get-Content.md) pour afficher le contenu de ces fichiers.

### Exemple 2 : ajouter une date à la fin des fichiers spécifiés

Cet exemple ajoute la date à des fichiers dans le répertoire actif et affiche la date dans la console PowerShell.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer deux nouveaux fichiers dans le répertoire actif. Le paramètre **value** spécifie l' `Get-Date` applet de commande pour récupérer la date et la transmet à `Add-Content` . L' `Add-Content` applet de commande écrit la date dans chaque fichier. Le paramètre **PassThru** passe un objet qui représente l’objet date. Étant donné qu’il n’existe aucune autre applet de commande pour recevoir l’objet passé, il est affiché dans la console PowerShell. L' `Get-Content` applet de commande affiche le fichier mis à jour, DateTimeFile1. log.

### Exemple 3 : ajouter le contenu d’un fichier spécifié dans un autre fichier

Cet exemple obtient le contenu d’un fichier et ajoute ce contenu dans un autre fichier.

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le nouveau fichier dans le répertoire actif, CopyToFile.txt. Le paramètre **value** utilise l' `Get-Content` applet de commande pour récupérer le contenu du fichier, CopyFromFile.txt. Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande. Le paramètre de **valeur** est passé à `Add-Content` . L' `Add-Content` applet de commande ajoute les données au fichier CopyToFile.txt. L' `Get-Content` applet de commande affiche le fichier mis à jour, CopyToFile.txt.

### Exemple 4 : utiliser une variable pour ajouter le contenu d’un fichier spécifié dans un autre fichier

Cet exemple obtient le contenu d’un fichier et stocke le contenu dans une variable. La variable est utilisée pour ajouter le contenu dans un autre fichier.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

L' `Get-Content` applet de commande obtient le contenu de CopyFromFile.txt et stocke le contenu dans la `$From` variable. L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier CopyToFile.txt dans le répertoire actif. Le paramètre de **valeur** utilise la `$From` variable et passe le contenu à `Add-Content` . L' `Add-Content` applet de commande met à jour le fichier CopyToFile.txt. L' `Get-Content` applet de commande affiche CopyToFile.txt.

### Exemple 5 : créer un fichier et copier du contenu

Cet exemple crée un nouveau fichier et copie le contenu d’un fichier existant dans le nouveau fichier.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer un nouveau fichier dans le répertoire actif. Le paramètre **value** utilise l' `Get-Content` applet de commande pour récupérer le contenu d’un fichier existant, CopyFromFile.txt. Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande. Le paramètre **value** passe le contenu vers `Add-Content` lequel met à jour le fichier NewFile.txt. L' `Get-Content` applet de commande affiche le contenu du nouveau fichier, NewFile.txt.

### Exemple 6 : ajouter du contenu à un fichier en lecture seule

Cette commande ajoute la valeur au fichier même si l’attribut de fichier **IsReadOnly** a la valeur true.
Les étapes de création d’un fichier en lecture seule sont incluses dans l’exemple.

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier IsReadOnlyTextFile.txt dans le répertoire actif. L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier. L' `Get-ChildItem` applet de commande indique que le fichier est vide (0) et possède l’attribut de lecture seule ( `r` ). L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier. Le paramètre **value** comprend la chaîne de texte à ajouter au fichier. Le paramètre **force** écrit le texte dans le fichier en lecture seule. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu du fichier.

Pour supprimer l’attribut de lecture seule, utilisez la `Set-ItemProperty` commande avec le paramètre de **valeur** défini sur `False` .

## PARAMETERS

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

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

> [!WARNING]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `Default`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `Ascii` Utilise le jeu de caractères ASCII (7 bits).
- `BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `BigEndianUTF32` Utilise UTF-32 avec l’ordre des octets de poids fort (Big-endian).
- `Byte` Encode un jeu de caractères en une séquence d’octets.
- `Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).
- `Oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.
- `String` Identique au **format Unicode** .
- `Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `Unknown` Identique au **format Unicode** .
- `UTF7` Utilise UTF-7.
- `UTF8` Utilise UTF-8.
- `UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).

L’encodage est un paramètre dynamique que le fournisseur FileSystem ajoute à l’applet de commande `Add-Content` . Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

Omet les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que **\* . txt** . Les caractères génériques sont autorisés.

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

Spécifie un filtre dans le format ou le langage du fournisseur. La valeur de ce paramètre qualifie le paramètre **Path** . La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur. Les **filtres** sont plus efficaces que les autres paramètres, car le fournisseur applique des filtres lorsque les objets sont récupérés. Dans le cas contraire, PowerShell traite les filtres une fois les objets récupérés.

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

Remplace l'attribut de lecture seule pour que vous puissiez ajouter le contenu à un fichier en lecture seule. Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.

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

### -Include

Ajoute uniquement les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que **\* . txt** . Les caractères génériques sont autorisés.

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

Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire. Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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

### -NoNewline

Indique que cette applet de commande n’ajoute pas de nouvelle ligne ou de retour chariot au contenu.

Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie. Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie. Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.

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

### -PassThru

Retourne un objet qui représente le contenu ajouté. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Path

Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire. Les caractères génériques sont autorisés. Si vous spécifiez plusieurs chemins d'accès, séparez-les à l'aide de virgules.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

Spécifie un flux de données alternatif pour le contenu. Si le flux n’existe pas, cette applet de commande le crée. Les caractères génériques ne sont pas pris en charge.

**Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Add-Content` . Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Vous pouvez utiliser l' `Add-Content` applet de commande pour modifier le contenu du flux de données de remplacement de la **zone. identifier** . Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet. Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction

Inclut la commande dans la transaction active. Ce paramètre est uniquement valide au cours d’une transaction. Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

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

### -Value

Spécifie le contenu à ajouter. Tapez une chaîne entre guillemets, telle que **ces données sont destinées à un usage interne uniquement** , ou spécifiez un objet qui contient du contenu, tel que l’objet **DateTime** `Get-Date` généré par.

Vous ne pouvez pas spécifier le contenu d’un fichier en tapant son chemin d’accès, car il s’agit simplement d’une chaîne.
Vous pouvez utiliser une `Get-Content` commande pour obtenir le contenu et le passer au paramètre **value** .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Object, System. Management. Automation. PSCredential

Vous pouvez diriger des valeurs, des chemins d’accès ou des informations d’identification vers `Set-Content` .

## SORTIES

### Aucune ou System.String

Quand vous utilisez le paramètre **PassThru** , `Add-Content` génère un objet **System. String** qui représente le contenu. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Quand vous dirigez un objet vers `Add-Content` , l’objet est converti en chaîne avant d’être ajouté à l’élément. Le type d'objet détermine le format de la chaîne, mais le format peut être différent de l'affichage par défaut de l'objet. Pour contrôler le format de la chaîne, utilisez les paramètres de formatage de l'applet de commande d'envoi.

Vous pouvez également faire référence à `Add-Content` par son alias intégré, `ac` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

L' `Add-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[Clear-Content](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[New-Item](New-Item.md)

[Set-Content](Set-Content.md)
