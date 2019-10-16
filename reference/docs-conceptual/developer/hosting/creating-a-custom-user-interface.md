---
title: Création d’une interface utilisateur personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367628"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="f62fd-102">Création d’une interface utilisateur personnalisée</span><span class="sxs-lookup"><span data-stu-id="f62fd-102">Creating a custom user interface</span></span>

<span data-ttu-id="f62fd-103">Windows PowerShell fournit des classes abstraites et des interfaces qui vous permettent de créer une interface utilisateur interactive personnalisée qui héberge le moteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f62fd-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="f62fd-104">Pour créer une interface utilisateur personnalisée, vous devez implémenter la classe [System. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) .</span><span class="sxs-lookup"><span data-stu-id="f62fd-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="f62fd-105">Si vous le souhaitez, vous pouvez également implémenter les classes [System. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)et [System. Management. Automation. Host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) , ainsi que le [ Interfaces System. Management. Automation. Host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) et [System. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) .</span><span class="sxs-lookup"><span data-stu-id="f62fd-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
