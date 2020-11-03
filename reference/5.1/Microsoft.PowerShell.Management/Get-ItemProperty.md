---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203997"
---
# <span data-ttu-id="4546a-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-103">Get-ItemProperty</span></span>

## <span data-ttu-id="4546a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4546a-104">SYNOPSIS</span></span>
<span data-ttu-id="4546a-105">Obtient les propriétés de l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="4546a-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="4546a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4546a-106">SYNTAX</span></span>

### <span data-ttu-id="4546a-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4546a-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="4546a-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4546a-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="4546a-109">Description</span><span class="sxs-lookup"><span data-stu-id="4546a-109">DESCRIPTION</span></span>

<span data-ttu-id="4546a-110">L' `Get-ItemProperty` applet de commande obtient les propriétés des éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4546a-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="4546a-111">Par exemple, vous pouvez utiliser cette applet de commande pour obtenir la valeur de la propriété LastAccessTime d’un objet fichier.</span><span class="sxs-lookup"><span data-stu-id="4546a-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span>
<span data-ttu-id="4546a-112">Vous pouvez également utiliser cette applet de commande pour afficher les entrées de Registre et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="4546a-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="4546a-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4546a-113">EXAMPLES</span></span>

### <span data-ttu-id="4546a-114">Exemple 1 : obtenir des informations sur un répertoire spécifique</span><span class="sxs-lookup"><span data-stu-id="4546a-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="4546a-115">Cette commande obtient des informations sur le répertoire « C:\Windows ».</span><span class="sxs-lookup"><span data-stu-id="4546a-115">This command gets information about the "C:\Windows" directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="4546a-116">Exemple 2 : obtenir les propriétés d’un fichier spécifique</span><span class="sxs-lookup"><span data-stu-id="4546a-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="4546a-117">Cette commande obtient les propriétés du fichier « C:\Test\Weather.xls ».</span><span class="sxs-lookup"><span data-stu-id="4546a-117">This command gets the properties of the "C:\Test\Weather.xls" file.</span></span>
<span data-ttu-id="4546a-118">Le résultat est dirigé vers l' `Format-List` applet de commande pour afficher la sortie sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="4546a-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="4546a-119">Exemple 3 : afficher le nom de la valeur et les données des entrées de Registre dans une sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="4546a-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="4546a-120">Cette commande affiche le nom de la valeur et les données de chacune des entrées de Registre contenues dans la sous-clé de Registre « CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="4546a-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="4546a-121">Notez que la commande requiert l’existence d’un lecteur PowerShell nommé `HKLM:` qui est mappé à la ruche « HKEY_LOCAL_MACHINE » du Registre.</span><span class="sxs-lookup"><span data-stu-id="4546a-121">Note that the command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
<span data-ttu-id="4546a-122">Un lecteur avec ce nom et ce mappage est disponible dans PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="4546a-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
<span data-ttu-id="4546a-123">Le chemin d'accès à cette sous-clé de Registre peut également être spécifié à l'aide du chemin d'accès suivant, commençant par le nom du fournisseur suivi de deux deux-points :</span><span class="sxs-lookup"><span data-stu-id="4546a-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>

<span data-ttu-id="4546a-124">« Registry :: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="4546a-124">"Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### <span data-ttu-id="4546a-125">Exemple 4 : obtenir le nom de la valeur et les données d’une entrée de Registre dans une sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="4546a-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="4546a-126">Cette commande obtient le nom et les données de la valeur de l’entrée de Registre « ProgramFilesDir figurant » dans la sous-clé de Registre « CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="4546a-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="4546a-127">La commande utilise le paramètre **path** pour spécifier la sous-clé et le paramètre Name pour spécifier le nom de la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="4546a-127">The command uses the **Path** parameter to specify the subkey and the Name parameter to specify the value name of the entry.</span></span>

<span data-ttu-id="4546a-128">La commande utilise une graduation ou un accent grave ( \` ), le caractère de continuation PowerShell, pour continuer la commande sur la deuxième ligne.</span><span class="sxs-lookup"><span data-stu-id="4546a-128">The command uses a back tick or grave accent (\`), the PowerShell continuation character, to continue the command on the second line.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="4546a-129">Exemple 5 : obtenir les noms de valeur et les données des entrées de Registre dans une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="4546a-129">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="4546a-130">Cette commande obtient les noms de valeur et les données des entrées de Registre dans la clé de Registre « PowerShellEngine ».</span><span class="sxs-lookup"><span data-stu-id="4546a-130">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span>
<span data-ttu-id="4546a-131">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="4546a-131">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### <span data-ttu-id="4546a-132">Exemple 6 : obtenir, mettre en forme et afficher les résultats des valeurs et des données de Registre</span><span class="sxs-lookup"><span data-stu-id="4546a-132">Example 6: Get, format, and display the results of registry values and data</span></span>

<span data-ttu-id="4546a-133">Cet exemple montre comment mettre en forme la sortie d’une `Get-ItemProperty` commande dans une liste pour faciliter l’affichage des valeurs et des données de Registre et pour faciliter l’interprétation des résultats.</span><span class="sxs-lookup"><span data-stu-id="4546a-133">This example shows how to format the output of a `Get-ItemProperty` command in a list to make it easy to see the registry values and data and to make it easy to interpret the results.</span></span>

<span data-ttu-id="4546a-134">La première commande utilise l' `Get-ItemProperty` applet de commande pour récupérer les entrées de Registre dans la sous-clé **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="4546a-134">The first command uses the `Get-ItemProperty` cmdlet to get the registry entries in the **Microsoft.PowerShell** subkey.</span></span>
<span data-ttu-id="4546a-135">Cette sous-clé stocke les options de l’interpréteur de commandes par défaut pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4546a-135">This subkey stores options for the default shell for PowerShell.</span></span>
<span data-ttu-id="4546a-136">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="4546a-136">The results are shown in the following sample output.</span></span>

<span data-ttu-id="4546a-137">La sortie indique qu’il existe deux entrées de Registre, « path » et « ExecutionPolicy ».</span><span class="sxs-lookup"><span data-stu-id="4546a-137">The output shows that there are two registry entries, "Path" and "ExecutionPolicy".</span></span>
<span data-ttu-id="4546a-138">Lorsqu'une clé de Registre contient moins de cinq entrées, elle s'affiche par défaut dans un tableau, mais sa lecture est souvent plus facile dans une liste.</span><span class="sxs-lookup"><span data-stu-id="4546a-138">When a registry key contains fewer than five entries, by default it is displayed in a table, but it is often easier to view in a list.</span></span>

<span data-ttu-id="4546a-139">La deuxième commande utilise la même `Get-ItemProperty` commande.</span><span class="sxs-lookup"><span data-stu-id="4546a-139">The second command uses the same `Get-ItemProperty` command.</span></span>
<span data-ttu-id="4546a-140">Toutefois, cette fois-ci, la commande utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats de la commande à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="4546a-140">However, this time, the command uses a pipeline operator (`|`) to send the results of the command to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="4546a-141">La `Format-List` commande utilise le paramètre Property avec la valeur' \* ' (All) pour afficher toutes les propriétés des objets dans une liste.</span><span class="sxs-lookup"><span data-stu-id="4546a-141">The `Format-List` command uses the Property parameter with a value of '\*' (all) to display all of the properties of the objects in a list.</span></span>
<span data-ttu-id="4546a-142">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="4546a-142">The results are shown in the following sample output.</span></span>

<span data-ttu-id="4546a-143">L’affichage qui en résulte montre les entrées de Registre « Path » et « ExecutionPolicy », ainsi que plusieurs propriétés moins familières de l’objet de clé de registre.</span><span class="sxs-lookup"><span data-stu-id="4546a-143">The resulting display shows the "Path" and "ExecutionPolicy" registry entries, along with several less familiar properties of the registry key object.</span></span>
<span data-ttu-id="4546a-144">Les autres propriétés, précédées de PS, sont des propriétés d’objets personnalisés PowerShell, tels que les objets qui représentent les clés de registre.</span><span class="sxs-lookup"><span data-stu-id="4546a-144">The other properties, prefixed with PS, are properties of PowerShell custom objects, such as the objects that represent the registry keys.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## <span data-ttu-id="4546a-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4546a-145">PARAMETERS</span></span>

### <span data-ttu-id="4546a-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="4546a-146">-Credential</span></span>

<span data-ttu-id="4546a-147">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="4546a-147">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="4546a-148">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="4546a-148">The default is the current user.</span></span>

<span data-ttu-id="4546a-149">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="4546a-149">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="4546a-150">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4546a-150">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="4546a-151">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4546a-151">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4546a-152">-Exclude</span><span class="sxs-lookup"><span data-stu-id="4546a-152">-Exclude</span></span>

<span data-ttu-id="4546a-153">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="4546a-153">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="4546a-154">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="4546a-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="4546a-155">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="4546a-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="4546a-156">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4546a-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4546a-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="4546a-157">-Filter</span></span>

<span data-ttu-id="4546a-158">Spécifie un filtre dans le format ou la langue du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4546a-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="4546a-159">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="4546a-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="4546a-160">La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4546a-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="4546a-161">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="4546a-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4546a-162">-Include</span><span class="sxs-lookup"><span data-stu-id="4546a-162">-Include</span></span>

<span data-ttu-id="4546a-163">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="4546a-163">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="4546a-164">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="4546a-164">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="4546a-165">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="4546a-165">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="4546a-166">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4546a-166">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4546a-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4546a-167">-LiteralPath</span></span>

<span data-ttu-id="4546a-168">Spécifie le chemin d’accès à l’emplacement actuel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="4546a-168">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="4546a-169">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="4546a-169">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="4546a-170">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="4546a-170">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="4546a-171">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4546a-171">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="4546a-172">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4546a-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4546a-173">-Name</span><span class="sxs-lookup"><span data-stu-id="4546a-173">-Name</span></span>

<span data-ttu-id="4546a-174">Spécifie le nom des propriétés à récupérer.</span><span class="sxs-lookup"><span data-stu-id="4546a-174">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4546a-175">-Path</span><span class="sxs-lookup"><span data-stu-id="4546a-175">-Path</span></span>

<span data-ttu-id="4546a-176">Spécifie le chemin d'accès aux éléments.</span><span class="sxs-lookup"><span data-stu-id="4546a-176">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4546a-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="4546a-177">-UseTransaction</span></span>

<span data-ttu-id="4546a-178">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="4546a-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="4546a-179">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="4546a-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="4546a-180">Pour plus d’informations, consultez comprend la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="4546a-180">For more information, see Includes the command in the active transaction.</span></span>
<span data-ttu-id="4546a-181">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="4546a-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="4546a-182">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="4546a-182">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4546a-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4546a-183">CommonParameters</span></span>

<span data-ttu-id="4546a-184">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="4546a-184">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4546a-185">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4546a-185">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4546a-186">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4546a-186">INPUTS</span></span>

### <span data-ttu-id="4546a-187">System.String</span><span class="sxs-lookup"><span data-stu-id="4546a-187">System.String</span></span>

<span data-ttu-id="4546a-188">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="4546a-188">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="4546a-189">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4546a-189">OUTPUTS</span></span>

### <span data-ttu-id="4546a-190">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="4546a-190">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="4546a-191">`Get-ItemProperty` retourne un objet pour chaque propriété d’élément qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="4546a-191">`Get-ItemProperty` returns an object for each item property that it gets.</span></span>
<span data-ttu-id="4546a-192">Le type d'objet dépend de l'objet récupéré.</span><span class="sxs-lookup"><span data-stu-id="4546a-192">The object type depends on the object that is retrieved.</span></span>
<span data-ttu-id="4546a-193">Par exemple, dans un lecteur du système de fichiers, un fichier ou un dossier peut être retourné.</span><span class="sxs-lookup"><span data-stu-id="4546a-193">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="4546a-194">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4546a-194">NOTES</span></span>

<span data-ttu-id="4546a-195">L' `Get-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4546a-195">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4546a-196">Pour répertorier les fournisseurs disponibles dans votre session, tapez « `Get-PSProvider` ».</span><span class="sxs-lookup"><span data-stu-id="4546a-196">To list the providers available in your session, type "`Get-PSProvider`".</span></span> <span data-ttu-id="4546a-197">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="4546a-197">For more information, see about_Providers.</span></span>

## <span data-ttu-id="4546a-198">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4546a-198">RELATED LINKS</span></span>

[<span data-ttu-id="4546a-199">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-199">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="4546a-200">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-200">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="4546a-201">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-201">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="4546a-202">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-202">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="4546a-203">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-203">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="4546a-204">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-204">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="4546a-205">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4546a-205">Set-ItemProperty</span></span>](Set-ItemProperty.md)
