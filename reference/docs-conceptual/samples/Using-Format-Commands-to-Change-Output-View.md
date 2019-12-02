---
ms.date: 11/22/2019
keywords: powershell,applet de commande
title: Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417587"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="8443a-103">Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie</span><span class="sxs-lookup"><span data-stu-id="8443a-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="8443a-104">PowerShell dispose d’un ensemble d’applets de commande qui vous permettent de contrôler la façon dont les propriétés s’affichent pour certains objets.</span><span class="sxs-lookup"><span data-stu-id="8443a-104">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="8443a-105">Le nom de toutes les applets de commande commence par `Format`.</span><span class="sxs-lookup"><span data-stu-id="8443a-105">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="8443a-106">Vous pouvez sélectionner les propriétés que vous voulez afficher.</span><span class="sxs-lookup"><span data-stu-id="8443a-106">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="8443a-107">Cet article décrit les applets de commande `Format-Wide`, `Format-List` et `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="8443a-107">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="8443a-108">Dans PowerShell, chaque type d’objet possède des propriétés qui sont utilisées par défaut si vous ne précisez celles qui doivent être affichées.</span><span class="sxs-lookup"><span data-stu-id="8443a-108">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="8443a-109">De même, chaque applet de commande utilise le même paramètre **Property** pour spécifier les propriétés à afficher.</span><span class="sxs-lookup"><span data-stu-id="8443a-109">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="8443a-110">Comme `Format-Wide` n’affiche qu’une seule propriété, son paramètre **Property** n’accepte qu’une seule valeur, mais les paramètres des propriétés de `Format-List` et `Format-Table` acceptent une liste de noms de propriétés.</span><span class="sxs-lookup"><span data-stu-id="8443a-110">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="8443a-111">Dans cet exemple, la sortie par défaut de l’applet de commande `Get-Process` montre qu’il y a deux instances d’Internet Explorer en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8443a-111">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="8443a-112">Par défaut, les objets **Process** affichent les propriétés présentées ici :</span><span class="sxs-lookup"><span data-stu-id="8443a-112">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="8443a-113">Utilisation de l’applet de commande Format-Wide pour une sortie d’élément unique</span><span class="sxs-lookup"><span data-stu-id="8443a-113">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="8443a-114">Par défaut, l’applet de commande `Format-Wide` affiche uniquement la propriété par défaut d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8443a-114">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="8443a-115">Les informations associées à chaque objet s’affichent dans une seule colonne :</span><span class="sxs-lookup"><span data-stu-id="8443a-115">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="8443a-116">Vous pouvez également spécifier une propriété autre que celle par défaut :</span><span class="sxs-lookup"><span data-stu-id="8443a-116">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="8443a-117">Contrôle de l’affichage de Format-Wide avec une colonne</span><span class="sxs-lookup"><span data-stu-id="8443a-117">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="8443a-118">La cmdlet `Format-Wide` ne permet d’afficher qu’une seule propriété à la fois.</span><span class="sxs-lookup"><span data-stu-id="8443a-118">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="8443a-119">Cela s’avère utile pour afficher des listes volumineuses dans plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="8443a-119">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="8443a-120">Utilisation de l’applet de commande Format-List pour un Affichage Liste</span><span class="sxs-lookup"><span data-stu-id="8443a-120">Using Format-List for a List View</span></span>

<span data-ttu-id="8443a-121">L’applet de commande `Format-List` affiche un objet sous forme de liste, chaque propriété étant étiquetée et affichée sur une ligne distincte :</span><span class="sxs-lookup"><span data-stu-id="8443a-121">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="8443a-122">Vous pouvez spécifier autant de propriétés que vous le souhaitez :</span><span class="sxs-lookup"><span data-stu-id="8443a-122">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="8443a-123">Obtention d’informations détaillées en utilisant l’applet de commande Format-List avec des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="8443a-123">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="8443a-124">L’applet de commande `Format-List` permet d’utiliser un caractère générique comme valeur de son paramètre **Property**.</span><span class="sxs-lookup"><span data-stu-id="8443a-124">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="8443a-125">Cela permet d’afficher des informations détaillées.</span><span class="sxs-lookup"><span data-stu-id="8443a-125">This lets you display detailed information.</span></span> <span data-ttu-id="8443a-126">Souvent, les objets contiennent plus d’informations qu’il n’en faut. C’est pourquoi, par défaut, PowerShell n’affiche pas les valeurs de toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="8443a-126">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="8443a-127">Pour afficher toutes les propriétés d’un objet, utilisez la commande `Format-List -Property *`.</span><span class="sxs-lookup"><span data-stu-id="8443a-127">To show all of properties of an object, use the `Format-List -Property *` command.</span></span> <span data-ttu-id="8443a-128">La commande suivante génère plus de 60 lignes de sortie pour un seul processus :</span><span class="sxs-lookup"><span data-stu-id="8443a-128">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="8443a-129">Bien que la commande `Format-List` soit utile pour afficher des détails, si vous voulez obtenir une vue d’ensemble d’une sortie qui comporte un grand nombre d’éléments, une simple vue tabulaire est souvent plus utile.</span><span class="sxs-lookup"><span data-stu-id="8443a-129">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="8443a-130">Utilisation de l’applet de commande Format-Table pour une sortie tabulaire</span><span class="sxs-lookup"><span data-stu-id="8443a-130">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="8443a-131">Si vous utilisez l’applet de commande `Format-Table` sans spécifier de noms de propriétés pour mettre en forme la sortie de la commande `Get-Process`, vous obtenez exactement la même sortie que si vous n’utilisiez pas d’applet de commande `Format`.</span><span class="sxs-lookup"><span data-stu-id="8443a-131">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="8443a-132">Par défaut, PowerShell affiche les objets **Process** dans un format tabulaire.</span><span class="sxs-lookup"><span data-stu-id="8443a-132">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="8443a-133">Amélioration de la sortie de l’applet de commande Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="8443a-133">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="8443a-134">Bien qu’une vue tabulaire soit utile pour afficher beaucoup d’informations, elle peut être difficile à interpréter si l’affichage est trop étroit pour les données.</span><span class="sxs-lookup"><span data-stu-id="8443a-134">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="8443a-135">Dans l’exemple précédent, la sortie est tronquée.</span><span class="sxs-lookup"><span data-stu-id="8443a-135">In the previous example, the output is truncated.</span></span> <span data-ttu-id="8443a-136">Si vous spécifiez le paramètre **AutoSize** quand vous exécutez la commande `Format-Table`, PowerShell calcule les largeurs des colonnes en fonction des données réelles affichées.</span><span class="sxs-lookup"><span data-stu-id="8443a-136">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="8443a-137">Les colonnes deviennent ainsi lisibles.</span><span class="sxs-lookup"><span data-stu-id="8443a-137">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="8443a-138">L’applet de commande `Format-Table` peut continuer de tronquer des données, mais cela ne se produit qu’à la fin de l’écran.</span><span class="sxs-lookup"><span data-stu-id="8443a-138">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="8443a-139">Les propriétés, à l’exception de la dernière affichée, disposent de la taille nécessaire pour que leur élément de données le plus long s’affiche correctement.</span><span class="sxs-lookup"><span data-stu-id="8443a-139">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="8443a-140">La commande `Format-Table` part du principe que les propriétés sont listées par ordre d’importance.</span><span class="sxs-lookup"><span data-stu-id="8443a-140">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="8443a-141">Elle tente donc d’afficher entièrement les propriétés les plus proches du début.</span><span class="sxs-lookup"><span data-stu-id="8443a-141">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="8443a-142">Si la commande `Format-Table` ne peut pas afficher toutes les propriétés, elle supprime certaines colonnes de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="8443a-142">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="8443a-143">Vous pouvez observer ce comportement dans l’exemple précédent de la propriété **DependentServices**.</span><span class="sxs-lookup"><span data-stu-id="8443a-143">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="8443a-144">Retour automatique à la ligne de la sortie de l’applet de commande Format-Table dans les colonnes (Wrap)</span><span class="sxs-lookup"><span data-stu-id="8443a-144">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="8443a-145">Vous pouvez forcer le retour automatique à la ligne des données `Format-Table` retournées en nombre dans leur colonne d’affichage en utilisant le paramètre **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="8443a-145">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="8443a-146">L’utilisation du paramètre **Wrap** ne produit pas nécessairement le résultat escomptés, car si vous ne spécifiez pas **AutoSize**, les paramètres par défaut sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="8443a-146">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="8443a-147">L’utilisation du paramètre **Wrap** par lui-même ne ralentit considérablement le traitement.</span><span class="sxs-lookup"><span data-stu-id="8443a-147">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="8443a-148">Cependant, si vous voulez mettre en forme une liste récursive de fichiers d’une structure d’annuaire volumineuse en utilisant le paramètre **AutoSize**, celui-ci tardera à afficher les premiers éléments de sortie et mobilisera beaucoup de mémoire.</span><span class="sxs-lookup"><span data-stu-id="8443a-148">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="8443a-149">Si vous n’êtes pas préoccupé par la charge du système, **AutoSize** fonctionne bien avec le paramètre **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="8443a-149">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="8443a-150">Les premières colonnes continuent d’utiliser la largeur nécessaire à l’affichage des éléments sur une même ligne, mais la colonne finale est réduite, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8443a-150">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="8443a-151">Il se peut que certaines colonnes ne s’affichent pas si vous spécifiez les colonnes les plus larges en premier.</span><span class="sxs-lookup"><span data-stu-id="8443a-151">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="8443a-152">Pour de meilleurs résultats, spécifiez les éléments de données les plus petits en premier.</span><span class="sxs-lookup"><span data-stu-id="8443a-152">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="8443a-153">Dans l’exemple suivant, les propriétés les plus larges sont spécifiées en premier.</span><span class="sxs-lookup"><span data-stu-id="8443a-153">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="8443a-154">Même avec le retour automatique à la ligne, la dernière colonne **Id** est omise :</span><span class="sxs-lookup"><span data-stu-id="8443a-154">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="8443a-155">Organisation de la sortie de table (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="8443a-155">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="8443a-156">Un autre paramètre utile pour le contrôle de la sortie tabulaire est **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="8443a-156">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="8443a-157">Des listes tabulaires plus longues en particulier peuvent être difficiles à comparer.</span><span class="sxs-lookup"><span data-stu-id="8443a-157">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="8443a-158">Le paramètre **GroupBy** groupe la sortie en fonction d’une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="8443a-158">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="8443a-159">Par exemple, nous pouvons grouper les services en fonction du paramètre **StartType** pour faciliter l’inspection, en omettant la valeur de **StartType** de la liste des propriétés :</span><span class="sxs-lookup"><span data-stu-id="8443a-159">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
