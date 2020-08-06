---
title: Exemple de code GetProc02 (VB.NET) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 98261f2d6678e24bb8e8df6d2c8a405b25203364
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787170"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="002e4-102">Exemple de code GetProc02 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="002e4-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="002e4-103">Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui accepte l’entrée de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="002e4-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="002e4-104">Notez que cette implémentation définit un `Name` paramètre pour autoriser l’entrée de ligne de commande et qu’elle utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour l’envoi d’objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="002e4-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="002e4-105">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="002e4-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="002e4-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="002e4-106">See Also</span></span>

[<span data-ttu-id="002e4-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="002e4-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
