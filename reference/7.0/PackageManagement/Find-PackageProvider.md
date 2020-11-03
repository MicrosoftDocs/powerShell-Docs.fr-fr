---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: 96e8829b6939c40c85fb924ae65d73f48d2e475b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201525"
---
# Find-PackageProvider

## SYNOPSIS
Retourne une liste de Package Management fournisseurs de packages disponibles pour l’installation.

## SYNTAX

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## Description

L’applet de commande **Find-PackageProvider** recherche les fournisseurs PackageManagement correspondants qui sont disponibles dans les sources de package inscrites auprès de PowerShellGet.
Il s’agit de fournisseurs de packages disponibles pour l’installation avec l’applet de commande Install-PackageProvider.
Par défaut, cela comprend les modules disponibles dans le PowerShell Gallery avec les balises **PackageManagement** et **Provider** .

**Find-PackageProvider** recherche également les fournisseurs de Package Management correspondants qui sont disponibles dans le magasin d’objets Blob Azure Package Management.
Utilisez le fournisseur du programme d’amorçage pour les Rechercher et les installer.

## EXEMPLES

### Exemple 1 : Rechercher tous les fournisseurs de packages disponibles

```
PS C:\> Find-PackageProvider
```

Cette commande obtient une liste de tous les fournisseurs de packages qui sont disponibles dans les référentiels pris en charge par Package Management.
Par défaut, ces fournisseurs de packages sont disponibles sur le PowerShell Gallery et à l’aide de l’application d’amorçage Package Management.

### Exemple 2 : Rechercher toutes les versions d’un fournisseur

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

Cette commande recherche toutes les versions du fournisseur de package nommé NuGet.

### Exemple 3 : Rechercher un fournisseur à partir d’une source spécifiée

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

Cette commande recherche un fournisseur de package disponible à l’aide d’une source de package spécifiée.

## PARAMETERS

### -AllVersions

Indique que cette applet de commande retourne toutes les versions disponibles du fournisseur de package.
Par défaut, **Find-PackageProvider** retourne uniquement la version disponible la plus récente.

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

Spécifie un compte d’utilisateur qui a l’autorisation de rechercher des fournisseurs de packages.

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

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.
Actuellement, cette valeur est équivalente au paramètre *ForceBootstrap* .

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

Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.

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

### -IncludeDependencies

Indique que cette applet de commande comprend des dépendances.

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

Spécifie la version maximale autorisée du fournisseur de packages que vous souhaitez rechercher.
Si vous n’ajoutez pas ce paramètre, **Find-PackageProvider** recherche la version la plus élevée disponible du fournisseur.

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

### -MinimumVersion

Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez rechercher.
Si vous n’ajoutez pas ce paramètre, **Find-PackageProvider** recherche la version disponible la plus élevée du package qui satisfait également à la version maximale spécifiée spécifiée par le paramètre *MaximumVersion* .

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

### -Name

Spécifie un ou plusieurs noms de module du fournisseur de package, ou des noms de fournisseurs avec des caractères génériques.
Séparez plusieurs noms de packages par des virgules.

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

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .

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

Spécifie la version exacte du fournisseur de packages que vous souhaitez rechercher.
Si vous n’ajoutez pas ce paramètre, **Find-PackageProvider** recherche la version disponible la plus élevée du fournisseur qui satisfait également à toute version maximale spécifiée par le paramètre *MaximumVersion* .

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

### -Source

Spécifie une ou plusieurs sources de package.
Vous pouvez obtenir la liste des sources de packages disponibles à l’aide de l’applet de commande Get-PackageSource.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### Microsoft. PackageManagement. Packaging. SoftwareIdentity

Cette applet de commande retourne un objet **SoftwareIdentity** .
Un objet **SoftwareIdentity** peut être transmis à **install-PackageProvider** pour installer les résultats de **Find-PackageProvider** .

## REMARQUES

## LIENS CONNEXES

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Install-PackageProvider](Install-PackageProvider.md)
