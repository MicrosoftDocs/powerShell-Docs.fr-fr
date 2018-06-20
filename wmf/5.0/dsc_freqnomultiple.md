---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218380"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples les unes des autres

Dans la version précédente de DSC, le gestionnaire de configuration local traitait `RefreshFrequencyMins` et `ConfigurationModeFrequencyMins` comme des multiples. Dans WMF 5.0 RTM, ces propriétés sont traitées indépendamment l’une de l’autre.

Pour plus d’informations, consultez [Configuration du Gestionnaire de configuration local](https://msdn.microsoft.com/powershell/dsc/metaconfig).
