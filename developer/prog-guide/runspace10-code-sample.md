---
title: Exemple de Code RunSpace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081238"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="55700-102">Exemple de code RunSpace10</span><span class="sxs-lookup"><span data-stu-id="55700-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="55700-103">Voici le code source pour l’exemple Runspace10.</span><span class="sxs-lookup"><span data-stu-id="55700-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="55700-104">Cet exemple d’application ajoute une applet de commande pour [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) , puis utilise les informations de configuration modifié pour créer l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="55700-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="55700-105">Vous pouvez télécharger le C# le fichier source (runspace10.cs) en utilisant le Kit du développement de logiciel Windows pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="55700-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="55700-106">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="55700-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="55700-107">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="55700-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="55700-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="55700-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="55700-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55700-109">See Also</span></span>

[<span data-ttu-id="55700-110">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="55700-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="55700-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="55700-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)