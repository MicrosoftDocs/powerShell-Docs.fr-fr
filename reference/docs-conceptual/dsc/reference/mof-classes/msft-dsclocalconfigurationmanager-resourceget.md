---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceGet, méthode
description: ResourceGet, méthode
ms.openlocfilehash: bff737f04e02740fa09fd82d7b27c75b11303dad
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650752"
---
# <a name="resourceget-method"></a>ResourceGet, méthode

Appelle directement la méthode **Get** d’une ressource DSC.

## <a name="syntax"></a>Syntaxe

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Paramètres

**ResourceType** \[in\] Nom de la ressource à appeler.

**ModuleName** \[in\] Nom du module qui contient la ressource à appeler.

**resourceProperty** \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.

**configurations** \[out\] En retour, contient une instance incorporée des configurations.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
