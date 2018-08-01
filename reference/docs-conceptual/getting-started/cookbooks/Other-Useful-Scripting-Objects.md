---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Autres objets de script utiles
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 04e94f858b568928b3910dd0ee85a912a6afc264
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268498"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="7ec83-103">Autres objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="7ec83-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="7ec83-104">Les objets suivants fournissent des fonctionnalités de script supplémentaires dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ec83-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="7ec83-105">Ils ne sont pas inclus dans la hiérarchie **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="7ec83-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="7ec83-106">Objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="7ec83-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="7ec83-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="7ec83-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="7ec83-108">Il existe certaines restrictions sur la façon dont Windows PowerShell ISE interagit avec les applications de console.</span><span class="sxs-lookup"><span data-stu-id="7ec83-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="7ec83-109">Une commande ou un script d’automatisation qui nécessite l’intervention de l’utilisateur peut ne pas fonctionner de la même façon qu’à partir de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ec83-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="7ec83-110">Vous pouvez empêcher l’exécution de ces commandes ou scripts dans le volet Commande de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ec83-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="7ec83-111">L’objet **$psUnsupportedConsoleApplications** conserve la liste de ces commandes.</span><span class="sxs-lookup"><span data-stu-id="7ec83-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="7ec83-112">Si vous essayez d’exécuter les commandes de cette liste, vous obtenez un message indiquant qu’elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="7ec83-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="7ec83-113">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="7ec83-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="7ec83-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="7ec83-114">$psLocalHelp</span></span>

<span data-ttu-id="7ec83-115">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des rubriques d’aide et leurs liens correspondants dans le fichier d’aide HTML compilé local.</span><span class="sxs-lookup"><span data-stu-id="7ec83-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="7ec83-116">Il est utilisé pour localiser l’aide locale d’une rubrique particulière.</span><span class="sxs-lookup"><span data-stu-id="7ec83-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="7ec83-117">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="7ec83-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="7ec83-118">L’exemple de code suivant illustre certaines paires clé-valeur contenues dans `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="7ec83-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="7ec83-119">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="7ec83-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="7ec83-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="7ec83-120">$psOnlineHelp</span></span>

<span data-ttu-id="7ec83-121">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des titres de rubriques d’aide et leurs URL externes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="7ec83-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="7ec83-122">Il est utilisé pour localiser l’aide d’une rubrique particulière sur le web.</span><span class="sxs-lookup"><span data-stu-id="7ec83-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="7ec83-123">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="7ec83-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="7ec83-124">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="7ec83-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="7ec83-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ec83-125">See Also</span></span>

[<span data-ttu-id="7ec83-126">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7ec83-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)