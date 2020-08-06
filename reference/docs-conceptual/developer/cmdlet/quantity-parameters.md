---
title: Paramètres Quantity | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7ff6562380bb6336b08879b31d8d9fed47bfb6a7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781815"
---
# <a name="quantity-parameters"></a><span data-ttu-id="ea5bf-102">Paramètres de quantité</span><span class="sxs-lookup"><span data-stu-id="ea5bf-102">Quantity Parameters</span></span>

<span data-ttu-id="ea5bf-103">Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres Quantity.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="ea5bf-104">Paramètre</span><span class="sxs-lookup"><span data-stu-id="ea5bf-104">Parameter</span></span>|<span data-ttu-id="ea5bf-105">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="ea5bf-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="ea5bf-106">**Tout**</span><span class="sxs-lookup"><span data-stu-id="ea5bf-106">**All**</span></span><br><span data-ttu-id="ea5bf-107">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="ea5bf-107">Data type: Boolean</span></span>|<span data-ttu-id="ea5bf-108">Implémentez ce paramètre pour `true` indiquer que toutes les ressources doivent être traitées au lieu d’un sous-ensemble de ressources par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="ea5bf-109">Implémentez ce paramètre afin `false` d’indiquer un sous-ensemble des ressources.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="ea5bf-110">**Allocation**</span><span class="sxs-lookup"><span data-stu-id="ea5bf-110">**Allocation**</span></span><br><span data-ttu-id="ea5bf-111">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="ea5bf-111">Data type: Int32</span></span>|<span data-ttu-id="ea5bf-112">Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre d’éléments à allouer.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="ea5bf-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="ea5bf-113">**BlockCount**</span></span><br><span data-ttu-id="ea5bf-114">Type de données : Int64</span><span class="sxs-lookup"><span data-stu-id="ea5bf-114">Data type: Int64</span></span>|<span data-ttu-id="ea5bf-115">Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre de blocs.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="ea5bf-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="ea5bf-116">**Count**</span></span><br><span data-ttu-id="ea5bf-117">Type de données : Int64</span><span class="sxs-lookup"><span data-stu-id="ea5bf-117">Data type: Int64</span></span>|<span data-ttu-id="ea5bf-118">Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="ea5bf-119">**Portée**</span><span class="sxs-lookup"><span data-stu-id="ea5bf-119">**Scope**</span></span><br><span data-ttu-id="ea5bf-120">Type de données : mot clé</span><span class="sxs-lookup"><span data-stu-id="ea5bf-120">Data type: Keyword</span></span>|<span data-ttu-id="ea5bf-121">Implémentez ce paramètre pour permettre à l’utilisateur de spécifier l’étendue à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ea5bf-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ea5bf-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea5bf-122">See Also</span></span>

[<span data-ttu-id="ea5bf-123">Paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="ea5bf-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="ea5bf-124">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea5bf-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="ea5bf-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ea5bf-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
