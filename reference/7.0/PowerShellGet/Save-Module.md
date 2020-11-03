---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 1a41cc743bfb2572e1ab99bf161c2f13174bd163
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201822"
---
# Save-Module

## SYNOPSIS
Enregistre un module et ses dépendances sur l’ordinateur local, mais n’installe pas le module.

## SYNTAX

### NameAndPathParameterSet (par défaut)

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameAndLiteralPathParameterSet

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObjectAndLiteralPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObjectAndPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## Description

L' `Save-Module` applet de commande télécharge un module et toutes les dépendances à partir d’un dépôt inscrit.
`Save-Module` télécharge et enregistre la version la plus récente d’un module. Les fichiers sont enregistrés dans un chemin d’accès spécifié sur l’ordinateur local. Le module n’est pas installé, mais le contenu est disponible pour inspection par un administrateur. Le module enregistré peut ensuite être copié à l' `$env:PSModulePath` emplacement approprié de l’ordinateur hors connexion.

`Get-PSRepository` affiche les référentiels inscrits de l’ordinateur local. Vous pouvez utiliser l' `Find-Module` applet de commande pour rechercher des dépôts inscrits.

## EXEMPLES

### Exemple 1 : enregistrer un module

Dans cet exemple, un module et ses dépendances sont enregistrés sur l’ordinateur local.

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

`Save-Module` utilise le paramètre **Name** pour spécifier le module, **PowerShellGet** . Le paramètre **path** spécifie l’emplacement où stocker le module téléchargé. Le paramètre de **dépôt** spécifie un référentiel inscrit, **PSGallery** . Une fois le téléchargement terminé, `Get-ChildItem` affiche le contenu du **chemin d’accès** où les fichiers sont stockés.

### Exemple 2 : enregistrer une version spécifique d’un module

Cet exemple montre comment utiliser un paramètre tel que **MaximumVersion** ou **RequiredVersion** pour spécifier une version de module.

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

`Save-Module` utilise le paramètre **Name** pour spécifier le module, **PowerShellGet** . Le paramètre **path** spécifie l’emplacement où stocker le module téléchargé. Le paramètre de **dépôt** spécifie un référentiel inscrit, **PSGallery** . **MaximumVersion** spécifie que la version **2.1.0** est téléchargée et enregistrée. Une fois le téléchargement terminé, `Get-ChildItem` affiche le contenu du **chemin d’accès** où les fichiers sont stockés.

### Exemple 3 : Rechercher et enregistrer une version spécifique d’un module

Dans cet exemple, une version de module obligatoire est trouvée dans le référentiel et enregistrée sur l’ordinateur local.

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

`Find-Module` utilise le paramètre **Name** pour spécifier le module, **PowerShellGet** . Le paramètre de **dépôt** spécifie un référentiel inscrit, **PSGallery** . **RequiredVersion** spécifie la version **1.6.5** .

L’objet est envoyé dans le pipeline à `Save-Module` . Le paramètre **path** spécifie l’emplacement où stocker le module téléchargé. Une fois le téléchargement terminé, `Get-ChildItem` affiche le contenu du **chemin d’accès** où les fichiers sont stockés.

## PARAMETERS

### -AcceptLicense

Accepter automatiquement le contrat de licence si le package l’exige.

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

### -AllowPrerelease

Vous permet d’enregistrer un module marqué comme version préliminaire.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer l’exécution de l' `Save-Module` .

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

Spécifie un compte d’utilisateur qui dispose des droits d’enregistrement d’un module.

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

### -Force

Force l' `Save-Module` exécution sans demander la confirmation de l’utilisateur.

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

### -InputObject

Accepte un objet **PSRepositoryItemInfo** . Par exemple, `Find-Module` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur du paramètre **LiteralPath** est utilisée exactement comme entrée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples. PowerShell n’interprète pas les caractères placés entre guillemets simples comme séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version maximale ou la plus récente du module à enregistrer. Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie la version minimale d’un module unique à enregistrer. Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs modules. Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms de modules à enregistrer.

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie l’emplacement sur l’ordinateur local où stocker un module enregistré. Accepte les caractères génériques.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Proxy

Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .

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

### -Référentiel

Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` . Utilisez `Get-PSRepository` pour afficher les dépôts inscrits.

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie le numéro de version exact du module à enregistrer.

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passerait si le `Save-Module` s’exécute. L’applet de commande n’est pas exécutée.

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

### System.String[]

### System. Management. Automation. PSObject []

### System.String

### System.Uri

### System. Management. Automation. PSCredential

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES
