---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource Log dans DSC
description: Ressource Log dans DSC
ms.openlocfilehash: 281d1f8aeeb4d075f073419ac02a0f81888ed2b5
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142461"
---
# <a name="dsc-log-resource"></a>Ressource Log dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **Log** dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> Par défaut, seuls les journaux des opérations relatifs à DSC sont activés. Pour que le journal d’analyse soit disponible ou visible, il doit être activé. Pour plus d’informations, consultez [Où se trouvent les journaux des événements DSC ?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Propriétés

| Propriété |                                                   Description                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| Message  | Indique le message à écrire dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic. |

## <a name="common-properties"></a>Propriétés communes

|       Propriété       |                                                                                                                                                          Description                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DependsOn            | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
| PsDscRunAsCredential | Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.                                                                                                                                                                                                                                                                        |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

L’exemple suivant écrit un message dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

> [!NOTE]
> Si vous exécutez [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) avec cette ressource configurée, elle retourne toujours la valeur **$false** .

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
