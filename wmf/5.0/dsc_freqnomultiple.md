---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058401"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples les unes des autres

Dans la version précédente de DSC, le gestionnaire de configuration local traitait `RefreshFrequencyMins` et `ConfigurationModeFrequencyMins` comme des multiples. Dans WMF 5.0 RTM, ces propriétés sont traitées indépendamment l’une de l’autre.

Pour plus d’informations, consultez [Configuration du Gestionnaire de configuration local](https://msdn.microsoft.com/powershell/dsc/metaconfig).
