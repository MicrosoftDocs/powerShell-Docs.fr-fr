---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressources ServiceSet dans DSC
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953026"
---
# <a name="dsc-serviceset-resource"></a>Ressources ServiceSet dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible. Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété **Name**.

Utilisez cette ressource quand vous voulez configurer certains services au même état.

## <a name="syntax"></a>Syntaxe

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Indique les noms des services. Notez qu’ils peuvent être différents des noms d’affichages. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande `Get-Service`. |
|StartupType |Indique le type de démarrage pour les services. Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**. |
|BuiltInAccount |Indique le compte de connexion à utiliser pour les services. Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem** et **NetworkService**. |
|State |Indique l’état que vous voulez assurer pour les services : **Arrêté** ou **Exécution en cours**. |
|Credential |Indique les informations d’identification pour le compte sous lequel s’exécute la ressource de service. Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si les services existent sur le système. Affectez la valeur **Absent** à cette propriété pour vous assurer que les services n’existent pas. Définissez-la sur **Present** pour faire en sorte que les services cibles n’existent pas. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

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