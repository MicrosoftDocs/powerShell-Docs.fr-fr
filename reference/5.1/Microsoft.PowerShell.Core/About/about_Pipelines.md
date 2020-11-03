---
description: Combinaison de commandes dans des pipelines dans PowerShell
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: 651ba1f42743d83958d6711cff01fec030fa9a02
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208765"
---
# <a name="about-pipelines"></a><span data-ttu-id="ebc15-104">À propos des pipelines</span><span class="sxs-lookup"><span data-stu-id="ebc15-104">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="ebc15-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="ebc15-105">Short description</span></span>

<span data-ttu-id="ebc15-106">Combinaison de commandes dans des pipelines dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebc15-106">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="ebc15-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="ebc15-107">Long description</span></span>

<span data-ttu-id="ebc15-108">Un pipeline est une série de commandes connectées par des opérateurs de pipeline ( `|` ) (ASCII 124).</span><span class="sxs-lookup"><span data-stu-id="ebc15-108">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="ebc15-109">Chaque opérateur de pipeline envoie les résultats de la commande précédente à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="ebc15-109">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="ebc15-110">La sortie de la première commande peut être envoyée pour traitement comme entrée à la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="ebc15-110">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="ebc15-111">Et cette sortie peut être envoyée à une autre commande.</span><span class="sxs-lookup"><span data-stu-id="ebc15-111">And that output can be sent to yet another command.</span></span> <span data-ttu-id="ebc15-112">Le résultat est une chaîne de commande complexe ou un _pipeline_ qui est composé d’une série de commandes simples.</span><span class="sxs-lookup"><span data-stu-id="ebc15-112">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="ebc15-113">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="ebc15-113">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="ebc15-114">Dans cet exemple, les objets qui `Command-1` émettent sont envoyés à `Command-2` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-114">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="ebc15-115">`Command-2` traite les objets et les envoie à `Command-3` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-115">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="ebc15-116">`Command-3` traite les objets et les envoie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-116">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="ebc15-117">Étant donné qu’il n’y a plus de commandes dans le pipeline, les résultats s’affichent dans la console.</span><span class="sxs-lookup"><span data-stu-id="ebc15-117">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="ebc15-118">Dans un pipeline, les commandes sont traitées dans l’ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="ebc15-118">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="ebc15-119">Le traitement est géré comme une opération unique et la sortie est affichée au fur et à mesure de sa génération.</span><span class="sxs-lookup"><span data-stu-id="ebc15-119">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="ebc15-120">Voici un exemple simple.</span><span class="sxs-lookup"><span data-stu-id="ebc15-120">Here is a simple example.</span></span> <span data-ttu-id="ebc15-121">La commande suivante obtient le processus du bloc-notes, puis l’arrête.</span><span class="sxs-lookup"><span data-stu-id="ebc15-121">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="ebc15-122">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="ebc15-122">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="ebc15-123">La première commande utilise l' `Get-Process` applet de commande pour récupérer un objet représentant le processus du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="ebc15-123">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="ebc15-124">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet processus à l’applet de commande `Stop-Process` , qui arrête le processus Notepad.</span><span class="sxs-lookup"><span data-stu-id="ebc15-124">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="ebc15-125">Notez que la `Stop-Process` commande n’a pas de paramètre **Name** ou **ID** pour spécifier le processus, car le processus spécifié est soumis via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-125">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="ebc15-126">Cet exemple de pipeline obtient les fichiers texte dans le répertoire actif, sélectionne uniquement les fichiers dont la longueur est supérieure à 10 000 octets, les trie par longueur et affiche le nom et la longueur de chaque fichier dans une table.</span><span class="sxs-lookup"><span data-stu-id="ebc15-126">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="ebc15-127">Ce pipeline se compose de quatre commandes dans l’ordre spécifié.</span><span class="sxs-lookup"><span data-stu-id="ebc15-127">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="ebc15-128">L’illustration suivante montre la sortie de chaque commande telle qu’elle est transmise à la commande suivante dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-128">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

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

## <a name="using-pipelines"></a><span data-ttu-id="ebc15-129">Utilisation des pipelines</span><span class="sxs-lookup"><span data-stu-id="ebc15-129">Using pipelines</span></span>

<span data-ttu-id="ebc15-130">La plupart des applets de commande PowerShell sont conçues pour prendre en charge les pipelines.</span><span class="sxs-lookup"><span data-stu-id="ebc15-130">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="ebc15-131">Dans la plupart des cas, vous pouvez _diriger_ les résultats d’une applet de commande **obtenir** vers une autre applet de commande du même nom.</span><span class="sxs-lookup"><span data-stu-id="ebc15-131">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="ebc15-132">Par exemple, vous pouvez diriger la sortie de l' `Get-Service` applet de commande vers les `Start-Service` applets de commande ou `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-132">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="ebc15-133">Cet exemple de pipeline démarre le service WMI sur l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="ebc15-133">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="ebc15-134">Pour un autre exemple, vous pouvez diriger la sortie de `Get-Item` ou `Get-ChildItem` dans le fournisseur de Registre PowerShell vers l’applet de commande `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-134">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="ebc15-135">Cet exemple ajoute une nouvelle entrée de Registre, **NoOfEmployees** , avec une valeur de **8124** , à la clé de Registre **MyCompany** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-135">This example adds a new registry entry, **NoOfEmployees** , with a value of **8124** , to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="ebc15-136">La plupart des applets de commande utilitaires, telles que,,, `Get-Member` `Where-Object` `Sort-Object` `Group-Object` et `Measure-Object` sont utilisées presque exclusivement dans des pipelines.</span><span class="sxs-lookup"><span data-stu-id="ebc15-136">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="ebc15-137">Vous pouvez diriger tout type d’objet vers ces applets de commande.</span><span class="sxs-lookup"><span data-stu-id="ebc15-137">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="ebc15-138">Cet exemple montre comment trier tous les processus sur l’ordinateur en fonction du nombre de descripteurs ouverts dans chaque processus.</span><span class="sxs-lookup"><span data-stu-id="ebc15-138">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="ebc15-139">Vous pouvez diriger les objets vers les applets de commande de mise en forme, d’exportation et de sortie, telles que,,, `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` et `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-139">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="ebc15-140">Cet exemple montre comment utiliser l' `Format-List` applet de commande pour afficher la liste des propriétés d’un objet processus.</span><span class="sxs-lookup"><span data-stu-id="ebc15-140">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="ebc15-141">Avec un peu de pratique, vous constaterez que la combinaison de commandes simples dans des pipelines permet d’économiser du temps et de la saisie, et d’améliorer l’efficacité de vos scripts.</span><span class="sxs-lookup"><span data-stu-id="ebc15-141">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="ebc15-142">Fonctionnement des pipelines</span><span class="sxs-lookup"><span data-stu-id="ebc15-142">How pipelines work</span></span>

<span data-ttu-id="ebc15-143">Cette section explique comment les objets d’entrée sont liés aux paramètres d’applet de commande et traités lors de l’exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-143">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="ebc15-144">Accepte l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="ebc15-144">Accepts pipeline input</span></span>

<span data-ttu-id="ebc15-145">Pour prendre en charge le traitement en pipeline, l’applet de commande de réception doit avoir un paramètre qui accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-145">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="ebc15-146">Utilisez la `Get-Help` commande avec les options **Full** ou **Parameter** pour déterminer les paramètres d’une applet de commande acceptant l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-146">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="ebc15-147">Par exemple, pour déterminer les paramètres de l’applet de commande qui `Start-Service` accepte l’entrée de pipeline, tapez :</span><span class="sxs-lookup"><span data-stu-id="ebc15-147">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="ebc15-148">ou</span><span class="sxs-lookup"><span data-stu-id="ebc15-148">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="ebc15-149">L’aide de l' `Start-Service` applet de commande montre que seuls les paramètres **InputObject** et **Name** acceptent l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-149">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

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

<span data-ttu-id="ebc15-150">Lorsque vous envoyez des objets via le pipeline à `Start-Service` , PowerShell tente d’associer les objets aux paramètres **InputObject** et **Name** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-150">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="ebc15-151">Méthodes d’acceptation de l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="ebc15-151">Methods of accepting pipeline input</span></span>

<span data-ttu-id="ebc15-152">Les paramètres des applets de commande peuvent accepter l’entrée de pipeline de deux façons différentes :</span><span class="sxs-lookup"><span data-stu-id="ebc15-152">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="ebc15-153">**ByValue** : le paramètre accepte les valeurs qui correspondent au type .net attendu ou qui peuvent être converties en ce type.</span><span class="sxs-lookup"><span data-stu-id="ebc15-153">**ByValue** : The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="ebc15-154">Par exemple, le paramètre **Name** de `Start-Service` accepte les entrées de pipeline par valeur.</span><span class="sxs-lookup"><span data-stu-id="ebc15-154">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="ebc15-155">Il peut accepter des objets de chaîne ou des objets qui peuvent être convertis en chaînes.</span><span class="sxs-lookup"><span data-stu-id="ebc15-155">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="ebc15-156">**ByPropertyName** : le paramètre accepte l’entrée uniquement lorsque l’objet d’entrée a une propriété du même nom que le paramètre.</span><span class="sxs-lookup"><span data-stu-id="ebc15-156">**ByPropertyName** : The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="ebc15-157">Par exemple, le paramètre Name de `Start-Service` peut accepter des objets qui ont une propriété **Name** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-157">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="ebc15-158">Pour répertorier les propriétés d’un objet, dirigez-le vers `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-158">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="ebc15-159">Certains paramètres peuvent accepter des objets par nom de valeur ou de propriété, ce qui facilite l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-159">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="ebc15-160">Liaison de paramètres</span><span class="sxs-lookup"><span data-stu-id="ebc15-160">Parameter binding</span></span>

<span data-ttu-id="ebc15-161">Lorsque vous dirigez des objets d’une commande vers une autre commande, PowerShell tente d’associer les objets dirigés à un paramètre de l’applet de commande de réception.</span><span class="sxs-lookup"><span data-stu-id="ebc15-161">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="ebc15-162">Le composant de liaison de paramètre de PowerShell associe les objets d’entrée aux paramètres d’applet de commande en fonction des critères suivants :</span><span class="sxs-lookup"><span data-stu-id="ebc15-162">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="ebc15-163">Le paramètre doit accepter l’entrée d’un pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-163">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="ebc15-164">Le paramètre doit accepter le type d’objet envoyé ou un type qui peut être converti vers le type attendu.</span><span class="sxs-lookup"><span data-stu-id="ebc15-164">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="ebc15-165">Le paramètre n’a pas été utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="ebc15-165">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="ebc15-166">Par exemple, l' `Start-Service` applet de commande a plusieurs paramètres, mais seuls deux d’entre eux, **Name** et **InputObject** acceptent l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-166">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="ebc15-167">Le paramètre **Name** prend des chaînes et le paramètre **InputObject** prend des objets de service.</span><span class="sxs-lookup"><span data-stu-id="ebc15-167">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="ebc15-168">Par conséquent, vous pouvez diriger des chaînes, des objets de service et des objets avec des propriétés qui peuvent être converties en objets de service ou de chaîne.</span><span class="sxs-lookup"><span data-stu-id="ebc15-168">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="ebc15-169">PowerShell gère la liaison de paramètre aussi efficacement que possible.</span><span class="sxs-lookup"><span data-stu-id="ebc15-169">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="ebc15-170">Vous ne pouvez pas suggérer ou forcer PowerShell à établir une liaison avec un paramètre spécifique.</span><span class="sxs-lookup"><span data-stu-id="ebc15-170">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="ebc15-171">La commande échoue si PowerShell ne peut pas lier les objets redirigés.</span><span class="sxs-lookup"><span data-stu-id="ebc15-171">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="ebc15-172">Pour plus d’informations sur le dépannage des erreurs de liaison, consultez [examen des erreurs de pipeline](#investigating-pipeline-errors) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="ebc15-172">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="ebc15-173">Traitement une fois par heure</span><span class="sxs-lookup"><span data-stu-id="ebc15-173">One-at-a-time processing</span></span>

<span data-ttu-id="ebc15-174">La redirection d’objets vers une commande est très similaire à l’utilisation d’un paramètre de la commande pour envoyer les objets.</span><span class="sxs-lookup"><span data-stu-id="ebc15-174">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="ebc15-175">Examinons un exemple de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-175">Let's look at a pipeline example.</span></span> <span data-ttu-id="ebc15-176">Dans cet exemple, nous utilisons un pipeline pour afficher une table d’objets de service.</span><span class="sxs-lookup"><span data-stu-id="ebc15-176">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="ebc15-177">Fonctionnellement, cela revient à utiliser le paramètre **InputObject** de `Format-Table` pour envoyer la collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="ebc15-177">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="ebc15-178">Par exemple, nous pouvons enregistrer la collection de services dans une variable qui est passée à l’aide du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-178">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="ebc15-179">Ou nous pouvons incorporer la commande dans le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-179">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="ebc15-180">Toutefois, il existe une différence importante.</span><span class="sxs-lookup"><span data-stu-id="ebc15-180">However, there's an important difference.</span></span> <span data-ttu-id="ebc15-181">Lorsque vous dirigez plusieurs objets vers une commande, PowerShell les envoie un par un à la commande.</span><span class="sxs-lookup"><span data-stu-id="ebc15-181">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="ebc15-182">Lorsque vous utilisez un paramètre de commande, les objets sont envoyés sous la forme d’un objet de tableau unique.</span><span class="sxs-lookup"><span data-stu-id="ebc15-182">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="ebc15-183">Cette différence mineure a des conséquences significatives.</span><span class="sxs-lookup"><span data-stu-id="ebc15-183">This minor difference has significant consequences.</span></span>

<span data-ttu-id="ebc15-184">Lors de l’exécution d’un pipeline, PowerShell énumère automatiquement tout type qui implémente l' `IEnumerable` interface et envoie un à un les membres via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-184">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="ebc15-185">L’exception est `[hashtable]` , qui requiert un appel à la `GetEnumerator()` méthode.</span><span class="sxs-lookup"><span data-stu-id="ebc15-185">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="ebc15-186">Dans les exemples suivants, un tableau et une table de hachage sont dirigés vers l' `Measure-Object` applet de commande pour compter le nombre d’objets reçus à partir du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-186">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="ebc15-187">Le tableau a plusieurs membres, et la table de hachage a plusieurs paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="ebc15-187">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="ebc15-188">Seul le tableau est énuméré un à la fois.</span><span class="sxs-lookup"><span data-stu-id="ebc15-188">Only the array is enumerated one at a time.</span></span>

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

<span data-ttu-id="ebc15-189">De même, si vous dirigez plusieurs objets de processus de l' `Get-Process` applet de commande vers l’applet de commande `Get-Member` , PowerShell envoie chaque objet de processus, un à la fois, à `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-189">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="ebc15-190">`Get-Member` affiche la classe .NET (type) des objets processus, ainsi que leurs propriétés et méthodes.</span><span class="sxs-lookup"><span data-stu-id="ebc15-190">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

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
> <span data-ttu-id="ebc15-191">`Get-Member` élimine les doublons. par conséquent, si les objets sont tous du même type, il n’affiche qu’un seul type d’objet.</span><span class="sxs-lookup"><span data-stu-id="ebc15-191">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="ebc15-192">Toutefois, si vous utilisez le paramètre **InputObject** de `Get-Member` , `Get-Member` reçoit un tableau d’objets **System. Diagnostics. Process** comme une seule unité.</span><span class="sxs-lookup"><span data-stu-id="ebc15-192">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="ebc15-193">Elle affiche les propriétés d’un tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="ebc15-193">It displays the properties of an array of objects.</span></span> <span data-ttu-id="ebc15-194">(Notez le symbole de tableau ( `[]` ) après le nom du type **System. Object** .)</span><span class="sxs-lookup"><span data-stu-id="ebc15-194">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="ebc15-195">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="ebc15-195">For example,</span></span>

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

<span data-ttu-id="ebc15-196">Ce résultat n’est peut-être pas ce que vous souhaitiez.</span><span class="sxs-lookup"><span data-stu-id="ebc15-196">This result might not be what you intended.</span></span> <span data-ttu-id="ebc15-197">Mais une fois que vous l’avez compris, vous pouvez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="ebc15-197">But after you understand it, you can use it.</span></span> <span data-ttu-id="ebc15-198">Par exemple, tous les objets tableau ont une propriété **Count** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-198">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="ebc15-199">Vous pouvez l’utiliser pour compter le nombre de processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ebc15-199">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="ebc15-200">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="ebc15-200">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="ebc15-201">Il est important de se souvenir que les objets envoyés dans le pipeline sont remis un à la fois.</span><span class="sxs-lookup"><span data-stu-id="ebc15-201">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="ebc15-202">Examen des erreurs de pipeline</span><span class="sxs-lookup"><span data-stu-id="ebc15-202">Investigating pipeline errors</span></span>

<span data-ttu-id="ebc15-203">Lorsque PowerShell ne peut pas associer les objets dirigés à un paramètre de l’applet de commande de réception, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="ebc15-203">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="ebc15-204">Dans l’exemple suivant, nous essayons de déplacer une entrée de registre d’une clé de Registre vers une autre.</span><span class="sxs-lookup"><span data-stu-id="ebc15-204">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="ebc15-205">L' `Get-Item` applet de commande obtient le chemin d’accès de destination, qui est ensuite redirigé vers l’applet de commande `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-205">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="ebc15-206">La `Move-ItemProperty` commande spécifie le chemin d’accès actuel et le nom de l’entrée de Registre à déplacer.</span><span class="sxs-lookup"><span data-stu-id="ebc15-206">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="ebc15-207">La commande échoue et PowerShell affiche le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="ebc15-207">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="ebc15-208">Pour examiner, utilisez l' `Trace-Command` applet de commande pour suivre le composant de liaison de paramètre de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebc15-208">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="ebc15-209">L’exemple suivant effectue le suivi de la liaison de paramètre pendant l’exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-209">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="ebc15-210">Le paramètre **PSHost** affiche les résultats de la trace dans la console et le paramètre **filePath** envoie les résultats de la trace au `debug.txt` fichier pour référence ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ebc15-210">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="ebc15-211">Les résultats de la trace sont longs, mais ils affichent les valeurs qui sont liées à l’applet de commande, `Get-Item` puis les valeurs nommées qui sont liées à l’applet de commande `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-211">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

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

<span data-ttu-id="ebc15-212">Enfin, il indique que la tentative de liaison du chemin d’accès au paramètre de **destination** de `Move-ItemProperty` a échoué.</span><span class="sxs-lookup"><span data-stu-id="ebc15-212">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

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

<span data-ttu-id="ebc15-213">Utilisez l' `Get-Help` applet de commande pour afficher les attributs du paramètre de **destination** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-213">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

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

<span data-ttu-id="ebc15-214">Les résultats montrent que la **destination** prend uniquement l’entrée de pipeline « par nom de propriété ».</span><span class="sxs-lookup"><span data-stu-id="ebc15-214">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="ebc15-215">Par conséquent, l’objet dirigé doit avoir une propriété nommée **destination** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-215">Therefore, the piped object must have a property named **Destination** .</span></span>

<span data-ttu-id="ebc15-216">Utilisez `Get-Member` pour afficher les propriétés de l’objet provenant de `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="ebc15-216">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="ebc15-217">La sortie indique que l’élément est un objet **Microsoft. Win32. RegistryKey** qui n’a pas de propriété de **destination** .</span><span class="sxs-lookup"><span data-stu-id="ebc15-217">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="ebc15-218">Cela explique pourquoi la commande a échoué.</span><span class="sxs-lookup"><span data-stu-id="ebc15-218">That explains why the command failed.</span></span>

<span data-ttu-id="ebc15-219">Le paramètre **path** accepte l’entrée de pipeline par nom ou par valeur.</span><span class="sxs-lookup"><span data-stu-id="ebc15-219">The **Path** parameter accepts pipeline input by name or by value.</span></span>

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

<span data-ttu-id="ebc15-220">Pour corriger la commande, nous devons spécifier la destination dans l' `Move-ItemProperty` applet de commande et utiliser `Get-Item` pour obtenir le **chemin d’accès** de l’élément que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="ebc15-220">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="ebc15-221">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="ebc15-221">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="ebc15-222">Continuation de ligne intrinsèque</span><span class="sxs-lookup"><span data-stu-id="ebc15-222">Intrinsic line continuation</span></span>

<span data-ttu-id="ebc15-223">Comme nous l’avons déjà vu, un pipeline est une série de commandes connectées par des opérateurs de pipeline ( `|` ), généralement écrits sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="ebc15-223">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="ebc15-224">Toutefois, pour des raisons de lisibilité, PowerShell vous permet de fractionner le pipeline sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="ebc15-224">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="ebc15-225">Lorsqu’un opérateur de canal est le dernier jeton de la ligne, l’analyseur PowerShell joint la ligne suivante à la commande actuelle pour poursuivre la construction du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ebc15-225">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="ebc15-226">Par exemple, le pipeline à ligne unique suivant :</span><span class="sxs-lookup"><span data-stu-id="ebc15-226">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="ebc15-227">peut être écrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="ebc15-227">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="ebc15-228">Les espaces de début sur les lignes suivantes ne sont pas significatifs.</span><span class="sxs-lookup"><span data-stu-id="ebc15-228">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="ebc15-229">La mise en retrait améliore la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="ebc15-229">The indentation enhances readability.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebc15-230">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebc15-230">See Also</span></span>

[<span data-ttu-id="ebc15-231">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ebc15-231">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="ebc15-232">about_Objects</span><span class="sxs-lookup"><span data-stu-id="ebc15-232">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="ebc15-233">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="ebc15-233">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="ebc15-234">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="ebc15-234">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="ebc15-235">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="ebc15-235">about_ForEach</span></span>](about_foreach.md)
