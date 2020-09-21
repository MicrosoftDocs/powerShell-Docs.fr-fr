---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: ResourceTest, méthode
ms.openlocfilehash: 7ef65227342091cb2a5063aaf95a2780d217f85a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463803"
---
# <a name="resourcetest-method"></a>ResourceTest, méthode

Appelle directement la méthode **Test** d’une ressource DSC.

## <a name="syntax"></a>Syntaxe

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Paramètres

**ResourceType** \[in\] Nom de la ressource à appeler.

**ModuleName** \[in\] Nom du module qui contient la ressource à appeler.

***resourceProperty** \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.

*InDesiredState** \[out\] En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.

## <a name="return-value"></a>Valeur retournée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
