---
title: GetProc03 (VB.NET) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301568"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="5f76c-102">Exemple de code GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="5f76c-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="5f76c-103">Le code suivant illustre l’implémentation d’un `Get-Process` entrée en pipeline l’applet de commande qui peut accepter.</span><span class="sxs-lookup"><span data-stu-id="5f76c-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="5f76c-104">Cette implémentation définit un `Name` paramètre qui accepte les entrées de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis et utilise ensuite le [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)(méthode) comme mécanisme de sortie pour envoyer des objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5f76c-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5f76c-105">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="5f76c-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
