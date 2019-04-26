---
title: Écriture d’un flux de travail Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080320"
---
# <a name="writing-a-windows-powershell-workflow"></a>Écriture d'un workflow Windows PowerShell

Vous pouvez créer un flux de travail XAML en ajoutant des activités exposées par les assemblys Windows PowerShell pour le Concepteur de flux de travail dans Visual Studio. Les assemblys de Windows PowerShell suivantes exposent des activités de flux de travail.

> [!IMPORTANT]
> Si vous souhaitez fournir une aide pour le flux de travail, un workflow XAML doit être empaqueté en tant que module. Pour plus d’informations sur les modules, consultez [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).

- [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft.Powershell.Core.Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft.Powershell.Diagnostics.Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft.Powershell.Security.Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft.Powershell.Utility.Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  Les rubriques suivantes décrivent comment créer un flux de travail à l’aide des activités de Windows PowerShell.

- [Ajout d’activités de Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Création d’un flux de travail avec Windows PowerShell activités](./creating-a-workflow-with-windows-powershell-activities.md)

- [Création d’un Workflow à l’aide d’un Script PowerShell de Windows](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [L’importation et l’appel d’un flux de travail Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Création d’une activité de flux de travail à partir d’une applet de commande Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)