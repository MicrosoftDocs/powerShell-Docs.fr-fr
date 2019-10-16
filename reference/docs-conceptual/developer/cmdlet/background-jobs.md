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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363558"
---
# <a name="background-jobs"></a><span data-ttu-id="d46b5-102">Travaux en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="d46b5-102">Background Jobs</span></span>

<span data-ttu-id="d46b5-103">Les applets de commande peuvent exécuter leur action en interne ou en tant que*tâche en arrière-plan*Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46b5-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="d46b5-104">Lorsqu’une applet de commande s’exécute en tant que tâche en arrière-plan, le travail est effectué de façon asynchrone dans son propre thread distinct du thread de pipeline que l’applet de commande utilise.</span><span class="sxs-lookup"><span data-stu-id="d46b5-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="d46b5-105">Du point de vue de l’utilisateur, lorsqu’une applet de commande s’exécute en tant que tâche en arrière-plan, l’invite de commandes est immédiatement retournée même si la tâche prend beaucoup de temps et que l’utilisateur peut continuer sans interruption pendant l’exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d46b5-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="d46b5-106">Travaux en arrière-plan, travaux enfants et référentiel des tâches</span><span class="sxs-lookup"><span data-stu-id="d46b5-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="d46b5-107">L’objet de traitement retourné par les applets de commande qui prennent en charge les travaux en arrière-plan définit le travail.</span><span class="sxs-lookup"><span data-stu-id="d46b5-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="d46b5-108">(L’applet de commande [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) retourne également un objet de traitement.) Nom du travail, un identificateur utilisé pour spécifier le travail, les informations d’État et les travaux enfants sont inclus dans cette définition.</span><span class="sxs-lookup"><span data-stu-id="d46b5-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="d46b5-109">Le travail n’effectue aucune tâche.</span><span class="sxs-lookup"><span data-stu-id="d46b5-109">The job does not perform any of the work.</span></span> <span data-ttu-id="d46b5-110">Chaque travail en arrière-plan a au moins un travail enfant, car le travail enfant effectue le travail réel.</span><span class="sxs-lookup"><span data-stu-id="d46b5-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="d46b5-111">Lorsque vous exécutez une applet de commande afin que le travail soit effectué en arrière-plan, l’applet de commande doit ajouter le travail et les tâches enfants à un référentiel commun, appelé *référentiel de travaux*.</span><span class="sxs-lookup"><span data-stu-id="d46b5-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="d46b5-112">Pour plus d’informations sur la gestion des tâches en arrière-plan sur la ligne de commande, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d46b5-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="d46b5-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="d46b5-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="d46b5-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="d46b5-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="d46b5-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="d46b5-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="d46b5-116">Écriture d’une applet de commande qui s’exécute en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="d46b5-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="d46b5-117">Pour écrire une applet de commande qui peut être exécutée en tant que tâche en arrière-plan, vous devez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d46b5-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="d46b5-118">Définissez un paramètre de commutateur `asJob` pour permettre à l’utilisateur de décider s’il faut exécuter l’applet de commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d46b5-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="d46b5-119">Créez un objet qui dérive de la classe [System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) .</span><span class="sxs-lookup"><span data-stu-id="d46b5-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="d46b5-120">Cet objet peut être un objet de traitement personnalisé ou un objet de traitement fourni par Windows PowerShell, tel qu’un objet [System. Management. Automation. PSEventJob](/dotnet/api/System.Management.Automation.PSEventJob) .</span><span class="sxs-lookup"><span data-stu-id="d46b5-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="d46b5-121">Dans une méthode de traitement des enregistrements, ajoutez une instruction `if` qui détecte si l’applet de commande doit s’exécuter en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d46b5-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="d46b5-122">Pour les objets de travail personnalisés, implémentez la classe Job.</span><span class="sxs-lookup"><span data-stu-id="d46b5-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="d46b5-123">Retourne les objets appropriés, selon que l’applet de commande est exécutée en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d46b5-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="d46b5-124">Pour obtenir un exemple de code, consultez [Comment prendre en charge les travaux](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="d46b5-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="d46b5-125">API relatives aux tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="d46b5-125">Background Job-Related APIs</span></span>

<span data-ttu-id="d46b5-126">Les API suivantes sont fournies par Windows PowerShell pour gérer les travaux en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d46b5-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="d46b5-127">[System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) dérive des objets de tâche personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d46b5-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="d46b5-128">Il s’agit d’une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="d46b5-128">This is an abstract class.</span></span>

<span data-ttu-id="d46b5-129">[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gère et fournit des informations sur les travaux en arrière-plan actifs actuels.</span><span class="sxs-lookup"><span data-stu-id="d46b5-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="d46b5-130">[System. Management. Automation. Jobstate](/dotnet/api/System.Management.Automation.JobState) définit l’état de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d46b5-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="d46b5-131">Les États incluent Started, Running et Stopped.</span><span class="sxs-lookup"><span data-stu-id="d46b5-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="d46b5-132">[System. Management. Automation. JobStateInfo](/dotnet/api/System.Management.Automation.JobStateInfo) fournit des informations sur l’état d’une tâche en arrière-plan et, si le dernier changement d’État a été provoqué par une erreur, la raison pour laquelle le travail est passé à son état actuel.</span><span class="sxs-lookup"><span data-stu-id="d46b5-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="d46b5-133">[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fournit les arguments pour un événement qui est déclenché lorsqu’un travail en arrière-plan change d’État.</span><span class="sxs-lookup"><span data-stu-id="d46b5-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="d46b5-134">Applets de commande Windows PowerShell Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="d46b5-135">Les applets de commande suivantes sont fournies par Windows PowerShell pour gérer les travaux en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d46b5-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="d46b5-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="d46b5-137">Obtient les tâches en arrière-plan Windows PowerShell qui s'exécutent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d46b5-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="d46b5-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="d46b5-139">Obtient les résultats des tâches Windows PowerShell en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d46b5-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="d46b5-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="d46b5-141">Supprime une tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46b5-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d46b5-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="d46b5-143">Démarre une tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46b5-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d46b5-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="d46b5-145">Arrête une tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46b5-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d46b5-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d46b5-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="d46b5-147">Supprime l'invite de commandes jusqu'à ce qu'une ou toutes les tâches en arrière-plan Windows PowerShell en cours d'exécution dans la session soient terminées.</span><span class="sxs-lookup"><span data-stu-id="d46b5-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="d46b5-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d46b5-148">See Also</span></span>

[<span data-ttu-id="d46b5-149">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d46b5-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
