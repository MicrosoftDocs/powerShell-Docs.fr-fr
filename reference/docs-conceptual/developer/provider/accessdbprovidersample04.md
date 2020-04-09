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
ms.openlocfilehash: 0d3133c75d8e608967f15ffb7345fc0f63e1cd5c
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977503"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande `Copy-Item`, `Get-ChildItem`, `New-Item`et `Remove-Item`. Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Illustre le

> [!IMPORTANT]
> Votre classe de fournisseur sera probablement dérivée de [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Cet exemple illustre les fonctions suivantes :

- Déclaration de l’attribut `CmdletProvider`.
- Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .
- Remplacement de la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) pour modifier le comportement de l’applet de commande `Copy-Item` qui permet à l’utilisateur de copier des éléments d’un emplacement à un autre. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `Copy-Item`.)
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour modifier le comportement de l’applet de commande « obtenir-ChildItems », qui permet à l’utilisateur de récupérer les éléments enfants de l’élément parent. (Cet exemple ne montre pas comment ajouter des paramètres dynamiques à l’applet de commande ChildItems.)
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) pour modifier le comportement de l’applet de commande « ChildItems » lorsque le paramètre `Name` de l’applet de commande est spécifié.
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) pour modifier le comportement de l’applet de commande `New-Item`, qui permet à l’utilisateur d’ajouter des éléments au magasin de données. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `New-Item`.)
- Remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) pour modifier le comportement de l’applet de commande `Remove-Item`. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l’applet de commande `Remove-Item`.)

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour copier, créer et supprimer des éléments, ainsi que les méthodes permettant d’obtenir les éléments enfants d’un élément parent.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-1635":::

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur Windows PowerShell](./provider-types.md)
