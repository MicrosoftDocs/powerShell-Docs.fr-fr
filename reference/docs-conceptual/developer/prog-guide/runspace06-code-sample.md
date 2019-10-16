---
title: Exemple de code RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: f0197e6ca3535b72f843ba52e97381c0f2531598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366488"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="fd1c5-102">Exemple de code RunSpace06</span><span class="sxs-lookup"><span data-stu-id="fd1c5-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="fd1c5-103">Voici le code source de l’exemple Runspace06 décrit dans [configuration d’une instance d’exécution à l’aide d’un composant logiciel enfichable Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="fd1c5-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="fd1c5-104">Cet exemple d’application crée une instance d’exécution basée sur un composant logiciel enfichable Windows PowerShell, qui est ensuite utilisé pour exécuter un pipeline avec une seule commande.</span><span class="sxs-lookup"><span data-stu-id="fd1c5-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="fd1c5-105">Pour ce faire, l’application crée les informations de configuration de l’instance d’exécution, crée une instance d’exécution, crée un pipeline avec une commande unique, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="fd1c5-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="fd1c5-106">Vous pouvez télécharger le C# fichier source (runspace06.cs) à l’aide du kit de développement logiciel (SDK) Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="fd1c5-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fd1c5-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="fd1c5-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="fd1c5-108">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="fd1c5-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fd1c5-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="fd1c5-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="fd1c5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd1c5-110">See Also</span></span>

[<span data-ttu-id="fd1c5-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd1c5-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fd1c5-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fd1c5-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
