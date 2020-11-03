---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 3ae91d03e6882eeaf6743d11cfeed5d0ed1aae0c
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206121"
---
# Add-Content

## SYNOPSIS
Ajoute le contenu aux éléments spécifiés (ajout de mots à un fichier, par exemple).

## SYNTAX

### Chemin d’accès (par défaut)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
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

Le paramètre **path** spécifie tous les `.txt` fichiers dans le répertoire actif, mais le paramètre **Exclude** ignore les noms de fichiers qui correspondent au modèle spécifié. Le paramètre **value** spécifie la chaîne de texte qui est écrite dans les fichiers.

### Exemple 2 : ajouter une date à la fin des fichiers spécifiés

Cet exemple ajoute la date à des fichiers dans le répertoire actif et affiche la date dans la console PowerShell.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

L' `Add-Content` applet de commande crée deux nouveaux fichiers dans le répertoire actif. Le paramètre **value** contient la sortie de l' `Get-Date` applet de commande. Le paramètre **PassThru** génère le contenu ajouté dans le pipeline.
Étant donné qu’il n’existe aucune autre applet de commande pour recevoir la sortie, elle est affichée dans la console PowerShell.
L' `Get-Content` applet de commande affiche le fichier mis à jour, `DateTimeFile1.log` .

### Exemple 3 : ajouter le contenu d’un fichier spécifié dans un autre fichier

Cet exemple obtient le contenu d’un fichier et stocke le contenu dans une variable. La variable est utilisée pour ajouter le contenu dans un autre fichier.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- L' `Get-Content` applet de commande obtient le contenu de `CopyFromFile.txt` et stocke le contenu dans la `$From` variable.
- L' `Add-Content` applet de commande met à jour le `CopyToFile.txt` fichier à l’aide du contenu de la `$From` variable.
- L' `Get-Content` applet de commande affiche CopyToFile.txt.

### Exemple 4 : ajouter le contenu d’un fichier spécifié à un autre fichier à l’aide du pipeline

Cet exemple obtient le contenu d’un fichier et le dirige vers l' `Add-Content` applet de commande.

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

L' `Get-Content` applet de commande obtient le contenu de `CopyFromFile.txt` . Les résultats sont dirigés vers l’applet de commande `Add-Content` , qui met à jour le `CopyToFile.txt` .
La dernière `Get-Content` applet de commande s’affiche `CopyToFile.txt` .

### Exemple 5 : créer un fichier et copier du contenu

Cet exemple crée un nouveau fichier et copie le contenu d’un fichier existant dans le nouveau fichier.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer un nouveau fichier dans le répertoire actif.
- L' `Get-Content` applet de commande obtient le contenu d’un fichier existant `CopyFromFile.txt` et le passe au paramètre **value** . Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande.
- L' `Get-Content` applet de commande affiche le contenu du nouveau fichier, `NewFile.txt` .

### Exemple 6 : ajouter du contenu à un fichier en lecture seule

Cette commande ajoute une valeur au fichier même si l’attribut de fichier **IsReadOnly** a la valeur **true** .
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
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier `IsReadOnlyTextFile.txt` dans le répertoire actif.
- L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier.
- L' `Get-ChildItem` applet de commande indique que le fichier est vide (0) et possède l’attribut de lecture seule ( `r` ).
- L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier. Le paramètre **value** comprend la chaîne de texte à ajouter au fichier. Le paramètre **force** écrit le texte dans le fichier en lecture seule.
- L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu du fichier.

Pour supprimer l’attribut de lecture seule, utilisez la `Set-ItemProperty` commande avec le paramètre de **valeur** défini sur `False` .

### Exemple 7 : utiliser des filtres avec Add-Content

Vous pouvez spécifier un filtre pour l' `Add-Content` applet de commande. Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.

La commande suivante ajoute le mot « DONE » (terminé) au contenu de tous les `*.txt` fichiers dans le `C:\Temp` répertoire.

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## PARAMETERS

### -AsByteStream

Spécifie que le contenu doit être lu en tant que flux d’octets. Ce paramètre a été introduit dans PowerShell 6,0.

Un avertissement se produit quand vous utilisez le paramètre **AsByteStream** avec le paramètre **Encoding** . Le paramètre **AsByteStream** ignore tout encodage et la sortie est retournée en tant que flux d’octets.

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `utf8NoBOM`.

L’encodage est un paramètre dynamique que le fournisseur FileSystem ajoute à l’applet de commande `Add-Content` . Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `bigendianutf32`: Encode au format UTF-32 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

> [!NOTE]
> **UTF-7** * n’est plus recommandé d’utiliser. Dans PowerShell 7,1, un avertissement est écrit si vous spécifiez `utf7` pour le paramètre **Encoding** .

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
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
Aliases: PSPath, LP

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

Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire.
Les caractères génériques sont autorisés.
Les chemins d'accès doivent être ceux des éléments et non des conteneurs.
Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.
Si vous spécifiez plusieurs chemins d'accès, séparez-les à l'aide de virgules.

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

### System. Object, System. Management. Automation. PSCredential

Vous pouvez diriger des valeurs, des chemins d’accès ou des informations d’identification vers `Set-Content` .

## SORTIES

### Aucune ou System.String

Quand vous utilisez le paramètre **PassThru** , `Add-Content` génère un objet **System. String** qui représente le contenu. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- Quand vous dirigez un objet vers `Add-Content` , l’objet est converti en chaîne avant d’être ajouté à l’élément. Le type d'objet détermine le format de la chaîne, mais le format peut être différent de l'affichage par défaut de l'objet. Pour contrôler le format de la chaîne, utilisez les paramètres de formatage de l'applet de commande d'envoi.
- Vous pouvez également faire référence à `Add-Content` par son alias intégré, `ac` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- L' `Add-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Content](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[New-Item](New-Item.md)

[Set-Content](Set-Content.md)

