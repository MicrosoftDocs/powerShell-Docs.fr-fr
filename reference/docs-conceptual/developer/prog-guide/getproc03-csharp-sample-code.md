---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code GetProc03 (C#)
description: Exemple de code GetProc03 (C#)
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355576"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="4d82c-103">Exemple de code GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="4d82c-103">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="4d82c-104">Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui peut accepter une entrée en pipeline.</span><span class="sxs-lookup"><span data-stu-id="4d82c-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="4d82c-105">Cette implémentation définit un `Name` paramètre qui accepte l’entrée de pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour envoyer des objets au pipeline.</span><span class="sxs-lookup"><span data-stu-id="4d82c-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="4d82c-106">Vous pouvez télécharger le fichier source C# (getprov03.cs) pour cette Get-Proc applet de commande à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0.</span><span class="sxs-lookup"><span data-stu-id="4d82c-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4d82c-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4d82c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4d82c-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="4d82c-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4d82c-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="4d82c-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="4d82c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d82c-110">See Also</span></span>

[<span data-ttu-id="4d82c-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d82c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4d82c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4d82c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
