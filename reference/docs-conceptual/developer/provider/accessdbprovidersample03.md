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
ms.openlocfilehash: 87b6b82225354e77e908b4af2bad1039a29b2980
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691985"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Cet exemple montre comment remplacer les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) pour prendre en charge les appels aux `Get-Item` applets de commande et `Set-Item` . La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

## <a name="demonstrates"></a>Illustre le

> [!IMPORTANT]
> Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :
>
> - Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
> - Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).

Cet exemple indique :

- Déclaration de l' `CmdletProvider` attribut.
- Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
- Remplacement de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) pour modifier le comportement de l' `New-PSDrive` applet de commande, ce qui permet à l’utilisateur de créer des lecteurs.
  (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `New-PSDrive` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour prendre en charge la suppression des lecteurs existants.
- Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pour modifier le comportement de l' `Get-Item` applet de commande, ce qui permet à l’utilisateur de récupérer des éléments à partir du magasin de données. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Get-Item` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) pour modifier le comportement de l' `Set-Item` applet de commande, ce qui permet à l’utilisateur de mettre à jour les éléments dans le magasin de données. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Get-Item` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) pour modifier le comportement de l' `Test-Path` applet de commande. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Test-Path` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) pour déterminer si le chemin d’accès fourni est valide.

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour obtenir et définir des éléments dans une base de données Microsoft Access.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-976":::

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur Windows PowerShell](./provider-types.md)
