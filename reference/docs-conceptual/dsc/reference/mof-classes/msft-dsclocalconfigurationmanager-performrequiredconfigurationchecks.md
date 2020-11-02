---
ms.date: 07/17/2020
ms.topic: reference
title: PerformRequiredConfigurationChecks, méthode
description: PerformRequiredConfigurationChecks, méthode
ms.openlocfilehash: c5e847cda6376f4266cc771dc947032a279e25f4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650826"
---
# <a name="performrequiredconfigurationchecks-method"></a>PerformRequiredConfigurationChecks, méthode

Commence une vérification de cohérence à l’aide du Planificateur de tâches.

## <a name="syntax"></a>Syntaxe

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Paramètres

**Flags** \[in\] Masque de bits qui spécifie le type de vérification de cohérence à exécuter. Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :

|Valeur |Description |
|:--- |:---|
|**1** | Vérification de cohérence normale. |
|**2** | Poursuite d’une vérification de cohérence après un redémarrage. Cette valeur ne doit pas être combinée avec d’autres valeurs. |
|**4** | La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud. Cette valeur doit toujours être combinée avec **1** avec une valeur de **5** . |
|**8** | Envoyez l’état au serveur de rapports. |

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
