---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Service dans DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076888"
---
# <a name="dsc-service-resource"></a>Ressource Service dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource **Service** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Indique le nom du service Notez qu’il peut être différent du nom d’affichage. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande Get-Service.|
| BuiltInAccount| Indique le compte de connexion à utiliser pour le service. Sont autorisées pour cette propriété les valeurs suivantes : **LocalService**, **LocalSystem** et **NetworkService**.|
| Credential| Indique les informations d’identification pour le compte sous lequel s’exécute le service. Cette propriété et la propriété __BuiltinAccount__ ne peuvent pas être utilisées ensemble.|
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Indique le type de démarrage du service. Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**|
| State| Indique l’état que vous voulez assurer pour le service.|
| Description | Indique la description du service cible.|
| DisplayName | Indique le nom complet du service cible.|
| Ensure | Indique si le service cible existe sur le système. Affectez la valeur **Absent** à cette propriété pour vous assurer que le service cible n’existe pas. La valeur **Present** (valeur par défaut) permet de s’assurer que le service cible existe.|
| Path | Indique le chemin du fichier binaire d’un nouveau service.|

## <a name="example"></a>Exemple

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```