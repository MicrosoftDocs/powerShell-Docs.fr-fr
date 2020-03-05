---
title: Création d’un flux de travail avec des activités Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 7d399786b9b43ee302493359d9702981045212e9
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78277460"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Création d’un workflow avec des activités Windows PowerShell

Vous pouvez créer un flux de travail Windows PowerShell en sélectionnant activités dans la boîte à outils Visual Studio et en les faisant glisser vers la fenêtre de Concepteur de flux de travail. Pour plus d’informations sur l’ajout d’activités Windows PowerShell à la boîte à outils de Visual Studio, consultez [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Les procédures suivantes décrivent comment créer un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifiés par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joints, puis vérifie à nouveau l’État.

### <a name="setting-up-the-project"></a>Configuration du projet

1. Suivez la procédure décrite dans [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) pour créer un projet de workflow et ajouter les activités des assemblys [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) et [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) à la boîte à outils.

2. Ajoutez System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities et Microsoft. PowerShell. Commands. Management au projet en tant qu’assemblys de référence.

### <a name="adding-activities-to-the-workflow"></a>Ajout d’activités au flux de travail

1. Ajoutez une activité **Sequence** au workflow.

2. Créez un argument nommé `ComputerName` avec un type d’argument `String[]`. Cet argument représente les noms des ordinateurs à vérifier et joindre.

3. Créez un argument nommé `DomainCred` de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Cet argument représente les informations d’identification de domaine d’un compte de domaine qui est autorisé à joindre un ordinateur au domaine.

4. Créez un argument nommé `MachineCred` de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Cet argument représente les informations d’identification d’un administrateur sur les ordinateurs à vérifier et à joindre.

5. Ajoutez une activité **ParallelForEach** dans l’activité **Sequence** . Entrez `comp` et `ComputerName` dans les zones de texte afin que la boucle itère au sein des éléments du tableau `ComputerName`.

6. Ajoutez une activité **Sequence** au corps de l’activité **ParallelForEach** . Définissez la propriété **DisplayName** de la séquence sur `JoinDomain`.

7. Ajoutez une activité **GetWmiObject** à la séquence **JoinDomain** .

8. Modifiez les propriétés de l’activité **GetWmiObject** comme suit.

   |Propriété|Valeur|
   |--------------|-----------|
   |**Classe**|« Win32_ComputerSystem »|
   |**PSComputerName**|conformes|
   |**PSCredential**|MachineCred|

9. Ajoutez une activité **AddComputer** à la séquence **JoinDomain** après l’activité **GetWmiObject** .

10. Modifiez les propriétés de l’activité **AddComputer** comme suit.

    |Propriété|Valeur|
    |--------------|-----------|
    |**ComputerName**|conformes|
    |**DomainCredential**|DomainCred|

11. Ajoutez une activité **RestartComputer** à la séquence **JoinDomain** après l’activité **AddComputer** .

12. Modifiez les propriétés de l’activité **RestartComputer** comme suit.

    |Propriété|Valeur|
    |--------------|-----------|
    |**ComputerName**|conformes|
    |**Informations d'identification**|MachineCred|
    |**Pour**|Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell|
    |**Force**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. Ajoutez une activité **GetWmiObject** à la séquence **JoinDomain** après l’activité **RestartComputer** . Modifiez ses propriétés afin qu’elles soient identiques à celles de l’activité **GetWmiObject** précédente.

    Lorsque vous avez terminé les procédures, la fenêtre de conception de Workflow doit ressembler à ceci.

    ![XAML JoinDomain dans le concepteur de flux de travail](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
    ![XAML JoinDomain dans le concepteur de workflow](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")