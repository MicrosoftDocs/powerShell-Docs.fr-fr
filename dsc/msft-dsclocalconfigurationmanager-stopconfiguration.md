---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218873"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager

Arrête la modification de la configuration en cours.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a>Paramètres
----------

*force* \[in\] **true** pour forcer l’arrêt de la configuration.

## <a name="return-value"></a>Valeur renvoyée
------------

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications
------------
>**MOF :** DscCore.mof

>**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Voir aussi


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)