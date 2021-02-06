---
description: Décrit comment interpréter et mettre en forme la sortie des commandes distantes.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 476afc62089795d22002ece05c7ce2bf53994237
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595707"
---
# <a name="about-remote-output"></a><span data-ttu-id="19df2-103">À propos de la sortie à distance</span><span class="sxs-lookup"><span data-stu-id="19df2-103">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="19df2-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="19df2-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="19df2-105">Décrit comment interpréter et mettre en forme la sortie des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="19df2-105">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="19df2-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="19df2-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="19df2-107">La sortie d’une commande exécutée sur un ordinateur distant peut ressembler à la sortie de la même commande exécutée sur un ordinateur local, mais il existe des différences significatives.</span><span class="sxs-lookup"><span data-stu-id="19df2-107">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="19df2-108">Cette rubrique explique comment interpréter, mettre en forme et afficher la sortie des commandes exécutées sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="19df2-108">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="19df2-109">AFFICHAGE DU NOM DE L’ORDINATEUR</span><span class="sxs-lookup"><span data-stu-id="19df2-109">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="19df2-110">Lorsque vous utilisez l’applet de commande Invoke-Command pour exécuter une commande sur un ordinateur distant, la commande retourne un objet qui comprend le nom de l’ordinateur qui a généré les données.</span><span class="sxs-lookup"><span data-stu-id="19df2-110">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="19df2-111">Le nom de l’ordinateur distant est stocké dans la propriété PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="19df2-111">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="19df2-112">Pour de nombreuses commandes, PSComputerName est affiché par défaut.</span><span class="sxs-lookup"><span data-stu-id="19df2-112">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="19df2-113">Par exemple, la commande suivante exécute une commande Get-Culture sur deux ordinateurs distants, serveur01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="19df2-113">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="19df2-114">La sortie, qui apparaît ci-dessous, comprend les noms des ordinateurs distants sur lesquels la commande a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="19df2-114">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="19df2-115">Vous pouvez utiliser le paramètre HideComputerName de Invoke-Command pour masquer la propriété PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="19df2-115">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="19df2-116">Ce paramètre est conçu pour les commandes qui collectent des données à partir d’un seul ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="19df2-116">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="19df2-117">La commande suivante exécute une commande Get-Culture sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="19df2-117">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="19df2-118">Elle utilise le paramètre HideComputerName pour masquer la propriété PSComputerName et les propriétés associées.</span><span class="sxs-lookup"><span data-stu-id="19df2-118">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="19df2-119">Vous pouvez également afficher la propriété PSComputerName si elle n’est pas affichée par défaut.</span><span class="sxs-lookup"><span data-stu-id="19df2-119">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="19df2-120">Par exemple, les commandes suivantes utilisent l’applet de commande Format-Table pour ajouter la propriété PSComputerName à la sortie d’une commande de Get-Date à distance.</span><span class="sxs-lookup"><span data-stu-id="19df2-120">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="19df2-121">AFFICHAGE DE LA PROPRIÉTÉ MACHINENAME</span><span class="sxs-lookup"><span data-stu-id="19df2-121">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="19df2-122">Plusieurs applets de commande, y compris obtenir-process, obtenir-service et obtenir-EventLog, ont un paramètre ComputerName qui obtient les objets sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="19df2-122">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="19df2-123">Ces applets de commande n’utilisent pas la communication à distance PowerShell. vous pouvez donc les utiliser même sur des ordinateurs qui ne sont pas configurés pour la communication à distance dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19df2-123">These cmdlets do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="19df2-124">Les objets que ces applets de commande retournent stockent le nom de l’ordinateur distant dans la propriété MachineName.</span><span class="sxs-lookup"><span data-stu-id="19df2-124">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="19df2-125">(Ces objets n’ont pas de propriété PSComputerName.)</span><span class="sxs-lookup"><span data-stu-id="19df2-125">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="19df2-126">Par exemple, cette commande obtient le processus PowerShell sur les ordinateurs distants SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="19df2-126">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="19df2-127">L’affichage par défaut n’inclut pas la propriété MachineName.</span><span class="sxs-lookup"><span data-stu-id="19df2-127">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="19df2-128">Vous pouvez utiliser l’applet de commande Format-Table pour afficher la propriété MachineName des objets de processus.</span><span class="sxs-lookup"><span data-stu-id="19df2-128">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="19df2-129">Par exemple, la commande suivante enregistre les processus dans la variable $p, puis utilise un opérateur de pipeline (|) pour envoyer les processus dans $p à la commande Format-Table.</span><span class="sxs-lookup"><span data-stu-id="19df2-129">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="19df2-130">La commande utilise le paramètre Property de Format-Table pour inclure la propriété MachineName dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="19df2-130">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="19df2-131">La commande suivante plus complexe ajoute la propriété MachineName à l’affichage du processus par défaut.</span><span class="sxs-lookup"><span data-stu-id="19df2-131">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="19df2-132">Il utilise des tables de hachage pour spécifier des propriétés calculées.</span><span class="sxs-lookup"><span data-stu-id="19df2-132">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="19df2-133">Heureusement, vous n’avez pas à le comprendre pour l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="19df2-133">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="19df2-134">(Notez que la Supercycle ['] est le caractère de continuation.)</span><span class="sxs-lookup"><span data-stu-id="19df2-134">(Note that the backtick [\`] is the continuation character.)</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a><span data-ttu-id="19df2-135">OBJETS DÉSÉRIALISÉS</span><span class="sxs-lookup"><span data-stu-id="19df2-135">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="19df2-136">Lorsque vous exécutez des commandes distantes qui génèrent une sortie, le résultat de la commande est transmis sur le réseau à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="19df2-136">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="19df2-137">Étant donné que la plupart des objets en direct Microsoft .NET Framework (tels que les objets retournés par les applets de commande PowerShell) ne peuvent pas être transmis sur le réseau, les objets actifs sont « sérialisés ».</span><span class="sxs-lookup"><span data-stu-id="19df2-137">Because most live Microsoft .NET Framework objects (such as the objects that PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="19df2-138">En d’autres termes, les objets actifs sont convertis en représentations XML de l’objet et de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="19df2-138">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="19df2-139">Ensuite, l’objet sérialisé XML est transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="19df2-139">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="19df2-140">Sur l’ordinateur local, PowerShell reçoit l’objet sérialisé XML et le « désérialise » en convertissant l’objet XML en un objet de .NET Framework standard.</span><span class="sxs-lookup"><span data-stu-id="19df2-140">On the local computer, PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="19df2-141">Toutefois, l’objet désérialisé n’est pas un objet actif.</span><span class="sxs-lookup"><span data-stu-id="19df2-141">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="19df2-142">Il s’agit d’un instantané de l’objet au moment où il a été sérialisé, et il comprend des propriétés, mais pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="19df2-142">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="19df2-143">Vous pouvez utiliser et gérer ces objets dans PowerShell, y compris les transmettre dans des pipelines, afficher les propriétés sélectionnées et les mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="19df2-143">You can use and manage these objects in PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="19df2-144">La plupart des objets désérialisés sont automatiquement mis en forme pour être affichés par les entrées dans les fichiers XML Types.ps1XML ou Format.ps1.</span><span class="sxs-lookup"><span data-stu-id="19df2-144">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="19df2-145">Toutefois, l’ordinateur local n’a peut-être pas de fichier de mise en forme pour tous les objets désérialisés qui ont été générés sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="19df2-145">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="19df2-146">Lorsque les objets ne sont pas mis en forme, toutes les propriétés de chaque objet s’affichent dans la console dans une liste de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="19df2-146">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="19df2-147">Lorsque les objets ne sont pas mis en forme automatiquement, vous pouvez utiliser les applets de commande de mise en forme, telles que Format-Table ou format-list, pour mettre en forme et afficher les propriétés sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="19df2-147">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="19df2-148">Vous pouvez utiliser l’applet de commande Out-GridView pour afficher les objets dans une table.</span><span class="sxs-lookup"><span data-stu-id="19df2-148">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="19df2-149">En outre, si vous exécutez une commande sur un ordinateur distant qui utilise des applets de commande que vous n’avez pas sur votre ordinateur local, les objets renvoyés par la commande peuvent ne pas être correctement mis en forme, car vous ne disposez pas des fichiers de mise en forme de ces objets sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="19df2-149">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="19df2-150">Pour récupérer des données de mise en forme à partir d’un autre ordinateur, utilisez les applets de commande Get-FormatData et Export-FormatData.</span><span class="sxs-lookup"><span data-stu-id="19df2-150">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="19df2-151">Certains types d’objets, tels que les objets DirectoryInfo et les GUID, sont reconvertis en objets dynamiques lorsqu’ils sont reçus.</span><span class="sxs-lookup"><span data-stu-id="19df2-151">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="19df2-152">Ces objets n’ont pas besoin d’une gestion ou d’une mise en forme spéciale.</span><span class="sxs-lookup"><span data-stu-id="19df2-152">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="19df2-153">CLASSEMENT DES RÉSULTATS</span><span class="sxs-lookup"><span data-stu-id="19df2-153">ORDERING THE RESULTS</span></span>

<span data-ttu-id="19df2-154">L’ordre des noms d’ordinateur dans le paramètre ComputerName des applets de commande détermine l’ordre dans lequel PowerShell se connecte aux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="19df2-154">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which PowerShell connects to the remote computers.</span></span> <span data-ttu-id="19df2-155">Toutefois, les résultats s’affichent dans l’ordre dans lequel l’ordinateur local les reçoit, ce qui peut être un ordre différent.</span><span class="sxs-lookup"><span data-stu-id="19df2-155">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="19df2-156">Pour modifier l’ordre des résultats, utilisez l’applet de commande Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="19df2-156">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="19df2-157">Vous pouvez effectuer un tri sur la propriété PSComputerName ou MachineName.</span><span class="sxs-lookup"><span data-stu-id="19df2-157">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="19df2-158">Vous pouvez également effectuer un tri sur une autre propriété de l’objet afin que les résultats de différents ordinateurs soient intercalés.</span><span class="sxs-lookup"><span data-stu-id="19df2-158">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="19df2-159">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="19df2-159">SEE ALSO</span></span>

[<span data-ttu-id="19df2-160">about_Remote</span><span class="sxs-lookup"><span data-stu-id="19df2-160">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="19df2-161">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="19df2-161">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="19df2-162">Format-Table</span><span class="sxs-lookup"><span data-stu-id="19df2-162">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="19df2-163">Get-Process</span><span class="sxs-lookup"><span data-stu-id="19df2-163">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="19df2-164">Get-Service</span><span class="sxs-lookup"><span data-stu-id="19df2-164">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="19df2-165">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="19df2-165">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="19df2-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="19df2-166">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

