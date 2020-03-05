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
ms.openlocfilehash: 7d399786b9b43ee302493359d9702981045212e9
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78277460"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="fd273-102">Création d’un workflow avec des activités Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd273-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="fd273-103">Vous pouvez créer un flux de travail Windows PowerShell en sélectionnant activités dans la boîte à outils Visual Studio et en les faisant glisser vers la fenêtre de Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fd273-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="fd273-104">Pour plus d’informations sur l’ajout d’activités Windows PowerShell à la boîte à outils de Visual Studio, consultez [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="fd273-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="fd273-105">Les procédures suivantes décrivent comment créer un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifiés par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joints, puis vérifie à nouveau l’État.</span><span class="sxs-lookup"><span data-stu-id="fd273-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="fd273-106">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="fd273-106">Setting up the Project</span></span>

1. <span data-ttu-id="fd273-107">Suivez la procédure décrite dans [Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) pour créer un projet de workflow et ajouter les activités des assemblys [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) et [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) à la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="fd273-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="fd273-108">Ajoutez System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities et Microsoft. PowerShell. Commands. Management au projet en tant qu’assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="fd273-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="fd273-109">Ajout d’activités au flux de travail</span><span class="sxs-lookup"><span data-stu-id="fd273-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="fd273-110">Ajoutez une activité **Sequence** au workflow.</span><span class="sxs-lookup"><span data-stu-id="fd273-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="fd273-111">Créez un argument nommé `ComputerName` avec un type d’argument `String[]`.</span><span class="sxs-lookup"><span data-stu-id="fd273-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="fd273-112">Cet argument représente les noms des ordinateurs à vérifier et joindre.</span><span class="sxs-lookup"><span data-stu-id="fd273-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="fd273-113">Créez un argument nommé `DomainCred` de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="fd273-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="fd273-114">Cet argument représente les informations d’identification de domaine d’un compte de domaine qui est autorisé à joindre un ordinateur au domaine.</span><span class="sxs-lookup"><span data-stu-id="fd273-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="fd273-115">Créez un argument nommé `MachineCred` de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="fd273-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="fd273-116">Cet argument représente les informations d’identification d’un administrateur sur les ordinateurs à vérifier et à joindre.</span><span class="sxs-lookup"><span data-stu-id="fd273-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="fd273-117">Ajoutez une activité **ParallelForEach** dans l’activité **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="fd273-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="fd273-118">Entrez `comp` et `ComputerName` dans les zones de texte afin que la boucle itère au sein des éléments du tableau `ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="fd273-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="fd273-119">Ajoutez une activité **Sequence** au corps de l’activité **ParallelForEach** .</span><span class="sxs-lookup"><span data-stu-id="fd273-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="fd273-120">Définissez la propriété **DisplayName** de la séquence sur `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="fd273-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="fd273-121">Ajoutez une activité **GetWmiObject** à la séquence **JoinDomain** .</span><span class="sxs-lookup"><span data-stu-id="fd273-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="fd273-122">Modifiez les propriétés de l’activité **GetWmiObject** comme suit.</span><span class="sxs-lookup"><span data-stu-id="fd273-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="fd273-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="fd273-123">Property</span></span>|<span data-ttu-id="fd273-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd273-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="fd273-125">**Classe**</span><span class="sxs-lookup"><span data-stu-id="fd273-125">**Class**</span></span>|<span data-ttu-id="fd273-126">« Win32_ComputerSystem »</span><span class="sxs-lookup"><span data-stu-id="fd273-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="fd273-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="fd273-127">**PSComputerName**</span></span>|<span data-ttu-id="fd273-128">conformes</span><span class="sxs-lookup"><span data-stu-id="fd273-128">{comp}</span></span>|
   |<span data-ttu-id="fd273-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="fd273-129">**PSCredential**</span></span>|<span data-ttu-id="fd273-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="fd273-130">MachineCred</span></span>|

9. <span data-ttu-id="fd273-131">Ajoutez une activité **AddComputer** à la séquence **JoinDomain** après l’activité **GetWmiObject** .</span><span class="sxs-lookup"><span data-stu-id="fd273-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="fd273-132">Modifiez les propriétés de l’activité **AddComputer** comme suit.</span><span class="sxs-lookup"><span data-stu-id="fd273-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="fd273-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="fd273-133">Property</span></span>|<span data-ttu-id="fd273-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd273-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="fd273-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="fd273-135">**ComputerName**</span></span>|<span data-ttu-id="fd273-136">conformes</span><span class="sxs-lookup"><span data-stu-id="fd273-136">{comp}</span></span>|
    |<span data-ttu-id="fd273-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="fd273-137">**DomainCredential**</span></span>|<span data-ttu-id="fd273-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="fd273-138">DomainCred</span></span>|

11. <span data-ttu-id="fd273-139">Ajoutez une activité **RestartComputer** à la séquence **JoinDomain** après l’activité **AddComputer** .</span><span class="sxs-lookup"><span data-stu-id="fd273-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="fd273-140">Modifiez les propriétés de l’activité **RestartComputer** comme suit.</span><span class="sxs-lookup"><span data-stu-id="fd273-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="fd273-141">Propriété</span><span class="sxs-lookup"><span data-stu-id="fd273-141">Property</span></span>|<span data-ttu-id="fd273-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd273-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="fd273-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="fd273-143">**ComputerName**</span></span>|<span data-ttu-id="fd273-144">conformes</span><span class="sxs-lookup"><span data-stu-id="fd273-144">{comp}</span></span>|
    |<span data-ttu-id="fd273-145">**Informations d'identification**</span><span class="sxs-lookup"><span data-stu-id="fd273-145">**Credential**</span></span>|<span data-ttu-id="fd273-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="fd273-146">MachineCred</span></span>|
    |<span data-ttu-id="fd273-147">**Pour**</span><span class="sxs-lookup"><span data-stu-id="fd273-147">**For**</span></span>|<span data-ttu-id="fd273-148">Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd273-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="fd273-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="fd273-149">**Force**</span></span>|<span data-ttu-id="fd273-150">True</span><span class="sxs-lookup"><span data-stu-id="fd273-150">True</span></span>|
    |<span data-ttu-id="fd273-151">Wait</span><span class="sxs-lookup"><span data-stu-id="fd273-151">Wait</span></span>|<span data-ttu-id="fd273-152">True</span><span class="sxs-lookup"><span data-stu-id="fd273-152">True</span></span>|
    |<span data-ttu-id="fd273-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="fd273-153">PSComputerName</span></span>|<span data-ttu-id="fd273-154">{""}</span><span class="sxs-lookup"><span data-stu-id="fd273-154">{""}</span></span>|

13. <span data-ttu-id="fd273-155">Ajoutez une activité **GetWmiObject** à la séquence **JoinDomain** après l’activité **RestartComputer** .</span><span class="sxs-lookup"><span data-stu-id="fd273-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="fd273-156">Modifiez ses propriétés afin qu’elles soient identiques à celles de l’activité **GetWmiObject** précédente.</span><span class="sxs-lookup"><span data-stu-id="fd273-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="fd273-157">Lorsque vous avez terminé les procédures, la fenêtre de conception de Workflow doit ressembler à ceci.</span><span class="sxs-lookup"><span data-stu-id="fd273-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="fd273-158">![XAML JoinDomain dans le concepteur de flux de travail](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
    ![XAML JoinDomain dans le concepteur de workflow](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="fd273-158">![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span></span>