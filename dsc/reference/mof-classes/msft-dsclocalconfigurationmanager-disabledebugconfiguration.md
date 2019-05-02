---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ec5a401de4cb93f302f8572c0408e3f32d8876ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078892"
---
# <a name="disabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager

Désactive le débogage des ressources DSC.

## <a name="syntax"></a>Syntaxe

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>Paramètres

Cette méthode n’a aucun paramètre.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)