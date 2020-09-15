---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: GetConfigurationResultOutput, méthode
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464075"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput, méthode

Obtient la sortie de l’agent de configuration associée à un travail spécifique.

## <a name="syntax"></a>Syntaxe

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Paramètres

**jobId** \[in\] ID du travail pour lequel obtenir les données de sortie.

**resumeOutputBookmark** \[in\] Spécifie que la sortie doit être une continuation à partir d’un signet précédent.

**output** \[out\] Sortie pour le travail spécifié.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
