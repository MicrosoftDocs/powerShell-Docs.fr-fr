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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364638"
---
# <a name="activity-parameters"></a>Paramètres d’activité

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres d’activité.

|Paramètre|Fonctionnalités|
|---|---|
|**Append**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour permettre à l’utilisateur d’ajouter du contenu à la fin d’une ressource lorsque le paramètre est spécifié.|
|**CaseSensitive**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’utilisateur puisse exiger le respect de la casse lorsque le paramètre est spécifié.|
|**Commandee**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier une chaîne de commande à exécuter.|
|**CompatibleVersion**<br>Type de données : objet System. version|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la sémantique avec laquelle l’applet de commande doit être compatible pour la compatibilité avec les versions précédentes.|
|**Compresser**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que la compression des données soit utilisée lorsque le paramètre est spécifié.|
|**Compresser**<br>Type de données : mot clé|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’algorithme à utiliser pour la compression des données.|
|**Propositions**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les données soient traitées jusqu’à ce que l’utilisateur mette fin à l’applet de commande lorsque le paramètre est spécifié. Si le paramètre n’est pas spécifié, l’applet de commande traite une quantité de données prédéfinie, puis termine l’opération.|
|**Créer**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour indiquer qu’une ressource est créée s’il n’en existe pas déjà une lorsque le paramètre est spécifié.|
|**Supprimer**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les ressources soient supprimées lorsque l’applet de commande a terminé son opération lorsque le paramètre est spécifié.|
|**Vidé**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour indiquer que les éléments de travail en suspens sont traités avant que l’applet de commande traite les nouvelles données lorsque le paramètre est spécifié. Si le paramètre n’est pas spécifié, les éléments de travail sont traités immédiatement.|
|**Erase**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre de fois où une ressource est effacée avant d’être supprimée.|
|**ErrorLevel**<br>Type de données : Int32|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le niveau d’erreurs à signaler.|
|**Exclure**<br>Type de données : String []|Implémentez ce paramètre afin que l’utilisateur puisse exclure des éléments d’une activité. Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](input-filter-parameters.md).|
|**Filtre**<br>Type de données : mot clé|Implémentez ce paramètre afin que l’utilisateur puisse spécifier un filtre qui sélectionne les ressources sur lesquelles exécuter l’action d’applet de commande. Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](./input-filter-parameters.md).|
|**Suivez**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que la progression soit suivie lorsque le paramètre est spécifié.|
|**Force**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour indiquer que l’utilisateur peut exécuter une action même si des restrictions sont rencontrées lorsque le paramètre est spécifié. Le paramètre ne permet pas de compromettre la sécurité. Par exemple, ce paramètre permet à un utilisateur de remplacer un fichier en lecture seule.|
|**Include**<br>Type de données : String []|Implémentez ce paramètre pour permettre à l’utilisateur d’inclure des éléments dans une activité. Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](input-filter-parameters.md).|
|**Incrémentielle**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour indiquer que le traitement est effectué de façon incrémentielle lorsque le paramètre est spécifié. Par exemple, ce paramètre permet à un utilisateur d’effectuer des sauvegardes incrémentielles qui sauvegardent des fichiers uniquement depuis la dernière sauvegarde.|
|**InputObject**<br>Type de données : objet|Implémentez ce paramètre lorsque l’applet de commande prend en entrée d’autres applets de commande. Quand vous définissez un paramètre **InputObject** , spécifiez toujours le mot clé **ValueFromPipeline** lorsque vous déclarez l’attribut de **paramètre** . Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](./input-filter-parameters.md).|
|**Insert**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande insère un élément lorsque le paramètre est spécifié.|
|**Interactive**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande fonctionne de manière interactive avec l’utilisateur lorsque le paramètre est spécifié.|
|**Intervalle**<br>Type de données : HashTable|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une table de hachage de mots clés qui contient les valeurs. L’exemple suivant montre des exemples de valeurs pour le paramètre **Interval** : `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour auditer les actions de l’applet de commande lorsque le paramètre est spécifié.|
|**NoClobber**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que la ressource ne soit pas remplacée lorsque le paramètre est spécifié. Ce paramètre s’applique généralement aux applets de commande qui créent des objets, afin qu’ils puissent empêcher le remplacement des objets existants portant le même nom.|
|**Indiquer**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’utilisateur soit informé que l’activité est terminée lorsque le paramètre est spécifié.|
|**NotifyAddress**<br>Type de données : adresse de messagerie|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’adresse de messagerie à utiliser pour envoyer une notification lorsque le paramètre **Notify** est spécifié.|
|**Remplacer**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande remplace toutes les données existantes lorsque le paramètre est spécifié.|
|**Demander**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier une invite pour l’applet de commande.|
|**Silencieux**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande supprime les commentaires de l’utilisateur pendant ses actions lorsque le paramètre est spécifié.|
|**Recurse**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande effectue ses actions de manière récursive sur les ressources lorsque le paramètre est spécifié.|
|**Repair**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande tente de corriger un état de rupture lorsque le paramètre est spécifié.|
|**RepairString**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier une chaîne à utiliser lorsque le paramètre de **réparation** est spécifié.|
|**Nouvelle tentative**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre de fois où l’applet de commande tentera une action.|
|**Sélectionner**<br>Type de données : tableau de mots clés|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un tableau des types d’éléments.|
|**Flux**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’utilisateur puisse diffuser plusieurs objets de sortie via le pipeline lorsque le paramètre est spécifié.|
|**Strict**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que toutes les erreurs soient traitées comme des erreurs d’arrêt lorsque le paramètre est spécifié.|
|**TempLocation**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’emplacement des données temporaires utilisées pendant l’opération de l’applet de commande.|
|**Timeout**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’intervalle de délai d’attente (en millisecondes).|
|**Tronquer**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande tronque ses actions lorsque le paramètre est spécifié. Si le paramètre n’est pas spécifié, l’applet de commande effectue une autre action.|
|**Vérifier**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande effectue un test pour déterminer si une action a eu lieu lorsque le paramètre est spécifié.|
|**Wait**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que l’applet de commande attende l’entrée de l’utilisateur avant de continuer lorsque le paramètre est spécifié.
|**Délai**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la durée (en secondes) pendant laquelle l’applet de commande attendra l’entrée de l’utilisateur lorsque le paramètre **Wait** est spécifié.|

## <a name="see-also"></a>Voir aussi

[Paramètres d’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
