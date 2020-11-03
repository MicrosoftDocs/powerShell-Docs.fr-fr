---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/register-cimindicationevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-CimIndicationEvent
ms.openlocfilehash: 802af0d2a130a0ddc01d9a94cadf7f503eb7d697
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201318"
---
# Register-CimIndicationEvent

## SYNOPSIS
S’abonne à des indications à l’aide d’une expression de filtre ou d’une expression de requête.

## SYNTAX

### ClassNameComputerSet (par défaut)

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### ClassNameSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionComputerSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## Description

L' `Register-CimIndicationEvent` applet de commande s’abonne aux indications à l’aide d’un nom de classe d’indication ou d’une expression de requête. Utilisez le paramètre **SourceIdentifier** pour attribuer un nom à l’abonnement.

Cette applet de commande retourne un objet **événement** . Vous pouvez utiliser cet objet pour annuler l’abonnement.

## EXEMPLES

### Exemple 1 : enregistrer les événements générés par une classe

Cet exemple s’abonne aux événements générés par la classe nommée **Win32_ProcessStartTrace** . Cette classe déclenche un événement à chaque démarrage d'un processus.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
Get-Event -SourceIdentifier "ProcessStarted"
```

L' `Get-Event` applet de commande obtient les événements avec l’abonnement **ProcessStarted** . Pour plus d’informations, consultez la rubrique [obtenir un événement](../Microsoft.PowerShell.Utility/Get-Event.md).

> [!NOTE]
> Pour cet exemple, vous devez exécuter PowerShell en tant qu’administrateur.

### Exemple 2 : inscrire les événements à l’aide d’une requête

Cet exemple utilise une requête pour s’abonner à un événement généré chaque fois qu’une modification est apportée à l’instance d’une classe nommée **Win32_LocalTime** .

```powershell
$query = "SELECT * FROM CIM_InstModification WHERE TargetInstance ISA 'Win32_LocalTime'"
Register-CimIndicationEvent -Query $query -SourceIdentifier "Timer"
```

### Exemple 3 : exécuter un script lors de l’arrivée de l’événement

Cet exemple montre comment utiliser une action en réponse à un événement. La variable `$action` contient le bloc de script pour **action** , qui utilise la `$event` variable pour accéder à l’événement reçu à partir de CIM.

```powershell
$action = {
  $name = $event.SourceEventArgs.NewEvent.ProcessName
  $id = $event.SourceEventArgs.NewEvent.ProcessId
  Write-Host -Object "New Process Started : Name = $name
 ID = $id"
}
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

Pour plus d’informations, consultez [Win32_ProcessStartTrace](/previous-versions/windows/desktop/krnlprov/win32-processstarttrace).

### Exemple 4 : inscrire les événements sur un ordinateur distant

Cet exemple s’abonne aux événements sur un ordinateur distant nommé **SERVEUR01** . Les événements reçus du serveur CIM sont stockés dans la file d’attente des événements dans la session PowerShell active, puis ils exécutent un local `Get-Event` pour récupérer les événements.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -ComputerName Server01
Get-Event -SourceIdentifier "ProcessStarted"
```

## PARAMETERS

### -Action

Spécifie les commandes qui gèrent les événements. Les commandes spécifiées par ce paramètre s’exécutent lorsqu’un événement est déclenché, au lieu d’envoyer l’événement à la file d’attente d’événements. Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.

Le bloc de script spécifié avec l' **action** peut inclure les variables automatiques,,, `$Event` `$EventSubscriber` `$Sender` `$SourceEventArgs` et `$SourceArgs` , qui fournissent des informations sur l’événement au bloc de script de l' **action** . Pour plus d’informations, consultez [à propos des variables automatiques](../microsoft.powershell.core/about/about_automatic_variables.md).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

Exécute la commande à l’aide de la session CIM spécifiée. Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` . Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: ClassNameSessionSet, QueryExpressionSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClassName

Spécifie la classe d’indication à laquelle vous vous abonnez. Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM. Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.

Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan. Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue une opération sur le système local à l’aide du modèle COM (Component Object Model).

Si plusieurs opérations sont exécutées sur le même ordinateur, connectez-vous à l’aide d’une session CIM pour obtenir de meilleures performances.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QueryExpressionComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Suivant

Indique que les événements de l’abonnement sont transférés à la session sur l’ordinateur local. Utilisez ce paramètre lorsque vous vous inscrivez aux événements sur un ordinateur distant ou dans une session à distance.

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

### -MaxTriggerCount

Pour indiquer que l’inscription de l’abonné doit être annulée automatiquement après avoir été déclenchée pour des heures spécifiées. Si la valeur est inférieure ou égale à zéro, il n’y a aucune limite sur le nombre de fois où l’événement peut être déclenché sans être désinscrit.

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

### -MessageData

Spécifie toutes les données supplémentaires à associer à cet abonnement aux événements. La valeur de ce paramètre apparaît dans la propriété **MessageData** de tous les événements associés à cet abonnement.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms

Spécifie l’espace de noms pour l’opération CIM. L’espace de noms par défaut est **root/cimv2** . Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.

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

### -OperationTimeoutSec

Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur. Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.

Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

Spécifie une requête à exécuter sur le serveur CIM. Si la valeur spécifiée contient des guillemets doubles, des `"` guillemets simples `'` ou une barre oblique inverse `\` , vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder d’une barre oblique inverse. Si la valeur spécifiée utilise l’opérateur LIKE WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les plaçant entre crochets `[]` : pourcentage, trait de `%` soulignement `_` ou crochet ouvrant `[` .

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryDialect

Spécifie le langage de requête utilisé pour le paramètre de **requête** . Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL** . La valeur par défaut est **WQL** .

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie un nom pour l’abonnement. Le nom que vous spécifiez doit être unique dans la session active. La valeur par défaut est un GUID assigné par PowerShell. Cette valeur apparaît dans la valeur de la propriété **SourceIdentifier** de l’objet abonné et de tous les objets événement associés à cet abonnement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Indique que l’abonnement aux événements est masqué. Utilisez ce paramètre lorsque l'abonnement actuel fait partie d'un mécanisme d'inscription d'événement plus complexe et qu'il ne doit pas être découvert indépendamment.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucun objet d’entrée.

## SORTIES

### System.Object

Cette applet de commande génère un objet **événement** .

## REMARQUES

## LIENS CONNEXES

[Get-Event](../microsoft.powershell.utility/get-event.md)

[Remove-Event](../microsoft.powershell.utility/remove-event.md)

[Unregister-Event](../microsoft.powershell.utility/unregister-event.md)

[Write-Host](../microsoft.powershell.utility/write-host.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
