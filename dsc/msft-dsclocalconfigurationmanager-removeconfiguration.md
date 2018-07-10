---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892682"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager

Supprime les fichiers de configuration.

## <a name="syntax"></a>Syntaxe

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Paramètres

*Stage* \[in\] Spécifie le document de configuration à supprimer. Les valeurs suivantes sont valides :

|Valeur |Description |
|:--- |:---|
|**1** | Document de configuration **Current** (current.mof). |
|**2** | Document de configuration **Pending** (pending.mof).  |
|**4** | Document de configuration **Previous** (previous.mof). |

*Force* \[in\] **true** pour forcer la suppression de la configuration.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)