---
title: Création d’une interface utilisateur personnalisée | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebbaba4231b54d42cdcdef07a3ff665bd207d696
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779775"
---
# <a name="creating-a-custom-user-interface"></a>Création d’une interface utilisateur personnalisée

Windows PowerShell fournit des classes abstraites et des interfaces qui vous permettent de créer une interface utilisateur interactive personnalisée qui héberge le moteur Windows PowerShell. Pour créer une interface utilisateur personnalisée, vous devez implémenter la classe [System. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) . Si vous le souhaitez, vous pouvez également implémenter les classes [System. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)et [System. Management](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) . Automation. Host. Pshostuserinterface, ainsi que les interfaces System. Management. Automation. Host. [Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) et [System. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) .
