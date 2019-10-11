---
ms.date: 10/16/2017
keywords: dsc,powershell,configuration,setup
title: Application des configurations
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953646"
---
# <a name="enacting-configurations"></a>Application des configurations

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Il existe deux façons de promulguer des configurations DSC PowerShell : le mode par envoi et le mode par extraction.

## <a name="push-mode"></a>Mode par envoi

![Mode par envoi](../images/pushModel.png "Fonctionnement du mode par envoi")

Avec le mode par envoi, l’utilisateur applique activement une configuration à un nœud cible en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

Après la création et la compilation d’une configuration, vous pouvez la promulguer avec le mode par envoi en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) et en définissant le paramètre -Path de l’applet de commande sur le chemin de la configuration MOF.
Par exemple, si la configuration MOF se trouve à l’emplacement `C:\DSC\Configurations\localhost.mof`, vous pouvez l’appliquer à l’ordinateur local avec la commande suivante :`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Remarque__ : par défaut, DSC exécute une configuration comme tâche en arrière-plan. Pour exécuter la configuration de manière interactive, appelez [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) avec le paramètre __-Wait__.

## <a name="pull-mode"></a>Mode par extraction

![Mode par extraction](../images/pullModel.png "Fonctionnement du mode par extraction")

Avec le mode par extraction, les clients d’extraction sont configurés de façon à obtenir leurs configurations d’état souhaité à partir d’un service d’extraction distant.
De même, le serveur a été configuré pour héberger le service DSC et approvisionné avec les configurations et les ressources requises par les clients d’extraction.
Chacun des clients d’extraction est associé à un événement planifié qui effectue une vérification de conformité à intervalles réguliers sur la configuration du nœud.
Quand l’événement est déclenché pour la première fois, le gestionnaire de configuration local sur le client d’extraction envoie une requête au service d’extraction pour obtenir la configuration spécifiée dans le gestionnaire de configuration local.
Si cette configuration existe sur le service d’extraction et si les vérifications de validation initiales renvoient un résultat positif, la configuration est téléchargée sur le client d’extraction, où elle est ensuite exécutée par le gestionnaire de configuration local.

Le gestionnaire de configuration local vérifie que le client est conforme à la configuration à intervalles réguliers, dont la fréquence est spécifiée par la propriété **ConfigurationModeFrequencyMins** du gestionnaire de configuration local.
Le gestionnaire de configuration local vérifie la présence de configurations mises à jour sur le service d’extraction à intervalles réguliers, spécifiés par la propriété **RefreshModeFrequency** du gestionnaire de configuration local.
Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md).

La solution recommandée pour l’hébergement d’un service d’extraction est le service de cloud DSC, [Azure Automation](https://azure.microsoft.com/services/automation/).
Cette solution hébergée fournit des fonctionnalités de gestion graphique, de rapports et de gestion centralisée.

Pour plus d’informations sur la configuration d’un service d’extraction sur Windows Server, consultez [Configuration d’un serveur collecteur sur Windows Server](pullServer.md).
N’oubliez cependant pas que cette implémentation a des fonctionnalités limitées et nécessite une intégration « faite maison ».

Les rubriques suivantes expliquent les clients et les services d’extraction :

- [Vue d’ensemble d’Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configuration d’un serveur collecteur SMB](pullServerSMB.md)
- [Configuration d’un client d’extraction](pullClientConfigID.md)
