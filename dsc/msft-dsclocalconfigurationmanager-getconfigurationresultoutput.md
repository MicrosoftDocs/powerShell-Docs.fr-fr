---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186804"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager

Obtient la sortie de l’agent de configuration associée à un travail spécifique.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Paramètres
----------

*jobId* \[in\] ID du travail pour lequel obtenir les données de sortie.

*resumeOutputBookmark* \[in\] Spécifie que la sortie doit être une continuation à partir d’un signet précédent.

*output* \[out\] Sortie pour le travail spécifié.

## <a name="return-value"></a>Valeur renvoyée
------------

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications
------------
>**MOF :** DscCore.mof

>**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Voir aussi


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)