---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203073"
---
# Update-DscConfiguration

## SYNOPSIS
Recherche une configuration mise à jour dans le serveur collecteur et l’applique.

## SYNTAX

### ComputerNameSet (par défaut)

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L' `Update-DscConfiguration` applet de commande se connecte à un serveur collecteur, télécharge la configuration si elle diffère de la valeur actuelle sur le nœud, puis applique la configuration à l’ordinateur.

Cette applet de commande est disponible uniquement dans le cadre du [correctif cumulatif de novembre 2014 pour Windows RT 8,1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) à partir de la bibliothèque de support Microsoft.

## EXEMPLES

### Exemple 1 : mettre à jour une configuration

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

Après avoir exécuté cette commande, le serveur se connecte au service d’extraction inscrit, télécharge la dernière configuration attribuée, puis l’applique.
Les paramètres-Wait et-verbose sont facultatifs.
Lorsque vous travaillez de manière interactive, ces paramètres regroupés activent les commentaires en temps réel sur la progression et la réussite ou l’échec lors de l’application de la configuration.

### Exemple 2 : mettre à jour une configuration en se connectant via une session CIM

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.
La commande vous invite à entrer un mot de passe.
Pour plus d'informations, voir `Get-Help New-CimSession`.

La deuxième commande met à jour l’ordinateur spécifié dans le **CimSession** stocké dans $session.
La commande spécifie le paramètre *Wait* .
La console n’accepte pas de commandes supplémentaires tant que la commande en cours n’est pas terminée.

## PARAMETERS

### -CimSession
Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.
Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .
La valeur par défaut est la session active sur l’ordinateur local.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Spécifie un tableau de noms d'ordinateurs.
L’applet de commande applique les paramètres de configuration aux ordinateurs que ce paramètre spécifie.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
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
Parameter Sets: ComputerNameSet
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

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
