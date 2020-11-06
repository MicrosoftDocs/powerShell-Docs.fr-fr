---
ms.date: 08/11/2020
keywords: dsc,powershell,configuration,installation
title: Appel direct de méthodes de ressources DSC
description: L’applet de commande Invoke-DscResource peut être utilisée pour appeler les fonctions ou méthodes d’une ressource DSC. Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources.
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650997"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="be8b1-105">Appel direct de méthodes de ressources DSC</span><span class="sxs-lookup"><span data-stu-id="be8b1-105">Calling DSC resource methods directly</span></span>

> <span data-ttu-id="be8b1-106">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="be8b1-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="be8b1-107">Vous pouvez utiliser l’applet de commande [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) pour appeler directement les fonctions ou méthodes d’une ressource DSC (les fonctions `Get-TargetResource`, `Set-TargetResource` et `Test-TargetResource` d’une ressource basée sur MOF ou les méthodes **Get** , **Set** et **Test** d’une ressource basée sur la classe).</span><span class="sxs-lookup"><span data-stu-id="be8b1-107">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get** , **Set** , and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="be8b1-108">Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources.</span><span class="sxs-lookup"><span data-stu-id="be8b1-108">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="be8b1-109">Dans PowerShell 7.0+, `Invoke-DscResource` ne prend plus en charge l’appel des ressources DSC WMI.</span><span class="sxs-lookup"><span data-stu-id="be8b1-109">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="be8b1-110">Sont incluses les ressources **File** et **Log** dans **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="be8b1-110">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="be8b1-111">Cette applet de commande est généralement utilisée avec une propriété de métaconfiguration `refreshMode = 'Disabled'`, mais vous pouvez l’utiliser quelle que soit la valeur de **refreshMode**.</span><span class="sxs-lookup"><span data-stu-id="be8b1-111">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="be8b1-112">Lors de l’appel de l’applet de commande `Invoke-DscResource`, vous spécifiez la méthode ou fonction à appeler à l’aide du paramètre **Method**.</span><span class="sxs-lookup"><span data-stu-id="be8b1-112">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="be8b1-113">Vous spécifiez les propriétés de la ressource en passant une table de hachage comme valeur du paramètre **Property**.</span><span class="sxs-lookup"><span data-stu-id="be8b1-113">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="be8b1-114">Voici quelques exemples d’appels directs de méthodes de ressources :</span><span class="sxs-lookup"><span data-stu-id="be8b1-114">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="be8b1-115">S’assurer de la présence d’un fichier</span><span class="sxs-lookup"><span data-stu-id="be8b1-115">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="be8b1-116">Tester la présence d’un fichier</span><span class="sxs-lookup"><span data-stu-id="be8b1-116">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="be8b1-117">Obtenir le contenu du fichier</span><span class="sxs-lookup"><span data-stu-id="be8b1-117">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> <span data-ttu-id="be8b1-118">l’appel direct de méthodes de ressources composites n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="be8b1-118">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="be8b1-119">Appelez plutôt les ressources sous-jacentes qui forment la ressource composite.</span><span class="sxs-lookup"><span data-stu-id="be8b1-119">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="be8b1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be8b1-120">See Also</span></span>

- [<span data-ttu-id="be8b1-121">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="be8b1-121">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="be8b1-122">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="be8b1-122">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="be8b1-123">Débogage des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="be8b1-123">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
