---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: c0efd10680d3323b6c8d932604176c4425e7266a
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633360"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux `Copy-Item` applets de commande,, `Get-ChildItem` `New-Item` et `Remove-Item` . Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Illustre

> [!IMPORTANT]
> Votre classe de fournisseur sera probablement dérivée de [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Cet exemple indique :

- Déclaration de l' `CmdletProvider` attribut.
- Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .
- Remplacement de la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) pour modifier le comportement de l' `Copy-Item` applet de commande qui permet à l’utilisateur de copier des éléments d’un emplacement à un autre. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Copy-Item` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour modifier le comportement de l’applet de commande « obtenir-ChildItems », qui permet à l’utilisateur de récupérer les éléments enfants de l’élément parent. (Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande ChildItems.)
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) pour modifier le comportement de l’applet de commande « ChildItems » lorsque le `Name` paramètre de l’applet de commande est spécifié.
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) pour modifier le comportement de l' `New-Item` applet de commande, ce qui permet à l’utilisateur d’ajouter des éléments au magasin de données. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `New-Item` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) pour modifier le comportement de l' `Remove-Item` applet de commande. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Remove-Item` applet de commande.)

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour copier, créer et supprimer des éléments, ainsi que les méthodes permettant d’obtenir les éléments enfants d’un élément parent.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur Windows PowerShell](./provider-types.md)
