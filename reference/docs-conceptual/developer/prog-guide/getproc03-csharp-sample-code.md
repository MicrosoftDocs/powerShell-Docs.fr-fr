---
title: Exemple deC#code GetProc03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 126df3092c0722b0fc9d02cb61d3faf0578b8e97
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416125"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="111b5-102">Exemple de code GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="111b5-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="111b5-103">Le code suivant illustre l’implémentation d’une applet de commande `Get-Process` qui peut accepter une entrée en pipeline.</span><span class="sxs-lookup"><span data-stu-id="111b5-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="111b5-104">Cette implémentation définit un paramètre de `Name` qui accepte l’entrée de pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour envoyer des objets au pipeline.</span><span class="sxs-lookup"><span data-stu-id="111b5-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="111b5-105">Vous pouvez télécharger le C# fichier source (getprov03.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="111b5-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="111b5-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="111b5-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="111b5-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="111b5-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="111b5-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="111b5-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="111b5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="111b5-109">See Also</span></span>

[<span data-ttu-id="111b5-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="111b5-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="111b5-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="111b5-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
