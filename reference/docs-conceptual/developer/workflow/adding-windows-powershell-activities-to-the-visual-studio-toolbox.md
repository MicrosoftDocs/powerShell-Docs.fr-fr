---
title: Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359648"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio

Avant de créer un flux de travail PowerShell à l’aide de Concepteur de flux de travail, vous devez d’abord ajouter les activités PowerShell à la boîte à outils dans un projet d’application console de flux de travail Visual Studio. La procédure suivante montre comment ajouter les activités de l’assembly Microsoft. PowerShell. Core. Activities à la boîte à outils Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Ajout d’activités Windows PowerShell à la boîte à outils

1. Créez un projet d’application console de workflow dans Visual Studio.

2. Dans le menu **Affichage** , cliquez sur **Boîte à outils**.

3. Ajoutez un nouvel onglet dans la boîte à outils en cliquant avec le bouton droit dans la boîte à outils, puis en cliquant sur **Ajouter un onglet**, et donnez un nom au nouvel onglet, par exemple « activités PowerShell ».

   L’ajout d’un onglet vous permet de regrouper les activités PowerShell séparées des autres outils de la boîte à outils.

4. Dans l’onglet nouvelle boîte à outils, cliquez sur **choisir les éléments...** . La boîte de dialogue **choisir des éléments de boîte à outils** s’affiche.

5. Dans la boîte de dialogue **choisir des éléments de boîte à outils** , cliquez sur l’onglet **System. Activities** .

6. Cliquez sur **Parcourir**.

7. Accédez au dossier%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e, puis double-cliquez sur Microsoft. PowerShell. Core. Activities. dll.

8. Cliquez sur **OK**. Les activités définies par l’assembly Microsoft. PowerShell. Core. Activities sont désormais disponibles dans la boîte à outils.

## <a name="see-also"></a>Voir aussi

[Écriture d’un workflow Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Création d’un flux de travail avec des activités Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)