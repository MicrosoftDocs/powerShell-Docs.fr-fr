---
title: Exemple de code Runspace02 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1e58f035f20baa7443d9031499062a45beae01b9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778445"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="ff493-102">Exemple de code Runspace02 (C#)</span><span class="sxs-lookup"><span data-stu-id="ff493-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="ff493-103">Voici le code source C# de l’exemple Runspace02.</span><span class="sxs-lookup"><span data-stu-id="ff493-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="ff493-104">Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter l’applet de commande de `Get-Process` façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="ff493-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="ff493-105">Les Windows Forms et la liaison de données sont ensuite utilisés pour afficher les résultats dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="ff493-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="ff493-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="ff493-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="ff493-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff493-107">See Also</span></span>

[<span data-ttu-id="ff493-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ff493-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
