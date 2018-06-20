---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219876"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager

Restaure la configuration à une version précédente.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Paramètres
----------

*configurationNumber* \[in\] Spécifie la configuration demandée.

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