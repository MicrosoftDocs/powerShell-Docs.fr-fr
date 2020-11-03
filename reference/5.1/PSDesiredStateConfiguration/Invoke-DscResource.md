---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203942"
---
# Invoke-DscResource

## SYNOPSIS
Exécute une méthode d’une ressource DSC spécifiée.

## SYNTAX

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## Description
L’applet de commande **Invoke-DscResource** exécute une méthode d’une ressource DSC (Desired State Configuration) Windows PowerShell spécifiée.
Avant d’exécuter cette applet de commande, définissez le mode d’actualisation du Configuration Manager local (LCM) sur désactivé.

Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration.
À l’aide de cette applet de commande, les produits de gestion de la configuration peuvent gérer Windows à l’aide des ressources DSC.
Cette applet de commande permet également de déboguer des ressources lorsque le moteur DSC ou le LCM s’exécute avec le débogage activé.

## EXEMPLES

### Exemple 1 : appeler la méthode Set d’une ressource en spécifiant ses propriétés obligatoires

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

Cette commande appelle la méthode **Set** d’une ressource nommée log et spécifie une propriété de **message** pour celle-ci.

### Exemple 2 : appeler la méthode de test d’une ressource pour un module spécifié

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

Cette commande appelle la méthode de **test** d’une ressource nommée WindowsProcess, qui se trouve dans le module nommé PSDesiredStateConfiguration.

## PARAMETERS

### -Méthode
Spécifie la méthode de la ressource appelée par cette applet de commande. Les valeurs acceptables pour ce paramètre sont les suivantes : obtenir, définir et tester.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ModuleName
Spécifie le nom du module à partir duquel cette applet de commande appelle la ressource spécifiée.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
Spécifie le nom de la ressource DSC à démarrer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Propriété
Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’applet de commande **Get-DscResource** pour découvrir les propriétés de ressources et leurs types.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### Microsoft. Management. infrastructure. CimInstance, System. Boolean

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Get-DscResource](Get-DscResource.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
