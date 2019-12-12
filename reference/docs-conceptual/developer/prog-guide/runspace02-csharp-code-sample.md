---
title: Exemple deC#code Runspace02 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: abf539bc29bd9ccac59bd5957397fbe68951f266
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366618"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="07dfa-102">Exemple de code Runspace02 (C#)</span><span class="sxs-lookup"><span data-stu-id="07dfa-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="07dfa-103">Voici le C# code source de l’exemple Runspace02.</span><span class="sxs-lookup"><span data-stu-id="07dfa-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="07dfa-104">Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter l’applet de commande `Get-Process` de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="07dfa-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="07dfa-105">Les Windows Forms et la liaison de données sont ensuite utilisés pour afficher les résultats dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="07dfa-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="07dfa-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="07dfa-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="07dfa-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07dfa-107">See Also</span></span>

[<span data-ttu-id="07dfa-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="07dfa-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
