---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: PerformRequiredConfigurationChecks, méthode
ms.openlocfilehash: ea4294ffdcb2580fa7b39b18966b642d58073eb6
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464449"
---
# <a name="performrequiredconfigurationchecks-method"></a>PerformRequiredConfigurationChecks, méthode

Commence une vérification de cohérence à l’aide du Planificateur de tâches.

## <a name="syntax"></a>Syntaxe

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Paramètres

**Flags** \[in\] Masque de bits qui spécifie le type de vérification de cohérence à exécuter. Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :

|Valeur |Description |
|:--- |:---|
|**1** | Vérification de cohérence normale. |
|**2** | Poursuite d’une vérification de cohérence après un redémarrage. Cette valeur ne doit pas être combinée avec d’autres valeurs. |
|**4** | La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud. Cette valeur doit toujours être combinée avec **1** avec une valeur de **5**. |
|**8** | Envoyez l’état au serveur de rapports. |

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
