---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISESnippet
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028887"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="14bfb-103">Objet ISESnippet</span><span class="sxs-lookup"><span data-stu-id="14bfb-103">The ISESnippetObject</span></span>

<span data-ttu-id="14bfb-104">Un objet **ISESnippet** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="14bfb-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="14bfb-105">Les membres de la collection **$psISE.CurrentPowerShellTab.Snippets** sont tous des exemples d’objets **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="14bfb-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="14bfb-106">La façon la plus simple de créer un extrait de code est d’utiliser l’applet de commande [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="14bfb-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="14bfb-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="14bfb-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="14bfb-108">Auteur</span><span class="sxs-lookup"><span data-stu-id="14bfb-108">Author</span></span>

<span data-ttu-id="14bfb-109">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="14bfb-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="14bfb-110">Propriété en lecture seule qui obtient le nom de l’auteur de l’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="14bfb-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="14bfb-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="14bfb-111">CodeFragment</span></span>

<span data-ttu-id="14bfb-112">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="14bfb-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="14bfb-113">Propriété en lecture seule qui obtient le fragment de code à insérer dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="14bfb-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="14bfb-114">Raccourci</span><span class="sxs-lookup"><span data-stu-id="14bfb-114">Shortcut</span></span>

<span data-ttu-id="14bfb-115">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="14bfb-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="14bfb-116">Propriété en lecture seule qui obtient le raccourci clavier Windows associé à l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="14bfb-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="14bfb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14bfb-117">See Also</span></span>

- [<span data-ttu-id="14bfb-118">Objet ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="14bfb-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="14bfb-119">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="14bfb-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="14bfb-120">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="14bfb-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
