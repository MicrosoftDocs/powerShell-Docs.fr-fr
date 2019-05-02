---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085279"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="d2008-102">Get-ChildItem a un paramètre -Depth</span><span class="sxs-lookup"><span data-stu-id="d2008-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="d2008-103">**Get-ChildItem** a maintenant un paramètre **–Depth** que vous pouvez utiliser avec **– Recurse** pour limiter la récursivité :</span><span class="sxs-lookup"><span data-stu-id="d2008-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="d2008-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="d2008-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="d2008-105">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="d2008-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="d2008-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="d2008-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="d2008-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="d2008-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="d2008-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="d2008-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="d2008-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="d2008-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="d2008-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="d2008-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="d2008-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="d2008-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="d2008-112">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="d2008-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="d2008-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="d2008-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="d2008-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="d2008-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="d2008-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="d2008-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="d2008-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="d2008-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="d2008-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="d2008-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="d2008-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="d2008-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="d2008-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="d2008-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="d2008-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="d2008-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
