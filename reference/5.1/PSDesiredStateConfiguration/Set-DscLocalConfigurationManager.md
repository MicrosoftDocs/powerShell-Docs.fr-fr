---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "93205294"
---
# Set-DscLocalConfigurationManager

## SYNOPSIS

Applique les paramètres du Configuration Manager local (LCM) aux nœuds.

## SYNTAX

### ComputerNameSet (par défaut)

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-DscLocalConfigurationManager` applet de commande applique les paramètres du gestionnaire de configuration local aux nœuds. Spécifiez les ordinateurs en indiquant leurs noms ou en utilisant des sessions CIM (Common Information Model). Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande applique les paramètres à l'ordinateur local.

## EXEMPLES

### Exemple 1 : appliquer les paramètres du gestionnaire de configuration local

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

Cette commande applique les paramètres du gestionnaire de configuration local à des `C:\DSC\Configurations\` nœuds ciblés. Une fois les paramètres reçus, le gestionnaire de configuration local les traite.

> [!WARNING]
> S’il existe plusieurs méta-MOF pour le même ordinateur stocké dans le dossier spécifié, seul le premier méta MOF sera appliqué.

### Exemple 2 : appliquer les paramètres du gestionnaire de configuration local à l’aide d’une session CIM

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

Cet exemple applique les paramètres du gestionnaire de configuration local à un ordinateur et applique les paramètres. L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande. Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.

La première commande crée une session CIM à l’aide de l’applet de commande `New-CimSession` , puis stocke l’objet **CimSession** dans la `$Session` variable. La commande vous invite à entrer un mot de passe. Pour plus d'informations, voir `Get-Help New-CimSession`.

La deuxième commande applique les paramètres LCM du nœud ciblé de `C:\DSC\Configurations\` à l’ordinateur identifié par les objets **CimSession** stockés dans la `$Session` variable. Dans cet exemple, la `$Session` variable contient une session CIM uniquement pour l’ordinateur nommé SERVEUR01. La commande applique les paramètres. Une fois les paramètres reçus, le gestionnaire de configuration local les traite.

## PARAMETERS

### -CimSession

Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant. Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) ou [CimSession](/powershell/module/CimCmdlets/Get-CimSession) .
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

Spécifie un tableau de noms d'ordinateurs. Ce paramètre limite les ordinateurs qui ont des documents de méta-configuration dans le paramètre **path** à ceux spécifiés dans le tableau.

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

Spécifie un nom d'utilisateur et un mot de passe, sous la forme d'un objet **PSCredential** , pour l'ordinateur cible. Pour obtenir un objet **PSCredential** , utilisez l'applet de commande Get-Credential. Pour plus d'informations, voir `Get-Help Get-Credential`.

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

### -Path

Spécifie le chemin d'accès d'un dossier qui contient les fichiers de paramètres de configuration. L’applet de commande publie et applique ces paramètres LCM aux ordinateurs qui ont des fichiers de paramètres dans le chemin d’accès spécifié. Chaque nœud cible doit avoir un fichier de paramètres au format suivant : `NetBIOS Name.meta.mof` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande. Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur. Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.

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

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)
