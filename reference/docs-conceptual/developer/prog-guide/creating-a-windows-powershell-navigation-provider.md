---
title: Création d’un fournisseur de navigation Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: f73e732ca9416b906b3647c5090dfa04ad940484
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416202"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Création d’un fournisseur de navigation Windows PowerShell

Cette rubrique explique comment créer un fournisseur de navigation Windows PowerShell qui peut naviguer dans le magasin de données. Ce type de fournisseur prend en charge les commandes récursives, les conteneurs imbriqués et les chemins d’accès relatifs.

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (AccessDBSampleProvider05.cs) pour ce fournisseur à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

Le fournisseur décrit ici permet à l’utilisateur de gérer une base de données Access en tant que lecteur afin que l’utilisateur puisse accéder aux tables de données de la base de données. Lorsque vous créez votre propre fournisseur de navigation, vous pouvez implémenter des méthodes qui peuvent rendre les chemins d’accès qualifiés pour la navigation, normaliser les chemins d’accès relatifs, déplacer les éléments du magasin de données, ainsi que les méthodes qui obtiennent des noms enfants, obtenir le chemin d’accès parent d’un élément et tester pour déterminer si un élément est un conteneur.

> [!CAUTION]
> N’oubliez pas que cette conception suppose qu’il s’agit d’une base de données qui a un champ avec l’ID de nom et que le type du champ est LongInteger.

## <a name="define-the-windows-powershell-provider"></a>Définir le fournisseur Windows PowerShell

Un fournisseur de navigation Windows PowerShell doit créer une classe .NET qui dérive de la classe de base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Voici la définition de classe pour le fournisseur de navigation décrit dans cette section.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Notez que dans ce fournisseur, l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) comprend deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose au runtime Windows PowerShell pendant le traitement de la commande. Pour ce fournisseur, aucune fonctionnalité spécifique de Windows PowerShell n’est ajoutée.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de base

Comme décrit dans [conception de votre fournisseur PS](./designing-your-windows-powershell-provider.md), la classe de base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) dérive de plusieurs autres classes qui offraient des fonctionnalités de fournisseur différentes. Un fournisseur de navigation Windows PowerShell, par conséquent, doit définir toutes les fonctionnalités fournies par ces classes.

Pour implémenter les fonctionnalités d’ajout d’informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur PS de base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.

Pour obtenir l’accès à la Banque de données via un lecteur Windows PowerShell, vous devez implémenter les méthodes de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Pour manipuler les éléments d’un magasin de données, tels que l’obtention, la définition et l’effacement des éléments, le fournisseur doit implémenter les méthodes fournies par la classe de base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur d’éléments Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Pour accéder aux éléments enfants, ou à leur nom, du magasin de données, ainsi qu’aux méthodes qui créent, copient, renomment et suppriment des éléments, vous devez implémenter les méthodes fournies par la classe de base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Création d’un chemin d’accès Windows PowerShell

Le fournisseur de navigation Windows PowerShell utilise un chemin d’accès Windows PowerShell interne au fournisseur pour parcourir les éléments du magasin de données. Pour créer un chemin d’accès interne au fournisseur, le fournisseur doit implémenter la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) pour prendre en charge les appels à partir de l’applet de commande combine-Path. Cette méthode combine un chemin d’accès parent et enfant dans un chemin d’accès interne au fournisseur, à l’aide d’un séparateur de chemin d’accès spécifique au fournisseur entre les chemins d’accès parent et enfant.

L’implémentation par défaut accepte les chemins d’accès avec « / » ou «\\» comme séparateur de chemin d’accès, normalise le séparateur de chemin d’accès à «\\», combine les parties de tracé parent et enfant avec le séparateur, puis retourne une chaîne qui contient les chemins d’accès combinés.

Ce fournisseur de navigation n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Points à retenir concernant l’implémentation de MakePath

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Votre implémentation de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) ne doit pas valider le chemin d’accès en tant que chemin d’accès qualifié complet légal dans l’espace de noms du fournisseur. N’oubliez pas que chaque paramètre ne peut représenter qu’une partie d’un chemin d’accès et que les parties combinées ne génèrent pas de chemin d’accès qualifié complet. Par exemple, la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) pour le fournisseur FileSystem peut recevoir « Windows\System32 » dans le paramètre `parent` et « ABC. dll » dans le paramètre `child`. La méthode joint ces valeurs avec le séparateur «\\» et retourne « windows\system32\abc.dll », qui n’est pas un chemin d’accès complet au système de fichiers.

  > [!IMPORTANT]
  > Les parties du chemin d’accès fournies dans l’appel à [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) peuvent contenir des caractères non autorisés dans l’espace de noms du fournisseur. Ces caractères sont très probablement utilisés pour l’extension de caractères génériques et l’implémentation de cette méthode ne doit pas les supprimer.

## <a name="retrieving-the-parent-path"></a>Récupération du chemin d’accès parent

Les fournisseurs de navigation Windows PowerShell implémentent la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) pour récupérer la partie parente du chemin d’accès complet ou partiel spécifié du fournisseur. La méthode supprime la partie enfant du chemin d’accès et retourne la partie du chemin d’accès parent. Le paramètre `root` spécifie le chemin d’accès complet à la racine d’un lecteur. Ce paramètre peut avoir la valeur null ou être vide si un lecteur monté n’est pas utilisé pour l’opération de récupération. Si une racine est spécifiée, la méthode doit retourner un chemin d’accès à un conteneur dans la même arborescence que la racine.

L’exemple de fournisseur de navigation ne remplace pas cette méthode, mais utilise l’implémentation par défaut. Il accepte les chemins d’accès qui utilisent à la fois « / » et «\\» comme séparateurs de chemin. En premier lieu, il normalise le chemin d’accès pour avoir uniquement des séparateurs «\\», puis divise le chemin d’accès parent au dernier «\\» et retourne le chemin d’accès parent.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Pour se souvenir de l’implémentation de GetParentPath

Votre implémentation de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) doit fractionner le chemin d’accès lexicalement sur le séparateur de chemin d’accès de l’espace de noms du fournisseur. Par exemple, le fournisseur FileSystem utilise cette méthode pour rechercher le dernier «\\» et retourne tout ce qui se trouve à gauche du séparateur.

## <a name="retrieve-the-child-path-name"></a>Récupérer le nom du chemin d’accès enfant

Votre fournisseur de navigation implémente la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) pour récupérer le nom (élément feuille) de l’enfant de l’élément situé dans le chemin d’accès complet ou partiel spécifique au fournisseur spécifié.

L’exemple de fournisseur de navigation ne remplace pas cette méthode. L’implémentation par défaut est illustrée ci-dessous. Il accepte les chemins d’accès qui utilisent à la fois « / » et «\\» comme séparateurs de chemin. Il normalise d’abord le chemin d’accès pour avoir uniquement des séparateurs «\\», puis divise le chemin d’accès parent au dernier «\\» et retourne le nom de la partie du chemin d’accès enfant.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Points à retenir concernant l’implémentation de GetChildName

Votre implémentation de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) doit fractionner le chemin d’accès lexicalement sur le séparateur de chemin d’accès. Si le chemin d’accès fourni ne contient pas de séparateurs de chemin d’accès, la méthode doit retourner le chemin d’accès non modifié.

> [!IMPORTANT]
> Le chemin d’accès fourni dans l’appel à cette méthode peut contenir des caractères non conformes dans l’espace de noms du fournisseur. Ces caractères sont très probablement utilisés pour l’extension de caractères génériques ou la correspondance d’expression régulière, et l’implémentation de cette méthode ne doit pas les supprimer.

## <a name="determining-if-an-item-is-a-container"></a>Déterminer si un élément est un conteneur

Le fournisseur de navigation peut implémenter la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) pour déterminer si le chemin d’accès spécifié indique un conteneur. Elle retourne true si le chemin d’accès représente un conteneur, et false dans le cas contraire. L’utilisateur a besoin de cette méthode pour pouvoir utiliser l’applet de commande `Test-Path` pour le chemin d’accès fourni.

Le code suivant illustre l’implémentation de [System. Management. Automation. Provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) dans notre exemple de fournisseur de navigation. La méthode vérifie que le chemin d’accès spécifié est correct et, si la table existe, et retourne la valeur true si le chemin d’accès indique un conteneur.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Points à retenir concernant l’implémentation de IsItemContainer

La classe .NET de votre fournisseur de navigation peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ce cas, l’implémentation de [System. Management. Automation. Provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) doit garantir que le chemin d’accès satisfait aux exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, la propriété [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

## <a name="moving-an-item"></a>Déplacement d’un élément

Pour la prise en charge de l’applet de commande `Move-Item`, votre fournisseur de navigation implémente la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Cette méthode déplace l’élément spécifié par le paramètre `path` vers le conteneur à l’emplacement fourni dans le paramètre `destination`.

L’exemple de fournisseur de navigation ne remplace pas la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . L’implémentation par défaut est la suivante.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Points à retenir concernant l’implémentation de MoveItem

La classe .NET de votre fournisseur de navigation peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ce cas, l’implémentation de [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) doit garantir que le chemin d’accès satisfait aux exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, la propriété **CmdletProvider. Exclude** .

Par défaut, les substitutions de cette méthode ne doivent pas déplacer des objets sur des objets existants, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit définie sur `true`. Par exemple, le fournisseur FileSystem ne copie pas c:\temp\abc.txt sur un fichier c:\bar.txt existant, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit définie sur `true`. Si le chemin d’accès spécifié dans le paramètre `destination` existe et qu’il s’agit d’un conteneur, la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) n’est pas obligatoire. Dans ce cas, [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) doit déplacer l’élément indiqué par le paramètre `path` vers le conteneur indiqué par le paramètre `destination` en tant qu’enfant.

Votre implémentation de la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération quand une modification est apportée à l’état du système, par exemple, en supprimant des fichiers. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte des paramètres de ligne de commande ou des variables de préférence pour déterminer ce qui doit être affiché à l’utilisateur.

Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message à l’utilisateur pour permettre aux commentaires de savoir si l’opération doit être poursuivie. Votre fournisseur doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) pour une vérification supplémentaire des modifications système potentiellement dangereuses.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Move-Item

Parfois, l’applet de commande `Move-Item` requiert des paramètres supplémentaires fournis de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de navigation doit implémenter la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) pour obtenir les valeurs de paramètre requises à partir de l’élément au chemin indiqué, et retourner un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Ce fournisseur de navigation n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalisation d’un chemin d’accès relatif

Votre fournisseur de navigation implémente la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) pour normaliser le chemin d’accès complet indiqué dans le paramètre `path` comme relatif au chemin d’accès spécifié par le paramètre `basePath`. La méthode retourne une représentation sous forme de chaîne du chemin d’accès normalisé. Il écrit une erreur si le paramètre `path` spécifie un chemin d’accès inexistant.

L’exemple de fournisseur de navigation ne remplace pas cette méthode. L’implémentation par défaut est la suivante.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Points à retenir concernant l’implémentation de NormalizeRelativePath

Votre implémentation de [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) doit analyser le paramètre `path`, mais il n’est pas nécessaire d’utiliser l’analyse syntaxique purement simple. Vous êtes encouragé à concevoir cette méthode pour utiliser le chemin d’accès pour rechercher les informations de chemin d’accès dans le magasin de données et créer un chemin d’accès qui correspond à la casse et à la syntaxe de chemin d’accès normalisé.

## <a name="code-sample"></a>Exemple de code

Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Un fournisseur peut ajouter des membres à des objets existants ou définir de nouveaux objets. Pour plus d’informations, consultez[extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Génération du fournisseur Windows PowerShell

Pour plus d’informations, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Lorsque votre fournisseur Windows PowerShell a été inscrit auprès de Windows PowerShell, vous pouvez le tester en exécutant les applets de commande prises en charge sur la ligne de commande, y compris les applets de commande rendues disponibles par dérivation. Cet exemple teste l’exemple de fournisseur de navigation.

1. Exécutez votre nouveau shell et utilisez l’applet de commande `Set-Location` pour définir le chemin d’accès pour indiquer la base de données Access.

   ```powershell
   Set-Location mydb:
   ```

2. Exécutez maintenant l’applet de commande `Get-Childitem` pour récupérer une liste des éléments de base de données, qui sont les tables de base de données disponibles. Pour chaque table, cette applet de commande récupère également le nombre de lignes de table.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Utilisez à nouveau l’applet de commande `Set-Location` pour définir l’emplacement de la table de données Employees.

   ```powershell
   Set-Location Employees
   ```

4. Nous allons maintenant utiliser l’applet de commande `Get-Location` pour récupérer le chemin d’accès à la table Employees.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. À présent, utilisez l’applet de commande `Get-Childitem` dirigée vers l’applet de commande `Format-Table`. Cet ensemble d’applets de commande récupère les éléments de la table de données Employees, qui sont les lignes de la table. Ils sont mis en forme comme spécifié par l’applet de commande `Format-Table`.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Vous pouvez maintenant exécuter l’applet de commande `Get-Item` pour récupérer les éléments de la ligne 0 de la table de données Employees.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Utilisez à nouveau l’applet de commande `Get-Item` pour récupérer les données de l’employé pour les éléments de la ligne 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implémenter un fournisseur Windows PowerShell de conteneur](./creating-a-windows-powershell-container-provider.md)

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
