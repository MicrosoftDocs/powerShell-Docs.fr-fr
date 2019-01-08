---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources ServiceSet dans DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047266"
---
# <a name="dsc-serviceset-resource"></a>Ressources ServiceSet dans DSC

> S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible. Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété `Name`.

Utilisez cette ressource quand vous voulez configurer certains services au même état.

## <a name="syntax"></a>Syntaxe

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Indique les noms des services. Notez qu’ils peuvent être différents des noms d’affichages. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande [Get-Service](https://technet.microsoft.com/library/hh849804.aspx).|
| StartupType| Indique le type de démarrage du service. Les valeurs autorisées pour cette propriété sont : **Automatique**, **désactivé**, et **manuel**|
| BuiltInAccount| Indique le compte de connexion à utiliser pour les services. Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem**, et **NetworkService**.|
| State| Indique l’état que vous voulez assurer pour le service. **Arrêté** ou **en cours d’exécution**.|
| Ensure| Indique si les services existent sur le système. Affectez la valeur **Absent** à cette propriété pour vous assurer que les services n’existent pas. La valeur **Present** (valeur par défaut) permet de s’assurer que le services cibles existent.|
| Credential| Indique les informations d’identification pour le compte sous lequel s’exécute la ressource de service. Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.|
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource *ResourceName* de type *ResourceType*, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Exemple

La configuration suivante démarre les services « Audio Windows » et « Services Bureau à distance ».

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
