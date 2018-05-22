---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2ec96-103">Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2ec96-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2ec96-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="2ec96-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="2ec96-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec96-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="2ec96-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ec96-106">Parameters</span></span>
----------

<span data-ttu-id="2ec96-107">*MetaConfiguration* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="2ec96-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ec96-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2ec96-108">Return value</span></span>
------------

<span data-ttu-id="2ec96-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2ec96-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ec96-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="2ec96-110">Remarks</span></span>

<span data-ttu-id="2ec96-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="2ec96-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ec96-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2ec96-112">Requirements</span></span>
------------
><span data-ttu-id="2ec96-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2ec96-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2ec96-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ec96-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2ec96-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ec96-115">See also</span></span>


[<span data-ttu-id="2ec96-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2ec96-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)