---
title: Exemple de code RunSpace03 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: df34652f60ed85b13739a04485cf6622cf924872
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784790"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="9e907-102">Exemple de code RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="9e907-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="9e907-103">Voici le code source C# de l’application console décrite dans « création d’une application console qui exécute un script spécifié ».</span><span class="sxs-lookup"><span data-stu-id="9e907-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="9e907-104">Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter un script qui récupère les informations de processus à l’aide de la liste des noms de processus passée dans le script.</span><span class="sxs-lookup"><span data-stu-id="9e907-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="9e907-105">Il montre comment passer des objets d’entrée à un script et comment récupérer des objets d’erreur ainsi que les objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="9e907-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="9e907-106">Vous pouvez télécharger le fichier source C# (runspace03.cs) pour cet exemple à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="9e907-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9e907-107">Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9e907-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9e907-108">Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.</span><span class="sxs-lookup"><span data-stu-id="9e907-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9e907-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="9e907-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="9e907-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e907-110">See Also</span></span>

[<span data-ttu-id="9e907-111">Guide de programmation pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e907-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9e907-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9e907-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
