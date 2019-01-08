---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047277"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bf901-103">Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bf901-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bf901-104">Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.</span><span class="sxs-lookup"><span data-stu-id="bf901-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf901-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf901-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="bf901-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf901-106">Parameters</span></span>

<span data-ttu-id="bf901-107">*configurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="bf901-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="bf901-108">*InDesiredState* \[out\] En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.</span><span class="sxs-lookup"><span data-stu-id="bf901-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="bf901-109">*ResourcesInDesiredState* \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="bf901-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="bf901-110">*ResourcesNotInDesiredState* \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="bf901-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf901-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bf901-111">Return value</span></span>

<span data-ttu-id="bf901-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bf901-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf901-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="bf901-113">Remarks</span></span>

<span data-ttu-id="bf901-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="bf901-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf901-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf901-115">Requirements</span></span>

<span data-ttu-id="bf901-116">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bf901-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bf901-117">\*\*Espace de noms : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf901-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bf901-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf901-118">See also</span></span>

[<span data-ttu-id="bf901-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bf901-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)