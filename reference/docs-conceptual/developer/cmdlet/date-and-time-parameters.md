---
title: Paramètres de date et d’heure | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369788"
---
# <a name="date-and-time-parameters"></a>Paramètres de date et d’heure

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres qui gèrent les informations de date et d’heure. Les paramètres de date et d’heure sont généralement utilisés pour enregistrer lors de la création ou de l’accès à un.

|Paramètre|Fonctionnalités|
|---|---|
|**Atteint**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que, lorsqu’il est spécifié, l’applet de commande fonctionne sur les ressources qui ont été consultées en fonction de la date et de l’heure spécifiées par les paramètres **Before** et **after** . Si ce paramètre est spécifié, les paramètres **créés** et **modifiés** ne doivent pas être spécifiés.|
|**Postérieur**<br>Type de données : DateTime|Implémentez ce paramètre pour spécifier la date et l’heure après lesquelles l’applet de commande a été utilisée. Pour que le paramètre **after** fonctionne, l’applet de commande doit également avoir un paramètre **accessible**, **créé**ou **modifié** . Et, ce paramètre doit avoir la valeur **true** lorsque l’applet de commande est appelée.|
|**Antérieures**<br>Type de données : DateTime|Implémentez ce paramètre pour spécifier la date et l’heure auxquelles l’applet de commande a été utilisée. Pour que le paramètre **Before** fonctionne, l’applet de commande doit également avoir un paramètre **accessible**, **créé**ou **modifié** . Et, ce paramètre doit avoir la valeur **true** lorsque l’applet de commande est appelée.|
|**Créer**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que, lorsqu’il est spécifié, l’applet de commande fonctionne sur les ressources qui ont été créées en fonction de la date et de l’heure spécifiées par les paramètres **Before** et **after** . Si ce paramètre est spécifié, les paramètres **accessibles** et **modifiés** ne doivent pas être spécifiés.|
|**Identique**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que, lorsqu’il est spécifié, le terme de ressource doive correspondre exactement au nom de la ressource. Lorsque le paramètre n’est pas spécifié, le terme et le nom de la ressource n’ont pas besoin de correspondre exactement.|
|**Port**<br>Type de données : DateTime|Implémentez ce paramètre afin que, lorsqu’il est spécifié, l’applet de commande fonctionne sur les ressources qui ont été modifiées en fonction de la date et de l’heure spécifiées par les paramètres **Before** et **after** . Si ce paramètre est spécifié, les paramètres **accédé** et **créé** ne doivent pas être spécifiés.|
## <a name="see-also"></a>Voir aussi

[Paramètres d’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
