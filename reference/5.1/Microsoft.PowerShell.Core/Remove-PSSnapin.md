---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202677"
---
# <span data-ttu-id="8a415-103">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8a415-103">Remove-PSSnapin</span></span>

## <span data-ttu-id="8a415-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8a415-104">SYNOPSIS</span></span>
<span data-ttu-id="8a415-105">Supprime des composants logiciels enfichables Windows PowerShell de la session active.</span><span class="sxs-lookup"><span data-stu-id="8a415-105">Removes Windows PowerShell snap-ins from the current session.</span></span>

## <span data-ttu-id="8a415-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a415-106">SYNTAX</span></span>

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a415-107">Description</span><span class="sxs-lookup"><span data-stu-id="8a415-107">DESCRIPTION</span></span>
<span data-ttu-id="8a415-108">L’applet de commande **Remove-PSSnapin** supprime un composant logiciel enfichable Windows PowerShell de la session active.</span><span class="sxs-lookup"><span data-stu-id="8a415-108">The **Remove-PSSnapin** cmdlet removes a Windows PowerShell snap-in from the current session.</span></span>
<span data-ttu-id="8a415-109">Vous pouvez l’utiliser pour supprimer les composants logiciels enfichables que vous avez ajoutés à Windows PowerShell. vous ne pouvez pas utiliser cette applet de commande pour supprimer les composants logiciels enfichables qui sont installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a415-109">You can use it to remove snap-ins that you have added to Windows PowerShell You cannot use this cmdlet to remove the snap-ins that are installed with Windows PowerShell.</span></span>

<span data-ttu-id="8a415-110">Une fois que vous avez supprimé un composant logiciel enfichable de la session active, le composant logiciel enfichable est toujours chargé, mais les applets de commande et les fournisseurs du composant logiciel enfichable ne sont plus disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="8a415-110">After you remove a snap-in from the current session, the snap-in is still loaded, but the cmdlets and providers in the snap-in are no longer available in the session.</span></span>

## <span data-ttu-id="8a415-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8a415-111">EXAMPLES</span></span>

### <span data-ttu-id="8a415-112">Exemple 1 : supprimer un composant logiciel enfichable</span><span class="sxs-lookup"><span data-stu-id="8a415-112">Example 1: Remove a snap-in</span></span>

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

<span data-ttu-id="8a415-113">Cette commande supprime le composant logiciel enfichable **Microsoft. Exchange** de la session active.</span><span class="sxs-lookup"><span data-stu-id="8a415-113">This command removes the **Microsoft.Exchange** snap-in from the current session.</span></span>
<span data-ttu-id="8a415-114">Une fois l'exécution de la commande terminée, les applets de commande et les fournisseurs pris en charge par le composant logiciel enfichable ne sont plus disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="8a415-114">When the command is complete, the cmdlets and providers that the snap-in supported are not available in the session.</span></span>

### <span data-ttu-id="8a415-115">Exemple 2 : supprimer les composants logiciels enfichables à l’aide de noms avec le pipeline</span><span class="sxs-lookup"><span data-stu-id="8a415-115">Example 2: Remove snap-ins by using names with the pipeline</span></span>

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

<span data-ttu-id="8a415-116">Cette commande supprime les composants logiciels enfichables Windows PowerShell dont les noms commencent par SMP à partir de la session active.</span><span class="sxs-lookup"><span data-stu-id="8a415-116">This command removes the Windows PowerShell snap-ins that have names that start with smp from the current session.</span></span>

<span data-ttu-id="8a415-117">La commande utilise l’applet de commande **« obtient-PSSnapin »** pour récupérer les objets qui représentent les composants logiciels enfichables. L’opérateur de pipeline (|) envoie les résultats à l’applet de commande **Remove-PSSnapin** , qui les supprime de la session.</span><span class="sxs-lookup"><span data-stu-id="8a415-117">The command uses the **Get-PSSnapin** cmdlet to get objects that represent the snap-ins. The pipeline operator (|) sends the results to the **Remove-PSSnapin** cmdlet, which removes them from the session.</span></span>
<span data-ttu-id="8a415-118">Les fournisseurs et les applets de commande pris en charge par ce composant logiciel enfichable ne sont plus disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="8a415-118">The providers and cmdlets that this snap-in supports are no longer available in the session.</span></span>

<span data-ttu-id="8a415-119">Lorsque vous dirigez des objets vers **Remove-PSSnapin** , les noms des objets sont associés au paramètre *Name* , qui accepte les objets du pipeline qui ont une propriété **Name** .</span><span class="sxs-lookup"><span data-stu-id="8a415-119">When you pipe objects to **Remove-PSSnapin** , the names of the objects are associated with the *Name* parameter, which accepts objects from the pipeline that have a **Name** property.</span></span>

### <span data-ttu-id="8a415-120">Exemple 3 : supprimer des composants logiciels enfichables à l’aide de noms</span><span class="sxs-lookup"><span data-stu-id="8a415-120">Example 3: Remove snap-ins by using names</span></span>

```
PS C:\> Remove-PSSnapin -Name *event*
```

<span data-ttu-id="8a415-121">Cette commande supprime tous les composants logiciels enfichables Windows PowerShell dont les noms incluent Event.</span><span class="sxs-lookup"><span data-stu-id="8a415-121">This command removes all Windows PowerShell snap-ins that have names that include event.</span></span>

## <span data-ttu-id="8a415-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a415-122">PARAMETERS</span></span>

### <span data-ttu-id="8a415-123">-Name</span><span class="sxs-lookup"><span data-stu-id="8a415-123">-Name</span></span>
<span data-ttu-id="8a415-124">Spécifie les noms des composants logiciels enfichables Windows PowerShell à supprimer de la session active.</span><span class="sxs-lookup"><span data-stu-id="8a415-124">Specifies the names of Windows PowerShell snap-ins to remove from the current session.</span></span>
<span data-ttu-id="8a415-125">Les caractères génériques (\*) sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8a415-125">Wildcard characters (\*) are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8a415-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8a415-126">-PassThru</span></span>
<span data-ttu-id="8a415-127">Retourne un objet qui représente le composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="8a415-127">Returns an object that represents the snap-in.</span></span>
<span data-ttu-id="8a415-128">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="8a415-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8a415-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a415-129">-Confirm</span></span>
<span data-ttu-id="8a415-130">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a415-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a415-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a415-131">-WhatIf</span></span>
<span data-ttu-id="8a415-132">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a415-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8a415-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8a415-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8a415-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a415-134">CommonParameters</span></span>
<span data-ttu-id="8a415-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a415-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a415-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8a415-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a415-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8a415-137">INPUTS</span></span>

### <span data-ttu-id="8a415-138">System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="8a415-138">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="8a415-139">Vous pouvez diriger un objet de composant logiciel enfichable vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a415-139">You can pipe a snap-in object to this cmdlet.</span></span>

## <span data-ttu-id="8a415-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8a415-140">OUTPUTS</span></span>

### <span data-ttu-id="8a415-141">Aucun, System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="8a415-141">None, System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="8a415-142">Cette applet de commande génère un objet **System. Management. Automation. PSSnapInInfo** qui représente le composant logiciel enfichable, si vous spécifiez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="8a415-142">This cmdlet generates a **System.Management.Automation.PSSnapInInfo** object that represents the snap-in, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="8a415-143">Par défaut, **Remove-PSSnapin** ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="8a415-143">By default, **Remove-PSSnapin** does not generate any output.</span></span>

## <span data-ttu-id="8a415-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8a415-144">NOTES</span></span>

* <span data-ttu-id="8a415-145">**Remove-PSSnapin** ne vérifie pas la version de Windows PowerShell avant de supprimer un composant logiciel enfichable de la session.</span><span class="sxs-lookup"><span data-stu-id="8a415-145">**Remove-PSSnapin** does not check the version of Windows PowerShell before removing a snap-in from the session.</span></span> <span data-ttu-id="8a415-146">Si un composant logiciel enfichable ne peut pas être supprimé, un avertissement s'affiche avant l'échec de la commande.</span><span class="sxs-lookup"><span data-stu-id="8a415-146">If a snap-in cannot be removed, a warning appears and the command fails.</span></span>
* <span data-ttu-id="8a415-147">**Remove-PSSnapin** affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="8a415-147">**Remove-PSSnapin** affects only the current session.</span></span> <span data-ttu-id="8a415-148">Si vous avez ajouté une commande Add-PSSnapin à votre profil Windows PowerShell, vous devez la supprimer pour retirer le composant logiciel enfichable des futures sessions.</span><span class="sxs-lookup"><span data-stu-id="8a415-148">If you have added an Add-PSSnapin command to your Windows PowerShell profile, you should delete the command to remove the snap-in from future sessions.</span></span> <span data-ttu-id="8a415-149">Pour obtenir des instructions, tapez `Get-Help about_Profiles` .</span><span class="sxs-lookup"><span data-stu-id="8a415-149">For instructions, type `Get-Help about_Profiles`.</span></span>

## <span data-ttu-id="8a415-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8a415-150">RELATED LINKS</span></span>

[<span data-ttu-id="8a415-151">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8a415-151">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="8a415-152">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8a415-152">Get-PSSnapin</span></span>](Get-PSSnapin.md)
