---
title: Mettre en forme paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251181"
---
# <a name="format-parameters"></a>Paramètres de format

Le tableau suivant répertorie les noms recommandés et les fonctionnalités pour les paramètres qui sont utilisées pour mettre en forme ou pour générer des données.

|Paramètre|Fonctionnalités|
|---|---|
|**en tant que**<br>Type de données : Mot clé|Implémentez ce paramètre pour spécifier le format de sortie d’applet de commande. Par exemple, les valeurs possibles peut être texte ou un Script.|
|**fichier binaire**<br>Type de données : SwitchParameter|Implémentez ce paramètre pour indiquer que l’applet de commande gère les valeurs binaires.|
|**Encodage**<br>Type de données : Mot clé|Implémentez ce paramètre pour spécifier le type de codage pris en charge. Par exemple, les valeurs possibles peut être ASCII, UTF-8, Unicode, UTF7, BigEndianUnicode, octets et chaîne.|
|**NewLine**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les caractères de saut de ligne sont pris en charge lorsque le paramètre est spécifié.|
|**ShortName**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les noms courts sont pris en charge lorsque le paramètre est spécifié.|
|**Width**<br>Type de données : Ent32|Implémentez ce paramètre afin que l’utilisateur peut spécifier la largeur du périphérique de sortie.|
|**Retour à la ligne**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que l’habillage du texte est pris en charge lorsque le paramètre est spécifié.|
## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
