---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e461c07360b3d9eaf7d9a3c8875d34cd1fc841e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596331"
---
# <span data-ttu-id="6f0d6-102">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="6f0d6-102">ConvertTo-Xml</span></span>

## <span data-ttu-id="6f0d6-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6f0d6-103">SYNOPSIS</span></span>
<span data-ttu-id="6f0d6-104">Crée une représentation XML d'un objet.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-104">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="6f0d6-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6f0d6-105">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="6f0d6-106">Description</span><span class="sxs-lookup"><span data-stu-id="6f0d6-106">DESCRIPTION</span></span>

<span data-ttu-id="6f0d6-107">L' `ConvertTo-Xml` applet de commande crée une représentation [XML](/dotnet/api/system.xml.xmldocument) d’un ou de plusieurs objets .net.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-107">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="6f0d6-108">Pour utiliser cette applet de commande, dirigez un ou plusieurs objets vers l’applet de commande, ou utilisez le paramètre **InputObject** pour spécifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-108">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="6f0d6-109">Lorsque vous dirigez plusieurs objets vers `ConvertTo-Xml` ou utilisez le paramètre **InputObject** pour envoyer plusieurs objets, `ConvertTo-Xml` retourne un document XML en mémoire unique qui comprend les représentations de tous les objets.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-109">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="6f0d6-110">Cette applet de commande est similaire à [Export-Clixml](./Export-Clixml.md) , à ceci près que `Export-Clixml` stocke les données XML résultantes dans un fichier [XML Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) qui peuvent être réimportées en tant qu’objets avec [Import-Clixml](./Import-Clixml.md).</span><span class="sxs-lookup"><span data-stu-id="6f0d6-110">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="6f0d6-111">`ConvertTo-Xml` retourne une représentation en mémoire d’un document XML, ce qui vous permet de continuer à le traiter dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-111">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="6f0d6-112">`ConvertTo-Xml` n’a pas d’option permettant de convertir des objets en langage XML CLI.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-112">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="6f0d6-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6f0d6-113">EXAMPLES</span></span>

### <span data-ttu-id="6f0d6-114">Exemple 1 : convertir une date en XML</span><span class="sxs-lookup"><span data-stu-id="6f0d6-114">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="6f0d6-115">Cette commande convertit la date actuelle (un objet **DateTime** ) en XML.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-115">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="6f0d6-116">Exemple 2 : convertir des processus en XML</span><span class="sxs-lookup"><span data-stu-id="6f0d6-116">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="6f0d6-117">Cette commande convertit les objets processus qui représentent tous les processus sur l'ordinateur en document XML.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-117">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="6f0d6-118">Les objets sont étendus à une profondeur de trois niveaux.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-118">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="6f0d6-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6f0d6-119">PARAMETERS</span></span>

### <span data-ttu-id="6f0d6-120">-As</span><span class="sxs-lookup"><span data-stu-id="6f0d6-120">-As</span></span>

<span data-ttu-id="6f0d6-121">Détermine le format de sortie.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-121">Determines the output format.</span></span>
<span data-ttu-id="6f0d6-122">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="6f0d6-122">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6f0d6-123">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-123">String.</span></span>
<span data-ttu-id="6f0d6-124">retourne une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-124">Returns a single string.</span></span>
- <span data-ttu-id="6f0d6-125">Flux.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-125">Stream.</span></span>
<span data-ttu-id="6f0d6-126">retourne un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-126">Returns an array of strings.</span></span>
- <span data-ttu-id="6f0d6-127">Document.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-127">Document.</span></span>
<span data-ttu-id="6f0d6-128">Retourne un objet **XmlDocument** .</span><span class="sxs-lookup"><span data-stu-id="6f0d6-128">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="6f0d6-129">La valeur par défaut est document.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-129">The default value is Document.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6f0d6-130">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="6f0d6-130">-Depth</span></span>

<span data-ttu-id="6f0d6-131">Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation XML.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-131">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="6f0d6-132">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-132">The default value is 1.</span></span>

<span data-ttu-id="6f0d6-133">Par exemple, si les propriétés de l'objet contiennent également des objets, pour enregistrer une représentation XML des propriétés des objets contenus, vous devez spécifier une profondeur de 2.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-133">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="6f0d6-134">La valeur par défaut peut être remplacée par le type d'objet des fichiers Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-134">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="6f0d6-135">Pour plus d'informations, consultez about_Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-135">For more information, see about_Types.ps1xml.</span></span>

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

### <span data-ttu-id="6f0d6-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6f0d6-136">-InputObject</span></span>

<span data-ttu-id="6f0d6-137">Spécifie l'objet à convertir.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-137">Specifies the object to be converted.</span></span> <span data-ttu-id="6f0d6-138">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-138">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="6f0d6-139">Vous pouvez également diriger les objets vers **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-139">You can also pipe objects to **ConvertTo-XML**.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6f0d6-140">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="6f0d6-140">-NoTypeInformation</span></span>

<span data-ttu-id="6f0d6-141">Omet l'attribut Type des nœuds d'objet.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-141">Omits the Type attribute from the object nodes.</span></span>

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

### <span data-ttu-id="6f0d6-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6f0d6-142">CommonParameters</span></span>

<span data-ttu-id="6f0d6-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6f0d6-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6f0d6-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6f0d6-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6f0d6-145">INPUTS</span></span>

### <span data-ttu-id="6f0d6-146">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6f0d6-146">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6f0d6-147">Vous pouvez diriger n’importe quel objet vers **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="6f0d6-147">You can pipe any object to **ConvertTo-XML**.</span></span>

## <span data-ttu-id="6f0d6-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6f0d6-148">OUTPUTS</span></span>

### <span data-ttu-id="6f0d6-149">Document System. String ou System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="6f0d6-149">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="6f0d6-150">La valeur du paramètre *As* détermine le type d’objet retourné par **ConvertTo-XML** .</span><span class="sxs-lookup"><span data-stu-id="6f0d6-150">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="6f0d6-151">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6f0d6-151">NOTES</span></span>

## <span data-ttu-id="6f0d6-152">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6f0d6-152">RELATED LINKS</span></span>

[<span data-ttu-id="6f0d6-153">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="6f0d6-153">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="6f0d6-154">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="6f0d6-154">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="6f0d6-155">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="6f0d6-155">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="6f0d6-156">Obtient la date</span><span class="sxs-lookup"><span data-stu-id="6f0d6-156">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="6f0d6-157">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="6f0d6-157">Import-Clixml</span></span>](Import-Clixml.md)

