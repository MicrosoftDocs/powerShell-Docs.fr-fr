---
title: Création d’un flux de travail à l’aide d’un script Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870844"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="0e3dd-102">Création d’un workflow avec un script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e3dd-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="0e3dd-103">Vous pouvez créer un flux de travail en écrivant un script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="0e3dd-104">Pour créer un flux de travail, utilisez le mot clé Workflow suivi d’un nom pour le flux de travail avant le corps du script.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="0e3dd-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e3dd-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="0e3dd-106">Vous trouvez le flux de travail de la même façon que vous le feriez pour toute autre commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="0e3dd-107">Implémentation de Parallel et Sequence</span><span class="sxs-lookup"><span data-stu-id="0e3dd-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="0e3dd-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) prend en charge l’exécution des activités en parallèle.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supports execution of activities in parallel.</span></span> <span data-ttu-id="0e3dd-109">Pour implémenter cette fonctionnalité dans un script Windows PowerShell, utilisez le mot clé `parallel` devant un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="0e3dd-110">Vous pouvez également utiliser la construction `foreach -parallel` pour itérer au sein d’une collection d’objets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="0e3dd-111">Pour exécuter un groupe d’activités dans un ordre séquentiel dans un bloc parallèle, placez ce groupe d’activités dans un bloc de script et précédez le bloc avec le mot clé Sequence.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="0e3dd-112">Joindre des ordinateurs à un domaine</span><span class="sxs-lookup"><span data-stu-id="0e3dd-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="0e3dd-113">Le script suivant crée un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifiés par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joints, puis vérifie à nouveau l’État.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>
<span data-ttu-id="0e3dd-114">Il s’agit d’une version de script du flux de travail XAML expliquée dans [création d’un workflow avec des activités Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="0e3dd-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```