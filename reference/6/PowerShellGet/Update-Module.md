---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 42a2b37144d9af188a7204500227fddf4827bdf9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204542"
---
# Update-Module

## SYNOPSIS
Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.

## SYNTAX

### Tous

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Update-Module` applet de commande installe la version la plus récente d’un module à partir d’une galerie en ligne. Vous êtes invité à confirmer la mise à jour avant son installation. Les mises à jour sont installées uniquement pour les modules qui ont été installés sur l’ordinateur local avec `Install-Module` . `Update-Module` recherche `$env:PSModulePath` les modules installés.

`Update-Module` Si aucun paramètre n’est spécifié, tous les modules installés sont mis à jour. Pour spécifier un module à mettre à jour, utilisez le paramètre **Name** . Vous pouvez mettre à jour vers une version spécifique d’un module à l’aide du paramètre **RequiredVersion** .

Si un module installé est déjà la version la plus récente, le module n’est pas mis à jour. Si le module est introuvable dans `$env:PSModulePath` , une erreur s’affiche.

Pour afficher les modules installés, utilisez `Get-InstalledModule` .

## EXEMPLES

### Exemple 1 : mettre à jour tous les modules

Cet exemple met à jour tous les modules installés vers la version la plus récente dans une galerie en ligne.

```powershell
Update-Module
```

### Exemple 2 : mettre à jour un module par nom

Cet exemple met à jour un module spécifique vers la version la plus récente dans une galerie en ligne.

```powershell
Update-Module -Name SpeculationControl
```

`Update-Module` utilise le paramètre **Name** pour mettre à jour un module spécifique, **SpeculationControl** .

### Exemple 3 : afficher les Update-Module les exécutions

Cet exemple fait un scénario de simulation pour montrer ce qui se passe si `Update-Module` est exécuté. La commande n’est pas exécutée.

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

`Update-Module` utilise le paramètre **WhatIf** pour afficher ce qui se passerait si `Update-Module` était exécuté.

### Exemple 4 : mettre à jour un module vers une version spécifiée

Dans cet exemple, un module est mis à jour vers une version spécifique. La version doit exister dans la galerie en ligne ou une erreur s’affiche.

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl** . Le paramètre **RequiredVersion** spécifie la version, **1.0.14** .

### Exemple 5 : mettre à jour un module sans confirmation

Cet exemple ne demande pas de confirmation pour mettre à jour le module vers la version la plus récente d’une galerie en ligne. Si le module est déjà installé, le paramètre **force** réinstalle le module.

```powershell
Update-Module -Name SpeculationControl -Force
```

`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl** . Le paramètre **force** met à jour le module sans demander la confirmation de l’utilisateur.

## PARAMETERS

### -AcceptLicense

Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.

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

Vous permet de mettre à jour un module avec le module le plus récent marqué comme version préliminaire.

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

### -Confirm

Vous invite à confirmer l’exécution `Update-Module` .

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

Spécifie un compte d’utilisateur qui a l’autorisation de mettre à jour un module.

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

Force une mise à jour de chaque module spécifié sans demander de confirmation. Si le module est déjà installé, **force** réinstalle le module.

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

### -MaximumVersion

Spécifie la version maximale d’un module unique à mettre à jour. Vous ne pouvez pas ajouter ce paramètre si vous tentez de mettre à jour plusieurs modules. Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie les noms d’un ou plusieurs modules à mettre à jour. `Update-Module` recherche `$env:PSModulePath` les modules à mettre à jour. Si aucune correspondance n’est trouvée dans `$env:PSModulePath` pour le nom de module spécifié, une erreur se produit.

Les caractères génériques sont acceptés dans les noms de module. Si vous ajoutez des caractères génériques au nom spécifié et qu’aucune correspondance n’est trouvée, aucune erreur ne se produit.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Proxy

Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.

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

Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .

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

### -RequiredVersion

Spécifie la version exacte à laquelle le module installé existant sera mis à jour. La version spécifiée par **RequiredVersion** doit exister dans la galerie en ligne ou une erreur s’affiche. Si plusieurs modules sont mis à jour dans une même commande, vous ne pouvez pas utiliser **RequiredVersion** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Étendue

Spécifie l’étendue d’installation du module. Les valeurs acceptables pour ce paramètre sont **ALLUSERS** et **CurrentUser** . Si **scope** n’est pas spécifié, la mise à jour est installée dans l’étendue **CurrentUser** .

L’étendue **ALLUSERS** nécessite des autorisations élevées et installe les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur :

`$env:ProgramFiles\PowerShell\Modules`

Le **CurrentUser** ne requiert pas d’autorisations élevées et installe les modules dans un emplacement accessible uniquement à l’utilisateur actuel de l’ordinateur :

`$home\Documents\PowerShell\Modules`

Si aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la version PowerShellGet.

- Dans PowerShellGet versions 2.0.0 et ultérieures, la valeur par défaut est **CurrentUser** , ce qui ne nécessite pas d’élévation pour l’installation.
- Dans les versions de PowerShellGet 1. x, la valeur par défaut est **ALLUSERS** , ce qui nécessite une élévation pour l’installation.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe si `Update-Module` s’exécute. L’applet de commande n’est pas exécutée.

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

### System.String

### System. Management. Automation. PSCredential

### System.Uri

## SORTIES

### System.Object

## REMARQUES

Pour PowerShell version 6,0 et versions ultérieures, l’étendue d’installation par défaut est toujours **CurrentUser** .
Les mises à jour de module pour **CurrentUser** , `$home\Documents\PowerShell\Modules` , n’ont pas besoin d’autorisations élevées. Les mises à jour de module pour **ALLUSERS** , `$env:ProgramFiles\PowerShell\Modules` , ont besoin d’autorisations élevées.

`Update-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.

Si le module que vous spécifiez avec le paramètre **Name** n’a pas été installé à l’aide de `Install-Module` , une erreur se produit.

Vous ne pouvez exécuter que `Update-Module` sur les modules que vous avez installés à partir de la galerie en ligne en exécutant `Install-Module` .

Si `Update-Module` tente de mettre à jour les fichiers binaires qui sont en cours d’utilisation, `Update-Module` retourne une erreur qui identifie les processus posant problème. L’utilisateur est informé de nouvelles tentatives `Update-Module` une fois les processus arrêtés.

## LIENS CONNEXES

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Uninstall-Module](Uninstall-Module.md)
