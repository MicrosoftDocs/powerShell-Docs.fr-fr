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
ms.openlocfilehash: c5e71ddacae1036164c5e8e579ddc8704d30670e
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978387"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="3f580-102">Exemple de code GetProc02 (C#)</span><span class="sxs-lookup"><span data-stu-id="3f580-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="3f580-103">Le code suivant illustre l’implémentation d’une applet de commande `Get-Process` qui accepte l’entrée de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3f580-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="3f580-104">Notez que cette implémentation définit un paramètre `Name` pour autoriser l’entrée de ligne de commande, et utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour l’envoi d’objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="3f580-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3f580-105">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="3f580-105">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="3f580-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f580-106">See Also</span></span>

[<span data-ttu-id="3f580-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3f580-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
