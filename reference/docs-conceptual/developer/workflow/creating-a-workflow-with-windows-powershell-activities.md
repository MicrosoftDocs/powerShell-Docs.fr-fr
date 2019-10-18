---
title: Création d’un flux de travail avec des activités Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359628"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="1a14a-102">Création d’un workflow avec des activités Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a14a-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="1a14a-103">Vous pouvez créer un flux de travail Windows PowerShell en sélectionnant activités dans la boîte à outils Visual Studio et en les faisant glisser vers la fenêtre de Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1a14a-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="1a14a-104">Pour plus d’informations sur l’ajout d’activités Windows PowerShell à la boîte à outils de Visual Studio, consultez [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="1a14a-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="1a14a-105">Les procédures suivantes décrivent comment créer un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifiés par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joints, puis vérifie à nouveau l’État.</span><span class="sxs-lookup"><span data-stu-id="1a14a-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="1a14a-106">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="1a14a-106">Setting up the Project</span></span>

1. <span data-ttu-id="1a14a-107">Suivez la procédure décrite dans [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) pour créer un projet de flux de travail et ajouter des activités à partir de [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) et [Microsoft. PowerShell. Management. Activities ](/dotnet/api/Microsoft.PowerShell.Management.Activities)assemblys de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="1a14a-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="1a14a-108">Ajoutez System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities et Microsoft. PowerShell. Commands. Management au projet en tant qu’assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="1a14a-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="1a14a-109">Ajout d’activités au flux de travail</span><span class="sxs-lookup"><span data-stu-id="1a14a-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="1a14a-110">Ajoutez une activité **Sequence** au workflow.</span><span class="sxs-lookup"><span data-stu-id="1a14a-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="1a14a-111">Créez un argument nommé `ComputerName` avec un type d’argument `String[]`.</span><span class="sxs-lookup"><span data-stu-id="1a14a-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="1a14a-112">Cet argument représente les noms des ordinateurs à vérifier et joindre.</span><span class="sxs-lookup"><span data-stu-id="1a14a-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="1a14a-113">Créez un argument nommé `DomainCred` de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="1a14a-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="1a14a-114">Cet argument représente les informations d’identification de domaine d’un compte de domaine qui est autorisé à joindre un ordinateur au domaine.</span><span class="sxs-lookup"><span data-stu-id="1a14a-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="1a14a-115">Créez un argument nommé `MachineCred` de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="1a14a-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="1a14a-116">Cet argument représente les informations d’identification d’un administrateur sur les ordinateurs à vérifier et à joindre.</span><span class="sxs-lookup"><span data-stu-id="1a14a-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="1a14a-117">Ajoutez une activité **ParallelForEach** dans l’activité **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="1a14a-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="1a14a-118">Entrez `comp` et `ComputerName` dans les zones de texte afin que la boucle itère au sein des éléments du tableau `ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="1a14a-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="1a14a-119">Ajoutez une activité **Sequence** au corps de l’activité **ParallelForEach** .</span><span class="sxs-lookup"><span data-stu-id="1a14a-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="1a14a-120">Définissez la propriété **DisplayName** de la séquence sur `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="1a14a-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="1a14a-121">Ajoutez une activité **GetWmiObject** à la séquence **JoinDomain** .</span><span class="sxs-lookup"><span data-stu-id="1a14a-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="1a14a-122">Modifiez les propriétés de l’activité **GetWmiObject** comme suit.</span><span class="sxs-lookup"><span data-stu-id="1a14a-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="1a14a-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="1a14a-123">Property</span></span>|<span data-ttu-id="1a14a-124">Value</span><span class="sxs-lookup"><span data-stu-id="1a14a-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="1a14a-125">**Type**</span><span class="sxs-lookup"><span data-stu-id="1a14a-125">**Class**</span></span>|<span data-ttu-id="1a14a-126">« Win32_ComputerSystem »</span><span class="sxs-lookup"><span data-stu-id="1a14a-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="1a14a-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="1a14a-127">**PSComputerName**</span></span>|<span data-ttu-id="1a14a-128">conformes</span><span class="sxs-lookup"><span data-stu-id="1a14a-128">{comp}</span></span>|
   |<span data-ttu-id="1a14a-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="1a14a-129">**PSCredential**</span></span>|<span data-ttu-id="1a14a-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="1a14a-130">MachineCred</span></span>|

9. <span data-ttu-id="1a14a-131">Ajoutez une activité **AddComputer** à la séquence **JoinDomain** après l’activité **GetWmiObject** .</span><span class="sxs-lookup"><span data-stu-id="1a14a-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="1a14a-132">Modifiez les propriétés de l’activité **AddComputer** comme suit.</span><span class="sxs-lookup"><span data-stu-id="1a14a-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="1a14a-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="1a14a-133">Property</span></span>|<span data-ttu-id="1a14a-134">Value</span><span class="sxs-lookup"><span data-stu-id="1a14a-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1a14a-135">**Nomd’ordinateur**</span><span class="sxs-lookup"><span data-stu-id="1a14a-135">**ComputerName**</span></span>|<span data-ttu-id="1a14a-136">conformes</span><span class="sxs-lookup"><span data-stu-id="1a14a-136">{comp}</span></span>|
    |<span data-ttu-id="1a14a-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="1a14a-137">**DomainCredential**</span></span>|<span data-ttu-id="1a14a-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="1a14a-138">DomainCred</span></span>|

11. <span data-ttu-id="1a14a-139">Ajoutez une activité **RestartComputer** à la séquence **JoinDomain** après l’activité **AddComputer** .</span><span class="sxs-lookup"><span data-stu-id="1a14a-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="1a14a-140">Modifiez les propriétés de l’activité **RestartComputer** comme suit.</span><span class="sxs-lookup"><span data-stu-id="1a14a-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="1a14a-141">Propriété</span><span class="sxs-lookup"><span data-stu-id="1a14a-141">Property</span></span>|<span data-ttu-id="1a14a-142">Value</span><span class="sxs-lookup"><span data-stu-id="1a14a-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1a14a-143">**Nomd’ordinateur**</span><span class="sxs-lookup"><span data-stu-id="1a14a-143">**ComputerName**</span></span>|<span data-ttu-id="1a14a-144">conformes</span><span class="sxs-lookup"><span data-stu-id="1a14a-144">{comp}</span></span>|
    |<span data-ttu-id="1a14a-145">**Justificative**</span><span class="sxs-lookup"><span data-stu-id="1a14a-145">**Credential**</span></span>|<span data-ttu-id="1a14a-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="1a14a-146">MachineCred</span></span>|
    |<span data-ttu-id="1a14a-147">**Pour**</span><span class="sxs-lookup"><span data-stu-id="1a14a-147">**For**</span></span>|<span data-ttu-id="1a14a-148">Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a14a-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="1a14a-149">**Appliqués**</span><span class="sxs-lookup"><span data-stu-id="1a14a-149">**Force**</span></span>|<span data-ttu-id="1a14a-150">True</span><span class="sxs-lookup"><span data-stu-id="1a14a-150">True</span></span>|
    |<span data-ttu-id="1a14a-151">Wait</span><span class="sxs-lookup"><span data-stu-id="1a14a-151">Wait</span></span>|<span data-ttu-id="1a14a-152">True</span><span class="sxs-lookup"><span data-stu-id="1a14a-152">True</span></span>|
    |<span data-ttu-id="1a14a-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="1a14a-153">PSComputerName</span></span>|<span data-ttu-id="1a14a-154">{""}</span><span class="sxs-lookup"><span data-stu-id="1a14a-154">{""}</span></span>|

13. <span data-ttu-id="1a14a-155">Ajoutez une activité **GetWmiObject** à la séquence **JoinDomain** après l’activité **RestartComputer** .</span><span class="sxs-lookup"><span data-stu-id="1a14a-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="1a14a-156">Modifiez ses propriétés afin qu’elles soient identiques à celles de l’activité **GetWmiObject** précédente.</span><span class="sxs-lookup"><span data-stu-id="1a14a-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="1a14a-157">Lorsque vous avez terminé les procédures, la fenêtre de conception de Workflow doit ressembler à ceci.</span><span class="sxs-lookup"><span data-stu-id="1a14a-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="1a14a-158">![JoinDomain XAML dans le concepteur de flux de travail @ no__t-1![JOINDOMAIN XAML dans le concepteur de workflow](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="1a14a-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>