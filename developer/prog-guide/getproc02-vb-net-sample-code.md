---
title: GetProc02 (VB.NET) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 821d0dd327529614322e446bfb30d128d1b6a7f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081581"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="c4317-102">Exemple de code GetProc02 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c4317-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="c4317-103">Le code suivant illustre l’implémentation d’un `Get-Process` applet de commande qui accepte les entrées de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c4317-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="c4317-104">Notez que cette implémentation définit un `Name` paramètre pour autoriser l’entrée de ligne de commande et il utilise le [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) méthode comme sortie mécanisme pour envoyer la sortie des objets au pipeline.</span><span class="sxs-lookup"><span data-stu-id="c4317-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c4317-105">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c4317-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="c4317-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4317-106">See Also</span></span>

[<span data-ttu-id="c4317-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c4317-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)