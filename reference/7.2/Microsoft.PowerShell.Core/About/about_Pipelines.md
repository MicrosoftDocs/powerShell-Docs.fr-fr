---
description: Combinaison de commandes dans des pipelines dans PowerShell
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: e4ae85fbbfe5232048a90e1fe4f62db3e95e5f1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598183"
---
# <a name="about-pipelines"></a><span data-ttu-id="bfac7-103">À propos des pipelines</span><span class="sxs-lookup"><span data-stu-id="bfac7-103">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="bfac7-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="bfac7-104">Short description</span></span>

<span data-ttu-id="bfac7-105">Combinaison de commandes dans des pipelines dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfac7-105">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="bfac7-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="bfac7-106">Long description</span></span>

<span data-ttu-id="bfac7-107">Un pipeline est une série de commandes connectées par des opérateurs de pipeline ( `|` ) (ASCII 124).</span><span class="sxs-lookup"><span data-stu-id="bfac7-107">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="bfac7-108">Chaque opérateur de pipeline envoie les résultats de la commande précédente à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="bfac7-108">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="bfac7-109">La sortie de la première commande peut être envoyée pour traitement comme entrée à la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="bfac7-109">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="bfac7-110">Et cette sortie peut être envoyée à une autre commande.</span><span class="sxs-lookup"><span data-stu-id="bfac7-110">And that output can be sent to yet another command.</span></span> <span data-ttu-id="bfac7-111">Le résultat est une chaîne de commande complexe ou un _pipeline_ qui est composé d’une série de commandes simples.</span><span class="sxs-lookup"><span data-stu-id="bfac7-111">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="bfac7-112">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="bfac7-112">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="bfac7-113">Dans cet exemple, les objets qui `Command-1` émettent sont envoyés à `Command-2` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-113">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="bfac7-114">`Command-2` traite les objets et les envoie à `Command-3` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-114">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="bfac7-115">`Command-3` traite les objets et les envoie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-115">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="bfac7-116">Étant donné qu’il n’y a plus de commandes dans le pipeline, les résultats s’affichent dans la console.</span><span class="sxs-lookup"><span data-stu-id="bfac7-116">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="bfac7-117">Dans un pipeline, les commandes sont traitées dans l’ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="bfac7-117">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="bfac7-118">Le traitement est géré comme une opération unique et la sortie est affichée au fur et à mesure de sa génération.</span><span class="sxs-lookup"><span data-stu-id="bfac7-118">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="bfac7-119">Voici un exemple simple.</span><span class="sxs-lookup"><span data-stu-id="bfac7-119">Here is a simple example.</span></span> <span data-ttu-id="bfac7-120">La commande suivante obtient le processus du bloc-notes, puis l’arrête.</span><span class="sxs-lookup"><span data-stu-id="bfac7-120">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="bfac7-121">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="bfac7-121">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="bfac7-122">La première commande utilise l' `Get-Process` applet de commande pour récupérer un objet représentant le processus du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="bfac7-122">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="bfac7-123">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet processus à l’applet de commande `Stop-Process` , qui arrête le processus Notepad.</span><span class="sxs-lookup"><span data-stu-id="bfac7-123">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="bfac7-124">Notez que la `Stop-Process` commande n’a pas de paramètre **Name** ou **ID** pour spécifier le processus, car le processus spécifié est soumis via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-124">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="bfac7-125">Cet exemple de pipeline obtient les fichiers texte dans le répertoire actif, sélectionne uniquement les fichiers dont la longueur est supérieure à 10 000 octets, les trie par longueur et affiche le nom et la longueur de chaque fichier dans une table.</span><span class="sxs-lookup"><span data-stu-id="bfac7-125">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="bfac7-126">Ce pipeline se compose de quatre commandes dans l’ordre spécifié.</span><span class="sxs-lookup"><span data-stu-id="bfac7-126">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="bfac7-127">L’illustration suivante montre la sortie de chaque commande telle qu’elle est transmise à la commande suivante dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-127">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a><span data-ttu-id="bfac7-128">Utilisation des pipelines</span><span class="sxs-lookup"><span data-stu-id="bfac7-128">Using pipelines</span></span>

<span data-ttu-id="bfac7-129">La plupart des applets de commande PowerShell sont conçues pour prendre en charge les pipelines.</span><span class="sxs-lookup"><span data-stu-id="bfac7-129">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="bfac7-130">Dans la plupart des cas, vous pouvez _diriger_ les résultats d’une applet de commande **obtenir** vers une autre applet de commande du même nom.</span><span class="sxs-lookup"><span data-stu-id="bfac7-130">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="bfac7-131">Par exemple, vous pouvez diriger la sortie de l' `Get-Service` applet de commande vers les `Start-Service` applets de commande ou `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-131">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="bfac7-132">Cet exemple de pipeline démarre le service WMI sur l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="bfac7-132">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="bfac7-133">Pour un autre exemple, vous pouvez diriger la sortie de `Get-Item` ou `Get-ChildItem` dans le fournisseur de Registre PowerShell vers l’applet de commande `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-133">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="bfac7-134">Cet exemple ajoute une nouvelle entrée de Registre, **NoOfEmployees**, avec une valeur de **8124**, à la clé de Registre **MyCompany** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-134">This example adds a new registry entry, **NoOfEmployees**, with a value of **8124**, to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="bfac7-135">La plupart des applets de commande utilitaires, telles que,,, `Get-Member` `Where-Object` `Sort-Object` `Group-Object` et `Measure-Object` sont utilisées presque exclusivement dans des pipelines.</span><span class="sxs-lookup"><span data-stu-id="bfac7-135">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="bfac7-136">Vous pouvez diriger tout type d’objet vers ces applets de commande.</span><span class="sxs-lookup"><span data-stu-id="bfac7-136">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="bfac7-137">Cet exemple montre comment trier tous les processus sur l’ordinateur en fonction du nombre de descripteurs ouverts dans chaque processus.</span><span class="sxs-lookup"><span data-stu-id="bfac7-137">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="bfac7-138">Vous pouvez diriger les objets vers les applets de commande de mise en forme, d’exportation et de sortie, telles que,,, `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` et `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-138">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="bfac7-139">Cet exemple montre comment utiliser l' `Format-List` applet de commande pour afficher la liste des propriétés d’un objet processus.</span><span class="sxs-lookup"><span data-stu-id="bfac7-139">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="bfac7-140">Avec un peu de pratique, vous constaterez que la combinaison de commandes simples dans des pipelines permet d’économiser du temps et de la saisie, et d’améliorer l’efficacité de vos scripts.</span><span class="sxs-lookup"><span data-stu-id="bfac7-140">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="bfac7-141">Fonctionnement des pipelines</span><span class="sxs-lookup"><span data-stu-id="bfac7-141">How pipelines work</span></span>

<span data-ttu-id="bfac7-142">Cette section explique comment les objets d’entrée sont liés aux paramètres d’applet de commande et traités lors de l’exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-142">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="bfac7-143">Accepte l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="bfac7-143">Accepts pipeline input</span></span>

<span data-ttu-id="bfac7-144">Pour prendre en charge le traitement en pipeline, l’applet de commande de réception doit avoir un paramètre qui accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-144">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="bfac7-145">Utilisez la `Get-Help` commande avec les options **Full** ou **Parameter** pour déterminer les paramètres d’une applet de commande acceptant l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-145">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="bfac7-146">Par exemple, pour déterminer les paramètres de l’applet de commande qui `Start-Service` accepte l’entrée de pipeline, tapez :</span><span class="sxs-lookup"><span data-stu-id="bfac7-146">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="bfac7-147">ou</span><span class="sxs-lookup"><span data-stu-id="bfac7-147">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="bfac7-148">L’aide de l' `Start-Service` applet de commande montre que seuls les paramètres **InputObject** et **Name** acceptent l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-148">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

<span data-ttu-id="bfac7-149">Lorsque vous envoyez des objets via le pipeline à `Start-Service` , PowerShell tente d’associer les objets aux paramètres **InputObject** et **Name** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-149">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="bfac7-150">Méthodes d’acceptation de l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="bfac7-150">Methods of accepting pipeline input</span></span>

<span data-ttu-id="bfac7-151">Les paramètres des applets de commande peuvent accepter l’entrée de pipeline de deux façons différentes :</span><span class="sxs-lookup"><span data-stu-id="bfac7-151">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="bfac7-152">**ByValue**: le paramètre accepte les valeurs qui correspondent au type .net attendu ou qui peuvent être converties en ce type.</span><span class="sxs-lookup"><span data-stu-id="bfac7-152">**ByValue**: The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="bfac7-153">Par exemple, le paramètre **Name** de `Start-Service` accepte les entrées de pipeline par valeur.</span><span class="sxs-lookup"><span data-stu-id="bfac7-153">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="bfac7-154">Il peut accepter des objets de chaîne ou des objets qui peuvent être convertis en chaînes.</span><span class="sxs-lookup"><span data-stu-id="bfac7-154">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="bfac7-155">**ByPropertyName**: le paramètre accepte l’entrée uniquement lorsque l’objet d’entrée a une propriété du même nom que le paramètre.</span><span class="sxs-lookup"><span data-stu-id="bfac7-155">**ByPropertyName**: The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="bfac7-156">Par exemple, le paramètre Name de `Start-Service` peut accepter des objets qui ont une propriété **Name** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-156">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="bfac7-157">Pour répertorier les propriétés d’un objet, dirigez-le vers `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-157">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="bfac7-158">Certains paramètres peuvent accepter des objets par nom de valeur ou de propriété, ce qui facilite l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-158">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="bfac7-159">Liaison de paramètres</span><span class="sxs-lookup"><span data-stu-id="bfac7-159">Parameter binding</span></span>

<span data-ttu-id="bfac7-160">Lorsque vous dirigez des objets d’une commande vers une autre commande, PowerShell tente d’associer les objets dirigés à un paramètre de l’applet de commande de réception.</span><span class="sxs-lookup"><span data-stu-id="bfac7-160">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="bfac7-161">Le composant de liaison de paramètre de PowerShell associe les objets d’entrée aux paramètres d’applet de commande en fonction des critères suivants :</span><span class="sxs-lookup"><span data-stu-id="bfac7-161">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="bfac7-162">Le paramètre doit accepter l’entrée d’un pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-162">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="bfac7-163">Le paramètre doit accepter le type d’objet envoyé ou un type qui peut être converti vers le type attendu.</span><span class="sxs-lookup"><span data-stu-id="bfac7-163">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="bfac7-164">Le paramètre n’a pas été utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="bfac7-164">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="bfac7-165">Par exemple, l' `Start-Service` applet de commande a plusieurs paramètres, mais seuls deux d’entre eux, **Name** et **InputObject** acceptent l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-165">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="bfac7-166">Le paramètre **Name** prend des chaînes et le paramètre **InputObject** prend des objets de service.</span><span class="sxs-lookup"><span data-stu-id="bfac7-166">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="bfac7-167">Par conséquent, vous pouvez diriger des chaînes, des objets de service et des objets avec des propriétés qui peuvent être converties en objets de service ou de chaîne.</span><span class="sxs-lookup"><span data-stu-id="bfac7-167">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="bfac7-168">PowerShell gère la liaison de paramètre aussi efficacement que possible.</span><span class="sxs-lookup"><span data-stu-id="bfac7-168">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="bfac7-169">Vous ne pouvez pas suggérer ou forcer PowerShell à établir une liaison avec un paramètre spécifique.</span><span class="sxs-lookup"><span data-stu-id="bfac7-169">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="bfac7-170">La commande échoue si PowerShell ne peut pas lier les objets redirigés.</span><span class="sxs-lookup"><span data-stu-id="bfac7-170">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="bfac7-171">Pour plus d’informations sur le dépannage des erreurs de liaison, consultez [examen des erreurs de pipeline](#investigating-pipeline-errors) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="bfac7-171">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="bfac7-172">Traitement une fois par heure</span><span class="sxs-lookup"><span data-stu-id="bfac7-172">One-at-a-time processing</span></span>

<span data-ttu-id="bfac7-173">La redirection d’objets vers une commande est très similaire à l’utilisation d’un paramètre de la commande pour envoyer les objets.</span><span class="sxs-lookup"><span data-stu-id="bfac7-173">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="bfac7-174">Examinons un exemple de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-174">Let's look at a pipeline example.</span></span> <span data-ttu-id="bfac7-175">Dans cet exemple, nous utilisons un pipeline pour afficher une table d’objets de service.</span><span class="sxs-lookup"><span data-stu-id="bfac7-175">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="bfac7-176">Fonctionnellement, cela revient à utiliser le paramètre **InputObject** de `Format-Table` pour envoyer la collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="bfac7-176">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="bfac7-177">Par exemple, nous pouvons enregistrer la collection de services dans une variable qui est passée à l’aide du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-177">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="bfac7-178">Ou nous pouvons incorporer la commande dans le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-178">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="bfac7-179">Toutefois, il existe une différence importante.</span><span class="sxs-lookup"><span data-stu-id="bfac7-179">However, there's an important difference.</span></span> <span data-ttu-id="bfac7-180">Lorsque vous dirigez plusieurs objets vers une commande, PowerShell les envoie un par un à la commande.</span><span class="sxs-lookup"><span data-stu-id="bfac7-180">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="bfac7-181">Lorsque vous utilisez un paramètre de commande, les objets sont envoyés sous la forme d’un objet de tableau unique.</span><span class="sxs-lookup"><span data-stu-id="bfac7-181">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="bfac7-182">Cette différence mineure a des conséquences significatives.</span><span class="sxs-lookup"><span data-stu-id="bfac7-182">This minor difference has significant consequences.</span></span>

<span data-ttu-id="bfac7-183">Lors de l’exécution d’un pipeline, PowerShell énumère automatiquement tout type qui implémente l' `IEnumerable` interface et envoie un à un les membres via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-183">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="bfac7-184">L’exception est `[hashtable]` , qui requiert un appel à la `GetEnumerator()` méthode.</span><span class="sxs-lookup"><span data-stu-id="bfac7-184">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="bfac7-185">Dans les exemples suivants, un tableau et une table de hachage sont dirigés vers l' `Measure-Object` applet de commande pour compter le nombre d’objets reçus à partir du pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-185">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="bfac7-186">Le tableau a plusieurs membres, et la table de hachage a plusieurs paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="bfac7-186">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="bfac7-187">Seul le tableau est énuméré un à la fois.</span><span class="sxs-lookup"><span data-stu-id="bfac7-187">Only the array is enumerated one at a time.</span></span>

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="bfac7-188">De même, si vous dirigez plusieurs objets de processus de l' `Get-Process` applet de commande vers l’applet de commande `Get-Member` , PowerShell envoie chaque objet de processus, un à la fois, à `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-188">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="bfac7-189">`Get-Member` affiche la classe .NET (type) des objets processus, ainsi que leurs propriétés et méthodes.</span><span class="sxs-lookup"><span data-stu-id="bfac7-189">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> <span data-ttu-id="bfac7-190">`Get-Member` élimine les doublons. par conséquent, si les objets sont tous du même type, il n’affiche qu’un seul type d’objet.</span><span class="sxs-lookup"><span data-stu-id="bfac7-190">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="bfac7-191">Toutefois, si vous utilisez le paramètre **InputObject** de `Get-Member` , `Get-Member` reçoit un tableau d’objets **System. Diagnostics. Process** comme une seule unité.</span><span class="sxs-lookup"><span data-stu-id="bfac7-191">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="bfac7-192">Elle affiche les propriétés d’un tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="bfac7-192">It displays the properties of an array of objects.</span></span> <span data-ttu-id="bfac7-193">(Notez le symbole de tableau ( `[]` ) après le nom du type **System. Object** .)</span><span class="sxs-lookup"><span data-stu-id="bfac7-193">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="bfac7-194">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="bfac7-194">For example,</span></span>

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

<span data-ttu-id="bfac7-195">Ce résultat n’est peut-être pas ce que vous souhaitiez.</span><span class="sxs-lookup"><span data-stu-id="bfac7-195">This result might not be what you intended.</span></span> <span data-ttu-id="bfac7-196">Mais une fois que vous l’avez compris, vous pouvez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="bfac7-196">But after you understand it, you can use it.</span></span> <span data-ttu-id="bfac7-197">Par exemple, tous les objets tableau ont une propriété **Count** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-197">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="bfac7-198">Vous pouvez l’utiliser pour compter le nombre de processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bfac7-198">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="bfac7-199">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="bfac7-199">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="bfac7-200">Il est important de se souvenir que les objets envoyés dans le pipeline sont remis un à la fois.</span><span class="sxs-lookup"><span data-stu-id="bfac7-200">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="bfac7-201">Examen des erreurs de pipeline</span><span class="sxs-lookup"><span data-stu-id="bfac7-201">Investigating pipeline errors</span></span>

<span data-ttu-id="bfac7-202">Lorsque PowerShell ne peut pas associer les objets dirigés à un paramètre de l’applet de commande de réception, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="bfac7-202">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="bfac7-203">Dans l’exemple suivant, nous essayons de déplacer une entrée de registre d’une clé de Registre vers une autre.</span><span class="sxs-lookup"><span data-stu-id="bfac7-203">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="bfac7-204">L' `Get-Item` applet de commande obtient le chemin d’accès de destination, qui est ensuite redirigé vers l’applet de commande `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-204">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="bfac7-205">La `Move-ItemProperty` commande spécifie le chemin d’accès actuel et le nom de l’entrée de Registre à déplacer.</span><span class="sxs-lookup"><span data-stu-id="bfac7-205">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="bfac7-206">La commande échoue et PowerShell affiche le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="bfac7-206">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="bfac7-207">Pour examiner, utilisez l' `Trace-Command` applet de commande pour suivre le composant de liaison de paramètre de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfac7-207">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="bfac7-208">L’exemple suivant effectue le suivi de la liaison de paramètre pendant l’exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-208">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="bfac7-209">Le paramètre **PSHost** affiche les résultats de la trace dans la console et le paramètre **filePath** envoie les résultats de la trace au `debug.txt` fichier pour référence ultérieure.</span><span class="sxs-lookup"><span data-stu-id="bfac7-209">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="bfac7-210">Les résultats de la trace sont longs, mais ils affichent les valeurs qui sont liées à l’applet de commande, `Get-Item` puis les valeurs nommées qui sont liées à l’applet de commande `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-210">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

<span data-ttu-id="bfac7-211">Enfin, il indique que la tentative de liaison du chemin d’accès au paramètre de **destination** de `Move-ItemProperty` a échoué.</span><span class="sxs-lookup"><span data-stu-id="bfac7-211">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

<span data-ttu-id="bfac7-212">Utilisez l' `Get-Help` applet de commande pour afficher les attributs du paramètre de **destination** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-212">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

<span data-ttu-id="bfac7-213">Les résultats montrent que la **destination** prend uniquement l’entrée de pipeline « par nom de propriété ».</span><span class="sxs-lookup"><span data-stu-id="bfac7-213">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="bfac7-214">Par conséquent, l’objet dirigé doit avoir une propriété nommée **destination**.</span><span class="sxs-lookup"><span data-stu-id="bfac7-214">Therefore, the piped object must have a property named **Destination**.</span></span>

<span data-ttu-id="bfac7-215">Utilisez `Get-Member` pour afficher les propriétés de l’objet provenant de `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="bfac7-215">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="bfac7-216">La sortie indique que l’élément est un objet **Microsoft. Win32. RegistryKey** qui n’a pas de propriété de **destination** .</span><span class="sxs-lookup"><span data-stu-id="bfac7-216">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="bfac7-217">Cela explique pourquoi la commande a échoué.</span><span class="sxs-lookup"><span data-stu-id="bfac7-217">That explains why the command failed.</span></span>

<span data-ttu-id="bfac7-218">Le paramètre **path** accepte l’entrée de pipeline par nom ou par valeur.</span><span class="sxs-lookup"><span data-stu-id="bfac7-218">The **Path** parameter accepts pipeline input by name or by value.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

<span data-ttu-id="bfac7-219">Pour corriger la commande, nous devons spécifier la destination dans l' `Move-ItemProperty` applet de commande et utiliser `Get-Item` pour obtenir le **chemin d’accès** de l’élément que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="bfac7-219">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="bfac7-220">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="bfac7-220">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="bfac7-221">Continuation de ligne intrinsèque</span><span class="sxs-lookup"><span data-stu-id="bfac7-221">Intrinsic line continuation</span></span>

<span data-ttu-id="bfac7-222">Comme nous l’avons déjà vu, un pipeline est une série de commandes connectées par des opérateurs de pipeline ( `|` ), généralement écrits sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="bfac7-222">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="bfac7-223">Toutefois, pour des raisons de lisibilité, PowerShell vous permet de fractionner le pipeline sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="bfac7-223">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="bfac7-224">Lorsqu’un opérateur de canal est le dernier jeton de la ligne, l’analyseur PowerShell joint la ligne suivante à la commande actuelle pour poursuivre la construction du pipeline.</span><span class="sxs-lookup"><span data-stu-id="bfac7-224">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="bfac7-225">Par exemple, le pipeline à ligne unique suivant :</span><span class="sxs-lookup"><span data-stu-id="bfac7-225">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="bfac7-226">peut être écrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="bfac7-226">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="bfac7-227">Les espaces de début sur les lignes suivantes ne sont pas significatifs.</span><span class="sxs-lookup"><span data-stu-id="bfac7-227">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="bfac7-228">La mise en retrait améliore la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="bfac7-228">The indentation enhances readability.</span></span>

<span data-ttu-id="bfac7-229">PowerShell 7 ajoute la prise en charge de la continuation des pipelines avec le caractère de pipeline au début d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="bfac7-229">PowerShell 7 adds support for continuation of pipelines with the pipeline character at the beginning of a line.</span></span> <span data-ttu-id="bfac7-230">Les exemples suivants montrent comment utiliser cette nouvelle fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="bfac7-230">The following examples show how you could use this new functionality.</span></span>

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> <span data-ttu-id="bfac7-231">Lorsque vous travaillez de manière interactive dans l’interpréteur de commandes, collez le code avec des pipelines au début d’une ligne uniquement lorsque vous utilisez <kbd>CTRL</kbd> + <kbd>V</kbd> pour coller.</span><span class="sxs-lookup"><span data-stu-id="bfac7-231">When working interactively in the shell, pasting code with pipelines at the beginning of a line only when using <kbd>Ctrl</kbd>+<kbd>V</kbd> to paste.</span></span>
> <span data-ttu-id="bfac7-232">Cliquez avec le bouton droit sur collage opérations insérer les lignes une par une.</span><span class="sxs-lookup"><span data-stu-id="bfac7-232">Right-click paste operations insert the lines one at a time.</span></span> <span data-ttu-id="bfac7-233">Étant donné que la ligne ne se termine pas par un caractère de pipeline, PowerShell considère que l’entrée est terminée et exécute cette ligne telle qu’elle a été entrée.</span><span class="sxs-lookup"><span data-stu-id="bfac7-233">Since the line does not end with a pipeline character, PowerShell considers the input to be complete and executes that line as entered.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfac7-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfac7-234">See Also</span></span>

[<span data-ttu-id="bfac7-235">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="bfac7-235">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="bfac7-236">about_Objects</span><span class="sxs-lookup"><span data-stu-id="bfac7-236">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="bfac7-237">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="bfac7-237">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="bfac7-238">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="bfac7-238">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="bfac7-239">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="bfac7-239">about_ForEach</span></span>](about_foreach.md)

