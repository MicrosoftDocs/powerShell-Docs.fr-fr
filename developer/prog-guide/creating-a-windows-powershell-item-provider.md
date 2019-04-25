---
title: Création d’un fournisseur d’éléments de PowerShell Windows | Microsoft Docs
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
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081867"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Création d’un fournisseur d’élément Windows PowerShell

Cette rubrique décrit comment créer un fournisseur Windows PowerShell qui peut manipuler les données dans un magasin de données. Dans cette rubrique, les éléments de données dans le magasin sont désignés pour stocker les « éléments » des données. Par conséquent, un fournisseur qui peut manipuler les données dans le magasin est appelé un fournisseur d’éléments de Windows PowerShell.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider03.cs) pour ce fournisseur en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

Le fournisseur d’éléments de Windows PowerShell décrit dans cette rubrique Obtient les éléments de données à partir d’une base de données Access. Dans ce cas, un « élément » est soit une table dans la base de données Access ou une ligne dans une table.

La liste suivante contient les sections de cette rubrique. Si vous n’êtes pas familiarisé avec l’écriture d’un fournisseur d’éléments de Windows PowerShell, lisez ces sections dans l’ordre où ils apparaissent. Toutefois, si vous êtes familiarisé avec l’écriture d’un fournisseur d’éléments de Windows PowerShell, accédez directement aux informations dont vous avez besoin :

- [Définition de la classe de fournisseur Windows PowerShell élément](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Définition des fonctionnalités de Base](#Defining-Base-Functionality)

- [Vérification de la validité du chemin d’accès](#Checking-for-Path-Validity)

- [Déterminer si un élément existe](#Determining-if-an-Item-Exists)

- [Attachement des paramètres dynamiques à la `Test-Path` applet de commande](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Extraction d’un élément](#Retrieving-an-Item)

- [Attachement des paramètres dynamiques à la `Get-Item` applet de commande](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Spécification d’un élément](#Setting-an-Item)

- [Attachement des paramètres dynamiques à la `Set-Item` applet de commande](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Efface un élément](#Clearing-an-Item)

- [Attachement des paramètres dynamiques à l’applet de commande Clear-Item](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Exécution d’une Action par défaut pour un élément](#Performing-a-Default-Action-for-an-Item)

- [Récupération des paramètres dynamiques pour InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implémentation des Classes et méthodes d’assistance](#Implementing-Helper-Methods-and-Classes)

- [Exemple de code](#Code-Sample)

- [Définition des Types d’objets et mise en forme](#Defining-Object-Types-and-Formatting)

- [Construction du fournisseur PowerShell de Windows](#Building-the-Windows-PowerShell-provider)

- [Test du fournisseur PowerShell de Windows](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Définition de la classe de fournisseur Windows PowerShell élément

Un fournisseur d’éléments de Windows PowerShell doive définir une classe .NET qui dérive de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe de base. Voici la définition de classe pour le fournisseur d’éléments décrit dans cette section.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Notez que, dans cette définition, de la classe la [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut inclut deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande. Pour ce fournisseur, il n’existe aucun ajout capacités spécifiques de Windows PowerShell.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de Base

Comme décrit dans [fournisseur Design Your Windows PowerShell](./designing-your-windows-powershell-provider.md), le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe est dérivée de plusieurs autres classes fourni différents fonctionnalités du fournisseur. Un fournisseur d’éléments de Windows PowerShell, par conséquent, doive définir toutes les fonctionnalités fournies par les classes.

Pour plus d’informations sur la façon d’implémenter des fonctionnalités permettant d’ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur de PowerShell Windows base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs, y compris le fournisseur décrit ici, peut utiliser l’implémentation par défaut de cette fonctionnalité est fournie par Windows PowerShell.

Avant que le fournisseur d’éléments de Windows PowerShell peut manipuler les éléments dans le magasin, il doit implémenter les méthodes de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base pour accéder au magasin de données. Pour plus d’informations sur l’implémentation de cette classe, consultez [création d’un fournisseur de lecteur Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Vérification de la validité du chemin d’accès

Lorsque vous recherchez un élément de données, le runtime Windows PowerShell fournit un chemin d’accès Windows PowerShell pour le fournisseur, tel que défini dans la section « Concepts PSPath » de [Windows PowerShell fonctionnement](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Un fournisseur d’éléments de Windows PowerShell doit vérifier la validité syntaxique et sémantique de n’importe quel chemin d’accès passé en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) (méthode). Cette méthode retourne `true` si le chemin d’accès est valide, et `false` dans le cas contraire. Être conscient que l’implémentation de cette méthode ne doit pas vérifier l’existence de l’élément dans le chemin d’accès, mais uniquement le chemin d’accès est syntaxiquement et sémantiquement correct.

Voici l’implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) méthode pour ce fournisseur. Notez que cette implémentation appelle une méthode d’assistance de NormalizePath pour convertir tous les séparateurs dans le chemin d’accès vers un uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Déterminer si un élément existe

Après avoir vérifié le chemin d’accès, le runtime Windows PowerShell doit déterminer si un élément de données existe à ce chemin d’accès. Pour prendre en charge ce type de requête, le fournisseur d’éléments de Windows PowerShell implémente le [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) (méthode). Cette méthode retourne `true` un élément est trouvé dans le chemin spécifié et `false` (par défaut) dans le cas contraire.

Voici l’implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) méthode pour ce fournisseur. Notez que cette méthode appelle les méthodes d’assistance PathIsDrive, ChunkPath et GetTable et utilise un fournisseur définis DatabaseTableInfo objet.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Points à retenir sur l’implémentation ItemExists

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Lorsque vous définissez la classe de fournisseur, un fournisseur d’éléments de Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) méthode devez vous assurer que le chemin d’accès transmis à la méthode remplit les conditions de la valeur capabilities spécifiée. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- L’implémentation de cette méthode doit gérer toutes les formes de l’accès à l’élément qui peut rendre l’élément visible par l’utilisateur. Par exemple, si un utilisateur a accès à un fichier via le fournisseur FileSystem (fourni par Windows PowerShell), mais pas l’accès en lecture, le fichier existe toujours et [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourne `true`. Votre implémentation peut nécessiter la vérification d’un élément parent pour voir si l’élément enfant peut être énuméré.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Test-Path

Parfois le `Test-Path` applet de commande qui appelle [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques Windows PowerShell élément fournisseur doit implémenter la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Test-Path` applet de commande.

Ce fournisseur d’élément de Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Extraction d’un élément

Pour récupérer un élément, le fournisseur d’éléments de Windows PowerShell doit remplacer [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode pour prendre en charge les appels à partir de la `Get-Item` applet de commande. Cette méthode écrit l’élément à l’aide du [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (méthode).

Voici l’implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode pour ce fournisseur. Notez que cette méthode utilise les méthodes d’assistance GetTable et GetRow pour récupérer des éléments qui sont des tables dans la base de données Access ou des lignes dans une table de données.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Points à retenir sur l’implémentation GetItem

Les conditions suivantes peuvent s’appliquer à une implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Lorsque vous définissez la classe de fournisseur, un fournisseur d’éléments de Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) devez vous assurer que le chemin d’accès transmis à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer les objets qui sont généralement masquées à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Par exemple, le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode pour les vérifications de fournisseur de système de fichiers le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété avant d’essayer d’appeler [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) cachés ou les fichiers système.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Get-Item

Parfois le `Get-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques Windows PowerShell élément fournisseur doit implémenter la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Get-Item` applet de commande.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Spécification d’un élément

Pour définir un élément, le fournisseur d’éléments de Windows PowerShell doit remplacer le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthode pour prendre en charge les appels à partir de la `Set-Item` applet de commande. Cette méthode définit la valeur de l’élément dans le chemin spécifié.

Ce fournisseur ne fournit pas un remplacement pour le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) (méthode). Toutefois, ce qui suit est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Points à retenir sur l’implémentation SetItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Lorsque vous définissez la classe de fournisseur, un fournisseur d’éléments de Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) devez vous assurer que le chemin d’accès transmis à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas définir ou écrire des objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être envoyée à la [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) méthode si le chemin d’accès représente un élément caché et [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

- Votre implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération lorsqu’une modification est apportée au magasin de données, par exemple, la suppression de fichiers. Le [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) méthode envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell en prenant en compte tous les paramètres de ligne de commande ou variables de préférence pour déterminer ce qui doit être affiché.

  Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message à l’utilisateur pour que les commentaires vérifier si l’opération doit être poursuivie. L’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permet une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Récupération des paramètres dynamiques pour SetItem

Parfois le `Set-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques Windows PowerShell élément fournisseur doit implémenter la [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Set-Item` applet de commande.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Efface un élément

Pour supprimer un élément, le fournisseur d’éléments de Windows PowerShell implémente le [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) méthode pour prendre en charge les appels à partir de la `Clear-Item` applet de commande. Cette méthode efface l’élément de données dans le chemin spécifié.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Points à retenir sur l’implémentation ClearItem

Les conditions suivantes peuvent s’appliquer à une implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Lorsque vous définissez la classe de fournisseur, un fournisseur d’éléments de Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) devez vous assurer que le chemin d’accès transmis à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas définir ou écrire des objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être envoyée à la [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) méthode si le chemin d’accès représente un élément est masqué pour l’utilisateur et [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

- Votre implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération lorsqu’une modification est apportée au magasin de données, par exemple, la suppression de fichiers. Le [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) méthode envoie le nom de la ressource à être modifié à l’utilisateur, avec le runtime de Windows PowerShell et de gérer les paramètres de ligne de commande ou une préférence variables de déterminer ce qui doit être affiché.

  Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message à l’utilisateur pour que les commentaires vérifier si l’opération doit être poursuivie. L’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permet une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Récupérer les paramètres dynamiques pour ClearItem

Parfois le `Clear-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques Windows PowerShell élément fournisseur doit implémenter la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Clear-Item` applet de commande.

Ce fournisseur de l’élément n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Exécution d’une Action par défaut pour un élément

Un fournisseur d’éléments de Windows PowerShell peut implémenter la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) méthode pour prendre en charge les appels à partir de la `Invoke-Item` applet de commande, qui permet au fournisseur à effectuer une action par défaut pour l’élément dans le chemin spécifié. Par exemple, le fournisseur FileSystem peut utiliser cette méthode à appeler ShellExecute pour un élément spécifique.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Points à retenir sur l’implémentation InvokeDefaultAction

Les conditions suivantes peuvent s’appliquer à une implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Lorsque vous définissez la classe de fournisseur, un fournisseur d’éléments de Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) devez vous assurer que le chemin d’accès transmis à la méthode répond à ces exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas définir ou écrire des objets masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être envoyée à la [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) méthode si le chemin d’accès représente un élément est masqué pour l’utilisateur et [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Récupérer les paramètres dynamiques pour InvokeDefaultAction

Parfois le `Invoke-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques Windows PowerShell élément fournisseur doit implémenter la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime de Windows PowerShell utilise l’objet retourné pour ajouter les paramètres dynamiques à la `Invoke-Item` applet de commande.

Ce fournisseur de l’élément n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implémentation des Classes et méthodes d’assistance

Ce fournisseur d’élément implémente plusieurs méthodes d’assistance et les classes qui sont utilisées par le public substituer les méthodes définies par Windows PowerShell. Le code de ces classes et méthodes d’assistance sont affichés dans le [exemple de Code](#Code-Sample) section.

### <a name="normalizepath-method"></a>NormalizePath (méthode)

Ce fournisseur d’élément implémente une méthode d’assistance de NormalizePath pour vérifier que le chemin d’accès a un format cohérent. Le format spécifié utilise une barre oblique inverse (\\) comme séparateur.

### <a name="pathisdrive-method"></a>PathIsDrive (méthode)

Ce fournisseur d’élément implémente une méthode d’assistance de PathIsDrive pour déterminer si le chemin d’accès spécifié est en fait le nom du lecteur.

### <a name="chunkpath-method"></a>ChunkPath (méthode)

Ce fournisseur d’élément implémente une méthode d’assistance ChunkPath qui répartit le chemin d’accès spécifié afin que le fournisseur puisse identifier ses éléments individuels. Elle retourne qu'un tableau composé des éléments de chemin d’accès.

### <a name="gettable-method"></a>GetTable (méthode)

Ce fournisseur d’élément implémente la méthode d’assistance GetTables qui retourne un objet DatabaseTableInfo qui représente des informations sur la table spécifiée dans l’appel.

### <a name="getrow-method"></a>GetRow, méthode

Le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode de ce fournisseur d’élément appelle la méthode d’assistance de GetRows. Cette méthode d’assistance récupère un objet DatabaseRowInfo qui représente des informations sur la ligne spécifiée dans la table.

### <a name="databasetableinfo-class"></a>Classe de DatabaseTableInfo

Ce fournisseur de l’élément définit une classe DatabaseTableInfo qui représente une collection d’informations dans une table de données dans la base de données. Cette classe est semblable à la [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) classe.

L’exemple de fournisseur d’élément définit une méthode DatabaseTableInfo.GetTables qui retourne une collection d’objets d’informations de table définissant les tables dans la base de données. Cette méthode inclut un bloc try/catch pour vous assurer que toute erreur de base de données s’affiche comme une ligne avec les entrées de zéro.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo Class

Ce fournisseur d’élément définit la classe d’assistance DatabaseRowInfo qui représente une ligne dans une table de la base de données. Cette classe est semblable à la [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) classe.

L’exemple de fournisseur définit une méthode DatabaseRowInfo.GetRows pour retourner une collection d’objets d’informations de ligne pour la table spécifiée. Cette méthode inclut un bloc try/catch pour intercepter les exceptions. Aucune information de ligne entraîne des erreurs.

## <a name="code-sample"></a>Exemple de code

Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Lorsque vous écrivez un fournisseur, il peut être nécessaire d’ajouter des membres à des objets existants ou définir de nouveaux objets. Lorsque vous avez terminé, créez un fichier de Types que Windows PowerShell peut utiliser pour identifier les membres de l’objet et un fichier de Format qui définit comment l’objet est affiché. Pour plus d’informations, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Construction du fournisseur Windows PowerShell

Consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Lorsque ce fournisseur d’élément de Windows PowerShell est enregistré avec Windows PowerShell, vous pouvez uniquement tester le basic et lecteur de fonctionnalité du fournisseur. Pour tester la manipulation d’éléments, vous devez également implémenter des fonctionnalités de conteneur décrites dans [implémentation d’un fournisseur de PowerShell de conteneur Windows](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Conception du fournisseur de votre Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Fonctionnement de Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Création d’un fournisseur de lecteur de PowerShell de Windows](./creating-a-windows-powershell-drive-provider.md)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)