---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: eb8cedd8275e9d8ea092a508c542464b8021878e
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524421"
---
# Install-PackageProvider

## SYNOPSIS
Installe un ou plusieurs fournisseurs de packages Package Management.

## SYNTAXE

### PackageBySearch (par défaut)

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### PackageByInputObject

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Install-PackageProvider` applet de commande installe les fournisseurs de Package Management correspondants qui sont disponibles dans les sources de package inscrites auprès de **PowerShellGet**. Par défaut, cela comprend les modules disponibles dans le PowerShell Gallery Windows avec la balise **PackageManagement** . Le fournisseur de Package Management **PowerShellGet** est utilisé pour rechercher des fournisseurs dans ces dépôts.

Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles à l’aide de l’application d’amorçage Package Management.

Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles dans le magasin d’objets BLOB Azure Package Management. Utilisez le fournisseur du programme d’amorçage pour les Rechercher et les installer.

Pour pouvoir s’exécuter la première fois, PackageManagement requiert une connexion Internet pour télécharger le fournisseur de package NuGet. Toutefois, si votre ordinateur ne dispose pas d’une connexion Internet et que vous devez utiliser le fournisseur NuGet ou PowerShellGet, vous pouvez les télécharger sur un autre ordinateur et les copier sur votre ordinateur cible. Utilisez les étapes suivantes pour effectuer cette opération :

1. Exécutez `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` pour installer le fournisseur à partir d’un ordinateur disposant d’une connexion Internet.
1. Après l’installation, vous trouverez le fournisseur installé dans `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .
1. Placez le `<ProviderName>` dossier, qui est dans ce cas le dossier NuGet, à l’emplacement correspondant sur votre ordinateur cible. Si votre ordinateur cible est un serveur nano, vous devez exécuter `Install-PackageProvider` à partir de nano Server pour télécharger les fichiers binaires NuGet appropriés.
1. Redémarrez PowerShell pour charger automatiquement le fournisseur de package. Vous pouvez également exécuter `Get-PackageProvider -ListAvailable` pour répertorier tous les fournisseurs de packages disponibles sur l’ordinateur.
   Utilisez ensuite `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` pour importer le fournisseur dans la session Windows PowerShell actuelle.

## EXEMPLES

### Exemple 1 : installer un fournisseur de package à partir de la PowerShell Gallery

Cette commande installe le fournisseur de packages GistProvider à partir de l’PowerShell Gallery.

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### Exemple 2 : installer une version spécifiée d’un fournisseur de packages

Cet exemple installe une version spécifiée du fournisseur de package NuGet.

La première commande recherche toutes les versions du fournisseur de package nommé NuGet.
La deuxième commande installe une version spécifiée du fournisseur de package NuGet.

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### Exemple 3 : Rechercher un fournisseur et l’installer

Cet exemple utilise `Find-PackageProvider` et le pipeline pour rechercher le fournisseur du Registre et l’installer.

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### Exemple 4 : installer un fournisseur dans le dossier du module de l’utilisateur actuel

Cette commande installe un fournisseur de package pour `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` que seul l’utilisateur actuel puisse l’utiliser.

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## PARAMÈTRES

### -AllVersions

Indique que cette applet de commande installe toutes les versions disponibles du fournisseur de package. Par défaut, `Install-PackageProvider` retourne uniquement la version la plus récente disponible.

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

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’installer des fournisseurs de packages.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que cette applet de commande force toutes les actions avec cette applet de commande qui peuvent être forcées. Actuellement, cela signifie que le paramètre **force** agit de la même façon que le paramètre **ForceBootstrap** .

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

### -ForceBootstrap

Indique que cette applet de commande installe automatiquement le fournisseur de package.

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

Spécifie un objet **SoftwareIdentity** . Utilisez l' `Find-PackageProvider` applet de commande pour obtenir un objet **SoftwareIdentity** dans lequel canaliser `Install-PackageProvider` .

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version maximale autorisée du fournisseur de package que vous souhaitez installer. Si vous n’ajoutez pas ce paramètre, `Install-PackageProvider` installe la version disponible la plus récente du fournisseur.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez installer. Si vous n’ajoutez pas ce paramètre, `Install-PackageProvider` installe la version disponible la plus élevée du package qui répond également aux exigences spécifiées par le paramètre *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un ou plusieurs noms de module du fournisseur de package. Séparez plusieurs noms de packages par des virgules.
Les caractères génériques ne sont pas pris en charge.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie la version exacte du fournisseur de packages que vous souhaitez installer. Si vous n’ajoutez pas ce paramètre, `Install-PackageProvider` installe la version disponible la plus récente du fournisseur qui satisfait également à toute version maximale spécifiée par le paramètre **MaximumVersion** .

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Étendue

Spécifie l’étendue d’installation du fournisseur. Les valeurs valides pour ce paramètre sont :

- **ALLUSERS** -installe les fournisseurs à un emplacement accessible à tous les utilisateurs de l’ordinateur.
  Par défaut, il s’agit de **$env :P rogramfiles\packagemanagement\providerassemblies.**

- **CurrentUser** -installe les fournisseurs à un emplacement où ils sont uniquement accessibles à l’utilisateur actuel. Par défaut, il s’agit de **$env : LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Spécifie une ou plusieurs sources de package. Utilisez l' `Get-PackageSource` applet de commande pour obtenir la liste des sources de package disponibles.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### Microsoft. PackageManagement. Packaging. SoftwareIdentity

Vous pouvez diriger un objet **SoftwareIdentity** vers cette applet de commande. Utilisez `Find-PackageProvider` pour obtenir un objet **SoftwareIdentity** qui peut être dirigé vers `Install-PackageProvider` .

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)
