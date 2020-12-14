---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 39896c4f48d6cd8809d4a680e776d36deb65b0d8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889859"
---
# Find-DscResource

## SYNOPSIS
Recherche les ressources de configuration d’état souhaité (DSC).

## SYNTAXE

### Tous

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## Description

L' `Find-DscResource` applet de commande recherche les référentiels inscrits pour trouver les ressources DSC contenues dans les modules. Par défaut, `Find-DscResource` recherche tous les dépôts inscrits.

Pour chaque module trouvé par `Find-DscResource` , un objet **PSGetDscResourceInfo** est retourné.
Les objets **PSGetDscResourceInfo** peuvent être envoyés vers l’applet de commande via le pipeline `Install-Module` .
`Install-Module` installe le module.

## EXEMPLES

### Exemple 1 : Rechercher toutes les ressources DSC

`Find-DscResource` retourne des ressources DSC à partir de dépôts inscrits. Pour effectuer une recherche dans un référentiel spécifique, utilisez le paramètre de **référentiel** .

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### Exemple 2 : Rechercher une ressource DSC par nom

`Find-DscResource` localise les ressources DSC par nom. Utilisez des virgules pour séparer un tableau de noms de ressources.

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

`Find-DscResource` utilise le paramètre **Name** pour rechercher le tableau spécifié de ressources DSC.

### Exemple 3 : Rechercher une ressource DSC et l’installer

`Find-DscResource` localise une ressource DSC et envoie l’objet dans le pipeline à installer.
Après l’installation, utilisez `Get-InstalledModule` pour afficher les résultats.

Plusieurs ressources du même module peuvent être envoyées vers le pipeline vers le `Install-Module` .
`Install-Module` tente d’installer le module une seule fois.

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

`Find-DscResource` utilise le paramètre **Name** pour rechercher la ressource nommée **xWebsite**. L’objet est envoyé dans le pipeline à l’applet de commande `Install-Module` . `Install-Module` installe le module **xWebAdministration** pour la ressource.

### Exemple 4 : Rechercher toutes les ressources DSC dans un module

`Find-DscResource` recherche toutes les ressources DSC contenues dans un module spécifié. Par défaut, la version actuelle est affichée. Pour afficher d’autres versions, utilisez les paramètres **AllVersions** ou **RequiredVersions** .

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

`Find-DscResource` utilise le paramètre **modulename** pour spécifier le **xWebAdministration** et rechercher les ressources DSC contenues dans le module. La version actuelle de chaque ressource est affichée.

### Exemple 5 : Rechercher une ressource DSC par balise et version requise

Les ressources DSC peuvent être localisées à l’aide des paramètres **tag** et **RequiredVersion**. **Tag** affiche la version actuelle de chaque ressource contenant la balise spécifiée dans le référentiel.
**RequiredVersion** a besoin du paramètre **modulename** et le paramètre **Name** est facultatif. Les paramètres **Name** et **modulename** limitent la sortie. Utilisez le paramètre **AllVersions** pour afficher les versions disponibles d’une ressource DSC.

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### Exemple 6 : Rechercher une ressource à l’aide d’un filtre

`Find-DscResource` recherche toutes les ressources et utilise le paramètre **Filter** pour spécifier les résultats par **domaine**. Le paramètre de **filtre** recherche la valeur de filtre dans la description ou le nom de module de l’objet. Utilisez l' `Select-Object` applet de commande pour afficher les propriétés d’un objet.

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## PARAMETERS

### -AllowPrerelease

Comprend les ressources marquées comme préversion dans les résultats.

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

### -AllVersions

Le paramètre **AllVersions** affiche chacune des versions disponibles d’une ressource DSC. Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion**, **MaximumVersion** ou **RequiredVersion** .

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

### -Filter

Recherche des ressources en fonction de la syntaxe de recherche du fournisseur **PackageManagement** . Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .

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

Spécifie la version maximale de la ressource à inclure dans les résultats. Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

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

Spécifie la version minimale de la ressource à inclure dans les résultats. Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

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

### -ModuleName

Spécifie un module qui contient la ressource DSC.

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

Spécifie le nom d'une ressource. La valeur par défaut est toutes les ressources. Utilisez des virgules pour séparer un tableau de noms de ressources.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Spécifie un compte d’utilisateur disposant de l’autorisation d’utiliser le serveur proxy spécifié dans le paramètre **proxy** .

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

Spécifie un référentiel dans lequel Rechercher des ressources. Utilisez des virgules pour séparer un tableau de noms de référentiel.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie le numéro de version exact du module à inclure dans les résultats. Les paramètres **RequiredVersion** et **MinimumVersion** ne peuvent pas être utilisés dans la même commande.

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

### -Tag

Spécifie les balises qui classent les modules dans un référentiel. Utilisez des virgules pour séparer un tableau de balises.

```yaml
Type: System.String[]
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

## SORTIES

### PSGetDscResourceInfo

`Find-DscResource` retourne un objet **PSGetDscResourceInfo** .

## REMARQUES

> [!IMPORTANT]
> Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security). Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.

## LIENS CONNEXES

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Module Uninstall](Uninstall-Module.md)
