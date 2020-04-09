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
ms.openlocfilehash: 047d14d70853399bc262ac3f1541da38184c3ff8
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977877"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="32e3c-102">Exemple de code Runspace02 (C#)</span><span class="sxs-lookup"><span data-stu-id="32e3c-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="32e3c-103">Voici le C# code source de l’exemple Runspace02.</span><span class="sxs-lookup"><span data-stu-id="32e3c-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="32e3c-104">Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter l’applet de commande `Get-Process` de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="32e3c-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="32e3c-105">Les Windows Forms et la liaison de données sont ensuite utilisés pour afficher les résultats dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="32e3c-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="32e3c-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="32e3c-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="32e3c-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32e3c-107">See Also</span></span>

[<span data-ttu-id="32e3c-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="32e3c-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
