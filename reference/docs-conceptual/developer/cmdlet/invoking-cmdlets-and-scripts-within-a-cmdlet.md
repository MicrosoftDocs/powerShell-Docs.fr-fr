---
ms.date: 09/13/2016
ms.topic: reference
title: Appel d’applets de commande et de scripts dans une applet de commande
description: Appel d’applets de commande et de scripts dans une applet de commande
ms.openlocfilehash: 246c61661f2d290e7e7ac62a8ad303b05bdc7582
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652654"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="860ca-103">Appel d’applets de commande et de scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="860ca-103">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="860ca-104">Une applet de commande peut appeler d’autres applets de commande et scripts à partir de la méthode de traitement d’entrée de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="860ca-104">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="860ca-105">Cela vous permet d’ajouter les fonctionnalités des applets de commande et des scripts existants à votre applet de commande sans avoir à réécrire le code.</span><span class="sxs-lookup"><span data-stu-id="860ca-105">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="860ca-106">La méthode Invoke</span><span class="sxs-lookup"><span data-stu-id="860ca-106">The Invoke Method</span></span>

<span data-ttu-id="860ca-107">Toutes les applets de commande peuvent appeler une applet de commande existante en appelant la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) de commande à partir d’une méthode de traitement d’entrée, telle que [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), qui est remplacée par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="860ca-107">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="860ca-108">Toutefois, vous pouvez appeler uniquement les applets de commande qui dérivent directement de la classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande.</span><span class="sxs-lookup"><span data-stu-id="860ca-108">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="860ca-109">Vous ne pouvez pas appeler une applet de commande qui dérive de la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="860ca-109">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="860ca-110">La méthode [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) contient les variantes suivantes.</span><span class="sxs-lookup"><span data-stu-id="860ca-110">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="860ca-111">[System. Management. Automation. applet de commande. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet d’applet de commande et retourne une collection d’objets de type « T ».</span><span class="sxs-lookup"><span data-stu-id="860ca-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="860ca-112">[System. Management. Automation. applet de commande. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet cmdlet et retourne un emumerator fortement typé.</span><span class="sxs-lookup"><span data-stu-id="860ca-112">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="860ca-113">Cette variante permet à l’utilisateur d’utiliser les objets de la collection pour effectuer des opérations personnalisées.</span><span class="sxs-lookup"><span data-stu-id="860ca-113">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="860ca-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="860ca-114">Examples</span></span>

|<span data-ttu-id="860ca-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="860ca-115">Example</span></span>|<span data-ttu-id="860ca-116">Description</span><span class="sxs-lookup"><span data-stu-id="860ca-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="860ca-117">Appel d’applets de commande dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="860ca-117">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="860ca-118">Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="860ca-118">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="860ca-119">Appel de scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="860ca-119">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="860ca-120">Cet exemple montre comment appeler un script fourni à l’applet de commande à partir d’une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="860ca-120">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="860ca-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="860ca-121">See Also</span></span>

[<span data-ttu-id="860ca-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="860ca-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
