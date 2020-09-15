---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: Ressource nxService dans DSC pour Linux
ms.openlocfilehash: 2aec8b943d386fad33dfc1cfdd916c5e18039eaa
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463633"
---
# <a name="dsc-for-linux-nxservice-resource"></a>Ressource nxService dans DSC pour Linux

La ressource **nxService** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des services sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Nom du service/démon à configurer. |
|Contrôleur |Type de contrôleur de service à utiliser lors de la configuration du service. |
|activé |Indique si le service s’exécute au démarrage du système. |
|State |Indique si le service est en cours d’exécution. Définissez cette propriété sur **Stopped** pour vous assurer que le service n’est pas en cours d’exécution. Définissez cette propriété sur **Running** pour vous assurer que le service est en cours d’exécution. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="additional-information"></a>Informations supplémentaires

La ressource **nxService** ne crée pas de fichier de définition ni de script pour le service si celui-ci n’existe pas. Vous pouvez utiliser la ressource **nxFile** dans DSC PowerShell pour gérer l’existence ou le contenu du fichier de définition ou script du service.

## <a name="example"></a>Exemple

L’exemple suivant configure le service 'httpd' (pour Apache HTTP Server) qui est inscrit auprès du contrôleur de service **SystemD**.

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
