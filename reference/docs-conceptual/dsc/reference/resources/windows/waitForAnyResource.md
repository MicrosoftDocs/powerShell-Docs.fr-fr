---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource DSC WaitForAny
description: Ressource DSC WaitForAny
ms.openlocfilehash: d997176c81ec390b9e58f5a28cae1814ee3dbcde
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143124"
---
# <a name="dsc-waitforany-resource"></a>Ressource DSC WaitForAny

> S’applique à : Windows PowerShell 5.1

La ressource de configuration d’état souhaité (DSC) **WaitForAny** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName** .

> [!NOTE]
> La ressource **WaitForAny** utilise Windows Remote Management pour vérifier l’état d’autres nœuds. Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity).

## <a name="syntax"></a>Syntaxe

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Nom_ressource |Le nom de la ressource de la dépendance. Si cette ressource appartient à une configuration différente, mettez le nom sous la forme `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`. |
|NodeName |Les nœuds cible de la ressource de la dépendance. |
|RetryIntervalSec |Le nombre de secondes avant la nouvelle tentative. Le minimum est 1. |
|RetryCount |Le nombre maximum de nouvelles tentatives. |
|ThrottleLimit |Le nombre de machines à connecter simultanément. La valeur par défaut est `New-CimSession` par défaut. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)
