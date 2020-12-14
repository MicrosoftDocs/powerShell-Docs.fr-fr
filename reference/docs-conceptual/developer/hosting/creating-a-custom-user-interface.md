---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une interface utilisateur personnalisée
description: Création d’une interface utilisateur personnalisée
ms.openlocfilehash: 411165f868cd524c0cef0ba9cce3188c60a7dbdf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645399"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="cfbb6-103">Création d’une interface utilisateur personnalisée</span><span class="sxs-lookup"><span data-stu-id="cfbb6-103">Creating a custom user interface</span></span>

<span data-ttu-id="cfbb6-104">Windows PowerShell fournit des classes abstraites et des interfaces qui vous permettent de créer une interface utilisateur interactive personnalisée qui héberge le moteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cfbb6-104">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="cfbb6-105">Pour créer une interface utilisateur personnalisée, vous devez implémenter la classe [System. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) .</span><span class="sxs-lookup"><span data-stu-id="cfbb6-105">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="cfbb6-106">Si vous le souhaitez, vous pouvez également implémenter les classes [System. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)et [System. Management](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) . Automation. Host. Pshostuserinterface, ainsi que les interfaces System. Management. Automation. Host. [Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) et [System. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) .</span><span class="sxs-lookup"><span data-stu-id="cfbb6-106">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
