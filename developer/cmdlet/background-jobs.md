---
title: Tâches en arrière-plan | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857165"
---
# <a name="background-jobs"></a>Travaux en arrière-plan

Applets de commande peut exécuter leur action en interne ou un PowerShell Windows*tâche en arrière-plan*. Quand une applet de commande s’exécute en tant que tâche en arrière-plan, le travail est effectué de façon asynchrone dans son propre thread séparé à partir du thread de pipeline à l’aide de l’applet de commande. Du point de vue de l’utilisateur, quand une applet de commande s’exécute en tant que tâche en arrière-plan, l’invite de commande retourne immédiatement même si le travail prend un certain temps, et l’utilisateur peut continuer sans interruption pendant l’exécution de la tâche.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Tâches en arrière-plan, les travaux d’enfant et le référentiel de tâches

L’objet de travail qui est retourné par les applets de commande qui prennent en charge les tâches en arrière-plan définit la tâche. (Le [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) applet de commande renvoie également un objet de traitement.) Le nom de la tâche, un identificateur qui est utilisé pour spécifier le travail, les informations d’état et les tâches enfant sont inclus dans cette définition. La tâche n’effectue aucun du travail. Chaque tâche en arrière-plan a au moins une tâche enfant, car la tâche enfant effectue le travail réel. Lorsque vous exécutez une applet de commande afin que le travail est effectué en tant que tâche en arrière-plan, l’applet de commande doit ajouter le travail et les tâches enfant à un référentiel commun, appelé le *référentiel de tâches*.
L’objet de travail qui est retourné par les applets de commande qui prennent en charge les tâches en arrière-plan définit la tâche. (Le [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) applet de commande renvoie également un objet de traitement.) Le nom de la tâche, un identificateur qui est utilisé pour spécifier le travail, les informations d’état et les tâches enfant sont inclus dans cette définition. La tâche n’effectue aucun du travail. Chaque tâche en arrière-plan a au moins une tâche enfant, car la tâche enfant effectue le travail réel. Lorsque vous exécutez une applet de commande afin que le travail est effectué en tant que tâche en arrière-plan, l’applet de commande doit ajouter le travail et les tâches enfant à un référentiel commun, appelé le *référentiel de tâches*.

Pour plus d’informations sur la gestion des tâches en arrière-plan sur la ligne de commande, consultez les rubriques suivantes :

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Écriture d’une applet de commande qui s’exécute en tant que tâche en arrière-plan

Pour écrire une applet de commande qui peut être exécuté en tant que tâche en arrière-plan, vous devez effectuer les tâches suivantes :

- Définir un `asJob` paramètre de commutateur afin que l’utilisateur peut décider s’il faut exécuter l’applet de commande en tant que tâche en arrière-plan.

- Créer un objet qui dérive de la [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe. Cet objet peut être un objet de tâche personnalisé ou un objet de travail fournis par Windows PowerShell, par exemple un [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objet.

- Dans une méthode de traitement enregistrement, ajoutez un `if` instruction qui détecte si l’applet de commande doit s’exécuter en tant que tâche en arrière-plan.

- Pour les objets de tâche personnalisé, implémentez la classe de tâche.

- Retourner les objets appropriés, selon que l’applet de commande est exécutée comme une tâche en arrière-plan.

Pour obtenir un exemple de code, consultez [comment les tâches de prise en charge](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API liées au travail en arrière-plan

Les API suivantes sont fournies par PowerShell de Windows pour gérer les tâches en arrière-plan.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) dérive des objets de tâche personnalisé. Il s’agit d’une classe abstraite.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gère et fournit des informations sur les tâches d’arrière-plan active actuelle.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) définit l’état de la tâche en arrière-plan. Les États incluent démarré et arrêté en cours d’exécution.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fournit des informations sur l’état d’une tâche en arrière-plan et, si l’état de la dernière modification a été provoqué par une erreur, la raison pour laquelle le travail est passé à son état actuel.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fournit les arguments pour un événement qui est déclenché lorsqu’une tâche en arrière-plan change d’état.

## <a name="windows-powershell-job-cmdlets"></a>Applets de commande PowerShell Windows

Les applets de commande suivantes sont fournies par PowerShell de Windows pour gérer les tâches en arrière-plan.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Obtient les tâches en arrière-plan Windows PowerShell qui s'exécutent dans la session active.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Obtient les résultats des tâches Windows PowerShell en arrière-plan dans la session active.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Supprime une tâche en arrière-plan Windows PowerShell.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Démarre une tâche en arrière-plan Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Arrête une tâche en arrière-plan Windows PowerShell.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Supprime l'invite de commandes jusqu'à ce qu'une ou toutes les tâches en arrière-plan Windows PowerShell en cours d'exécution dans la session soient terminées.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
