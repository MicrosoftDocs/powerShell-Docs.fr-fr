---
title: Importation et appel d’un flux de travail Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366038"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importation et appel d’un workflow Windows PowerShell

Windows PowerShell 3 vous permet d’importer et d’appeler un flux de travail empaqueté en tant que module Windows PowerShell. Pour plus d’informations sur les modules Windows PowerShell, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).

La classe [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)est utilisée comme un proxy côté client pour les objets de flux de travail sur le serveur. La procédure suivante explique comment utiliser un objet [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)pour appeler un Workflow.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Création d’un objet PSJobProxy pour exécuter des commandes de workflow sur un serveur distant.

1. Créez un objet [System. Management. Automation. instances d’exécution. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)pour créer une connexion à une instance d’exécution distante.

2. Définissez la propriété [System. Management. Automation. instances d’exécution. Wsmanconnectioninfo. Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) de l’objet [System. Management. Automation. instances d’exécution. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)sur `Microsoft.PowerShell.Workflow` pour spécifier un point de terminaison Windows PowerShell.

3. Créez une instance d’exécution qui utilise la connexion créée en effectuant les étapes précédentes.

4. Créez un objet [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)et définissez sa propriété [System. Management. Automation. PowerShell. Runspace *](/dotnet/api/System.Management.Automation.PowerShell.Runspace) sur l’instance d’exécution créée à l’étape précédente.

5. Importez le module de flux de travail et ses commandes dans [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell).

6. Créez un objet [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) et utilisez-le pour exécuter des commandes de workflow sur le serveur distant.

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment appeler un workflow à l’aide de Windows PowerShell.

Cet exemple requiert Windows PowerShell 3.

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