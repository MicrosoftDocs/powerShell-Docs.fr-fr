---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081064"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Cet exemple montre comment remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthodes pour prendre en charge les appels à la `Get-Item` et `Set-Item` applets de commande. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

## <a name="demonstrates"></a>Montre

> [!IMPORTANT]
> Votre classe de fournisseur sera très probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe. Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Pour plus d’informations sur le choix de la classe de fournisseur à dérivent selon les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).

Cet exemple montre les éléments suivants :

- Déclarer la `CmdletProvider` attribut.

- Définition d’une classe de fournisseur qui dérive de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

- En remplaçant le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) méthode pour modifier le comportement de la `New-PSDrive` applet de commande, permettant à l’utilisateur à créer de nouveaux lecteurs. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `New-PSDrive` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthode pour prendre en charge la suppression de lecteurs existants.

- En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode pour modifier le comportement de la `Get-Item` applet de commande, permettant à l’utilisateur récupérer des éléments à partir du magasin de données. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Get-Item` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthode pour modifier le comportement de la `Set-Item` applet de commande, permettant à l’utilisateur à mettre à jour les éléments dans le magasin de données. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Get-Item` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) méthode pour modifier le comportement de la `Test-Path` applet de commande. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Test-Path` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) méthode pour déterminer si le chemin d’accès fourni est valide.

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour obtenir et définir les éléments de données Microsoft Access base.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur de PowerShell Windows](./provider-types.md)