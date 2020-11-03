---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 796d510a1f7fd9bd7206e313dd23409fd8b2de1d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202474"
---
# Compress-Archive

## SYNOPSIS
Crée une archive compressée, ou un fichier compressé, à partir des fichiers et répertoires spécifiés.

## SYNTAX

### Chemin d’accès (par défaut)

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithUpdate

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithForce

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithUpdate

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithForce

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Compress-Archive` applet de commande crée un fichier d’archive compressé ou compressé à partir d’un ou de plusieurs fichiers ou répertoires spécifiés. Une archive empaquette plusieurs fichiers, avec compression facultative, dans un seul fichier zippé pour faciliter la distribution et le stockage. Un fichier d’archive peut être compressé à l’aide de l’algorithme de compression spécifié par le paramètre **CompressionLevel** .

L' `Compress-Archive` applet de commande utilise l’API Microsoft .NET [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) pour compresser les fichiers.
La taille de fichier maximale est de 2 Go, car il existe une limitation de l’API sous-jacente.

Certains exemples utilisent la projection pour réduire la longueur de ligne des exemples de code. Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

## EXEMPLES

### Exemple 1 : compresser des fichiers pour créer un fichier d’archive

Cet exemple compresse les fichiers de différents répertoires et crée un fichier d’archive. Un caractère générique est utilisé pour obtenir tous les fichiers avec une extension de fichier particulière. Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

Le paramètre **path** accepte des noms de fichiers et des noms de fichiers spécifiques avec des caractères génériques, `*.vsd` . Le **chemin d’accès** utilise une liste séparée par des virgules pour obtenir les fichiers de différents répertoires. Le niveau de compression est **plus rapide** pour réduire le temps de traitement. Le paramètre **DestinationPath** spécifie l’emplacement du `Draft.zip` fichier. Le `Draft.zip` fichier contient `Draftdoc.docx` et tous les fichiers avec une `.vsd` extension.

### Exemple 2 : compresser des fichiers à l’aide d’un LiteralPath

Cet exemple compresse des fichiers nommés spécifiques et crée un nouveau fichier d’archive. Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

Le chemin d’accès absolu et les noms de fichiers sont utilisés, car le paramètre **LiteralPath** n’accepte pas les caractères génériques. Le **chemin d’accès** utilise une liste séparée par des virgules pour obtenir les fichiers de différents répertoires. Le niveau de compression est **plus rapide** pour réduire le temps de traitement. Le paramètre **DestinationPath** spécifie l’emplacement du `Draft.zip` fichier. Le `Draft.zip` fichier contient uniquement `Draftdoc.docx` et `diagram2.vsd` .

### Exemple 3 : compresser un répertoire qui comprend le répertoire racine

Cet exemple compresse un répertoire et crée un fichier d’archive qui **comprend** le répertoire racine, ainsi que tous ses fichiers et sous-répertoires. Le fichier d’archive a une structure de répertoires, car le **chemin d’accès** spécifie un répertoire racine.

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` . Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive. L' `Draft.zip` archive comprend le `Reference` répertoire racine, ainsi que tous ses fichiers et sous-répertoires.

### Exemple 4 : compresser un répertoire qui exclut le répertoire racine

Cet exemple compresse un répertoire et crée un fichier d’archive qui **exclut** le répertoire racine, car le **chemin d’accès** utilise un `*` caractère générique astérisque (). L’archive contient une structure de répertoires qui contient les fichiers et les sous-répertoires du répertoire racine.

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` avec un `*` caractère générique astérisque (). Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive. L' `Draft.zip` archive contient les fichiers et les sous-répertoires du répertoire racine. Le `Reference` répertoire racine est exclu de l’archive.

### Exemple 5 : compresser uniquement les fichiers dans un répertoire racine

Cet exemple compresse uniquement les fichiers dans un répertoire racine et crée un fichier d’archive. Il n’existe aucune structure de répertoires dans l’archive, car seuls les fichiers sont compressés.

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` avec un caractère générique en **étoile-point-étoile** ( `*.*` ). Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive. L' `Draft.zip` archive contient uniquement les `Reference` fichiers du répertoire racine et le répertoire racine est exclu.

### Exemple 6 : utilisation du pipeline pour archiver des fichiers

Cet exemple envoie des fichiers vers le dessous du pipeline pour créer une archive. Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

`Get-ChildItem` utilise le paramètre **path** pour spécifier deux fichiers de répertoires différents. Chaque fichier est représenté par un objet **FileInfo** et est envoyé dans le pipeline à `Compress-Archive` .
Les deux fichiers spécifiés sont archivés dans `PipelineFiles.zip` .

### Exemple 7 : utiliser le pipeline pour archiver un répertoire

Cet exemple envoie un répertoire dans le pipeline pour créer une archive. Les fichiers sont envoyés en tant qu’objets et répertoires **FileInfo** en tant qu’objets **DirectoryInfo** . La structure de répertoires de l’archive n’inclut pas le répertoire racine, mais ses fichiers et sous-répertoires sont inclus dans l’archive.

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

`Get-ChildItem` utilise le paramètre **path** pour spécifier le `C:\LogFiles` répertoire racine. Chaque objet **FileInfo** et **DirectoryInfo** est envoyé vers le pipeline.

`Compress-Archive` Ajoute chaque objet à l' `PipelineDir.zip` archive. Le paramètre **path** n’est pas spécifié, car les objets de pipeline sont reçus dans la position de paramètre 0.

### Exemple 8 : comment la récursivité peut affecter les Archives

Cet exemple montre comment la récursivité peut dupliquer des fichiers dans votre archive. Par exemple, si vous utilisez `Get-ChildItem` avec le paramètre **recurse** . En tant que processus de récursivité, chaque objet **FileInfo** et **DirectoryInfo** est envoyé vers le pipeline et ajouté à l’archive.

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

Le `C:\TestLog` Répertoire ne contient aucun fichier. Elle contient un sous-répertoire nommé `testsub` qui contient le `testlog.txt` fichier.

`Get-ChildItem` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\TestLog` . Le paramètre **recurse** traite les fichiers et les répertoires. Un objet **DirectoryInfo** est créé pour `testsub` et un objet **FileInfo** `testlog.txt` .

Chaque objet est envoyé dans le pipeline à `Compress-Archive` . Le **DestinationPath** spécifie l’emplacement du fichier d’archive. Le paramètre **path** n’est pas spécifié, car les objets de pipeline sont reçus dans la position de paramètre 0.

Le résumé suivant décrit le `PipelineRecurse.zip` contenu de l’archive qui contient un fichier dupliqué :

- L’objet **DirectoryInfo** crée le `testsub` répertoire et contient le `testlog.txt` fichier, qui reflète la structure de répertoire d’origine.
- L’objet **FileInfo** crée un doublon `testlog.txt` dans la racine de l’archive. Le fichier dupliqué est créé, car la récursivité a envoyé un objet de fichier à `Compress-Archive` . Ce comportement est normal, car chaque objet envoyé dans le pipeline est ajouté à l’archive.

### Exemple 9 : mettre à jour un fichier d’archive existant

Cet exemple met à jour un fichier d’archive existant, `Draft.Zip` , dans le `C:\Archives` répertoire. Dans cet exemple, le fichier d’archive existant contient le répertoire racine, ainsi que ses fichiers et sous-répertoires.

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

La commande est mise à jour `Draft.Zip` avec des versions plus récentes des fichiers existants dans le `C:\Reference` répertoire et ses sous-répertoires. De plus, les nouveaux fichiers qui ont été ajoutés à `C:\Reference` ou à ses sous-répertoires sont inclus dans l’archive mise à jour `Draft.Zip` .

## PARAMETERS

### -CompressionLevel

Spécifie la quantité de compression à appliquer lors de la création du fichier d’archive. La compression plus rapide nécessite moins de temps pour créer le fichier, mais peut entraîner des tailles de fichier supérieures.

Si ce paramètre n’est pas spécifié, la commande utilise la valeur par défaut, **optimale** .

Les valeurs acceptables pour ce paramètre sont les suivantes :

- **Plus rapide** . Utilisez la méthode de compression la plus rapide disponible pour réduire le temps de traitement. Une compression plus rapide peut entraîner des tailles de fichier supérieures.
- **NoCompression** . Ne compresse pas les fichiers sources.
- **Optimal** . Le temps de traitement dépend de la taille du fichier.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
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

### -DestinationPath

Ce paramètre est obligatoire et spécifie le chemin d’accès au fichier de sortie d’archive. Le **DestinationPath** doit inclure le nom du fichier zippé et le chemin d’accès absolu ou relatif au fichier compressé.

Si le nom de fichier dans **DestinationPath** n’a pas d’extension de nom de fichier `.zip` , l’applet de commande ajoute l' `.zip` extension de nom de fichier.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le ou les chemins d’accès aux fichiers que vous souhaitez ajouter au fichier compressé d’archive. Contrairement au paramètre **path** , la valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès comprend des caractères d’échappement, mettez chaque caractère d’échappement entre des guillemets simples pour indiquer à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.
Pour spécifier plusieurs chemins d’accès et inclure des fichiers dans plusieurs emplacements de votre fichier compressé de sortie, utilisez des virgules pour séparer les chemins d’accès.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le ou les chemins d’accès aux fichiers que vous souhaitez ajouter au fichier compressé d’archive. Pour spécifier plusieurs chemins d’accès et inclure des fichiers dans plusieurs emplacements, utilisez des virgules pour séparer les chemins d’accès.

Ce paramètre accepte les caractères génériques. Les caractères génériques vous permettent d’ajouter tous les fichiers d’un répertoire à votre fichier d’archive.

L’utilisation de caractères génériques avec un répertoire racine affecte le contenu de l’archive :

- Pour créer une archive qui **comprend** le répertoire racine, ainsi que tous ses fichiers et sous-répertoires, spécifiez le répertoire racine dans le **chemin** sans caractères génériques. Par exemple : `-Path C:\Reference`
- Pour créer une archive qui **exclut** le répertoire racine, mais compresse tous ses fichiers et sous-répertoires, utilisez le `*` caractère générique astérisque (). Par exemple : `-Path C:\Reference\*`
- Pour créer une archive qui compresse uniquement les fichiers dans le répertoire racine, utilisez le caractère générique **étoile-point-étoile** ( `*.*` ). Les sous-répertoires de la racine ne sont pas inclus dans l’archive. Par exemple : `-Path C:\Reference\*.*`

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Mise à jour

Met à jour l’archive spécifiée en remplaçant les anciennes versions de fichiers de l’Archive par des versions de fichier plus récentes portant le même nom. Vous pouvez également ajouter ce paramètre pour ajouter des fichiers à une archive existante.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
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

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers un ou plusieurs fichiers.

## SORTIES

### Aucun

## REMARQUES

L’utilisation de la récursivité et l’envoi d’objets dans le pipeline peuvent dupliquer des fichiers dans votre archive. Par exemple, si vous utilisez `Get-ChildItem` avec le paramètre **recurse** , chaque objet **FileInfo** et **DirectoryInfo** qui est envoyé vers le pipeline est ajouté à l’archive.

La [spécification du fichier zip](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ne spécifie pas de méthode standard d’encodage des noms de fichiers qui contiennent des caractères non-ASCII. L' `Compress-Archive` applet de commande utilise l’encodage UTF-8. D’autres outils d’archive ZIP peuvent utiliser un schéma d’encodage différent. Lorsque vous extrayez des fichiers dont les noms de fichiers ne sont pas stockés à l’aide de l’encodage UTF-8, `Expand-Archive` utilise la valeur brute trouvée dans l’archive. Cela peut entraîner un nom de fichier différent du nom de fichier source stocké dans l’archive.

## LIENS CONNEXES

[Expand-Archive](Expand-Archive.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)
