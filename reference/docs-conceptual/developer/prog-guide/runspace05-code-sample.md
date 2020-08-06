---
title: Exemple de code RunSpace05 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31a73f965a6e38dceec740a2f7d4adead3e2a3f9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784739"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="eee64-102">Exemple de code RunSpace05</span><span class="sxs-lookup"><span data-stu-id="eee64-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="eee64-103">Voici le code source de l’exemple Runspace05 décrit dans [configuration d’une instance d’exécution à l’aide de RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="eee64-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="eee64-104">Cet exemple montre comment créer les informations de configuration de l’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une commande unique, puis exécuter le pipeline.</span><span class="sxs-lookup"><span data-stu-id="eee64-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="eee64-105">La commande exécutée est l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="eee64-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="eee64-106">Vous pouvez télécharger le fichier source C# (runspace05.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="eee64-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eee64-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="eee64-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="eee64-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="eee64-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="eee64-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="eee64-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="eee64-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eee64-110">See Also</span></span>

[<span data-ttu-id="eee64-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eee64-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="eee64-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="eee64-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
