---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 0481526aead285e3d5fb494218d1573e03216f2e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599002"
---
# Resolve-Path

## SYNOPSIS
Résout les caractères génériques inclus dans un chemin d'accès et affiche le contenu de ce dernier.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## Description

L' `Resolve-Path` applet de commande affiche les éléments et les conteneurs qui correspondent au modèle de caractère générique à l’emplacement spécifié. La correspondance peut inclure des fichiers, des dossiers, des clés de registre ou tout autre objet accessible à partir d’un fournisseur PSDrive.

## EXEMPLES

### Exemple 1 : résoudre le chemin d’accès du dossier de démarrage

Le caractère tilde (~) est une notation abrégée pour le dossier de démarrage de l’utilisateur actuel. Cet exemple montre comment `Resolve-Path` retourner la valeur de chemin qualifié complet.

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### Exemple 2 : résoudre le chemin d’accès du dossier Windows

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

Lorsqu’elle est exécutée à partir de la racine du lecteur C :, cette commande retourne le chemin d’accès du dossier Windows sur le lecteur C :.

### Exemple 3 : récupération de tous les chemins d’accès dans le dossier Windows

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

Cette commande retourne tous les dossiers du dossier C:\Windows. La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne de chemin d’accès à `Resolve-Path` .

### Exemple 4 : résoudre un chemin d’accès UNC

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

Cette commande résout un chemin d'accès UNC (Universal Naming Convention) et retourne les partages dans le chemin d'accès.

### Exemple 5 : récupérer les chemins d’accès relatifs

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

Cette commande retourne des chemins d'accès relatifs aux répertoires situés à la racine du lecteur C:.

### Exemple 6 : résoudre un chemin d’accès contenant des crochets

Cet exemple utilise le paramètre **LiteralPath** pour résoudre le chemin d’accès du \[ \] sous-dossier XML de test.
L’utilisation de **LiteralPath** provoque le traitement des crochets comme des caractères normaux plutôt qu’une expression régulière.

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## PARAMETERS

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou transmettez un objet **PSCredential** . Vous pouvez créer un objet **PSCredential** à l’aide de l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.

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

### -LiteralPath

Spécifie le chemin d'accès à résoudre.
La valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.
Aucun caractère n'est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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

Spécifie le chemin d’accès PowerShell à résoudre.
Ce paramètre est obligatoire.
Vous pouvez également diriger une chaîne de chemin vers `Resolve-Path` .
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

### -Relatif

Indique que cette applet de commande retourne un chemin d’accès relatif.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande

## SORTIES

### System. Management. Automation. PathInfo, System. String

Retourne un objet **PathInfo** . Retourne une valeur de chaîne pour le chemin d’accès résolu si vous spécifiez le paramètre **relatif** .

## REMARQUES

Les `*-Path` applets de commande fonctionnent avec le système de fichiers, le registre et les fournisseurs de certificats.

`Resolve-Path` est conçu pour fonctionner avec n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d’informations, consultez [about_Providers](../microsoft.powershell.core/about/about_providers.md).

`Resolve-Path` résout uniquement les chemins d’accès existants. Il ne peut pas être utilisé pour résoudre un emplacement qui n’existe pas encore.

## LIENS CONNEXES

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

