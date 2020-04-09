---
title: Exemple de code RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 55005a254ef50a2230121095770899cb3b9b70f1
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978219"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="dba26-102">Exemple de code RunSpace07</span><span class="sxs-lookup"><span data-stu-id="dba26-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="dba26-103">Voici le code source de l’exemple Runspace07 décrit dans [création d’une application console qui ajoute des commandes à un pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="dba26-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="dba26-104">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="dba26-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="dba26-105">Les commandes ajoutées au pipeline sont les applets de commande `Get-Process` et `Measure-Object`.</span><span class="sxs-lookup"><span data-stu-id="dba26-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="dba26-106">Vous pouvez télécharger le C# fichier source (runspace07.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="dba26-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dba26-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="dba26-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="dba26-108">Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="dba26-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dba26-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="dba26-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="dba26-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dba26-110">See Also</span></span>

[<span data-ttu-id="dba26-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dba26-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dba26-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dba26-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
