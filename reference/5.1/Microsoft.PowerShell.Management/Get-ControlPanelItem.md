---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204025"
---
# <span data-ttu-id="8e2cf-103">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8e2cf-103">Get-ControlPanelItem</span></span>

## <span data-ttu-id="8e2cf-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8e2cf-104">SYNOPSIS</span></span>
<span data-ttu-id="8e2cf-105">Obtient les éléments du panneau de commande.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-105">Gets control panel items.</span></span>

## <span data-ttu-id="8e2cf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8e2cf-106">SYNTAX</span></span>

### <span data-ttu-id="8e2cf-107">RegularName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8e2cf-107">RegularName (Default)</span></span>

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8e2cf-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="8e2cf-108">CanonicalName</span></span>

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8e2cf-109">Description</span><span class="sxs-lookup"><span data-stu-id="8e2cf-109">DESCRIPTION</span></span>

<span data-ttu-id="8e2cf-110">L' `Get-ControlPanelItem` applet de commande obtient les éléments du panneau de configuration sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-110">The `Get-ControlPanelItem` cmdlet gets control panel items on the local computer.</span></span> <span data-ttu-id="8e2cf-111">Vous pouvez l’utiliser pour rechercher des éléments du Panneau de configuration par nom, catégorie ou description, même sur des systèmes sans interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-111">You can use it to find control panel items by name, category, or description, even on systems that do not have a user interface.</span></span>

<span data-ttu-id="8e2cf-112">Cette applet de commande obtient uniquement les éléments du panneau de configuration qui peuvent être ouverts sur le système.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-112">This cmdlet gets only the control panel items that can be opened on the system.</span></span> <span data-ttu-id="8e2cf-113">Sur les ordinateurs qui ne disposent pas du panneau de configuration ou de l’Explorateur de fichiers, cette applet de commande obtient uniquement les éléments du panneau de configuration qui peuvent être ouverts sans ces composants.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-113">On computers that do not have Control Panel or File Explorer, this cmdlet gets only control panel items that can open without these components.</span></span>

<span data-ttu-id="8e2cf-114">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-114">This cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="8e2cf-115">Il fonctionne uniquement sur Windows 8 et Windows Server 2012 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-115">It works only on Windows 8 and Windows Server 2012 and newer.</span></span>

## <span data-ttu-id="8e2cf-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8e2cf-116">EXAMPLES</span></span>

### <span data-ttu-id="8e2cf-117">Exemple 1 : Obtenir tous les éléments du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="8e2cf-117">Example 1: Get all control panel items</span></span>

<span data-ttu-id="8e2cf-118">Cette commande obtient tous les éléments du Panneau de configuration présents sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-118">This command gets all control panel items on the local computer.</span></span>

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### <span data-ttu-id="8e2cf-119">Exemple 2 : Obtenir les éléments du Panneau de configuration par nom</span><span class="sxs-lookup"><span data-stu-id="8e2cf-119">Example 2: Get control panel items by name</span></span>

<span data-ttu-id="8e2cf-120">Cet exemple obtient les éléments du panneau de configuration dont le nom contient le programme ou l’application.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-120">This example gets control panel items that have Program or App in their names.</span></span>

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### <span data-ttu-id="8e2cf-121">Exemple 3 : Obtenir les éléments du Panneau de configuration par catégorie</span><span class="sxs-lookup"><span data-stu-id="8e2cf-121">Example 3: Get control panel items by category</span></span>

<span data-ttu-id="8e2cf-122">Cette commande obtient tous les éléments du panneau de configuration dans les catégories dont le nom contient la sécurité.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-122">This command gets all control panel items in categories that have Security in their names.</span></span>

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### <span data-ttu-id="8e2cf-123">Exemple 4 : Ouvrir un élément du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="8e2cf-123">Example 4: Open a control panel item</span></span>

<span data-ttu-id="8e2cf-124">Cet exemple ouvre l’élément du panneau de configuration du pare-feu Windows sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-124">This example opens the Windows Firewall control panel item on the local computer.</span></span>

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="8e2cf-125">L' `Get-ControlPanelItem` applet de commande obtient l’élément du panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-125">The `Get-ControlPanelItem` cmdlet gets the control panel item.</span></span> <span data-ttu-id="8e2cf-126">L’applet de commande l' `Show-ControlPanelItem` ouvre.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-126">The `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="8e2cf-127">Exemple 5 : Obtenir les éléments du Panneau de configuration sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="8e2cf-127">Example 5: Get control panel items on a remote computer</span></span>

<span data-ttu-id="8e2cf-128">Cet exemple obtient l’Chiffrement de lecteur BitLocker élément du panneau de configuration sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-128">This example gets the BitLocker Drive Encryption control panel item on the Server01 remote computer.</span></span>
<span data-ttu-id="8e2cf-129">L' `Invoke-Command` applet de commande exécute l' `Get-ControlPanelItem` applet de commande à distance.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-129">The `Invoke-Command` cmdlet runs the `Get-ControlPanelItem` cmdlet remotely.</span></span>

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### <span data-ttu-id="8e2cf-130">Exemple 6 : Rechercher les descriptions des éléments du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="8e2cf-130">Example 6: Search the descriptions of control panel items</span></span>

<span data-ttu-id="8e2cf-131">Cet exemple recherche la propriété **Description** des éléments du panneau de configuration pour n’afficher que ceux qui contiennent le nom de l' **appareil** .</span><span class="sxs-lookup"><span data-stu-id="8e2cf-131">This example searches the **Description** property of the control panel items to get only those that contain the name **Device** .</span></span>

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

<span data-ttu-id="8e2cf-132">L' `Get-ControlPanelItem` applet de commande obtient tous les éléments du panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-132">The `Get-ControlPanelItem` cmdlet gets all control panel items.</span></span> <span data-ttu-id="8e2cf-133">L' `Where-Object` applet de commande filtre les éléments selon la valeur de la propriété **Description** .</span><span class="sxs-lookup"><span data-stu-id="8e2cf-133">The `Where-Object` cmdlet filters the items by the value of the **Description** property.</span></span>

## <span data-ttu-id="8e2cf-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8e2cf-134">PARAMETERS</span></span>

### <span data-ttu-id="8e2cf-135">-CanonicalName</span><span class="sxs-lookup"><span data-stu-id="8e2cf-135">-CanonicalName</span></span>

<span data-ttu-id="8e2cf-136">Spécifie, sous forme de tableau de chaînes, les éléments du panneau de configuration par leurs noms canoniques ou modèles de nom que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-136">Specifies, as a string array, the control panel items by their canonical names or name patterns that this cmdlet gets.</span></span> <span data-ttu-id="8e2cf-137">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-137">Wildcards are permitted.</span></span> <span data-ttu-id="8e2cf-138">Si vous entrez plusieurs noms, cette applet de commande obtient les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur « or ».</span><span class="sxs-lookup"><span data-stu-id="8e2cf-138">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span>

<span data-ttu-id="8e2cf-139">Par défaut, cette applet de commande obtient tous les éléments du panneau de configuration du système.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-139">By default, this cmdlet gets all control panel items in the system.</span></span>

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

### <span data-ttu-id="8e2cf-140">-Catégorie</span><span class="sxs-lookup"><span data-stu-id="8e2cf-140">-Category</span></span>

<span data-ttu-id="8e2cf-141">Spécifie, sous forme de tableau de chaînes, les catégories des éléments du panneau de configuration dans les catégories spécifiées que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-141">Specifies, as a string array, the categories of the control panel items in the specified categories that this cmdlet gets.</span></span> <span data-ttu-id="8e2cf-142">Entrez un nom de catégorie ou un modèle de nom.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-142">Enter a category name or name pattern.</span></span> <span data-ttu-id="8e2cf-143">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-143">Wildcards are permitted.</span></span> <span data-ttu-id="8e2cf-144">Si vous entrez plusieurs noms, cette applet de commande obtient les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur « or ».</span><span class="sxs-lookup"><span data-stu-id="8e2cf-144">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span> <span data-ttu-id="8e2cf-145">Par défaut, cette applet de commande obtient tous les éléments du panneau de configuration du système.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-145">By default, this cmdlet gets all control panel items in the system.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8e2cf-146">-Name</span><span class="sxs-lookup"><span data-stu-id="8e2cf-146">-Name</span></span>

<span data-ttu-id="8e2cf-147">Spécifie, sous forme de tableau de chaînes, les noms ou modèles de nom du panneau de configuration que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-147">Specifies, as a string array, the names or name patterns of the control panel that this cmdlet gets.</span></span>
<span data-ttu-id="8e2cf-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-148">Wildcards are permitted.</span></span> <span data-ttu-id="8e2cf-149">Vous pouvez également diriger un nom ou un modèle de nom vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-149">You can also pipe a name or name pattern to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8e2cf-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8e2cf-150">CommonParameters</span></span>

<span data-ttu-id="8e2cf-151">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8e2cf-152">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8e2cf-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8e2cf-153">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8e2cf-153">INPUTS</span></span>

### <span data-ttu-id="8e2cf-154">System.String</span><span class="sxs-lookup"><span data-stu-id="8e2cf-154">System.String</span></span>

<span data-ttu-id="8e2cf-155">Vous pouvez diriger un nom ou un modèle de nom vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-155">You can pipe a name or name pattern to this cmdlet.</span></span>

## <span data-ttu-id="8e2cf-156">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8e2cf-156">OUTPUTS</span></span>

### <span data-ttu-id="8e2cf-157">Microsoft. PowerShell. Commands. ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8e2cf-157">Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="8e2cf-158">Cette applet de commande obtient les éléments du panneau de configuration sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-158">This cmdlet gets control panel items on the local computer.</span></span>

## <span data-ttu-id="8e2cf-159">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8e2cf-159">NOTES</span></span>

## <span data-ttu-id="8e2cf-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8e2cf-160">RELATED LINKS</span></span>

[<span data-ttu-id="8e2cf-161">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="8e2cf-161">Show-ControlPanelItem</span></span>](Show-ControlPanelItem.md)
