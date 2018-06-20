---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217989"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="c1284-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="c1284-102">New-TemporaryFile</span></span>
<span data-ttu-id="c1284-103">Parfois, dans vos scripts, vous devez créer un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="c1284-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="c1284-104">Avec l’applet de commande **New-TemporaryFile**, cette opération est très simple :</span><span class="sxs-lookup"><span data-stu-id="c1284-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="c1284-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="c1284-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="c1284-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="c1284-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="c1284-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="c1284-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
