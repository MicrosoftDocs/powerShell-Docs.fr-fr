---
title: Runspace01 exemple de Code (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12ee5382-95ba-41c7-8291-7f69a6f63514
caps.latest.revision: 7
ms.openlocfilehash: c45e802605bf0b4fd84a8847787bcc937b7f417b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081431"
---
# <a name="runspace01-vbnet-code-sample"></a><span data-ttu-id="09c46-102">Exemple de code Runspace01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="09c46-102">Runspace01 (VB.NET) Code Sample</span></span>

<span data-ttu-id="09c46-103">Voici les exemples de code pour l’instance d’exécution décrit dans [création d’une Console Application qui s’exécute une commande spécifiée](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="09c46-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="09c46-104">Pour ce faire, l’application appelle une instance d’exécution et appelle ensuite une commande.</span><span class="sxs-lookup"><span data-stu-id="09c46-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="09c46-105">(Notez que cette application ne spécifie pas les informations de configuration d’instance d’exécution, ni il crée explicitement un pipeline). La commande est appelée est la `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09c46-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>

## <a name="code-sample"></a><span data-ttu-id="09c46-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="09c46-106">Code Sample</span></span>

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a><span data-ttu-id="09c46-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09c46-107">See Also</span></span>

[<span data-ttu-id="09c46-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="09c46-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)