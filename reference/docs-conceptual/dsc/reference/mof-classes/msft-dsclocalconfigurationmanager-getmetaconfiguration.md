---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: GetMetaConfiguration, méthode
ms.openlocfilehash: 5111cb3b15e0fba0bf71b412580efdd3cd95b2dc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463973"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="94928-103">GetMetaConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="94928-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="94928-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="94928-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="94928-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94928-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="94928-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94928-106">Parameters</span></span>

<span data-ttu-id="94928-107">**MetaConfiguration** \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="94928-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="94928-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="94928-108">Return value</span></span>

<span data-ttu-id="94928-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="94928-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="94928-110">Notes</span><span class="sxs-lookup"><span data-stu-id="94928-110">Remarks</span></span>

<span data-ttu-id="94928-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="94928-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94928-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="94928-112">Requirements</span></span>

<span data-ttu-id="94928-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="94928-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="94928-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="94928-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="94928-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94928-115">See also</span></span>

[<span data-ttu-id="94928-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="94928-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
