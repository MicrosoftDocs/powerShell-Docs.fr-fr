---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply, méthode
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954876"
---
# <a name="sendmetaconfigurationapply-method"></a>SendMetaConfigurationApply, méthode

Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.

## <a name="syntax"></a>Syntaxe

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Paramètres

*ConfigurationData* \[in\] Les données d’environnement pour la configuration.

*force* \[in\] **true** pour forcer l’arrêt de la configuration.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
