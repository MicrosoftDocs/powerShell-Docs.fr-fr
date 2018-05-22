---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="0f3ea-102">L’applet de commande Test-DscConfiguration prend en charge les configurations de référence</span><span class="sxs-lookup"><span data-stu-id="0f3ea-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="0f3ea-103">L’applet de commande Test-DscConfiguration a été mise à jour pour autoriser le test de l’état de configuration souhaitée d’un ou plusieurs nœuds cibles en spécifiant un document de configuration de référence à comparer.</span><span class="sxs-lookup"><span data-stu-id="0f3ea-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="0f3ea-104">Les nouveaux jeux de paramètres suivants utilisent des configurations DSC dans le chemin spécifié uniquement pour tester et jamais pour appliquer chaque configuration sur les nœuds cibles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0f3ea-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="0f3ea-105">Comme avec Start-DscConfiguration et d’autres applets de commande DSC, le nom de chaque document MOF est utilisé pour déterminer le nœud cible sur lequel tester la configuration.</span><span class="sxs-lookup"><span data-stu-id="0f3ea-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

<span data-ttu-id="0f3ea-106">Les nouveaux jeux de paramètres suivants utilisent une configuration DSC unique seulement pour tester et jamais pour appliquer la configuration sur les nœuds cibles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0f3ea-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
