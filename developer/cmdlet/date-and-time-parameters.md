---
title: Paramètres de date et heure | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068230"
---
# <a name="date-and-time-parameters"></a>Paramètres de date et d’heure

Le tableau suivant répertorie les noms recommandés et les fonctionnalités pour les paramètres qui gèrent les informations de date / heure. Paramètres de date et heure servent généralement à enregistrer lorsque quelque chose est créée ou accédée.

|Paramètre|Fonctionnalités|
|---|---|
|**Accessed**<br>Type de données : SwitchParameter|Mettre en œuvre de ce paramètre afin que lorsqu’il est spécifié à l’applet de commande opère sur les ressources qui ont été consultés basée sur la date et l’heure spécifiée par le **avant** et **après** paramètres. Si ce paramètre est spécifié, le **créé** et **Modified** paramètres doivent être ne pas être spécifié.|
|**Après avoir**<br>Type de données : DateTime|Implémentez ce paramètre pour spécifier la date et l’heure après laquelle l’applet de commande a été utilisé. Pour le **après** paramètre fonctionne, l’applet de commande doit également avoir un **Accessed**, **créé**, ou **Modified** paramètre. Et, ce paramètre doit être défini sur **true** lorsque l’applet de commande est appelée.|
|**Avant**<br>Type de données : DateTime|Implémentez ce paramètre pour spécifier la date et l’heure avant laquelle l’applet de commande a été utilisé. Pour le **avant** paramètre fonctionne, l’applet de commande doit également avoir un **Accessed**, **créé**, ou **Modified** paramètre. Et, ce paramètre doit être défini sur **true** lorsque l’applet de commande est appelée.|
|**Créé**<br>Type de données : SwitchParameter|Mettre en œuvre de ce paramètre afin que lorsqu’il est spécifié à l’applet de commande opère sur les ressources qui ont été créés basés sur la date et l’heure spécifiée par le **avant** et **après** paramètres. Si ce paramètre est spécifié, le **Accessed** et **Modified** paramètres ne doivent pas être spécifiés.|
|**Exacte**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que lorsqu’il est spécifié le terme de la ressource doit correspondre au nom ressource exactement. Lorsque le paramètre n’est pas spécifié le terme de la ressource et le nom n’avez pas besoin de correspondre exactement.|
|**Modifié**<br>Type de données : DateTime|Mettre en œuvre de ce paramètre afin que lorsqu’il est spécifié à l’applet de commande opère sur les ressources qui ont été modifiées basée sur la date et l’heure spécifiée par le **avant** et **après** paramètres. Si ce paramètre est spécifié, le **Accessed** et **créé** paramètres ne doivent pas être spécifiés.|
## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
