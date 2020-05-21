---
title: Écriture d’un workflow Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 0f8a9938a1685e9abc2f1dbfb18c3b2b9008d9be
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564924"
---
# <a name="writing-a-windows-powershell-workflow"></a>Écriture d'un workflow Windows PowerShell

Vous pouvez créer un flux de travail XAML en ajoutant des activités exposées par les assemblys Windows PowerShell au concepteur de flux de travail dans Visual Studio. Les assemblys Windows PowerShell suivants exposent les activités compatibles avec les workflows.

> [!IMPORTANT]
> Un flux de travail XAML doit être empaqueté en tant que module si vous souhaitez fournir de l’aide pour le Workflow. Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft. PowerShell. Core. Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft. PowerShell. Diagnostics. Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft. PowerShell. Security. Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft. PowerShell. Utility. Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  Les rubriques suivantes décrivent comment créer un flux de travail à l’aide d’activités Windows PowerShell.

- [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Création d’un workflow avec des activités Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)

- [Création d’un workflow avec un script Windows PowerShell](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importation et appel d’un workflow Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Création d’une activité de workflow à partir d’une applet de commande Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)
