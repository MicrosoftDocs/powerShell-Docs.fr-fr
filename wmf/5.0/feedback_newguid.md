---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678138"
---
# <a name="new-guid"></a><span data-ttu-id="41bd9-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="41bd9-102">New-Guid</span></span>
<span data-ttu-id="41bd9-103">Bien souvent, lors de l’écriture de scripts (ou même d’une ressource DSC), vous devez utiliser un identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="41bd9-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="41bd9-104">Les GUID fonctionnent correctement, et il est facile d’appeler la classe Guid du .NET Framework pour en générer un, mais le fait de disposer d’une applet de commande rend cela plus simple à découvrir pour les utilisateurs qui ne se sont pas encore familiarisés avec la classe .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="41bd9-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="41bd9-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="41bd9-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="41bd9-106">Guid</span><span class="sxs-lookup"><span data-stu-id="41bd9-106">Guid</span></span>

----

<span data-ttu-id="41bd9-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="41bd9-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
