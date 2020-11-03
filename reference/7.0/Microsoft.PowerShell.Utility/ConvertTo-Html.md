---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 21ef51476ccee8efc5c7c13d273ef8a7811f33c4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205918"
---
# <span data-ttu-id="9be0d-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="9be0d-103">ConvertTo-Html</span></span>

## <span data-ttu-id="9be0d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9be0d-104">SYNOPSIS</span></span>
<span data-ttu-id="9be0d-105">Convertit les objets .NET en code HTML qui peut être affiché dans un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="9be0d-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="9be0d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9be0d-106">SYNTAX</span></span>

### <span data-ttu-id="9be0d-107">Page (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9be0d-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="9be0d-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="9be0d-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="9be0d-109">Description</span><span class="sxs-lookup"><span data-stu-id="9be0d-109">DESCRIPTION</span></span>

<span data-ttu-id="9be0d-110">L' `ConvertTo-Html` applet de commande convertit les objets .net en HTML qui peuvent être affichés dans un navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="9be0d-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="9be0d-111">Vous pouvez utiliser cette applet de commande pour afficher la sortie d'une commande dans une page web.</span><span class="sxs-lookup"><span data-stu-id="9be0d-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="9be0d-112">Vous pouvez utiliser les paramètres de `ConvertTo-Html` pour sélectionner des propriétés d’objet, pour spécifier un format de table ou de liste, pour spécifier le titre de la page HTML, pour ajouter du texte avant et après l’objet et pour retourner uniquement le fragment de table ou de liste, au lieu d’une page DTD stricte.</span><span class="sxs-lookup"><span data-stu-id="9be0d-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="9be0d-113">Lorsque vous envoyez plusieurs objets à `ConvertTo-Html` , PowerShell crée la table (ou la liste) en fonction des propriétés du premier objet que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="9be0d-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="9be0d-114">Si les objets restants n'ont pas l'une des propriétés spécifiées, la valeur de propriété de cet objet est une cellule vide.</span><span class="sxs-lookup"><span data-stu-id="9be0d-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="9be0d-115">Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété ne sont pas incluses dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="9be0d-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="9be0d-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9be0d-116">EXAMPLES</span></span>

### <span data-ttu-id="9be0d-117">Exemple 1 : créer une page Web pour afficher la date</span><span class="sxs-lookup"><span data-stu-id="9be0d-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="9be0d-118">Cette commande crée une page HTML qui affiche les propriétés de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="9be0d-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="9be0d-119">Elle utilise le paramètre **InputObject** pour envoyer les résultats d’une `Get-Date` commande à l' `ConvertTo-Html` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9be0d-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="9be0d-120">Exemple 2 : créer une page Web pour afficher des alias PowerShell</span><span class="sxs-lookup"><span data-stu-id="9be0d-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="9be0d-121">Cette commande crée une page HTML qui répertorie les alias PowerShell dans la console active.</span><span class="sxs-lookup"><span data-stu-id="9be0d-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="9be0d-122">La commande utilise l' `Get-Alias` applet de commande pour récupérer les alias.</span><span class="sxs-lookup"><span data-stu-id="9be0d-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="9be0d-123">Elle utilise l’opérateur de pipeline ( `|` ) pour envoyer les alias à l’applet de commande `ConvertTo-Html` , qui crée la page html.</span><span class="sxs-lookup"><span data-stu-id="9be0d-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="9be0d-124">La commande utilise également l' `Out-File` applet de commande pour envoyer le code HTML au `aliases.htm` fichier.</span><span class="sxs-lookup"><span data-stu-id="9be0d-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="9be0d-125">Exemple 3 : créer une page Web pour afficher les événements PowerShell</span><span class="sxs-lookup"><span data-stu-id="9be0d-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="9be0d-126">Cette commande crée une page HTML appelée `pslog.htm` qui affiche les événements dans le journal des événements Windows PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9be0d-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="9be0d-127">Elle utilise l' `Get-EventLog` applet de commande pour récupérer les événements dans le journal Windows PowerShell, puis utilise l’opérateur de pipeline ( `|` ) pour envoyer les événements à l’applet de commande `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="9be0d-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="9be0d-128">La commande utilise également l' `Out-File` applet de commande pour envoyer le code HTML au `pslog.htm` fichier.</span><span class="sxs-lookup"><span data-stu-id="9be0d-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="9be0d-129">La commande utilise également l' `Out-File` applet de commande pour envoyer le code HTML au `pslog.htm` fichier.</span><span class="sxs-lookup"><span data-stu-id="9be0d-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="9be0d-130">Exemple 4 : créer une page Web pour afficher des processus</span><span class="sxs-lookup"><span data-stu-id="9be0d-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="9be0d-131">Ces commandes créent et ouvrent une page HTML qui répertorie le nom, le chemin d'accès et la société des processus sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9be0d-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="9be0d-132">La première commande utilise l' `Get-Process` applet de commande pour récupérer des objets qui représentent les processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9be0d-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="9be0d-133">La commande utilise l’opérateur de pipeline ( `|` ) pour envoyer les objets de processus à l’applet de commande `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="9be0d-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="9be0d-134">La commande utilise le paramètre **Property** pour sélectionner trois propriétés des objets Process à inclure dans la table.</span><span class="sxs-lookup"><span data-stu-id="9be0d-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="9be0d-135">La commande utilise le paramètre **title** pour spécifier un titre pour la page html.</span><span class="sxs-lookup"><span data-stu-id="9be0d-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="9be0d-136">La commande utilise également l' `Out-File` applet de commande pour envoyer le code html résultant vers un fichier nommé Proc.htm.</span><span class="sxs-lookup"><span data-stu-id="9be0d-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="9be0d-137">La deuxième commande utilise l' `Invoke-Item` applet de commande pour ouvrir le `Proc.htm` dans le navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9be0d-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="9be0d-138">Exemple 5 : créer une page Web pour afficher des objets de service</span><span class="sxs-lookup"><span data-stu-id="9be0d-138">Example 5: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

<span data-ttu-id="9be0d-139">Cette commande crée une page HTML des objets de service `Get-Service` retournées par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9be0d-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="9be0d-140">La commande utilise le paramètre **CssUri** pour spécifier une feuille de style en cascade pour la page html.</span><span class="sxs-lookup"><span data-stu-id="9be0d-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="9be0d-141">Le paramètre **CssUri** ajoute une `<link rel="stylesheet" type="text/css" href="test.css">` balise supplémentaire au code html résultant.</span><span class="sxs-lookup"><span data-stu-id="9be0d-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="9be0d-142">L'attribut HREF de la balise contient le nom de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="9be0d-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="9be0d-143">Exemple 6 : créer une page Web pour afficher des objets de service</span><span class="sxs-lookup"><span data-stu-id="9be0d-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="9be0d-144">Cette commande crée une page HTML des objets de service `Get-Service` retournées par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9be0d-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="9be0d-145">La commande utilise le paramètre **As** pour spécifier un format de liste.</span><span class="sxs-lookup"><span data-stu-id="9be0d-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="9be0d-146">L’applet `Out-File` de commande envoie le code html résultant au `Services.htm` fichier.</span><span class="sxs-lookup"><span data-stu-id="9be0d-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="9be0d-147">Exemple 7 : créer une table Web pour la date du jour</span><span class="sxs-lookup"><span data-stu-id="9be0d-147">Example 7: Create a web table for the current date</span></span>

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

<span data-ttu-id="9be0d-148">Cette commande utilise `ConvertTo-Html` pour générer une table HTML de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="9be0d-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="9be0d-149">La commande utilise l' `Get-Date` applet de commande pour récupérer la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="9be0d-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="9be0d-150">Elle utilise un opérateur de pipeline (|) pour envoyer les résultats à l’applet de commande `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="9be0d-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="9be0d-151">La `ConvertTo-Html` commande comprend le paramètre **fragment** , qui limite la sortie à une table HTML.</span><span class="sxs-lookup"><span data-stu-id="9be0d-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="9be0d-152">Par conséquent, les autres éléments d'une page HTML, tels que les balises `<HEAD>` et `<BODY>`, sont omis.</span><span class="sxs-lookup"><span data-stu-id="9be0d-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="9be0d-153">Exemple 8 : créer une page Web pour afficher les événements PowerShell</span><span class="sxs-lookup"><span data-stu-id="9be0d-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="9be0d-154">Cette commande utilise la `Get-EventLog` cmdlet pour récupérer des événements à partir du journal des événements Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9be0d-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="9be0d-155">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les événements à l’applet de commande `ConvertTo-Html` , qui convertit les événements au format html.</span><span class="sxs-lookup"><span data-stu-id="9be0d-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="9be0d-156">La `ConvertTo-Html` commande utilise le paramètre **Property** pour sélectionner uniquement les propriétés **ID** , **Level** et **Task** de l’événement.</span><span class="sxs-lookup"><span data-stu-id="9be0d-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="9be0d-157">Exemple 9 : créer une page Web pour afficher les services spécifiés</span><span class="sxs-lookup"><span data-stu-id="9be0d-157">Example 9: Create a web page to display specified services</span></span>

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

<span data-ttu-id="9be0d-158">Cette commande crée et ouvre une page Web qui affiche les services sur l’ordinateur qui commencent par. Elle utilise le **titre** , le **corps** , le **prétexte** et les paramètres **PostContent** de `ConvertTo-Html` pour personnaliser la sortie.</span><span class="sxs-lookup"><span data-stu-id="9be0d-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="9be0d-159">La première partie de la commande utilise l' `Get-Service` applet de commande pour obtenir les services sur l’ordinateur qui commencent par. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats à l’applet de commande `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="9be0d-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="9be0d-160">La commande utilise également l' `Out-File` applet de commande pour envoyer la sortie vers le fichier Services.htm.</span><span class="sxs-lookup"><span data-stu-id="9be0d-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="9be0d-161">Un point-virgule ( `;` ) termine la première commande et démarre une deuxième commande, qui utilise l' `Invoke-Item` applet de commande pour ouvrir le `Services.htm` fichier dans le navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9be0d-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="9be0d-162">Exemple 10 : définir les propriétés méta et le charset du code HTML</span><span class="sxs-lookup"><span data-stu-id="9be0d-162">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="9be0d-163">Cette commande crée le code HTML pour une page Web avec les balises méta pour l’actualisation, l’auteur et les mots clés.</span><span class="sxs-lookup"><span data-stu-id="9be0d-163">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="9be0d-164">Le jeu de caractères de la page est défini sur UTF-8</span><span class="sxs-lookup"><span data-stu-id="9be0d-164">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="9be0d-165">Exemple 11 : définir la DTD transitoire du code HTML sur XHTML</span><span class="sxs-lookup"><span data-stu-id="9be0d-165">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="9be0d-166">Cette commande définit le DOCTYPE du HTML retourné sur la DTD transitoire XHTML</span><span class="sxs-lookup"><span data-stu-id="9be0d-166">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="9be0d-167">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9be0d-167">PARAMETERS</span></span>

### <span data-ttu-id="9be0d-168">-As</span><span class="sxs-lookup"><span data-stu-id="9be0d-168">-As</span></span>

<span data-ttu-id="9be0d-169">Détermine si l'objet est dans un format de table ou de liste.</span><span class="sxs-lookup"><span data-stu-id="9be0d-169">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="9be0d-170">Les valeurs valides sont **table** et **List** .</span><span class="sxs-lookup"><span data-stu-id="9be0d-170">Valid values are **Table** and **List** .</span></span> <span data-ttu-id="9be0d-171">La valeur par défaut est **table** .</span><span class="sxs-lookup"><span data-stu-id="9be0d-171">The default value is **Table** .</span></span>

<span data-ttu-id="9be0d-172">La valeur de **table** génère une table HTML qui ressemble au format de table PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9be0d-172">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="9be0d-173">La ligne d'en-tête affiche les noms des propriétés.</span><span class="sxs-lookup"><span data-stu-id="9be0d-173">The header row displays the property names.</span></span> <span data-ttu-id="9be0d-174">Chaque ligne de la table représente un objet et affiche les valeurs de l'objet pour chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="9be0d-174">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="9be0d-175">La valeur **List** génère une table HTML à deux colonnes pour chaque objet qui ressemble au format de liste PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9be0d-175">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="9be0d-176">La première colonne affiche le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9be0d-176">The first column displays the property name.</span></span> <span data-ttu-id="9be0d-177">La deuxième colonne affiche la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9be0d-177">The second column displays the property value.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-178">-Corps</span><span class="sxs-lookup"><span data-stu-id="9be0d-178">-Body</span></span>

<span data-ttu-id="9be0d-179">Spécifie le texte à ajouter après la balise ouvrante `<BODY>`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-179">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="9be0d-180">Par défaut, il n'y a pas de texte à cette position.</span><span class="sxs-lookup"><span data-stu-id="9be0d-180">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-181">-Charset</span><span class="sxs-lookup"><span data-stu-id="9be0d-181">-Charset</span></span>

<span data-ttu-id="9be0d-182">Spécifie le texte à ajouter à la `<charset>` balise d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="9be0d-182">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="9be0d-183">Par défaut, il n'y a pas de texte à cette position.</span><span class="sxs-lookup"><span data-stu-id="9be0d-183">By default, there is no text in that position.</span></span>

<span data-ttu-id="9be0d-184">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9be0d-184">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-185">-CssUri</span><span class="sxs-lookup"><span data-stu-id="9be0d-185">-CssUri</span></span>

<span data-ttu-id="9be0d-186">Spécifie l'URI (Uniform Resource Identifier) de la feuille de style en cascade (CSS) qui est appliquée au fichier HTML.</span><span class="sxs-lookup"><span data-stu-id="9be0d-186">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="9be0d-187">L'URI est inclus dans un lien de feuille de style dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="9be0d-187">The URI is included in a style sheet link in the output.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-188">-Fragment</span><span class="sxs-lookup"><span data-stu-id="9be0d-188">-Fragment</span></span>

<span data-ttu-id="9be0d-189">Génère uniquement une table HTML.</span><span class="sxs-lookup"><span data-stu-id="9be0d-189">Generates only an HTML table.</span></span> <span data-ttu-id="9be0d-190">Les balises HTML, HEAD, TITLE et BODY sont omises.</span><span class="sxs-lookup"><span data-stu-id="9be0d-190">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-191">-Head</span><span class="sxs-lookup"><span data-stu-id="9be0d-191">-Head</span></span>

<span data-ttu-id="9be0d-192">Spécifie le contenu de la balise `<HEAD>`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-192">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="9be0d-193">La valeur par défaut est `<title\>HTML TABLE</title>`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-193">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="9be0d-194">Si vous utilisez le paramètre **Head** , le paramètre **title** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="9be0d-194">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9be0d-195">-InputObject</span></span>

<span data-ttu-id="9be0d-196">Spécifie les objets à représenter au format HTML.</span><span class="sxs-lookup"><span data-stu-id="9be0d-196">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="9be0d-197">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="9be0d-197">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="9be0d-198">Si vous utilisez ce paramètre pour envoyer plusieurs objets, tels que tous les services sur un ordinateur, `ConvertTo-Html` crée une table qui affiche les propriétés d’une collection ou d’un tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="9be0d-198">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="9be0d-199">Pour créer une table des objets individuels, utilisez l’opérateur de pipeline pour diriger les objets vers `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="9be0d-199">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-200">-Méta</span><span class="sxs-lookup"><span data-stu-id="9be0d-200">-Meta</span></span>

<span data-ttu-id="9be0d-201">Spécifie le texte à ajouter à la `<meta>` balise d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="9be0d-201">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="9be0d-202">Par défaut, il n'y a pas de texte à cette position.</span><span class="sxs-lookup"><span data-stu-id="9be0d-202">By default, there is no text in that position.</span></span>

<span data-ttu-id="9be0d-203">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9be0d-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-204">-PostContent</span><span class="sxs-lookup"><span data-stu-id="9be0d-204">-PostContent</span></span>

<span data-ttu-id="9be0d-205">Spécifie le texte à ajouter après la balise fermante `</TABLE>`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-205">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="9be0d-206">Par défaut, il n'y a pas de texte à cette position.</span><span class="sxs-lookup"><span data-stu-id="9be0d-206">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-207">-Prétexte</span><span class="sxs-lookup"><span data-stu-id="9be0d-207">-PreContent</span></span>

<span data-ttu-id="9be0d-208">Spécifie le texte à ajouter avant la balise ouvrante `<TABLE>`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-208">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="9be0d-209">Par défaut, il n'y a pas de texte à cette position.</span><span class="sxs-lookup"><span data-stu-id="9be0d-209">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-210">-Propriété</span><span class="sxs-lookup"><span data-stu-id="9be0d-210">-Property</span></span>

<span data-ttu-id="9be0d-211">Inclut les propriétés spécifiées des objets dans le code HTML.</span><span class="sxs-lookup"><span data-stu-id="9be0d-211">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="9be0d-212">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="9be0d-212">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="9be0d-213">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="9be0d-213">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="9be0d-214">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="9be0d-214">Valid key-value pairs are:</span></span>

- <span data-ttu-id="9be0d-215">Nom (ou étiquette)- `<string>` (ajouté dans PowerShell 6. x)</span><span class="sxs-lookup"><span data-stu-id="9be0d-215">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="9be0d-216">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="9be0d-216">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="9be0d-217">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="9be0d-217">FormatString - `<string>`</span></span>
- <span data-ttu-id="9be0d-218">Largeur- `<int32>` -doit être supérieur à `0`</span><span class="sxs-lookup"><span data-stu-id="9be0d-218">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="9be0d-219">Alignment : la valeur peut être `Left` , `Center` ou `Right`</span><span class="sxs-lookup"><span data-stu-id="9be0d-219">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="9be0d-220">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="9be0d-220">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-221">-Title</span><span class="sxs-lookup"><span data-stu-id="9be0d-221">-Title</span></span>

<span data-ttu-id="9be0d-222">Spécifie un titre pour le fichier HTML, c'est-à-dire le texte qui apparaît entre les balises `<TITLE>`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-222">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-223">-Transitionnel</span><span class="sxs-lookup"><span data-stu-id="9be0d-223">-Transitional</span></span>

<span data-ttu-id="9be0d-224">Change la Déclaration **DOCTYPE** en **DTD transitoire XHTML** , le **DOCTYPE** par défaut est **xhtml strict DTD** .</span><span class="sxs-lookup"><span data-stu-id="9be0d-224">Changes the **DOCTYPE** to **XHTML Transitional DTD** , Default **DOCTYPE** is **XHTML Strict DTD** .</span></span>

<span data-ttu-id="9be0d-225">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9be0d-225">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be0d-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9be0d-226">CommonParameters</span></span>

<span data-ttu-id="9be0d-227">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9be0d-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9be0d-228">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9be0d-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9be0d-229">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9be0d-229">INPUTS</span></span>

### <span data-ttu-id="9be0d-230">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9be0d-230">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9be0d-231">Vous pouvez diriger n’importe quel objet .NET vers `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="9be0d-231">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="9be0d-232">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9be0d-232">OUTPUTS</span></span>

### <span data-ttu-id="9be0d-233">Document System. String ou System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="9be0d-233">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="9be0d-234">`ConvertTo-Html` retourne une série de chaînes qui comprennent du code HTML valide.</span><span class="sxs-lookup"><span data-stu-id="9be0d-234">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="9be0d-235">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9be0d-235">NOTES</span></span>

<span data-ttu-id="9be0d-236">Pour utiliser cette applet de commande, dirigez un ou plusieurs objets vers l’applet de commande ou utilisez le paramètre **InputObject** pour spécifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="9be0d-236">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="9be0d-237">Quand l'entrée comporte plusieurs objets, la sortie de ces deux méthodes est assez différente.</span><span class="sxs-lookup"><span data-stu-id="9be0d-237">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="9be0d-238">Lorsque vous dirigez plusieurs objets vers une applet de commande, PowerShell envoie les objets à l’applet de commande, l’un après l’autre.</span><span class="sxs-lookup"><span data-stu-id="9be0d-238">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="9be0d-239">Par conséquent, `ConvertTo-Html` crée une table qui affiche les objets individuels.</span><span class="sxs-lookup"><span data-stu-id="9be0d-239">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="9be0d-240">Par exemple, si vous dirigez les processus sur un ordinateur vers `ConvertTo-Html` , la table résultante affiche tous les processus.</span><span class="sxs-lookup"><span data-stu-id="9be0d-240">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="9be0d-241">Quand vous utilisez le paramètre **InputObject** pour envoyer plusieurs objets, `ConvertTo-Html` reçoit ces objets sous la forme d’une collection ou d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="9be0d-241">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="9be0d-242">Par conséquent, l'applet de commande crée une table qui affiche le tableau et ses propriétés, pas les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="9be0d-242">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="9be0d-243">Par exemple, si vous utilisez **InputObject** pour envoyer les processus sur un ordinateur à `ConvertTo-Html` , la table résultante affiche un tableau d’objets et ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="9be0d-243">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="9be0d-244">Pour se conformer à la DTD strict XHTML, la balise DOCTYPE est modifiée en conséquence :</span><span class="sxs-lookup"><span data-stu-id="9be0d-244">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="9be0d-245">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9be0d-245">RELATED LINKS</span></span>

[<span data-ttu-id="9be0d-246">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="9be0d-246">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="9be0d-247">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="9be0d-247">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="9be0d-248">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="9be0d-248">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="9be0d-249">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="9be0d-249">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="9be0d-250">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="9be0d-250">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="9be0d-251">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="9be0d-251">Import-Clixml</span></span>](Import-Clixml.md)
