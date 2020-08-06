---
title: AccessDBProviderSample05 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67a10d9192350b339da1b82d9eb367ee4af6ef86
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786847"
---
# <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux `Move-Item` applets de commande et `Join-Path` . Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

## <a name="demonstrates"></a>Illustre le

> [!IMPORTANT]
> Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :
>
> - Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).
> - Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .
>
> Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).

Cet exemple indique :

- Déclaration de l' `CmdletProvider` attribut.

- Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

- Remplacement de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) pour modifier le comportement de l' `Move-Item` applet de commande, ce qui permet à l’utilisateur de déplacer des éléments d’un emplacement à un autre. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Move-Item` applet de commande.)

- Remplacement de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) pour modifier le comportement de l' `Join-Path` applet de commande.

- Remplacement de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) .

- Remplacement de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) .

- Remplacement de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) .

- Remplacement de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) .

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour déplacer des éléments dans une base de données Microsoft Access.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur Windows PowerShell](./provider-types.md)
