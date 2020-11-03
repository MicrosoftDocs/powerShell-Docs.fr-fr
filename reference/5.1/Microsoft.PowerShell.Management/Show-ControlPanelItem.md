---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203489"
---
# <span data-ttu-id="8bcb4-103">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8bcb4-103">Show-ControlPanelItem</span></span>

## <span data-ttu-id="8bcb4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8bcb4-104">SYNOPSIS</span></span>
<span data-ttu-id="8bcb4-105">Ouvre les éléments du panneau de commande.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-105">Opens control panel items.</span></span>

## <span data-ttu-id="8bcb4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8bcb4-106">SYNTAX</span></span>

### <span data-ttu-id="8bcb4-107">RegularName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8bcb4-107">RegularName (Default)</span></span>

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="8bcb4-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="8bcb4-108">CanonicalName</span></span>

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="8bcb4-109">ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8bcb4-109">ControlPanelItem</span></span>

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## <span data-ttu-id="8bcb4-110">Description</span><span class="sxs-lookup"><span data-stu-id="8bcb4-110">DESCRIPTION</span></span>

<span data-ttu-id="8bcb4-111">L' `Show-ControlPanelItem` applet de commande ouvre les éléments du panneau de configuration sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-111">The `Show-ControlPanelItem` cmdlet opens control panel items on the local computer.</span></span> <span data-ttu-id="8bcb4-112">Vous pouvez l’utiliser pour ouvrir des éléments du panneau de configuration par nom, catégorie ou description, même sur des systèmes qui n’ont pas d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-112">You can use it to open control panel items by name, category, or description, even on systems that do not have a user interface.</span></span> <span data-ttu-id="8bcb4-113">Vous pouvez diriger les éléments du panneau de configuration de l' `Get-ControlPanelItem` applet de commande vers `Show-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="8bcb4-113">You can pipe control panel items from the `Get-ControlPanelItem` cmdlet to `Show-ControlPanelItem`.</span></span>

<span data-ttu-id="8bcb4-114">`Show-ControlPanelItem` recherche uniquement les éléments du panneau de configuration qui peuvent être ouverts sur le système.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-114">`Show-ControlPanelItem` searches only control panel items that can be opened on the system.</span></span> <span data-ttu-id="8bcb4-115">Sur les ordinateurs qui ne disposent pas **du panneau de configuration** ou de l' **Explorateur de fichiers** , `Show-ControlPanelItem` recherche uniquement les éléments du panneau de configuration qui peuvent être ouverts sans ces composants.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-115">On computers that do not have **Control Panel** or **File Explorer** , `Show-ControlPanelItem` searches only control panel items that can open without these components.</span></span>

<span data-ttu-id="8bcb4-116">Cette applet de commande a été introduite dans Windows PowerShell 3,0 et fonctionne sur Windows 8, Windows Server 2012 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-116">This cmdlet was introduced in Windows PowerShell 3.0 and works on Windows 8, Windows Server 2012, and higher versions.</span></span>

## <span data-ttu-id="8bcb4-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8bcb4-117">EXAMPLES</span></span>

### <span data-ttu-id="8bcb4-118">Exemple 1 : afficher un élément du panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="8bcb4-118">Example 1: Show a control panel item</span></span>

<span data-ttu-id="8bcb4-119">Cet exemple lance l’élément du panneau de configuration de l' **exécution automatique** .</span><span class="sxs-lookup"><span data-stu-id="8bcb4-119">This example launches the **AutoPlay** control panel item.</span></span>

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### <span data-ttu-id="8bcb4-120">Exemple 2 : diriger un élément du panneau de configuration vers cette applet de commande</span><span class="sxs-lookup"><span data-stu-id="8bcb4-120">Example 2: Pipe a control panel item to this cmdlet</span></span>

<span data-ttu-id="8bcb4-121">Cet exemple ouvre l’élément du panneau de configuration du **pare-feu Windows Defender** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-121">This example opens the **Windows Defender Firewall** control panel item on the local computer.</span></span>
<span data-ttu-id="8bcb4-122">Le nom de l’élément du panneau de configuration du pare-feu Windows a changé par rapport aux versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-122">The name of the Windows Firewall control panel item has changed over the versions of Windows.</span></span> <span data-ttu-id="8bcb4-123">Cet exemple utilise un modèle de caractère générique pour Rechercher l’élément du panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-123">This example uses a wildcard pattern to find the control panel item.</span></span>

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="8bcb4-124">`Get-ControlPanelItem` Obtient l’élément du panneau de configuration et l’applet de commande l' `Show-ControlPanelItem` ouvre.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-124">`Get-ControlPanelItem` gets the control panel item and the `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="8bcb4-125">Exemple 3 : Utiliser un nom de fichier pour ouvrir un élément du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="8bcb4-125">Example 3: Use a file name to open a control panel item</span></span>

<span data-ttu-id="8bcb4-126">Cet exemple ouvre l’élément **programmes et fonctionnalités** du panneau de configuration en utilisant son nom d’application.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-126">This example opens the **Programs and Features** control panel item by using its application name.</span></span>

```powershell
appwiz.cpl
```

<span data-ttu-id="8bcb4-127">Cette méthode est une alternative à l’utilisation d’une `Show-ControlPanelItem` commande.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-127">This method is an alternative to using a `Show-ControlPanelItem` command.</span></span>

> [!NOTE]
> <span data-ttu-id="8bcb4-128">Dans PowerShell, vous pouvez omettre l’extension de fichier. cpl pour les fichiers du panneau de configuration, car elle est incluse dans la valeur de la `$env:PathExt` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-128">In PowerShell, you can omit the .cpl file extension for control panel files because it's included in the value of the `$env:PathExt` environment variable.</span></span>

## <span data-ttu-id="8bcb4-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8bcb4-129">PARAMETERS</span></span>

### <span data-ttu-id="8bcb4-130">-CanonicalName</span><span class="sxs-lookup"><span data-stu-id="8bcb4-130">-CanonicalName</span></span>

<span data-ttu-id="8bcb4-131">Spécifie les éléments du panneau de configuration à l’aide des noms canoniques ou modèles de nom spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-131">Specifies control panel items by using the specified canonical names or name patterns.</span></span> <span data-ttu-id="8bcb4-132">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-132">Wildcard characters are permitted.</span></span> <span data-ttu-id="8bcb4-133">Si vous entrez plusieurs noms, cette applet de commande ouvre les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur **or** .</span><span class="sxs-lookup"><span data-stu-id="8bcb4-133">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8bcb4-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8bcb4-134">-InputObject</span></span>

<span data-ttu-id="8bcb4-135">Spécifie les éléments du panneau de configuration à ouvrir en envoyant des objets éléments du panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-135">Specifies control panel items to open by submitting control panel item objects.</span></span> <span data-ttu-id="8bcb4-136">Entrez une variable qui contient les objets éléments du panneau de configuration, ou tapez une commande ou une expression qui obtient les objets éléments du panneau de configuration, tels que `Get-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="8bcb4-136">Enter a variable that contains control panel item objects, or type a command or expression that gets control panel item objects, such as `Get-ControlPanelItem`.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8bcb4-137">-Name</span><span class="sxs-lookup"><span data-stu-id="8bcb4-137">-Name</span></span>

<span data-ttu-id="8bcb4-138">Spécifie les noms des éléments du panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-138">Specifies names of control panel items.</span></span> <span data-ttu-id="8bcb4-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="8bcb4-140">Si vous entrez plusieurs noms, cette applet de commande ouvre les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur **or** .</span><span class="sxs-lookup"><span data-stu-id="8bcb4-140">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8bcb4-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8bcb4-141">CommonParameters</span></span>

<span data-ttu-id="8bcb4-142">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8bcb4-143">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8bcb4-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8bcb4-144">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8bcb4-144">INPUTS</span></span>

### <span data-ttu-id="8bcb4-145">System. String, Microsoft. PowerShell. Commands. ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8bcb4-145">System.String, Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="8bcb4-146">Vous pouvez diriger un nom ou un objet élément du panneau de configuration vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-146">You can pipe a name or control panel item object to this cmdlet.</span></span>

## <span data-ttu-id="8bcb4-147">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8bcb4-147">OUTPUTS</span></span>

### <span data-ttu-id="8bcb4-148">Aucun</span><span class="sxs-lookup"><span data-stu-id="8bcb4-148">None</span></span>

<span data-ttu-id="8bcb4-149">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8bcb4-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="8bcb4-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8bcb4-150">NOTES</span></span>

## <span data-ttu-id="8bcb4-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8bcb4-151">RELATED LINKS</span></span>

[<span data-ttu-id="8bcb4-152">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8bcb4-152">Get-ControlPanelItem</span></span>](Get-ControlPanelItem.md)
