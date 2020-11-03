---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203566"
---
# Remove-Computer

## SYNOPSIS
Supprime l’ordinateur local de son domaine.

## SYNTAX

### Local (par défaut)

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Remote

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Remove-Computer` applet de commande supprime l’ordinateur local et les ordinateurs distants de leurs domaines actuels.

Lorsque vous supprimez un ordinateur d’un domaine, `Remove-Computer` désactive également le compte de domaine de l’ordinateur. Vous devez fournir des informations d’identification explicites pour disjoindre l’ordinateur de son domaine, même s’il s’agit des informations d’identification de l’utilisateur actuel. Vous devez redémarrer l’ordinateur pour que la modification prenne effet. De plus, lorsque vous supprimez un ordinateur d’un domaine, vous devez le déplacer vers un groupe de travail. Utilisez le paramètre **WorkgroupName** pour spécifier le groupe de travail.

Pour déplacer un ordinateur d’un groupe de travail vers un domaine, d’un groupe de travail vers un autre, ou d’un domaine vers un autre, utilisez l’applet de commande `Add-Computer`.

Pour obtenir les résultats de la commande, utilisez les paramètres **Verbose** et **PassThru** . Pour supprimer l’invite utilisateur, utilisez le paramètre **Force** .

`Remove-Computer` supprime l’ordinateur local et les ordinateurs distants des domaines. Elle inclut de nouveaux paramètres d'informations d'identification qui spécifient d'autres informations d'identification pour la connexion à des ordinateurs distants et la disjonction d'un domaine, un nouveau paramètre **Restart** pour le redémarrage des ordinateurs concernés et un paramètre **WorkgroupName** pour la spécification du nom du groupe de travail auquel les ordinateurs sont ajoutés.

## EXEMPLES

### Exemple 1 : supprimer l’ordinateur local de son domaine

Cet exemple supprime l’ordinateur local du domaine auquel il est joint.

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

Le paramètre **UnjoinDomainCredential** fournit les informations d’identification d’un administrateur de domaine. Les paramètres communs **PassThru** et **Verbose** affichent des informations sur la réussite ou l’échec de la commande. Le paramètre **restart** redémarre l’ordinateur pour terminer l’opération de suppression.

Si aucun nom de groupe de travail n’est spécifié, l’ordinateur est déplacé vers le groupe de travail nommé une fois qu’il a été supprimé de son domaine.

### Exemple 2 : déplacer plusieurs ordinateurs vers un groupe de travail hérité

Cet exemple supprime tous les ordinateurs figurant dans le `OldServers.txt` fichier de leurs domaines et les déplace dans le groupe de travail **hérité** .

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

Le paramètre **LocalCredential** fournit les informations d’identification d’un utilisateur qui a l’autorisation de se connecter à des ordinateurs distants. Le paramètre **UnjoinDomainCredential** fournit les informations d’identification d’un utilisateur qui a l’autorisation de supprimer les ordinateurs de leurs domaines. Le paramètre **force** supprime les invites de confirmation pour chaque ordinateur. Le paramètre **restart** redémarre chaque ordinateur après sa suppression de son domaine.

### Exemple 3 : supprimer des ordinateurs d’un groupe de travail sans confirmation

Cet exemple supprime l’ordinateur distant, serveur01 et l’ordinateur local de leurs domaines et les ajoute au groupe de travail **local** .

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

Le paramètre **force** supprime l’invite de confirmation pour chaque ordinateur. Le paramètre **restart** redémarre les ordinateurs pour que la modification prenne effet.

## PARAMETERS

### -ComputerName

Spécifie les ordinateurs à supprimer de leurs domaines. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) des ordinateurs distants. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** de `Remove-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

Supprime l’invite utilisateur. Par défaut, `Remove-Computer` vous demande confirmation avant de supprimer chaque ordinateur.

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

### -LocalCredential

Spécifie un compte d’utilisateur qui a l’autorisation de se connecter aux ordinateurs que le paramètre **ComputerName** spécifie. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, l’applet de commande vous invite à entrer un mot de passe. Pour spécifier un compte d’utilisateur qui a l’autorisation de supprimer l’ordinateur de son domaine actuel, utilisez le paramètre **UnjoinDomainCredential** .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne les résultats de la commande. Sinon, cette applet de commande ne génère aucune sortie.

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

### -Restart

Indique que cette applet de commande redémarre les ordinateurs qui sont en cours de suppression. Un redémarrage est souvent nécessaire pour que le changement devienne effectif.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### -UnjoinDomainCredential

Spécifie un compte d’utilisateur qui a l’autorisation de supprimer les ordinateurs de leurs domaines actuels.
Des informations d’identification explicites, fournies par ce paramètre, sont requises pour supprimer les ordinateurs distants d’un domaine, même lorsque la valeur est représentée par les informations d’identification de l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par `Get-Credential` . Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter aux ordinateurs distants, utilisez le paramètre **LocalCredential** .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkgroupName

Spécifie le nom d’un groupe de travail auquel les ordinateurs sont ajoutés lorsqu’ils sont supprimés de leurs domaines. La valeur par défaut est **Workgroup** . Lorsque vous supprimez un ordinateur d’un domaine, vous devez l’ajouter à un groupe de travail.

Ce paramètre a été introduit dans PowerShell 3,0.

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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

### System.String

Vous pouvez diriger les noms d’ordinateurs vers thiscmdlet.

## SORTIES

### Microsoft. PowerShell. Commands. ComputerChangeInfo

Quand vous utilisez le paramètre **PassThru** , `Remove-Computer` retourne un objet **ComputerChangeInfo** .
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Cette applet de commande ne supprime pas les ordinateurs des groupes de travail.

## LIENS CONNEXES

[Add-Computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Stop-Computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
