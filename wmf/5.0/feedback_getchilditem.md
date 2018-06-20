---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221899"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="29b27-102">Get-ChildItem a un paramètre -Depth</span><span class="sxs-lookup"><span data-stu-id="29b27-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="29b27-103">**Get-ChildItem** a maintenant un paramètre **–Depth** que vous pouvez utiliser avec **– Recurse** pour limiter la récursivité :</span><span class="sxs-lookup"><span data-stu-id="29b27-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="29b27-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="29b27-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="29b27-105">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="29b27-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="29b27-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="29b27-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="29b27-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="29b27-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="29b27-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="29b27-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="29b27-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="29b27-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="29b27-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="29b27-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="29b27-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="29b27-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="29b27-112">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="29b27-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="29b27-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="29b27-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="29b27-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="29b27-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="29b27-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="29b27-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="29b27-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="29b27-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="29b27-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="29b27-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="29b27-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="29b27-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="29b27-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="29b27-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="29b27-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="29b27-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
