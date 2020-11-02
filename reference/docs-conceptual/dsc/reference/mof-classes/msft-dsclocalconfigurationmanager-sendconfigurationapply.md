---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApply, méthode
description: SendConfigurationApply, méthode
ms.openlocfilehash: 9bd63220644e096b348f71ee9d4ac216af6a7ccc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648972"
---
# <a name="sendconfigurationapply-method"></a>SendConfigurationApply, méthode

Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.

## <a name="syntax"></a>Syntaxe

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Paramètres

**ConfigurationData** \[in\] Les données d’environnement pour la configuration.

**force** \[in\] **true** pour forcer l’arrêt de la configuration.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
