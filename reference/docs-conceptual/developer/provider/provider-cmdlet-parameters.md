---
title: Paramètres d’applet de commande du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366308"
---
# <a name="provider-cmdlet-parameters"></a>Paramètres des applets de commande de fournisseur

Les applets de commande de fournisseur sont fournies avec un ensemble de paramètres statiques qui sont disponibles pour tous les fournisseurs qui prennent en charge l’applet de commande, ainsi que les paramètres dynamiques qui sont ajoutés lorsque l’utilisateur spécifie une certaine valeur pour certains paramètres statiques de l’applet de commande du fournisseur.

## <a name="provider-cmdlet-static-parameters"></a>Paramètres statiques de l’applet de commande du fournisseur

Les paramètres statiques sont définis par Windows PowerShell. Un grand ensemble de ces paramètres est implémenté par Windows PowerShell pour assurer la cohérence entre tous les fournisseurs et pour offrir une expérience de développement plus simple. Les paramètres `literalPath`, `exclude`et `include` de l’applet de commande `Get-Item` sont des exemples de ces paramètres. Un plus petit ensemble de ces paramètres peut être remplacé pour fournir des actions spécifiques à votre fournisseur. Les exemples de ces paramètres incluent le paramètre `Path` et `Value` de l’applet de commande `Set-Item`. Voici une liste des paramètres qui peuvent être remplacés pour les applets de commande du fournisseur.

`Clear-Content` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Clear-Content` en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

`Clear-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Clear-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Name` de l’applet de commande `Clear-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path`, `Destination`et `Recurse` de l’applet de commande `Copy-Item` en implémentant la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) .

Applet de commande ChildItems : vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Recurse` de l’applet de commande `Get-ChildItem` en implémentant les méthodes [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) et [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

`Get-Content` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Get-Content` en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

`Get-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Get-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

`Get-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Name` de l’applet de commande `Get-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

`Invoke-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Invoke-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

`Move-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Destination` de l’applet de commande `Move-Item` en implémentant la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

`New-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path`, `ItemType`et `Value` de l’applet de commande `New-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) .

`New-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path`, `Name`, `PropertyType`et `Value` de l’applet de commande `New-ItemProperty` en implémentant la méthode [Microsoft. PowerShell. Commands. Registryprovider. Newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) .

`Remove-Item` vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Recurse` de l’applet de commande `Remove-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty` vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Name` de l’applet de commande `Remove-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. RemoveProperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) .

`Rename-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `NewName` de l’applet de commande `Rename-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty` vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path`, `NewName`et `Name` de l’applet de commande `Rename-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) .

`Set-Content` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Set-Content` en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

`Set-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Value` de l’applet de commande `Set-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

`Set-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux paramètres `Path` et `Value` de l’applet de commande `Set-Item` en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

`Test-Path` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au paramètre `Path` de l’applet de commande `Test-Path` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

En outre, vous ne pouvez pas spécifier les caractéristiques de ces paramètres, par exemple s’ils sont facultatifs ou obligatoires, ni attribuer à ces paramètres un alias ou spécifier l’un des attributs de validation. En revanche, vous pouvez spécifier des caractéristiques de paramètre dans des applets de commande autonomes à l’aide d’attributs tels que l’attribut `Parameters`.

## <a name="provider-cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande du fournisseur

Les paramètres dynamiques pour les fournisseurs d’applets de commande sont similaires aux fournisseurs dynamiques pour les applets de commande autonomes. Dans les deux cas, les paramètres sont ajoutés à l’applet de commande lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres par défaut, comme le paramètre `path`. Toutefois, tous les paramètres statiques ne peuvent pas être utilisés pour déclencher l’ajout de paramètres dynamiques. Pour plus d’informations sur les paramètres dynamiques, consultez [paramètres dynamiques des applets](./provider-cmdlet-dynamic-parameters.md)de commande du fournisseur.

## <a name="see-also"></a>Voir aussi

[Paramètres dynamiques des applets de commande du fournisseur](./provider-cmdlet-dynamic-parameters.md)

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)