---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 03f32d798a9e7ec1e58cdeb4ddf5d30edccd2490
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204866"
---
# Test-ModuleManifest

## SYNOPSIS
Vérifie qu'un fichier manifeste de module décrit précisément le contenu d'un module.

## SYNTAX

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## Description

L’applet de commande **Test-ModuleManifest** vérifie que les fichiers qui sont répertoriés dans le fichier manifeste du module (. psd1) se trouvent dans les chemins d’accès spécifiés.

Cette applet de commande est conçue pour aider les auteurs du module à tester leurs fichiers manifeste.
Les utilisateurs du module peuvent également utiliser cette applet de commande dans des scripts et des commandes pour détecter les erreurs avant d’exécuter des scripts qui dépendent du module.

**Test-ModuleManifest** retourne un objet qui représente le module.
Il s’agit du même type d’objet que Get-Module retourne.
Si des fichiers ne figurent pas aux emplacements spécifiés dans le manifeste, l'applet de commande génère également une erreur pour chaque fichier manquant.

## EXEMPLES

### Exemple 1 : tester un manifeste

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

Cette commande teste le manifeste de module TestModule.psd1.

### Exemple 2 : tester un manifeste à l’aide du pipeline

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

Cette commande utilise un opérateur de pipeline (|) pour envoyer une chaîne de chemin d’accès à **Test-ModuleManifest** .

La sortie de la commande indique que le test a échoué, car le fichier TestTypes.ps1xml, indiqué dans le manifeste, est introuvable.

### Exemple 3 : écrire une fonction pour tester un manifeste de module

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

Cette fonction est similaire **à Test-ModuleManifest** , mais retourne une valeur booléenne.
La fonction retourne $True si le manifeste a réussi le test et $False dans le cas contraire.

La fonction utilise l’applet de commande Get-ChildItem, alias = dir, pour récupérer le manifeste de module spécifié par la variable $path.
La commande utilise un opérateur de pipeline (|) pour passer l’objet fichier à **Test-ModuleManifest** .

**Test-ModuleManifest** utilise le paramètre commun *ErrorAction* avec la valeur SilentlyContinue pour supprimer l’affichage des erreurs générées par la commande.
Elle enregistre également l’objet **PSModuleInfo** que **Test-ModuleManifest** renvoie dans la variable $a.
Par conséquent, l’objet n’est pas affiché.

Ensuite, dans une commande distincte, la fonction affiche la valeur de $ ?
variable automatique.
Si la commande précédente ne génère pas d’erreur, la commande affiche $True et $False dans le cas contraire.

Vous pouvez utiliser cette fonction dans des instructions conditionnelles, telles que celles qui peuvent précéder une commande **import-module** ou une commande qui utilise le module.

## PARAMETERS

### -Path

Spécifie un chemin d’accès et un nom de fichier pour le fichier manifeste.
Entrez un chemin d’accès et un nom facultatifs pour le fichier manifeste de module avec l’extension de nom de fichier. psd1.
L'emplacement par défaut est le répertoire actif.
Les caractères génériques sont pris en charge, mais ils doivent être résolus en un seul fichier manifeste de module.
Ce paramètre est obligatoire.
Vous pouvez également diriger un chemin vers **Test-ModuleManifest** .

```yaml
Type: System.String
Parameter Sets: (All)
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

Vous pouvez diriger le chemin d’accès vers un manifeste de module vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSModuleInfo

Cette applet de commande retourne un objet **PSModuleInfo** qui représente le module.
Il retourne cet objet même si le manifeste comporte des erreurs.

## REMARQUES

## LIENS CONNEXES

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Module d’importation](Import-Module.md)

[New-Module](New-Module.md)

[New-ModuleManifest](New-ModuleManifest.md)

[Remove-Module](Remove-Module.md)

[about_Modules](About/about_Modules.md)
