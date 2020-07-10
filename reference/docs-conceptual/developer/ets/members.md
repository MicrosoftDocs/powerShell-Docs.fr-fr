---
title: Membres de classe de système de type étendu
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: c066bd69c0ab20cceff96aa789654e80443758e5
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217948"
---
# <a name="extended-type-system-class-members"></a>Membres de classe de système de type étendu

ETS fait référence à plusieurs genres de membres dont les types sont définis par l’énumération **PSMemberTypes** . Ces types de membres incluent des propriétés, des méthodes, des membres et des jeux de membres qui sont tous définis par leur propre type CLR. Par exemple, un **NoteProperty** est défini par son propre type **PSNoteProperty** . Ces types CLR individuels ont à la fois leurs propres propriétés uniques et propriétés communes qui sont héritées de la [classe PSMemberInfo](/dotnet/api/system.management.automation.psmemberinfo).

## <a name="the-psmemberinfo-class"></a>La classe PSMemberInfo

La classe **PSMemberInfo** sert de classe de base pour tous les types de membres ETS. Cette classe fournit les propriétés de base suivantes à tous les types CLR de membre.

- Propriété **Name** : nom du membre. Ce nom peut être défini par l’objet de base ou défini par PowerShell quand des membres adaptés ou des membres étendus sont exposés.
- Propriété de **valeur** : valeur retournée par le membre particulier. Chaque type de membre définit la manière dont il gère sa valeur de membre.
- Propriété **TypeNameOfValue** : il s’agit du nom du type CLR de la valeur retournée par la propriété Value.

## <a name="accessing-members"></a>Accès aux membres

Les collections de membres sont accessibles via les propriétés des **membres**, des **méthodes**et des **Propriétés** de l’objet **PSObject** .

## <a name="ets-properties"></a>Propriétés de ETS

Les propriétés ETS sont des membres qui peuvent être traités comme une propriété. Pour l’essentiel, ils peuvent apparaître sur le côté gauche d’une expression. Elles incluent des propriétés d’alias, des propriétés de code, des propriétés PowerShell, des propriétés de note et des propriétés de script. Pour plus d’informations sur ces types de propriétés, consultez [Propriétés ETS](properties.md).

## <a name="ets-methods"></a>Méthodes ETS

Les méthodes ETS sont des membres qui peuvent prendre des arguments, peuvent retourner des résultats et ne peuvent pas apparaître sur le côté gauche d’une expression. Elles incluent les méthodes de code, les méthodes PowerShell et les méthodes de script.
Pour plus d’informations sur ces types de méthodes, consultez [méthodes ETS](methods.md).
