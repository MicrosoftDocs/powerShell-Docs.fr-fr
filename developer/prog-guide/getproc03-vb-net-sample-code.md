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
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081646"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="01419-102">Exemple de code GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="01419-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="01419-103">Le code suivant illustre l’implémentation d’un `Get-Process` entrée en pipeline l’applet de commande qui peut accepter.</span><span class="sxs-lookup"><span data-stu-id="01419-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="01419-104">Cette implémentation définit un `Name` paramètre qui accepte les entrées de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis et utilise ensuite la [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) méthode en tant que le mécanisme de sortie pour envoyer des objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="01419-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="01419-105">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="01419-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->