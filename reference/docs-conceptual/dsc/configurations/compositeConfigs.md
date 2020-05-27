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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="4817e-103">Imbrication des configurations DSC</span><span class="sxs-lookup"><span data-stu-id="4817e-103">Nesting DSC configurations</span></span>

<span data-ttu-id="4817e-104">Une configuration imbriquée (également appelée configuration composite) est une configuration appelée dans une autre configuration, comme s’il s’agissait d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="4817e-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="4817e-105">Les deux configurations doivent être définies dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="4817e-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="4817e-106">Examinons un exemple simple :</span><span class="sxs-lookup"><span data-stu-id="4817e-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="4817e-107">Dans cet exemple, `FileConfig` accepte deux paramètres obligatoires, **CopyFrom** et **CopyTo**, tous deux utilisés comme valeurs pour les propriétés **SourcePath** et **DestinationPath** du bloc de ressources `File`.</span><span class="sxs-lookup"><span data-stu-id="4817e-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="4817e-108">La configuration `NestedConfig` appelle `FileConfig` comme s’il s’agissait d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="4817e-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="4817e-109">Les propriétés du bloc de ressources `NestedConfig` (**CopyFrom** et **CopyTo**) sont les paramètres de la configuration `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="4817e-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="4817e-110">DSC ne prend pas actuellement en charge l’imbrication de configurations dans des configurations imbriquées.</span><span class="sxs-lookup"><span data-stu-id="4817e-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="4817e-111">Vous pouvez uniquement imbriquer une configuration d’une profondeur de couche.</span><span class="sxs-lookup"><span data-stu-id="4817e-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="4817e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4817e-112">See Also</span></span>

- [<span data-ttu-id="4817e-113">Ressources composites : utilisation d’une configuration DSC en tant que ressource</span><span class="sxs-lookup"><span data-stu-id="4817e-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
