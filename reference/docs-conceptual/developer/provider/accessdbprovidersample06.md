---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample06
description: AccessDBProviderSample06
ms.openlocfilehash: a2037c6f13ba24ba2dcb4ffecbd802566452d64e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656926"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Cet exemple montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux `Clear-Content` applets de commande, `Get-Content` et `Set-Content` . Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et implémente l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

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
- Définition d’une classe de fournisseur qui dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et qui déclare l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .
- Remplacement de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) pour modifier le comportement de l' `Clear-Content` applet de commande, ce qui permet à l’utilisateur de supprimer le contenu d’un élément. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Clear-Content` applet de commande.)
- Remplacement de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) pour modifier le comportement de l' `Get-Content` applet de commande, ce qui permet à l’utilisateur de récupérer le contenu d’un élément. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Get-Content` applet de commande.).
- Remplacement de la méthode [Microsoft. PowerShell. Commands. FileSystemProvider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) pour modifier le comportement de l’applet de commande `Set-Content` , ce qui permet à l’utilisateur de mettre à jour le contenu d’un élément. (Cet exemple n’indique pas comment ajouter des paramètres dynamiques à l' `Set-Content` applet de commande.)

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour effacer, obtenir et définir le contenu des éléments dans une base de données Microsoft Access.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur Windows PowerShell](./provider-types.md)
