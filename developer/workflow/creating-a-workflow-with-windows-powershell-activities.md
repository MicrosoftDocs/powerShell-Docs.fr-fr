---
title: Création d’un flux de travail avec Windows PowerShell activités | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080428"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Création d’un workflow avec des activités Windows PowerShell

Vous pouvez créer un flux de travail Windows PowerShell en sélectionnant des activités à partir de la boîte à outils Visual Studio et en les faisant glisser vers la fenêtre du Concepteur de flux de travail. Pour plus d’informations sur l’ajout d’activités de Windows PowerShell à la boîte à outils Visual Studio, consultez [Ajout d’activités Windows PowerShell pour Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Les procédures suivantes décrivent comment créer un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifié par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joint, puis vérifie à nouveau l’état.

### <a name="setting-up-the-project"></a>Configuration du projet

1. Suivez la procédure de [Ajout d’activités Windows PowerShell pour Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) pour créer un projet de flux de travail et ajouter les activités à partir de la [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) et [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) des assemblys de la boîte à outils.

2. Ajouter System.Management.Automation Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities et Microsoft.PowerShell.Commands.Management concernant le projet en tant que les assemblys de référence.

### <a name="adding-activities-to-the-workflow"></a>Ajout d’activités au flux de travail

1. Ajouter un **séquence** activité au flux de travail.

2. Créer un argument nommé `ComputerName` avec un type d’argument de `String[]`. Cet argument représente les noms des ordinateurs à vérifier et à joindre.

3. Créer un argument nommé `DomainCred` de type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Cet argument représente les informations d’identification de domaine d’un compte de domaine qui est autorisé à joindre un ordinateur au domaine.

4. Créer un argument nommé `MachineCred` de type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Cet argument représente les informations d’identification d’un administrateur sur les ordinateurs à vérifier et à joindre.

5. Ajouter un **ParallelForEach** activité à l’intérieur du **séquence** activité. Entrez `comp` et `ComputerName` dans les zones de texte afin que la boucle effectue une itération dans les éléments de la `ComputerName` tableau.

6. Ajouter un **séquence** activité au corps de la **ParallelForEach** activité. Définir le **DisplayName** propriété de la séquence à `JoinDomain`.

7. Ajouter un **GetWmiObject** activité à la **JoinDomain** séquence.

8. Modifier les propriétés de la **GetWmiObject** activité comme suit.

   |Propriété|Valeur|
   |--------------|-----------|
   |**Class**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Ajouter un **AddComputer** activité à la **JoinDomain** séquence après le **GetWmiObject** activité.

10. Modifier les propriétés de la **AddComputer** activité comme suit.

    |Propriété|Valeur|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Ajouter un **RestartComputer** activité à la **JoinDomain** séquence après le **AddComputer** activité.

12. Modifier les propriétés de la **RestartComputer** activité comme suit.

    |Propriété|Valeur|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Informations d’identification**|MachineCred|
    |**Pour**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. Ajouter un **GetWmiObject** activité à la **JoinDomain** séquence après le **RestartComputer** activité. Modifier ses propriétés pour être le même que le précédent **GetWmiObject** activité.

    Lorsque vous avez terminé les procédures, la fenêtre de conception de flux de travail doit ressembler à ceci.

    ![XAML JoinDomain dans le Concepteur de flux de travail](../media/joindomainworkflow.png)
    ![XAML JoinDomain dans le Concepteur de flux de travail](../media/joindomainworkflow.png "JoinDomainWorkflow")