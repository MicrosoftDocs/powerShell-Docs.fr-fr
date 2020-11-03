---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: 2e7ebe3a528095873dc7ba5ba0deba2905f531ee
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204214"
---
# <span data-ttu-id="9f8b2-103">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="9f8b2-103">ConvertTo-Xml</span></span>

## <span data-ttu-id="9f8b2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9f8b2-104">SYNOPSIS</span></span>
<span data-ttu-id="9f8b2-105">Crée une représentation XML d'un objet.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-105">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="9f8b2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9f8b2-106">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="9f8b2-107">Description</span><span class="sxs-lookup"><span data-stu-id="9f8b2-107">DESCRIPTION</span></span>

<span data-ttu-id="9f8b2-108">L' `ConvertTo-Xml` applet de commande crée une représentation [XML](/dotnet/api/system.xml.xmldocument) d’un ou de plusieurs objets .net.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-108">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="9f8b2-109">Pour utiliser cette applet de commande, dirigez un ou plusieurs objets vers l’applet de commande, ou utilisez le paramètre **InputObject** pour spécifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-109">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="9f8b2-110">Lorsque vous dirigez plusieurs objets vers `ConvertTo-Xml` ou utilisez le paramètre **InputObject** pour envoyer plusieurs objets, `ConvertTo-Xml` retourne un document XML en mémoire unique qui comprend les représentations de tous les objets.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-110">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="9f8b2-111">Cette applet de commande est similaire à [Export-Clixml](./Export-Clixml.md) , à ceci près que `Export-Clixml` stocke les données XML résultantes dans un fichier [XML Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) qui peuvent être réimportées en tant qu’objets avec [Import-Clixml](./Import-Clixml.md).</span><span class="sxs-lookup"><span data-stu-id="9f8b2-111">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="9f8b2-112">`ConvertTo-Xml` retourne une représentation en mémoire d’un document XML, ce qui vous permet de continuer à le traiter dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-112">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="9f8b2-113">`ConvertTo-Xml` n’a pas d’option permettant de convertir des objets en langage XML CLI.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-113">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="9f8b2-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9f8b2-114">EXAMPLES</span></span>

### <span data-ttu-id="9f8b2-115">Exemple 1 : convertir une date en XML</span><span class="sxs-lookup"><span data-stu-id="9f8b2-115">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="9f8b2-116">Cette commande convertit la date actuelle (un objet **DateTime** ) en XML.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-116">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="9f8b2-117">Exemple 2 : convertir des processus en XML</span><span class="sxs-lookup"><span data-stu-id="9f8b2-117">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="9f8b2-118">Cette commande convertit les objets processus qui représentent tous les processus sur l'ordinateur en document XML.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-118">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="9f8b2-119">Les objets sont étendus à une profondeur de trois niveaux.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-119">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="9f8b2-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f8b2-120">PARAMETERS</span></span>

### <span data-ttu-id="9f8b2-121">-As</span><span class="sxs-lookup"><span data-stu-id="9f8b2-121">-As</span></span>

<span data-ttu-id="9f8b2-122">Détermine le format de sortie.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-122">Determines the output format.</span></span>
<span data-ttu-id="9f8b2-123">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="9f8b2-123">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9f8b2-124">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-124">String.</span></span>
<span data-ttu-id="9f8b2-125">retourne une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-125">Returns a single string.</span></span>
- <span data-ttu-id="9f8b2-126">Flux.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-126">Stream.</span></span>
<span data-ttu-id="9f8b2-127">retourne un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-127">Returns an array of strings.</span></span>
- <span data-ttu-id="9f8b2-128">Document.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-128">Document.</span></span>
<span data-ttu-id="9f8b2-129">Retourne un objet **XmlDocument** .</span><span class="sxs-lookup"><span data-stu-id="9f8b2-129">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="9f8b2-130">La valeur par défaut est document.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-130">The default value is Document.</span></span>

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

### <span data-ttu-id="9f8b2-131">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="9f8b2-131">-Depth</span></span>

<span data-ttu-id="9f8b2-132">Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation XML.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-132">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="9f8b2-133">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-133">The default value is 1.</span></span>

<span data-ttu-id="9f8b2-134">Par exemple, si les propriétés de l'objet contiennent également des objets, pour enregistrer une représentation XML des propriétés des objets contenus, vous devez spécifier une profondeur de 2.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-134">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="9f8b2-135">La valeur par défaut peut être remplacée par le type d'objet des fichiers Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-135">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="9f8b2-136">Pour plus d'informations, consultez about_Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-136">For more information, see about_Types.ps1xml.</span></span>

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

### <span data-ttu-id="9f8b2-137">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9f8b2-137">-InputObject</span></span>

<span data-ttu-id="9f8b2-138">Spécifie l'objet à convertir.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-138">Specifies the object to be converted.</span></span> <span data-ttu-id="9f8b2-139">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-139">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="9f8b2-140">Vous pouvez également diriger les objets vers **ConvertTo-XML** .</span><span class="sxs-lookup"><span data-stu-id="9f8b2-140">You can also pipe objects to **ConvertTo-XML** .</span></span>

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

### <span data-ttu-id="9f8b2-141">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="9f8b2-141">-NoTypeInformation</span></span>

<span data-ttu-id="9f8b2-142">Omet l'attribut Type des nœuds d'objet.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-142">Omits the Type attribute from the object nodes.</span></span>

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

### <span data-ttu-id="9f8b2-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f8b2-143">CommonParameters</span></span>

<span data-ttu-id="9f8b2-144">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f8b2-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f8b2-145">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9f8b2-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f8b2-146">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9f8b2-146">INPUTS</span></span>

### <span data-ttu-id="9f8b2-147">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9f8b2-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9f8b2-148">Vous pouvez diriger n’importe quel objet vers **ConvertTo-XML** .</span><span class="sxs-lookup"><span data-stu-id="9f8b2-148">You can pipe any object to **ConvertTo-XML** .</span></span>

## <span data-ttu-id="9f8b2-149">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9f8b2-149">OUTPUTS</span></span>

### <span data-ttu-id="9f8b2-150">Document System. String ou System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="9f8b2-150">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="9f8b2-151">La valeur du paramètre *As* détermine le type d’objet retourné par **ConvertTo-XML** .</span><span class="sxs-lookup"><span data-stu-id="9f8b2-151">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="9f8b2-152">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9f8b2-152">NOTES</span></span>

## <span data-ttu-id="9f8b2-153">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9f8b2-153">RELATED LINKS</span></span>

[<span data-ttu-id="9f8b2-154">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="9f8b2-154">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="9f8b2-155">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="9f8b2-155">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="9f8b2-156">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="9f8b2-156">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="9f8b2-157">Obtient la date</span><span class="sxs-lookup"><span data-stu-id="9f8b2-157">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="9f8b2-158">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="9f8b2-158">Import-Clixml</span></span>](Import-Clixml.md)

