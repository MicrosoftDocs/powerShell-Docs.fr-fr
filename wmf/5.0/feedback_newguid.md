---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225587"
---
# <a name="new-guid"></a><span data-ttu-id="20ba6-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="20ba6-102">New-Guid</span></span>
<span data-ttu-id="20ba6-103">Bien souvent, lors de l’écriture de scripts (ou même d’une ressource DSC), vous devez utiliser un identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="20ba6-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="20ba6-104">Les GUID fonctionnent correctement, et il est facile d’appeler la classe Guid du .NET Framework pour en générer un, mais le fait de disposer d’une applet de commande rend cela plus simple à découvrir pour les utilisateurs qui ne se sont pas encore familiarisés avec la classe .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="20ba6-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="20ba6-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="20ba6-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="20ba6-106">Guid</span><span class="sxs-lookup"><span data-stu-id="20ba6-106">Guid</span></span>

----

<span data-ttu-id="20ba6-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="20ba6-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
