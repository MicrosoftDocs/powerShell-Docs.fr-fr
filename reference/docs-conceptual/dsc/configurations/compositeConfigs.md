---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Imbrication des configurations
ms.openlocfilehash: e74c0fe1d7f7b198c2d6f796c0bf120eb0ec21d9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564020"
---
# <a name="nesting-dsc-configurations"></a>Imbrication des configurations DSC

Une configuration imbriquée (également appelée configuration composite) est une configuration appelée dans une autre configuration, comme s’il s’agissait d’une ressource. Les deux configurations doivent être définies dans le même fichier.

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

Dans cet exemple, `FileConfig` accepte deux paramètres obligatoires, **CopyFrom** et **CopyTo**, tous deux utilisés comme valeurs pour les propriétés **SourcePath** et **DestinationPath** du bloc de ressources `File`. La configuration `NestedConfig` appelle `FileConfig` comme s’il s’agissait d’une ressource. Les propriétés du bloc de ressources `NestedConfig` (**CopyFrom** et **CopyTo**) sont les paramètres de la configuration `FileConfig`.

DSC ne prend pas actuellement en charge l’imbrication de configurations dans des configurations imbriquées. Vous pouvez uniquement imbriquer une configuration d’une profondeur de couche.

## <a name="see-also"></a>Voir aussi

- [Ressources composites : utilisation d’une configuration DSC en tant que ressource](../resources/authoringResourceComposite.md)
