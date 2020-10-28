---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Autres objets de script utiles
description: Cet article décrit les objets qui fournissent des fonctionnalités de script supplémentaires dans Windows PowerShell ISE.
ms.openlocfilehash: c20daa0045bc07b1f21aafa42a80ce7c47ee7331
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500264"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="8e9db-104">Autres objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="8e9db-104">Other Useful Scripting Objects</span></span>

<span data-ttu-id="8e9db-105">Les objets suivants fournissent des fonctionnalités de script supplémentaires dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8e9db-105">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="8e9db-106">Ils ne sont pas inclus dans la hiérarchie **$psISE** .</span><span class="sxs-lookup"><span data-stu-id="8e9db-106">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="8e9db-107">Objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="8e9db-107">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="8e9db-108">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="8e9db-108">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="8e9db-109">Il existe certaines restrictions sur la façon dont Windows PowerShell ISE interagit avec les applications de console.</span><span class="sxs-lookup"><span data-stu-id="8e9db-109">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="8e9db-110">Une commande ou un script d’automatisation qui nécessite l’intervention de l’utilisateur peut ne pas fonctionner de la même façon qu’à partir de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e9db-110">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="8e9db-111">Vous pouvez empêcher l’exécution de ces commandes ou scripts dans le volet Commande de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8e9db-111">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="8e9db-112">L’objet **$psUnsupportedConsoleApplications** conserve la liste de ces commandes.</span><span class="sxs-lookup"><span data-stu-id="8e9db-112">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="8e9db-113">Si vous essayez d’exécuter les commandes de cette liste, vous obtenez un message indiquant qu’elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="8e9db-113">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="8e9db-114">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="8e9db-114">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="8e9db-115">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="8e9db-115">$psLocalHelp</span></span>

<span data-ttu-id="8e9db-116">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des rubriques d’aide et leurs liens correspondants dans le fichier d’aide HTML compilé local.</span><span class="sxs-lookup"><span data-stu-id="8e9db-116">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="8e9db-117">Il est utilisé pour localiser l’aide locale d’une rubrique particulière.</span><span class="sxs-lookup"><span data-stu-id="8e9db-117">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="8e9db-118">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="8e9db-118">You can add or delete topics from this list.</span></span> <span data-ttu-id="8e9db-119">L’exemple de code suivant illustre certaines paires clé-valeur contenues dans `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="8e9db-119">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```Output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="8e9db-120">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="8e9db-120">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="8e9db-121">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="8e9db-121">$psOnlineHelp</span></span>

<span data-ttu-id="8e9db-122">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des titres de rubriques d’aide et leurs URL externes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="8e9db-122">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="8e9db-123">Il est utilisé pour localiser l’aide d’une rubrique particulière sur le web.</span><span class="sxs-lookup"><span data-stu-id="8e9db-123">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="8e9db-124">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="8e9db-124">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```Output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="8e9db-125">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="8e9db-125">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="8e9db-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e9db-126">See Also</span></span>

[<span data-ttu-id="8e9db-127">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8e9db-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
