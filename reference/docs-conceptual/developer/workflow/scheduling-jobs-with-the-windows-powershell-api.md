---
title: Planification de travaux à l’aide de l’API Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64718f8e-de60-4fb7-894d-2975b5257ff6
caps.latest.revision: 4
ms.openlocfilehash: bdced961d91088dd75be347b7b74b22467c8c9be
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366018"
---
# <a name="scheduling-jobs-with-the-powershell-api"></a><span data-ttu-id="5579c-102">Planification de travaux avec l’API PowerShell</span><span class="sxs-lookup"><span data-stu-id="5579c-102">Scheduling jobs with the PowerShell API</span></span>

<span data-ttu-id="5579c-103">Vous pouvez utiliser les objets exposés par l’espace de noms **Microsoft. PowerShell. ScheduledJob** pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5579c-103">You can use the objects exposed by the **Microsoft.PowerShell.ScheduledJob** namespace to do the following:</span></span>

- <span data-ttu-id="5579c-104">Créer une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="5579c-104">Create a scheduled job.</span></span>
- <span data-ttu-id="5579c-105">Définir le moment d’exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="5579c-105">Define when the job runs.</span></span>
- <span data-ttu-id="5579c-106">Obtenir des résultats sur la tâche terminée.</span><span class="sxs-lookup"><span data-stu-id="5579c-106">Get results about the completed job.</span></span>

## <a name="triggering-the-job"></a><span data-ttu-id="5579c-107">Déclenchement du travail</span><span class="sxs-lookup"><span data-stu-id="5579c-107">Triggering the job</span></span>

<span data-ttu-id="5579c-108">La première étape de la création d’une tâche planifiée consiste à spécifier le moment où le travail doit s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5579c-108">The first step in creating a scheduled job is specifying when the job should run.</span></span> <span data-ttu-id="5579c-109">Pour ce faire, créez et configurez un objet **Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="5579c-109">Do this by creating and configuring a **Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger** object.</span></span> <span data-ttu-id="5579c-110">Le code suivant crée un déclencheur qui planifie une tâche pour qu’elle s’exécute une seule fois 20 secondes à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="5579c-110">The following code creates a trigger that schedules a job to run a single time 20 seconds in the future.</span></span>

```csharp
ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20), // Create trigger to start job in 20 seconds.
                    TimeSpan.Zero,               // No random delay
                    null,                        // No repetition interval time
                    null,                        // No repetition interval duration
                    1,                           // Trigger Id
                    true);                       // Create trigger enabled

```

## <a name="defining-the-job"></a><span data-ttu-id="5579c-111">Définition du travail</span><span class="sxs-lookup"><span data-stu-id="5579c-111">Defining the job</span></span>

<span data-ttu-id="5579c-112">Vous définissez un travail PowerShell en créant un dictionnaire de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5579c-112">You define a PowerShell job by creating a parameter dictionary.</span></span> <span data-ttu-id="5579c-113">Les paramètres suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="5579c-113">The following parameters are supported:</span></span>

|<span data-ttu-id="5579c-114">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="5579c-114">Parameter Name</span></span>|<span data-ttu-id="5579c-115">Description</span><span class="sxs-lookup"><span data-stu-id="5579c-115">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="5579c-116">**Nomme**</span><span class="sxs-lookup"><span data-stu-id="5579c-116">**Name**</span></span>|<span data-ttu-id="5579c-117">Nom du travail.</span><span class="sxs-lookup"><span data-stu-id="5579c-117">The name of the job.</span></span>|
|<span data-ttu-id="5579c-118">**ScriptBock**</span><span class="sxs-lookup"><span data-stu-id="5579c-118">**ScriptBock**</span></span>|<span data-ttu-id="5579c-119">Bloc de script PowerShell qui spécifie ce que fait le travail.</span><span class="sxs-lookup"><span data-stu-id="5579c-119">A PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="5579c-120">**Cheminfichier**</span><span class="sxs-lookup"><span data-stu-id="5579c-120">**FilePath**</span></span>|<span data-ttu-id="5579c-121">Chemin d’accès à un fichier qui contient un bloc de script PowerShell pour spécifier le rôle du travail.</span><span class="sxs-lookup"><span data-stu-id="5579c-121">Path to a file that contains a PowerShell script block to specify what the job does.</span></span>|
|<span data-ttu-id="5579c-122">**InitializationScript**</span><span class="sxs-lookup"><span data-stu-id="5579c-122">**InitializationScript**</span></span>|<span data-ttu-id="5579c-123">Un bloc de script PowerShell qui initialise le travail.</span><span class="sxs-lookup"><span data-stu-id="5579c-123">A PowerShell script block that initializes the job.</span></span>|
|<span data-ttu-id="5579c-124">**ArgumentList**</span><span class="sxs-lookup"><span data-stu-id="5579c-124">**ArgumentList**</span></span>|<span data-ttu-id="5579c-125">Tableau d’objets qui spécifient les arguments que prend le travail.</span><span class="sxs-lookup"><span data-stu-id="5579c-125">An array of objects that specify arguments that the job takes.</span></span>|
|<span data-ttu-id="5579c-126">**RunAs32**</span><span class="sxs-lookup"><span data-stu-id="5579c-126">**RunAs32**</span></span>|<span data-ttu-id="5579c-127">Valeur booléenne qui spécifie si le travail doit être exécuté dans un processus 32 bits.</span><span class="sxs-lookup"><span data-stu-id="5579c-127">A boolean value that specifies whether to run the job in a 32-bit process.</span></span>|

<span data-ttu-id="5579c-128">Le code suivant crée un objet de dictionnaire de paramètres et définit les paramètres **Name** et **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="5579c-128">The following code creates a parameter dictionary object and sets the **Name** and **ScriptBlock** parameters.</span></span>

```csharp
string schedJobDefName = "MySampleSchedJob";
  Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
  jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

  ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
  jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                    // is required.

```

## <a name="creating-the-invocation-and-job-definition-objects"></a><span data-ttu-id="5579c-129">Création des objets d’appel et de définition de tâche</span><span class="sxs-lookup"><span data-stu-id="5579c-129">Creating the invocation and job definition objects</span></span>

<span data-ttu-id="5579c-130">Vous créez ensuite des objets `ScheduledJobInvocationInfo` et `ScheduledJobDefinition` pour exécuter le travail, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5579c-130">You then create `ScheduledJobInvocationInfo` and `ScheduledJobDefinition` objects to run the job as shown in the following example:</span></span>

```csharp
ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
    jobDefParameters);

    schedJobDefinition = new ScheduledJobDefinition(
    jobInvocationInfo,                          // Defines the PowerShell job to run.
    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
    null,                                       // No custom options. We accept default.
    null);                                      // No credentials. PowerShell job is run
                                                // in default Task Scheduler process, account.

```

## <a name="registering-the-job-with-the-task-scheduler"></a><span data-ttu-id="5579c-131">Inscription du travail à l’aide du planificateur de tâches</span><span class="sxs-lookup"><span data-stu-id="5579c-131">Registering the job with the task scheduler</span></span>

<span data-ttu-id="5579c-132">Le code suivant inscrit le travail avec le [Planificateur de tâches Windows](https://go.microsoft.com/fwlink/?LinkId=251817).</span><span class="sxs-lookup"><span data-stu-id="5579c-132">The following code registers the job with the [Windows Task Scheduler](https://go.microsoft.com/fwlink/?LinkId=251817).</span></span>

```csharp
schedJobDefinition.Register();
    registrationSucceeded = true;
    Console.WriteLine("Scheduled job is registered. Waiting 30 seconds for it to run.");

```

## <a name="complete-code-example"></a><span data-ttu-id="5579c-133">Exemple de code complet</span><span class="sxs-lookup"><span data-stu-id="5579c-133">Complete code Example</span></span>

<span data-ttu-id="5579c-134">Voici l’exemple de code complet à partir duquel les extraits de code précédents ont été pris.</span><span class="sxs-lookup"><span data-stu-id="5579c-134">The following is the complete code example from which the previous snippets were taken.</span></span>

```csharp
using System;
using System.Threading;
using System.Collections.Generic;
using System.Management.Automation;             // PowerShell namespace.
using Microsoft.PowerShell.ScheduledJob;        // PowerShell ScheduledJob namespace.

namespace Microsoft.Samples.PowerShell.ScheduledJob
{
    /// <summary>
    /// This class contains the Main entry point for the application.
    /// </summary>
    public class ScheduledJobSample
    {
        /// <summary>
        /// This sample shows how to use the PowerShell ScheduledJob API to create
        /// a simple PowerShell scheduled job, register it with a trigger object
        /// that defines when the job will run and retrieve job run results from
        /// the job file store.
        /// </summary>
        /// <param name="args"></param>
        public static void Main(string[] args)
        {
            // ScheduledJobDefinition contains all elements of a PowerShell scheduled
            // job including the PowerShell job script or script file path, scheduling
            // triggers, and scheduling options.
            ScheduledJobDefinition schedJobDefinition = null;
            bool registrationSucceeded = false;

            try
            {
                // First create a scheduled job trigger object.  This object will
                // define when the PowerShell job is scheduled to run.  For this
                // example we will create a trigger to run the job just one time
                // 20 seconds after the trigger object is created.
                // Note: If you are stepping through this code in a debugger you
                // may want to increase the 20 seconds value so that the trigger time
                // remains in the future once you register the scheduled job.
                ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20),      // Create trigger to start job in 20 seconds.
                    TimeSpan.Zero,                    // No random delay
                    null,                             // No repetition interval time
                    null,                             // No repetition interval duration
                    1,                                // Trigger Id
                    true);                            // Create trigger enabled

                // Create a parameter dictionary that defines the PowerShell job.
                // For this example we will create a simple script that runs for
                // 5 seconds generating output.
                // Here are the parameters supported to define the PowerShell job.
                // Name                 - Job name string.
                // ScriptBlock          - PowerShell ScriptBlock type.
                // FilePath             - PowerShell script file path string.
                // InitializationScript - PowerShell Scriptblock type.
                // ArgumentList         - object[] type.
                // RunAs32              - Switch (boolean type).
                string schedJobDefName = "MySampleSchedJob";
                Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
                jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

                ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
                jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath is required.

                // Now create a JobInvocation object that contains all information about the PowerShell job to run.
                ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
                    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
                    jobDefParameters);

                // Finally create the scheduled job definition object that pulls all
                // of this information together.
                schedJobDefinition = new ScheduledJobDefinition(
                   jobInvocationInfo,                          // Defines the PowerShell job to run.
                   new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the job.
                   null,                                       // No custom options. Accept default.
                   null);                                      // No credentials. PowerShell job is
                                                               // run in default Task Scheduler
                                                               // process, account.

                // Next we register this scheduled job object with Windows Task Scheduler.
                // The Task Scheduler runs the PowerShell script based on the provided job trigger.
                schedJobDefinition.Register();
                registrationSucceeded = true;
                Console.WriteLine("Scheduled job is registered. Waiting 30 seconds for it to run.");

                // You can see this PowerShell job task registered in the Task Scheduler UI.
                // Look under path:
                // Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs

                // Wait for Task Scheduler to run the PowerShell job.
                // This should happen in 20 seconds and then the job takes about 5 seconds to run.
                // If PowerShell job task doesn't run try increasing the trigger time in the
                // ScheduledJobTrigger object.
                // You can run this task manually from the Task Scheduler UI.
                for (int count = 1; count < 31; ++count)
                {
                    Thread.Sleep(1000);
                    Console.WriteLine(count + " seconds elapsed");
                }

                Console.WriteLine();
                Console.WriteLine("Job run results.");
                Console.WriteLine();

                // Since the PowerShell job runs in a non-interactive Task Scheduler
                // process the job status and output data is written to a file based
                // job store and the directory location is the current user local app
                // data ($env:LOCALAPPDATA).
                // This job store can be accessed through the ScheduledJobSourceAdapter class.
                ScheduledJobSourceAdapter schedJobSourceAdapter = new ScheduledJobSourceAdapter();
                IList<Job2> jobRuns = schedJobSourceAdapter.GetJobs();
                foreach (var jobRun in jobRuns)
                {
                    // Check for jobs in finished state.
                    // Note that job data is not written to the job store until the job
                    // has reached a finished state.
                    JobState jobState = jobRun.JobStateInfo.State;
                    if (jobState == JobState.Completed ||
                        jobState == JobState.Stopped ||
                        jobState == JobState.Failed)
                    {
                        // Write job run finished state.
                        Console.WriteLine("Job Status: " + jobRun.JobStateInfo.State);
                        Console.WriteLine();
                        Console.WriteLine("Job Data");

                        // Write output data.
                        foreach (var item in jobRun.Output)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Write any errors.
                        foreach (var item in jobRun.Error)
                        {
                            Console.WriteLine(item.ToString());
                        }
                    }
                }

                Console.WriteLine();
                Console.WriteLine("Press any key to continue...");
                Console.ReadKey();
            }
            catch (ScheduledJobException e)
            {
                Console.WriteLine("Error: " + e.Message);
            }
            finally
            {
                // Unregister this scheduled job or an error will be thrown when
                // running this sample code again (scheduled job already exists.)
                // because all registered scheduled jobs must have a unique name.
                if (registrationSucceeded)
                {
                    schedJobDefinition.Remove(true);
                }
            }
        }
    }
}

```
