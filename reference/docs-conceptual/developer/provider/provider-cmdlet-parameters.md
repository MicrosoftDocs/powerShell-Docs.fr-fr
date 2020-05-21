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
ms.openlocfilehash: 8ce13032a55d164121a073ef94086dc1de09b902
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564204"
---
# <a name="provider-cmdlet-parameters"></a>Paramètres des applets de commande de fournisseur

Les applets de commande de fournisseur sont fournies avec un ensemble de paramètres statiques qui sont disponibles pour tous les fournisseurs qui prennent en charge l’applet de commande, ainsi que les paramètres dynamiques qui sont ajoutés lorsque l’utilisateur spécifie une certaine valeur pour certains paramètres statiques de l’applet de commande du fournisseur.

## <a name="provider-cmdlet-static-parameters"></a>Paramètres statiques de l’applet de commande du fournisseur

Les paramètres statiques sont définis par Windows PowerShell. Un grand ensemble de ces paramètres est implémenté par Windows PowerShell pour assurer la cohérence entre tous les fournisseurs et pour offrir une expérience de développement plus simple. Les `literalPath` `exclude` paramètres, et `include` de l’applet de commande sont des exemples de ces paramètres `Get-Item` . Un plus petit ensemble de ces paramètres peut être remplacé pour fournir des actions spécifiques à votre fournisseur. Les exemples de ces paramètres incluent `Path` le `Value` paramètre et de l’applet de commande `Set-Item` . Voici une liste des paramètres qui peuvent être remplacés pour les applets de commande du fournisseur.

`Clear-Content`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Clear-Content` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

`Clear-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Clear-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Name` paramètres et de l' `Clear-ItemProperty` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Destination` paramètres, et `Recurse` de l’applet de commande `Copy-Item` en implémentant la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) .

Applet de commande ChildItems : vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Recurse` paramètres et de l’applet de commande `Get-ChildItem` en implémentant les méthodes [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) et [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

`Get-Content`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Get-Content` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

`Get-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Get-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

`Get-ItemProperty`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs transmises aux `Path` `Name` paramètres et de l' `Get-ItemProperty` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

`Invoke-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Invoke-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

`Move-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Destination` paramètres et de l' `Move-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

`New-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `ItemType` paramètres, et `Value` de l’applet de commande `New-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) .

`New-ItemProperty`vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Name` paramètres,, `PropertyType` et `Value` de l' `New-ItemProperty` applet de commande en implémentant la méthode [Microsoft. PowerShell. Commands. Registryprovider. Newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) .

`Remove-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées `Path` aux `Recurse` paramètres et de l’applet de commande `Remove-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées `Path` aux `Name` paramètres et de l’applet de commande `Remove-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. RemoveProperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) .

`Rename-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `NewName` paramètres et de l' `Rename-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées `Path` aux `NewName` paramètres, et `Name` de l' `Rename-ItemProperty` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) .

`Set-Content`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Set-Content` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

`Set-Item`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Value` paramètres et de l' `Set-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

`Set-ItemProperty`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées aux `Path` `Value` paramètres et de l' `Set-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

`Test-Path`Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées au `Path` paramètre de l' `Test-Path` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

En outre, vous ne pouvez pas spécifier les caractéristiques de ces paramètres, par exemple s’ils sont facultatifs ou obligatoires, ni attribuer à ces paramètres un alias ou spécifier l’un des attributs de validation. En revanche, vous pouvez spécifier des caractéristiques de paramètre dans des applets de commande autonomes à l’aide d’attributs tels que l' `Parameters` attribut.

## <a name="provider-cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande du fournisseur

Les paramètres dynamiques pour les fournisseurs d’applets de commande sont similaires aux fournisseurs dynamiques pour les applets de commande autonomes. Dans les deux cas, les paramètres sont ajoutés à l’applet de commande lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres par défaut, tel que le `path` paramètre. Toutefois, tous les paramètres statiques ne peuvent pas être utilisés pour déclencher l’ajout de paramètres dynamiques. Pour plus d’informations sur les paramètres dynamiques, consultez [paramètres dynamiques des applets](./provider-cmdlet-dynamic-parameters.md)de commande du fournisseur.

## <a name="see-also"></a>Voir aussi

[Paramètres dynamiques des applets de commande du fournisseur](./provider-cmdlet-dynamic-parameters.md)

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)
