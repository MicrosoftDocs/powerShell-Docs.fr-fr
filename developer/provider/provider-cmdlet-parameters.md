---
title: Paramètres d’applet de commande de fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081136"
---
# <a name="provider-cmdlet-parameters"></a>Paramètres des applets de commande de fournisseur

Applets de commande fournisseur sont fournis avec un jeu de paramètres statiques qui sont disponibles à tous les fournisseurs qui prennent en charge de l’applet de commande, les paramètres ainsi que dynamiques qui sont ajoutés lorsque l’utilisateur spécifie une certaine valeur pour certains des paramètres de l’applet de commande fournisseur.

## <a name="provider-cmdlet-static-parameters"></a>Paramètres du fournisseur de statique de l’applet de commande

Paramètres statiques sont définis par Windows PowerShell. Un grand ensemble de ces paramètres est implémenté par Windows PowerShell pour assurer la cohérence entre tous les fournisseurs et pour fournir une expérience de développement plus simple. Exemples de ces paramètres incluent le `literalPath`, `exclude`, et `include` paramètres de la `Get-Item` applet de commande. Un jeu limité de ces paramètres peut être remplacé pour fournir des actions qui sont spécifiques à votre fournisseur. Exemples de ces paramètres incluent le `Path` et `Value` paramètre de la `Set-Item` applet de commande. Voici une liste des paramètres qui peuvent être remplacés pour les applets de commande fournisseur.

`Clear-Content` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Clear-Content` applet de commande en implémentant la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)(méthode).

`Clear-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Clear-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) méthode.

`Clear-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Name` paramètres de le `Clear-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) (méthode).

`Copy-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path`, `Destination`, et `Recurse` paramètres de le `Copy-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) (méthode).

Applet de commande Get-ChildItems vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Recurse` paramètres de le `Get-ChildItem` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) et [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) méthodes.

`Get-Content` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Get-Content` applet de commande en implémentant la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) (méthode).

`Get-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Get-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) (méthode).

`Get-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Name` paramètres de le `Get-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) (méthode).

`Invoke-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Invoke-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)(méthode).

`Move-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Destination` paramètres de le `Move-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) (méthode).

`New-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path`, `ItemType`, et `Value` paramètres de le `New-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) (méthode).

`New-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path`, `Name`, `PropertyType`, et `Value` paramètres de le `New-ItemProperty` applet de commande en implémentant le [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) (méthode).

`Remove-Item` Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Recurse` paramètres de le `Remove-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) (méthode).

`Remove-ItemProperty` Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Name` paramètres de le `Remove-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) (méthode).

`Rename-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `NewName` paramètres de le `Rename-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) (méthode).

`Rename-ItemProperty` Vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path`, `NewName`, et `Name` paramètres de le `Rename-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) (méthode).

`Set-Content` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Set-Content` applet de commande en implémentant la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) (méthode).

`Set-Item` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Value` paramètres de le `Set-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) (méthode).

`Set-ItemProperty` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` et `Value` paramètres de le `Set-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) (méthode).

`Test-Path` applet de commande vous pouvez définir la façon dont votre fournisseur utilisera les valeurs passées à la `Path` paramètre de la `Test-Path` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)(méthode).

En outre, vous ne pouvez pas spécifier les caractéristiques de ces paramètres, tels que si elles sont facultatives ou obligatoires, ni de ces paramètres, donnez-lui un alias ou spécifier un des attributs de validation. En revanche, vous pouvez spécifier les caractéristiques des paramètres dans les applets de commande autonomes à l’aide des attributs tels que le `Parameters` attribut.

## <a name="provider-cmdlet-dynamic-parameters"></a>Paramètres dynamiques de l’applet de commande du fournisseur

Les paramètres dynamiques pour les fournisseurs de l’applet de commande sont semblables aux fournisseurs dynamiques pour les applets de commande autonomes. Dans les deux cas, les paramètres sont ajoutés à l’applet de commande lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres par défaut, tels que le `path` paramètre. Toutefois, tous les paramètres statiques peuvent servir à déclencher l’ajout de paramètres dynamiques. Pour plus d’informations sur les paramètres dynamiques, consultez [fournisseur applet de commande des paramètres dynamiques](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Voir aussi

[Paramètres dynamiques de l’applet de commande du fournisseur](./provider-cmdlet-dynamic-parameters.md)

[Écriture d’un fournisseur PowerShell de Windows](./writing-a-windows-powershell-provider.md)