---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: d635a1f037194380c143190e48d654e828f88bc8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890162"
---
# Get-Package

## SYNOPSIS
Retourne une liste de tous les packages logiciels qui ont été installés avec **PackageManagement**.

## SYNTAXE

### NuGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## Description

L' `Get-Package` applet de commande renvoie la liste de tous les packages logiciels sur l’ordinateur local qui ont été installés avec **PackageManagement**. Vous pouvez exécuter `Get-Package` sur des ordinateurs distants en l’exécutant dans le cadre d’une `Invoke-Command` commande ou d’un `Enter-PSSession` script.

## EXEMPLES

### Exemple 1 : récupération de tous les packages installés

L' `Get-Package` applet de commande obtient tous les packages qui sont installés sur l’ordinateur local.

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### Exemple 2 : obtenir les packages qui sont installés sur un ordinateur distant

Cette commande obtient la liste des packages qui ont été installés par **PackageManagement** sur un ordinateur distant. Cette commande vous invite à fournir le mot de passe de l’utilisateur spécifié.

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier un ordinateur distant, **SERVEUR01**. Le paramètre **Credential** spécifie un domaine et un nom d’utilisateur disposant des autorisations nécessaires pour exécuter des commandes sur l’ordinateur. Le paramètre **scriptblock** exécute l' `Get-Package` applet de commande sur l’ordinateur distant.

### Exemple 3 : obtenir des packages pour un fournisseur spécifié

Cette commande obtient les packages logiciels installés sur l’ordinateur local à partir d’un fournisseur spécifique.

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package` utilise le paramètre **providerName** pour spécifier un fournisseur spécifique, **PowerShellGet**.
Le paramètre **All-versions** affiche chaque version installée.

### Exemple 4 : obtenir une version exacte d’un package spécifique

Cette commande obtient une version spécifique d’un package installé. Il est possible d’installer plusieurs versions d’un package.

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package` utilise le paramètre **Name** pour spécifier le nom du package, **PackageManagement**. Le paramètre **providerName** spécifie le fournisseur, **PowerShellGet**. Le paramètre **Required-version** spécifie une version installée.

### Exemple 5 : désinstaller un package

Cet exemple obtient des informations sur le package, puis désinstalle le package.

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

`Get-Package` utilise le paramètre **Name** pour spécifier le nom du package, **Posh-git**. Le paramètre **RequiredVersion** est une version spécifique du package. L’objet est envoyé dans le pipeline à l’applet de commande `Uninstall-Package` . `Uninstall-Package` supprime le package.

## PARAMETERS

### -AllowClobber

Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes. Remplace les commandes existantes qui portent le même nom que les commandes installées par un module.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

Comprend les packages marqués comme version préliminaire dans les résultats.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Indique que `Get-Package` retourne toutes les versions disponibles du package. Par défaut, `Get-Package` retourne uniquement la version disponible la plus récente.

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

### -Destination

Spécifie le chemin d’accès à un répertoire qui contient des fichiers de package extraits.

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExcludeVersion

Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

Indique que `Get-Package` impose l’installation automatique du fournisseur de package par **PackageManagement** .

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

### -InstallUpdate

Indique que cette applet de commande installe les mises à jour.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version de package maximale que vous souhaitez rechercher.

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

Spécifie la version minimale du package que vous souhaitez rechercher. Si une version plus récente est disponible, cette version est retournée.

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

Spécifie un ou plusieurs noms de packages, ou des noms de package avec des caractères génériques. Séparez plusieurs noms de packages par des virgules.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -NoPathUpdate

**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` . **NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Get-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Spécifie le nom d’un fournisseur de gestion des packages.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Spécifie un ou plusieurs noms de fournisseurs de packages. Séparez les noms de plusieurs fournisseurs de packages par des virgules.
Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie la version exacte du package à rechercher.

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

### -Étendue

Spécifie l’étendue de recherche pour le package.

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

### -SkipDependencies

Commutateur qui spécifie d’ignorer la recherche de dépendances de package.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

Vous permet d’obtenir une version de package plus récente que la version installée. Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### SoftwareIdentity[]

## REMARQUES

L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande. Les paramètres dynamiques sont spécifiques à un fournisseur de packages. L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur. Par exemple, `Get-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .

> [!IMPORTANT]
> Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security). Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.

## LIENS CONNEXES

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[Find-Package](Find-Package.md)

[Get-Help](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Install-Package](Install-Package.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)
