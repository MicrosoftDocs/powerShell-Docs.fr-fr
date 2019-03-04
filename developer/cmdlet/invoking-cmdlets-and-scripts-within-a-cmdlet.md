---
title: Appel des applets de commande et Scripts au sein d’une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855185"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="efb8e-102">Appel d’applets de commande et de scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="efb8e-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="efb8e-103">Une applet de commande peut appeler les autres applets de commande et les scripts à partir de l’entrée de la méthode de l’applet de commande de traitement.</span><span class="sxs-lookup"><span data-stu-id="efb8e-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="efb8e-104">Cela vous permet de vous permet d’ajouter la fonctionnalité d’applets de commande existantes et des scripts à votre applet de commande sans avoir à réécrire le code.</span><span class="sxs-lookup"><span data-stu-id="efb8e-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="efb8e-105">L’appel de méthode</span><span class="sxs-lookup"><span data-stu-id="efb8e-105">The Invoke Method</span></span>

<span data-ttu-id="efb8e-106">Toutes les applets de commande peuvent invoquer une cmdlet existante en appelant le [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode à partir d’une entrée de traitement de méthode, telle que [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), qui est remplacée par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="efb8e-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="efb8e-107">Toutefois, vous pouvez appeler uniquement ces applets de commande qui dérivent directement de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="efb8e-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="efb8e-108">Vous ne pouvez pas appeler une applet de commande qui dérive de la [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="efb8e-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="efb8e-109">Le [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode a les variantes suivantes.</span><span class="sxs-lookup"><span data-stu-id="efb8e-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="efb8e-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet de l’applet de commande et retourne une collection d’objets de type « T ».</span><span class="sxs-lookup"><span data-stu-id="efb8e-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="efb8e-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet de l’applet de commande et retourne un emumerator fortement typée.</span><span class="sxs-lookup"><span data-stu-id="efb8e-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="efb8e-112">Cette variante permet à l’utilisateur à utiliser les objets dans la collection pour effectuer des opérations personnalisées.</span><span class="sxs-lookup"><span data-stu-id="efb8e-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="efb8e-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="efb8e-113">Examples</span></span>

|<span data-ttu-id="efb8e-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="efb8e-114">Example</span></span>|<span data-ttu-id="efb8e-115">Description</span><span class="sxs-lookup"><span data-stu-id="efb8e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="efb8e-116">Appel des applets de commande au sein d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="efb8e-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="efb8e-117">Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="efb8e-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="efb8e-118">Appel de Scripts au sein d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="efb8e-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="efb8e-119">Cet exemple montre comment appeler un script qui est fourni à l’applet de commande à partir d’une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="efb8e-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="efb8e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efb8e-120">See Also</span></span>

[<span data-ttu-id="efb8e-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="efb8e-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
