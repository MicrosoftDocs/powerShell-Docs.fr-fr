---
title: Applets de commande fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854765"
---
# <a name="provider-cmdlets"></a>Applets de commande de fournisseur

Les applets de commande que l’utilisateur peut exécuter pour gérer un magasin de données sont appelés des applets de commande fournisseur. Pour prendre en charge de ces applets de commande, vous devez remplacer certaines des méthodes définies par les classes de fournisseur de base et interfaces.

## <a name="provider-cmdlets"></a>Applets de commande fournisseur

Voici les applets de commande fournisseur peut être exécuté par l’utilisateur :

### <a name="psdrive-cmdlets"></a>Applets de commande PSDrive

- `Get-PSDrive` : Cette applet de commande retourne que les lecteurs Windows PowerShell dans la session active. Il est inutile de remplacer toutes les méthodes pour prendre en charge de cette applet de commande.

- `New-PSDrive` : Cette applet de commande permet à l’utilisateur créer des lecteurs Windows PowerShell pour accéder au magasin de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) méthodes.

- `Remove-PSDrive` : Cette applet de commande permet à l’utilisateur à supprimer des lecteurs Windows PowerShell qui accèdent à la banque de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) (méthode).

### <a name="item-cmdlets"></a>Applets de commande Item

- `Clear-Item` : Cette applet de commande permet à l’utilisateur à supprimer de la valeur d’un élément dans le magasin de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) et [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) méthodes.

- `Copy-Item` : Cette applet de commande permet à l’utilisateur à copier un élément d’un emplacement vers un autre. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) et [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) méthodes.

- `Get-Item` : Cette applet de commande permet à l’utilisateur récupérer des données à partir du magasin de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) méthodes.

- `Get-ChildItem` : Cette applet de commande permet à l’utilisateur récupérer les éléments enfants de l’élément parent. Pour prendre en charge cette applet de commande, remplacer les méthodes suivantes :

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item` : Cette applet de commande permet à l’utilisateur effectuer l’action par défaut spécifiée par l’élément. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) et [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) méthodes.

- `Move-Item` : Cette applet de commande permet à l’utilisateur déplacer un élément d’un emplacement vers un autre emplacement. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) et [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)méthodes de s.

- `New-ItemProperty` : Cette applet de commande permet à l’utilisateur créer un nouvel élément dans le magasin de données.

- `Remove-Item` : Cette applet de commande permet à l’utilisateur à supprimer des éléments dans le magasin de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) et [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) méthodes.

- `Rename-Item` : Cette applet de commande permet à l’utilisateur renommer des éléments dans le magasin de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) et [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) méthodes.

- `Set-Item` : Cette applet de commande permet à l’utilisateur à mettre à jour les valeurs d’éléments dans le magasin de données. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) et [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) méthodes.

### <a name="item-content-cmdlets"></a>Applets de commande Item contenu

- `Add-Content` : Cette applet de commande permet à l’utilisateur d’ajouter du contenu à un élément.

- `Clear-Content` : Cette applet de commande permet à l’utilisateur à supprimer du contenu à partir d’un élément sans supprimer l’élément. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) et [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) méthodes.

- `Get-Content` : Cette applet de commande permet à l’utilisateur récupérer le contenu d’un élément. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) et [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) méthodes. Le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) méthode retourne un [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface qui définit les méthodes utilisées pour lire le contenu.

- `Set-Content` : Cette applet de commande permet à l’utilisateur à mettre à jour le contenu d’un élément. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) et [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) méthodes. Le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) méthode retourne un [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface qui définit les méthodes utilisées pour écrire le contenu.

### <a name="item-property-cmdlets"></a>Applets de commande de propriété Item

- `Clear-ItemProperty` : Cette applet de commande permet à l’utilisateur à supprimer la valeur d’une propriété. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) et [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) méthodes.

- `Copy-ItemProperty` : Cette applet de commande permet à l’utilisateur copie une propriété et sa valeur d’un emplacement à un autre. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) et [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) méthodes.

- `Get-ItemProperty` : Cette applet de commande récupère les propriétés d’un élément. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) et [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) méthodes.

- `Move-ItemProperty` : Cette applet de commande permet à l’utilisateur à déplacer une propriété et sa valeur d’un emplacement vers un autre. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) et [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) méthodes.

- `New-ItemProperty` : Cette applet de commande permet à l’utilisateur à créer une nouvelle propriété et définissez sa valeur. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) et [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) méthodes.

- `Remove-ItemProperty` : Cette applet de commande permet à l’utilisateur supprimer une propriété et sa valeur. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) et [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) méthodes.

- `Rename-ItemProperty` : Cette applet de commande permet à l’utilisateur modifier le nom d’une propriété. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) et [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) méthodes.

- `Set-ItemProperty` : Cette applet de commande permet à l’utilisateur à mettre à jour les propriétés d’un élément. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) et [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) méthodes.

### <a name="location-cmdlets"></a>Applets de commande location

- `Get-Location` : Récupère des informations sur l’emplacement de travail actuel. Il est inutile de remplacer toutes les méthodes pour prendre en charge de cette applet de commande.

- `Pop-Location` : Cette applet de commande modifie l’emplacement actuel vers le dernier emplacement placé sur la pile. Il est inutile de remplacer toutes les méthodes pour prendre en charge de cette applet de commande.

- `Push-Location` : Cette applet de commande ajoute l’emplacement actuel vers le haut d’une liste d’emplacements (ou « pile »). Il est inutile de remplacer toutes les méthodes pour prendre en charge de cette applet de commande.

- `Set-Location` : Cette applet de commande définit l’emplacement de travail actuel vers un emplacement spécifié. Il est inutile de remplacer toutes les méthodes pour prendre en charge de cette applet de commande.

### <a name="path-cmdlets"></a>Applets de commande de chemin d’accès

- `Join-Path` : Cette applet de commande permet à l’utilisateur combiner un segment de chemin d’accès parent et enfant pour créer un chemin d’accès interne au fournisseur. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) (méthode).

- `Convert-Path` : Cette applet de commande convertit un chemin d’accès à partir d’un chemin d’accès Windows PowerShell en un chemin d’accès du fournisseur Windows PowerShell.

- `Split-Path` : Retourne la partie spécifiée d'un chemin d'accès.

- `Resolve-Path` : Résout les caractères génériques inclus dans un chemin d'accès et affiche le contenu de ce dernier.

- `Test-Path` : Cette applet de commande détermine si tous les éléments d’un chemin d’accès existent. Pour prendre en charge cette applet de commande, vous devez remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) et [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) méthodes.

### <a name="psprovider-cmdlets"></a>Applets de commande PSProvider

- `Get-PSProvider` : Cette applet de commande retourne des informations sur les fournisseurs disponibles dans la session. Il est inutile de remplacer toutes les méthodes pour prendre en charge de cette applet de commande.