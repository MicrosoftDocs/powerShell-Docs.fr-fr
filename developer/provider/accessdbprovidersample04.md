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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057618"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels à la `Copy-Item`, `Get-ChildItem`, `New-Item`, et `Remove-Item` applets de commande. Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

## <a name="demonstrates"></a>Montre

> [!IMPORTANT]
> Votre classe de fournisseur dérivent très probablement le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Cet exemple montre les éléments suivants :

- Déclarer la `CmdletProvider` attribut.

- Définition d’une classe de fournisseur qui dérive de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

- En remplaçant le [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) méthode pour modifier le comportement de la `Copy-Item` applet de commande qui permet à l’utilisateur copier des éléments d’un emplacement vers un autre. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Copy-Item` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour modifier le comportement de l’applet de commande Get-ChildItems, ce qui permet à l’utilisateur récupérer les éléments enfants de l’élément parent (méthode) . (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à l’applet de commande Get-ChildItems.)

- En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) méthode pour modifier le comportement de l’applet de commande Get-ChildItems lorsque le `Name` de l’applet de commande est précisé.

- En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode pour modifier le comportement de la `New-Item` applet de commande, qui permet à l’utilisateur d’ajouter des éléments au magasin de données. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `New-Item` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) méthode pour modifier le comportement de la `Remove-Item` applet de commande. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Remove-Item` applet de commande.)

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour copier, créer et supprimer des éléments, ainsi que des méthodes pour obtenir des éléments d’un élément parent de l’enfant.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur de PowerShell Windows](./provider-types.md)