---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources ServiceSet dans DSC
ms.openlocfilehash: 1f879d2eafeb11e69968252a11f0c550c9b103f3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-serviceset-resource"></a>Ressources ServiceSet dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible. Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété `Name`.

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
| StartupType| Indique le type de démarrage du service. Les valeurs autorisées pour cette propriété sont : **Automatic**, **Disabled** et **Manual**|
| BuiltInAccount| Indique le compte de connexion à utiliser pour les services. Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem** et **NetworkService**.|
| State| Indique l’état que vous voulez assurer pour les services : **Arrêté** ou **En cours d’exécution**.|
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