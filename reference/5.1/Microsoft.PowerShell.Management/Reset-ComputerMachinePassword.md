---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203530"
---
# Reset-ComputerMachinePassword

## SYNOPSIS
Réinitialise le mot de passe du compte ordinateur de l'ordinateur.

## SYNTAX

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description
L’applet de commande **Reset-ComputerMachinePassword** change le mot de passe du compte d’ordinateur utilisé par les ordinateurs pour s’authentifier auprès des contrôleurs de domaine du domaine.
Vous pouvez l’utiliser pour réinitialiser le mot de passe de l’ordinateur local.

## EXEMPLES

### Exemple 1 : réinitialiser le mot de passe de l’ordinateur local

```
PS C:\> Reset-ComputerMachinePassword
```

Cette commande réinitialise le mot de passe de l’ordinateur local.
La commande s’exécute avec les informations d’identification de l’utilisateur actuel.

### Exemple 2 : réinitialiser le mot de passe de l’ordinateur local à l’aide d’un contrôleur de domaine spécifié

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

Cette commande réinitialise le mot de passe de l’ordinateur local à l’aide du contrôleur de domaine DC01.
Elle utilise le paramètre *Credential* pour spécifier un compte d’utilisateur qui a l’autorisation de réinitialiser un mot de passe d’ordinateur dans le domaine.

### Exemple 3 : réinitialiser le mot de passe sur un ordinateur distant

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

Cette commande utilise l’applet de commande Invoke-Command pour exécuter une commande **Reset-ComputerMachinePassword** sur l’ordinateur distant SERVEUR01.

Pour plus d'informations sur les commandes à distance dans Windows PowerShell, consultez about_Remote et **Invoke-Command** .

## PARAMETERS

### -Credential
Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande Get-Credential.
Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Server
Spécifie le nom d’un contrôleur de domaine à utiliser lorsque cette applet de commande définit le mot de passe du compte d’ordinateur.

Ce paramètre est facultatif.
Si vous omettez ce paramètre, un contrôleur de domaine est choisi pour exécuter la commande.

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

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

## LIENS CONNEXES
