---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxGroup dans DSC pour Linux
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093600"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>Ressource nxGroup dans DSC pour Linux

La ressource **nxGroup** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description |
|---|---|
| GroupName| Spécifie le nom du groupe pour lequel vous souhaitez garantir un état spécifique.|
| Ensure| Détermine si l’existence du groupe doit être vérifiée. Définissez cette propriété sur « Present » pour vous assurer que le groupe existe. Définissez la propriété sur « Absent » pour vous assurer que le groupe n’existe pas. La valeur par défaut est « Present ».|
| Members| Spécifie les membres qui constituent le groupe.|
| MembersToInclude| Spécifie les utilisateurs qui doivent faire partie du groupe.|
| MembersToExclude| Spécifie les utilisateurs qui ne doivent pas faire partie du groupe.|
| PreferredGroupID| Définit l’ID de groupe à la valeur fournie, si possible. Si l’ID de groupe est déjà utilisé, l’ID de groupe disponible suivant est utilisé.|
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Exemple

L’exemple suivant vérifie que l’utilisateur 'monuser' existe et qu’il est membre du groupe 'DBusers'.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```