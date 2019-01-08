---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047434"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager

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

MOF** DscCore.mof

**Espace de noms : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)