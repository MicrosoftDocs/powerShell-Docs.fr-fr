---
title: Création d’une activité de workflow à partir d’une applet de commande Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: 5761ed2168a46d6ed9a2e50554d459f5b93223ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359658"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a><span data-ttu-id="fd7a5-102">Création d’une activité de workflow à partir d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd7a5-102">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="fd7a5-103">Tout module ou applet de commande Windows PowerShell peut être empaqueté en tant qu’activité de flux de travail à l’aide des méthodes de la classe [Microsoft. PowerShell. Activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) .</span><span class="sxs-lookup"><span data-stu-id="fd7a5-103">Any Windows PowerShell module or cmdlet can be packaged as a Workflow activity by using the methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class.</span></span> <span data-ttu-id="fd7a5-104">Utilisez les méthodes [Microsoft. PowerShell. Activities. Activitygenerator. Generatefrommoduleinfo \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft. PowerShell. Activities. Activitygenerator. Generatefromcommandinfo \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)et Microsoft. PowerShell. Activities. [Activitygenerator. Generatefromname \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) de la classe [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) . C# Activitygenerator pour générer le code qui représente une activité.</span><span class="sxs-lookup"><span data-stu-id="fd7a5-104">Use the [Microsoft.Powershell.Activities.Activitygenerator.Generatefrommoduleinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft.Powershell.Activities.Activitygenerator.Generatefromcommandinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo), and [Microsoft.Powershell.Activities.Activitygenerator.Generatefromname\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class to generate C# code that represents an activity.</span></span> <span data-ttu-id="fd7a5-105">Vous pouvez ensuite compiler le code C# résultant dans un assembly qui peut être ajouté à un projet en tant qu’activité.</span><span class="sxs-lookup"><span data-stu-id="fd7a5-105">You can then compile the resulting C# code into an assembly that can be added to a project as an activity.</span></span>

<span data-ttu-id="fd7a5-106">Vous pouvez ensuite compiler le code C# résultant dans un assembly qui peut être ajouté à un projet en tant qu’activité à l’aide d’une ligne de commande au format suivant.</span><span class="sxs-lookup"><span data-stu-id="fd7a5-106">You can then compile the resulting C# code into an assembly that can be added to a project as an activity by using a command line with the following form.</span></span>

<span data-ttu-id="fd7a5-107">**CSC/nologo/out : AssemblyName/target : Library/Reference : System. Activities. Activity/Reference : Microsoft. PowerShell. Activities codefile.cs**</span><span class="sxs-lookup"><span data-stu-id="fd7a5-107">**csc /nologo /out:AssemblyName /target:library /reference:System.Activities.Activity /reference:Microsoft.PowerShell.Activities codefile.cs**</span></span>

## <a name="example"></a><span data-ttu-id="fd7a5-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd7a5-108">Example</span></span>

<span data-ttu-id="fd7a5-109">L’exemple suivant montre comment générer C# du code pour une activité à partir d’un module Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd7a5-109">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell module.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a><span data-ttu-id="fd7a5-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd7a5-110">Example</span></span>

<span data-ttu-id="fd7a5-111">L’exemple suivant montre comment générer C# du code pour une activité à partir d’une applet de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd7a5-111">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell cmdlet.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```