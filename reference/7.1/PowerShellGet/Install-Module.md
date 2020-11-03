---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: e2e4dc34fb84a54fb92cc4c809c84d67beafe576
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205833"
---
# Install-Module

## SYNOPSIS
Télécharge un ou plusieurs modules à partir d’un référentiel et les installe sur l’ordinateur local.

## SYNTAX

### NameParameterSet (par défaut)

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Install-Module` applet de commande obtient un ou plusieurs modules qui répondent aux critères spécifiés à partir d’un référentiel en ligne. L’applet de commande vérifie que les résultats de la recherche sont des modules valides et copie les dossiers du module vers l’emplacement d’installation. Les modules installés ne sont pas automatiquement importés après l’installation.
Vous pouvez filtrer le module installé en fonction des versions minimale, maximale et exacte des modules spécifiés.

Si le module en cours d’installation a le même nom ou la même version, ou contient des commandes dans un module existant, des messages d’avertissement s’affichent. Après avoir confirmé que vous voulez installer le module et remplacer les avertissements, utilisez les `-Force` `-AllowClobber` paramètres et. Selon les paramètres de votre référentiel, vous devrez peut-être répondre à une invite pour que l’installation du module se poursuive.

Ces exemples utilisent le [PowerShell Gallery](https://www.powershellgallery.com/) comme seul référentiel enregistré. `Get-PSRepository` affiche les dépôts inscrits. Si vous avez plusieurs référentiels inscrits, utilisez le `-Repository` paramètre pour spécifier le nom du référentiel.

## EXEMPLES

### Exemple 1 : Rechercher et installer un module

Cet exemple recherche un module dans le référentiel et installe le module.

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

Le `Find-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . Par défaut, la version la plus récente du module est téléchargée à partir du référentiel. L’objet est envoyé dans le pipeline à l’applet de commande `Install-Module` . `Install-Module` installe le module pour tous les utilisateurs dans `$env:ProgramFiles\PowerShell\Modules` .

### Exemple 2 : installer un module par nom

Dans cet exemple, la version la plus récente du module **PowerShellGet** est installée.

```powershell
Install-Module -Name PowerShellGet
```

Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . Par défaut, la version la plus récente du module est téléchargée à partir du référentiel et installée.

### Exemple 3 : installer un module en utilisant sa version minimale

Dans cet exemple, la version minimale du module **PowerShellGet** est installée. Le paramètre **MinimumVersion** spécifie la version la plus basse du module à installer. Si une version plus récente du module est disponible, cette version est téléchargée et installée pour tous les utilisateurs.

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . Le paramètre **MinimumVersion** spécifie que la version **2.0.1** est téléchargée à partir du référentiel et installée. Étant donné que la version **2.0.4** est disponible, cette version est téléchargée et installée pour tous les utilisateurs.

### Exemple 4 : installer une version spécifique d’un module

Dans cet exemple, une version spécifique du module **PowerShellGet** est installée.

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** . Le paramètre **RequiredVersion** spécifie que la version **2.0.0** est téléchargée et installée pour tous les utilisateurs.

### Exemple 5 : installer un module uniquement pour l’utilisateur actuel

Cet exemple télécharge et installe la version la plus récente d’un module, uniquement pour l’utilisateur actuel.

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .
`Install-Module` télécharge et installe la version la plus récente de **PowerShellGet** dans le répertoire de l’utilisateur actuel, `$home\Documents\PowerShell\Modules` .

## PARAMETERS

### -AcceptLicense

Pour les modules qui nécessitent une licence, **AcceptLicense** accepte automatiquement le contrat de licence lors de l’installation. Pour plus d’informations, consultez [modules nécessitant l’acceptation](/powershell/scripting/gallery/concepts/module-license-acceptance)de la licence.

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

### -AllowClobber

Remplace les messages d’avertissement relatifs aux conflits d’installation concernant les commandes existantes sur un ordinateur.
Remplace les commandes existantes qui portent le même nom que les commandes installées par un module.
**AllowClobber** et **force** peuvent être utilisés ensemble dans une `Install-Module` commande.

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

Vous permet d’installer un module marqué en tant que version préliminaire.

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

Vous invite à confirmer l’exécution de l' `Install-Module` applet de commande.

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

### -Force

Installe un module et remplace les messages d’avertissement relatifs aux conflits d’installation du module. Si un module portant le même nom existe déjà sur l’ordinateur, **force** autorise l’installation de plusieurs versions. S’il existe un module avec le même nom et la même version, **force** remplace cette version. **Force** et **AllowClobber** peuvent être utilisés ensemble dans une `Install-Module` commande.

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

Spécifie la version maximale d’un module unique à installer. La version installée doit être inférieure ou égale à **MaximumVersion** . Si vous souhaitez installer plusieurs modules, vous ne pouvez pas utiliser **MaximumVersion** . **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même `Install-Module` commande.

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

Spécifie la version minimale d’un module unique à installer. La version installée doit être supérieure ou égale à **MinimumVersion** . Si une version plus récente du module est disponible, la version la plus récente est installée. Si vous souhaitez installer plusieurs modules, vous ne pouvez pas utiliser **MinimumVersion** .
**MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même `Install-Module` commande.

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

Spécifie les noms exacts des modules à installer à partir de la galerie en ligne. Une liste séparée par des virgules de noms de modules est acceptée. Le nom du module doit correspondre au nom du module dans le référentiel. Utilisez `Find-Module` pour obtenir une liste de noms de modules.

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

### -PassThru

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
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

Utilisez le paramètre de **dépôt** pour spécifier le référentiel utilisé pour télécharger et installer un module. Utilisé lorsque plusieurs dépôts sont inscrits. Spécifie le nom d’un référentiel inscrit dans la `Install-Module` commande. Pour inscrire un dépôt, utilisez `Register-PSRepository` .
Pour afficher les dépôts inscrits, utilisez `Get-PSRepository` .

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

Spécifie la version exacte d’un module unique à installer. S’il n’existe aucune correspondance dans le référentiel pour la version spécifiée, une erreur s’affiche. Si vous souhaitez installer plusieurs modules, vous ne pouvez pas utiliser **RequiredVersion** . **RequiredVersion** ne peut pas être utilisé dans la même `Install-Module` commande que **MinimumVersion** ou **MaximumVersion** .

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

Spécifie l’étendue d’installation du module. Les valeurs acceptables pour ce paramètre sont **ALLUSERS** et **CurrentUser** .

L’étendue **ALLUSERS** installe les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur :

`$env:ProgramFiles\PowerShell\Modules`

Le **CurrentUser** installe les modules dans un emplacement accessible uniquement à l’utilisateur actuel de l’ordinateur. Par exemple :

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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

Vous permet d’installer une version plus récente d’un module qui existe déjà sur votre ordinateur. Par exemple, lorsqu’un module existant est signé numériquement par un éditeur approuvé, mais que la nouvelle version n’est pas signée numériquement par un éditeur approuvé.

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

### -WhatIf

Montre ce qui se passe si une `Install-Module` commande a été exécutée. L’applet de commande n’est pas exécutée.

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

### PSRepositoryItemInfo

`Find-Module` crée les objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le dessous du pipeline `Install-Module` .

### System.String[]

### System. Management. Automation. PSObject []

### System.String

### System. Management. Automation. PSCredential

### System.Uri

## SORTIES

### Microsoft. PowerShell. Commands. PSRepositoryItemInfo

Lors de l’utilisation du paramètre **PassThru** , `Install-Module` génère un objet **PSRepositoryItemInfo** pour le module. Il s’agit des mêmes informations que celles que vous obteniez de l’applet de commande `Find-Module` .

## REMARQUES

`Install-Module` s’exécute sur PowerShell 5,0 ou versions ultérieures, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.

En guise de meilleure pratique de sécurité, évaluez le code d’un module avant d’exécuter des applets de commande ou des fonctions pour la première fois. Pour empêcher l’exécution de modules contenant du code malveillant, les modules installés ne sont pas automatiquement importés après l’installation.

Si le nom de module spécifié par le paramètre **Name** n’existe pas dans le référentiel, `Install-Module` retourne une erreur.

Pour installer plusieurs modules, utilisez le paramètre **Name** et spécifiez un tableau de noms de module séparés par des virgules. Si vous spécifiez plusieurs noms de module, vous ne pouvez pas utiliser **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** . `Find-Module` crée les objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le dessous du pipeline `Install-Module` . Le pipeline est une autre façon de spécifier plusieurs modules à installer dans une seule commande.

Par défaut, les modules de l’étendue de **ALLUSERS** sont installés dans `$env:ProgramFiles\PowerShell\Modules` . La valeur par défaut empêche toute confusion quand vous installez les ressources DSC (Desired State Configuration) PowerShell.

L’installation d’un module échoue et ne peut pas être importée s’il n’a pas `.psm1` `.psd1` de, ou `.dll` du même nom dans le dossier. Utilisez le paramètre **force** pour installer le module.

Si la version d’un module existant correspond au nom spécifié par le paramètre **Name** et que le paramètre **MinimumVersion** ou **RequiredVersion** n’est pas utilisé, `Install-Module` continue sans assistance, mais n’installe pas le module.

Si la version d’un module existant est supérieure à la valeur du paramètre **MinimumVersion** ou égale à la valeur du paramètre **RequiredVersion** , `Install-Module` continue sans assistance, mais n’installe pas le module.

Si le module existant ne correspond pas aux valeurs spécifiées par les paramètres **MinimumVersion** ou **RequiredVersion** , une erreur se produit dans la `Install-Module` commande. Par exemple, si la version du module installé existant est inférieure à la valeur **MinimumVersion** ou différente de la valeur **RequiredVersion** .

Une installation de module installe également tous les modules dépendants spécifiés comme requis par l’éditeur du module.
L’éditeur spécifie les modules requis et leurs versions dans le manifeste du module.

## LIENS CONNEXES

[Find-Module](Find-Module.md)

[Get-PSRepository](Get-PSRepository.md)

[Module d’importation](../Microsoft.PowerShell.Core/Import-Module.md)

[Publish-Module](Publish-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[about_Module](../Microsoft.PowerShell.Core/About/about_Modules.md)
