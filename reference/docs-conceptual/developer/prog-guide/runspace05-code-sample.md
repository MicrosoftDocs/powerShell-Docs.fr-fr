---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code RunSpace05
description: Exemple de code RunSpace05
ms.openlocfilehash: f128e09522bdb05cba2c160bce4944c829a5c108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654214"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="f8b4c-103">Exemple de code RunSpace05</span><span class="sxs-lookup"><span data-stu-id="f8b4c-103">RunSpace05 Code Sample</span></span>

<span data-ttu-id="f8b4c-104">Voici le code source de l’exemple Runspace05 décrit dans [configuration d’une instance d’exécution à l’aide de RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="f8b4c-104">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="f8b4c-105">Cet exemple montre comment créer les informations de configuration de l’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une commande unique, puis exécuter le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8b4c-105">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="f8b4c-106">La commande exécutée est l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="f8b4c-106">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f8b4c-107">Vous pouvez télécharger le fichier source C# (runspace05.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="f8b4c-107">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f8b4c-108">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f8b4c-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="f8b4c-109">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="f8b4c-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f8b4c-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="f8b4c-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="f8b4c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8b4c-111">See Also</span></span>

[<span data-ttu-id="f8b4c-112">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8b4c-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f8b4c-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f8b4c-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
