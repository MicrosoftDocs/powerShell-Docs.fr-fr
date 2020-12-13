---
ms.date: 08/21/2019
ms.topic: reference
title: Types de fournisseur
description: Types de fournisseur
ms.openlocfilehash: 9d3b458d7647a297fcda086db3540a0c15c576db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661753"
---
# <a name="provider-types"></a>Types de fournisseur

Les fournisseurs définissent leurs fonctionnalités de base en modifiant la façon dont les applets de commande du fournisseur, fournies par PowerShell, effectuent leurs actions. Par exemple, les fournisseurs peuvent utiliser la fonctionnalité par défaut de l’applet de commande `Get-Item` , ou ils peuvent modifier le fonctionnement de cette applet de commande lors de l’extraction d’éléments du magasin de données. La fonctionnalité du fournisseur décrite dans ce document comprend des fonctionnalités définies en remplaçant les méthodes à partir de classes de base et d’interfaces spécifiques du fournisseur.

> [!NOTE]
> Pour les fonctionnalités du fournisseur prédéfinies par PowerShell, consultez [fonctionnalités du fournisseur](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Fournisseurs compatibles avec le lecteur

Les fournisseurs compatibles avec le lecteur spécifient les lecteurs par défaut disponibles pour l’utilisateur et permettent à l’utilisateur d’ajouter ou de supprimer des lecteurs. Dans la plupart des cas, les fournisseurs sont des fournisseurs compatibles avec les lecteurs, car ils nécessitent un lecteur par défaut pour accéder à la Banque de données. Toutefois, lors de l’écriture de votre propre fournisseur, vous pouvez ou non souhaiter autoriser l’utilisateur à créer et à supprimer des lecteurs.

Pour créer un fournisseur compatible avec les lecteurs, votre classe de fournisseur doit dériver de la classe [System. Management. Automation. Provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) ou d’une autre classe qui dérive de cette classe. La classe **System. Management. Automation. Provider. DriveCmdletProvider** définit les méthodes suivantes pour l’implémentation des lecteurs par défaut du fournisseur et la prise en charge des `New-PSDrive` applets de commande et `Remove-PSDrive` . Dans la plupart des cas, pour prendre en charge une applet de commande de fournisseur, vous devez remplacer la méthode appelée par le moteur PowerShell pour appeler l’applet de commande, telle que la `NewDrive` méthode pour l' `New-PSDrive` applet de commande, et vous pouvez éventuellement remplacer une deuxième méthode, telle que `NewDriveDynamicParameters` , pour ajouter des paramètres dynamiques à l’applet de commande.

- La méthode [System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) définit les lecteurs par défaut qui sont disponibles pour l’utilisateur chaque fois que le fournisseur est utilisé.

- Les méthodes [System. Management. Automation. Provider. DriveCmdletProvider. les](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `New-PSDrive` fournisseur. Cette applet de commande permet à l’utilisateur de créer des lecteurs pour accéder au magasin de données.

- La méthode [System. Management. Automation. Provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) définit la façon dont votre fournisseur prend en charge l’applet de commande du `Remove-PSDrive` fournisseur. Cette applet de commande permet à l’utilisateur de supprimer des lecteurs de la Banque de données.

## <a name="item-enabled-providers"></a>Fournisseurs compatibles avec les éléments

Les fournisseurs compatibles avec les éléments permettent à l’utilisateur d’acquérir, de définir ou d’effacer les éléments dans le magasin de données. Un « élément » est un élément du magasin de données auquel l’utilisateur peut accéder ou gérer de manière indépendante. Pour créer un fournisseur compatible avec les éléments, votre classe de fournisseur doit dériver de la classe [System. Management. Automation. Provider. ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) ou d’une autre classe qui dérive de cette classe.

La classe **System. Management. Automation. Provider. ItemCmdletProvider** définit les méthodes suivantes pour l’implémentation d’applets de commande de fournisseur spécifiques. Dans la plupart des cas, pour prendre en charge une applet de commande de fournisseur, vous devez remplacer la méthode appelée par le moteur PowerShell pour appeler l’applet de commande, telle que la `ClearItem` méthode pour l' `Clear-Item` applet de commande, et vous pouvez éventuellement remplacer une deuxième méthode, telle que `ClearItemDynamicParameters` , pour ajouter des paramètres dynamiques à l’applet de commande.

- Les méthodes [System. Management. Automation. Provider. ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) et [System. Management. Automation. Provider. ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Clear-Item` fournisseur. Cette applet de commande permet à l’utilisateur de supprimer la valeur d’un élément dans le magasin de données.

- Les méthodes [System. Management. Automation. Provider. ItemCmdletProvider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System. Management. Automation. Provider. ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Get-Item` fournisseur. Cette applet de commande permet à l’utilisateur de récupérer des données à partir du magasin de données.

- Les méthodes [System. Management. Automation. Provider. ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) et [System. Management. Automation. Provider. ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Set-Item` fournisseur. Cette applet de commande permet à l’utilisateur de mettre à jour les valeurs des éléments dans le magasin de données.

- Les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) et [System. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Invoke-Item` fournisseur. Cette applet de commande permet à l’utilisateur d’exécuter l’action par défaut spécifiée par l’élément.

- Les méthodes [System. Management. Automation. Provider. ItemCmdletProvider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) et [System. Management. Automation. Provider. ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Test-Path` fournisseur. Cette applet de commande permet à l’utilisateur de déterminer si tous les éléments d’un chemin d’accès existent.

Outre les méthodes utilisées pour implémenter les applets de commande du fournisseur, la classe **System. Management. Automation. Provider. ItemCmdletProvider** définit également les méthodes suivantes :

- La méthode [System. Management. Automation. Provider. ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) permet à l’utilisateur d’utiliser des caractères génériques lors de la spécification du chemin d’accès du fournisseur.

- [System. Management. Automation. Provider. ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) est utilisé pour déterminer si un chemin d’accès est syntaxiquement et sémantiquement valide pour le fournisseur.

## <a name="container-enabled-providers"></a>Fournisseurs compatibles avec les conteneurs

Les fournisseurs compatibles avec les conteneurs permettent à l’utilisateur de gérer les éléments qui sont des conteneurs. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. Pour créer un fournisseur compatible avec les conteneurs, votre classe de fournisseur doit dériver de la classe [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) ou d’une autre classe qui dérive de cette classe.

> [!IMPORTANT]
> Les fournisseurs compatibles avec les conteneurs ne peuvent pas accéder aux magasins de données qui contiennent des conteneurs imbriqués. Si un élément enfant d’un conteneur est un autre conteneur, vous devez implémenter un fournisseur qui prend en charge la navigation.

La classe **System. Management. Automation. Provider. ContainerCmdletProvider** définit les méthodes suivantes pour l’implémentation d’applets de commande de fournisseur spécifiques. Dans la plupart des cas, pour prendre en charge une applet de commande de fournisseur, vous devez remplacer la méthode appelée par le moteur PowerShell pour appeler l’applet de commande, telle que la `CopyItem` méthode pour l' `Copy-Item` applet de commande, et vous pouvez éventuellement remplacer une deuxième méthode, telle que `CopyItemDynamicParameters` , pour ajouter des paramètres dynamiques à l’applet de commande.

- Les méthodes [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) et [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Copy-Item` fournisseur. Cette applet de commande permet à l’utilisateur de copier un élément d’un emplacement vers un autre.

- Les méthodes [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) et [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Get-ChildItem` fournisseur. Cette applet de commande permet à l’utilisateur de récupérer les éléments enfants de l’élément parent.

- Les méthodes [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) et [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande `Get-ChildItem` Provider si son `Name` paramètre est spécifié.

- Les méthodes [System. Management. Automation. Provider. ContainerCmdletProvider. newItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) et [System. Management. Automation. Provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `New-Item` fournisseur. Cette applet de commande permet à l’utilisateur de créer des éléments dans le magasin de données.

- Les méthodes [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) et [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Remove-Item` fournisseur. Cette applet de commande permet à l’utilisateur de supprimer des éléments du magasin de données.

- Les méthodes [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) et [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Rename-Item` fournisseur. Cette applet de commande permet à l’utilisateur de renommer des éléments dans le magasin de données.

Outre les méthodes utilisées pour implémenter les applets de commande du fournisseur, la classe **System. Management. Automation. Provider. ContainerCmdletProvider** définit également les méthodes suivantes :

- La méthode [System. Management. Automation. Provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) peut être utilisée par la classe de fournisseur pour déterminer si un élément a des éléments enfants.

- La méthode [System. Management. Automation. Provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) peut être utilisée par la classe de fournisseur pour créer un chemin d’accès spécifique au fournisseur à partir d’un chemin d’accès spécifié.

## <a name="navigation-enabled-providers"></a>Fournisseurs compatibles avec la navigation

Les fournisseurs activés pour la navigation permettent à l’utilisateur de déplacer des éléments dans le magasin de données. Pour créer un fournisseur compatible avec la navigation, votre classe de fournisseur doit dériver de la classe [System. Management. Automation. Provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

La classe **System. Management. Automation. Provider. NavigationCmdletProvider** définit les méthodes suivantes pour l’implémentation d’applets de commande de fournisseur spécifiques. Dans la plupart des cas, pour prendre en charge une applet de commande de fournisseur, vous devez remplacer la méthode appelée par le moteur PowerShell pour appeler l’applet de commande, telle que la `MoveItem` méthode pour l' `Move-Item` applet de commande, et vous pouvez éventuellement remplacer une deuxième méthode, telle que `MoveItemDynamicParameters` , pour ajouter des paramètres dynamiques à l’applet de commande.

- Les méthodes [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) et [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Move-Item` fournisseur. Cette applet de commande permet à l’utilisateur de déplacer un élément d’un emplacement dans le magasin vers un autre emplacement.

- La méthode [System. Management. Automation. Provider. NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) définit la façon dont votre fournisseur prend en charge l’applet de commande du `Join-Path` fournisseur. Cette applet de commande permet à l’utilisateur de combiner un segment de chemin d’accès parent et enfant pour créer un chemin d’accès interne au fournisseur.

Outre les méthodes utilisées pour implémenter les applets de commande du fournisseur, la classe **System. Management. Automation. Provider. NavigationCmdletProvider** définit également les méthodes suivantes :

- La méthode [System. Management. Automation. Provider. NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) extrait le nom du nœud enfant d’un chemin d’accès.

- La méthode [System. Management. Automation. Provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) extrait la partie parente d’un chemin d’accès.

- La méthode [System. Management. Automation. Provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) détermine si l’élément est un élément de conteneur. Dans ce contexte, un conteneur est un groupe d’éléments enfants sous un élément parent commun.

- La méthode [System. Management. Automation. Provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) retourne un chemin d’accès à un élément relatif à un chemin d’accès de base spécifié.

## <a name="content-enabled-providers"></a>Fournisseurs de contenu

Les fournisseurs de contenu permettent à l’utilisateur d’effacer, d’obtenir ou de définir le contenu des éléments d’un magasin de données.
Par exemple, le fournisseur FileSystem vous permet d’effacer, d’obtenir et de définir le contenu des fichiers dans le système de fichiers. Pour créer un fournisseur de contenu activé, votre classe de fournisseur doit implémenter les méthodes de l’interface [System. Management. Automation. Provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

L’interface **System. Management. Automation. Provider. IContentCmdletProvider** définit les méthodes suivantes pour l’implémentation d’applets de commande de fournisseur spécifiques. Dans la plupart des cas, pour prendre en charge une applet de commande de fournisseur, vous devez remplacer la méthode appelée par le moteur PowerShell pour appeler l’applet de commande, telle que la `ClearContent` méthode pour l' `Clear-Content` applet de commande, et vous pouvez éventuellement remplacer une deuxième méthode, telle que `ClearContentDynamicParameters` , pour ajouter des paramètres dynamiques à l’applet de commande.

- Les méthodes [System. Management. Automation. Provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) et [System. Management. Automation. Provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Clear-Content` fournisseur. Cette applet de commande permet à l’utilisateur de supprimer le contenu d’un élément sans supprimer l’élément.

- Les méthodes [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) et [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Get-Content` fournisseur. Cette applet de commande permet à l’utilisateur de récupérer le contenu d’un élément. La `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` méthode retourne une interface [System. Management. Automation. Provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) qui définit les méthodes utilisées pour lire le contenu.

- Les méthodes [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) et [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Set-Content` fournisseur. Cette applet de commande permet à l’utilisateur de mettre à jour le contenu d’un élément. La `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter` méthode retourne une interface [System. Management. Automation. Provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) qui définit les méthodes utilisées pour écrire le contenu.

## <a name="property-enabled-providers"></a>Fournisseurs activés pour les propriétés

Les fournisseurs activés pour les propriétés permettent à l’utilisateur de gérer les propriétés des éléments dans le magasin de données.
Pour créer un fournisseur prenant en charge les propriétés, votre classe de fournisseur doit implémenter les méthodes des interfaces [System. Management. Automation. Provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) et [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) . Dans la plupart des cas, pour prendre en charge une applet de commande de fournisseur, vous devez remplacer la méthode appelée par le moteur PowerShell pour appeler l’applet de commande, telle que la `ClearProperty` méthode pour l’applet de commande Clear-Property et, éventuellement, vous pouvez remplacer une deuxième méthode, telle que `ClearPropertyDynamicParameters` , pour ajouter des paramètres dynamiques à l’applet de commande.

L’interface **System. Management. Automation. Provider. IPropertyCmdletProvider** définit les méthodes suivantes pour l’implémentation d’applets de commande de fournisseur spécifiques :

- Les méthodes [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) et [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Clear-ItemProperty` fournisseur. Cette applet de commande permet à l’utilisateur de supprimer la valeur d’une propriété.

- Les méthodes [System. Management. Automation. Provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) et [System. Management. Automation. Provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Get-ItemProperty` fournisseur. Cette applet de commande permet à l’utilisateur de récupérer la propriété d’un élément.

- Les méthodes [System. Management. Automation. Provider. IPropertyCmdletProvider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) et [System. Management. Automation. Provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Set-ItemProperty` fournisseur. Cette applet de commande permet à l’utilisateur de mettre à jour les propriétés d’un élément.

  L’interface **System. Management. Automation. Provider. IDynamicPropertyCmdletProvider** définit les méthodes suivantes pour l’implémentation d’applets de commande de fournisseur spécifiques :

- Les méthodes [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) et [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Copy-ItemProperty` fournisseur. Cette applet de commande permet à l’utilisateur de copier une propriété et sa valeur d’un emplacement vers un autre.

- Les méthodes [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) et [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `Move-ItemProperty` fournisseur. Cette applet de commande permet à l’utilisateur de déplacer une propriété et sa valeur d’un emplacement à un autre.

- Les méthodes [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) et [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande du `New-ItemProperty` fournisseur. Cette applet de commande permet à l’utilisateur de créer une nouvelle propriété et de définir sa valeur.

- Les méthodes [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) et [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande `Remove-ItemProperty` . Cette applet de commande permet à l’utilisateur de supprimer une propriété et sa valeur.

- Les méthodes [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) et [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) définissent la façon dont votre fournisseur prend en charge l’applet de commande `Rename-ItemProperty` . Cette applet de commande permet à l’utilisateur de modifier le nom d’une propriété.

## <a name="see-also"></a>Voir aussi

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)
