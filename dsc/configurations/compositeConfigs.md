---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Imbrication des configurations
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080235"
---
# <a name="nesting-dsc-configurations"></a>Imbrication des configurations DSC

Une configuration imbriquée (également appelée configuration composite) est une configuration appelée dans une autre configuration, comme s’il s’agissait d’une ressource.
Les deux configurations doivent être définies dans le même fichier.

Examinons un exemple simple :

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

Dans cet exemple, `FileConfig` accepte deux paramètres obligatoires, **CopyFrom** et **CopyTo**, tous deux utilisés comme valeurs pour les propriétés **SourcePath** et **DestinationPath** du bloc de ressources `File`.
La configuration `NestedConfig` appelle `FileConfig` comme s’il s’agissait d’une ressource.
Les propriétés du bloc de ressources `NestedConfig` (**CopyFrom** et **CopyTo**) sont les paramètres de la configuration `FileConfig`.

## <a name="see-also"></a>Voir aussi

- [Ressources composites : utilisation d’une configuration DSC en tant que ressource](../resources/authoringResourceComposite.md)