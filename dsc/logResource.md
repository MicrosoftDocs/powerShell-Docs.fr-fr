---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Log dans DSC
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268430"
---
# <a name="dsc-log-resource"></a>Ressource Log dans DSC

_S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_

La ressource __Log__ dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Par défaut, seuls les journaux des opérations relatifs à DSC sont activés. Pour que le journal d’analyse soit disponible ou visible, il doit être activé. Pour plus d’informations, consultez [Où se trouvent les journaux des événements DSC ?](troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Propriétés

| Propriété | Description |
| --- | --- |
| Message| Indique le message à écrire dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant l’écriture de ce message dans le journal. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Exemple

L’exemple suivant écrit un message dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.

> [!NOTE]
> Si vous exécutez [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) avec cette ressource configurée, elle retourne toujours la valeur **$false**.

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