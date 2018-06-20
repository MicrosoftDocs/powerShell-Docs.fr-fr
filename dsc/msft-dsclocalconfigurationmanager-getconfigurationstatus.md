---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221763"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager

Obtenez l’historique des états de la configuration.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Paramètres
----------

*All* \[in\] **true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.

*configurationStatus* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.

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