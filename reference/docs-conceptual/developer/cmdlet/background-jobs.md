---
title: Travaux en arrière-plan | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363558"
---
# <a name="background-jobs"></a>Travaux en arrière-plan

Les applets de commande peuvent exécuter leur action en interne ou en tant que*tâche en arrière-plan*Windows PowerShell. Lorsqu’une applet de commande s’exécute en tant que tâche en arrière-plan, le travail est effectué de façon asynchrone dans son propre thread distinct du thread de pipeline que l’applet de commande utilise. Du point de vue de l’utilisateur, lorsqu’une applet de commande s’exécute en tant que tâche en arrière-plan, l’invite de commandes est immédiatement retournée même si la tâche prend beaucoup de temps et que l’utilisateur peut continuer sans interruption pendant l’exécution de la tâche.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Travaux en arrière-plan, travaux enfants et référentiel des tâches

L’objet de traitement retourné par les applets de commande qui prennent en charge les travaux en arrière-plan définit le travail. (L’applet de commande [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) retourne également un objet de traitement.) Nom du travail, un identificateur utilisé pour spécifier le travail, les informations d’État et les travaux enfants sont inclus dans cette définition. Le travail n’effectue aucune tâche. Chaque travail en arrière-plan a au moins un travail enfant, car le travail enfant effectue le travail réel. Lorsque vous exécutez une applet de commande afin que le travail soit effectué en arrière-plan, l’applet de commande doit ajouter le travail et les tâches enfants à un référentiel commun, appelé *référentiel de travaux*.

Pour plus d’informations sur la gestion des tâches en arrière-plan sur la ligne de commande, consultez les rubriques suivantes :

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Écriture d’une applet de commande qui s’exécute en tant que tâche en arrière-plan

Pour écrire une applet de commande qui peut être exécutée en tant que tâche en arrière-plan, vous devez effectuer les tâches suivantes :

- Définissez un paramètre de commutateur `asJob` pour permettre à l’utilisateur de décider s’il faut exécuter l’applet de commande en tant que tâche en arrière-plan.

- Créez un objet qui dérive de la classe [System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) . Cet objet peut être un objet de traitement personnalisé ou un objet de traitement fourni par Windows PowerShell, tel qu’un objet [System. Management. Automation. PSEventJob](/dotnet/api/System.Management.Automation.PSEventJob) .

- Dans une méthode de traitement des enregistrements, ajoutez une instruction `if` qui détecte si l’applet de commande doit s’exécuter en tant que tâche en arrière-plan.

- Pour les objets de travail personnalisés, implémentez la classe Job.

- Retourne les objets appropriés, selon que l’applet de commande est exécutée en tant que tâche en arrière-plan.

Pour obtenir un exemple de code, consultez [Comment prendre en charge les travaux](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API relatives aux tâches en arrière-plan

Les API suivantes sont fournies par Windows PowerShell pour gérer les travaux en arrière-plan.

[System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) dérive des objets de tâche personnalisés. Il s’agit d’une classe abstraite.

[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gère et fournit des informations sur les travaux en arrière-plan actifs actuels.

[System. Management. Automation. Jobstate](/dotnet/api/System.Management.Automation.JobState) définit l’état de la tâche en arrière-plan. Les États incluent Started, Running et Stopped.

[System. Management. Automation. JobStateInfo](/dotnet/api/System.Management.Automation.JobStateInfo) fournit des informations sur l’état d’une tâche en arrière-plan et, si le dernier changement d’État a été provoqué par une erreur, la raison pour laquelle le travail est passé à son état actuel.

[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fournit les arguments pour un événement qui est déclenché lorsqu’un travail en arrière-plan change d’État.

## <a name="windows-powershell-job-cmdlets"></a>Applets de commande Windows PowerShell Job

Les applets de commande suivantes sont fournies par Windows PowerShell pour gérer les travaux en arrière-plan.

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
