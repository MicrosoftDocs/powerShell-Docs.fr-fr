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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083040"
---
# <a name="creating-a-custom-user-interface"></a>Création d’une interface utilisateur personnalisée

Windows PowerShell fournit des classes abstraites et des interfaces qui vous permettent de créer une interface interactive personnalisée qui héberge le moteur Windows PowerShell. Pour créer une interface utilisateur personnalisée, vous devez implémenter le [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) classe. Si vous le souhaitez, vous pouvez également implémenter le [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)et [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) les classes et les [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) et [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.
