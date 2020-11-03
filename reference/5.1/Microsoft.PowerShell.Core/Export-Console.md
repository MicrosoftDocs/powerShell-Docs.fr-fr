---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202317"
---
# Export-Console

## SYNOPSIS
Exporte les noms des composants logiciels enfichables de la session active dans un fichier de console.

## SYNTAX

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Export-Console** exporte les noms des composants logiciels enfichables Windows PowerShell de la session active dans un fichier de console Windows PowerShell (. psc1).
Vous pouvez utiliser cette applet de commande pour enregistrer les composants logiciels enfichables à utiliser plus tard dans d'autres sessions.

Pour ajouter les composants logiciels enfichables du fichier de console. psc1 à une session, démarrez Windows PowerShell (Powershell.exe) sur la ligne de commande à l’aide de Cmd.exe ou d’une autre session Windows PowerShell, puis utilisez le paramètre *PSConsoleFile* de Powershell.exe pour spécifier le fichier de console.

Pour plus d'informations sur les composants logiciels enfichables Windows PowerShell, consultez about_PSSnapins.

## EXEMPLES

### Exemple 1 : exporter les noms des composants logiciels enfichables dans la session active

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

Cette commande exporte les noms des composants logiciels enfichables Windows PowerShell de la session active dans le fichier ConsoleS1. psc1 dans le dossier consoles du dossier d’installation de Windows PowerShell, $pshome.

### Exemple 2 : exporter les noms des composants logiciels enfichables vers le fichier de console le plus récent

```
PS C:\> Export-Console
```

Cette commande exporte les noms des composants logiciels enfichables Windows PowerShell de la session active dans le dernier fichier de console Windows PowerShell utilisé dans la session active.
Elle remplace le contenu précédent du fichier.

Si vous n'avez pas exporté de fichier de console pendant la session active, vous êtes invité à autoriser la poursuite de l'opération et à entrer un nom de fichier.

### Exemple 3 : ajouter un composant logiciel enfichable et exporter les noms des composants logiciels enfichables

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

Ces commandes ajoutent le composant logiciel enfichable Windows PowerShell NewPSSnapin à la session active, exportent les noms des composants logiciels enfichables Windows PowerShell de la session active dans un fichier de console, puis démarrent une session Windows PowerShell avec le fichier de console.

La première commande utilise l’applet de commande **Add-PSSnapin** pour ajouter le composant logiciel enfichable NewPSSnapin à la session active.
Vous ne pouvez ajouter que les composants logiciels enfichables Windows PowerShell inscrits sur votre système.

La deuxième commande exporte les noms des composants logiciels enfichables Windows PowerShell dans le fichier NewPSSnapinConsole.psc1.

La troisième commande démarre Windows PowerShell avec le fichier NewPSSnapinConsole.psc1.
Étant donné que le fichier de console inclut le nom du composant logiciel enfichable Windows PowerShell, les applets de commande et les fournisseurs du composant logiciel enfichable sont disponibles dans la session active.

### Exemple 4 : exporter les noms des composants logiciels enfichables vers un emplacement spécifié

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

Cette commande exporte les noms des composants logiciels enfichables Windows PowerShell de la session active vers le fichier Console01.psc1 dans le répertoire actif.

La deuxième commande affiche le contenu du fichier Console01.psc1 dans le Bloc-notes.

### Exemple 5 : déterminer le fichier de console à mettre à jour

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

Cet exemple montre comment utiliser la variable automatique $ConsoleFileName pour déterminer le fichier de console qui sera mis à jour si vous utilisez **Export-Console** sans valeur de paramètre *path* .

La première commande utilise le paramètre *PSConsoleFile* de PowerShell.exe pour ouvrir Windows PowerShell avec le fichier fichier Console01. psc1.

La deuxième commande utilise l’applet de commande **Add-PSSnapin** pour ajouter le composant logiciel enfichable Windows PowerShell MySnapin à la session active.

La troisième commande utilise l’applet de commande **Export-Console** pour exporter les noms de tous les composants logiciels enfichables Windows PowerShell de la session dans le fichier NewConsole. psc1.

La quatrième commande affiche la variable $ConsoleFileName.
Il contient le dernier fichier de console utilisé.
L'exemple de sortie montre que NewConsole.ps1 est le dernier fichier utilisé.

La cinquième commande ajoute SnapIn03 à la console actuelle.

La sixième commande utilise l’applet de commande **Export-Console** sans paramètre *path* .
Cette commande exporte les noms de tous les composants logiciels enfichables Windows PowerShell de la session active dans le dernier fichier utilisé, NewConsole.psc1.

## PARAMETERS

### -Force
Indique que cette applet de commande remplace les données dans un fichier de console sans avertissement, même si le fichier a l’attribut de lecture seule.
L’attribut de lecture seule est modifié et n’est pas réinitialisé à la fin de l’exécution de la commande.

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

### -NoClobber
Indique que cette applet de commande ne remplace pas un fichier de console existant.
Par défaut, si un fichier se trouve dans le chemin d’accès spécifié, **Export-Console** remplace le fichier sans avertissement.

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

### -Path
Spécifie un chemin d'accès et un nom de fichier pour le fichier de console (*.psc1).
Entrez un chemin d’accès et un nom facultatifs.
Les caractères génériques ne sont pas autorisés.

Si vous spécifiez uniquement un nom de fichier, **Export-Console** crée un fichier portant ce nom et l’extension de nom de fichier. psc1 dans le répertoire actif.

Ce paramètre est obligatoire, sauf si vous avez ouvert Windows PowerShell avec le paramètre *PSConsoleFile* ou exporté un fichier de console pendant la session active.
Elle est également requise quand vous utilisez le paramètre *NoClobber* pour empêcher le fichier de console actif d’être remplacé.

Si vous omettez ce paramètre, **Export-Console** remplace le fichier de console qui a été utilisé le plus récemment dans cette session.
Le chemin d’accès du dernier fichier de console utilisé est stocké dans la valeur de la variable automatique $ConsoleFileName.
Pour plus d'informations, consultez about_Automatic_Variables.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
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
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String
Vous pouvez diriger une chaîne de chemin d’accès vers cette applet de commande.

## SORTIES

### System. IO. FileInfo
Cette applet de commande crée un fichier qui contient les alias exportés.

## REMARQUES

* Quand un fichier de console (.psc1) est utilisé pour démarrer la session, son nom est automatiquement stocké dans la variable automatique $ConsoleFileName. La valeur de $ConsoleFileName est mise à jour quand vous utilisez le paramètre *path* de **Export-Console** pour spécifier un nouveau fichier de console. Quand aucun fichier de console n’est utilisé, $ConsoleFileName n’a aucune valeur ($Null).

  Pour utiliser un fichier de console Windows PowerShell dans une nouvelle session, employez la syntaxe suivante pour démarrer Windows PowerShell :

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  Vous pouvez également enregistrer les composants logiciels enfichables Windows PowerShell pour des sessions futures en ajoutant une commande Add-PSSnapin à votre profil Windows PowerShell.
Pour plus d'informations, consultez about_Providers.


## LIENS CONNEXES

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
