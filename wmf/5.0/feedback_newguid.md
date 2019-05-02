---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085320"
---
# <a name="new-guid"></a><span data-ttu-id="aad0a-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="aad0a-102">New-Guid</span></span>
<span data-ttu-id="aad0a-103">Bien souvent, lors de l’écriture de scripts (ou même d’une ressource DSC), vous devez utiliser un identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="aad0a-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="aad0a-104">Les GUID fonctionnent correctement, et il est facile d’appeler la classe Guid du .NET Framework pour en générer un, mais le fait de disposer d’une applet de commande rend cela plus simple à découvrir pour les utilisateurs qui ne se sont pas encore familiarisés avec la classe .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="aad0a-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="aad0a-105">PS C :\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="aad0a-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="aad0a-106">Guid</span><span class="sxs-lookup"><span data-stu-id="aad0a-106">Guid</span></span>

----

<span data-ttu-id="aad0a-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="aad0a-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
