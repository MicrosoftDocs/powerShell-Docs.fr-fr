---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: b8f55770770fa9077f654d382818386cc480c638
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596323"
---
# Get-EventSubscriber

## SYNOPSIS
Obtient les abonnés aux événements dans la session active.

## SYNTAXE

### BySource (par défaut)

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### Méthode BYID

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-EventSubscriber** obtient les abonnés aux événements dans la session active.

Lorsque vous vous abonnez à un événement à l’aide d’une applet de commande d’événement Register, un abonné aux événements est ajouté à votre session PowerShell et les événements auxquels vous vous êtes abonné sont ajoutés à la file d’attente d’événements chaque fois qu’ils sont déclenchés.
Pour annuler l'abonnement à un événement, supprimez l'abonné aux événements à l'aide de l'applet de commande Unregister-Event.

## EXEMPLES

### Exemple 1 : obtenir l’abonné aux événements pour un événement de minuterie

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

Cet exemple utilise une commande **EventSubscriber** pour obtenir l’abonné aux événements pour un événement de minuterie.

La première commande utilise l'applet de commande New-Object pour créer une instance d'un objet minuteur.
Elle enregistre le nouvel objet minuteur dans la variable $Timer.

La deuxième commande utilise l'applet de commande Get-Member pour afficher les événements qui sont disponibles pour les objets minuteur.
La commande utilise le paramètre de type de l’applet de commande **obten-Member** avec la valeur Event.

La troisième commande utilise l'applet de commande Register-ObjectEvent pour s'inscrire à l'événement Elapsed sur l'objet minuteur.

La quatrième commande utilise l’applet de commande **obtenir-EventSubscriber** pour obtenir l’abonné aux événements pour l’événement Elapsed.

### Exemple 2 : utiliser le module dynamique dans PSEventJob dans la propriété action de l’abonné aux événements

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

Cet exemple montre comment utiliser le module dynamique dans l’objet **PSEventJob** dans la propriété action de l’abonné aux événements.

La première commande utilise l'applet de commande New-Object pour créer un objet Timer.
La deuxième commande définit l'intervalle de la minuterie à 500 millisecondes.

La troisième commande utilise l'applet de commande Register-ObjectEvent pour inscrire l'événement Elapsed de l'objet Timer.
La commande comprend une action qui gère l'événement.
Chaque fois que l'intervalle de la minuterie est dépassé, un événement est déclenché et les commandes de l'action s'exécutent.
Dans ce cas, l’applet de commande Get-Random génère un nombre aléatoire compris entre 0 et 100 et l’enregistre dans la variable $Random.
L'identificateur source de l'événement est Timer.Random.

Quand vous utilisez un paramètre d' *action* dans une commande **Register-ObjectEvent** , la commande retourne un objet **PSEventJob** qui représente l’action.

La quatrième commande active la minuterie.

La cinquième commande utilise l’applet de commande **EventSubscriber** pour récupérer l’abonné aux événements de l’événement Timer. Random.
Elle enregistre l’objet d’abonné aux événements dans la variable $Subscriber.

La sixième commande indique que la propriété action de l’objet d’abonné aux événements contient un objet **PSEventJob** .
En fait, elle contient le même objet **PSEventJob** que celui retourné par la commande **Register-ObjectEvent** .

La septième commande utilise l’applet de commande Format-List pour afficher toutes les propriétés de l’objet **PSEventJob** dans la propriété action dans une liste.
Le résultat révèle que l’objet **PSEventJob** a une propriété module qui contient un module de script dynamique qui implémente l’action.

Les commandes restantes utilisent l’opérateur d’appel (&) pour appeler la commande dans le module et afficher la valeur de la variable $Random.
Vous pouvez utiliser l'opérateur d'appel pour appeler une commande dans un module, y compris des commandes qui ne sont pas exportées.
Dans ce cas, les commandes montrent le nombre aléatoire qui est généré quand l'événement Elapsed se produit.

Pour plus d’informations sur les modules, consultez [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

## PARAMETERS

### -Force

Indique que cette applet de commande obtient tous les abonnés aux événements, y compris les abonnés pour les événements qui sont masqués à l’aide du paramètre *SupportEvent* de Register-ObjectEvent, Register-WmiEvent et Register-EngineEvent.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie la valeur de la propriété **SourceIdentifier** qui obtient uniquement les abonnés aux événements.
Par défaut, l’option **EventSubscriber** obtient tous les abonnés aux événements dans la session.
Les caractères génériques ne sont pas autorisés.
Ce paramètre respecte la casse.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId

Spécifie l’identificateur d’abonnement que cette applet de commande obtient.
Par défaut, l’option **EventSubscriber** obtient tous les abonnés aux événements dans la session.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### None

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSEventSubscriber

La méthode **obtient-EventSubscriber** retourne un objet qui représente chaque abonné aux événements.

## REMARQUES

* L'applet de commande New-Event, qui crée un événement personnalisé, ne génère pas d'abonné. Par conséquent, l’applet de commande **EventSubscriber** ne trouvera pas d’objet d’abonné pour ces événements. Toutefois, si vous utilisez l’applet de commande Register-EngineEvent pour vous abonner à un événement personnalisé (afin de transférer l’événement ou de spécifier une action), la commande **EventSubscriber** trouve l’abonné généré par **Register-EngineEvent** .

  Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.
Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

*

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

