---
title: Exemple de code RunSpace03 (VB.NET) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3b4181889ed15e14c59e3f47a09e39a2696df28c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784773"
---
# <a name="runspace03-vbnet-code-sample"></a><span data-ttu-id="4bcf7-102">Exemple de code RunSpace03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="4bcf7-102">RunSpace03 (VB.NET) Code Sample</span></span>

<span data-ttu-id="4bcf7-103">Voici le code source VB.NET pour l’application console décrite dans la section « création d’une application console qui exécute un script spécifié ».</span><span class="sxs-lookup"><span data-stu-id="4bcf7-103">Here is the VB.NET source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="4bcf7-104">Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter un script qui récupère les informations de processus pour la liste des noms de processus passés dans le script.</span><span class="sxs-lookup"><span data-stu-id="4bcf7-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information for the list of process names passed into the script.</span></span> <span data-ttu-id="4bcf7-105">Il montre comment passer des objets d’entrée à un script et comment récupérer des objets d’erreur ainsi que les objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="4bcf7-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="4bcf7-106">Vous pouvez télécharger le fichier source VB.NET (runspace03. vb) pour cet exemple à l’aide du kit de développement logiciel (SDK) Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="4bcf7-106">You can download the VB.NET source file (runspace03.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4bcf7-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4bcf7-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4bcf7-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="4bcf7-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4bcf7-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="4bcf7-109">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.ObjectModel
Imports System.Text
Imports Microsoft.VisualBasic
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace03

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script that retrieves process information for the
        ''' list of process names passed into the script.
        ''' It shows how to pass input objects to a script and
        ''' how to retrieve error objects as well as the output objects.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that were generated
        '''    during the execution of that script.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of processes to look for
            Dim processNames() As String = {"lsass", "nosuchprocess", _
                "services", "nosuchprocess2"}

            ' The script to run to get these processes. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | get-process -name {$_}"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            Dim errors As System.Collections.IList = Nothing
            Dim result As PSObject
            For Each result In invoker.Invoke(script, processNames, errors)
                Console.WriteLine("{0,-20} {1}", _
                result.Members("ProcessName").Value, _
                result.Members("HandleCount").Value)
            Next result

            ' Now process any error records that were generated while
            ' running the script.
            Console.WriteLine(vbCrLf & _
                "The following non-terminating errors occurred:" & vbCrLf)
            If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                Dim err As PSObject
                For Each err In errors
                    System.Console.WriteLine("    error: {0}", err.ToString())
                Next err
            End If
            System.Console.WriteLine(vbCRLF & "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main

    End Class 'Runspace03

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace03.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace03.vb#L09-L83 "Runspace03.vb")] -->

## <a name="see-also"></a><span data-ttu-id="4bcf7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bcf7-110">See Also</span></span>

[<span data-ttu-id="4bcf7-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4bcf7-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4bcf7-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4bcf7-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
