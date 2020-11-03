---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203930"
---
# Start-DscConfiguration

## SYNOPSIS
Applique la configuration à des nœuds.

## SYNTAX

### ComputerNameAndPathSet (par défaut)

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimSessionAndPathSet

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L'applet de commande **Start-DscConfiguration** applique la configuration à des nœuds.
Lorsqu’elle est utilisée avec le paramètre *UseExisting* , la configuration existante sur l’ordinateur cible est appliquée.
Spécifiez les ordinateurs auxquels vous souhaitez appliquer la configuration en spécifiant des noms d’ordinateur ou à l’aide de sessions Common Information Model (CIM).

Par défaut, cette applet de commande crée une tâche et retourne un objet **Job** .
Pour plus d’informations sur les tâches en arrière-plan, tapez `Get-Help about_Jobs` .
Pour utiliser cette applet de commande de manière interactive, spécifiez le paramètre *Wait* .

Spécifiez le paramètre *Verbose* pour afficher en détail de ce que fait l'applet de commande lorsqu'elle applique des paramètres de configuration.

## EXEMPLES

### Exemple 1 : appliquer les paramètres de configuration

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

Cette commande applique les paramètres de configuration de C:\DSC\Configurations\ à chaque ordinateur possédant des paramètres dans ce dossier.
La commande retourne des objets **Job** pour chaque nœud cible visé par le déploiement.

### Exemple 2 : appliquer des paramètres de configuration et attendre la fin de la configuration

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

Cette commande applique la configuration de C:\DSC\Configurations\ à l'ordinateur local.
La commande retourne des objets **Job** pour chaque nœud cible visé par le déploiement (dans ce cas, uniquement l'ordinateur local).
Cet exemple spécifie le paramètre *Verbose* .
Par conséquent, la commande envoie des messages à la console à mesure qu’elle se poursuit.
La commande comprend le paramètre *Wait* .
Par conséquent, vous ne pouvez pas utiliser la console tant que la commande n’a pas terminé toutes les tâches de configuration.

### Exemple 3 : appliquer des paramètres de configuration à l’aide d’une session CIM

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

Cet exemple applique les paramètres de configuration à un ordinateur spécifié.
L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.
Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.

La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.
La commande vous invite à entrer un mot de passe.
Pour plus d'informations, voir `Get-Help NewCimSession`.

La deuxième commande applique les paramètres de configuration de C:\DSC\Configurations\ aux ordinateurs identifiés par les objets **CimSession** stockés dans la variable $session.
Dans cet exemple, la variable $Session contient une session CIM uniquement pour l'ordinateur Server01.
La commande applique la configuration.
La commande crée des objets **Job** pour chaque ordinateur configuré.

## PARAMETERS

### -CimSession
Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.
Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .
La valeur par défaut est la session active sur l’ordinateur local.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Spécifie un tableau de noms d'ordinateurs.
Ce paramètre limite les ordinateurs qui ont des documents de configuration dans le paramètre *path* à ceux spécifiés dans le tableau.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
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
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Arrête l’opération de configuration en cours d’exécution sur l’ordinateur cible et commence la nouvelle opération de Start-Configuration.
Si la propriété **RefreshMode** de l’Configuration Manager local est définie sur **pull** , la spécification de ce paramètre le remplace par **Push** .

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

### -JobName
Spécifie le nom convivial d'une tâche.
Si vous spécifiez ce paramètre, l'applet de commande s'exécute en tant que tâche et retourne un objet **Job** .

Par défaut, Windows PowerShell attribue le nom JobN, où N est un entier.

Si vous spécifiez le paramètre *Wait* , ne spécifiez pas ce paramètre.

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

### -Path
Spécifie le chemin d'accès d'un dossier qui contient les fichiers de paramètres de configuration.
Cette applet de commande publie et applique ces paramètres de configuration aux ordinateurs qui ont des fichiers de paramètres dans le chemin d’accès spécifié.
Chaque nœud cible doit avoir un fichier de paramètres au format suivant : NetBIOS Name. mof.

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
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

### -UseExisting
Indique que cette applet de commande applique la configuration existante.
La configuration peut exister sur l’ordinateur cible en cas d’adoption à l’aide de **Start-DscConfiguration** ou de la publication à l’aide de l’applet de commande Publish-DscConfiguration.

Avant de spécifier ce paramètre pour cette applet de commande, passez en revue les informations [contenues dans Nouveautés de Windows PowerShell 5,0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait
Indique que l’applet de commande bloque la console jusqu’à ce qu’elle termine toutes les tâches de configuration.

Si vous spécifiez ce paramètre, ne spécifiez pas le paramètre *JobName* .

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
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/overview)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)
