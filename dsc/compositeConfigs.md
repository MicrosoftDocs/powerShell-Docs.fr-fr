---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Imbrication des configurations
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="38590-103">Imbrication des configurations DSC</span><span class="sxs-lookup"><span data-stu-id="38590-103">Nesting DSC configurations</span></span>

<span data-ttu-id="38590-104">Une configuration imbriquée (également appelée configuration composite) est une configuration appelée dans une autre configuration, comme s’il s’agissait d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="38590-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="38590-105">Les deux configurations doivent être définies dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="38590-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="38590-106">Examinons un exemple simple :</span><span class="sxs-lookup"><span data-stu-id="38590-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="38590-107">Dans cet exemple, `FileConfig` accepte deux paramètres obligatoires, **CopyFrom** et **CopyTo**, tous deux utilisés comme valeurs pour les propriétés **SourcePath** et **DestinationPath** du bloc de ressources `File`.</span><span class="sxs-lookup"><span data-stu-id="38590-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="38590-108">La configuration `NestedConfig` appelle `FileConfig` comme s’il s’agissait d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="38590-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="38590-109">Les propriétés du bloc de ressources `NestedConfig` (**CopyFrom** et **CopyTo**) sont les paramètres de la configuration `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="38590-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="38590-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38590-110">See Also</span></span>

- [<span data-ttu-id="38590-111">Ressources composites : utilisation d’une configuration DSC en tant que ressource</span><span class="sxs-lookup"><span data-stu-id="38590-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)