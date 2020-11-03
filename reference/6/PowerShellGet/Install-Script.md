---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: ecae1ba3a3aea6628817bab2f09fc23e23162f03
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204278"
---
# Install-Script

## SYNOPSIS
Installe un script.

## SYNTAX

### NameParameterSet (par défaut)

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Install-Script` applet de commande acquiert une charge utile de script à partir d’un référentiel, vérifie que la charge utile est un script PowerShell valide et copie le fichier de script vers un emplacement d’installation spécifié.

Les référentiels par défaut `Install-Script` fonctionnent sur peuvent être configurés par le biais des `Register-PSRepository` applets de commande,, `Set-PSRepository` `Unregister-PSRepository` et `Get-PSRepository` . En cas de fonctionnement sur plusieurs dépôts, `Install-Script` installe le premier script qui correspond aux critères de recherche spécifiés ( **Name** , **MinimumVersion** ou **MaximumVersion** ) à partir du premier référentiel sans aucune erreur.

## EXEMPLES

### Exemple 1 : Rechercher un script et l’installer

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

La première commande recherche le script nommé `Required-Script2` à partir du référentiel local1 et affiche les résultats.

La deuxième commande recherche le `Required-Script2` script, puis utilise l’opérateur de pipeline pour le passer à l' `Install-Script` applet de commande pour l’installer.

La troisième commande utilise l' `Get-Command` applet de commande pour obtenir `Required-Script2` , puis affiche les résultats.

La quatrième commande utilise l' `Get-InstalledScript` applet de commande pour obtenir `Required-Script2` et afficher les résultats.

La cinquième commande récupère `Required-Script2` et utilise l’opérateur de pipeline pour la passer à l' `Format-List` applet de commande afin de mettre en forme la sortie.

### Exemple 2 : installer un script avec l’étendue AllUsers

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

La première commande installe le script nommé `Required-Script3` et lui attribue l’étendue ALLUSERS.

La deuxième commande obtient le script installé `Required-Script3` et affiche des informations à son sujet.

La troisième commande récupère `Required-Script3` et utilise l’opérateur de pipeline pour la passer à l' `Format-List` applet de commande afin de mettre en forme la sortie.

### Exemple 3 : installer un script et ses dépendances

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

La première commande recherche le script nommé `Script-WithDependencies2` et ses dépendances dans le référentiel local1 et affiche les résultats.

La deuxième commande installe `Script-WithDependencies2` .

La troisième commande utilise l' `Get-InstalledScript` applet de commande script pour obtenir les scripts installés et afficher les résultats.

La quatrième commande utilise l' `Get-InstalledModule` applet de commande pour obtenir les modules installés et afficher les résultats.

La cinquième commande utilise l' `Find-Script` applet de commande pour rechercher les scripts dont le nom commence par `Required-Script` et afficher les résultats.

La sixième commande installe les scripts dont le nom commence par `Required-Script` dans le référentiel local1.

La commande finale obtient les scripts installés et affiche les résultats.

## PARAMETERS

### -AcceptLicense

Accepter automatiquement le contrat de licence au cours de l’installation si le module l’exige.

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

Vous permet d’installer un script marqué comme version préliminaire.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

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

### -Credential

Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un script pour un fournisseur de package ou une source spécifiés.

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

### -InputObject

Utilisé pour l’entrée de pipeline.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version maximale d’un seul script à installer. Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs scripts. Les paramètres **MaximumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie la version minimale d’un script unique à installer. Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs scripts. Les paramètres **MinimumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms de scripts à installer.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoPathUpdate

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

### -PassThru

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

Spécifie le nom convivial d’un référentiel inscrit avec l’applet de commande `Register-PSRepository` . La valeur par défaut est tous les dépôts inscrits.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie le numéro de version exact du script à installer.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Étendue

Spécifie l’étendue d’installation du script.
Les valeurs valides sont : AllUsers et CurrentUser.

L’étendue AllUsers permet d’installer les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur, c’est-à-dire `$env:ProgramFiles\WindowsPowerShell\Scripts` .

L’étendue CurrentUser permet d’installer les modules uniquement dans `$home\Documents\WindowsPowerShell\Scripts` , afin que le module ne soit disponible que pour l’utilisateur actuel.

Quand aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la session active :

- Pour une session PowerShell avec élévation de privilèges, l' **étendue** est définie par défaut sur ALLUSERS ;
- Pour les sessions PowerShell non élevées dans [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) et ultérieures, la **portée** est CurrentUser ;
- Pour les sessions PowerShell non élevées dans PowerShellGet versions 1.6.7 et antérieures, la **portée** n’est pas définie et `Install-Module` échoue.

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

### System.String[]

### System. Management. Automation. PSObject []

### System.String

### System.Uri

### System. Management. Automation. PSCredential

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Find-Script](Find-Script.md)

[Publish-Script](Publish-Script.md)

[Save-Script](Save-Script.md)

[Uninstall-Script](Uninstall-Script.md)

[Update-Script](Update-Script.md)
