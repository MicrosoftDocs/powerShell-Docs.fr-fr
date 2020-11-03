---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203074"
---
# Test-DscConfiguration

## SYNOPSIS
Teste si la configuration réelle sur les nœuds correspond à la configuration souhaitée.

## SYNTAX

### ComputerNameSet (par défaut)

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### ComputerNameAndPathSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### ComputerNameAndReferenceConfigurationSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionAndPathSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### CimSessionAndReferenceConfigurationSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## Description
L'applet de commande **Test-DscConfiguration** teste si la configuration réelle sur les nœuds correspond à la configuration souhaitée.
Spécifiez les ordinateurs pour lesquels vous souhaitez tester les configurations à l’aide de noms d’ordinateur ou de sessions Common Information Model (CIM).
Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande teste la configuration de l'ordinateur local.

Si les configurations souhaitées et réelles correspondent, l’applet de commande retourne la valeur de chaîne « true ».
Sinon, elle retourne une valeur de chaîne de « false ».

## EXEMPLES

### Exemple 1 : configuration de test pour l’ordinateur local

```
PS C:\> Test-DscConfiguration
```

Cette commande teste la configuration de l'ordinateur local.

### Exemple 2 : configuration de test pour un ordinateur spécifié

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

Cet exemple teste la configuration d'un ordinateur spécifié par une session CIM.
L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.
Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.

La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.
La commande vous invite à entrer un mot de passe.
Pour plus d'informations, voir `Get-Help New-CimSession`.

La deuxième commande teste la configuration des ordinateurs identifiés par les objets **CimSession** stockés dans la variable $Session (dans ce cas, l'ordinateur nommé Server01).

### Exemple 3 : configurations de test avec des résultats détaillés

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

Cette commande teste les configurations pour un ensemble d’ordinateurs spécifiés par le paramètre *ComputerName* et retourne des informations détaillées qui incluent l’état global, les ressources qui sont dans l’état souhaité, les ressources qui ne sont pas dans l’état souhaité et le nom de l’ordinateur.

### Exemple 4 : configurations de test spécifiées dans un dossier

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

Cette commande teste les configurations définies dans un dossier spécifié par le paramètre *path* .
Les configurations sont testées sur un ensemble d’ordinateurs, chacun identifié par le nom de fichier du fichier de configuration.

### Exemple 5 : configurations de test spécifiées dans un fichier

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

Cette commande teste une configuration définie dans un fichier par rapport à un ensemble d’ordinateurs spécifié par le paramètre *ComputerName* .

## PARAMETERS

### -AsJob
Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.

Si vous spécifiez le paramètre *AsJob* , la commande retourne un objet qui représente le travail, puis affiche l’invite de commandes.
Vous pouvez continuer à travailler dans la session jusqu’à ce que la tâche se termine.
La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.
Pour gérer la tâche, utilisez les applets de commande Job.
Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.

Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir Windows PowerShell avec l’option Exécuter en tant qu’administrateur.
Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

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

### -CimSession
Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.
Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .
La valeur par défaut est la session active sur l’ordinateur local.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Spécifie un tableau de noms d’ordinateurs sur lequel cette applet de commande teste la configuration.
L’applet de commande teste le document de configuration à l’emplacement spécifié par le paramètre *path* à ces ordinateurs.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Spécifie un nom d'utilisateur et un mot de passe, sous la forme d'un objet **PSCredential** , pour l'ordinateur cible.
Pour obtenir un objet **PSCredential** , utilisez l'applet de commande Get-Credential.
Pour plus d'informations, voir `Get-Help Get-Credential`.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Detailed
Indique que cette applet de commande retourne un résultat détaillé de la comparaison du document de configuration avec l’état souhaité des nœuds.
Le résultat comprend des informations telles que l’état global, les ressources qui sont dans l’état souhaité, les ressources qui ne sont pas dans l’état souhaité et le nom de l’ordinateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Spécifie le chemin d’accès d’un dossier qui contient des fichiers de document de configuration.
L’applet de commande teste la configuration par rapport à l’état souhaité des ordinateurs spécifiés par le paramètre *ComputerName* ou *CimSession* .

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceConfiguration
Spécifie le chemin d’accès du fichier du document de configuration.
Cette applet de commande teste la configuration par rapport à l’état réel des ordinateurs spécifiés par le paramètre *ComputerName* ou *CimSession* .

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.
Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.
Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.

```yaml
Type: System.Int32
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

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)
