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
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067669"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="3a23c-102">Appel d’applets de commande et de scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="3a23c-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="3a23c-103">Une applet de commande peut appeler les autres applets de commande et les scripts à partir de l’entrée de la méthode de l’applet de commande de traitement.</span><span class="sxs-lookup"><span data-stu-id="3a23c-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="3a23c-104">Cela vous permet de vous permet d’ajouter la fonctionnalité d’applets de commande existantes et des scripts à votre applet de commande sans avoir à réécrire le code.</span><span class="sxs-lookup"><span data-stu-id="3a23c-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="3a23c-105">L’appel de méthode</span><span class="sxs-lookup"><span data-stu-id="3a23c-105">The Invoke Method</span></span>

<span data-ttu-id="3a23c-106">Toutes les applets de commande peuvent invoquer une cmdlet existante en appelant le [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode à partir d’une entrée de traitement de méthode, telle que [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), qui est remplacée par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3a23c-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="3a23c-107">Toutefois, vous pouvez appeler uniquement ces applets de commande qui dérivent directement de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="3a23c-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="3a23c-108">Vous ne pouvez pas appeler une applet de commande qui dérive de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="3a23c-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="3a23c-109">Le [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode a les variantes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3a23c-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="3a23c-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet de l’applet de commande et retourne une collection d’objets de type « T ».</span><span class="sxs-lookup"><span data-stu-id="3a23c-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="3a23c-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet de l’applet de commande et retourne un emumerator fortement typée.</span><span class="sxs-lookup"><span data-stu-id="3a23c-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="3a23c-112">Cette variante permet à l’utilisateur à utiliser les objets dans la collection pour effectuer des opérations personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3a23c-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="3a23c-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="3a23c-113">Examples</span></span>

|<span data-ttu-id="3a23c-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a23c-114">Example</span></span>|<span data-ttu-id="3a23c-115">Description</span><span class="sxs-lookup"><span data-stu-id="3a23c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a23c-116">Appel des applets de commande au sein d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="3a23c-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="3a23c-117">Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3a23c-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="3a23c-118">Appel de Scripts au sein d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="3a23c-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="3a23c-119">Cet exemple montre comment appeler un script qui est fourni à l’applet de commande à partir d’une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3a23c-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3a23c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a23c-120">See Also</span></span>

[<span data-ttu-id="3a23c-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a23c-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
