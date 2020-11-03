---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 67dd525da0f1ee7b9f49e585588640030ede8c2b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93202002"
---
# <span data-ttu-id="6f6c3-103">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="6f6c3-103">Import-Clixml</span></span>

## <span data-ttu-id="6f6c3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6f6c3-104">SYNOPSIS</span></span>
<span data-ttu-id="6f6c3-105">Importe un fichier CLIXML et crée des objets correspondants dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-105">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="6f6c3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6f6c3-106">SYNTAX</span></span>

### <span data-ttu-id="6f6c3-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6f6c3-107">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="6f6c3-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="6f6c3-108">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="6f6c3-109">Description</span><span class="sxs-lookup"><span data-stu-id="6f6c3-109">DESCRIPTION</span></span>

<span data-ttu-id="6f6c3-110">L' `Import-Clixml` applet de commande importe un fichier XML Common Language Infrastructure (CLI) avec des données qui représentent Microsoft .net objets Framework et crée les objets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-110">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="6f6c3-111">Pour plus d’informations sur l’interface CLI, consultez [indépendance du langage](/dotnet/standard/language-independence).</span><span class="sxs-lookup"><span data-stu-id="6f6c3-111">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="6f6c3-112">Une utilisation intéressante de `Import-Clixml` sur les ordinateurs Windows consiste à importer des informations d’identification et des chaînes sécurisées exportées en XML sécurisé à l’aide de `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="6f6c3-112">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="6f6c3-113">Pour obtenir un exemple, consultez l’exemple 2.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-113">For an example, see Example 2.</span></span>

<span data-ttu-id="6f6c3-114">`Import-Clixml` utilise la marque d’ordre d’octet (BOM) pour détecter le format d’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-114">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="6f6c3-115">Si le fichier n’a pas de nomenclature, il suppose que l’encodage est UTF8.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-115">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="6f6c3-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6f6c3-116">EXAMPLES</span></span>

### <span data-ttu-id="6f6c3-117">Exemple 1 : importer un fichier sérialisé et recréer un objet</span><span class="sxs-lookup"><span data-stu-id="6f6c3-117">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="6f6c3-118">Cet exemple utilise l' `Export-Clixml` applet de commande pour enregistrer une copie sérialisée des informations de processus retournées par `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="6f6c3-118">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="6f6c3-119">`Import-Clixml` Récupère le contenu du fichier sérialisé et recrée un objet qui est stocké dans la `$Processes` variable.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-119">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="6f6c3-120">Exemple 2 : importer un objet d’informations d’identification sécurisé</span><span class="sxs-lookup"><span data-stu-id="6f6c3-120">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="6f6c3-121">Dans cet exemple, étant donné les informations d’identification que vous avez stockées dans la `$Credential` variable en exécutant l' `Get-Credential` applet de commande, vous pouvez exécuter l' `Export-Clixml` applet de commande pour enregistrer les informations d’identification sur le disque.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-121">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f6c3-122">`Export-Clixml` exporte uniquement les informations d’identification chiffrées sur Windows.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-122">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="6f6c3-123">Sur les systèmes d’exploitation autres que Windows, tels que macOS et Linux, les informations d’identification sont exportées en texte brut.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-123">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="6f6c3-124">L' `Export-Clixml` applet de commande chiffre les objets d’informations d’identification à l’aide de l' [API de protection des données](/previous-versions/windows/apps/hh464970(v=win.10))Windows.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-124">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="6f6c3-125">Le chiffrement garantit que seul votre compte d’utilisateur peut déchiffrer le contenu de l’objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-125">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="6f6c3-126">Le `CLIXML` fichier exporté ne peut pas être utilisé sur un autre ordinateur ou un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-126">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="6f6c3-127">Dans l’exemple, le fichier dans lequel les informations d’identification sont stockées est représenté par `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="6f6c3-127">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="6f6c3-128">Remplacez **TestScript** par le nom du script avec lequel vous chargez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-128">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="6f6c3-129">Vous envoyez l’objet d’informations d’identification dans le pipeline à `Export-Clixml` et l’enregistrez dans le chemin d’accès, `$Credxmlpath` , que vous avez spécifié dans la première commande.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-129">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="6f6c3-130">Pour importer automatiquement les informations d’identification dans votre script, exécutez les deux commandes finales.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-130">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="6f6c3-131">Exécutez `Import-Clixml` pour importer l’objet d’informations d’identification sécurisé dans votre script.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-131">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="6f6c3-132">Cette importation élimine le risque d’exposer les mots de passe en texte brut dans votre script.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-132">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="6f6c3-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6f6c3-133">PARAMETERS</span></span>

### <span data-ttu-id="6f6c3-134">-First</span><span class="sxs-lookup"><span data-stu-id="6f6c3-134">-First</span></span>

<span data-ttu-id="6f6c3-135">Obtient uniquement le nombre d’objets spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-135">Gets only the specified number of objects.</span></span> <span data-ttu-id="6f6c3-136">Entrez le nombre d’objets à obtenir.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-136">Enter the number of objects to get.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6f6c3-137">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="6f6c3-137">-IncludeTotalCount</span></span>

<span data-ttu-id="6f6c3-138">Indique le nombre total d’objets dans le jeu de données, suivis des objets sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-138">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="6f6c3-139">Si l’applet de commande ne peut pas déterminer le nombre total, elle affiche le **nombre total inconnu** .</span><span class="sxs-lookup"><span data-stu-id="6f6c3-139">If the cmdlet can't determine the total count, it displays **Unknown total count** .</span></span> <span data-ttu-id="6f6c3-140">L’entier possède une propriété **Accuracy** qui indique la fiabilité de la valeur du nombre total.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-140">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="6f6c3-141">La valeur des plages de **précision** allant de `0.0` à `1.0` où `0.0` signifie que l’applet de commande n’a pas pu compter les objets, `1.0` signifie que le nombre est exact et une valeur comprise entre `0.0` et `1.0` indique une estimation de plus en plus fiable.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-141">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

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

### <span data-ttu-id="6f6c3-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6f6c3-142">-LiteralPath</span></span>

<span data-ttu-id="6f6c3-143">Spécifie le chemin d’accès aux fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-143">Specifies the path to the XML files.</span></span> <span data-ttu-id="6f6c3-144">Contrairement à **path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-144">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="6f6c3-145">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6f6c3-146">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6f6c3-147">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6f6c3-148">-Path</span><span class="sxs-lookup"><span data-stu-id="6f6c3-148">-Path</span></span>

<span data-ttu-id="6f6c3-149">Spécifie le chemin d’accès aux fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-149">Specifies the path to the XML files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6f6c3-150">-Ignorer</span><span class="sxs-lookup"><span data-stu-id="6f6c3-150">-Skip</span></span>

<span data-ttu-id="6f6c3-151">Ignore le nombre spécifié d’objets, puis obtient les objets restants.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-151">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="6f6c3-152">Entrez le nombre d’objets à ignorer.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-152">Enter the number of objects to skip.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6f6c3-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6f6c3-153">CommonParameters</span></span>

<span data-ttu-id="6f6c3-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6f6c3-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6f6c3-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6f6c3-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6f6c3-156">INPUTS</span></span>

### <span data-ttu-id="6f6c3-157">System.String</span><span class="sxs-lookup"><span data-stu-id="6f6c3-157">System.String</span></span>

<span data-ttu-id="6f6c3-158">Vous pouvez canaliser une chaîne qui contient un chemin d’accès à `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="6f6c3-158">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="6f6c3-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6f6c3-159">OUTPUTS</span></span>

### <span data-ttu-id="6f6c3-160">PSObject</span><span class="sxs-lookup"><span data-stu-id="6f6c3-160">PSObject</span></span>

<span data-ttu-id="6f6c3-161">`Import-Clixml` retourne les objets qui ont été désérialisés à partir des fichiers XML stockés.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-161">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="6f6c3-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6f6c3-162">NOTES</span></span>

<span data-ttu-id="6f6c3-163">Quand vous spécifiez plusieurs valeurs pour un paramètre, séparez-les par des virgules.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-163">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="6f6c3-164">Par exemple : `<parameter-name> <value1>, <value2>`.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-164">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="6f6c3-165">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6f6c3-165">RELATED LINKS</span></span>

[<span data-ttu-id="6f6c3-166">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="6f6c3-166">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="6f6c3-167">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="6f6c3-167">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="6f6c3-168">Join-Path</span><span class="sxs-lookup"><span data-stu-id="6f6c3-168">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="6f6c3-169">Stocker en toute sécurité les informations d’identification sur le disque</span><span class="sxs-lookup"><span data-stu-id="6f6c3-169">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="6f6c3-170">Utiliser PowerShell pour transmettre des informations d’identification à des systèmes hérités</span><span class="sxs-lookup"><span data-stu-id="6f6c3-170">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)
