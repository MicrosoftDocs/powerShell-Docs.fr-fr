---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAny
ms.openlocfilehash: c9700c908f8601db85f9c922445969a34b59d453
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186709"
---
# <a name="dsc-waitforany-resource"></a>Ressource DSC WaitForAny

> S’applique à : Windows PowerShell 5.1 et ultérieur

La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.

La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur un des nœuds cible définis dans la propriété **NodeName**.


## <a name="syntax"></a>Syntaxe

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Nom_ressource| Le nom de la ressource de la dépendance. Si cette ressource appartient à une configuration différente, mettez en forme le nom comme ceci : "[__type_ressource__]__nom_ressource__::[__nom_configuration__]::[__nom_configuration__]"|
| NodeName| Les nœuds cible de la ressource de la dépendance.|
| RetryIntervalSec| Le nombre de secondes avant la nouvelle tentative. Le minimum est 1.|
| RetryCount| Le nombre maximum de nouvelles tentatives.|
| ThrottleLimit| Le nombre de machines à connecter simultanément. La valeur par défaut est new-cimsession.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)