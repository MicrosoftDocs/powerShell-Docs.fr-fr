---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 71602cb0621c835257f556a0a9db15bd754a3aee
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206326"
---
# <span data-ttu-id="d46d1-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="d46d1-103">Out-File</span></span>

## <span data-ttu-id="d46d1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d46d1-104">SYNOPSIS</span></span>
<span data-ttu-id="d46d1-105">Envoie la sortie vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="d46d1-105">Sends output to a file.</span></span>

## <span data-ttu-id="d46d1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d46d1-106">SYNTAX</span></span>

### <span data-ttu-id="d46d1-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d46d1-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <string>] [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d46d1-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="d46d1-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <string>] -LiteralPath <string> [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d46d1-109">Description</span><span class="sxs-lookup"><span data-stu-id="d46d1-109">DESCRIPTION</span></span>

<span data-ttu-id="d46d1-110">L' `Out-File` applet de commande envoie la sortie vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="d46d1-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="d46d1-111">Il utilise implicitement le système de mise en forme de PowerShell pour écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d46d1-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="d46d1-112">Le fichier reçoit la même représentation d’affichage que le terminal.</span><span class="sxs-lookup"><span data-stu-id="d46d1-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="d46d1-113">Cela signifie que la sortie peut ne pas être idéale pour le traitement par programme, sauf si tous les objets d’entrée sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="d46d1-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="d46d1-114">Lorsque vous devez spécifier des paramètres pour la sortie, utilisez `Out-File` plutôt que l’opérateur de redirection ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="d46d1-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="d46d1-115">Pour plus d’informations sur la redirection, consultez [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span><span class="sxs-lookup"><span data-stu-id="d46d1-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="d46d1-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d46d1-116">EXAMPLES</span></span>

### <span data-ttu-id="d46d1-117">Exemple 1 : envoyer une sortie et créer un fichier</span><span class="sxs-lookup"><span data-stu-id="d46d1-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="d46d1-118">Cet exemple montre comment envoyer une liste des processus de l’ordinateur local à un fichier.</span><span class="sxs-lookup"><span data-stu-id="d46d1-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="d46d1-119">Si le fichier n’existe pas, `Out-File` crée le fichier dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="d46d1-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

<span data-ttu-id="d46d1-120">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d46d1-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="d46d1-121">Les objets **processus** sont envoyés dans le pipeline à l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="d46d1-122">`Out-File` utilise le paramètre **filePath** et crée un fichier dans le répertoire actif nommé **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="d46d1-123">La `Get-Content` commande obtient le contenu du fichier et l’affiche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46d1-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="d46d1-124">Exemple 2 : empêcher le remplacement d’un fichier existant</span><span class="sxs-lookup"><span data-stu-id="d46d1-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="d46d1-125">Cet exemple empêche le remplacement d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="d46d1-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="d46d1-126">Par défaut, `Out-File` remplace les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="d46d1-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="d46d1-127">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d46d1-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="d46d1-128">Les objets **processus** sont envoyés dans le pipeline à l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="d46d1-129">`Out-File` utilise le paramètre **filePath** et tente d’écrire dans un fichier dans le répertoire actif nommé **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="d46d1-130">Le paramètre **NoClobber** empêche le fichier d’être remplacé et affiche un message indiquant que le fichier existe déjà.</span><span class="sxs-lookup"><span data-stu-id="d46d1-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="d46d1-131">Exemple 3 : envoyer la sortie vers un fichier au format ASCII</span><span class="sxs-lookup"><span data-stu-id="d46d1-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="d46d1-132">Cet exemple montre comment encoder une sortie avec un type d’encodage spécifique.</span><span class="sxs-lookup"><span data-stu-id="d46d1-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="d46d1-133">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d46d1-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="d46d1-134">Les objets **processus** sont stockés dans la variable, `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="d46d1-135">`Out-File` utilise le paramètre **filePath** et crée un fichier dans le répertoire actif nommé **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="d46d1-136">Le paramètre **InputObject** passe les objets de processus dans `$Procs` au fichier **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt** .</span></span> <span data-ttu-id="d46d1-137">Le paramètre **Encoding** convertit la sortie au format **ASCII** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="d46d1-138">Le paramètre **Width** limite chaque ligne du fichier à 50 caractères, de sorte que certaines données peuvent être tronquées.</span><span class="sxs-lookup"><span data-stu-id="d46d1-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="d46d1-139">Exemple 4 : utiliser un fournisseur et envoyer une sortie vers un fichier</span><span class="sxs-lookup"><span data-stu-id="d46d1-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="d46d1-140">Cet exemple montre comment utiliser l' `Out-File` applet de commande lorsque vous n’êtes pas dans un lecteur du fournisseur **FileSystem** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="d46d1-141">Utilisez l' `Get-PSProvider` applet de commande pour afficher les fournisseurs sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d46d1-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="d46d1-142">Pour plus d'informations, consultez [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d46d1-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

<span data-ttu-id="d46d1-143">La `Set-Location` commande utilise le paramètre **path** pour définir l’emplacement actuel sur le fournisseur Registry `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="d46d1-144">L' `Get-Location` applet de commande affiche le chemin d’accès complet de `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="d46d1-145">`Get-ChildItem` envoie des objets dans le pipeline à l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="d46d1-146">`Out-File` utilise le paramètre **filePath** pour spécifier le chemin d’accès complet et le nom de fichier de la sortie, **C:\TestDir\AliasNames.txt** .</span><span class="sxs-lookup"><span data-stu-id="d46d1-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt** .</span></span> <span data-ttu-id="d46d1-147">L' `Get-Content` applet de commande utilise le paramètre **path** et affiche le contenu du fichier dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46d1-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="d46d1-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d46d1-148">PARAMETERS</span></span>

### <span data-ttu-id="d46d1-149">-Append</span><span class="sxs-lookup"><span data-stu-id="d46d1-149">-Append</span></span>

<span data-ttu-id="d46d1-150">Ajoute la sortie à la fin d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="d46d1-150">Adds the output to the end of an existing file.</span></span> <span data-ttu-id="d46d1-151">Si aucun **encodage** n’est spécifié, l’applet de commande utilise l’encodage par défaut.</span><span class="sxs-lookup"><span data-stu-id="d46d1-151">If no **Encoding** is specified, the cmdlet uses the default encoding.</span></span> <span data-ttu-id="d46d1-152">Cet encodage peut ne pas correspondre à l’encodage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="d46d1-152">That encoding may not match the encoding of the target file.</span></span> <span data-ttu-id="d46d1-153">Il s’agit du même comportement que l’opérateur de redirection ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="d46d1-153">This is the same behavior as the redirection operator (`>>`).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-154">-Encoding</span><span class="sxs-lookup"><span data-stu-id="d46d1-154">-Encoding</span></span>

<span data-ttu-id="d46d1-155">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="d46d1-155">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="d46d1-156">La valeur par défaut est `unicode`.</span><span class="sxs-lookup"><span data-stu-id="d46d1-156">The default value is `unicode`.</span></span>

<span data-ttu-id="d46d1-157">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d46d1-157">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="d46d1-158">`ascii` Utilise le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="d46d1-158">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="d46d1-159">`bigendianunicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="d46d1-159">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="d46d1-160">`default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).</span><span class="sxs-lookup"><span data-stu-id="d46d1-160">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="d46d1-161">`oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="d46d1-161">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="d46d1-162">`string` Identique à `unicode`.</span><span class="sxs-lookup"><span data-stu-id="d46d1-162">`string` Same as `unicode`.</span></span>
- <span data-ttu-id="d46d1-163">`unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="d46d1-163">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="d46d1-164">`unknown` Identique à `unicode`.</span><span class="sxs-lookup"><span data-stu-id="d46d1-164">`unknown` Same as `unicode`.</span></span>
- <span data-ttu-id="d46d1-165">`utf7` Utilise UTF-7.</span><span class="sxs-lookup"><span data-stu-id="d46d1-165">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="d46d1-166">`utf8` Utilise UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d46d1-166">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="d46d1-167">`utf32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="d46d1-167">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: 1
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-168">-FilePath</span><span class="sxs-lookup"><span data-stu-id="d46d1-168">-FilePath</span></span>

<span data-ttu-id="d46d1-169">Spécifie le chemin d'accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-169">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-170">-Force</span><span class="sxs-lookup"><span data-stu-id="d46d1-170">-Force</span></span>

<span data-ttu-id="d46d1-171">Remplace l’attribut de lecture seule et remplace un fichier en lecture seule existant.</span><span class="sxs-lookup"><span data-stu-id="d46d1-171">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="d46d1-172">Le paramètre **force** ne remplace pas les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d46d1-172">The **Force** parameter does not override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-173">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d46d1-173">-InputObject</span></span>

<span data-ttu-id="d46d1-174">Spécifie les objets à écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d46d1-174">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="d46d1-175">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="d46d1-175">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="d46d1-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d46d1-176">-LiteralPath</span></span>

<span data-ttu-id="d46d1-177">Spécifie le chemin d'accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-177">Specifies the path to the output file.</span></span> <span data-ttu-id="d46d1-178">Le paramètre **LiteralPath** est utilisé exactement tel qu’il est tapé.</span><span class="sxs-lookup"><span data-stu-id="d46d1-178">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="d46d1-179">Les caractères génériques ne sont pas acceptés.</span><span class="sxs-lookup"><span data-stu-id="d46d1-179">Wildcard characters are not accepted.</span></span> <span data-ttu-id="d46d1-180">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="d46d1-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d46d1-181">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d46d1-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="d46d1-182">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="d46d1-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-183">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="d46d1-183">-NoClobber</span></span>

<span data-ttu-id="d46d1-184">**NoClobber** empêche le remplacement d’un fichier existant et affiche un message indiquant que le fichier existe déjà.</span><span class="sxs-lookup"><span data-stu-id="d46d1-184">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="d46d1-185">Par défaut, si un fichier existe dans le chemin d’accès spécifié, `Out-File` remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="d46d1-185">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-186">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="d46d1-186">-NoNewline</span></span>

<span data-ttu-id="d46d1-187">Spécifie que le contenu écrit dans le fichier ne se termine pas par un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="d46d1-187">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="d46d1-188">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-188">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="d46d1-189">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-189">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="d46d1-190">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-190">No newline is added after the last output string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-191">-Largeur</span><span class="sxs-lookup"><span data-stu-id="d46d1-191">-Width</span></span>

<span data-ttu-id="d46d1-192">Spécifie le nombre de caractères dans chaque ligne de la sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-192">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="d46d1-193">Tous les caractères supplémentaires sont tronqués, pas renvoyés à la ligne.</span><span class="sxs-lookup"><span data-stu-id="d46d1-193">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="d46d1-194">Si ce paramètre n’est pas utilisé, la largeur est déterminée par les caractéristiques de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="d46d1-194">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="d46d1-195">La valeur par défaut de la console PowerShell est de 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="d46d1-195">The default for the PowerShell console is 80 characters.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d46d1-196">-Confirm</span></span>

<span data-ttu-id="d46d1-197">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d46d1-197">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d46d1-198">-WhatIf</span></span>

<span data-ttu-id="d46d1-199">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d46d1-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d46d1-200">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d46d1-200">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d46d1-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d46d1-201">CommonParameters</span></span>

<span data-ttu-id="d46d1-202">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d46d1-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d46d1-203">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d46d1-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d46d1-204">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d46d1-204">INPUTS</span></span>

### <span data-ttu-id="d46d1-205">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="d46d1-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d46d1-206">Vous pouvez diriger n’importe quel objet vers `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="d46d1-206">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="d46d1-207">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d46d1-207">OUTPUTS</span></span>

### <span data-ttu-id="d46d1-208">Aucun</span><span class="sxs-lookup"><span data-stu-id="d46d1-208">None</span></span>

<span data-ttu-id="d46d1-209">`Out-File` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="d46d1-209">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="d46d1-210">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d46d1-210">NOTES</span></span>

<span data-ttu-id="d46d1-211">Les objets d’entrée sont mis en forme automatiquement comme ils le seraient dans le terminal, mais vous pouvez utiliser une `Format-*` applet de commande pour contrôler explicitement la mise en forme de la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d46d1-211">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="d46d1-212">Par exemple : `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="d46d1-212">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="d46d1-213">Pour envoyer la sortie d’une commande PowerShell à l’applet de commande `Out-File` , utilisez le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d46d1-213">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="d46d1-214">Vous pouvez également stocker les données dans une variable et utiliser le paramètre **InputObject** pour passer des données à l' `Out-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d46d1-214">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="d46d1-215">`Out-File` enregistre les données dans un fichier, mais ne produit pas d’objets de sortie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d46d1-215">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="d46d1-216">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d46d1-216">RELATED LINKS</span></span>

[<span data-ttu-id="d46d1-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d46d1-217">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="d46d1-218">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="d46d1-218">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="d46d1-219">Out-Default</span><span class="sxs-lookup"><span data-stu-id="d46d1-219">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="d46d1-220">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="d46d1-220">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="d46d1-221">Out-Host</span><span class="sxs-lookup"><span data-stu-id="d46d1-221">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="d46d1-222">Out-Null</span><span class="sxs-lookup"><span data-stu-id="d46d1-222">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="d46d1-223">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="d46d1-223">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="d46d1-224">Out-String</span><span class="sxs-lookup"><span data-stu-id="d46d1-224">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="d46d1-225">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="d46d1-225">Tee-Object</span></span>](Tee-Object.md)
