---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 916b0ca30240002949b947b857b257214ea9ca1a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204661"
---
# <span data-ttu-id="9319a-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="9319a-103">Export-Clixml</span></span>

## <span data-ttu-id="9319a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9319a-104">SYNOPSIS</span></span>
<span data-ttu-id="9319a-105">Crée une représentation XML d'un ou plusieurs objets et la stocke dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="9319a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9319a-106">SYNTAX</span></span>

### <span data-ttu-id="9319a-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9319a-107">ByPath (Default)</span></span>

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9319a-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="9319a-108">ByLiteralPath</span></span>

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9319a-109">Description</span><span class="sxs-lookup"><span data-stu-id="9319a-109">DESCRIPTION</span></span>

<span data-ttu-id="9319a-110">L' `Export-Clixml` applet de commande crée une représentation XML Common Language Infrastructure (CLI) d’un ou de tous les objets et le stocke dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="9319a-111">Vous pouvez ensuite utiliser l' `Import-Clixml` applet de commande pour recréer l’objet enregistré en fonction du contenu de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="9319a-112">Pour plus d’informations sur l’interface CLI, consultez [indépendance du langage](/dotnet/standard/language-independence).</span><span class="sxs-lookup"><span data-stu-id="9319a-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="9319a-113">Cette applet de commande est semblable à `ConvertTo-Xml` , à ceci près que `Export-Clixml` stocke les données XML résultantes dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="9319a-114">`ConvertTo-XML` retourne le code XML, ce qui vous permet de continuer à le traiter dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9319a-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="9319a-115">Une utilisation intéressante de `Export-Clixml` sur les ordinateurs Windows consiste à exporter les informations d’identification et à sécuriser les chaînes en toute sécurité au format XML.</span><span class="sxs-lookup"><span data-stu-id="9319a-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="9319a-116">Pour obtenir un exemple, consultez l’exemple 3.</span><span class="sxs-lookup"><span data-stu-id="9319a-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="9319a-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9319a-117">EXAMPLES</span></span>

### <span data-ttu-id="9319a-118">Exemple 1 : exporter une chaîne dans un fichier XML</span><span class="sxs-lookup"><span data-stu-id="9319a-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="9319a-119">Cet exemple crée un fichier XML qui stocke dans le répertoire actif, une représentation de la chaîne qu' **il s’agit d’un test** .</span><span class="sxs-lookup"><span data-stu-id="9319a-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test** .</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="9319a-120">La chaîne qu' **il s’agit d’un test** est envoyée dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="9319a-120">The string **This is a test** is sent down the pipeline.</span></span> <span data-ttu-id="9319a-121">`Export-Clixml` utilise le paramètre **path** pour créer un fichier XML nommé `sample.xml` dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="9319a-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="9319a-122">Exemple 2 : exporter un objet dans un fichier XML</span><span class="sxs-lookup"><span data-stu-id="9319a-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="9319a-123">Cet exemple montre comment exporter un objet vers un fichier XML, puis créer un objet en important le contenu XML du fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="9319a-124">L' `Get-Acl` applet de commande obtient le descripteur de sécurité du `Test.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="9319a-125">Il envoie l’objet dans le pipeline pour lui transmettre le descripteur de sécurité `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="9319a-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="9319a-126">La représentation XML de l’objet est stockée dans un fichier nommé `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="9319a-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="9319a-127">L' `Import-Clixml` applet de commande crée un objet à partir du code XML dans le `FileACL.xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="9319a-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="9319a-128">Ensuite, il enregistre l’objet dans la `$fileacl` variable.</span><span class="sxs-lookup"><span data-stu-id="9319a-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="9319a-129">Exemple 3 : chiffrer un objet d’informations d’identification exporté sur Windows</span><span class="sxs-lookup"><span data-stu-id="9319a-129">Example 3: Encrypt an exported credential object on Windows</span></span>

<span data-ttu-id="9319a-130">Dans cet exemple, étant donné les informations d’identification que vous avez stockées dans la `$Credential` variable en exécutant l' `Get-Credential` applet de commande, vous pouvez exécuter l' `Export-Clixml` applet de commande pour enregistrer les informations d’identification sur le disque.</span><span class="sxs-lookup"><span data-stu-id="9319a-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9319a-131">`Export-Clixml` exporte uniquement les informations d’identification chiffrées sur Windows.</span><span class="sxs-lookup"><span data-stu-id="9319a-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="9319a-132">Sur les systèmes d’exploitation autres que Windows, tels que macOS et Linux, les informations d’identification sont exportées sous forme de texte brut stocké en tant que tableau de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="9319a-132">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="9319a-133">Cela fournit un certain brouillage, mais ne fournit pas de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="9319a-133">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="9319a-134">L' `Export-Clixml` applet de commande chiffre les objets d’informations d’identification à l’aide de l' [API de protection des données](/previous-versions/windows/apps/hh464970(v=win.10))Windows.</span><span class="sxs-lookup"><span data-stu-id="9319a-134">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span> <span data-ttu-id="9319a-135">Le chiffrement garantit que seul votre compte d’utilisateur sur cet ordinateur peut déchiffrer le contenu de l’objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="9319a-135">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span>
<span data-ttu-id="9319a-136">Le `CLIXML` fichier exporté ne peut pas être utilisé sur un autre ordinateur ou un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9319a-136">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="9319a-137">Dans l’exemple, le fichier dans lequel les informations d’identification sont stockées est représenté par `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="9319a-137">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="9319a-138">Remplacez **TestScript** par le nom du script avec lequel vous chargez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="9319a-138">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="9319a-139">Vous envoyez l’objet d’informations d’identification dans le pipeline à `Export-Clixml` et l’enregistrez dans le chemin d’accès, `$Credxmlpath` , que vous avez spécifié dans la première commande.</span><span class="sxs-lookup"><span data-stu-id="9319a-139">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="9319a-140">Pour importer automatiquement les informations d’identification dans votre script, exécutez les deux commandes finales.</span><span class="sxs-lookup"><span data-stu-id="9319a-140">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="9319a-141">Exécutez `Import-Clixml` pour importer l’objet d’informations d’identification sécurisé dans votre script.</span><span class="sxs-lookup"><span data-stu-id="9319a-141">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="9319a-142">Cette importation élimine le risque d’exposer les mots de passe en texte brut dans votre script.</span><span class="sxs-lookup"><span data-stu-id="9319a-142">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

### <span data-ttu-id="9319a-143">Exemple 4 : exportation d’un objet d’informations d’identification sur Linux ou macOS</span><span class="sxs-lookup"><span data-stu-id="9319a-143">Example 4: Exporting a credential object on Linux or macOS</span></span>

<span data-ttu-id="9319a-144">Dans cet exemple, nous créons un **PSCredential** dans la `$Credential` variable à l’aide de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="9319a-144">In this example, we create a **PSCredential** in the `$Credential` variable using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9319a-145">Ensuite, nous utilisons `Export-Clixml` pour enregistrer les informations d’identification sur le disque.</span><span class="sxs-lookup"><span data-stu-id="9319a-145">Then we use `Export-Clixml` to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9319a-146">`Export-Clixml` exporte uniquement les informations d’identification chiffrées sur Windows.</span><span class="sxs-lookup"><span data-stu-id="9319a-146">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="9319a-147">Sur les systèmes d’exploitation autres que Windows, tels que macOS et Linux, les informations d’identification sont exportées sous forme de texte brut stocké en tant que tableau de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="9319a-147">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="9319a-148">Cela fournit un certain brouillage, mais ne fournit pas de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="9319a-148">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

<span data-ttu-id="9319a-149">La sortie de `Get-Content` dans cet exemple a été tronquée pour se concentrer sur les informations d’identification dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="9319a-149">The output of `Get-Content` in this example has been truncate to focus on the credential information in the XML file.</span></span> <span data-ttu-id="9319a-150">Notez que la valeur de texte brut du mot de passe est stockée dans le fichier XML sous la forme d’un tableau de caractères Unicode, comme démontré par `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="9319a-150">Note that the plain text value of the password is stored in the XML file as a Unicode character array as proven by `Format-Hex`.</span></span> <span data-ttu-id="9319a-151">La valeur est donc encodée, mais pas chiffrée.</span><span class="sxs-lookup"><span data-stu-id="9319a-151">So the value is encoded but not encrypted.</span></span>

## <span data-ttu-id="9319a-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9319a-152">PARAMETERS</span></span>

### <span data-ttu-id="9319a-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9319a-153">-Confirm</span></span>

<span data-ttu-id="9319a-154">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9319a-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9319a-155">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="9319a-155">-Depth</span></span>

<span data-ttu-id="9319a-156">Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation XML.</span><span class="sxs-lookup"><span data-stu-id="9319a-156">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="9319a-157">La valeur par défaut est `2`.</span><span class="sxs-lookup"><span data-stu-id="9319a-157">The default value is `2`.</span></span>

<span data-ttu-id="9319a-158">La valeur par défaut peut être remplacée par le type d’objet dans les `Types.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="9319a-158">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="9319a-159">Pour plus d’informations, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="9319a-159">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9319a-160">-Encoding</span><span class="sxs-lookup"><span data-stu-id="9319a-160">-Encoding</span></span>

<span data-ttu-id="9319a-161">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="9319a-161">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="9319a-162">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="9319a-162">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="9319a-163">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9319a-163">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9319a-164">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="9319a-164">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="9319a-165">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="9319a-165">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9319a-166">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="9319a-166">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="9319a-167">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="9319a-167">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="9319a-168">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="9319a-168">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="9319a-169">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9319a-169">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="9319a-170">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="9319a-170">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9319a-171">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="9319a-171">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9319a-172">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="9319a-172">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="9319a-173">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="9319a-173">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="9319a-174">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="9319a-174">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9319a-175">-Force</span><span class="sxs-lookup"><span data-stu-id="9319a-175">-Force</span></span>

<span data-ttu-id="9319a-176">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9319a-176">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="9319a-177">Indique à l'applet de commande d'effacer l'attribut de lecture seule du fichier de sortie, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9319a-177">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="9319a-178">L'applet de commande tente de réinitialiser l'attribut de lecture seule à la fin de l'exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="9319a-178">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9319a-179">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9319a-179">-InputObject</span></span>

<span data-ttu-id="9319a-180">Spécifie l'objet à convertir.</span><span class="sxs-lookup"><span data-stu-id="9319a-180">Specifies the object to be converted.</span></span> <span data-ttu-id="9319a-181">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="9319a-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="9319a-182">Vous pouvez également diriger les objets vers `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="9319a-182">You can also pipe objects to `Export-Clixml`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9319a-183">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9319a-183">-LiteralPath</span></span>

<span data-ttu-id="9319a-184">Spécifie le chemin d'accès du fichier où sera stockée la représentation XML de l'objet.</span><span class="sxs-lookup"><span data-stu-id="9319a-184">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="9319a-185">Contrairement à **path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="9319a-185">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="9319a-186">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="9319a-186">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9319a-187">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="9319a-187">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9319a-188">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="9319a-188">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9319a-189">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="9319a-189">-NoClobber</span></span>

<span data-ttu-id="9319a-190">Indique que l’applet de commande ne remplace pas le contenu d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="9319a-190">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="9319a-191">Par défaut, si un fichier existe dans le chemin d’accès spécifié, `Export-Clixml` remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="9319a-191">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9319a-192">-Path</span><span class="sxs-lookup"><span data-stu-id="9319a-192">-Path</span></span>

<span data-ttu-id="9319a-193">Spécifie le chemin d'accès du fichier où sera stockée la représentation XML de l'objet.</span><span class="sxs-lookup"><span data-stu-id="9319a-193">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

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

### <span data-ttu-id="9319a-194">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9319a-194">-WhatIf</span></span>

<span data-ttu-id="9319a-195">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9319a-195">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9319a-196">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9319a-196">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9319a-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9319a-197">CommonParameters</span></span>

<span data-ttu-id="9319a-198">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9319a-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9319a-199">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9319a-199">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9319a-200">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9319a-200">INPUTS</span></span>

### <span data-ttu-id="9319a-201">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9319a-201">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9319a-202">Vous pouvez effectuer un pipeline de n’importe quel objet vers `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="9319a-202">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="9319a-203">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9319a-203">OUTPUTS</span></span>

### <span data-ttu-id="9319a-204">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="9319a-204">System.IO.FileInfo</span></span>

<span data-ttu-id="9319a-205">`Export-Clixml` crée un fichier qui contient le XML.</span><span class="sxs-lookup"><span data-stu-id="9319a-205">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="9319a-206">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9319a-206">NOTES</span></span>

## <span data-ttu-id="9319a-207">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9319a-207">RELATED LINKS</span></span>

[<span data-ttu-id="9319a-208">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="9319a-208">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="9319a-209">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="9319a-209">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="9319a-210">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="9319a-210">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="9319a-211">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="9319a-211">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="9319a-212">Join-Path</span><span class="sxs-lookup"><span data-stu-id="9319a-212">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="9319a-213">Stocker en toute sécurité les informations d’identification sur le disque</span><span class="sxs-lookup"><span data-stu-id="9319a-213">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="9319a-214">Utiliser PowerShell pour transmettre des informations d’identification à des systèmes hérités</span><span class="sxs-lookup"><span data-stu-id="9319a-214">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="9319a-215">Windows.Security.Cryptography.DataProtection</span><span class="sxs-lookup"><span data-stu-id="9319a-215">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
