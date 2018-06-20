---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188283"
---
# <a name="separation-of-node-and-configuration-ids"></a>Séparation des ID de nœud et de configuration

## <a name="overview"></a>Vue d’ensemble

Afin d’offrir une expérience plus flexible et rationalisée lors de l’utilisation de DSC en mode par extraction, nous avons ajouté un certain nombre de fonctionnalités dans cette version. Ces fonctionnalités ont pour but de vous aider à configurer et à déployer des configurations sur plusieurs nœuds de manière simple et flexible, tout en assurant le suivi et en fournissant des informations pour chaque nœud.
Il s’agit des fonctionnalités suivantes :

* Un nom de configuration qui identifie la configuration d’un ordinateur. Ce nom peut être partagé par plusieurs nœuds cibles.
* Un ID d’agent qui identifie de façon unique un nœud unique.
* Une étape d’inscription qui est exécutée uniquement la première fois qu’un nœud cible se connecte à un serveur collecteur.

**Remarque :** Ces fonctionnalités ont été ajoutées et ne remplacent pas les fonctionnalités et les concepts d’extraction existants. Vous pouvez utiliser ces nouvelles fonctionnalités ou les anciennes avec le nouveau serveur collecteur fourni avec cette version.

Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide du nom de configuration](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).
