---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 1011011c8ce5471f976336e6b563f6d1662e17e4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201421"
---
# <span data-ttu-id="33ec7-103">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="33ec7-103">Remove-TypeData</span></span>

## <span data-ttu-id="33ec7-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="33ec7-104">Synopsis</span></span>
<span data-ttu-id="33ec7-105">Supprime les types étendus de la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-105">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="33ec7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33ec7-106">Syntax</span></span>

### <span data-ttu-id="33ec7-107">RemoveTypeDataSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="33ec7-107">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="33ec7-108">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="33ec7-108">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="33ec7-109">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="33ec7-109">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="33ec7-110">Description</span><span class="sxs-lookup"><span data-stu-id="33ec7-110">DESCRIPTION</span></span>

<span data-ttu-id="33ec7-111">L' `Remove-TypeData` applet de commande supprime les données de type étendu de la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-111">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="33ec7-112">Cette applet de commande affecte seulement la session active et les sessions qui sont créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-112">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="33ec7-113">Vous pouvez ajouter des propriétés et des méthodes aux objets dans PowerShell en les définissant dans les `Update-TypeData` commandes et les `Types.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="33ec7-113">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="33ec7-114">`Remove-TypeData` supprime ces propriétés et méthodes étendues de la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-114">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="33ec7-115">`Remove-TypeData` ne supprime pas les `Types.ps1xml` fichiers ou ne supprime pas les définitions de type étendu des `Types.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="33ec7-115">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="33ec7-116">Pour plus d’informations sur les `Types.ps1xml` fichiers, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="33ec7-116">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="33ec7-117">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="33ec7-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="33ec7-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="33ec7-118">Examples</span></span>

### <span data-ttu-id="33ec7-119">Exemple 1 : supprimer les données de type pour un type spécifié</span><span class="sxs-lookup"><span data-stu-id="33ec7-119">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="33ec7-120">Cet exemple supprime toutes les données de type pour le type **System. Array** de la session, y compris les données de type qui ont été ajoutées par un `Types.ps1xml` fichier et les données de type dynamique qui ont été ajoutées à la session à l’aide de l’applet de commande `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="33ec7-120">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="33ec7-121">Exemple 2 : supprimer un type de données étendu d’une session</span><span class="sxs-lookup"><span data-stu-id="33ec7-121">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="33ec7-122">Cet exemple montre l’effet de la suppression des données de type étendu d’une session.</span><span class="sxs-lookup"><span data-stu-id="33ec7-122">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="33ec7-123">La première `Get-TypeData` obtient les données de type étendu pour le type **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="33ec7-123">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="33ec7-124">La sortie indique qu’une propriété **DateTime** a été ajoutée à tous les objets **System. DateTime** dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33ec7-124">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="33ec7-125">L' `Get-Date` applet de commande retourne un objet **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="33ec7-125">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="33ec7-126">La commande utilise la notation par points pour récupérer la valeur de la propriété **DateTime** de l’objet **System. DateTime** qui `Get-Date` retourne.</span><span class="sxs-lookup"><span data-stu-id="33ec7-126">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

<span data-ttu-id="33ec7-127">L' `Get-TypeData` applet de commande suivante pour obtenir toutes les données de type étendu pour le type **System. DateTime** et les canalise vers l' `Remove-TypeData` applet de commande pour supprimer les données de type étendu.</span><span class="sxs-lookup"><span data-stu-id="33ec7-127">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="33ec7-128">La dernière `Get-Date` applet de commande montre l’effet de la suppression des données de type étendu pour le type **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="33ec7-128">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="33ec7-129">Étant donné que la propriété **System. DateTime** n’existe plus, une commande permettant d’obtenir sa valeur ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="33ec7-129">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="33ec7-130">Exemple 3 : supprimer les types étendus pour les modules</span><span class="sxs-lookup"><span data-stu-id="33ec7-130">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="33ec7-131">Cet exemple supprime toutes les données de type étendu pour les objets de module.</span><span class="sxs-lookup"><span data-stu-id="33ec7-131">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="33ec7-132">Quand vous dirigez un objet vers `Remove-TypeData` , `Remove-TypeData` obtient le nom du type d’objet et supprime toutes les données de type pour tous les objets de ce type.</span><span class="sxs-lookup"><span data-stu-id="33ec7-132">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="33ec7-133">Exemple 4 : supprimer les types étendus des modules spécifiés</span><span class="sxs-lookup"><span data-stu-id="33ec7-133">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="33ec7-134">Cet exemple utilise le paramètre **path** de l' `Remove-TypeData` applet de commande pour supprimer les types étendus qui sont définis dans les `Types.ps1xml` fichiers ajoutés par les modules **PSScheduledJob** et **PSWorkflow** .</span><span class="sxs-lookup"><span data-stu-id="33ec7-134">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="33ec7-135">Cette commande n’affecte pas les données de type dynamique ajoutées à l’aide de l’applet de commande `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="33ec7-135">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="33ec7-136">Cette commande réussit seulement quand les modules ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-136">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="33ec7-137">Pour plus d’informations sur les modules, consultez [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="33ec7-137">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="33ec7-138">Exemple 5 : supprimer les types étendus d’une session distante</span><span class="sxs-lookup"><span data-stu-id="33ec7-138">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="33ec7-139">Cet exemple supprime les types étendus d’une session à distance.</span><span class="sxs-lookup"><span data-stu-id="33ec7-139">This example removes extended types from a remote session.</span></span> <span data-ttu-id="33ec7-140">La commande utilise l' `Invoke-Command` applet de commande pour supprimer les données de type étendu pour tous les types CIM dans les sessions de la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="33ec7-140">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="33ec7-141">Paramètres</span><span class="sxs-lookup"><span data-stu-id="33ec7-141">Parameters</span></span>

### <span data-ttu-id="33ec7-142">-Path</span><span class="sxs-lookup"><span data-stu-id="33ec7-142">-Path</span></span>

<span data-ttu-id="33ec7-143">Spécifie un tableau de fichiers que cette applet de commande supprime des données de type étendu de la session.</span><span class="sxs-lookup"><span data-stu-id="33ec7-143">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="33ec7-144">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="33ec7-144">This parameter is required.</span></span>

<span data-ttu-id="33ec7-145">Entrez les chemins d’accès et les noms de fichiers d’un ou de plusieurs `Types.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="33ec7-145">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="33ec7-146">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="33ec7-146">Wildcards are not supported.</span></span> <span data-ttu-id="33ec7-147">Si vous omettez le chemin d'accès, l'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="33ec7-147">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33ec7-148">-TypeData</span><span class="sxs-lookup"><span data-stu-id="33ec7-148">-TypeData</span></span>

<span data-ttu-id="33ec7-149">Spécifie les données de type que cette applet de commande supprime de la session.</span><span class="sxs-lookup"><span data-stu-id="33ec7-149">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="33ec7-150">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="33ec7-150">This parameter is required.</span></span> <span data-ttu-id="33ec7-151">Entrez une variable qui contient des objets **TypeData** ( **System. Management. Automation. instances d’exécution. TypeData** ) ou une commande qui obtient les objets **TypeData** , par exemple une `Get-TypeData` commande.</span><span class="sxs-lookup"><span data-stu-id="33ec7-151">Enter a variable that contains **TypeData** objects ( **System.Management.Automation.Runspaces.TypeData** ) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="33ec7-152">Vous pouvez également diriger les objets **TypeData** vers `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="33ec7-152">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="33ec7-153">-TypeName</span><span class="sxs-lookup"><span data-stu-id="33ec7-153">-TypeName</span></span>

<span data-ttu-id="33ec7-154">Spécifie les types pour lesquels cette applet de commande supprime toutes les données de type étendu.</span><span class="sxs-lookup"><span data-stu-id="33ec7-154">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="33ec7-155">Pour les types de l'espace de noms système, entrez le nom court.</span><span class="sxs-lookup"><span data-stu-id="33ec7-155">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="33ec7-156">Sinon, le nom de type complet est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="33ec7-156">Otherwise, the full type name is required.</span></span> <span data-ttu-id="33ec7-157">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="33ec7-157">Wildcards are not supported.</span></span>

<span data-ttu-id="33ec7-158">Vous pouvez diriger les noms de types vers `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="33ec7-158">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="33ec7-159">Quand vous dirigez un objet vers `Remove-TypeData` , `Remove-TypeData` obtient le nom de type de l’objet et supprime toutes les données de type pour le type d’objet.</span><span class="sxs-lookup"><span data-stu-id="33ec7-159">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="33ec7-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="33ec7-160">-Confirm</span></span>

<span data-ttu-id="33ec7-161">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="33ec7-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="33ec7-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="33ec7-162">-WhatIf</span></span>

<span data-ttu-id="33ec7-163">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="33ec7-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="33ec7-164">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="33ec7-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="33ec7-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33ec7-165">CommonParameters</span></span>

<span data-ttu-id="33ec7-166">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33ec7-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33ec7-167">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="33ec7-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33ec7-168">Entrées</span><span class="sxs-lookup"><span data-stu-id="33ec7-168">Inputs</span></span>

### <span data-ttu-id="33ec7-169">System. Management. Automation. instances d’exécution. TypeData</span><span class="sxs-lookup"><span data-stu-id="33ec7-169">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="33ec7-170">Vous pouvez diriger un objet **TypeData** , tel que celui vers lequel l' `Get-TypeData` applet de commande retourne `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="33ec7-170">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="33ec7-171">System.String</span><span class="sxs-lookup"><span data-stu-id="33ec7-171">System.String</span></span>

<span data-ttu-id="33ec7-172">Vous pouvez diriger les noms de types vers `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="33ec7-172">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="33ec7-173">Quand vous dirigez un objet vers `Remove-TypeData` , `Remove-TypeData` obtient le nom de type de l’objet et supprime toutes les données de type pour le type d’objet.</span><span class="sxs-lookup"><span data-stu-id="33ec7-173">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="33ec7-174">Sorties</span><span class="sxs-lookup"><span data-stu-id="33ec7-174">Outputs</span></span>

### <span data-ttu-id="33ec7-175">Aucun</span><span class="sxs-lookup"><span data-stu-id="33ec7-175">None</span></span>

<span data-ttu-id="33ec7-176">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="33ec7-176">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="33ec7-177">Notes</span><span class="sxs-lookup"><span data-stu-id="33ec7-177">Notes</span></span>

<span data-ttu-id="33ec7-178">`Remove-TypeData` peut supprimer uniquement les données de type étendu dans la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-178">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="33ec7-179">Il ne peut pas supprimer les données de type étendu qui se trouvent sur l'ordinateur, mais qui n'ont pas été ajoutées à la session active, comme des types étendus qui sont définis dans des modules qui n'ont pas été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="33ec7-179">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="33ec7-180">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="33ec7-180">Related links</span></span>

[<span data-ttu-id="33ec7-181">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="33ec7-181">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="33ec7-182">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="33ec7-182">Update-TypeData</span></span>](Update-TypeData.md)
