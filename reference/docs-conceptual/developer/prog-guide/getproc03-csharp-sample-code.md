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
ms.openlocfilehash: 10c41ffd03e9adae82813bfe79d3e15030087953
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360338"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="769b3-102">Exemple de code GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="769b3-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="769b3-103">Le code suivant illustre l’implémentation d’une applet de commande `Get-Process` qui peut accepter une entrée en pipeline.</span><span class="sxs-lookup"><span data-stu-id="769b3-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="769b3-104">Cette implémentation définit un paramètre `Name` qui accepte l’entrée de pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme sortie. mécanisme pour envoyer des objets au pipeline.</span><span class="sxs-lookup"><span data-stu-id="769b3-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="769b3-105">Vous pouvez télécharger le C# fichier source (getprov03.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="769b3-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="769b3-106">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="769b3-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="769b3-107">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="769b3-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="769b3-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="769b3-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="769b3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="769b3-109">See Also</span></span>

[<span data-ttu-id="769b3-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="769b3-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="769b3-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="769b3-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
