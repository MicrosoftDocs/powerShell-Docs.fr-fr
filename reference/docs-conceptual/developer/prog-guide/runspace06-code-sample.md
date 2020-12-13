---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code RunSpace06
description: Exemple de code RunSpace06
ms.openlocfilehash: 627fa2be51721dd8bfdd63fabdd2e6f286d593be
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667473"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="a2f6f-103">Exemple de code RunSpace06</span><span class="sxs-lookup"><span data-stu-id="a2f6f-103">RunSpace06 Code Sample</span></span>

<span data-ttu-id="a2f6f-104">Voici le code source de l’exemple Runspace06 décrit dans [configuration d’une instance d’exécution à l’aide d’un composant logiciel enfichable Windows PowerShell](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="a2f6f-104">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="a2f6f-105">Cet exemple d’application crée une instance d’exécution basée sur un composant logiciel enfichable Windows PowerShell, qui est ensuite utilisé pour exécuter un pipeline avec une seule commande.</span><span class="sxs-lookup"><span data-stu-id="a2f6f-105">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="a2f6f-106">Pour ce faire, l’application crée les informations de configuration de l’instance d’exécution, crée une instance d’exécution, crée un pipeline avec une commande unique, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a2f6f-106">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="a2f6f-107">Vous pouvez télécharger le fichier source C# (runspace06.cs) à l’aide du kit de développement logiciel (SDK) Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="a2f6f-107">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a2f6f-108">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="a2f6f-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="a2f6f-109">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="a2f6f-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a2f6f-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="a2f6f-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="a2f6f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2f6f-111">See Also</span></span>

[<span data-ttu-id="a2f6f-112">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2f6f-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a2f6f-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a2f6f-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
