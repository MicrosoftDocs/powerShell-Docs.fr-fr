---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: SendConfigurationApplyAsync, méthode
ms.openlocfilehash: 4cfac5edb5fed94ee69deb98d7aa6be56b51c5b3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463735"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync, méthode

Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.

## <a name="syntax"></a>Syntaxe

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
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

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
