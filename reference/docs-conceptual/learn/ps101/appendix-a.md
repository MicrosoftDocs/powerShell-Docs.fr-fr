---
title: Annexe A - Syntaxe de l’aide
description: Cet article explique comment lire et comprendre la syntaxe d’une applet de commande telle que présentée par Get-Help.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437980"
---
# <a name="appendix-a---help-syntax"></a>Annexe A - Syntaxe de l’aide

L’exemple suivant montre comment obtenir la section **SYNTAXE** de l’aide pour l’applet de commande `Get-EventLog`.

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

Dans cet exemple, seule la partie pertinente de l’aide est indiquée.

La syntaxe est principalement composée de plusieurs séries de crochets ouvrants et fermants (`[]`). Ceux-ci ont deux significations différentes selon la façon dont ils sont utilisés. Tout ce qui est contenu entre crochets est facultatif, sauf s’il s’agit d’une série de crochets vides `[]`. Les crochets vides s’affichent uniquement après un type de données comme `<string[]>`. Cela signifie qu’un paramètre particulier peut accepter plusieurs valeurs de ce type.

Le premier paramètre du premier jeu de paramètres de `Get-EventLog` est **LogName**. LogName est placé entre crochets, ce qui signifie qu’il s’agit d’un paramètre positionnel. En d’autres termes, le fait de spécifier le nom du paramètre lui-même est facultatif, à condition qu’il soit spécifié à l’emplacement approprié. Les informations incluses entre crochets pointus (`<>`) après le nom du paramètre indiquent qu’il a besoin d’une seule valeur **string** (chaîne). Comme l’ensemble du nom de paramètre et du type de données ne sont pas placés entre crochets angulaires, le paramètre **LogName** est obligatoire lors de l’utilisation de ce jeu de paramètres.

```powershell
Get-EventLog [-LogName] <String>
```

Le deuxième paramètre est **InstanceId**. Notez que le nom de paramètre et le type de données sont tous deux placés en totalité entre crochets angulaires. Cela signifie que le paramètre **InstanceId** est facultatif, et non obligatoire. Notez également qu’**InstanceId** est placé entre sa propre série de crochets angulaires. Comme avec le paramètre **LogName**, cela signifie que le paramètre est positionnel. Il y a une dernière série de crochets angulaires après le type de données. Cela signifie qu’il peut accepter plusieurs valeurs sous la forme d’une table ou d’une liste séparée par des virgules.

```
[[-InstanceId] <Int64[]>]
```

Le deuxième jeu de paramètres a un paramètre **List**. Il s’agit d’un paramètre booléen car aucun type de données ne suit le nom du paramètre. Quand le paramètre **List** est spécifié, la valeur est **True**. Quand il n’est pas spécifié, la valeur est **False**.

```
[-List]
```

Les informations sur la syntaxe d’une commande peuvent également être récupérées avec `Get-Command` à l’aide du paramètre **Syntax**. Il s’agit d’un raccourci pratique que j’utilise tout le temps. Il me permet d’apprendre rapidement comment utiliser une commande sans avoir à passer en revue plusieurs pages d’informations d’aide. Si je vois que j’ai besoin d’informations supplémentaires, je reviens au contenu de l’aide.

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

Plus vous utilisez le système d’aide dans PowerShell, plus il est facile de mémoriser les différentes nuances. Avant même de vous en apercevoir, son utilisation devient une seconde nature.
