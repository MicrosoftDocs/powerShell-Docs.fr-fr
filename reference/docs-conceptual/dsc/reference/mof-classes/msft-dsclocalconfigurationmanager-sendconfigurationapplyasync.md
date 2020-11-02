---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApplyAsync, méthode
description: SendConfigurationApplyAsync, méthode
ms.openlocfilehash: 92c9d03a7653e72b1ff04084caea4a8b5aadb0e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644793"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync, méthode

Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.

## <a name="syntax"></a>Syntaxe

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Paramètres

**ConfigurationData** \[in\] Les données d’environnement pour la configuration.

**force** \[in\] **true** pour forcer l’arrêt de la configuration.

**jobId** \[in\] ID du travail pour lequel envoyer la configuration.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
