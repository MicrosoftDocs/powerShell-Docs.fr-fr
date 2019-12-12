---
title: Applets de commande du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359978"
---
# <a name="provider-cmdlets"></a>Applets de commande de fournisseur

Les applets de commande que l’utilisateur peut exécuter pour gérer un magasin de données sont appelées « applets de commande de fournisseur ». Pour prendre en charge ces applets de commande, vous devez remplacer certaines des méthodes définies par les classes et les interfaces du fournisseur de base.

## <a name="provider-cmdlets"></a>Applets de commande du fournisseur

Voici les applets de commande du fournisseur qui peuvent être exécutées par l’utilisateur :

### <a name="psdrive-cmdlets"></a>PSDrive, applets de commande

- `Get-PSDrive`: cette applet de commande retourne les lecteurs Windows PowerShell dans la session active. Vous n’avez pas besoin de remplacer les méthodes pour prendre en charge cette applet de commande.

- `New-PSDrive`: cette applet de commande permet à l’utilisateur de créer des lecteurs Windows PowerShell pour accéder au magasin de données. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Drivecmdletprovider. les](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

- `Remove-PSDrive`: cette applet de commande permet à l’utilisateur de supprimer les lecteurs Windows PowerShell qui accèdent au magasin de données. Pour prendre en charge cette applet de commande, remplacez la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Applets de commande Item

- `Clear-Item`: cette applet de commande permet à l’utilisateur de supprimer la valeur d’un élément dans le magasin de données. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) et [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

- `Copy-Item`: cette applet de commande permet à l’utilisateur de copier un élément d’un emplacement vers un autre. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) et [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

- `Get-Item`: cette applet de commande permet à l’utilisateur de récupérer des données à partir du magasin de données. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

- `Get-ChildItem`: cette applet de commande permet à l’utilisateur de récupérer les éléments enfants de l’élément parent. Pour prendre en charge cette applet de commande, remplacez les méthodes suivantes :

  - [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: cette applet de commande permet à l’utilisateur d’exécuter l’action par défaut spécifiée par l’élément. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) et [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

- `Move-Item`: cette applet de commande permet à l’utilisateur de déplacer un élément d’un emplacement vers un autre emplacement. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) et [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: cette applet de commande permet à l’utilisateur de créer un nouvel élément dans le magasin de données.

- `Remove-Item`: cette applet de commande permet à l’utilisateur de supprimer des éléments du magasin de données. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) et [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: cette applet de commande permet à l’utilisateur de renommer des éléments dans le magasin de données. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Containercmdletprovider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) et [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

- `Set-Item`: cette applet de commande permet à l’utilisateur de mettre à jour les valeurs des éléments dans le magasin de données. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) et [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

### <a name="item-content-cmdlets"></a>Applets de commande de contenu d’élément

- `Add-Content`: cette applet de commande permet à l’utilisateur d’ajouter du contenu à un élément.

- `Clear-Content`: cette applet de commande permet à l’utilisateur de supprimer le contenu d’un élément sans supprimer l’élément. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) et [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

- `Get-Content`: cette applet de commande permet à l’utilisateur de récupérer le contenu d’un élément. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) et [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . La méthode [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) retourne une interface [System. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) qui définit les méthodes utilisées pour lire le contenu.

- `Set-Content`: cette applet de commande permet à l’utilisateur de mettre à jour le contenu d’un élément. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) et [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) . La méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) retourne une interface [System. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) qui définit les méthodes utilisées pour écrire le contenu.

### <a name="item-property-cmdlets"></a>Applets de commande de propriété Item

- `Clear-ItemProperty`: cette applet de commande permet à l’utilisateur de supprimer la valeur d’une propriété. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) et [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

- `Copy-ItemProperty`: cette applet de commande permet à l’utilisateur de copier une propriété et sa valeur d’un emplacement vers un autre. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) et [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) .

- `Get-ItemProperty`: cette applet de commande récupère les propriétés d’un élément. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) et [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: cette applet de commande permet à l’utilisateur de déplacer une propriété et sa valeur d’un emplacement à un autre. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) et [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) .

- `New-ItemProperty`: cette applet de commande permet à l’utilisateur de créer une nouvelle propriété et de définir sa valeur. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) et [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

- `Remove-ItemProperty`: cette applet de commande permet à l’utilisateur de supprimer une propriété et sa valeur. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) et [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

- `Rename-ItemProperty`: cette applet de commande permet à l’utilisateur de modifier le nom d’une propriété. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) et [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

- `Set-ItemProperty`: cette applet de commande permet à l’utilisateur de mettre à jour les propriétés d’un élément. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) et [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Applets de commande Location

- `Get-Location`: récupère des informations sur l’emplacement de travail actuel. Vous n’avez pas besoin de remplacer les méthodes pour prendre en charge cette applet de commande.

- `Pop-Location`: cette applet de commande modifie l’emplacement actuel à l’emplacement le plus récemment déplacé vers la pile. Vous n’avez pas besoin de remplacer les méthodes pour prendre en charge cette applet de commande.

- `Push-Location`: cette applet de commande ajoute l’emplacement actuel en haut d’une liste d’emplacements (une « pile »). Vous n’avez pas besoin de remplacer les méthodes pour prendre en charge cette applet de commande.

- `Set-Location`: cette applet de commande définit l’emplacement de travail actuel à un emplacement spécifié. Vous n’avez pas besoin de remplacer les méthodes pour prendre en charge cette applet de commande.

### <a name="path-cmdlets"></a>Applets de commande Path

- `Join-Path`: cette applet de commande permet à l’utilisateur de combiner un segment de chemin d’accès parent et enfant pour créer un chemin d’accès interne au fournisseur. Pour prendre en charge cette applet de commande, remplacez la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: cette applet de commande convertit un chemin d’accès Windows PowerShell en chemin d’accès du fournisseur Windows PowerShell.

- `Split-Path`: retourne la partie spécifiée d’un chemin d’accès.

- `Resolve-Path`: résout les caractères génériques dans un chemin d’accès et affiche le contenu du chemin d’accès.

- `Test-Path`: cette applet de commande détermine si tous les éléments d’un chemin d’accès existent. Pour prendre en charge cette applet de commande, remplacez les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. itemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) et [System. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) .

### <a name="psprovider-cmdlets"></a>Applets de commande PSProvider

- `Get-PSProvider`: cette applet de commande retourne des informations sur les fournisseurs disponibles dans la session. Vous n’avez pas besoin de remplacer les méthodes pour prendre en charge cette applet de commande.