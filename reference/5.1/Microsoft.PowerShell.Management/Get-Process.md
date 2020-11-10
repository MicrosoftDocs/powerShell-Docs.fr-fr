---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: d1a576ce9c718561718bac5fee065983a057d458
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388295"
---
# <span data-ttu-id="89208-103">Get-Process</span><span class="sxs-lookup"><span data-stu-id="89208-103">Get-Process</span></span>

## <span data-ttu-id="89208-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="89208-104">SYNOPSIS</span></span>
<span data-ttu-id="89208-105">Obtient les processus qui s'exécutent sur l'ordinateur local ou un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="89208-105">Gets the processes that are running on the local computer or a remote computer.</span></span>

## <span data-ttu-id="89208-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="89208-106">SYNTAX</span></span>

### <span data-ttu-id="89208-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="89208-107">Name (Default)</span></span>

```
Get-Process [[-Name] <String[]>] [-ComputerName <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="89208-108">NameWithUserName</span><span class="sxs-lookup"><span data-stu-id="89208-108">NameWithUserName</span></span>

```
Get-Process [[-Name] <String[]>] [-IncludeUserName] [<CommonParameters>]
```

### <span data-ttu-id="89208-109">IdWithUserName</span><span class="sxs-lookup"><span data-stu-id="89208-109">IdWithUserName</span></span>

```
Get-Process -Id <Int32[]> [-IncludeUserName] [<CommonParameters>]
```

### <span data-ttu-id="89208-110">Id</span><span class="sxs-lookup"><span data-stu-id="89208-110">Id</span></span>

```
Get-Process -Id <Int32[]> [-ComputerName <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="89208-111">InputObjectWithUserName</span><span class="sxs-lookup"><span data-stu-id="89208-111">InputObjectWithUserName</span></span>

```
Get-Process -InputObject <Process[]> [-IncludeUserName] [<CommonParameters>]
```

### <span data-ttu-id="89208-112">InputObject</span><span class="sxs-lookup"><span data-stu-id="89208-112">InputObject</span></span>

```
Get-Process -InputObject <Process[]> [-ComputerName <String[]>] [-Module] [-FileVersionInfo]
 [<CommonParameters>]
```

## <span data-ttu-id="89208-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="89208-113">DESCRIPTION</span></span>

<span data-ttu-id="89208-114">L' `Get-Process` applet de commande obtient les processus sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="89208-114">The `Get-Process` cmdlet gets the processes on a local or remote computer.</span></span>

<span data-ttu-id="89208-115">Sans paramètre, cette applet de commande obtient tous les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="89208-115">Without parameters, this cmdlet gets all of the processes on the local computer.</span></span> <span data-ttu-id="89208-116">Vous pouvez également spécifier un processus particulier par nom de processus ou ID de processus (PID), ou passer un objet processus via le pipeline à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="89208-116">You can also specify a particular process by process name or process ID (PID) or pass a process object through the pipeline to this cmdlet.</span></span>

<span data-ttu-id="89208-117">Par défaut, cette applet de commande retourne un objet processus qui contient des informations détaillées sur le processus et prend en charge des méthodes qui vous permettent de démarrer et d’arrêter le processus.</span><span class="sxs-lookup"><span data-stu-id="89208-117">By default, this cmdlet returns a process object that has detailed information about the process and supports methods that let you start and stop the process.</span></span> <span data-ttu-id="89208-118">Vous pouvez également utiliser les paramètres de l' `Get-Process` applet de commande pour obtenir les informations de version de fichier pour le programme qui s’exécute dans le processus et pour obtenir les modules chargés par le processus.</span><span class="sxs-lookup"><span data-stu-id="89208-118">You can also use the parameters of the `Get-Process` cmdlet to get file version information for the program that runs in the process and to get the modules that the process loaded.</span></span>

## <span data-ttu-id="89208-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="89208-119">EXAMPLES</span></span>

### <span data-ttu-id="89208-120">Exemple 1 : obtenir la liste de tous les processus actifs sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="89208-120">Example 1: Get a list of all active processes on the local computer</span></span>

```powershell
Get-Process
```

<span data-ttu-id="89208-121">Cette commande obtient une liste de tous les processus actifs en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="89208-121">This command gets a list of all active processes running on the local computer.</span></span> <span data-ttu-id="89208-122">Pour obtenir une définition de chaque colonne, consultez la section [Remarques](#notes) .</span><span class="sxs-lookup"><span data-stu-id="89208-122">For a definition of each column, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="89208-123">Exemple 2 : obtenir toutes les données disponibles sur un ou plusieurs processus</span><span class="sxs-lookup"><span data-stu-id="89208-123">Example 2: Get all available data about one or more processes</span></span>

```powershell
Get-Process winword, explorer | Format-List *
```

<span data-ttu-id="89208-124">Cette commande obtient toutes les données disponibles sur les processus liés à Winword et à Explorer sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="89208-124">This command gets all available data about the Winword and Explorer processes on the computer.</span></span> <span data-ttu-id="89208-125">Elle utilise le paramètre **Name** pour spécifier les processus, mais elle omet le nom de paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="89208-125">It uses the **Name** parameter to specify the processes, but it omits the optional parameter name.</span></span> <span data-ttu-id="89208-126">L’opérateur de pipeline `|` transmet les données à l’applet de commande `Format-List` , qui affiche toutes les propriétés disponibles `*` des objets de processus Winword et Explorer.</span><span class="sxs-lookup"><span data-stu-id="89208-126">The pipeline operator `|` passes the data to the `Format-List` cmdlet, which displays all available properties `*` of the Winword and Explorer process objects.</span></span>

<span data-ttu-id="89208-127">Vous pouvez également identifier un processus à l'aide de son identificateur de processus.</span><span class="sxs-lookup"><span data-stu-id="89208-127">You can also identify the processes by their process IDs.</span></span> <span data-ttu-id="89208-128">Par exemple, `Get-Process -Id 664, 2060`.</span><span class="sxs-lookup"><span data-stu-id="89208-128">For instance, `Get-Process -Id 664, 2060`.</span></span>

### <span data-ttu-id="89208-129">Exemple 3 : obtenir tous les processus avec une plage de travail supérieure à une taille spécifiée</span><span class="sxs-lookup"><span data-stu-id="89208-129">Example 3: Get all processes with a working set greater than a specified size</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

<span data-ttu-id="89208-130">Cette commande obtient tous les processus qui ont une plage de travail supérieure à 20 Mo.</span><span class="sxs-lookup"><span data-stu-id="89208-130">This command gets all processes that have a working set greater than 20 MB.</span></span> <span data-ttu-id="89208-131">Elle utilise l' `Get-Process` applet de commande pour récupérer tous les processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="89208-131">It uses the `Get-Process` cmdlet to get all running processes.</span></span> <span data-ttu-id="89208-132">L’opérateur de pipeline `|` passe les objets de processus à l’applet de commande `Where-Object` , qui sélectionne uniquement l’objet dont la valeur est supérieure à 20 millions octets pour la propriété de la **plage** de temps.</span><span class="sxs-lookup"><span data-stu-id="89208-132">The pipeline operator `|` passes the process objects to the `Where-Object` cmdlet, which selects only the object with a value greater than 20,000,000 bytes for the **WorkingSet** property.</span></span>

<span data-ttu-id="89208-133">La **plage** de temps est l’une des nombreuses propriétés des objets de processus.</span><span class="sxs-lookup"><span data-stu-id="89208-133">**WorkingSet** is one of many properties of process objects.</span></span> <span data-ttu-id="89208-134">Pour afficher toutes les propriétés, tapez `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="89208-134">To see all of the properties, type `Get-Process | Get-Member`.</span></span> <span data-ttu-id="89208-135">Par défaut, les valeurs de toutes les propriétés Amount sont exprimées en octets, bien que l'affichage par défaut les répertorie en kilo-octets et mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="89208-135">By default, the values of all amount properties are in bytes, even though the default display lists them in kilobytes and megabytes.</span></span>

### <span data-ttu-id="89208-136">Exemple 4 : répertorier les processus sur l’ordinateur dans des groupes en fonction de la priorité</span><span class="sxs-lookup"><span data-stu-id="89208-136">Example 4: List processes on the computer in groups based on priority</span></span>

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

<span data-ttu-id="89208-137">Ces commandes répertorient les processus sur l’ordinateur dans des groupes en fonction de leur classe de priorité.</span><span class="sxs-lookup"><span data-stu-id="89208-137">These commands list the processes on the computer in groups based on their priority class.</span></span> <span data-ttu-id="89208-138">La première commande récupère tous les processus sur l’ordinateur, puis les stocke dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="89208-138">The first command gets all the processes on the computer and then stores them in the `$A` variable.</span></span>

<span data-ttu-id="89208-139">La deuxième commande dirige l’objet **processus** stocké dans la `$A` variable vers l’applet de commande `Get-Process` , puis vers l’applet de commande `Format-Table` , qui met en forme les processus à l’aide de la vue **Priority** .</span><span class="sxs-lookup"><span data-stu-id="89208-139">The second command pipes the **Process** object stored in the `$A` variable to the `Get-Process` cmdlet, then to the `Format-Table` cmdlet, which formats the processes by using the **Priority** view.</span></span>

<span data-ttu-id="89208-140">La vue **Priority** et d’autres vues sont définies dans les fichiers de format ps1xml dans le répertoire de racine PowerShell ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="89208-140">The **Priority** view, and other views, are defined in the PS1XML format files in the PowerShell home directory (`$pshome`).</span></span>

### <span data-ttu-id="89208-141">Exemple 5 : ajouter une propriété à l’affichage de sortie standard Get-Process</span><span class="sxs-lookup"><span data-stu-id="89208-141">Example 5: Add a property to the standard Get-Process output display</span></span>

```powershell
Get-Process powershell -ComputerName S1, localhost | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 S1          powershell
     6 23500 31348   142 2.75   4016 S1          powershell
    27 54572 54520   576 5.52   4428 localhost   powershell
```

<span data-ttu-id="89208-142">Cet exemple récupère des processus à partir de l’ordinateur local et d’un ordinateur distant (S1).</span><span class="sxs-lookup"><span data-stu-id="89208-142">This example retrieves processes from the local computer and a remote computer (S1).</span></span> <span data-ttu-id="89208-143">Les processus récupérés sont dirigés vers la `Format-Table` commande qui ajoute la propriété **MachineName** à l' `Get-Process` affichage de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="89208-143">The retrieved processes are piped to the `Format-Table` command that adds the **MachineName** property to the standard `Get-Process` output display.</span></span>

### <span data-ttu-id="89208-144">Exemple 6 : obtenir des informations sur la version d’un processus</span><span class="sxs-lookup"><span data-stu-id="89208-144">Example 6: Get version information for a process</span></span>

```powershell
Get-Process powershell -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.6713.1       6.1.6713.1 (f... C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe
```

<span data-ttu-id="89208-145">Cette commande utilise le paramètre **FileVersionInfo** pour obtenir les informations de version du fichier powershell.exe qui est le module principal du processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89208-145">This command uses the **FileVersionInfo** parameter to get the version information for the powershell.exe file that is the main module for the PowerShell process.</span></span>

<span data-ttu-id="89208-146">Pour exécuter cette commande avec des processus que vous ne possédez pas sur Windows Vista et les versions ultérieures de Windows, vous devez ouvrir PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="89208-146">To run this command with processes that you do not own on Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="89208-147">Exemple 7 : récupération des modules chargés avec le processus spécifié</span><span class="sxs-lookup"><span data-stu-id="89208-147">Example 7: Get modules loaded with the specified process</span></span>

```powershell
Get-Process SQL* -Module
```

<span data-ttu-id="89208-148">Cette commande utilise le paramètre **module** pour obtenir les modules qui ont été chargés par le processus.</span><span class="sxs-lookup"><span data-stu-id="89208-148">This command uses the **Module** parameter to get the modules that have been loaded by the process.</span></span>
<span data-ttu-id="89208-149">Cette commande obtient les modules pour les processus dont les noms commencent par SQL.</span><span class="sxs-lookup"><span data-stu-id="89208-149">This command gets the modules for the processes that have names that begin with SQL.</span></span>

<span data-ttu-id="89208-150">Pour exécuter cette commande sur Windows Vista et les versions ultérieures de Windows avec des processus que vous ne possédez pas, vous devez démarrer PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="89208-150">To run this command on Windows Vista and later versions of Windows with processes that you do not own, you must start PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="89208-151">Exemple 8 : Rechercher le propriétaire d’un processus</span><span class="sxs-lookup"><span data-stu-id="89208-151">Example 8: Find the owner of a process</span></span>

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     powershell
```

```powershell
$p = Get-WmiObject Win32_Process -Filter "name='powershell.exe'"
$p.GetOwner()
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 3
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Domain           : DOMAIN01
ReturnValue      : 0
User             : user01
```

<span data-ttu-id="89208-152">La première commande montre comment rechercher le propriétaire d’un processus.</span><span class="sxs-lookup"><span data-stu-id="89208-152">The first command shows how to find the owner of a process.</span></span> <span data-ttu-id="89208-153">Le paramètre **IncludeUserName** nécessite des droits d’utilisateur élevés (exécuter en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="89208-153">The **IncludeUserName** parameter requires elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="89208-154">La sortie révèle que le propriétaire est Domain01\user01.</span><span class="sxs-lookup"><span data-stu-id="89208-154">The output reveals that the owner is Domain01\user01.</span></span>

<span data-ttu-id="89208-155">La deuxième et la troisième commande sont une autre façon de rechercher le propriétaire d’un processus.</span><span class="sxs-lookup"><span data-stu-id="89208-155">The second and third command are another way to find the owner of a process.</span></span>

<span data-ttu-id="89208-156">La deuxième commande utilise `Get-WmiObject` pour accéder au processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89208-156">The second command uses `Get-WmiObject` to get the PowerShell process.</span></span>
<span data-ttu-id="89208-157">Elle l’enregistre dans la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="89208-157">It saves it in the `$p` variable.</span></span>

<span data-ttu-id="89208-158">La troisième commande utilise la méthode GetOwner pour récupérer le propriétaire du processus dans `$p` .</span><span class="sxs-lookup"><span data-stu-id="89208-158">The third command uses the GetOwner method to get the owner of the process in `$p`.</span></span> <span data-ttu-id="89208-159">La sortie révèle que le propriétaire est Domain01\user01.</span><span class="sxs-lookup"><span data-stu-id="89208-159">The output reveals that the owner is Domain01\user01.</span></span>

### <span data-ttu-id="89208-160">Exemple 9 : utiliser une variable automatique pour identifier le processus qui héberge la session active</span><span class="sxs-lookup"><span data-stu-id="89208-160">Example 9: Use an automatic variable to identify the process hosting the current session</span></span>

```powershell
Get-Process powershell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
308      26        52308      61780   567     3.18   5632 powershell
377      26        62676      63384   575     3.88   5888 powershell
```

```powershell
Get-Process -Id $PID
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
396      26        56488      57236   575     3.90   5888 powershell
```

<span data-ttu-id="89208-161">Ces commandes montrent comment utiliser la `$PID` variable automatique pour identifier le processus qui héberge la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="89208-161">These commands show how to use the `$PID` automatic variable to identify the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="89208-162">Vous pouvez utiliser cette méthode pour distinguer le processus hôte des autres processus PowerShell que vous pouvez arrêter ou fermer.</span><span class="sxs-lookup"><span data-stu-id="89208-162">You can use this method to distinguish the host process from other PowerShell processes that you might want to stop or close.</span></span>

<span data-ttu-id="89208-163">La première commande obtient tous les processus PowerShell dans la session active.</span><span class="sxs-lookup"><span data-stu-id="89208-163">The first command gets all of the PowerShell processes in the current session.</span></span>

<span data-ttu-id="89208-164">La deuxième commande obtient le processus PowerShell qui héberge la session active.</span><span class="sxs-lookup"><span data-stu-id="89208-164">The second command gets the PowerShell process that is hosting the current session.</span></span>

### <span data-ttu-id="89208-165">Exemple 10 : obtenir tous les processus qui ont un titre de fenêtre principale et les afficher dans une table</span><span class="sxs-lookup"><span data-stu-id="89208-165">Example 10: Get all processes that have a main window title and display them in a table</span></span>

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

<span data-ttu-id="89208-166">Cette commande obtient tous les processus qui ont un titre de fenêtre principale et les affiche dans un tableau avec l'ID de processus et le nom du processus.</span><span class="sxs-lookup"><span data-stu-id="89208-166">This command gets all the processes that have a main window title, and it displays them in a table with the process ID and the process name.</span></span>

<span data-ttu-id="89208-167">La propriété **mainWindowTitle** n’est qu’une des nombreuses propriétés utiles de l’objet **Process** qui `Get-Process` retourne.</span><span class="sxs-lookup"><span data-stu-id="89208-167">The **mainWindowTitle** property is just one of many useful properties of the **Process** object that `Get-Process` returns.</span></span> <span data-ttu-id="89208-168">Pour afficher toutes les propriétés, dirigez les résultats d’une `Get-Process` commande vers l' `Get-Member` applet de commande `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="89208-168">To view all of the properties, pipe the results of a `Get-Process` command to the `Get-Member` cmdlet `Get-Process | Get-Member`.</span></span>

## <span data-ttu-id="89208-169">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="89208-169">PARAMETERS</span></span>

### <span data-ttu-id="89208-170">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="89208-170">-ComputerName</span></span>

<span data-ttu-id="89208-171">Spécifie les ordinateurs pour lesquels cette applet de commande obtient les processus actifs.</span><span class="sxs-lookup"><span data-stu-id="89208-171">Specifies the computers for which this cmdlet gets active processes.</span></span> <span data-ttu-id="89208-172">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="89208-172">The default is the local computer.</span></span>

<span data-ttu-id="89208-173">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) d’un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="89208-173">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one or more computers.</span></span> <span data-ttu-id="89208-174">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="89208-174">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="89208-175">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89208-175">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="89208-176">Vous pouvez utiliser le paramètre **ComputerName** de cette applet de commande même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="89208-176">You can use the **ComputerName** parameter of this cmdlet even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, Id, InputObject
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89208-177">-FileVersionInfo</span><span class="sxs-lookup"><span data-stu-id="89208-177">-FileVersionInfo</span></span>

<span data-ttu-id="89208-178">Indique que cette applet de commande obtient les informations de version de fichier pour le programme qui s’exécute dans le processus.</span><span class="sxs-lookup"><span data-stu-id="89208-178">Indicates that this cmdlet gets the file version information for the program that runs in the process.</span></span>

<span data-ttu-id="89208-179">Sur Windows Vista et les versions ultérieures de Windows, vous devez ouvrir PowerShell avec l’option Exécuter en tant qu’administrateur pour utiliser ce paramètre sur les processus que vous ne possédez pas.</span><span class="sxs-lookup"><span data-stu-id="89208-179">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="89208-180">Vous ne pouvez pas utiliser les paramètres **FileVersionInfo** et **ComputerName** de l' `Get-Process` applet de commande dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="89208-180">You cannot use the **FileVersionInfo** and **ComputerName** parameters of the `Get-Process` cmdlet in the same command.</span></span>

<span data-ttu-id="89208-181">Pour obtenir les informations de version de fichier d’un processus sur un ordinateur distant, utilisez l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="89208-181">To get file version information for a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="89208-182">L’utilisation de ce paramètre revient à obtenir la propriété **propriété MainModule. FileVersionInfo** de chaque objet processus.</span><span class="sxs-lookup"><span data-stu-id="89208-182">Using this parameter is equivalent to getting the **MainModule.FileVersionInfo** property of each process object.</span></span> <span data-ttu-id="89208-183">Lorsque vous utilisez ce paramètre, `Get-Process` retourne un **FileVersionInfo** objet FileVersionInfo **System. Diagnostics. FileVersionInfo** , et non un objet processus.</span><span class="sxs-lookup"><span data-stu-id="89208-183">When you use this parameter, `Get-Process` returns a **FileVersionInfo** object **System.Diagnostics.FileVersionInfo** , not a process object.</span></span> <span data-ttu-id="89208-184">Par conséquent, vous ne pouvez pas diriger la sortie de la commande vers une applet de commande qui attend un objet processus, tel que `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="89208-184">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89208-185">-Id</span><span class="sxs-lookup"><span data-stu-id="89208-185">-Id</span></span>

<span data-ttu-id="89208-186">Spécifie un ou plusieurs processus par identificateur de processus (PID).</span><span class="sxs-lookup"><span data-stu-id="89208-186">Specifies one or more processes by process ID (PID).</span></span> <span data-ttu-id="89208-187">Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="89208-187">To specify multiple IDs, use commas to separate the IDs.</span></span> <span data-ttu-id="89208-188">Pour rechercher le PID d’un processus, tapez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="89208-188">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdWithUserName, Id
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89208-189">-IncludeUserName</span><span class="sxs-lookup"><span data-stu-id="89208-189">-IncludeUserName</span></span>

<span data-ttu-id="89208-190">Indique que la valeur UserName de l’objet **Process** est retournée avec les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="89208-190">Indicates that the UserName value of the **Process** object is returned with results of the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89208-191">-InputObject</span><span class="sxs-lookup"><span data-stu-id="89208-191">-InputObject</span></span>

<span data-ttu-id="89208-192">Spécifie un ou plusieurs objets processus.</span><span class="sxs-lookup"><span data-stu-id="89208-192">Specifies one or more process objects.</span></span> <span data-ttu-id="89208-193">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="89208-193">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObjectWithUserName, InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="89208-194">-Module</span><span class="sxs-lookup"><span data-stu-id="89208-194">-Module</span></span>

<span data-ttu-id="89208-195">Indique que cette applet de commande obtient les modules qui ont été chargés par les processus.</span><span class="sxs-lookup"><span data-stu-id="89208-195">Indicates that this cmdlet gets the modules that have been loaded by the processes.</span></span>

<span data-ttu-id="89208-196">Sur Windows Vista et les versions ultérieures de Windows, vous devez ouvrir PowerShell avec l’option **exécuter en tant qu’administrateur** pour utiliser ce paramètre sur les processus que vous ne possédez pas.</span><span class="sxs-lookup"><span data-stu-id="89208-196">On Windows Vista and later versions of Windows, you must open PowerShell with the **Run as administrator** option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="89208-197">Pour obtenir les modules qui ont été chargés par un processus sur un ordinateur distant, utilisez l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="89208-197">To get the modules that have been loaded by a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="89208-198">Ce paramètre équivaut à obtenir la propriété **modules** de chaque objet processus.</span><span class="sxs-lookup"><span data-stu-id="89208-198">This parameter is equivalent to getting the **Modules** property of each process object.</span></span> <span data-ttu-id="89208-199">Lorsque vous utilisez ce paramètre, cette applet de commande retourne un objet **ProcessModule** **System. Diagnostics. ProcessModule** , et non un objet processus.</span><span class="sxs-lookup"><span data-stu-id="89208-199">When you use this parameter, this cmdlet returns a **ProcessModule** object **System.Diagnostics.ProcessModule** , not a process object.</span></span> <span data-ttu-id="89208-200">Par conséquent, vous ne pouvez pas diriger la sortie de la commande vers une applet de commande qui attend un objet processus, tel que `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="89208-200">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

<span data-ttu-id="89208-201">Lorsque vous utilisez les paramètres *module* et **FileVersionInfo** dans la même commande, cette applet de commande retourne un objet **FileVersionInfo** avec des informations sur la version de fichier de tous les modules.</span><span class="sxs-lookup"><span data-stu-id="89208-201">When you use both the *Module* and **FileVersionInfo** parameters in the same command, this cmdlet returns a **FileVersionInfo** object with information about the file version of all modules.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89208-202">-Name</span><span class="sxs-lookup"><span data-stu-id="89208-202">-Name</span></span>

<span data-ttu-id="89208-203">Spécifie un ou plusieurs processus en fonction de leur nom de processus.</span><span class="sxs-lookup"><span data-stu-id="89208-203">Specifies one or more processes by process name.</span></span> <span data-ttu-id="89208-204">Vous pouvez taper plusieurs noms de processus (séparés par des virgules) et utiliser des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="89208-204">You can type multiple process names (separated by commas) and use wildcard characters.</span></span> <span data-ttu-id="89208-205">Le nom de paramètre (« Name ») est facultatif.</span><span class="sxs-lookup"><span data-stu-id="89208-205">The parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="89208-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89208-206">CommonParameters</span></span>

<span data-ttu-id="89208-207">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="89208-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89208-208">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="89208-208">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="89208-209">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="89208-209">INPUTS</span></span>

### <span data-ttu-id="89208-210">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="89208-210">System.Diagnostics.Process</span></span>

<span data-ttu-id="89208-211">Vous pouvez diriger un objet processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="89208-211">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="89208-212">SORTIES</span><span class="sxs-lookup"><span data-stu-id="89208-212">OUTPUTS</span></span>

### <span data-ttu-id="89208-213">System. Diagnostics. Process, System. Diagnostics. FileVersionInfo, System. Diagnostics. ProcessModule</span><span class="sxs-lookup"><span data-stu-id="89208-213">System.Diagnostics.Process, System.Diagnostics.FileVersionInfo, System.Diagnostics.ProcessModule</span></span>

<span data-ttu-id="89208-214">Par défaut, cette applet de commande retourne un objet **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="89208-214">By default, this cmdlet returns a **System.Diagnostics.Process** object.</span></span> <span data-ttu-id="89208-215">Si vous utilisez le paramètre **FileVersionInfo** , il retourne un objet **System. Diagnostics. FileVersionInfo** .</span><span class="sxs-lookup"><span data-stu-id="89208-215">If you use the **FileVersionInfo** parameter, it returns a **System.Diagnostics.FileVersionInfo** object.</span></span> <span data-ttu-id="89208-216">Si vous utilisez le paramètre **module** sans le paramètre **FileVersionInfo** , il retourne un objet **System. Diagnostics. ProcessModule** .</span><span class="sxs-lookup"><span data-stu-id="89208-216">If you use the **Module** parameter, without the **FileVersionInfo** parameter, it returns a **System.Diagnostics.ProcessModule** object.</span></span>

## <span data-ttu-id="89208-217">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="89208-217">NOTES</span></span>

- <span data-ttu-id="89208-218">Vous pouvez également faire référence à cette applet de commande à l’aide de ses alias intégrés, PS et GPS.</span><span class="sxs-lookup"><span data-stu-id="89208-218">You can also refer to this cmdlet by its built-in aliases, ps and gps.</span></span> <span data-ttu-id="89208-219">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="89208-219">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="89208-220">Sur les ordinateurs qui exécutent une version 64 bits de Windows, la version 64 bits de PowerShell obtient uniquement les modules de processus 64 bits et la version 32 bits de PowerShell obtient uniquement les modules de processus 32 bits.</span><span class="sxs-lookup"><span data-stu-id="89208-220">On computers that are running a 64-bit version of Windows, the 64-bit version of PowerShell gets only 64-bit process modules and the 32-bit version of PowerShell gets only 32-bit process modules.</span></span>
- <span data-ttu-id="89208-221">Vous pouvez utiliser les propriétés et les méthodes de l’objet Win32_Process Windows Management Instrumentation (WMI) dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89208-221">You can use the properties and methods of the Windows Management Instrumentation (WMI) Win32_Process object in PowerShell.</span></span> <span data-ttu-id="89208-222">Pour plus d’informations, consultez `Get-WmiObject` et le kit de développement logiciel (SDK) WMI.</span><span class="sxs-lookup"><span data-stu-id="89208-222">For information, see `Get-WmiObject` and the WMI SDK.</span></span>
- <span data-ttu-id="89208-223">L'affichage par défaut d'un processus est un tableau comportant les colonnes suivantes.</span><span class="sxs-lookup"><span data-stu-id="89208-223">The default display of a process is a table that includes the following columns.</span></span> <span data-ttu-id="89208-224">Pour obtenir une description de toutes les propriétés des objets process, consultez [Propriétés du processus](/dotnet/api/system.diagnostics.process).</span><span class="sxs-lookup"><span data-stu-id="89208-224">For a description of all of the properties of process objects, see [Process Properties](/dotnet/api/system.diagnostics.process).</span></span>
  - <span data-ttu-id="89208-225">Handles : nombre de handles ouverts par le processus.</span><span class="sxs-lookup"><span data-stu-id="89208-225">Handles: The number of handles that the process has opened.</span></span>
  - <span data-ttu-id="89208-226">NPM (K) : quantité de mémoire non paginée utilisée par le processus, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="89208-226">NPM(K): The amount of non-paged memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="89208-227">PM (K) : quantité de mémoire paginable utilisée par le processus, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="89208-227">PM(K): The amount of pageable memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="89208-228">WS (K) : taille de la plage de travail du processus, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="89208-228">WS(K): The size of the working set of the process, in kilobytes.</span></span>
    <span data-ttu-id="89208-229">La plage de travail inclut les pages de mémoire récemment référencées par le processus.</span><span class="sxs-lookup"><span data-stu-id="89208-229">The working set consists of the pages of memory that were recently referenced by the process.</span></span>
  - <span data-ttu-id="89208-230">Machine virtuelle (M) : quantité de mémoire virtuelle utilisée par le processus, en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="89208-230">VM(M): The amount of virtual memory that the process is using, in megabytes.</span></span>
    <span data-ttu-id="89208-231">La mémoire virtuelle inclut le stockage dans les fichiers de pagination sur le disque.</span><span class="sxs-lookup"><span data-stu-id="89208-231">Virtual memory includes storage in the paging files on disk.</span></span>
  - <span data-ttu-id="89208-232">PROCESSEUR (s) : quantité de temps processeur utilisée par le processus sur tous les processeurs, en secondes.</span><span class="sxs-lookup"><span data-stu-id="89208-232">CPU(s): The amount of processor time that the process has used on all processors, in seconds.</span></span>
  - <span data-ttu-id="89208-233">ID : ID de processus (PID) du processus.</span><span class="sxs-lookup"><span data-stu-id="89208-233">ID: The process ID (PID) of the process.</span></span>
  - <span data-ttu-id="89208-234">ProcessName : nom du processus.</span><span class="sxs-lookup"><span data-stu-id="89208-234">ProcessName: The name of the process.</span></span> <span data-ttu-id="89208-235">Pour obtenir des informations sur les concepts liés aux processus, consultez le Glossaire du Centre d'aide et de support et l'Aide du Gestionnaire des tâches.</span><span class="sxs-lookup"><span data-stu-id="89208-235">For explanations of the concepts related to processes, see the Glossary in Help and Support Center and the Help for Task Manager.</span></span>
- <span data-ttu-id="89208-236">Vous pouvez également utiliser les autres vues intégrées des processus disponibles avec `Format-Table` , comme **StartTime** et **Priority** , et vous pouvez concevoir vos propres vues.</span><span class="sxs-lookup"><span data-stu-id="89208-236">You can also use the built-in alternate views of the processes available with `Format-Table`, such as **StartTime** and **Priority** , and you can design your own views.</span></span>

## <span data-ttu-id="89208-237">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="89208-237">RELATED LINKS</span></span>

[<span data-ttu-id="89208-238">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="89208-238">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="89208-239">Get-Process</span><span class="sxs-lookup"><span data-stu-id="89208-239">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="89208-240">Start-Process</span><span class="sxs-lookup"><span data-stu-id="89208-240">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="89208-241">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="89208-241">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="89208-242">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="89208-242">Wait-Process</span></span>](Wait-Process.md)
