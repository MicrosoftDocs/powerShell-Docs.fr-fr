---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 1cd86a1c9abe6c8a4af9f68ed17ea1876ff1bd20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204166"
---
# Find-Command

## SYNOPSIS
Recherche des commandes PowerShell dans des modules.

## SYNTAX

### Tous

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## Description

L' `Find-Command` applet de commande recherche les commandes PowerShell, telles que les applets de commande, les alias, les fonctions et les workflows. `Find-Command` recherche des modules dans les référentiels inscrits.

Pour chaque commande trouvée par `Find-Command` , un objet **PSGetCommandInfo** est retourné. L’objet **PSGetCommandInfo** peut être envoyé dans le pipeline à l’applet de commande `Install-Module` .
`Install-Module` installe le module qui contient la commande.

## EXEMPLES

### Exemple 1 : Rechercher toutes les commandes dans un dépôt spécifié

L' `Find-Command` applet de commande recherche des modules dans un dépôt inscrit.

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

`Find-Command` utilise le paramètre de **référentiel** pour spécifier le nom d’un dépôt inscrit. Les objets sont envoyés dans le pipeline. `Select-Object` reçoit les objets et utilise le **premier** paramètre pour afficher les 10 premiers résultats.

### Exemple 2 : Rechercher une commande par nom

`Find-Command` peut utiliser le nom d’une commande pour localiser le module dans un référentiel. Il est possible qu’un nom de commande existe dans plusieurs **ModuleNames** .

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

`Find-Command` utilise le paramètre de **référentiel** pour rechercher le **PSGallery** . Le paramètre **Name** spécifie la commande **-TargetResource** .

### Exemple 3 : Rechercher les commandes par nom et installer le module

`Find-Command` peut localiser la commande et le module, puis envoyer l’objet à `Install-Module` . Si une commande est incluse dans plusieurs modules, utilisez le `Find-Command` paramètre **de nom du module** applets de commande.
Dans le cas contraire, il est possible que les modules que vous ne souhaitiez pas installer soient installés.

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

`Find-Command` utilise le paramètre **Name** pour spécifier la commande **-TargetResource** . Le paramètre de **référentiel** effectue une recherche dans le **PSGallery** . Le paramètre **modulename** spécifie le module que vous souhaitez installer, **SystemLocaleDsc** . L’objet est envoyé vers le pipeline vers `Install-Module` et le module est installé. Une fois l’installation terminée, vous pouvez utiliser `Get-InstalledModule` pour afficher les résultats.

### Exemple 4 : Rechercher une commande et enregistrer son module

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

`Find-Command` utilise les paramètres **Name** et **repository** pour rechercher la commande **Invoke-ScriptAnalyzer** dans le référentiel **PSGallery** . L’objet est envoyé dans le pipeline à `Save-Module` . Le paramètre **path** détermine l’emplacement d’enregistrement du module. **Verbose** est un paramètre facultatif, mais affiche la sortie de l’État dans la console PowerShell. La sortie détaillée est avantageuse pour la résolution des problèmes.

## PARAMETERS

### -AllowPrerelease

Comprend les modules marqués comme version préliminaire dans les résultats.

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

Indique que cette applet de commande obtient toutes les versions d’un module.

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

Recherche des modules en fonction de la syntaxe de recherche du fournisseur **PackageManagement** . Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .

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

Spécifie le nom d’un module dans lequel Rechercher des commandes. La valeur par défaut est tous les modules.

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

Spécifie le nom de la commande à rechercher dans un référentiel. Utilisez des virgules pour séparer un tableau de noms de commandes.

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

Spécifie le référentiel dans lequel Rechercher des commandes. Utilisez des virgules pour séparer un tableau de noms de référentiel. La valeur par défaut est tous les dépôts.

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

Spécifie la version du module à inclure dans les résultats.

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

### PSGetCommandInfo

`Find-Command` génère un objet **PSGetCommandInfo** .

## REMARQUES

## LIENS CONNEXES

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Save-Module](Save-Module.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-Module](Uninstall-Module.md)

