---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: e7437505bbe5fbbcfb38e9957f75ac45287d9b26
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206306"
---
# <span data-ttu-id="46c1e-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="46c1e-103">Out-File</span></span>

## <span data-ttu-id="46c1e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="46c1e-104">SYNOPSIS</span></span>
<span data-ttu-id="46c1e-105">Envoie la sortie vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="46c1e-105">Sends output to a file.</span></span>

## <span data-ttu-id="46c1e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46c1e-106">SYNTAX</span></span>

### <span data-ttu-id="46c1e-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="46c1e-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46c1e-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="46c1e-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="46c1e-109">Description</span><span class="sxs-lookup"><span data-stu-id="46c1e-109">DESCRIPTION</span></span>

<span data-ttu-id="46c1e-110">L' `Out-File` applet de commande envoie la sortie vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="46c1e-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="46c1e-111">Il utilise implicitement le système de mise en forme de PowerShell pour écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="46c1e-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="46c1e-112">Le fichier reçoit la même représentation d’affichage que le terminal.</span><span class="sxs-lookup"><span data-stu-id="46c1e-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="46c1e-113">Cela signifie que la sortie peut ne pas être idéale pour le traitement par programme, sauf si tous les objets d’entrée sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="46c1e-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="46c1e-114">Lorsque vous devez spécifier des paramètres pour la sortie, utilisez `Out-File` plutôt que l’opérateur de redirection ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="46c1e-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="46c1e-115">Pour plus d’informations sur la redirection, consultez [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span><span class="sxs-lookup"><span data-stu-id="46c1e-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="46c1e-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="46c1e-116">EXAMPLES</span></span>

### <span data-ttu-id="46c1e-117">Exemple 1 : envoyer une sortie et créer un fichier</span><span class="sxs-lookup"><span data-stu-id="46c1e-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="46c1e-118">Cet exemple montre comment envoyer une liste des processus de l’ordinateur local à un fichier.</span><span class="sxs-lookup"><span data-stu-id="46c1e-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="46c1e-119">Si le fichier n’existe pas, `Out-File` crée le fichier dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="46c1e-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

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

<span data-ttu-id="46c1e-120">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="46c1e-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="46c1e-121">Les objets **processus** sont envoyés dans le pipeline à l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="46c1e-122">`Out-File` utilise le paramètre **filePath** et crée un fichier dans le répertoire actif nommé **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="46c1e-123">La `Get-Content` commande obtient le contenu du fichier et l’affiche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46c1e-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="46c1e-124">Exemple 2 : empêcher le remplacement d’un fichier existant</span><span class="sxs-lookup"><span data-stu-id="46c1e-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="46c1e-125">Cet exemple empêche le remplacement d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="46c1e-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="46c1e-126">Par défaut, `Out-File` remplace les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="46c1e-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="46c1e-127">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="46c1e-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="46c1e-128">Les objets **processus** sont envoyés dans le pipeline à l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="46c1e-129">`Out-File` utilise le paramètre **filePath** et tente d’écrire dans un fichier dans le répertoire actif nommé **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="46c1e-130">Le paramètre **NoClobber** empêche le fichier d’être remplacé et affiche un message indiquant que le fichier existe déjà.</span><span class="sxs-lookup"><span data-stu-id="46c1e-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="46c1e-131">Exemple 3 : envoyer la sortie vers un fichier au format ASCII</span><span class="sxs-lookup"><span data-stu-id="46c1e-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="46c1e-132">Cet exemple montre comment encoder une sortie avec un type d’encodage spécifique.</span><span class="sxs-lookup"><span data-stu-id="46c1e-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="46c1e-133">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="46c1e-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="46c1e-134">Les objets **processus** sont stockés dans la variable, `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="46c1e-135">`Out-File` utilise le paramètre **filePath** et crée un fichier dans le répertoire actif nommé **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="46c1e-136">Le paramètre **InputObject** passe les objets de processus dans `$Procs` au fichier **Process.txt** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt** .</span></span> <span data-ttu-id="46c1e-137">Le paramètre **Encoding** convertit la sortie au format **ASCII** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="46c1e-138">Le paramètre **Width** limite chaque ligne du fichier à 50 caractères, de sorte que certaines données peuvent être tronquées.</span><span class="sxs-lookup"><span data-stu-id="46c1e-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="46c1e-139">Exemple 4 : utiliser un fournisseur et envoyer une sortie vers un fichier</span><span class="sxs-lookup"><span data-stu-id="46c1e-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="46c1e-140">Cet exemple montre comment utiliser l' `Out-File` applet de commande lorsque vous n’êtes pas dans un lecteur du fournisseur **FileSystem** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="46c1e-141">Utilisez l' `Get-PSProvider` applet de commande pour afficher les fournisseurs sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="46c1e-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="46c1e-142">Pour plus d'informations, consultez [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="46c1e-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

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

<span data-ttu-id="46c1e-143">La `Set-Location` commande utilise le paramètre **path** pour définir l’emplacement actuel sur le fournisseur Registry `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="46c1e-144">L' `Get-Location` applet de commande affiche le chemin d’accès complet de `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="46c1e-145">`Get-ChildItem` envoie des objets dans le pipeline à l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="46c1e-146">`Out-File` utilise le paramètre **filePath** pour spécifier le chemin d’accès complet et le nom de fichier de la sortie, **C:\TestDir\AliasNames.txt** .</span><span class="sxs-lookup"><span data-stu-id="46c1e-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt** .</span></span> <span data-ttu-id="46c1e-147">L' `Get-Content` applet de commande utilise le paramètre **path** et affiche le contenu du fichier dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46c1e-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="46c1e-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46c1e-148">PARAMETERS</span></span>

### <span data-ttu-id="46c1e-149">-Append</span><span class="sxs-lookup"><span data-stu-id="46c1e-149">-Append</span></span>

<span data-ttu-id="46c1e-150">Ajoute la sortie à la fin d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="46c1e-150">Adds the output to the end of an existing file.</span></span>

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

### <span data-ttu-id="46c1e-151">-Encoding</span><span class="sxs-lookup"><span data-stu-id="46c1e-151">-Encoding</span></span>

<span data-ttu-id="46c1e-152">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="46c1e-152">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="46c1e-153">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="46c1e-153">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="46c1e-154">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="46c1e-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="46c1e-155">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="46c1e-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="46c1e-156">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="46c1e-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="46c1e-157">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="46c1e-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="46c1e-158">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="46c1e-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="46c1e-159">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="46c1e-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="46c1e-160">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="46c1e-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="46c1e-161">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="46c1e-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="46c1e-162">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="46c1e-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="46c1e-163">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="46c1e-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="46c1e-164">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="46c1e-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="46c1e-165">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="46c1e-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46c1e-166">-FilePath</span><span class="sxs-lookup"><span data-stu-id="46c1e-166">-FilePath</span></span>

<span data-ttu-id="46c1e-167">Spécifie le chemin d'accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-167">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46c1e-168">-Force</span><span class="sxs-lookup"><span data-stu-id="46c1e-168">-Force</span></span>

<span data-ttu-id="46c1e-169">Remplace l’attribut de lecture seule et remplace un fichier en lecture seule existant.</span><span class="sxs-lookup"><span data-stu-id="46c1e-169">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="46c1e-170">Le paramètre **force** ne remplace pas les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="46c1e-170">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="46c1e-171">-InputObject</span><span class="sxs-lookup"><span data-stu-id="46c1e-171">-InputObject</span></span>

<span data-ttu-id="46c1e-172">Spécifie les objets à écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="46c1e-172">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="46c1e-173">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="46c1e-173">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="46c1e-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="46c1e-174">-LiteralPath</span></span>

<span data-ttu-id="46c1e-175">Spécifie le chemin d'accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-175">Specifies the path to the output file.</span></span> <span data-ttu-id="46c1e-176">Le paramètre **LiteralPath** est utilisé exactement tel qu’il est tapé.</span><span class="sxs-lookup"><span data-stu-id="46c1e-176">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="46c1e-177">Les caractères génériques ne sont pas acceptés.</span><span class="sxs-lookup"><span data-stu-id="46c1e-177">Wildcard characters are not accepted.</span></span> <span data-ttu-id="46c1e-178">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="46c1e-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="46c1e-179">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="46c1e-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="46c1e-180">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="46c1e-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="46c1e-181">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="46c1e-181">-NoClobber</span></span>

<span data-ttu-id="46c1e-182">**NoClobber** empêche le remplacement d’un fichier existant et affiche un message indiquant que le fichier existe déjà.</span><span class="sxs-lookup"><span data-stu-id="46c1e-182">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="46c1e-183">Par défaut, si un fichier existe dans le chemin d’accès spécifié, `Out-File` remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="46c1e-183">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="46c1e-184">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="46c1e-184">-NoNewline</span></span>

<span data-ttu-id="46c1e-185">Spécifie que le contenu écrit dans le fichier ne se termine pas par un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="46c1e-185">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="46c1e-186">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-186">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="46c1e-187">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-187">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="46c1e-188">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-188">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="46c1e-189">-Largeur</span><span class="sxs-lookup"><span data-stu-id="46c1e-189">-Width</span></span>

<span data-ttu-id="46c1e-190">Spécifie le nombre de caractères dans chaque ligne de la sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-190">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="46c1e-191">Tous les caractères supplémentaires sont tronqués, pas renvoyés à la ligne.</span><span class="sxs-lookup"><span data-stu-id="46c1e-191">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="46c1e-192">Si ce paramètre n’est pas utilisé, la largeur est déterminée par les caractéristiques de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="46c1e-192">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="46c1e-193">La valeur par défaut de la console PowerShell est de 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="46c1e-193">The default for the PowerShell console is 80 characters.</span></span>

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

### <span data-ttu-id="46c1e-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="46c1e-194">-Confirm</span></span>

<span data-ttu-id="46c1e-195">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="46c1e-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="46c1e-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="46c1e-196">-WhatIf</span></span>

<span data-ttu-id="46c1e-197">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="46c1e-197">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="46c1e-198">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="46c1e-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="46c1e-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46c1e-199">CommonParameters</span></span>

<span data-ttu-id="46c1e-200">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46c1e-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46c1e-201">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="46c1e-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46c1e-202">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="46c1e-202">INPUTS</span></span>

### <span data-ttu-id="46c1e-203">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="46c1e-203">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="46c1e-204">Vous pouvez diriger n’importe quel objet vers `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="46c1e-204">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="46c1e-205">SORTIES</span><span class="sxs-lookup"><span data-stu-id="46c1e-205">OUTPUTS</span></span>

### <span data-ttu-id="46c1e-206">Aucun</span><span class="sxs-lookup"><span data-stu-id="46c1e-206">None</span></span>

<span data-ttu-id="46c1e-207">`Out-File` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="46c1e-207">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="46c1e-208">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="46c1e-208">NOTES</span></span>

<span data-ttu-id="46c1e-209">Les objets d’entrée sont mis en forme automatiquement comme ils le seraient dans le terminal, mais vous pouvez utiliser une `Format-*` applet de commande pour contrôler explicitement la mise en forme de la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="46c1e-209">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="46c1e-210">Par exemple : `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="46c1e-210">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="46c1e-211">Pour envoyer la sortie d’une commande PowerShell à l’applet de commande `Out-File` , utilisez le pipeline.</span><span class="sxs-lookup"><span data-stu-id="46c1e-211">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="46c1e-212">Vous pouvez également stocker les données dans une variable et utiliser le paramètre **InputObject** pour passer des données à l' `Out-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="46c1e-212">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="46c1e-213">`Out-File` enregistre les données dans un fichier, mais ne produit pas d’objets de sortie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="46c1e-213">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="46c1e-214">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="46c1e-214">RELATED LINKS</span></span>

[<span data-ttu-id="46c1e-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="46c1e-215">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="46c1e-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="46c1e-216">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="46c1e-217">Out-Default</span><span class="sxs-lookup"><span data-stu-id="46c1e-217">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="46c1e-218">Out-Host</span><span class="sxs-lookup"><span data-stu-id="46c1e-218">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="46c1e-219">Out-Null</span><span class="sxs-lookup"><span data-stu-id="46c1e-219">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="46c1e-220">Out-String</span><span class="sxs-lookup"><span data-stu-id="46c1e-220">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="46c1e-221">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="46c1e-221">Tee-Object</span></span>](Tee-Object.md)
