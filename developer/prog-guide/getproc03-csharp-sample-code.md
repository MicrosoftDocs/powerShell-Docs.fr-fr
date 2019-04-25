---
title: GetProc03 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081512"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="4dbc4-102">Exemple de code GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="4dbc4-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="4dbc4-103">Le code suivant illustre l’implémentation d’un `Get-Process` entrée en pipeline l’applet de commande qui peut accepter.</span><span class="sxs-lookup"><span data-stu-id="4dbc4-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="4dbc4-104">Cette implémentation définit un `Name` paramètre qui accepte les entrées de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis et utilise ensuite la [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) méthode en tant que le mécanisme de sortie pour envoyer des objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="4dbc4-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="4dbc4-105">Vous pouvez télécharger le C# le fichier source (getprov03.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="4dbc4-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4dbc4-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4dbc4-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4dbc4-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="4dbc4-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4dbc4-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="4dbc4-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="4dbc4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dbc4-109">See Also</span></span>

[<span data-ttu-id="4dbc4-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4dbc4-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4dbc4-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4dbc4-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)