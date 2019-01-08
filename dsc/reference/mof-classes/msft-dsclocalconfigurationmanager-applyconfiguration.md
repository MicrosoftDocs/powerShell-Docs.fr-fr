---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047246"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1cee7-103">Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1cee7-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1cee7-104">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="1cee7-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="1cee7-105">S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="1cee7-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="1cee7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cee7-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="1cee7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1cee7-107">Parameters</span></span>

<span data-ttu-id="1cee7-108">*force* \[in\] Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="1cee7-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="1cee7-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1cee7-109">Return value</span></span>

<span data-ttu-id="1cee7-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1cee7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cee7-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="1cee7-111">Remarks</span></span>

<span data-ttu-id="1cee7-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="1cee7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cee7-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1cee7-113">Requirements</span></span>

<span data-ttu-id="1cee7-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1cee7-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1cee7-115">\*\*Espace de noms : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1cee7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1cee7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cee7-116">See also</span></span>

[<span data-ttu-id="1cee7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1cee7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)