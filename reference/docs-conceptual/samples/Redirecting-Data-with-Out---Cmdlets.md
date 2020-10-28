---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Redirection de données à l’aide d’applets de commande Out
description: Cet article explique comment utiliser les applets de commande qui gèrent la sortie dans PowerShell.
ms.openlocfilehash: 3a9e3b1ac06f5be4e6f3bbc52a15c4afb5b12cef
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500213"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="f6ac6-104">Redirection de données à l’aide d’applets de commande Out-\*</span><span class="sxs-lookup"><span data-stu-id="f6ac6-104">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="f6ac6-105">Windows PowerShell fournit plusieurs applets de commande qui vous permettent de contrôler directement la sortie de données.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-105">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="f6ac6-106">Ces applets de commande partagent deux caractéristiques importantes.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-106">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="f6ac6-107">Tout d’abord, elles transforment généralement les données en une forme de texte.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-107">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="f6ac6-108">Elles opèrent de la sorte, car elles envoient les données à des composants système qui requièrent une entrée de texte.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-108">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="f6ac6-109">Cela signifie qu’elles doivent représenter les objets sous forme de texte.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-109">This means they need to represent the objects as text.</span></span> <span data-ttu-id="f6ac6-110">C’est pourquoi le texte est mis en forme tel qu’il apparaît dans la fenêtre de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-110">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="f6ac6-111">Ensuite, ces applets de commande utilisent le verbe Windows PowerShell **Out** , car elles envoient des informations de Windows PowerShell vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-111">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="f6ac6-112">L’applet de commande **Out-Host** ne fait pas exception : l’affichage de la fenêtre hôte se trouve en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-112">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="f6ac6-113">Ceci est important car, lorsque des données sont envoyées hors de Windows PowerShell, elles sont réellement supprimées.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-113">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="f6ac6-114">Vous pouvez le constater si vous tentez de créer un pipeline qui pagine les données vers la fenêtre hôte, puis tentez d’appliquer une mise en forme de liste, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-114">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="f6ac6-115">Vous pouvez vous attendre à ce que la commande affiche des pages d’informations sur le processus sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-115">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="f6ac6-116">Au lieu de cela, elle affiche la liste tabulaire par défaut :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-116">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="f6ac6-117">L’applet de commande **Out-Host** envoyant les données directement à la console, la commande **Format-List** ne reçoit jamais rien à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-117">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="f6ac6-118">La façon correcte de structurer cette commande consiste à placer l’applet de commande **Out-Host** à la fin du pipeline, comme illustré ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-118">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="f6ac6-119">Ainsi, les données du processus sont mises en forme de liste avant d’être paginées et affichées.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-119">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="f6ac6-120">Cela s’applique à toutes les applets de commande **Out** .</span><span class="sxs-lookup"><span data-stu-id="f6ac6-120">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="f6ac6-121">Une applet de commande **Out** doit toujours apparaître à la fin du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-121">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ac6-122">Toutes les applets de commande **Out** restituent la sortie en tant que texte, en utilisant la mise en forme applicable à la fenêtre de console, y compris les limites de longueur de ligne.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-122">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

## <a name="paging-console-output-out-host"></a><span data-ttu-id="f6ac6-123">Pagination de la sortie de la console (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="f6ac6-123">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="f6ac6-124">Par défaut, Windows PowerShell envoie les données à la fenêtre hôte, ce qui est exactement ce que fait l’applet de commande Out-Host.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-124">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="f6ac6-125">La principale utilisation de l’applet de commande Out-Host est la pagination des données, que nous avons abordée précédemment.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-125">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="f6ac6-126">Par exemple, la commande suivante utilise l’applet de commande Out-Host pour paginer la sortie de l’applet de commande Get-Command :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-126">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="f6ac6-127">Vous pouvez également utiliser la fonction **more** pour paginer les données.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-127">You can also use the **more** function to page data.</span></span> <span data-ttu-id="f6ac6-128">Dans Windows PowerShell, la fonction **more** appelle l’applet de commande **Out-Host -Paging** .</span><span class="sxs-lookup"><span data-stu-id="f6ac6-128">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging** .</span></span> <span data-ttu-id="f6ac6-129">La commande suivante illustre l’utilisation de la fonction **more** pour paginer la sortie de l’applet de commande Get-Command :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-129">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="f6ac6-130">Si vous incluez un ou plusieurs noms de fichiers en tant qu’arguments pour la fonction more, celle-ci lit les fichiers spécifiés et pagine leur contenu vers l’hôte :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-130">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a><span data-ttu-id="f6ac6-131">Ignorance de la sortie (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="f6ac6-131">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="f6ac6-132">L’applet de commande **Out-Null** est conçue pour ignorer toute entrée qu’elle reçoit.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-132">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="f6ac6-133">Cela est utile pour ignorer des données superflues que vous recevez suite à l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-133">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="f6ac6-134">Lorsque vous tapez la commande suivante, celle-ci ne retourne rien :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-134">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="f6ac6-135">L’applet de commande **Out-Null** n’ignore pas la sortie d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-135">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="f6ac6-136">Par exemple, si vous entrez la commande suivante, un message s’affiche vous informant que Windows PowerShell ne reconnaît pas « Is-NotACommand » :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-136">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a><span data-ttu-id="f6ac6-137">Impression de données (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="f6ac6-137">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="f6ac6-138">L’applet de commande **Out-Printer** permet d’imprimer des données.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-138">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="f6ac6-139">Si vous ne fournissez pas de nom d’imprimante, l’applet de commande **Out-Printer** utilise votre imprimante par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-139">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="f6ac6-140">Vous pouvez utiliser n’importe quelle imprimante Windows en spécifiant son nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-140">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="f6ac6-141">Vous n’avez pas besoin de mappage de port d’imprimante ou même d’une imprimante physique réelle.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-141">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="f6ac6-142">Par exemple, si les outils de Microsoft Office Document Imaging sont installés, vous pouvez envoyer les données vers un fichier image en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-142">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a><span data-ttu-id="f6ac6-143">Enregistrement de données (Out-File)</span><span class="sxs-lookup"><span data-stu-id="f6ac6-143">Saving Data (Out-File)</span></span>

<span data-ttu-id="f6ac6-144">Vous pouvez envoyer une sortie vers un fichier plutôt que vers la fenêtre de console en utilisant l’applet de commande **Out-File** .</span><span class="sxs-lookup"><span data-stu-id="f6ac6-144">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="f6ac6-145">La ligne de commande suivante envoie une liste de processus au fichier **C:\\temp\\processlist.txt**  :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-145">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt** :</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="f6ac6-146">Les résultats de l’utilisation de l’applet de commande **Out-File** peuvent différer de ce que vous attendez si vous êtes habitué à la redirection de sortie traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-146">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="f6ac6-147">Pour comprendre le comportement de l’applet de commande **Out-File** , vous devez connaître le contexte dans lequel elle opère.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-147">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="f6ac6-148">Par défaut, l’applet de commande **Out-File** crée un fichier Unicode.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-148">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="f6ac6-149">Il s’agit de la meilleure option par défaut sur le long terme, mais elle signifie que les outils qui attendent des fichiers ASCII ne fonctionnent pas correctement avec le format de sortie par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-149">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="f6ac6-150">Vous pouvez modifier le format de sortie par défaut en ASCII à l’aide du paramètre **Encoding** :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-150">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="f6ac6-151">L’applet de commande **Out-File** met en forme le contenu du fichier pour qu’il ressemble à une sortie de la console.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-151">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="f6ac6-152">Cela a pour effet que, dans la plupart des cas, la sortie est tronquée comme dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-152">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="f6ac6-153">Par exemple, si vous exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-153">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="f6ac6-154">La sortie se présente ainsi :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-154">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="f6ac6-155">Pour obtenir une sortie qui ne force pas de retour automatique à la ligne pour correspondre à la largeur de l’écran, vous pouvez utiliser le paramètre **Width** pour spécifier une largeur de ligne.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-155">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="f6ac6-156">Étant donné que le paramètre **Width** est un entier 32 bits, il peut atteindre la valeur de 2147483647.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-156">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="f6ac6-157">Pour définir la largeur de ligne sur cette valeur maximale, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f6ac6-157">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="f6ac6-158">L’applet de commande **Out-File** est particulièrement utile si vous souhaitez enregistrer la sortie telle qu’elle s’afficherait sur la console.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-158">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="f6ac6-159">Afin de mieux contrôler le format de sortie, vous avez besoin d’outils plus avancés.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-159">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="f6ac6-160">Nous allons les examiner dans le chapitre suivant, en même temps que certains détails sur la manipulation des objets.</span><span class="sxs-lookup"><span data-stu-id="f6ac6-160">We will look at those in the next chapter, along with some details about object manipulation.</span></span>
