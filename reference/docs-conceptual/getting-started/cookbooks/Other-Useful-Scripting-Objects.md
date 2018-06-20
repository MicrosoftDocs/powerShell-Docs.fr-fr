---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Autres objets de script utiles
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949823"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="0d6d8-103">Autres objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="0d6d8-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="0d6d8-104">Les objets suivants fournissent des fonctionnalités de script supplémentaires dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="0d6d8-105">Ils ne sont pas inclus dans la hiérarchie **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="0d6d8-106">Objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="0d6d8-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="0d6d8-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="0d6d8-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="0d6d8-108">Il existe certaines restrictions sur la façon dont Windows PowerShell ISE interagit avec les applications de console.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="0d6d8-109">Une commande ou un script d’automatisation qui nécessite l’intervention de l’utilisateur peut ne pas fonctionner de la même façon qu’à partir de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="0d6d8-110">Vous pouvez empêcher l’exécution de ces commandes ou scripts dans le volet Commande de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="0d6d8-111">L’objet **$psUnsupportedConsoleApplications** conserve la liste de ces commandes.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="0d6d8-112">Si vous essayez d’exécuter les commandes de cette liste, vous obtenez un message indiquant qu’elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="0d6d8-113">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="0d6d8-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="0d6d8-114">$psLocalHelp</span></span>

<span data-ttu-id="0d6d8-115">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des rubriques d’aide et leurs liens correspondants dans le fichier d’aide HTML compilé local.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="0d6d8-116">Il est utilisé pour localiser l’aide locale d’une rubrique particulière.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="0d6d8-117">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="0d6d8-118">L’exemple de code suivant illustre certaines paires clé-valeur contenues dans **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="0d6d8-119">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="0d6d8-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="0d6d8-120">Clé : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="0d6d8-120">Key : Add-Computer</span></span>|<span data-ttu-id="0d6d8-121">Valeur : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="0d6d8-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="0d6d8-122">Clé : Add-Content</span><span class="sxs-lookup"><span data-stu-id="0d6d8-122">Key : Add-Content</span></span>|<span data-ttu-id="0d6d8-123">Valeur : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="0d6d8-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="0d6d8-124">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="0d6d8-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="0d6d8-125">$psOnlineHelp</span></span>

<span data-ttu-id="0d6d8-126">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des titres de rubriques d’aide et leurs URL externes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="0d6d8-127">Il est utilisé pour localiser l’aide d’une rubrique particulière sur le web.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="0d6d8-128">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="0d6d8-129">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="0d6d8-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="0d6d8-130">Clé : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="0d6d8-130">Key : Add-Computer</span></span>|<span data-ttu-id="0d6d8-131">Valeur : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="0d6d8-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="0d6d8-132">Clé : Add-Content</span><span class="sxs-lookup"><span data-stu-id="0d6d8-132">Key : Add-Content</span></span>|<span data-ttu-id="0d6d8-133">Valeur : http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="0d6d8-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="0d6d8-134">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="0d6d8-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="0d6d8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d6d8-135">See Also</span></span>

- [<span data-ttu-id="0d6d8-136">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0d6d8-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)