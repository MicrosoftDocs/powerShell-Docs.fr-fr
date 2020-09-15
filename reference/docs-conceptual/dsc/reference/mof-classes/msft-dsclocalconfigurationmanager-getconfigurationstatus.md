---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: GetConfigurationStatus, méthode
ms.openlocfilehash: c2c478151428052d656832fb4079f12d666a910d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464046"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="c3c14-103">GetConfigurationStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="c3c14-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="c3c14-104">Obtenez l’historique des états de la configuration.</span><span class="sxs-lookup"><span data-stu-id="c3c14-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3c14-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3c14-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="c3c14-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3c14-106">Parameters</span></span>

<span data-ttu-id="c3c14-107">**All** \[in\] **true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="c3c14-107">**All** \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="c3c14-108">**configurationStatus** \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="c3c14-108">**configurationStatus** \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3c14-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c3c14-109">Return value</span></span>

<span data-ttu-id="c3c14-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c3c14-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3c14-111">Notes</span><span class="sxs-lookup"><span data-stu-id="c3c14-111">Remarks</span></span>

<span data-ttu-id="c3c14-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="c3c14-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3c14-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3c14-113">Requirements</span></span>

<span data-ttu-id="c3c14-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c3c14-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c3c14-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c3c14-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c3c14-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3c14-116">See also</span></span>

[<span data-ttu-id="c3c14-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c3c14-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
