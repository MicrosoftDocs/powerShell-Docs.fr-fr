---
title: L’importation et l’appel d’un flux de travail Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854585"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importation et appel d’un workflow Windows PowerShell

Windows PowerShell 3, vous permet d’importer et d’appeler un workflow qui est empaqueté comme un module Windows PowerShell. Pour plus d’informations sur les modules Windows PowerShell, consultez [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).

Le [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)classe est utilisée comme un proxy côté client pour les objets de flux de travail sur le serveur. La procédure suivante explique comment utiliser un [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)objet pour appeler un flux de travail.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Création d’un objet PSJobProxy pour exécuter des commandes de flux de travail sur un serveur distant.

1. Créer un [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)objet à créer une connexion à une instance d’exécution à distance.

2. Définir le [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) propriété de la [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)objet `Microsoft.PowerShell.Workflow` à Spécifiez un point de terminaison de Windows PowerShell.

3. Créer une instance d’exécution qui utilise la connexion créée en effectuant les étapes précédentes.

4. Créer un [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)de l’objet et définissez son [System.Management.Automation.Powershell.Runspace*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) propriété à l’instance d’exécution créé à l’étape précédente.

5. Importer le module de flux de travail et ses commandes dans le [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).

6. Créer un [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) de l’objet et l’utiliser pour exécuter des commandes de flux de travail sur le serveur distant.

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment appeler un flux de travail à l’aide de Windows PowerShell.

Cet exemple nécessite Windows PowerShell 3.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```