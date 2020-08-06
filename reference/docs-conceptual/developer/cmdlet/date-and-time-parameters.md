---
title: Paramètres de date et d’heure | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f1b2bb3b3da2b73860298e36d88502bfd67c5b22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774658"
---
# <a name="date-and-time-parameters"></a>Paramètres de date et d’heure

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres qui gèrent les informations de date et d’heure. Les paramètres de date et d’heure sont généralement utilisés pour enregistrer lors de la création ou de l’accès à un.

|Paramètre|Fonctionnalité|
|---|---|
|**Atteint**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que, lorsqu’il est spécifié, l’applet de commande fonctionne sur les ressources qui ont été consultées en fonction de la date et de l’heure spécifiées par les paramètres **Before** et **after** . Si ce paramètre est spécifié, les paramètres **créés** et **modifiés** ne doivent pas être spécifiés.|
|**Après**<br>Type de données : DateTime|Implémentez ce paramètre pour spécifier la date et l’heure après lesquelles l’applet de commande a été utilisée. Pour que le paramètre **after** fonctionne, l’applet de commande doit également avoir un paramètre **accessible**, **créé**ou **modifié** . Et, ce paramètre doit avoir la valeur **true** lorsque l’applet de commande est appelée.|
|**Avant**<br>Type de données : DateTime|Implémentez ce paramètre pour spécifier la date et l’heure auxquelles l’applet de commande a été utilisée. Pour que le paramètre **Before** fonctionne, l’applet de commande doit également avoir un paramètre **accessible**, **créé**ou **modifié** . Et, ce paramètre doit avoir la valeur **true** lorsque l’applet de commande est appelée.|
|**Créé le**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que, lorsqu’il est spécifié, l’applet de commande fonctionne sur les ressources qui ont été créées en fonction de la date et de l’heure spécifiées par les paramètres **Before** et **after** . Si ce paramètre est spécifié, les paramètres **accessibles** et **modifiés** ne doivent pas être spécifiés.|
|**Exact**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que, lorsqu’il est spécifié, le terme de ressource doive correspondre exactement au nom de la ressource. Lorsque le paramètre n’est pas spécifié, le terme et le nom de la ressource n’ont pas besoin de correspondre exactement.|
|**Port**<br>Type de données : DateTime|Implémentez ce paramètre afin que, lorsqu’il est spécifié, l’applet de commande fonctionne sur les ressources qui ont été modifiées en fonction de la date et de l’heure spécifiées par les paramètres **Before** et **after** . Si ce paramètre est spécifié, les paramètres **accédé** et **créé** ne doivent pas être spécifiés.|
## <a name="see-also"></a>Voir aussi

[Paramètres des applets de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
