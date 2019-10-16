---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration, méthode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953406"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="a2727-103">GetMetaConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="a2727-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="a2727-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="a2727-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2727-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2727-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="a2727-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2727-106">Parameters</span></span>

<span data-ttu-id="a2727-107">*MetaConfiguration* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="a2727-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2727-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a2727-108">Return value</span></span>

<span data-ttu-id="a2727-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a2727-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2727-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="a2727-110">Remarks</span></span>

<span data-ttu-id="a2727-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="a2727-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2727-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a2727-112">Requirements</span></span>

<span data-ttu-id="a2727-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a2727-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a2727-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a2727-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a2727-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2727-115">See also</span></span>

[<span data-ttu-id="a2727-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a2727-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)