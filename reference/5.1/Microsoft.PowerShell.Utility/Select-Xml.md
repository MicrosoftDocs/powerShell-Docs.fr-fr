---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7e3d02dedb9f7809a8f8e1c657987fef8ec38fa9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387989"
---
# <span data-ttu-id="45909-103">Select-Xml</span><span class="sxs-lookup"><span data-stu-id="45909-103">Select-Xml</span></span>

## <span data-ttu-id="45909-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="45909-104">SYNOPSIS</span></span>
<span data-ttu-id="45909-105">Recherche du texte dans un document ou une chaîne XML.</span><span class="sxs-lookup"><span data-stu-id="45909-105">Finds text in an XML string or document.</span></span>

## <span data-ttu-id="45909-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="45909-106">SYNTAX</span></span>

### <span data-ttu-id="45909-107">XML (par défaut)</span><span class="sxs-lookup"><span data-stu-id="45909-107">Xml (Default)</span></span>

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="45909-108">Path</span><span class="sxs-lookup"><span data-stu-id="45909-108">Path</span></span>

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="45909-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="45909-109">LiteralPath</span></span>

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="45909-110">Contenu</span><span class="sxs-lookup"><span data-stu-id="45909-110">Content</span></span>

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="45909-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="45909-111">DESCRIPTION</span></span>

<span data-ttu-id="45909-112">L’applet de commande **Select-XML** vous permet d’utiliser des requêtes XPath pour rechercher du texte dans des chaînes et des documents XML.</span><span class="sxs-lookup"><span data-stu-id="45909-112">The **Select-Xml** cmdlet lets you use XPath queries to search for text in XML strings and documents.</span></span>
<span data-ttu-id="45909-113">Entrez une requête XPath et utilisez le paramètre *content* , *path* ou *XML* pour spécifier le code XML dans lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="45909-113">Enter an XPath query, and use the *Content* , *Path* , or *Xml* parameter to specify the XML to be searched.</span></span>

## <span data-ttu-id="45909-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="45909-114">EXAMPLES</span></span>

### <span data-ttu-id="45909-115">Exemple 1 : sélectionner des nœuds AliasProperty</span><span class="sxs-lookup"><span data-stu-id="45909-115">Example 1: Select AliasProperty nodes</span></span>

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

<span data-ttu-id="45909-116">Cet exemple obtient les propriétés d'alias dans Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="45909-116">This example gets the alias properties in the Types.ps1xml.</span></span>
<span data-ttu-id="45909-117">(Pour plus d'informations sur ce fichier, consultez about_Types.ps1xml.)</span><span class="sxs-lookup"><span data-stu-id="45909-117">(For information about this file, see about_Types.ps1xml.)</span></span>

<span data-ttu-id="45909-118">La première commande enregistre le chemin d'accès au fichier Types.ps1xml dans la variable $Path.</span><span class="sxs-lookup"><span data-stu-id="45909-118">The first command saves the path to the Types.ps1xml file in the $Path variable.</span></span>

<span data-ttu-id="45909-119">La deuxième commande enregistre le chemin d'accès XML au nœud AliasProperty dans la variable $XPath.</span><span class="sxs-lookup"><span data-stu-id="45909-119">The second command saves the XML path to the AliasProperty node in the $XPath variable.</span></span>

<span data-ttu-id="45909-120">La troisième commande utilise l'applet de commande **Select-Xml** pour obtenir les nœuds AliasProperty qui sont identifiés par l'instruction XPath à partir du fichier Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="45909-120">The third command uses the **Select-Xml** cmdlet to get the AliasProperty nodes that are identified by the XPath statement from the Types.ps1xml file.</span></span>
<span data-ttu-id="45909-121">La commande utilise un opérateur de pipeline pour envoyer les nœuds AliasProperty à l’applet de commande Select-Object.</span><span class="sxs-lookup"><span data-stu-id="45909-121">The command uses a pipeline operator to send the AliasProperty nodes to the Select-Object cmdlet.</span></span>
<span data-ttu-id="45909-122">Le paramètre *ExpandProperty* développe l’objet **node** et retourne ses propriétés Name et ReferencedMemberName.</span><span class="sxs-lookup"><span data-stu-id="45909-122">The *ExpandProperty* parameter expands the **Node** object and returns its Name and ReferencedMemberName properties.</span></span>

<span data-ttu-id="45909-123">Le résultat affiche les propriétés Name et ReferencedMemberName de chaque propriété d'alias dans le fichier Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="45909-123">The result shows the Name and ReferencedMemberName of each alias property in the Types.ps1xml file.</span></span>
<span data-ttu-id="45909-124">Par exemple, il existe une propriété **Count** qui est un alias de la propriété **Length** .</span><span class="sxs-lookup"><span data-stu-id="45909-124">For example, there is a **Count** property that is an alias of the **Length** property.</span></span>

### <span data-ttu-id="45909-125">Exemple 2 : entrée d’un document XML</span><span class="sxs-lookup"><span data-stu-id="45909-125">Example 2: Input an XML document</span></span>

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

<span data-ttu-id="45909-126">Cet exemple montre comment utiliser le paramètre *XML* pour fournir un document XML à l’applet de commande **Select-XML** .</span><span class="sxs-lookup"><span data-stu-id="45909-126">This example shows how to use the *XML* parameter to provide an XML document to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="45909-127">La première commande utilise l’applet de commande Get-Content pour récupérer le contenu du fichier XML Types.ps1et l’enregistrer dans la variable $Types.</span><span class="sxs-lookup"><span data-stu-id="45909-127">The first command uses the Get-Content cmdlet to get the content of the Types.ps1xml file and save it in the $Types variable.</span></span>
<span data-ttu-id="45909-128">Le \[ XML \] effectue un cast de la variable en objet XML.</span><span class="sxs-lookup"><span data-stu-id="45909-128">The \[xml\] casts the variable as an XML object.</span></span>

<span data-ttu-id="45909-129">La deuxième commande utilise l'applet de commande **Select-Xml** pour obtenir les nœuds MethodName dans le fichier Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="45909-129">The second command uses the **Select-Xml** cmdlet to get the MethodName nodes in the Types.ps1xml file.</span></span>
<span data-ttu-id="45909-130">La commande utilise le paramètre *Xml* pour spécifier le contenu XML dans la variable $Types et le paramètre *XPath* pour spécifier le chemin d'accès au nœud MethodName.</span><span class="sxs-lookup"><span data-stu-id="45909-130">The command uses the *Xml* parameter to specify the XML content in the $Types variable and the *XPath* parameter to specify the path to the MethodName node.</span></span>

### <span data-ttu-id="45909-131">Exemple 3 : Rechercher dans les fichiers d’aide PowerShell</span><span class="sxs-lookup"><span data-stu-id="45909-131">Example 3: Search PowerShell Help files</span></span>

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

<span data-ttu-id="45909-132">Cet exemple montre comment utiliser l’applet de commande **Select-XML** pour rechercher des fichiers d’aide sur les applets de commande XML PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45909-132">This example shows how to use the **Select-Xml** cmdlet to search the PowerShell XML-based cmdlet help files.</span></span>
<span data-ttu-id="45909-133">Dans cet exemple, nous allons rechercher le nom de l'applet de commande qui sert de titre pour chaque fichier d'aide et le chemin d'accès au fichier d'aide.</span><span class="sxs-lookup"><span data-stu-id="45909-133">In this example, we'll search for the cmdlet name that serves as a title for each help file and the path to the help file.</span></span>

<span data-ttu-id="45909-134">La première commande crée une table de hachage qui représente l'espace de noms XML qui est utilisé pour les fichiers d'aide et l'enregistre dans la variable $Namespace.</span><span class="sxs-lookup"><span data-stu-id="45909-134">The first command creates a hash table that represents the XML namespace that is used for the help files and saves it in the $Namespace variable.</span></span>

### <span data-ttu-id="45909-135">Exemple 4 : différentes façons d’entrer des données XML</span><span class="sxs-lookup"><span data-stu-id="45909-135">Example 4: Different ways to input XML</span></span>

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

<span data-ttu-id="45909-136">Cet exemple montre deux façons différentes d’envoyer du code XML à l’applet de commande **Select-XML** .</span><span class="sxs-lookup"><span data-stu-id="45909-136">This example shows two different ways to send XML to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="45909-137">La première commande enregistre une chaîne ici-String qui contient du code XML dans la variable $Xml.</span><span class="sxs-lookup"><span data-stu-id="45909-137">The first command saves a here-string that contains XML in the $Xml variable.</span></span>
<span data-ttu-id="45909-138">(Pour plus d'informations sur les chaînes here-string, consultez about_Quoting_Rules.)</span><span class="sxs-lookup"><span data-stu-id="45909-138">(For more information about here-strings, see about_Quoting_Rules.)</span></span>

### <span data-ttu-id="45909-139">Exemple 5 : utiliser l’espace de noms xmlns par défaut</span><span class="sxs-lookup"><span data-stu-id="45909-139">Example 5: Use the default xmlns namespace</span></span>

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

<span data-ttu-id="45909-140">Cet exemple montre comment utiliser l’applet de commande **Select-XML** avec des documents XML qui utilisent l’espace de noms xmlns par défaut.</span><span class="sxs-lookup"><span data-stu-id="45909-140">This example shows how to use the **Select-Xml** cmdlet with XML documents that use the default xmlns namespace.</span></span>
<span data-ttu-id="45909-141">L'exemple obtient les titres des fichiers d'extraits de code créés par l'utilisateur Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="45909-141">The example gets the titles of Windows PowerShell ISE user-created snippet files.</span></span>
<span data-ttu-id="45909-142">Pour plus d'informations sur les extraits de code, consultez New-IseSnippet.</span><span class="sxs-lookup"><span data-stu-id="45909-142">For information about snippets, see New-IseSnippet.</span></span>

<span data-ttu-id="45909-143">La première commande crée une table de hachage pour l’espace de noms par défaut qui est utilisé par les fichiers XML et les affecte à la variable $SnippetNamespace.</span><span class="sxs-lookup"><span data-stu-id="45909-143">The first command creates a hash table for the default namespace that snippet XML files use and assigns it to the $SnippetNamespace variable.</span></span>
<span data-ttu-id="45909-144">La valeur de table de hachage est l'URI du schéma XMLNS dans le fichier XML d'extraits de code.</span><span class="sxs-lookup"><span data-stu-id="45909-144">The hash table value is the XMLNS schema URI in the snippet XML.</span></span>
<span data-ttu-id="45909-145">Le nom de clé de la table de hachage, capture, est arbitraire.</span><span class="sxs-lookup"><span data-stu-id="45909-145">The hash table key name, snip, is arbitrary.</span></span>
<span data-ttu-id="45909-146">Vous pouvez utiliser n’importe quel nom qui n’est pas réservé, mais vous ne pouvez pas utiliser xmlns.</span><span class="sxs-lookup"><span data-stu-id="45909-146">You can use any name that is not reserved, but you cannot use xmlns.</span></span>

## <span data-ttu-id="45909-147">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="45909-147">PARAMETERS</span></span>

### <span data-ttu-id="45909-148">-Contenu</span><span class="sxs-lookup"><span data-stu-id="45909-148">-Content</span></span>

<span data-ttu-id="45909-149">Spécifie une chaîne qui contient le code XML dans lequel effectuer des recherches.</span><span class="sxs-lookup"><span data-stu-id="45909-149">Specifies a string that contains the XML to search.</span></span>
<span data-ttu-id="45909-150">Vous pouvez également diriger des chaînes vers **Select-XML**.</span><span class="sxs-lookup"><span data-stu-id="45909-150">You can also pipe strings to **Select-Xml**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45909-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="45909-151">-LiteralPath</span></span>

<span data-ttu-id="45909-152">Spécifie les chemins d'accès et les noms des fichiers XML dans lequel effectuer des recherches.</span><span class="sxs-lookup"><span data-stu-id="45909-152">Specifies the paths and file names of the XML files to search.</span></span>
<span data-ttu-id="45909-153">Contrairement au paramètre *Path* , la valeur du paramètre *LiteralPath* est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="45909-153">Unlike *Path* , the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="45909-154">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="45909-154">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="45909-155">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="45909-155">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="45909-156">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="45909-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="45909-157">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="45909-157">-Namespace</span></span>

<span data-ttu-id="45909-158">Spécifie une table de hachage des espaces de noms utilisés dans le code XML.</span><span class="sxs-lookup"><span data-stu-id="45909-158">Specifies a hash table of the namespaces used in the XML.</span></span>
<span data-ttu-id="45909-159">Utilisez le format @ { \<namespaceName\>  =  \<namespaceValue\> }.</span><span class="sxs-lookup"><span data-stu-id="45909-159">Use the format @{\<namespaceName\> = \<namespaceValue\>}.</span></span>

<span data-ttu-id="45909-160">Lorsque le code XML utilise l’espace de noms par défaut, qui commence par xmlns, utilisez une clé arbitraire pour le nom de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="45909-160">When the XML uses the default namespace, which begins with xmlns, use an arbitrary key for the namespace name.</span></span>
<span data-ttu-id="45909-161">Vous ne pouvez pas utiliser xmlns.</span><span class="sxs-lookup"><span data-stu-id="45909-161">You cannot use xmlns.</span></span>
<span data-ttu-id="45909-162">Dans l’instruction XPath, faites précéder chaque nom de nœud d’un nom d’espace de noms et d’un signe deux-points, par exemple//namespaceName : node.</span><span class="sxs-lookup"><span data-stu-id="45909-162">In the XPath statement, prefix each node name with the namespace name and a colon, such as //namespaceName:Node.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45909-163">-Path</span><span class="sxs-lookup"><span data-stu-id="45909-163">-Path</span></span>

<span data-ttu-id="45909-164">Spécifie le chemin d'accès et les noms des fichiers XML dans lequel effectuer des recherches.</span><span class="sxs-lookup"><span data-stu-id="45909-164">Specifies the path and file names of the XML files to search.</span></span>
<span data-ttu-id="45909-165">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="45909-165">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="45909-166">-XML</span><span class="sxs-lookup"><span data-stu-id="45909-166">-Xml</span></span>

<span data-ttu-id="45909-167">Spécifie un ou plusieurs nœuds XML.</span><span class="sxs-lookup"><span data-stu-id="45909-167">Specifies one or more XML nodes.</span></span>

<span data-ttu-id="45909-168">Un document XML est traité comme une collection de nœuds XML.</span><span class="sxs-lookup"><span data-stu-id="45909-168">An XML document will be processed as a collection of XML nodes.</span></span>
<span data-ttu-id="45909-169">Si vous dirigez un document XML vers **Select-XML** , chaque nœud de document est recherché séparément, car il passe par le pipeline.</span><span class="sxs-lookup"><span data-stu-id="45909-169">If you pipe an XML document to **Select-Xml** , each document node will be searched separately as it comes through the pipeline.</span></span>

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45909-170">-XPath</span><span class="sxs-lookup"><span data-stu-id="45909-170">-XPath</span></span>

<span data-ttu-id="45909-171">Spécifie une requête de recherche XPath.</span><span class="sxs-lookup"><span data-stu-id="45909-171">Specifies an XPath search query.</span></span>
<span data-ttu-id="45909-172">Le langage de requête respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="45909-172">The query language is case-sensitive.</span></span>
<span data-ttu-id="45909-173">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="45909-173">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45909-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45909-174">CommonParameters</span></span>

<span data-ttu-id="45909-175">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45909-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45909-176">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="45909-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45909-177">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="45909-177">INPUTS</span></span>

### <span data-ttu-id="45909-178">Nœud System. String ou System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="45909-178">System.String or System.Xml.XmlNode</span></span>

<span data-ttu-id="45909-179">Vous pouvez diriger un chemin d’accès ou un nœud XML vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="45909-179">You can pipe a path or XML node to this cmdlet.</span></span>

## <span data-ttu-id="45909-180">SORTIES</span><span class="sxs-lookup"><span data-stu-id="45909-180">OUTPUTS</span></span>

### <span data-ttu-id="45909-181">Microsoft. PowerShell. Commands. SelectXmlInfo</span><span class="sxs-lookup"><span data-stu-id="45909-181">Microsoft.PowerShell.Commands.SelectXmlInfo</span></span>

## <span data-ttu-id="45909-182">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="45909-182">NOTES</span></span>

<span data-ttu-id="45909-183">XPath est un langage standard qui est conçu pour identifier les parties d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="45909-183">XPath is a standard language that is designed to identify parts of an XML document.</span></span> <span data-ttu-id="45909-184">Pour plus d’informations sur le langage XPath, consultez [Référence XPath](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) et la section filtres de sélection de la [sélection d’événements](/previous-versions//aa385231(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="45909-184">For more information about the XPath language, see [XPath Reference](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) and the Selection Filters section of [Event Selection](/previous-versions//aa385231(v=vs.85)).</span></span>

## <span data-ttu-id="45909-185">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="45909-185">RELATED LINKS</span></span>

[<span data-ttu-id="45909-186">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="45909-186">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
