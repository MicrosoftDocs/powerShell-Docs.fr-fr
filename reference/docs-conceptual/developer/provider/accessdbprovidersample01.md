---
title: AccessDBProviderSample01 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 50ec218e8d0fe6b2be5c8ac00956f72c6723f84a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786915"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Cet exemple montre comment déclarer une classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Il est indiqué ici uniquement par souci de citer tous les exemples.

## <a name="demonstrates"></a>Illustre le

> [!IMPORTANT]
> Votre classe de fournisseur va probablement dériver de l’une des classes suivantes et éventuellement implémenter d’autres interfaces de fournisseur :
>
> - Classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Consultez [AccessDBProviderSample03](./accessdbprovidersample03.md).
> - Classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Pour plus d’informations sur le choix de la classe de fournisseur à partir de laquelle dériver les fonctionnalités du fournisseur, consultez [conception de votre fournisseur Windows PowerShell](./provider-types.md).

Cet exemple indique :

- Déclaration de l' `CmdletProvider` attribut.

- Définition d’une classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

## <a name="example"></a>Exemple

Cet exemple montre comment définir une classe de fournisseur et comment déclarer l' `CmdletProvider` attribut.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Conception de votre fournisseur Windows PowerShell](./provider-types.md)
