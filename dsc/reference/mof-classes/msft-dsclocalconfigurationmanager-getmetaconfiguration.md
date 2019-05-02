---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078518"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6cd0e-103">Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6cd0e-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6cd0e-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="6cd0e-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="6cd0e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cd0e-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="6cd0e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6cd0e-106">Parameters</span></span>

<span data-ttu-id="6cd0e-107">*MetaConfiguration* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="6cd0e-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="6cd0e-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6cd0e-108">Return value</span></span>

<span data-ttu-id="6cd0e-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6cd0e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cd0e-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6cd0e-110">Remarks</span></span>

<span data-ttu-id="6cd0e-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="6cd0e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6cd0e-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6cd0e-112">Requirements</span></span>

<span data-ttu-id="6cd0e-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6cd0e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6cd0e-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6cd0e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd0e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cd0e-115">See also</span></span>

[<span data-ttu-id="6cd0e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6cd0e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)