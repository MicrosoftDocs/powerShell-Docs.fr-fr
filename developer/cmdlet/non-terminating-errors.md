---
title: Sans fin d’exécution erreurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054355"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="70434-102">Erreur sans fin d’exécution</span><span class="sxs-lookup"><span data-stu-id="70434-102">Non-Terminating Errors</span></span>

<span data-ttu-id="70434-103">Cette rubrique décrit la méthode utilisée pour signaler les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="70434-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="70434-104">Elle explique également comment appeler la méthode à partir de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="70434-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="70434-105">Lorsqu’une erreur sans fin d’exécution se produit, l’applet de commande doit signaler cette erreur en appelant le [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode).</span><span class="sxs-lookup"><span data-stu-id="70434-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="70434-106">Lors de l’applet de commande signale une erreur sans fin d’exécution, l’applet de commande peut continuer à fonctionner sur cet objet d’entrée et sur entrante supplémentaire objets du pipeline.</span><span class="sxs-lookup"><span data-stu-id="70434-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="70434-107">Si l’applet de commande appelle le [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode), l’applet de commande peut écrire un enregistrement d’erreur qui décrit la condition ayant provoqué l’erreur sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="70434-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="70434-108">Pour plus d’informations sur les enregistrements d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="70434-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="70434-109">Applets de commande peut appeler [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) que nécessaire dans leurs méthodes de traitement des entrées.</span><span class="sxs-lookup"><span data-stu-id="70434-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="70434-110">Toutefois, les applets de commande peut appeler [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) uniquement à partir du thread qui a appelé le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="70434-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="70434-111">N’appelez pas [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) à partir d’un autre thread.</span><span class="sxs-lookup"><span data-stu-id="70434-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="70434-112">Au lieu de cela, communiquer des erreurs vers le thread principal.</span><span class="sxs-lookup"><span data-stu-id="70434-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="70434-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70434-113">See Also</span></span>

[<span data-ttu-id="70434-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="70434-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="70434-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="70434-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="70434-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="70434-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="70434-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="70434-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="70434-118">Windows PowerShell erreur enregistrements</span><span class="sxs-lookup"><span data-stu-id="70434-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="70434-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70434-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
