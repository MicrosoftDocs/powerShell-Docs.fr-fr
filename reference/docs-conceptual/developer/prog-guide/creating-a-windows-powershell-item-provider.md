---
title: Création d’un fournisseur d’éléments Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: a2d0f2b435b4b56ac491804f3af695641449e17a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360498"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Création d’un fournisseur d’élément Windows PowerShell

Cette rubrique explique comment créer un fournisseur Windows PowerShell qui peut manipuler les données dans un magasin de données. Dans cette rubrique, les éléments de données du magasin sont appelés « éléments » du magasin de données. Par conséquent, un fournisseur qui peut manipuler les données dans le magasin est appelé fournisseur d’éléments Windows PowerShell.

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (AccessDBSampleProvider03.cs) pour ce fournisseur à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples \<PowerShell >** .
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

Le fournisseur d’éléments Windows PowerShell décrit dans cette rubrique obtient les éléments de données d’une base de données Access. Dans ce cas, un « élément » est une table de la base de données Access ou une ligne d’une table.

## <a name="defining-the-windows-powershell-item-provider-class"></a>Définition de la classe de fournisseur d’éléments Windows PowerShell

Un fournisseur d’éléments Windows PowerShell doit définir une classe .NET qui dérive de la classe de base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Voici la définition de classe pour le fournisseur d’éléments décrit dans cette section.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Notez que dans cette définition de classe, l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) comprend deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose au runtime Windows PowerShell pendant le traitement de la commande. Pour ce fournisseur, aucune fonctionnalité spécifique de Windows PowerShell n’est ajoutée.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de base

Comme décrit dans [concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) dérive de plusieurs autres classes qui offraient des fonctionnalités de fournisseur différentes. Un fournisseur d’éléments Windows PowerShell, par conséquent, doit définir toutes les fonctionnalités fournies par ces classes.

Pour plus d’informations sur la façon d’implémenter des fonctionnalités pour ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs, y compris le fournisseur décrit ici, peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.

Pour que le fournisseur d’éléments Windows PowerShell puisse manipuler les éléments du magasin, il doit implémenter les méthodes de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) pour accéder au magasin de données. Pour plus d’informations sur l’implémentation de cette classe, consultez [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Vérification de la validité du chemin d’accès

Lors de la recherche d’un élément de données, le runtime Windows PowerShell fournit un chemin d’accès Windows PowerShell au fournisseur, tel que défini dans la section « concepts PSPath » de fonctionnement de [Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Un fournisseur d’éléments Windows PowerShell doit vérifier la validité syntaxique et sémantique de n’importe quel chemin d’accès qui lui est passé en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) . Cette méthode retourne `true` si le chemin d’accès est valide, et `false` dans le cas contraire. N’oubliez pas que l’implémentation de cette méthode ne doit pas vérifier l’existence de l’élément au niveau du chemin d’accès, mais uniquement que le chemin d’accès est syntaxiquement et sémantiquement correct.

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) pour ce fournisseur. Notez que cette implémentation appelle une méthode d’assistance NormalizePath pour convertir tous les séparateurs du chemin d’accès en un modèle uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Détermination de l’existence d’un élément

Après vérification du chemin d’accès, le runtime Windows PowerShell doit déterminer s’il existe un élément de données dans ce chemin d’accès. Pour prendre en charge ce type de requête, le fournisseur d’éléments Windows PowerShell implémente la méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) . Cette méthode retourne `true` un élément est trouvé au chemin d’accès spécifié et `false` (valeur par défaut) dans le cas contraire.

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) pour ce fournisseur. Notez que cette méthode appelle les méthodes d’assistance PathIsDrive, ChunkPath et GetTable, et utilise un objet DatabaseTableInfo défini par le fournisseur.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Points à retenir concernant l’implémentation de ItemExists

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Lors de la définition de la classe de fournisseur, un fournisseur d’éléments Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- L’implémentation de cette méthode doit gérer toute forme d’accès à l’élément qui peut rendre l’élément visible à l’utilisateur. Par exemple, si un utilisateur dispose d’un accès en écriture à un fichier via le fournisseur FileSystem (fourni par Windows PowerShell), mais pas d’accès en lecture, le fichier existe toujours et [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourne @no__ t-1. Votre implémentation peut nécessiter la vérification d’un élément parent pour voir si l’élément enfant peut être énuméré.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Test-Path

Parfois, l’applet de commande `Test-Path` qui appelle [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) nécessite des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur d’éléments Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Test-Path`.

Ce fournisseur d’éléments Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Récupération d’un élément

Pour récupérer un élément, le fournisseur d’éléments Windows PowerShell doit se substituer à la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pour prendre en charge les appels à partir de l’applet de commande `Get-Item`. Cette méthode écrit l’élément à l’aide de la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pour ce fournisseur. Notez que cette méthode utilise les méthodes d’assistance GetTable et GetRow pour récupérer des éléments qui sont des tables de la base de données Access ou des lignes d’une table de données.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Points à retenir concernant l’implémentation de GetItem

Les conditions suivantes peuvent s’appliquer à une implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Lors de la définition de la classe de fournisseur, un fournisseur d’éléments Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) doit garantir que le chemin d’accès passé à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer les objets qui sont généralement masqués par l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true`. Par exemple, la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pour le fournisseur FileSystem vérifie la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) avant de tenter d’appeler [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) pour les fichiers système ou masqués.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande

Parfois, l’applet de commande `Get-Item` requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur d’éléments Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Get-Item`.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Définition d’un élément

Pour définir un élément, le fournisseur d’éléments Windows PowerShell doit substituer la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) pour prendre en charge les appels à partir de l’applet de commande `Set-Item`. Cette méthode définit la valeur de l’élément au niveau du chemin d’accès spécifié.

Ce fournisseur ne fournit pas de remplacement pour la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) . Toutefois, l’implémentation par défaut de cette méthode est la suivante.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Points à retenir concernant l’implémentation de SetItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Lors de la définition de la classe de fournisseur, un fournisseur d’éléments Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) doit garantir que le chemin d’accès passé à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas définir ou écrire des objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true`. Une erreur doit être envoyée à la méthode [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) si le chemin d’accès représente un élément masqué et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false`.

- Votre implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant de faire toutes les modifications apportées au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération quand une modification est apportée au magasin de données, par exemple en supprimant des fichiers. La méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte de tous les paramètres de ligne de commande ou des variables de préférence dans détermination de ce qui doit être affiché.

  Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) doit appeler [ Méthode System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message à l’utilisateur pour permettre aux commentaires de vérifier si l’opération doit être poursuivie. L’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permet une vérification supplémentaire des modifications système potentiellement dangereuses.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Récupération des paramètres dynamiques pour SetItem

Parfois, l’applet de commande `Set-Item` requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur d’éléments Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Set-Item`.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Effacement d’un élément

Pour effacer un élément, le fournisseur d’éléments Windows PowerShell implémente la méthode [System. Management. Automation. Provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) pour prendre en charge les appels à partir de l’applet de commande `Clear-Item`. Cette méthode efface l’élément de données au niveau du chemin d’accès spécifié.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Points à retenir concernant l’implémentation de ClearItem

Les conditions suivantes peuvent s’appliquer à une implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Lors de la définition de la classe de fournisseur, un fournisseur d’éléments Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) doit garantir que le chemin d’accès passé à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas définir ou écrire des objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true`. Une erreur doit être envoyée à la méthode [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) si le chemin d’accès représente un élément qui est masqué par l’utilisateur et [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est Affectez la valeur `false`.

- Votre implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant de faire toutes les modifications apportées au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération quand une modification est apportée au magasin de données, par exemple en supprimant des fichiers. La méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell et gère les paramètres de ligne de commande ou les variables de préférence dans détermination de ce qui doit être affiché.

  Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, la méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) doit appeler [ Méthode System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message à l’utilisateur pour permettre aux commentaires de vérifier si l’opération doit être poursuivie. L’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permet une vérification supplémentaire des modifications système potentiellement dangereuses.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Récupérer les paramètres dynamiques pour ClearItem

Parfois, l’applet de commande `Clear-Item` requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur d’éléments Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Clear-Item`.

Ce fournisseur d’éléments n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Exécution d’une action par défaut pour un élément

Un fournisseur d’éléments Windows PowerShell peut implémenter la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) pour prendre en charge les appels à partir de l’applet de commande `Invoke-Item`, ce qui permet au fournisseur d’effectuer une action par défaut pour le élément au chemin d’accès spécifié. Par exemple, le fournisseur FileSystem peut utiliser cette méthode pour appeler ShellExecute pour un élément spécifique.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Points à retenir concernant l’implémentation de InvokeDefaultAction

Les conditions suivantes peuvent s’appliquer à une implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Lors de la définition de la classe de fournisseur, un fournisseur d’éléments Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) doit garantir que le chemin d’accès passé à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas définir ou écrire des objets masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true`. Une erreur doit être envoyée à la méthode [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) si le chemin d’accès représente un élément qui est masqué par l’utilisateur et [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est Affectez la valeur `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Récupérer les paramètres dynamiques pour InvokeDefaultAction

Parfois, l’applet de commande `Invoke-Item` requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur d’éléments Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres dynamiques à l’applet de commande `Invoke-Item`.

Ce fournisseur d’éléments n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implémentation de classes et de méthodes d’assistance

Ce fournisseur d’éléments implémente plusieurs méthodes d’assistance et classes qui sont utilisées par les méthodes de substitution publiques définies par Windows PowerShell. Le code de ces méthodes et classes d’assistance est indiqué dans la section [exemple de code](#code-sample) .

### <a name="normalizepath-method"></a>Méthode NormalizePath

Ce fournisseur d’éléments implémente une méthode d’assistance NormalizePath pour garantir que le chemin d’accès a un format cohérent. Le format spécifié utilise une barre oblique inverse (\\) comme séparateur.

### <a name="pathisdrive-method"></a>Méthode PathIsDrive

Ce fournisseur d’éléments implémente une méthode d’assistance PathIsDrive pour déterminer si le chemin d’accès spécifié est effectivement le nom du lecteur.

### <a name="chunkpath-method"></a>Méthode ChunkPath

Ce fournisseur d’éléments implémente une méthode d’assistance ChunkPath qui rompt le chemin d’accès spécifié afin que le fournisseur puisse identifier ses éléments individuels. Elle retourne un tableau composé des éléments Path.

### <a name="gettable-method"></a>Méthode GetTable

Ce fournisseur d’éléments implémente la méthode d’assistance GetTables qui retourne un objet DatabaseTableInfo qui représente des informations sur la table spécifiée dans l’appel.

### <a name="getrow-method"></a>Méthode GetRow

La méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) de ce fournisseur d’éléments appelle la méthode d’assistance GetRows. Cette méthode d’assistance récupère un objet DatabaseRowInfo qui représente des informations sur la ligne spécifiée dans la table.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo, classe

Ce fournisseur d’éléments définit une classe DatabaseTableInfo qui représente une collection d’informations dans une table de données de la base de données. Cette classe est semblable à la classe [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .

L’exemple de fournisseur d’élément définit une méthode DatabaseTableInfo. GetTables qui retourne une collection d’objets d’informations de table définissant les tables dans la base de données. Cette méthode comprend un bloc try/catch pour s’assurer que toutes les erreurs de base de données s’affichent sous la forme d’une ligne sans aucune entrée.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo, classe

Ce fournisseur d’éléments définit la classe d’assistance DatabaseRowInfo qui représente une ligne dans une table de la base de données. Cette classe est semblable à la classe [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) .

L’exemple de fournisseur définit une méthode DatabaseRowInfo. GetRows pour retourner une collection d’objets d’informations de ligne pour la table spécifiée. Cette méthode comprend un bloc try/catch pour intercepter les exceptions. Toute erreur ne se traduira par aucune information de ligne.

## <a name="code-sample"></a>Exemple de code

Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Lors de l’écriture d’un fournisseur, il peut être nécessaire d’ajouter des membres à des objets existants ou de définir de nouveaux objets. Lorsque vous avez terminé, créez un fichier de types que Windows PowerShell peut utiliser pour identifier les membres de l’objet et un fichier de format qui définit le mode d’affichage de l’objet. Pour plus d’informations sur, consultez [extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Génération du fournisseur Windows PowerShell

Découvrez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Lorsque ce fournisseur d’éléments Windows PowerShell est inscrit auprès de Windows PowerShell, vous pouvez tester uniquement les fonctionnalités de base et de lecteur du fournisseur. Pour tester la manipulation d’éléments, vous devez également implémenter la fonctionnalité de conteneur décrite dans [implémentation d’un fournisseur Windows PowerShell de conteneur](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Fonctionnement de Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Création d’un fournisseur Windows PowerShell de conteneur](./creating-a-windows-powershell-container-provider.md)

[Création d’un fournisseur de lecteur Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
