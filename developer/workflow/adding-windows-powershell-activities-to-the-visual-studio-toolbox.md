---
title: Ajout d’activités de Windows PowerShell à la boîte à outils Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080473"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio

Avant de créer un PowerShell Workflow à l’aide du Concepteur de flux de travail, vous devez d’abord ajouter les activités de PowerShell à la boîte à outils dans un projet d’application console Visual Studio Workflow. La procédure suivante montre comment ajouter des activités à partir de l’assembly Microsoft.PowerShell.Core.Activities à la boîte à outils Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Ajout d’activités de Windows PowerShell à la boîte à outils

1. Créer un nouveau projet d’application de console du flux de travail dans Visual Studio.

2. Sur le **vue** menu, cliquez sur **boîte à outils**.

3. Ajouter un nouvel onglet dans la boîte à outils en cliquant à l’intérieur de la boîte à outils, en cliquant sur **ajouter un onglet**et nommez le nouvel onglet tels que « Activités PowerShell ».

   Ajout d’un onglet vous permet de regrouper les activités PowerShell distinct à partir d’autres outils dans la boîte à outils.

4. Dans le nouvel onglet de boîte à outils, cliquez sur **choisir des éléments...** . Le **Choose Toolbox Items** boîte de dialogue apparaît.

5. Dans le **Choose Toolbox Items** boîte de dialogue, cliquez sur le **System.Activities** onglet.

6. Cliquez sur **Parcourir**.

7. Accédez au dossier %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e et double-cliquez sur Microsoft.PowerShell.Core.Activities.dll.

8. Cliquez sur **OK**. Les activités définies par l’assembly Microsoft.PowerShell.Core.Activities sont maintenant disponibles dans la boîte à outils.

## <a name="see-also"></a>Voir aussi

[Écriture d’un workflow Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Création d’un flux de travail avec Windows PowerShell activités](./creating-a-workflow-with-windows-powershell-activities.md)