---
title: Création d’un Workflow à l’aide d’un Script PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080371"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="7671b-102">Création d’un workflow avec un script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7671b-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="7671b-103">Vous pouvez créer un flux de travail en écrivant un script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7671b-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="7671b-104">Pour créer un flux de travail, utilisez le mot clé de flux de travail suivi d’un nom pour le flux de travail avant le corps du script.</span><span class="sxs-lookup"><span data-stu-id="7671b-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="7671b-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7671b-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="7671b-106">Le flux de travail se trouvent dans la même façon que vous le feriez pour toute autre commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7671b-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="7671b-107">Implémentation de Parallel et Sequence</span><span class="sxs-lookup"><span data-stu-id="7671b-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="7671b-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) prend en charge l’exécution des activités en parallèle.</span><span class="sxs-lookup"><span data-stu-id="7671b-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="7671b-109">Pour implémenter cette fonctionnalité dans un script Windows PowerShell, utilisez le `parallel` mot-clé devant un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="7671b-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="7671b-110">Vous pouvez également utiliser le `foreach -parallel` construction pour itérer une collection d’objets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="7671b-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="7671b-111">Pour exécuter un groupe d’activités dans un ordre séquentiel au sein d’un bloc parallèle, placez ce groupe d’activités dans un bloc de script et faites précéder le bloc avec le mot clé de séquence.</span><span class="sxs-lookup"><span data-stu-id="7671b-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="7671b-112">Joindre des ordinateurs à un domaine</span><span class="sxs-lookup"><span data-stu-id="7671b-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="7671b-113">Le script suivant crée un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifié par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joint, puis vérifie à nouveau l’état.</span><span class="sxs-lookup"><span data-stu-id="7671b-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="7671b-114">Il s’agit d’une version de script du flux de travail XAML expliqué dans [création d’un flux de travail avec Windows PowerShell activités](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="7671b-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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