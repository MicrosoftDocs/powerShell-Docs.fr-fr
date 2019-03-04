---
title: Vue d’ensemble de Windows PowerShell fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 31ee7222c35e82ee58d6d56f710792dbc5cb24d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858625"
---
# <a name="windows-powershell-provider-overview"></a>Vue d’ensemble du fournisseur Windows PowerShell

Un fournisseur Windows PowerShell permet de n’importe quel magasin de données d’être exposée comme un système de fichiers comme s’il s’agissait d’un lecteur monté. Par exemple, le fournisseur de Registre intégré vous permet de naviguer le Registre comme vous rechercheriez le `c` lecteur de votre ordinateur. Un fournisseur peut également remplacer le `Item` applets de commande (par exemple, `Get-Item`, `Set-Item`, etc.) telles que les données dans votre magasin de données peuvent être traitées comme des fichiers et répertoires sont traités lors de la navigation d’un système de fichiers. Pour plus d’informations sur les fournisseurs et les lecteurs et les fournisseurs intégrés dans Windows PowerShell, consultez [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).
Un fournisseur Windows PowerShell permet de n’importe quel magasin de données d’être exposée comme un système de fichiers comme s’il s’agissait d’un lecteur monté. Par exemple, le fournisseur de Registre intégré vous permet de naviguer le Registre comme vous rechercheriez le `c` lecteur de votre ordinateur. Un fournisseur peut également remplacer le `Item` applets de commande (par exemple, `Get-Item`, `Set-Item`, etc.) telles que les données dans votre magasin de données peuvent être traitées comme des fichiers et répertoires sont traités lors de la navigation d’un système de fichiers. Pour plus d’informations sur les fournisseurs et les lecteurs et les fournisseurs intégrés dans Windows PowerShell, consultez [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Fournisseurs et lecteurs

Un fournisseur définit la logique qui est utilisée pour accéder, parcourir et modifier un magasin de données, tandis qu’un lecteur Spécifie un point d’entrée spécifique à un magasin de données (ou une partie d’un magasin de données) qui est du type défini par le fournisseur. Par exemple, le fournisseur de Registre vous permet d’accéder aux ruches et clés dans un Registre, et les lecteurs HKLM et HKCU spécifient les ruches correspondantes dans le Registre. Les lecteurs HKLM et HKCU utilisent le fournisseur de Registre.

Lorsque vous écrivez un fournisseur, vous pouvez spécifier par défaut lecteurs de disques qui sont créées automatiquement lorsque le fournisseur est disponible. Vous définissez également une méthode pour créer de nouveaux lecteurs qui utilisent ce fournisseur.

## <a name="type-of-providers"></a>Type de fournisseurs

Il existe plusieurs types de fournisseurs, chacun d’eux fournit un autre niveau de fonctionnalité. Un fournisseur est implémenté en tant que classe qui dérive d’un des descendants de le [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) classe. Pour plus d’informations sur les différents types de fournisseurs, consultez [les types de fournisseur](./provider-types.md).

## <a name="provider-cmdlets"></a>Applets de commande de fournisseur

Fournisseurs peuvent implémenter des méthodes qui correspondent aux applets de commande, création de comportements personnalisés pour ces applets de commande lorsqu’il est utilisé dans un lecteur de ce fournisseur. Selon le type de fournisseur, différents ensembles d’applets de commande sont disponibles. Pour obtenir une liste complète des applets de commande disponibles pour la personnalisation dans les fournisseurs, consultez [applets de commande fournisseur](./provider-cmdlets.md).

## <a name="provider-paths"></a>Chemins d’accès de fournisseur

Les utilisateurs accèdent à des lecteurs de fournisseur tels que les systèmes de fichiers. Pour cette raison, ils s’attendent à la syntaxe des chemins d’accès pour qu’elles correspondent aux chemins utilisés dans la navigation dans le fichier système. Lorsqu’un utilisateur exécute une applet de commande du fournisseur, ils spécifient un chemin d’accès à l’élément accessible. Le chemin d’accès spécifié peut être interprétée de plusieurs façons. Un fournisseur doit prendre en charge un ou plusieurs des types suivants de chemin d’accès.

### <a name="drive-qualified-paths"></a>Chemins d’accès de lecteur qualifié

Un chemin d’accès complet incluant le lecteur est une combinaison de nom de l’élément, le conteneur et sous-conteneurs dans lequel se trouve l’élément et le lecteur Windows PowerShell par le biais duquel l’élément est visité. (Les lecteurs sont définies par le fournisseur qui est utilisé pour accéder au magasin de données. Ce chemin d’accès commence par le nom du lecteur suivi du signe deux-points ( :)). Par exemple : `get-childitem C:`

### <a name="provider-qualified-paths"></a>Qualifié par un fournisseur de chemins d’accès

Pour permettre au moteur de Windows PowerShell initialiser et annuler l’initialisation de votre fournisseur, le fournisseur doit prendre en charge un chemin d’accès qualifié par un fournisseur. Par exemple, l’utilisateur peut initialiser et annuler l’initialisation du fournisseur de système de fichiers, car il définit le chemin d’accès qualifié par un fournisseur suivant : `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Chemins d’accès direct de fournisseur

Pour autoriser l’accès à distance à votre fournisseur Windows PowerShell, il doit prendre en charge un chemin d’accès de fournisseur directs pour passer directement au fournisseur Windows PowerShell pour l’emplacement actuel. Par exemple, le fournisseur de Windows PowerShell de Registre peut utiliser `\\server\regkeypath` comme un chemin d’accès directs du fournisseur.

### <a name="provider-internal-paths"></a>Chemins d’accès de fournisseur-interne

Pour permettre à l’applet de commande du fournisseur accéder aux données à l’aide des interfaces de programmation d’applications (API) non - Windows PowerShell, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès interne au fournisseur. Ce chemin d’accès est indiqué après le « :: » dans le chemin d’accès qualifié par un fournisseur. Par exemple, le chemin d’accès interne de fournisseur pour le fournisseur Windows PowerShell de système de fichiers est `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Substitution de paramètres de l’applet de commande

Le comportement de certaines applets de commande spécifique au fournisseur peut être remplacé par un fournisseur. Pour une liste de paramètres qui peuvent être substituées et comment les remplacer dans votre classe de fournisseur, consultez [paramètres d’applet de commande de fournisseur](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Fournisseurs peuvent définir des paramètres dynamiques qui sont ajoutés à une applet de commande fournisseur lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres statiques de l’applet de commande. Un fournisseur met en œuvre une ou plusieurs méthodes de paramètre dynamique. Pour obtenir la liste des paramètres d’applet de commande qui peut être utilisé pour ajouter le paramètre dynamique et les méthodes utilisées pour leur implémentation, consultez [paramètres dynamiques du fournisseur d’applet de commande](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Capacités du fournisseur

Le [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération définit un certain nombre de fonctionnalités prenant en charge les fournisseurs. Ceux-ci incluent la possibilité d’utiliser les caractères génériques, filtrer les éléments et les transactions de la prise en charge. Pour spécifier les fonctionnalités pour un fournisseur, ajoutez une liste de valeurs de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération, combinée avec un opérateur logique `OR` opération, comme le [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) propriété (le deuxième paramètre de l’attribut) de la [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut pour votre classe de fournisseur. Par exemple, l’attribut suivant spécifie que le fournisseur prend en charge la [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) et [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) fonctionnalités.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Aide d’applet de commande de fournisseur

Lorsque vous écrivez un fournisseur, vous pouvez implémenter votre propre aide pour les applets de commande fournisseur que vous prenez en charge. Cela inclut une rubrique d’aide pour chaque applet de commande du fournisseur ou de plusieurs versions d’une rubrique d’aide pour les cas où l’applet de commande fournisseur agit différemment selon l’utilisation de paramètres dynamiques. Pour prendre en charge d’aide spécifique à l’applet de commande du fournisseur, votre fournisseur doit implémenter la [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interface.

Le moteur Windows PowerShell appelle le [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) méthode pour afficher la rubrique d’aide pour vos applets de commande fournisseur. Le moteur fournit le nom de l’applet de commande que l’utilisateur spécifié lors de l’exécution le `Get-Help` applet de commande et le chemin d’accès actuel de l’utilisateur. Le chemin d’accès actuel est requis si votre fournisseur implémente différentes versions de l’applet de commande fournisseur même pour des lecteurs différents. La méthode doit retourner une chaîne qui contient le code XML pour l’aide de l’applet de commande.

Le contenu du fichier d’aide est écrit à l’aide de PSMAML XML. Il s’agit du schéma XML qui est utilisé pour écrire le contenu d’aide pour les applets de commande autonomes. Ajoutez le contenu pour votre aide pour le fichier d’aide pour votre fournisseur de l’applet de commande personnalisée sous la `CmdletHelpPaths` élément. L’exemple suivant montre le `command` élément pour une applet de commande fournisseur unique et il montre la façon dont vous spécifiez le nom de l’applet de commande fournisseur que votre fournisseur. Prend en charge

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

[Fonctionnalités du fournisseur PowerShell Windows](./provider-types.md)

[Applets de commande fournisseur](./provider-cmdlets.md)

[Écriture d’un fournisseur PowerShell de Windows](./writing-a-windows-powershell-provider.md)