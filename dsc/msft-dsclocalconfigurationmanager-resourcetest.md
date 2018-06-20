---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 714bbb286ebbe4ed0f1faa15e03ac4b51a3ee87f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218856"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager

Appelle directement la méthode **Test** d’une ressource DSC.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>Paramètres
----------

*ResourceType* \[in\] Nom de la ressource à appeler.

*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.

*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.

*InDesiredState* \[out\] En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.

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