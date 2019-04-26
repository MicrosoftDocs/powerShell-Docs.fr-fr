---
title: Paramètres de propriété | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067567"
---
# <a name="property-parameters"></a>Paramètres de propriété

Le tableau suivant répertorie les noms recommandés pour les paramètres de propriété.

|Paramètre|Fonctionnalités|
|---|---|
|**Count**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nombre d’objets à traiter.|
|**Description**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une description pour une ressource.|
|**De**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’objet de référence pour obtenir des informations à partir de.|
|**Id**<br>Type de données : Dépendance entre la ressource|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’identificateur d’une ressource.|
|**entrée**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier la spécification de fichier d’entrée.|
|**Emplacement**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’emplacement de la ressource.|
|**LogName**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom du fichier journal à traiter ou à utiliser.|
|**Nom**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom de la ressource.|
|**Output**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le fichier de sortie.|
|**Propriétaire**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom du propriétaire de la ressource.|
|**Propriété**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom ou les noms des propriétés à utiliser.|
|**raison**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier pourquoi cette applet de commande est appelée.|
|**Regex**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les expressions régulières sont utilisées lorsque le paramètre est spécifié. Lorsque ce paramètre est spécifié, les caractères génériques ne sont pas résolus.|
|**Vitesse**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur peut spécifier la vitesse de transmission. L’utilisateur définit ce paramètre à la vitesse de la ressource.|
|**État**<br>Type de données : Tableau de mot clé|Implémentez ce paramètre afin que l’utilisateur peut spécifier les noms des États, par exemple KEYDOWN.|
|**Valeur**<br>Type de données : Objet|Implémentez ce paramètre afin que l’utilisateur peut spécifier une valeur à fournir à l’applet de commande.|
|**Version**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier la version de la propriété.|

## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
