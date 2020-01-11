---
title: Exemple de code RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 8802e308712be93992ead5ef77b97d8c21b137f7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870640"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="837d9-102">Exemple de code RunSpace05</span><span class="sxs-lookup"><span data-stu-id="837d9-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="837d9-103">Voici le code source de l’exemple Runspace05 décrit dans [configuration d’une instance d’exécution à l’aide de RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="837d9-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="837d9-104">Cet exemple montre comment créer les informations de configuration de l’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une commande unique, puis exécuter le pipeline.</span><span class="sxs-lookup"><span data-stu-id="837d9-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="837d9-105">La commande exécutée est l’applet de commande `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="837d9-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="837d9-106">Vous pouvez télécharger le C# fichier source (runspace05.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="837d9-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="837d9-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="837d9-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="837d9-108">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="837d9-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="837d9-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="837d9-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="837d9-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="837d9-110">See Also</span></span>

[<span data-ttu-id="837d9-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="837d9-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="837d9-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="837d9-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
