---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: EnableDebugConfiguration, méthode
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464092"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration, méthode

Active le débogage des ressources DSC.

## <a name="syntax"></a>Syntaxe

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Paramètres

**BreakAll** \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
