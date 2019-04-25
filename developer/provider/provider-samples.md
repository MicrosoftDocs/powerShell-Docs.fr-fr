---
title: Exemples de fournisseurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080932"
---
# <a name="provider-samples"></a>Exemples de fournisseurs

Cette section inclut des exemples de fournisseurs qui accèdent à une base de données Microsoft Access. Ces exemples incluent des classes de fournisseur qui dérivent toutes les classes de fournisseur de base.

## <a name="in-this-section"></a>Dans cette section

Cette section comprend les rubriques suivantes :

[Exemple de AccessDBProviderSample01](./accessdbprovidersample01.md) cet exemple montre comment déclarer la classe de fournisseur qui dérive directement de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe. Il est indiqué ici uniquement par souci de citer tous les exemples.

[AccessDBProviderSample02](./accessdbprovidersample02.md) cet exemple montre comment remplacer le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthodes pour prendre en charge les appels à la `New-PSDrive` et `Remove-PSDrive` applets de commande. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.

[AccessDBProviderSample03](./accessdbprovidersample03.md) cet exemple montre comment remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthodes pour prendre en charge les appels à la `Get-Item` et `Set-Item` applets de commande. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

[AccessDBProviderSample04](./accessdbprovidersample04.md) cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels à la `Copy-Item`, `Get-ChildItem`, `New-Item`, et `Remove-Item` applets de commande. Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

[AccessDBProviderSample05](./accessdbprovidersample05.md) cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels à la `Move-Item` et `Join-Path` applets de commande. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

[AccessDBProviderSample06](./accessdbprovidersample06.md) cet exemple montre comment remplacer les méthodes de contenu pour prendre en charge les appels à la `Clear-Content`, `Get-Content`, et `Set-Content` applets de commande. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe, qui implémente le [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur PowerShell de Windows](./writing-a-windows-powershell-provider.md)