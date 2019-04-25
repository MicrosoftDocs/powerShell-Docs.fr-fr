---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080983"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Cet exemple montre comment remplacer les méthodes de contenu pour prendre en charge les appels à la `Clear-Content`, `Get-Content`, et `Set-Content` applets de commande. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur dans cet exemple dérive le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe, qui implémente le [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="demonstrates"></a>Montre

> [!IMPORTANT]
> Votre classe de fournisseur sera très probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe. Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.
>
> Pour plus d’informations sur le choix de la classe de fournisseur à dérivent selon les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).

Cet exemple montre les éléments suivants :

- Déclarer la `CmdletProvider` attribut.

- Définition d’une classe de fournisseur qui dérive de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et qui déclare le [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

- En remplaçant le [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode pour modifier le comportement de la `Clear-Content` applet de commande, permettant à l’utilisateur à supprimer le contenu d’un élément. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Clear-Content` applet de commande.)

- En remplaçant le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) méthode pour modifier le comportement de la `Get-Content` applet de commande, permettant à l’utilisateur récupérer le contenu d’un élément. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Get-Content` applet de commande.).

- En remplaçant le [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) méthode pour modifier le comportement de la `Set-Content` applet de commande, permettant à l’utilisateur à mettre à jour le contenu d’un élément. (Cet exemple n’affiche pas comment ajouter des paramètres dynamiques à la `Set-Content` applet de commande.)

## <a name="example"></a>Exemple

Cet exemple montre comment remplacer les méthodes nécessaires pour effacer, obtenir et définir le contenu des éléments de données Microsoft Access base.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur de PowerShell Windows](./provider-types.md)