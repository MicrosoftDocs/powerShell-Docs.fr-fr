---
title: Exemple de code RunSpace06 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8767ac8dc3a3d9253c2a53a4754d9bd54304abb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784722"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="72bcc-102">Exemple de code RunSpace06</span><span class="sxs-lookup"><span data-stu-id="72bcc-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="72bcc-103">Voici le code source de l’exemple Runspace06 décrit dans [configuration d’une instance d’exécution à l’aide d’un composant logiciel enfichable Windows PowerShell](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="72bcc-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="72bcc-104">Cet exemple d’application crée une instance d’exécution basée sur un composant logiciel enfichable Windows PowerShell, qui est ensuite utilisé pour exécuter un pipeline avec une seule commande.</span><span class="sxs-lookup"><span data-stu-id="72bcc-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="72bcc-105">Pour ce faire, l’application crée les informations de configuration de l’instance d’exécution, crée une instance d’exécution, crée un pipeline avec une commande unique, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="72bcc-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="72bcc-106">Vous pouvez télécharger le fichier source C# (runspace06.cs) à l’aide du kit de développement logiciel (SDK) Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="72bcc-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="72bcc-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="72bcc-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="72bcc-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="72bcc-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="72bcc-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="72bcc-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="72bcc-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72bcc-110">See Also</span></span>

[<span data-ttu-id="72bcc-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="72bcc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="72bcc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="72bcc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
