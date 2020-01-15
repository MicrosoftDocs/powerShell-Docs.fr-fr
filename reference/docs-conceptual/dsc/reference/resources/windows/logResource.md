---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Log dans DSC
ms.openlocfilehash: 0a2f12793357fdf10bd4a2f6003f9dc2276b173c
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870759"
---
# <a name="dsc-log-resource"></a>Ressource Log dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **Log** dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

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
> Si vous exécutez [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1) avec cette ressource configurée, elle retourne toujours la valeur **$false**.

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
