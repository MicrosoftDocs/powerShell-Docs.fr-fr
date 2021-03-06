---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 67d9f351b8ef4936dcb4e9cff6583da0f464bc12
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "99598993"
---
# Get-Item

## SYNOPSIS
Obtient l'élément à l'emplacement spécifié.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### LiteralPath

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## Description

L' `Get-Item` applet de commande obtient l’élément à l’emplacement spécifié. Elle n’obtient pas le contenu de l’élément à l’emplacement, sauf si vous utilisez un caractère générique ( `*` ) pour demander tout le contenu de l’élément.

Cette applet de commande est utilisée par les fournisseurs PowerShell pour parcourir différents types de magasins de données.

## EXEMPLES

### Exemple 1 : récupérer le répertoire actif

Cet exemple obtient le répertoire actif. Le point ('. ') représente l’élément à l’emplacement actuel (et non son contenu).

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### Exemple 2 : récupération de tous les éléments dans le répertoire actif

Cet exemple obtient tous les éléments du répertoire actif. Le caractère générique ( `*` ) représente tout le contenu de l’élément actuel.

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### Exemple 3 : obtenir le répertoire actif d’un lecteur

Cet exemple obtient le répertoire actif du `C:` lecteur. L’objet récupéré représente uniquement le répertoire, pas son contenu.

```powershell
Get-Item C:\
```

### Exemple 4 : récupérer des éléments dans le lecteur spécifié

Cet exemple obtient les éléments du `C:` lecteur. Le caractère générique ( `*` ) représente tous les éléments dans le conteneur, et pas seulement le conteneur.

```powershell
Get-Item C:\*
```

Dans PowerShell, utilisez un seul astérisque ( `*` ) pour obtenir le contenu, plutôt que le traditionnel `*.*` . Le format est interprété littéralement. par conséquent, n' `*.*` extrayez pas les répertoires ou les noms de fichiers sans point.

### Exemple 5 : obtenir une propriété dans le répertoire spécifié

Cet exemple obtient la propriété **LastAccessTime** du `C:\Windows` répertoire. **LastAccessTime** n’est qu’une des propriétés des répertoires du système de fichiers. Pour afficher toutes les propriétés d’un répertoire, tapez `(Get-Item <directory-name>) | Get-Member` .

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### Exemple 6 : afficher le contenu d’une clé de Registre

Cet exemple montre le contenu de la clé de Registre **Microsoft. PowerShell** . Vous pouvez utiliser cette applet de commande avec le fournisseur de Registre PowerShell pour récupérer les clés et les sous-clés de Registre, mais vous devez utiliser l' `Get-ItemProperty` applet de commande pour récupérer les valeurs et les données du Registre.

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### Exemple 7 : obtenir des éléments dans un répertoire qui ont une exclusion

Cet exemple obtient les éléments du répertoire Windows dont les noms incluent un point ( `.` ), mais ne commencent pas par `w*` . Cet exemple fonctionne uniquement lorsque le chemin d’accès contient un caractère générique ( `*` ) pour spécifier le contenu de l’élément.

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### Exemple 8 : obtention d’informations hardlink

Dans PowerShell 6,2, une autre vue a été ajoutée pour obtenir les informations de liaison permanente. Pour récupérer les informations hardlink, dirigez la sortie vers `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### Exemple 9 : sortie pour les systèmes d’exploitation autres que Windows

Dans PowerShell 7,1 sur les systèmes UNIX, l’applet de commande `Get-Item` fournit une sortie de type UNIX :

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

Les nouvelles propriétés qui font désormais partie de la sortie sont les suivantes :

- **UnixMode** est l’autorisation de fichier représentée sur un système UNIX
- L' **utilisateur** est le propriétaire du fichier
- Le **groupe** est le propriétaire du groupe
- **Taille** correspond à la taille du fichier ou du répertoire tel qu’il est représenté sur un système UNIX.

> [!NOTE]
> Cette fonctionnalité a été déplacée de expérimental vers standard dans PowerShell 7,1.

## PARAMETERS

### -Stream

> [!NOTE]
> Ce paramètre est uniquement disponible sur Windows.

Obtient le flux de données alternatif spécifié à partir du fichier. Entrez le nom du flux. Les caractères génériques sont pris en charge. Pour récupérer tous les flux, utilisez un astérisque ( `*` ). Ce paramètre est valide sur les répertoires, mais notez que les répertoires n’ont pas de flux de données par défaut.

Ce paramètre a été introduit dans PowerShell 3,0.  À compter de PowerShell 7,2, `Get-Item` peut recevoir des flux de données alternatifs de répertoires et de fichiers.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

Spécifie un filtre pour qualifier le paramètre **path** . Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge les filtres. Les filtres sont plus efficaces que les autres paramètres. Le fournisseur applique le filtre lorsque l’applet de commande obtient les objets au lieu d’avoir PowerShell de filtrer les objets une fois qu’ils sont récupérés. La chaîne de filtrage est transmise à l’API .NET pour énumérer les fichiers. L’API prend en charge uniquement les `*` `?` caractères génériques et.

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

Indique que cette applet de commande obtient des éléments qui ne sont pas accessibles autrement, tels que des éléments masqués.
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

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

### -Path

Spécifie le chemin d’accès à un élément. Cette applet de commande obtient l’élément à l’emplacement spécifié. Les caractères génériques sont autorisés. Ce paramètre est obligatoire, mais le **chemin d’accès** au nom de paramètre est facultatif.

Utilisez un point ( `.` ) pour spécifier l’emplacement actuel. Utilisez le caractère générique ( `*` ) pour spécifier tous les éléments à l’emplacement actuel.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### System.Object

Cette applet de commande retourne les objets qu’elle obtient. Le type est déterminé par le type d’objets dans le chemin d’accès.

## REMARQUES

Cette applet de commande n’a pas de paramètre **recurse** , car elle obtient uniquement un élément, et non son contenu.
Pour récupérer le contenu d’un élément de manière récursive, utilisez `Get-ChildItem` .

Pour parcourir le registre, utilisez cette applet de commande pour récupérer les clés de Registre et le `Get-ItemProperty` pour accéder aux données et valeurs de registre. Les valeurs de Registre sont considérées comme des propriétés des clés de Registre.

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

