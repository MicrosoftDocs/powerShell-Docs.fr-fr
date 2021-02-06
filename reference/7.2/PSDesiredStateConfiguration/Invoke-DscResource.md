---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597764"
---
# Invoke-DscResource

## SYNOPSIS
Exécute une méthode d’une ressource DSC (Desired State Configuration) PowerShell spécifiée.

## SYNTAXE

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## Description

La cmdlet `Invoke-DscResource` exécute une méthode d’une ressource Desired State Configuration (DSC) PowerShell spécifiée.

Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration. À l’aide de cette applet de commande, les produits de gestion de la configuration peuvent gérer Windows ou Linux à l’aide de ressources DSC. Cette cmdlet de commande permet également de déboguer des ressources lorsque le moteur DSC s’exécute avec le débogage activé.

> [!NOTE]
> `Invoke-DscResource` est une fonctionnalité expérimentale de PowerShell 7. Pour utiliser l’applet de commande, vous devez l’activer à l’aide de la commande suivante.
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## EXEMPLES

### Exemple 1 : appeler la méthode Set d’une ressource en spécifiant ses propriétés obligatoires

Cet exemple appelle la méthode **Set** d’une ressource nommée **WindowsProcess** et fournit les propriétés **path** et **arguments** obligatoires pour démarrer le processus Windows spécifié.

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### Exemple 2 : appeler la méthode de test d’une ressource pour un module spécifié

Cet exemple appelle la méthode de **test** d’une ressource nommée **WindowsProcess**, qui se trouve dans le module nommé **PSDesiredStateConfiguration**.

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## PARAMETERS

### -Méthode

Spécifie la méthode de la ressource appelée par cette applet de commande. Les valeurs acceptables pour ce paramètre sont les suivantes : **obtenir**, **définir** et **Tester**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleName

Spécifie le nom du module à partir duquel cette applet de commande appelle la ressource spécifiée.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Propriété

Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

### Microsoft. PowerShell. Commands. ModuleSpecification

## SORTIES

### System.Object

## REMARQUES

- Auparavant, les ressources Windows PowerShell 5,1 étaient exécutées sous le contexte système, sauf si elles étaient spécifiées avec le contexte utilisateur à l’aide de la clé **PsDscRunAsCredential**. Dans PowerShell 7,0, les ressources s’exécutent dans le contexte de l’utilisateur, et **PsDscRunAsCredential** n’est plus pris en charge. Les configurations précédentes qui utilisent cette clé lèveront une exception.

- Depuis PowerShell 7, `Invoke-DscResource` ne prend plus en charge l’appel des ressources DSC WMI. Sont incluses les ressources **File** et **Log** dans **PSDesiredStateConfiguration**.

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscResource](Get-DscResource.md)
