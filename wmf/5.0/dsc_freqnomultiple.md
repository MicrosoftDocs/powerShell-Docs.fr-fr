---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="5886a-102">Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples les unes des autres</span><span class="sxs-lookup"><span data-stu-id="5886a-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="5886a-103">Dans la version précédente de DSC, le gestionnaire de configuration local traitait `RefreshFrequencyMins` et `ConfigurationModeFrequencyMins` comme des multiples.</span><span class="sxs-lookup"><span data-stu-id="5886a-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="5886a-104">Dans WMF 5.0 RTM, ces propriétés sont traitées indépendamment l’une de l’autre.</span><span class="sxs-lookup"><span data-stu-id="5886a-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="5886a-105">Pour plus d’informations, consultez [Configuration du Gestionnaire de configuration local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="5886a-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
