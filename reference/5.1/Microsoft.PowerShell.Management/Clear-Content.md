---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: b318abb06d36be5e28b9dcc3dc62fd4a70ab38fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204070"
---
# Clear-Content

## SYNOPSIS
Supprime le contenu d'un élément, mais ne supprime pas l'élément.

## SYNTAX

### Chemin d’accès (par défaut)

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

## Description

L' `Clear-Content` applet de commande supprime le contenu d’un élément, tel que la suppression du texte d’un fichier, mais il ne supprime pas l’élément.
En conséquence, l'élément existe, mais il est vide.
`Clear-Content`Est semblable à `Clear-Item` , mais il fonctionne sur des éléments avec du contenu, au lieu d’éléments avec des valeurs.

## EXEMPLES

### Exemple 1 : supprimer tout le contenu d’un répertoire

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

Cette commande supprime tout le contenu des fichiers « init.txt » dans l'ensemble des sous-répertoires du répertoire SmpUsers.
Les fichiers ne sont pas supprimés, mais ils sont vides.

### Exemple 2 : supprimer le contenu de tous les fichiers avec un caractère générique

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

Cette commande supprime le contenu de tous les fichiers du répertoire actif dont le nom est doté de l'extension « .log », y compris les fichiers en lecture seule.
L’astérisque ( \* ) dans le chemin d’accès représente tous les éléments du répertoire actif.
Le paramètre **force** rend la commande effective sur les fichiers en lecture seule.
L’utilisation d’un filtre pour limiter la commande aux fichiers avec l’extension de nom de fichier. log au lieu de spécifier \* . log dans le chemin rend l’opération plus rapide.

### Exemple 3 : effacer toutes les données d’un flux

Cet exemple montre comment l' `Clear-Content` applet de commande efface le contenu d’un autre flux de données tout en laissant intact le flux.

La première commande utilise l' `Get-Content` applet de commande pour récupérer le contenu du flux de zone. identificateur dans le fichier Copy-Script.ps1, qui a été téléchargé à partir d’Internet.

La deuxième commande utilise l' `Clear-Content` applet de commande pour effacer le contenu.

La troisième commande répète la première commande. Il vérifie que le contenu est effacé, mais le flux de données est conservé. Si le flux a été supprimé, la commande génère une erreur.

Vous pouvez utiliser une méthode telle que celle-ci pour effacer le contenu d’un flux de données de remplacement. Elle ne constitue cependant pas un moyen recommandé pour éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d'Internet. Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.

```powershell
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
[ZoneTransfer]
ZoneId=3
```

```powershell
Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output

```

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell. Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez Invoke-Command.

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

Spécifie, sous forme de tableau de chaînes, les chaînes omises par cette applet de commande dans le chemin d’accès au contenu.
La valeur de ce paramètre qualifie le paramètre **Path** .
Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ».
Les caractères génériques sont autorisés.

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

Spécifie un filtre dans le format ou le langage du fournisseur.
La valeur de ce paramètre qualifie le paramètre **Path** .
La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur.
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de la récupération des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

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

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

Spécifie, sous forme de tableau de chaînes, le contenu que cette applet de commande efface.
La valeur de ce paramètre qualifie le paramètre **Path** .
Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ».
Les caractères génériques sont autorisés.

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

Spécifie les chemins d'accès aux éléments dont le contenu est supprimé.
Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.
Aucun caractère n’est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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

Spécifie les chemins d'accès aux éléments dont le contenu est supprimé.
Les caractères génériques sont autorisés.
Les chemins d'accès doivent être ceux des éléments et non des conteneurs.
Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.
Les caractères génériques sont autorisés.
Ce paramètre est obligatoire, mais le nom de paramètre (« Path ») est facultatif.

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

Spécifie un flux de données alternatif pour le contenu.
Si le flux n’existe pas, cette applet de commande le crée.
Les caractères génériques ne sont pas pris en charge.

**Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Clear-Content` .
Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Vous pouvez utiliser l' `Clear-Content` applet de commande pour modifier le contenu du flux de données de remplacement de la zone. identifier.
Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet.
Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

Inclut la commande dans la transaction active.
Ce paramètre est uniquement valide au cours d’une transaction.
Pour plus d’informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

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

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

### Aucun

Vous ne pouvez pas diriger d’objets vers `Clear-Content` .

## SORTIES

### Aucun

Cette applet de commande ne retourne pas d'objets.

## REMARQUES

Vous pouvez utiliser `Clear-Content` avec le fournisseur FileSystem de PowerShell et avec d’autres fournisseurs qui manipulent du contenu.
Pour effacer les éléments qui ne sont pas considérés comme du contenu, tels que les éléments gérés par le certificat PowerShell ou les fournisseurs de Registre, utilisez `Clear-Item` .

L' `Clear-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.
Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .
Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Add-Content](Add-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[Set-Content](Set-Content.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
