---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: aa6965b3a21c145ecccb284d43c6d0913bb31027
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201226"
---
# Remove-PSSession

## SYNOPSIS
Ferme une ou plusieurs sessions PowerShell (sessions PSSession).

## SYNTAX

### ID (par défaut)

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### session

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ContainerId

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMId

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMName

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Nom

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet de commande **Remove-PSSession** ferme les sessions PowerShell ( **sessions PSSession** ) dans la session active.
Elle arrête toutes les commandes qui s’exécutent dans **sessions PSSession** , met fin à la **session PSSession** et libère les ressources utilisées par la **session PSSession** .
Si la **session PSSession** est connectée à un ordinateur distant, cette applet de commande ferme également la connexion entre les ordinateurs locaux et distants.

Pour supprimer une session **PSSession** , entrez *le nom* , *ComputerName* , *ID* ou *InstanceID* de la session.

Si vous avez enregistré la session *PSSession* dans une variable, l’objet de session reste dans la variable, mais l’état de la session *PSSession* est fermé.

## EXEMPLES

### Exemple 1 : supprimer des sessions à l’aide d’ID

```powershell
Remove-PSSession -Id 1, 2
```

Cette commande supprime les **sessions PSSession** qui ont les ID 1 et 2.

### Exemple 2 : supprimer toutes les sessions de la session active

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

Ces commandes suppriment toutes les **sessions PSSession** de la session active.
Bien que les formats des trois commandes semblent différents, ils ont le même effet.

### Exemple 3 : fermer des sessions à l’aide de noms

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

Ces commandes ferment les **sessions PSSession** connectées aux ordinateurs dont le nom commence par serv.

### Exemple 4 : fermer les sessions connectées à un port

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

Cette commande ferme les **sessions PSSession** connectés au port 90.
Vous pouvez utiliser ce format de commande pour identifier les **sessions PSSession** par des propriétés autres que *ComputerName* , *Name* , *InstanceID* et *ID* .

### Exemple 5 : fermer une session en fonction de l’ID d’instance

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

Ces commandes indiquent comment fermer une **session PSSession** en fonction de son ID d’instance, ou **RemoteRunspaceID** .

La première commande utilise l’applet de commande **obten-PSSession** pour récupérer le **sessions PSSession** dans la session active.
Elle utilise un opérateur de pipeline (|) pour envoyer le **sessions PSSession** à l’applet de commande Format-Table, qui met en forme leurs propriétés **ComputerName** et **InstanceID** dans une table.
Le paramètre *AutoSize* compresse les colonnes à afficher.

À partir de l’affichage qui en résulte, vous pouvez identifier la **session PSSession** à fermer, puis copier et coller l' *InstanceID* de cette **session PSSession** dans la deuxième commande.

La deuxième commande utilise l’applet de commande **Remove-PSSession** pour supprimer la *session PSSession* avec l’ID d’instance spécifié.

### Exemple 6 : créer une fonction qui supprime toutes les sessions dans la session active

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

Cette fonction supprime toutes les **sessions PSSession** de la session active.
Après avoir ajouté cette fonction à votre profil PowerShell, pour supprimer toutes les sessions, tapez `EndPSS` .

## PARAMETERS

### -ComputerName

Spécifie un tableau de noms d’ordinateurs.
Cette applet de commande ferme les **sessions PSSession** connectés aux ordinateurs spécifiés.
Les caractères génériques sont autorisés.

Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ContainerId

Spécifie un tableau d’ID de conteneurs. Cette applet de commande supprime les sessions pour chacun des conteneurs spécifiés. Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur. Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Id

Spécifie un tableau d’ID de sessions.
Cette applet de commande ferme le *sessions PSSession* avec les ID spécifiés.
Tapez un ou plusieurs ID, en les séparant par des virgules, ou utilisez l’opérateur de plage (..) pour spécifier une plage d’ID.

Un ID est un entier qui identifie de façon unique la session **PSSession** dans la session active.
Il est plus facile à mémoriser et à taper que *InstanceID* , mais il n’est unique que dans la session active.
Pour Rechercher l’ID d’une **session PSSession** , exécutez l’applet de commande Get-PSSession sans paramètres.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Spécifie un tableau d’ID d’instance.
Cette applet de commande ferme les **sessions PSSession** qui ont les ID d’instance spécifiés.

L’ID d’instance est un GUID qui identifie de façon unique une session **PSSession** dans la session active.
L’ID d’instance est unique, même si plusieurs sessions sont en cours d’exécution sur un seul ordinateur.

L’ID d’instance est stocké dans la propriété **InstanceID** de l’objet qui représente une **session PSSession** .
Pour Rechercher l' **InstanceID** de **sessions PSSession** dans la session active, tapez `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms conviviaux de sessions.
Cette applet de commande ferme les **sessions PSSession** qui ont les noms conviviaux spécifiés.
Les caractères génériques sont autorisés.

Étant donné que le nom convivial d’une **session PSSession** peut ne pas être unique, lorsque vous utilisez le paramètre *Name* , envisagez d’utiliser également le paramètre *WhatIf* ou *Confirm* dans la commande **Remove-PSSession** .

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

Spécifie les objets de session du **sessions PSSession** à fermer.
Entrez une variable qui contient **sessions PSSession** ou une commande qui crée ou obtient le **sessions PSSession** , tel qu’une commande New-PSSession ou la commande **obtenir-PSSession** .
Vous pouvez également diriger un ou plusieurs objets de session vers **Remove-PSSession** .

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMId

Spécifie un tableau d’ID de machines virtuelles.
Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.
Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Spécifie un tableau de noms d'ordinateurs virtuels.
Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.
Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l’applet de commande **obtenir-VM** .

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Management. Automation. instances d’exécution. PSSession

Vous pouvez diriger un objet de session vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne pas d'objets.

## REMARQUES

* Le paramètre *ID* est obligatoire. Pour supprimer tous les **sessions PSSession** de la session active, tapez `Get-PSSession | Remove-PSSession` .
* Une **session PSSession** utilise une connexion permanente à un ordinateur distant. Créez une **session PSSession** pour exécuter une série de commandes qui partagent des données. Pour plus d'informations, voir `Get-Help about_PSSessions`.
* Les **sessions PSSession** sont spécifiques à la session active. Lorsque vous terminez une session, les **sessions PSSession** que vous avez créés dans cette session sont fermés de force.

## LIENS CONNEXES

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
