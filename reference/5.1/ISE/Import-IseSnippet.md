---
external help file: ISE-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202478"
---
# Import-IseSnippet

## SYNOPSIS
Importe les extraits de code de l'environnement ISE dans la session active.

## SYNTAX

### FromFolder (par défaut)

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### FromModule

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## Description

L' `Import-IseSnippet` applet de commande importe des « extraits de code » de texte réutilisables à partir d’un module ou d’un répertoire dans la session active. Les extraits de code sont immédiatement disponibles pour une utilisation dans Windows PowerShell ISE. Cette applet de commande fonctionne uniquement dans Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).

Pour afficher et utiliser les extraits de code importés, dans le menu Windows PowerShell ISE **Edition** , cliquez sur **Démarrer les extraits** ou appuyez sur <kbd>CTRL</kbd> + <kbd>J</kbd>.

Les extraits importés sont disponibles uniquement dans la session active. Pour importer les extraits de code dans toutes les sessions Windows PowerShell ISE, ajoutez une `Import-IseSnippet` commande à votre profil Windows PowerShell ou copiez les fichiers d’extraits de code dans votre répertoire d’extraits de code local `$home\Documents\WindowsPowershell\Snippets` .

Pour importer des extraits de code, ceux-ci doivent être correctement mis en forme dans l’extrait de code XML pour les extraits de Windows PowerShell ISE et enregistrés dans Snippet.ps1fichiers XML. Pour créer des extraits de code éligibles, utilisez l’applet de commande `New-IseSnippet` . `New-IseSnippet` crée un `<SnippetTitle>.Snippets.ps1xml` fichier dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire. Vous pouvez déplacer ou copier les extraits de code dans le répertoire Snippets d'un module Windows PowerShell ou dans tout autre répertoire.

L' `Get-IseSnippet` applet de commande, qui obtient les extraits de code créés par l’utilisateur dans le répertoire des extraits de code locaux, n’obtient pas les extraits de code importés.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : importer des extraits de code à partir d’un répertoire

Cet exemple importe les extraits de code à partir du `\\Server01\Public\Snippets` répertoire dans la session active. Elle utilise le paramètre **recurse** pour récupérer des extraits de code à partir de tous les sous-répertoires du répertoire des extraits de code.

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### Exemple 2 : importer des extraits de code à partir d’un module

Cet exemple importe les extraits de code à partir du module **SnippetModule** . La commande utilise le paramètre **listAvailable** pour importer les extraits de code même si le module **SnippetModule** n’est pas importé dans la session de l’utilisateur lors de l’exécution de la commande.

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### Exemple 3 : Rechercher des extraits de code dans les modules

Cet exemple obtient des extraits de code dans tous les modules installés dans la variable d’environnement PSModulePath.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### Exemple 4 : importer tous les extraits de code de module

Cet exemple importe tous les extraits de code de tous les modules installés dans la session active. En règle générale, vous n’avez pas besoin d’exécuter une commande comme celle-ci, car les modules qui ont des extraits de code utiliseront l’applet de commande `Import-IseSnippet` pour les importer pour vous lors de l’importation du module.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### Exemple 5 : copier tous les extraits de code de module

Cet exemple copie les fichiers d’extraits de tous les modules installés dans le répertoire Snippets de l’utilisateur actuel. Contrairement aux extraits de code importés qui affectent uniquement la session active, les extraits copiés sont disponibles dans toutes les sessions Windows PowerShell ISE.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## PARAMETERS

### -ListAvailable

Indique que cette applet de commande obtient les extraits de code des modules installés sur l’ordinateur, même si les modules ne sont pas importés dans la session active. Si ce paramètre est omis et que le module spécifié par le paramètre **module** n’est pas importé dans la session active, la tentative d’extraction des extraits de code à partir du module échoue.

Ce paramètre est valide uniquement quand le paramètre **Module** est utilisé dans la commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Importe des extraits de code du module spécifié dans la session active. Les caractères génériques ne sont pas pris en charge.

Ce paramètre importe des extraits de code à partir de Snippet.ps1fichiers XML dans le sous-répertoire snippets dans le chemin d’accès du module, tel que `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .

Ce paramètre est conçu pour être utilisé par les auteurs de module dans un script de démarrage, tel qu'un script spécifié dans la clé **ScriptsToProcess** d'un manifeste de module. Les extraits de code d’un module ne sont pas importés automatiquement avec le module, mais vous pouvez utiliser une `Import-IseSnippet` commande pour les importer.

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès au répertoire des extraits de code dans lequel cette applet de commande importe des extraits de code.

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Recurse

Indique que cette applet de commande importe des extraits de code à partir de tous les sous-répertoires de la valeur du paramètre **path** .

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n'accepte pas d'entrée provenant du pipeline.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- Vous ne pouvez pas utiliser l' `Get-IseSnippet` applet de commande pour récupérer des extraits de code importés. `Get-IseSnippet` Obtient uniquement les extraits de code dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire.
- `Import-IseSnippet` utilise la méthode statique **Load** des objets **Microsoft. PowerShell. Host. ISE. ISESnippetCollection** . Vous pouvez également utiliser la méthode **Load** des extraits de code dans le modèle objet Windows PowerShell ISE : `$psISE.CurrentPowerShellTab.Snippets.Load()`
- L' `New-IseSnippet` applet de commande stocke les nouveaux extraits de code créés par l’utilisateur dans les fichiers. ps1xml non signés. Par conséquent, Windows PowerShell ne peut pas les charger dans une session dans laquelle la stratégie d'exécution est **AllSigned** ou **Restricted** . Dans une session **Restricted** ou **AllSigned** , vous pouvez créer, obtenir et importer des extraits de code créés par l'utilisateur non signés, mais vous ne pouvez pas les utiliser dans la session.

  Pour utiliser des extraits de code créés par l’utilisateur non signés que l’applet de commande `Import-IseSnippet` retourne, modifiez la stratégie d’exécution, puis redémarrez Windows PowerShell ISE.

  Pour plus d'informations sur les stratégies d'exécution Windows PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

## LIENS CONNEXES

[Get-IseSnippet](Get-IseSnippet.md)

[New-IseSnippet](New-IseSnippet.md)
