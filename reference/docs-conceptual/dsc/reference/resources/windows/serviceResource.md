---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Service dans DSC
ms.openlocfilehash: f936f58ffd00f84d8c6d5d41d93378eaa8db5879
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463582"
---
# <a name="dsc-service-resource"></a>Ressource Service dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **Service** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Nom |Indique le nom du service Notez qu’il peut être différent du nom d’affichage. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande `Get-Service`. |
|BuiltInAccount |Indique le compte de connexion à utiliser pour le service. Sont autorisées pour cette propriété les valeurs suivantes : **LocalService**, **LocalSystem** et **NetworkService**. |
|Informations d'identification |Indique les informations d’identification pour le compte sous lequel s’exécute le service. Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble. |
|StartupTimeout | Délai d’attente de l’exécution du service en millisecondes.|
|StartupType |Indique le type de démarrage du service. Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**. |
|State |Indique l’état que vous voulez assurer pour le service. Les valeurs sont : **Running** ou **Stopped**. |
|TerminateTimeout |Délai d’attente de l’arrêt du service en millisecondes.|
|Les dépendances | Tableau des noms des dépendances que le service doit avoir. |
|Description |Indique la description du service cible. |
|DesktopInteract | Indique si le service doit être en mesure de communiquer avec une fenêtre sur le bureau. Doit avoir la valeur false pour les services qui ne s’exécutent pas en tant que LocalSystem.|
|DisplayName |Indique le nom complet du service cible. |
|Chemin d’accès |Indique le chemin du fichier binaire d’un nouveau service. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si le service cible existe sur le système. Affectez la valeur **Absent** à cette propriété pour vous assurer que le service cible n’existe pas. Définissez-la sur **Present** pour être assuré que le service cible n’existe pas. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

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
