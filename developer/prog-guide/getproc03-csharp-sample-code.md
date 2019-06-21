---
title: GetProc03 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 116a116a5ba5b81a77b4432a81f001cc999fe46d
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301356"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="dff0e-102">Exemple de code GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="dff0e-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="dff0e-103">Le code suivant illustre l’implémentation d’un `Get-Process` entrée en pipeline l’applet de commande qui peut accepter.</span><span class="sxs-lookup"><span data-stu-id="dff0e-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="dff0e-104">Cette implémentation définit un `Name` paramètre qui accepte les entrées de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis et utilise ensuite le [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)(méthode) comme mécanisme de sortie pour envoyer des objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="dff0e-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="dff0e-105">Vous pouvez télécharger le C# le fichier source (getprov03.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="dff0e-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dff0e-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="dff0e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="dff0e-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="dff0e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dff0e-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="dff0e-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="dff0e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dff0e-109">See Also</span></span>

[<span data-ttu-id="dff0e-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dff0e-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dff0e-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dff0e-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
