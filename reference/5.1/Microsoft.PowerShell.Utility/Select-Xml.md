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
# Select-Xml

## SYNOPSIS
Recherche du texte dans un document ou une chaîne XML.

## SYNTAXE

### XML (par défaut)

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Path

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### LiteralPath

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Contenu

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## DESCRIPTION

L’applet de commande **Select-XML** vous permet d’utiliser des requêtes XPath pour rechercher du texte dans des chaînes et des documents XML.
Entrez une requête XPath et utilisez le paramètre *content* , *path* ou *XML* pour spécifier le code XML dans lequel effectuer la recherche.

## EXEMPLES

### Exemple 1 : sélectionner des nœuds AliasProperty

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

Cet exemple obtient les propriétés d'alias dans Types.ps1xml.
(Pour plus d'informations sur ce fichier, consultez about_Types.ps1xml.)

La première commande enregistre le chemin d'accès au fichier Types.ps1xml dans la variable $Path.

La deuxième commande enregistre le chemin d'accès XML au nœud AliasProperty dans la variable $XPath.

La troisième commande utilise l'applet de commande **Select-Xml** pour obtenir les nœuds AliasProperty qui sont identifiés par l'instruction XPath à partir du fichier Types.ps1xml.
La commande utilise un opérateur de pipeline pour envoyer les nœuds AliasProperty à l’applet de commande Select-Object.
Le paramètre *ExpandProperty* développe l’objet **node** et retourne ses propriétés Name et ReferencedMemberName.

Le résultat affiche les propriétés Name et ReferencedMemberName de chaque propriété d'alias dans le fichier Types.ps1xml.
Par exemple, il existe une propriété **Count** qui est un alias de la propriété **Length** .

### Exemple 2 : entrée d’un document XML

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

Cet exemple montre comment utiliser le paramètre *XML* pour fournir un document XML à l’applet de commande **Select-XML** .

La première commande utilise l’applet de commande Get-Content pour récupérer le contenu du fichier XML Types.ps1et l’enregistrer dans la variable $Types.
Le \[ XML \] effectue un cast de la variable en objet XML.

La deuxième commande utilise l'applet de commande **Select-Xml** pour obtenir les nœuds MethodName dans le fichier Types.ps1xml.
La commande utilise le paramètre *Xml* pour spécifier le contenu XML dans la variable $Types et le paramètre *XPath* pour spécifier le chemin d'accès au nœud MethodName.

### Exemple 3 : Rechercher dans les fichiers d’aide PowerShell

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

Cet exemple montre comment utiliser l’applet de commande **Select-XML** pour rechercher des fichiers d’aide sur les applets de commande XML PowerShell.
Dans cet exemple, nous allons rechercher le nom de l'applet de commande qui sert de titre pour chaque fichier d'aide et le chemin d'accès au fichier d'aide.

La première commande crée une table de hachage qui représente l'espace de noms XML qui est utilisé pour les fichiers d'aide et l'enregistre dans la variable $Namespace.

### Exemple 4 : différentes façons d’entrer des données XML

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

Cet exemple montre deux façons différentes d’envoyer du code XML à l’applet de commande **Select-XML** .

La première commande enregistre une chaîne ici-String qui contient du code XML dans la variable $Xml.
(Pour plus d'informations sur les chaînes here-string, consultez about_Quoting_Rules.)

### Exemple 5 : utiliser l’espace de noms xmlns par défaut

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

Cet exemple montre comment utiliser l’applet de commande **Select-XML** avec des documents XML qui utilisent l’espace de noms xmlns par défaut.
L'exemple obtient les titres des fichiers d'extraits de code créés par l'utilisateur Windows PowerShell ISE.
Pour plus d'informations sur les extraits de code, consultez New-IseSnippet.

La première commande crée une table de hachage pour l’espace de noms par défaut qui est utilisé par les fichiers XML et les affecte à la variable $SnippetNamespace.
La valeur de table de hachage est l'URI du schéma XMLNS dans le fichier XML d'extraits de code.
Le nom de clé de la table de hachage, capture, est arbitraire.
Vous pouvez utiliser n’importe quel nom qui n’est pas réservé, mais vous ne pouvez pas utiliser xmlns.

## PARAMÈTRES

### -Contenu

Spécifie une chaîne qui contient le code XML dans lequel effectuer des recherches.
Vous pouvez également diriger des chaînes vers **Select-XML**.

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

### -LiteralPath

Spécifie les chemins d'accès et les noms des fichiers XML dans lequel effectuer des recherches.
Contrairement au paramètre *Path* , la valeur du paramètre *LiteralPath* est utilisée exactement telle qu'elle est tapée.
Aucun caractère n’est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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

### -Espace de noms

Spécifie une table de hachage des espaces de noms utilisés dans le code XML.
Utilisez le format @ { \<namespaceName\>  =  \<namespaceValue\> }.

Lorsque le code XML utilise l’espace de noms par défaut, qui commence par xmlns, utilisez une clé arbitraire pour le nom de l’espace de noms.
Vous ne pouvez pas utiliser xmlns.
Dans l’instruction XPath, faites précéder chaque nom de nœud d’un nom d’espace de noms et d’un signe deux-points, par exemple//namespaceName : node.

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

### -Path

Spécifie le chemin d'accès et les noms des fichiers XML dans lequel effectuer des recherches.
Les caractères génériques sont autorisés.

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

### -XML

Spécifie un ou plusieurs nœuds XML.

Un document XML est traité comme une collection de nœuds XML.
Si vous dirigez un document XML vers **Select-XML** , chaque nœud de document est recherché séparément, car il passe par le pipeline.

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

### -XPath

Spécifie une requête de recherche XPath.
Le langage de requête respecte la casse.
Ce paramètre est obligatoire.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Nœud System. String ou System.Xml.Xml

Vous pouvez diriger un chemin d’accès ou un nœud XML vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. SelectXmlInfo

## REMARQUES

XPath est un langage standard qui est conçu pour identifier les parties d'un document XML. Pour plus d’informations sur le langage XPath, consultez [Référence XPath](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) et la section filtres de sélection de la [sélection d’événements](/previous-versions//aa385231(v=vs.85)).

## LIENS CONNEXES

[ConvertTo-Xml](ConvertTo-Xml.md)
