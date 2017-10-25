---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
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

*All* \[in\]  
**true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.

*configurationStatus* \[out\]  
En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.

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


 

 



