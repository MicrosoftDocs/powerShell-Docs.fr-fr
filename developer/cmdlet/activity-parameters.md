---
title: Paramètres d’activité | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075186"
---
# <a name="activity-parameters"></a>Paramètres d’activité

Le tableau suivant répertorie les noms recommandés pour les paramètres de l’activité.

|Paramètre|Fonctionnalités|
|---|---|
|**Ajouter**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’utilisateur peut ajouter du contenu à la fin d’une ressource lorsque le paramètre est spécifié.|
|**CaseSensitive**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin de l’utilisateur peut nécessiter respecte la casse lorsque le paramètre est spécifié.|
|**Command**<br>Type de données : String|Implémentez ce paramètre afin de l’utilisateur peut spécifier une chaîne de commande à exécuter.|
|**CompatibleVersion**<br>Type de données : Objet System.Version|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier la sémantique de l’applet de commande doit être compatible avec pour assurer la compatibilité avec les versions précédentes.|
|**Compresser**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que la compression de données est utilisée lorsque le paramètre est spécifié.|
|**Compresser**<br>Type de données : Mot clé|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’algorithme à utiliser pour la compression de données.|
|**continue**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les données sont traitées jusqu'à ce que l’utilisateur met fin à l’applet de commande lorsque le paramètre est spécifié. Si le paramètre n’est pas spécifié, l’applet de commande traite une quantité de données prédéfinie, puis termine l’opération.|
|**Create**<br>Type de données : SwitchParameter|Implémentez ce paramètre pour indiquer qu’une ressource est créée si celle-ci n’existe pas lorsque le paramètre est spécifié.|
|**Supprimer**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les ressources sont supprimés lors de l’applet de commande a terminé son opération lorsque le paramètre est spécifié.|
|**Aspirer**<br>Type de données : SwitchParameter|Implémentez ce paramètre pour indiquer que les éléments de travail en attente sont traitées avant que l’applet de commande traite des nouvelles données lorsque le paramètre est spécifié. Si le paramètre n’est pas spécifié, les éléments de travail sont traités immédiatement.|
|**effacement**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nombre de fois où qu'une ressource est effacée avant sa suppression.|
|**ErrorLevel**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur peut spécifier le niveau d’erreur à signaler.|
|**Exclude**<br>Type de données : String[]|Implémentez ce paramètre afin que l’utilisateur peut exclure quelque chose à partir d’une activité. Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [les paramètres de filtre d’entrée](input-filter-parameters.md).|
|**Filter**<br>Type de données : Mot clé|Implémentez ce paramètre afin que l’utilisateur peut spécifier un filtre qui sélectionne les ressources sur lequel effectuer l’action de l’applet de commande. Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [les paramètres de filtre d’entrée](./input-filter-parameters.md).|
|**Suivez**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les cours suivi lorsque le paramètre est spécifié.|
|**Force**<br>Type de données : SwitchParameter|Implémentez ce paramètre pour indiquer que l’utilisateur peut effectuer une action même si les restrictions sont rencontrées lorsque le paramètre est spécifié. Le paramètre n’autorise pas la sécurité d’être compromise. Par exemple, ce paramètre permet à un utilisateur de remplacer un fichier en lecture seule.|
|**Include**<br>Type de données : String[]|Implémentez ce paramètre afin que l’utilisateur peut inclure un élément dans une activité. Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [les paramètres de filtre d’entrée](input-filter-parameters.md).|
|**Incremental**<br>Type de données : SwitchParameter|Implémentez ce paramètre pour indiquer que le traitement est effectué de façon incrémentielle lorsque le paramètre est spécifié. Par exemple, ce paramètre permet à un utilisateur effectue des sauvegardes incrémentielles sauvegarder des fichiers uniquement depuis la dernière sauvegarde.|
|**InputObject**<br>Type de données : Objet|Implémentez ce paramètre lors de l’applet de commande prend en entrée à partir d’autres applets de commande. Lorsque vous définissez un **InputObject** paramètre, spécifiez toujours le **ValueFromPipeline** mot clé lorsque vous déclarez le **paramètre** attribut. Pour plus d’informations sur l’utilisation de filtres d’entrée, consultez [les paramètres de filtre d’entrée](./input-filter-parameters.md).|
|**INSERT**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande insère un élément lorsque le paramètre est spécifié.|
|**Interactive**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande fonctionne mode interactif avec l’utilisateur lorsque le paramètre est spécifié.|
|**Intervalle**<br>Type de données : HashTable|Implémentez ce paramètre afin que l’utilisateur peut spécifier une table de hachage des mots clés qui contient les valeurs. L’exemple suivant montre des exemples de valeurs pour le **intervalle** paramètre : `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Type de données : SwitchParameter|Implémenter cet audit paramètre les actions de l’applet de commande lorsque le paramètre est spécifié.|
|**NoClobber**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que la ressource ne sera pas remplacée lorsque le paramètre est spécifié. Ce paramètre s’applique généralement aux applets de commande qui créent de nouveaux objets afin qu’ils peuvent être empêchés remplacement d’objets existants portant le même nom.|
|**Notify**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’utilisateur est informé que l’activité est terminée lorsque le paramètre est spécifié.|
|**NotifyAddress**<br>Type de données : Adresse de messagerie|Mettre en œuvre de ce paramètre afin que l’utilisateur peut spécifier l’adresse de messagerie à utiliser pour envoyer une notification lorsque le **Notify** est précisé.|
|**Overwrite**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande remplace toutes les données existantes lorsque le paramètre est spécifié.|
|**Inviter**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une invite pour l’applet de commande.|
|**Silencieux**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande supprime les commentaires des utilisateurs au cours de ses actions lorsque le paramètre est spécifié.|
|**Recurse**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les applets de commande de manière récursive effectue ses actions sur les ressources lorsque le paramètre est spécifié.|
|**Réparation**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande va tenter de corriger quelque chose à partir d’un état interrompu lorsque le paramètre est spécifié.|
|**RepairString**<br>Type de données : String|Mettre en œuvre de ce paramètre afin que l’utilisateur peut spécifier une chaîne à utiliser lorsque le **réparation** est précisé.|
|**Retry**<br>Type de données : Int32|Implémentez ce paramètre afin de l’utilisateur peut spécifier le nombre de fois que l’applet de commande va tenter une action.|
|**Select**<br>Type de données : Tableau de mot clé|Implémentez ce paramètre afin que l’utilisateur peut spécifier un tableau des types d’éléments.|
|**flux de données**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin de l’utilisateur peut diffuser plusieurs objets de sortie via le pipeline lorsque le paramètre est spécifié.|
|**Strict**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que toutes les erreurs sont gérées comme des erreurs avec fin d’exécution lorsque le paramètre est spécifié.|
|**TempLocation**<br>Type de données : String|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier l’emplacement des données temporaires qui sont utilisées pendant l’opération de l’applet de commande.|
|**Délai d’attente**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’intervalle de délai d’attente (en millisecondes).|
|**tronquer**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande va tronquer ses actions lorsque le paramètre est spécifié. Si le paramètre n’est pas spécifié, l’applet de commande effectue une autre action.|
|**Vérifier**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande sera tester pour déterminer si une action s’est produite lorsque le paramètre est spécifié.|
|**attente**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’applet de commande attendra pour l’entrée utilisateur avant de continuer lorsque le paramètre est spécifié.
|**WaitTime**<br>Type de données : Int32|Mettre en œuvre de ce paramètre afin que l’utilisateur peut spécifier la durée (en secondes) que l’applet de commande attendra utilisateur entrée quand le **attente** est précisé.|

## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
