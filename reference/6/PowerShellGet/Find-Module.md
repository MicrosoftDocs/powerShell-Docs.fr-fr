---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 5795d48b2b76b4853d80d0cd79cb99d62332a39b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204290"
---
# Find-Module

## SYNOPSIS
Recherche les modules dans un référentiel qui correspondent aux critères spécifiés.

## SYNTAX

### Tous

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## Description

L' `Find-Module` applet de commande recherche les modules dans un référentiel qui correspondent aux critères spécifiés.
`Find-Module` retourne un objet **PSRepositoryItemInfo** pour chaque module qu’il trouve. Les objets peuvent être envoyés vers le pipeline vers des applets de commande telles que `Install-Module` .

La première fois `Find-Module` que vous tentez d’utiliser un référentiel, vous pouvez être invité à installer les mises à jour.
Si la source du référentiel n’est pas inscrite auprès de l’applet de commande `Register-PSRepository` , une erreur est retournée.

`Find-Module` retourne la version la plus récente d’un module si aucun paramètre n’est utilisé pour limiter la version. Pour obtenir la liste des versions d’un module dans un référentiel, utilisez le paramètre **AllVersions** .

Si le paramètre **MinimumVersion** est spécifié, `Find-Module` retourne la version du module qui est supérieure ou égale à la valeur minimale. Si une version plus récente est disponible dans le référentiel, la version la plus récente est retournée.

Si le paramètre **MaximumVersion** est spécifié, `Find-Module` retourne la version la plus récente du module qui ne dépasse pas la version spécifiée.

Si le paramètre **RequiredVersion** est spécifié, `Find-Module` retourne uniquement la version du module qui correspond exactement à la version spécifiée. `Find-Module` effectue une recherche dans tous les modules disponibles, car des conflits de noms entre les sources peuvent se produire.

Les exemples suivants utilisent l' [PowerShell Gallery](https://www.powershellgallery.com/) comme seul référentiel enregistré. `Get-PSRepository` affiche les dépôts inscrits. Si vous avez plusieurs référentiels inscrits, utilisez le `-Repository` paramètre pour spécifier le nom du référentiel.

## EXEMPLES

### Exemple 1 : Rechercher un module par son nom

Cet exemple recherche un module dans le référentiel par défaut.

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .

### Exemple 2 : Rechercher les modules avec des noms similaires

Cet exemple utilise le `*` caractère générique astérisque () pour rechercher des modules avec des noms similaires.

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

L' `Find-Module` applet de commande utilise le paramètre **Name** avec le `*` caractère générique astérisque () pour rechercher tous les modules qui contiennent **PowerShell** .

### Exemple 3 : Rechercher un module par version minimale

Cet exemple recherche la version minimale d’un module. Si le référentiel contient une version plus récente du module, la version la plus récente est retournée.

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . **MinimumVersion** spécifie la version **1.6.5** . `Find-Module` retourne la version PowerShellGet **2.1.0** , car elle dépasse la version minimale et est la version la plus récente.

### Exemple 4 : Rechercher un module par version spécifique

Cet exemple retourne un objet qui représente la version spécifique d’un module. Si la version spécifiée est introuvable, une erreur est retournée.

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . Le paramètre **RequiredVersion** spécifie la version **1.6.5** .

### Exemple 5 : Rechercher un module dans un référentiel spécifique

Cet exemple utilise le paramètre **repository** pour rechercher un module dans un référentiel spécifique.

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . Le paramètre de **dépôt** spécifie la recherche dans le référentiel **PSGallery** .

### Exemple 6 : Rechercher un module dans plusieurs référentiels

Cet exemple utilise `Register-PSRepository` pour spécifier un référentiel. `Find-Module` utilise le référentiel pour rechercher un module.

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

L' `Register-PSRepository` applet de commande inscrit un nouveau référentiel. Le paramètre **Name** attribue le nom **MySource** . Le paramètre **SourceLocation** spécifie l’adresse du dépôt.

L' `Find-Module` applet de commande utilise le paramètre **Name** avec le `*` caractère générique astérisque () pour spécifier le module **contoso** . Le paramètre de **dépôt** spécifie de rechercher deux dépôts, **PSGallery** et **MySource** .

### Exemple 7 : Rechercher un module qui contient une ressource DSC

Cette commande retourne les modules qui contiennent des ressources DSC. Le paramètre **includes** possède quatre fonctionnalités prédéfinies utilisées pour effectuer des recherches dans le référentiel. Utilisez l’onglet terminé pour afficher les quatre fonctionnalités prises en charge par le paramètre **includes** .

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

L' `Find-Module` applet de commande utilise le paramètre de **référentiel** pour effectuer une recherche dans le référentiel, **PSGallery** .
Le paramètre **includes** spécifie **DscResource** , qui est une fonctionnalité que le paramètre peut rechercher dans le référentiel.

### Exemple 8 : Rechercher un module à l’aide d’un filtre

Dans cet exemple, pour rechercher des modules, un filtre est utilisé pour effectuer une recherche dans le référentiel.

Pour un référentiel NuGet, le paramètre de **filtre** parcourt le nom, la description et les balises pour l’argument.

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

L' `Find-Module` applet de commande utilise le paramètre de **filtre** pour rechercher **AppDomain** dans le référentiel.

## PARAMETERS

### -AllowPrerelease

Comprend dans les modules de résultats marqués comme version préliminaire.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Spécifie d’inclure toutes les versions d’un module dans les résultats. Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .

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

Spécifie un tableau de commandes à rechercher dans les modules. Une commande peut être une fonction ou un flux de travail.

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

### -Credential

Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un module pour un fournisseur de package ou une source spécifiés.

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

### -DscResource

Spécifie le nom ou une partie du nom des modules qui contiennent des ressources DSC. Par conventions PowerShell, effectue une recherche **ou** lorsque vous fournissez plusieurs arguments.

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

### -Filter

Spécifie un filtre basé sur la syntaxe de recherche spécifique au fournisseur **PackageManagement** . Pour les modules NuGet, ce paramètre est l’équivalent de la recherche à l’aide de la barre de recherche sur le site Web [PowerShell Gallery](https://www.powershellgallery.com/) .

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

### -IncludeDependencies

Indique que cette opération comprend tous les modules qui dépendent du module spécifié dans le paramètre **Name** .

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

### -Comprend

Retourne uniquement les modules qui incluent des genres spécifiques de fonctionnalités PowerShell. Par exemple, vous souhaiterez peut-être Rechercher uniquement les modules qui incluent **DSCResource** . Les valeurs acceptables pour ce paramètre sont les suivantes :

- Applet de commande
- DscResource
- Fonction
- RoleCapability

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version maximale ou la plus récente du module à inclure dans les résultats de la recherche.
**MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

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

### -MinimumVersion

Spécifie la version minimale du module à inclure dans les résultats. **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

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

Spécifie les noms des modules à rechercher dans le référentiel. Une liste séparée par des virgules de noms de modules est acceptée. Les caractères génériques sont acceptés.

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

Utilisez le paramètre de **dépôt** pour spécifier le référentiel dans lequel Rechercher un module. Utilisé lorsque plusieurs dépôts sont inscrits. Accepte une liste de référentiels séparés par des virgules. Pour inscrire un dépôt, utilisez `Register-PSRepository` . Pour afficher les dépôts inscrits, utilisez `Get-PSRepository` .

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

Spécifie le numéro de version exact du module à inclure dans les résultats. **RequiredVersion** ne peut pas être utilisé dans la même commande que **MinimumVersion** ou **MaximumVersion** .

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

### -RoleCapability

Spécifie un tableau de capacités de rôle.

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

### -Tag

Spécifie un tableau de balises. Exemples de balises : **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** ou **PSModule** .

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

### System.String[]

### System.String

### System.Uri

### System. Management. Automation. PSCredential

## SORTIES

### PSRepositoryItemInfo

`Find-Module` crée des objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le pipeline vers des applets de commande telles que `Install-Module` .

## REMARQUES

Cette applet de commande s’exécute sur les versions PowerShell 5,0 ou ultérieures de PowerShell, sur Windows 7, ou Windows 2008 R2 et versions ultérieures de Windows.

## LIENS CONNEXES

[Get-PSRepository](Get-PSRepository.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[Register-PSRepository](Register-PSRepository.md)
