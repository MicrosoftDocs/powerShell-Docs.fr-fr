---
title: Exemple deC#code GetProc02 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360368"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="54f43-102">Exemple de code GetProc02 (C#)</span><span class="sxs-lookup"><span data-stu-id="54f43-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="54f43-103">Le code suivant illustre l’implémentation d’une applet de commande `Get-Process` qui accepte l’entrée de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="54f43-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="54f43-104">Notez que cette implémentation définit un paramètre `Name` pour autoriser l’entrée de ligne de commande, et utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour l’envoi d’objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="54f43-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="54f43-105">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="54f43-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="54f43-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54f43-106">See Also</span></span>

[<span data-ttu-id="54f43-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="54f43-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
