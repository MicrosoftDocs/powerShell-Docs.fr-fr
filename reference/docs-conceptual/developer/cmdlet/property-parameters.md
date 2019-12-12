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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369578"
---
# <a name="property-parameters"></a>Paramètres de propriété

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres de propriété.

|Paramètre|Fonctionnalités|
|---|---|
|**Compter**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre d’objets à traiter.|
|**Description**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une description pour une ressource.|
|**From**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’objet de référence à partir duquel les informations doivent être extraites.|
|**Id**<br>Type de données : dépendant de la ressource|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier l’identificateur d’une ressource.|
|**Entrée**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la spécification du fichier d’entrée.|
|**Emplacement**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’emplacement de la ressource.|
|**LogName**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom du fichier journal à traiter ou utiliser.|
|**Name**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom de la ressource.|
|**Sortie**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le fichier de sortie.|
|**Propriétaire**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom du propriétaire de la ressource.|
|**Propriété**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom ou les noms des propriétés à utiliser.|
|**Reason**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la raison pour laquelle cette applet de commande est appelée.|
|**Regex**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les expressions régulières soient utilisées lorsque le paramètre est spécifié. Lorsque ce paramètre est spécifié, les caractères génériques ne sont pas résolus.|
|**Vitesse**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la vitesse en bauds. L’utilisateur définit ce paramètre sur la vitesse de la ressource.|
|**État**<br>Type de données : tableau de mots clés|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le nom des États, par exemple keyverse.|
|**Valeur**<br>Type de données : objet|Implémentez ce paramètre afin que l’utilisateur puisse spécifier une valeur à fournir à l’applet de commande.|
|**Version**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la version de la propriété.|

## <a name="see-also"></a>Voir aussi

[Paramètres d’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
