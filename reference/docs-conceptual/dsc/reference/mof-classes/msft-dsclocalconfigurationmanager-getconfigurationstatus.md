---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationStatus, méthode
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955016"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="b7e41-103">GetConfigurationStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="b7e41-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="b7e41-104">Obtenez l’historique des états de la configuration.</span><span class="sxs-lookup"><span data-stu-id="b7e41-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7e41-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7e41-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="b7e41-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7e41-106">Parameters</span></span>

<span data-ttu-id="b7e41-107">*All* \[in\] **true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="b7e41-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="b7e41-108">*configurationStatus* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="b7e41-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7e41-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b7e41-109">Return value</span></span>

<span data-ttu-id="b7e41-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b7e41-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7e41-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7e41-111">Remarks</span></span>

<span data-ttu-id="b7e41-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="b7e41-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7e41-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b7e41-113">Requirements</span></span>

<span data-ttu-id="b7e41-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b7e41-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b7e41-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7e41-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b7e41-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7e41-116">See also</span></span>

[<span data-ttu-id="b7e41-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b7e41-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
