---
title: Vue d’ensemble du fournisseur Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366288"
---
# <a name="windows-powershell-provider-overview"></a>Vue d’ensemble du fournisseur Windows PowerShell

Un fournisseur Windows PowerShell permet d’exposer n’importe quel magasin de données comme un système de fichiers comme s’il s’agissait d’un lecteur monté. Par exemple, le fournisseur de registre intégré vous permet de parcourir le registre comme s’il s’agissait de l' `c` lecteur de votre ordinateur. Un fournisseur peut également remplacer les applets de commande `Item` (par exemple, `Get-Item`, `Set-Item`, etc.) de manière à ce que les données de votre magasin de données puissent être traitées comme les fichiers et les répertoires lors de la navigation dans un système de fichiers. Pour plus d’informations sur les fournisseurs et les lecteurs, ainsi que sur les fournisseurs intégrés dans Windows PowerShell, consultez [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Fournisseurs et lecteurs

Un fournisseur définit la logique utilisée pour accéder, parcourir et modifier un magasin de données, tandis qu’un lecteur spécifie un point d’entrée spécifique à un magasin de données (ou une partie d’un magasin de données) qui est du type défini par le fournisseur. Par exemple, le fournisseur Registry vous permet d’accéder aux ruches et aux clés d’un registre, et les lecteurs HKLM et HKCU spécifient les ruches correspondantes dans le registre. Les lecteurs HKLM et HKCU utilisent tous les deux le fournisseur Registry.

Lorsque vous écrivez un fournisseur, vous pouvez spécifier les lecteurs de lecteurs par défaut qui sont créés automatiquement lorsque le fournisseur est disponible. Vous définissez également une méthode pour créer de nouveaux lecteurs qui utilisent ce fournisseur.

## <a name="type-of-providers"></a>Type de fournisseurs

Il existe plusieurs types de fournisseurs, chacun d’eux offrant un niveau de fonctionnalité différent. Un fournisseur est implémenté en tant que classe qui dérive de l’un des descendants de la classe [System. Management. Automation. SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** . Pour plus d’informations sur les différents types de fournisseurs, consultez [types](./provider-types.md)de fournisseurs.

## <a name="provider-cmdlets"></a>Applets de commande de fournisseur

Les fournisseurs peuvent implémenter des méthodes qui correspondent aux cmdlets, créant ainsi des comportements personnalisés pour ces applets de commande lorsqu’ils sont utilisés dans un lecteur pour ce fournisseur. Selon le type de fournisseur, différents jeux d’applets de commande sont disponibles. Pour obtenir la liste complète des applets de commande disponibles pour la personnalisation dans les fournisseurs, consultez [applets](./provider-cmdlets.md)de commande du fournisseur.

## <a name="provider-paths"></a>Chemins d’accès des fournisseurs

Les utilisateurs parcourent les lecteurs du fournisseur comme les systèmes de fichiers. Pour cette raison, ils s’attendent à ce que la syntaxe des chemins d’accès corresponde aux chemins d’accès utilisés dans la navigation dans le système de fichiers. Lorsqu’un utilisateur exécute une applet de commande de fournisseur, il spécifie un chemin d’accès à l’élément auquel accéder. Le chemin d’accès spécifié peut être interprété de plusieurs façons. Un fournisseur doit prendre en charge un ou plusieurs des types de chemins d’accès suivants.

### <a name="drive-qualified-paths"></a>Chemins d’accès qualifiés par le lecteur

Un chemin d’accès qualifié sur un lecteur est une combinaison du nom de l’élément, du conteneur et des sous-conteneurs dans lesquels se trouve l’élément, et du lecteur Windows PowerShell par le biais duquel l’élément est accédé. (Les lecteurs sont définis par le fournisseur utilisé pour accéder au magasin de données. Ce chemin d’accès commence par le nom du lecteur suivi d’un signe deux-points ( :). Par exemple : `get-childitem C:`

### <a name="provider-qualified-paths"></a>Chemins d’accès qualifiés par le fournisseur

Pour permettre au moteur Windows PowerShell d’initialiser et d’initialiser votre fournisseur, le fournisseur doit prendre en charge un chemin d’accès qualifié par le fournisseur. Par exemple, l’utilisateur peut initialiser et désinitialiser le fournisseur FileSystem, car il définit le chemin d’accès qualifié du fournisseur suivant : `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Chemins d’accès directs du fournisseur

Pour autoriser l’accès à distance à votre fournisseur Windows PowerShell, il doit prendre en charge un chemin d’accès direct au fournisseur pour passer directement au fournisseur Windows PowerShell pour l’emplacement actuel. Par exemple, le fournisseur Windows PowerShell du Registre peut utiliser `\\server\regkeypath` comme un chemin d’accès direct au fournisseur.

### <a name="provider-internal-paths"></a>Fournisseurs-chemins d’accès internes

Pour permettre à l’applet de commande du fournisseur d’accéder aux données à l’aide d’interfaces de programmation d’applications (API) non-Windows PowerShell, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès interne au fournisseur. Ce chemin d’accès est indiqué après «  :: » dans le chemin d’accès qualifié du fournisseur. Par exemple, le chemin d’accès interne du fournisseur pour le fournisseur de système de fichiers Windows PowerShell est `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Remplacement des paramètres de l’applet de commande

Le comportement de certaines applets de commande spécifiques au fournisseur peut être remplacé par un fournisseur. Pour obtenir la liste des paramètres qui peuvent être substitués et comment les substituer dans votre classe de fournisseur, consultez [paramètres](./provider-cmdlet-parameters.md) de l’applet de commande du fournisseur.

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les fournisseurs peuvent définir des paramètres dynamiques qui sont ajoutés à une applet de commande de fournisseur lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres statiques de l’applet de commande. Pour ce faire, un fournisseur implémente une ou plusieurs méthodes de paramètres dynamiques. Pour obtenir la liste des paramètres d’applet de commande qui peuvent être utilisés pour ajouter un paramètre dynamique, ainsi que les méthodes utilisées pour les implémenter, consultez [paramètres dynamiques des applets](./provider-cmdlet-dynamic-parameters.md)de commande du fournisseur.

## <a name="provider-capabilities"></a>Fonctionnalités du fournisseur

L’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) définit un certain nombre de fonctionnalités que les fournisseurs peuvent prendre en charge. Celles-ci incluent la possibilité d’utiliser des caractères génériques, de filtrer les éléments et de prendre en charge les transactions. Pour spécifier des fonctionnalités pour un fournisseur, ajoutez une liste de valeurs de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) , associée à une opération de `OR` logique, en tant que la propriété [System. Management. Automation. Provider. Cmdletproviderattribute. Providercapabilities *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) (le deuxième paramètre de l’attribut) de l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) pour votre classe de fournisseur. Par exemple, l’attribut suivant spécifie que le fournisseur prend en charge les fonctionnalités de **transactions** [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess** et [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) .

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Aide sur l’applet de commande Provider

Lors de l’écriture d’un fournisseur, vous pouvez implémenter votre propre aide pour les applets de commande de fournisseur que vous prenez en charge. Cela comprend une rubrique d’aide unique pour chaque applet de commande de fournisseur ou plusieurs versions d’une rubrique d’aide dans les cas où l’applet de commande du fournisseur agit différemment en fonction de l’utilisation de paramètres dynamiques. Pour prendre en charge l’aide spécifique à l’applet de commande du fournisseur, votre fournisseur doit implémenter l’interface [System. Management. Automation. Provider. Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) .

Le moteur Windows PowerShell appelle la méthode [System. Management. Automation. Provider. Icmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) pour afficher la rubrique d’aide de vos applets de commande de fournisseur. Le moteur fournit le nom de l’applet de commande que l’utilisateur a spécifiée lors de l’exécution de l’applet de commande `Get-Help` et le chemin d’accès actuel de l’utilisateur. Le chemin d’accès actuel est requis si votre fournisseur implémente des versions différentes de la même applet de commande de fournisseur pour des lecteurs différents. La méthode doit retourner une chaîne qui contient le code XML de l’aide de l’applet de commande.

Le contenu du fichier d’aide est écrit à l’aide de PSMAML XML. Il s’agit du même schéma XML qui est utilisé pour écrire le contenu de l’aide pour les applets de commande autonomes. Ajoutez le contenu de l’aide de votre applet de commande personnalisée au fichier d’aide de votre fournisseur sous l’élément `CmdletHelpPaths`. L’exemple suivant montre l’élément `command` pour une applet de commande de fournisseur unique et indique comment vous spécifiez le nom de l’applet de commande du fournisseur que votre fournisseur. prend en charge

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Voir aussi

[Fonctionnalités du fournisseur Windows PowerShell](./provider-types.md)

[Applets de commande du fournisseur](./provider-cmdlets.md)

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)