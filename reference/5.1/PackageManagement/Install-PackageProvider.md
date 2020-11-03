---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 4e6940b655622444f0ac6c8f01cd7e77f854b109
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202930"
---
# Install-PackageProvider

## SYNOPSIS
Installe un ou plusieurs fournisseurs de packages Package Management.

## SYNTAX

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
L’applet de commande **install-PackageProvider** installe les fournisseurs de Package Management correspondants qui sont disponibles dans les sources de package inscrites auprès de **PowerShellGet** .
Par défaut, cela comprend les modules disponibles dans le PowerShell Gallery Windows avec la balise **PackageManagement** .
Le fournisseur de Package Management **PowerShellGet** est utilisé pour rechercher des fournisseurs dans ces dépôts.

Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles à l’aide de l’application d’amorçage Package Management.

Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles dans le magasin d’objets BLOB Azure Package Management.
Utilisez le fournisseur du programme d’amorçage pour les Rechercher et les installer.

Pour pouvoir s’exécuter la première fois, PackageManagement requiert une connexion Internet pour télécharger le fournisseur de package NuGet.
Toutefois, si votre ordinateur ne dispose pas d’une connexion Internet et que vous devez utiliser le fournisseur NuGet ou PowerShellGet, vous pouvez les télécharger sur un autre ordinateur et les copier sur votre ordinateur cible.
Utilisez les étapes suivantes pour effectuer cette opération :

1.
Exécutez `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` pour installer le fournisseur à partir d’un ordinateur disposant d’une connexion Internet.

2.
Après l’installation, vous trouverez le fournisseur installé dans `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .

3.
Placez le \<ProviderName\> dossier, qui est dans ce cas le dossier NuGet, à l’emplacement correspondant sur votre ordinateur cible.
Si votre ordinateur cible est un serveur nano, vous devez exécuter **install-PackageProvider** à partir de nano Server pour télécharger les fichiers binaires NuGet appropriés.

4.
Redémarrez PowerShell pour charger automatiquement le fournisseur de package.
Vous pouvez également exécuter `Get-PackageProvider -ListAvailable` pour répertorier tous les fournisseurs de packages disponibles sur l’ordinateur.
Utilisez ensuite `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` pour importer le fournisseur dans la session Windows PowerShell actuelle.

## EXEMPLES

### Exemple 1 : installer un fournisseur de package à partir de la PowerShell Gallery

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

Cette commande installe le Gistprovider à partir de la PowerShell Gallery.

### Exemple 2 : installer une version spécifiée d’un fournisseur de packages

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

Cet exemple installe une version spécifiée du fournisseur de package NuGet.

La première commande recherche toutes les versions du fournisseur de package nommé NuGet.
La deuxième commande installe une version spécifiée du fournisseur de package NuGet.

### Exemple 3 : Rechercher un fournisseur et l’installer

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

Cette commande utilise **Find-PackageProvider** et le pipeline pour rechercher le fournisseur de l’aide et l’installer.

### Exemple 4 : installer un fournisseur dans le dossier du module de l’utilisateur actuel

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

Cette commande installe un fournisseur de package pour $env : Localappdata\packagemanagement\providerassemblies. afin que seul l’utilisateur actuel puisse l’utiliser.

## PARAMETERS

### -AllVersions
Indique que cette applet de commande installe toutes les versions disponibles du fournisseur de package.
Par défaut, **install-PackageProvider** retourne uniquement la version la plus récente disponible.

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
Indique que cette applet de commande force toutes les actions avec cette applet de commande qui peuvent être forcées.
Actuellement, cela signifie que le paramètre *force* agit de la même façon que le paramètre *ForceBootstrap* .

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
Spécifie un objet **SoftwareIdentity** .
Utilisez l’applet de commande **Find-PackageProvider** pour obtenir un objet **SoftwareIdentity** pour canaliser dans **install-PackageProvider** .

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
Spécifie la version maximale autorisée du fournisseur de package que vous souhaitez installer.
Si vous n’ajoutez pas ce paramètre, **install-PackageProvider** installe la version disponible la plus récente du fournisseur.

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
Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez installer.
Si vous n’ajoutez pas ce paramètre, **install-PackageProvider** installe la version disponible la plus élevée du package qui répond également aux exigences spécifiées par le paramètre *MaximumVersion* .

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
Spécifie un ou plusieurs noms de module du fournisseur de package.
Séparez plusieurs noms de packages par des virgules.
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
Spécifie la version exacte du fournisseur de packages que vous souhaitez installer.
Si vous n’ajoutez pas ce paramètre, **install-PackageProvider** installe la version disponible la plus récente du fournisseur qui satisfait également à toute version maximale spécifiée par le paramètre *MaximumVersion* .

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
Spécifie l’étendue d’installation du fournisseur.
Les valeurs acceptables pour ce paramètre sont les suivantes : **ALLUSERS** et **CurrentUser** .

L’étendue **ALLUSERS** installe les fournisseurs à un emplacement accessible à tous les utilisateurs de l’ordinateur.
Par défaut, il s’agit de **$env :P rogramfiles\packagemanagement\providerassemblies.**

L’étendue **CurrentUser** installe les fournisseurs à un emplacement où ils sont accessibles uniquement à l’utilisateur actuel.
Par défaut, il s’agit de **$env : LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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
Spécifie une ou plusieurs sources de package.
Utilisez l’applet de commande Get-PackageSource pour obtenir la liste des sources de package disponibles.

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

### Microsoft. PackageManagement. Packaging. SoftwareIdentity
Vous pouvez diriger un objet **SoftwareIdentity** vers cette applet de commande.
Utilisez Find-PackageProvider pour obtenir un objet **SoftwareIdentity** qui peut être dirigé vers **install-PackageProvider** .

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)
