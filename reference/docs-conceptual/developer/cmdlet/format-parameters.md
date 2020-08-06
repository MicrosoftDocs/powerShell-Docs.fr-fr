---
title: Paramètres de format | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8e031f62aa8bcb0e9d5b900b2eace7187b1f3dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784280"
---
# <a name="format-parameters"></a>Paramètres de format

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres utilisés pour mettre en forme ou générer des données.

|Paramètre|Fonctionnalité|
|---|---|
|**Servir**<br>Type de données : mot clé|Implémentez ce paramètre pour spécifier le format de sortie de l’applet de commande. Par exemple, les valeurs possibles peuvent être du texte ou des scripts.|
|**Binaire**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour indiquer que l’applet de commande gère les valeurs binaires.|
|**Encodage**<br>Type de données : mot clé|Implémentez ce paramètre pour spécifier le type d’encodage pris en charge. Par exemple, les valeurs possibles sont ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte et String.|
|**Caractère**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les caractères de saut de ligne soient pris en charge lorsque le paramètre est spécifié.|
|**NomCourt**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les noms courts soient pris en charge lorsque le paramètre est spécifié.|
|**Width**<br>Type de données : Int32|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la largeur du périphérique de sortie.|
|**Encapsuler**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre pour que l’habillage du texte soit pris en charge lorsque le paramètre est spécifié.|
## <a name="see-also"></a>Voir aussi

[Paramètres des applets de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
