---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager

Commence une vérification de cohérence à l’aide du Planificateur de tâches.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Paramètres
----------

*Flags* \[in\]  
Masque de bits qui spécifie le type de vérification de cohérence à exécuter. Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :

|Valeur |Description |
|:--- |:---|
|**1** | Vérification de cohérence normale. |
|**2** | Poursuite d’une vérification de cohérence après un redémarrage. Cette valeur ne doit pas être combinée avec d’autres valeurs. |
|**4** | La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud. Cette valeur doit toujours être combinée avec **1** avec une valeur de **5**. |
|**8** | Envoyez l’état au serveur de rapports. |

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


 

 



