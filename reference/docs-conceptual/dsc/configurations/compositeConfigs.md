---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Imbrication des configurations
description: DSC vous permet de créer des configurations composites en imbriquant une configuration à l’intérieur d’une autre configuration.
ms.openlocfilehash: d7a81cb9673126e92e9185aacf19c5c7c17da8ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667417"
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

Dans cet exemple, `FileConfig` accepte deux paramètres obligatoires, **CopyFrom** et **CopyTo** , tous deux utilisés comme valeurs pour les propriétés **SourcePath** et **DestinationPath** du bloc de ressources `File`. La configuration `NestedConfig` appelle `FileConfig` comme s’il s’agissait d’une ressource. Les propriétés du bloc de ressources `NestedConfig` ( **CopyFrom** et **CopyTo** ) sont les paramètres de la configuration `FileConfig`.

DSC ne prend pas actuellement en charge l’imbrication de configurations dans des configurations imbriquées. Vous pouvez uniquement imbriquer une configuration d’une profondeur de couche.

## <a name="see-also"></a>Voir aussi

- [Ressources composites : utilisation d’une configuration DSC en tant que ressource](../resources/authoringResourceComposite.md)
