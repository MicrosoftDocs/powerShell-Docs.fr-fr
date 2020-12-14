---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: 1cee4ac54bf83d387f61a4842104a80512a8b223
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891522"
---
# Find-RoleCapability

## SYNOPSIS
Recherche les capacités de rôle dans des modules.

## SYNTAXE

### Tous

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## Description

L' `Find-RoleCapability` applet de commande recherche les référentiels inscrits pour rechercher les modules et les capacités de rôle PowerShell.

Pour chaque fonctionnalité de rôle trouvée par `Find-RoleCapability` , un objet **PSGetRoleCapabilityInfo** est retourné. Les objets **PSGetRoleCapabilityInfo** peuvent être envoyés vers le pipeline vers les `Install-Module` applets de commande ou `Save-Module` .

Les fonctionnalités de rôle PowerShell définissent les commandes et les applications qui sont disponibles pour un utilisateur sur un point de terminaison d’administration (JEA) juste suffisant. Les capacités de rôle sont définies par des fichiers avec une `.psrc` extension.

## EXEMPLES

### Exemple 1 : Rechercher des fonctionnalités de rôle

`Find-RoleCapability` recherche des fonctionnalités de rôle dans chaque dépôt inscrit. Pour effectuer une recherche dans un référentiel spécifique, utilisez le paramètre de **référentiel** .

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### Exemple 2 : Rechercher des fonctionnalités de rôle par nom

`Find-RoleCapability` recherche des fonctionnalités de rôle par nom. Utilisez des virgules pour séparer un tableau de noms.

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### Exemple 3 : Rechercher et enregistrer le module d’une fonctionnalité de rôle

L' `Find-RoleCapability` applet de commande recherche une capacité de rôle et envoie l’objet vers le pipeline.
`Save-Module` enregistre le module de la fonctionnalité de rôle dans un système de fichiers. `Get-ChildItem` affiche le contenu du répertoire du module.

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .
L’objet est envoyé dans le pipeline. `Save-Module` utilise le paramètre **path** pour l’emplacement du système de fichiers pour enregistrer le module. Une fois le module enregistré, `Get-ChildItem` spécifie le **chemin d’accès** du module et affiche le contenu du répertoire du module **JeaExamples** .

### Exemple 4 : Rechercher et installer le module d’une fonctionnalité de rôle

`Find-RoleCapability` recherche le module et envoie l’objet vers le dessous du pipeline. `Install-Module` installe le module. Après l’installation, utilisez `Get-InstalledModule` pour afficher les résultats.

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .
L’objet est envoyé dans le pipeline. `Install-Module` utilise le paramètre **Verbose** pour afficher les messages d’état lors de l’installation. Une fois l’installation terminée, la `Get-InstalledModule` sortie confirme que le module **JeaExamples** a été installé.

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

Indique que cette applet de commande obtient toutes les versions d’un module. Le paramètre **AllVersions** affiche chacune des versions disponibles d’un module.

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

Spécifie la version maximale du module à inclure dans les résultats. Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

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

Spécifie la version minimale du module à inclure dans les résultats. Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

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

Spécifie le nom du module dans lequel rechercher les fonctionnalités de rôle. La valeur par défaut est tous les modules.

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

Spécifie le nom d’une capacité de rôle. La valeur par défaut est toutes les capacités de rôle. Utilisez des virgules pour séparer un tableau de noms de ressources.

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

Spécifie un référentiel dans lequel Rechercher des fonctionnalités de rôle. Utilisez des virgules pour séparer un tableau de noms de référentiel.

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

### System.Uri

### System. Management. Automation. PSCredential

## SORTIES

### PSGetRoleCapabilityInfo

L' `Find-RoleCapability` applet de commande retourne un objet **PSGetRoleCapabilityInfo** .

## REMARQUES

> [!IMPORTANT]
> Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security). Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.

## LIENS CONNEXES

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[New-PSRoleCapabilityFile](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[Save-Module](Save-Module.md)
