---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Log dans DSC
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219383"
---
# <a name="dsc-log-resource"></a>Ressource Log dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource __Log__ dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

REMARQUE : Par défaut, seuls les journaux des opérations relatifs à DSC sont activés.
Pour que le journal d’analyse soit disponible ou visible, il doit être activé.
Consultez l’article suivant.

[Où se trouvent les journaux des événements DSC ?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Propriétés
|  Propriété  |  Description   |
|---|---|
| Message| Indique le message à écrire dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant l’écriture de ce message dans le journal. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemple

L’exemple suivant écrit un message dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

> **Remarque** : Si vous exécutez [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) avec cette ressource configurée, elle retourne toujours la valeur **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```