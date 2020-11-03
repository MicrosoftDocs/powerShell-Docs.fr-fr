---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 018a1da2a3fd40a95d378a563cacd68a734d9cd6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204842"
---
# Get-Acl

## SYNOPSIS
Obtient le descripteur de sécurité d'une ressource, comme une clé de Registre ou un fichier.

## SYNTAX

### ByPath (par défaut)

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### ByInputObject

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## Description

L' `Get-Acl` applet de commande obtient les objets qui représentent le descripteur de sécurité d’un fichier ou d’une ressource. Le descripteur de sécurité contient les listes de contrôle d'accès (ACL) de la ressource. La liste ACL spécifie les autorisations dont disposent les utilisateurs et les groupes d'utilisateurs pour accéder à la ressource.

À compter de Windows PowerShell 3,0, vous pouvez utiliser le paramètre **InputObject** de `Get-Acl` pour obtenir le descripteur de sécurité des objets qui n’ont pas de chemin d’accès.

## EXEMPLES

### Exemple 1 : obtenir une liste de contrôle d’accès pour un dossier

Cet exemple obtient le descripteur de sécurité du `C:\Windows` répertoire.

```powershell
Get-Acl C:\Windows
```

### Exemple 2 : obtenir une liste de contrôle d’accès pour un dossier à l’aide de caractères génériques

Cet exemple obtient le chemin d’accès PowerShell et le SDDL pour tous les `.log` fichiers du `C:\Windows` répertoire dont les noms commencent par `s` .

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

La commande utilise l' `Get-Acl` applet de commande pour récupérer des objets représentant les descripteurs de sécurité de chaque fichier journal. Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats à l’applet de commande `Format-List` . La commande utilise le paramètre **Property** de `Format-List` pour afficher uniquement les propriétés **PSPath** et **SDDL** de chaque objet descripteur de sécurité.

Les listes sont souvent utilisées dans PowerShell, car les valeurs longues apparaissent tronquées dans les tables.

Les valeurs **SDDL** sont précieuses pour les administrateurs système, car elles sont constituées de chaînes de texte simples qui contiennent toutes les informations du descripteur de sécurité. Par conséquent, elles sont faciles à transmettre et à stocker, et peuvent être analysées si nécessaire.

### Exemple 3 : obtenir le nombre d’entrées d’audit pour une liste de contrôle d’accès

Cet exemple obtient les descripteurs de sécurité des `.log` fichiers du `C:\Windows` répertoire dont les noms commencent par `s` .

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

Elle utilise le paramètre **Audit** pour obtenir les enregistrements d'audit de la liste SACL dans le descripteur de sécurité.
Elle utilise ensuite l' `ForEach-Object` applet de commande pour compter le nombre d’enregistrements d’audit associés à chaque fichier. Le résultat est une liste de nombres représentant le nombre d'enregistrements d'audit de chaque fichier journal.

### Exemple 4 : obtenir une liste de contrôle d’accès pour une clé de Registre

Cet exemple utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité de la sous-clé de contrôle ( `HKLM:\SYSTEM\CurrentControlSet\Control` ) du Registre.

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

Le paramètre **path** spécifie la sous-clé du contrôle. L’opérateur de pipeline ( `|` ) passe le descripteur de sécurité qui `Get-Acl` est extrait à la `Format-List` commande, qui met en forme les propriétés du descripteur de sécurité sous la forme d’une liste afin qu’elles soient faciles à lire.

### Exemple 5 : récupération d’une liste de contrôle d’accès à l’aide d' **InputObject**

Cet exemple utilise le paramètre **InputObject** de `Get-Acl` pour obtenir le descripteur de sécurité d’un objet de sous-système de stockage.

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## PARAMETERS

### -Audit

Obtient les données d'audit du descripteur de sécurité à partir de la liste de contrôle d'accès système (SACL).

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

### -Exclude

Omet les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés.

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

Spécifie un filtre dans le format ou le langage du fournisseur. La valeur de ce paramètre qualifie le paramètre **Path** . La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur. Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de l’obtention des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

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

### -Include

Obtient uniquement les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés.

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

### -Path

Spécifie le chemin d'accès à une ressource. `Get-Acl` Obtient le descripteur de sécurité de la ressource indiqué par le chemin d’accès. Les caractères génériques sont autorisés. Si vous omettez le paramètre **path** , `Get-Acl` obtient le descripteur de sécurité du répertoire actif.

Le nom de paramètre (« Path ») est facultatif.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -InputObject

Obtient le descripteur de sécurité de l'objet spécifié. Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.

Vous ne pouvez pas diriger un objet, autre qu’un chemin d’accès, vers `Get-Acl` . Utilisez plutôt le paramètre **InputObject** explicitement dans la commande.

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès à une ressource. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-Acl` .

## SORTIES

### System. Security. AccessControl. FileSecurity, System. Security. AccessControl. DirectorySecurity, System. Security. AccessControl. RegistrySecurity

`Get-Acl` retourne un objet qui représente les listes de contrôle d’accès qu’il obtient. Le type d'objet varie selon le type d'ACL.

## REMARQUES

Par défaut, `Get-Acl` affiche le chemin d’accès PowerShell à la ressource ( `<provider>::<resource-path>` ), le propriétaire de la ressource et « Access », une liste (tableau) des entrées de contrôle d’accès dans la liste de contrôle d’accès discrétionnaire (DACL) de la ressource. La liste DACL est contrôlée par le propriétaire de la ressource.

Lorsque vous mettez en forme le résultat sous la forme d’une liste, ( `Get-Acl | Format-List` ), en plus du chemin d’accès, du propriétaire et de la liste d’accès, PowerShell affiche les propriétés et les valeurs de propriétés suivantes :

- **Groupe** : groupe de sécurité du propriétaire.
- **Audit** : liste (tableau) d’entrées dans la liste de contrôle d’accès système (SACL). La liste SACL spécifie les types de tentatives d'accès pour lesquels Windows génère des enregistrements d'audit.
- **SDDL** : descripteur de sécurité de la ressource affiché dans une chaîne de texte unique au format de langage de définition du descripteur de sécurité. PowerShell utilise la méthode **GetSddlForm** des descripteurs de sécurité pour récupérer ces données.

Étant donné que `Get-Acl` est pris en charge par le système de fichiers et les fournisseurs de Registre, vous pouvez utiliser `Get-Acl` pour afficher la liste de contrôle d’accès des objets de système de fichiers, tels que les fichiers et les répertoires, et les objets de Registre, tels que les clés de Registre et les entrées.

## LIENS CONNEXES

[Set-Acl](Set-Acl.md)
