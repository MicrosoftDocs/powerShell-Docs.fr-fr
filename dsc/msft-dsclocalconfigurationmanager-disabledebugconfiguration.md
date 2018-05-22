---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fef4337e4e9c5cc72b457704899498624476f131
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="disabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager

Désactive le débogage des ressources DSC.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 DisableDebugConfiguration();
```

<a name="parameters"></a>Paramètres
----------

Cette méthode n’a aucun paramètre.

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