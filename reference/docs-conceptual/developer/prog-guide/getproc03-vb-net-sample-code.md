---
ms.date: 09/12/2016
ms.topic: reference
title: Exemple de code GetProc03 (VB.NET)
description: Exemple de code GetProc03 (VB.NET)
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355559"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="7f2d2-103">Exemple de code GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="7f2d2-103">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="7f2d2-104">Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui peut accepter une entrée en pipeline.</span><span class="sxs-lookup"><span data-stu-id="7f2d2-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="7f2d2-105">Cette implémentation définit un `Name` paramètre qui accepte l’entrée de pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour envoyer des objets au pipeline.</span><span class="sxs-lookup"><span data-stu-id="7f2d2-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7f2d2-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="7f2d2-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
