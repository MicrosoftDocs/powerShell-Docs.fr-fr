---
ms.date: 07/14/2020
keywords: dsc,powershell,configuration,installation
title: ApplyConfiguration, méthode
ms.openlocfilehash: bec74ccd6f75448484adfd26bf8a4af4e224eb3f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463837"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration, méthode

Utilise l’agent de configuration pour appliquer la configuration en attente.

S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.

## <a name="syntax"></a>Syntaxe

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Paramètres

### <a name="force"></a>force

Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Configuration requise

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
