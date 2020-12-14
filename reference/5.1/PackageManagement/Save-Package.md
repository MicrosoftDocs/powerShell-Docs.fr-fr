---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 1b780ad8c28c6c7095012fd75ed4dfa31d761b08
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889992"
---
# Save-Package

## SYNOPSIS
Enregistre les packages sur l’ordinateur local sans les installer.

## SYNTAXE

### PackageBySearch

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### PackageByInputObject

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NuGet : PackageByInputObject

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### NuGet

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### PowerShellGet : PackageByInputObject

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### PowerShellGet

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## Description

L' `Save-Package` applet de commande enregistre les packages sur l’ordinateur local, mais n’installe pas les packages.
Cette applet de commande enregistre la version la plus récente d’un package, sauf si vous spécifiez un **RequiredVerion**. Les paramètres **path** et **LiteralPath** s’excluent mutuellement et ne peuvent pas être ajoutés à la même commande.

## EXEMPLES

### Exemple 1 : enregistrer un package sur l’ordinateur local

Cet exemple enregistre la version la plus récente du package dans un répertoire sur l’ordinateur local. Les dépendances du package sont téléchargées avec le package.

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

`Save-Package` utilise le paramètre **Name** pour spécifier le package. Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** . Le paramètre Path détermine l’emplacement **d'** enregistrement du package.

### Exemple 2 : enregistrer une version de package spécifique

Cet exemple spécifie la version du package et l’enregistre dans un répertoire sur l’ordinateur local.

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

`Save-Package` utilise le paramètre **Name** pour spécifier le package. **RequiredVersion** indique une version de package spécifique. Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** . Le paramètre Path détermine l’emplacement **d'** enregistrement du package.

### Exemple 3 : utiliser Find-Package pour enregistrer un package

Cette commande utilise `Find-Package` pour localiser la version la plus récente du package et envoie l’objet à `Save-Package` .

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

`Find-Package` utilise le paramètre **Name** pour spécifier le package. Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** . L’objet est envoyé dans le pipeline à `Save-Package` . Le paramètre Path détermine l’emplacement **d'** enregistrement du package.

### Exemple 4 : enregistrer et installer le package

La version la plus récente du package et ses dépendances sont téléchargées et installées sur l’ordinateur local.

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

`Save-Package` télécharge le fichier de package et ses dépendances sur l’ordinateur local.
`Install-Package` installe le package et les dépendances à partir du répertoire spécifié.

## PARAMETERS

### -AcceptLicense

Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

Autorise l’enregistrement des packages marqués comme préversion.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Indique que cette applet de commande enregistre toutes les versions disponibles du package.

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

### -Command

Spécifie une ou plusieurs commandes incluses dans le package.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigFile

Spécifie un fichier de configuration.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Contient

`Save-Package` obtient des objets si un élément dans les valeurs de propriété de l’objet correspond exactement à la valeur spécifiée.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’enregistrer un package à partir d’un fournisseur de package ou d’une source spécifiés.

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

### -DscResource

Spécifie une ou plusieurs ressources de configuration d’état souhaité (DSC) pour le package.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Spécifie un filtre pour le package.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterOnTag

Spécifie la balise qui filtre les résultats. Les résultats qui ne contiennent pas la balise spécifiée sont exclus.

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
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

Indique que `Save-Package` force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.

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

### -En-têtes

Spécifie les en-têtes pour le package.

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Comprend

Indique les ressources incluses dans le package.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Objet d’ID de logiciel qui représente le package que vous souhaitez enregistrer. Les ID de logiciel font partie des résultats de l’applet de commande `Find-Package` .

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès littéral dans lequel vous souhaitez enregistrer le package. Vous ne pouvez pas ajouter à la fois ce paramètre et le paramètre **path** à la même commande.

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

### -MaximumVersion

Spécifie la version maximale du package que vous souhaitez enregistrer.

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

Spécifie la version minimale du package que vous souhaitez rechercher.

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

Spécifie un ou plusieurs noms de packages.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PackageManagementProvider

Spécifie un fournisseur de gestion des packages.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie l’emplacement sur l’ordinateur local où stocker le package.

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

### -ProviderName

Spécifie un ou plusieurs noms de fournisseurs.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Proxy

Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.

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

### -PublishLocation

Spécifie l’emplacement de publication.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie la version exacte du package à enregistrer.

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

### -RoleCapability

Spécifie un tableau de capacités de rôle.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Spécifie l’emplacement de publication du script.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Spécifie l’emplacement source du script.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

Commutateur qui ignore la validation des informations d’identification d’un package.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Spécifie une ou plusieurs sources de package.

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

### -Tag

Spécifie une balise à rechercher dans les métadonnées du package.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
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
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
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

### `Save-Package` accepte les objets du pipeline.

## SORTIES

### Cette applet de commande ne génère aucune sortie.

## REMARQUES

> [!IMPORTANT]
> Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security). Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.

## LIENS CONNEXES

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Package](Get-Package.md)

[Install-Package](Install-Package.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)
