---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: TestConfiguration, méthode
ms.openlocfilehash: 0611c4d5543c49b879bef9b60cafdd0b055c9b86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464296"
---
# <a name="testconfiguration-method"></a>TestConfiguration, méthode

Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.

## <a name="syntax"></a>Syntaxe

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Paramètres

**configurationData** \[in\] Données d’environnement pour la configuration.

**InDesiredState** \[out\] En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.

**ResourcesInDesiredState** \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.

**ResourcesNotInDesiredState** \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
