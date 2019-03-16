---
title: Création d’un fournisseur de conteneur Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 33effed9a96cf1b9ee5f1a50b60a1937526db9d1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055017"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Création d’un fournisseur de conteneur Windows PowerShell

Cette rubrique décrit comment créer un fournisseur Windows PowerShell qui peut fonctionner sur les magasins de données de plusieurs couches. Pour ce type de magasin de données, le niveau supérieur de la banque contient les éléments racine et chaque niveau suivant est appelé un nœud d’éléments enfants. En autorisant l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir de façon hiérarchique via le magasin de données.

Les fournisseurs peuvent travailler sur des magasins de données à plusieurs niveaux sont appelés fournisseurs de conteneur Windows PowerShell. Toutefois, n’oubliez pas qu’un fournisseur de conteneur de Windows PowerShell peut être utilisé uniquement s’il existe un conteneur (aucun conteneurs imbriqués) avec les éléments qu’il contient. S’il existe des conteneurs imbriqués, vous devez implémenter un fournisseur de navigation de Windows PowerShell. Pour plus d’informations sur l’implémentation de fournisseur de navigation de Windows PowerShell, consultez [création d’un fournisseur de Navigation de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider04.cs) pour ce fournisseur en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

Le fournisseur de conteneur Windows PowerShell décrit ici définit la base de données en tant que son conteneur unique, avec les tables et les lignes de la base de données définies en tant qu’éléments du conteneur.

> [!CAUTION]
> N’oubliez pas que cette conception suppose une base de données qui a un champ avec l’ID de nom, et que le type du champ est LongInteger.

Voici une liste des sections dans cette rubrique. Si vous n’êtes pas familiarisé avec l’écriture d’un fournisseur de conteneur Windows PowerShell, veuillez lire ces informations dans l’ordre dans lequel elle apparaît. Toutefois, si vous êtes familiarisé avec l’écriture d’un fournisseur de conteneur Windows PowerShell, accédez directement aux informations dont vous avez besoin.

- [Définition d’une classe de fournisseur de conteneur Windows PowerShell](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Définition des fonctionnalités de Base](#defining-base-functionality)

- [Récupération des éléments enfants](#Retrieving-Child-Items)

- [Attachement des paramètres dynamiques à la `Get-ChildItem` applet de commande](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Récupération des noms d’élément enfant](#Retrieving-Child-Item-Names)

- [Attachement des paramètres dynamiques à la `Get-ChildItem` (nom) de l’applet de commande](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Renommer des éléments](#Renaming-Items)

- [Attachement des paramètres dynamiques à la `Rename-Item` applet de commande](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Création d’éléments](#Creating-New-Items)

- [Attachement des paramètres dynamiques à la `New-Item` applet de commande](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Suppression de des éléments](#Removing-Items)

- [Attachement des paramètres dynamiques à la `Remove-Item` applet de commande](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Interrogation des éléments enfants](#Querying-for-Child-Items)

- [Copie les éléments](#Copying-Items)

- [Attachement des paramètres dynamiques à la `Copy-Item` applet de commande](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Exemple de code](#Code-Sample)

- [Construction du fournisseur PowerShell de Windows](#Building-the-Windows-PowerShell-Provider)

- [Test du fournisseur PowerShell de Windows](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Définition d’une classe de fournisseur de conteneur Windows PowerShell

Un fournisseur de conteneur Windows PowerShell doive définir une classe .NET qui dérive de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe de base. Voici la définition de classe pour le fournisseur de conteneur Windows PowerShell décrite dans cette section.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Notez que, dans cette définition, de la classe la [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut inclut deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande. Pour ce fournisseur, il n’existe aucun capacités spécifiques de Windows PowerShell qui sont ajoutées.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de Base

Comme décrit dans [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md), le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe est dérivée de plusieurs autres classes fourni fonctionnalités de l’autre fournisseur. Il doit par conséquent, un fournisseur de conteneur Windows PowerShell définir toutes les fonctionnalités fournies par les classes.

Pour implémenter des fonctionnalités permettant d’ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur de PowerShell Windows base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité est fournie par Windows PowerShell.

Pour accéder au magasin de données, le fournisseur doit implémenter les méthodes de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de lecteur Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Pour manipuler les éléments d’un magasin de données, telles que l’obtention de paramètre et effacement des éléments, le fournisseur doit implémenter les méthodes fournies par le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur d’éléments de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Récupération des éléments enfants

Pour récupérer un élément enfant, le fournisseur de conteneur Windows PowerShell doit remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode pour prendre en charge les appels à partir de la `Get-ChildItem` applet de commande. Cette méthode récupère des éléments enfants à partir du magasin de données et les écrit dans le pipeline en tant qu’objets. Si le `recurse` paramètre de l’applet de commande est spécifié, la méthode récupère tous les enfants indépendamment de quel niveau ils courent. Si le `recurse` paramètre n’est pas spécifié, la méthode récupère un seul niveau d’enfants.

Voici l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode pour ce fournisseur. Notez que cette méthode récupère les éléments enfants dans toutes les tables de base de données lorsque le chemin d’accès indique la base de données Access et récupère les éléments enfants à partir des lignes de la table si le chemin d’accès indique une table de données.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Points à retenir sur l’implémentation GetChildItems

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de conteneur Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- L’implémentation de cette méthode doit prendre en compte toutes les formes de l’accès à l’élément qui peut rendre l’élément visible par l’utilisateur. Par exemple, si un utilisateur a accès à un fichier via le fournisseur FileSystem (fourni par Windows PowerShell), mais pas l’accès en lecture, le fichier existe toujours et [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourne `true`. Votre implémentation peut nécessiter la vérification d’un élément parent pour voir si l’enfant peut être énuméré.

- Lors de l’écriture de plusieurs éléments, le [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode peut prendre un certain temps. Vous pouvez concevoir votre fournisseur pour écrire les éléments à l’aide de la [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) une méthode à la fois. À l’aide de cette technique présente les éléments à l’utilisateur dans un flux de données.

- Votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) est chargé pour empêcher une récurrence infinie lorsqu’il y a des liens circulaires et autres. Une exception de fin appropriée doit être levée pour refléter cette condition.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Get-ChildItem

Parfois le `Get-ChildItem` applet de commande qui appelle [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneur de Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Get-ChildItem` applet de commande.

Ce fournisseur de conteneur Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Récupération des noms d’élément enfant

Pour récupérer les noms des éléments enfants, le fournisseur de conteneur Windows PowerShell doit remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) méthode pour prendre en charge les appels à partir de la `Get-ChildItem`applet de commande lorsque son `Name` est précisé. Cette méthode récupère les noms des éléments enfants pour les noms d’élément enfant ou le chemin d’accès spécifiés pour tous les conteneurs si le `returnAllContainers` de l’applet de commande est précisé. Un nom de l’enfant est la partie de la feuille d’un chemin d’accès. Par exemple, le nom de l’enfant pour le chemin d’accès c:\windows\system32\abc.dll est « abc.dll ». Le nom de l’enfant pour le répertoire c:\windows\system32 est « system32 ».

Voici l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) méthode pour ce fournisseur. Notez que la méthode récupère les noms de tables si le chemin d’accès spécifié indique la base de données Access (lecteur) et les numéros de ligne si le chemin d’accès indique une table.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Points à retenir sur l’implémentation GetChildNames

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de conteneur Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

  > [!NOTE]
  > Une exception à cette règle se produit lorsque le `returnAllContainers` de l’applet de commande est précisé. Dans ce cas, la méthode doit récupérer n’importe quel nom de l’enfant d’un conteneur, même si elle ne correspond pas aux valeurs de la [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), ou [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer les noms des objets qui sont généralement masquées à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est spécifiée. Si le chemin d’accès spécifié indique un conteneur, le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété n’est pas obligatoire.

- Votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) est chargé pour empêcher une récurrence infinie lorsqu’il y a des liens circulaires et autres. Une exception de fin appropriée doit être levée pour refléter cette condition.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Attachement des paramètres dynamiques à l’applet de commande Get-ChildItem (nom)

Parfois le `Get-ChildItem` applet de commande (avec le `Name` paramètre) requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneur de Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Get-ChildItem` applet de commande.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Renommer des éléments

Pour renommer un élément, un fournisseur de conteneur Windows PowerShell doit remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) méthode pour prendre en charge les appels à partir de la `Rename-Item` applet de commande. Cette méthode modifie le nom de l’élément dans le chemin spécifié pour le nouveau nom fourni. Le nouveau nom doit toujours être relativement à l’élément parent (conteneur).

Ce fournisseur ne remplace pas le [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) (méthode). Toutefois, ce qui suit est l’implémentation par défaut.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Points à retenir sur l’implémentation RenameItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de conteneur Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Le [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) méthode est conçue pour la modification du nom d’un élément uniquement et non pour les opérations de déplacement. Votre implémentation de la méthode doit écrire une erreur si le `newName` paramètre contient des séparateurs de chemin d’accès ou pourraient sinon provoquer l’élément à modifier l’emplacement de son parent.

- Par défaut, les substitutions de cette méthode ne renommez pas les objets, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est spécifiée. Si le chemin d’accès spécifié indique un conteneur, le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété n’est pas obligatoire.

- Votre implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération lorsqu’une modification est apportée à l’état du système, par exemple, renommer les fichiers. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell en prenant en compte les paramètres de ligne de commande ou les variables de préférence dans déterminer ce qui doit être affiché.

  Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, le [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message d’un message de confirmation à l’utilisateur pour que les commentaires supplémentaires de dire si l’opération doit être poursuivie. Un fournisseur doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Rename-Item

Parfois le `Rename-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneur Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) (méthode). Cette méthode récupère les paramètres de l’article sur le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Rename-Item` applet de commande.

Ce fournisseur de conteneur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Création d’éléments

Pour créer des éléments, un fournisseur de conteneur doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode pour prendre en charge les appels à partir de la `New-Item` applet de commande. Cette méthode crée un élément de données situé dans le chemin d’accès spécifié. Le `type` paramètre de l’applet de commande contient le type défini par le fournisseur pour le nouvel élément. Par exemple, le fournisseur de système de fichiers utilise un `type` paramètre avec la valeur « file » ou « directory ». Le `newItemValue` paramètre de l’applet de commande spécifie une valeur spécifique au fournisseur pour le nouvel élément.

Voici l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode pour ce fournisseur.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Points à retenir sur l’implémentation NewItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Le [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode doit effectuer une comparaison respectant la casse de la chaîne passée dans le `type` paramètre. Il doit également permettre des correspondances moins ambigus. Par exemple, pour les types « file » et le « répertoire », seule la première lettre est requis pour lever l’ambiguïté. Si le `type` paramètre indique un type de votre fournisseur ne peut pas créer, le [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode doit écrire une exception ArgumentException avec un message indiquant les types, le fournisseur peut créer.

- Pour le `newItemValue` paramètre, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode est recommandée pour accepter des chaînes au minimum. Il doit également accepter le type d’objet est récupéré par le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) méthode pour le même chemin d’accès. Le [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode peut utiliser le [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) méthode pour convertir les types à le type souhaité.

- Votre implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne la valeur true, le [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) méthode comme une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande New-Item

Parfois le `New-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneur doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) (méthode). Cette méthode récupère les paramètres de l’article sur le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `New-Item` applet de commande.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Suppression d’éléments

Pour supprimer des éléments, le fournisseur Windows PowerShell doit remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) méthode pour prendre en charge les appels à partir de la `Remove-Item` applet de commande. Cette méthode supprime un élément du magasin de données dans le chemin spécifié. Si le `recurse` paramètre de la `Remove-Item` applet de commande est défini sur `true`, la méthode supprime tous les éléments enfants, quel que soit leur niveau. Si le paramètre est défini sur `false`, la méthode supprime uniquement un seul élément dans le chemin spécifié.

Ce fournisseur ne prend pas en charge la suppression d’éléments. Toutefois, le code suivant est l’implémentation par défaut de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Points à retenir sur l’implémentation RemoveItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de conteneur Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne devraient pas supprimer les objets, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur true. Si le chemin d’accès spécifié indique un conteneur, le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété n’est pas obligatoire.

- Votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) est chargé pour empêcher une récurrence infinie lorsqu’il y a des liens circulaires et autres. Une exception de fin appropriée doit être levée pour refléter cette condition.

- Votre implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, le [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) méthode comme une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Remove-Item

Parfois le `Remove-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneur doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) méthode pour gérer ces paramètres. Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Remove-Item` applet de commande.

Ce fournisseur de conteneur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Interrogation des éléments enfants

Pour vérifier s’il existe des éléments enfants dans le chemin spécifié, le fournisseur de conteneur Windows PowerShell doit remplacer le [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) (méthode). Cette méthode retourne `true` si l’élément a des enfants, et `false` dans le cas contraire. Pour un chemin d’accès null ou vide, la méthode considère que tous les éléments dans le magasin de données en tant qu’enfants et renvoie `true`.

Voici le remplacement de la [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) (méthode). S’il existe plus de deux parties de chemin d’accès créés par la méthode d’assistance ChunkPath, la méthode retourne `false`, étant donné qu’uniquement un conteneur de base de données et un conteneur de table sont définis. Pour plus d’informations sur cette méthode d’assistance, consultez la méthode ChunkPath est abordée dans [création d’un fournisseur d’éléments de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Points à retenir sur l’implémentation HasChildItems

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Si le fournisseur de conteneur expose une racine qui contient les points de montage intéressants, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) méthode doit retourner `true`quand une valeur null ou une chaîne vide est passée pour le chemin d’accès.

## <a name="copying-items"></a>Copie d’éléments

Pour copier des éléments, le fournisseur de conteneur doit implémenter le [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) méthode pour prendre en charge les appels à partir de la `Copy-Item` applet de commande. Cette méthode copie un élément de données à partir de l’emplacement indiqué par le `path` paramètre de l’applet de commande à l’emplacement indiqué par le `copyPath` paramètre. Si le `recurse` paramètre est spécifié, la méthode de copie tous les sous-conteneurs. Si le paramètre n’est pas spécifié, la méthode de copie uniquement un seul niveau d’éléments.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Points à retenir sur l’implémentation de CopyItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de conteneur Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne devraient pas copier les objets sur des objets existants, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Par exemple, le fournisseur FileSystem ne copiera pas c:\temp\abc.txt sur un fichier c:\abc.txt existant, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Si le chemin d’accès spécifié dans le `copyPath` paramètre existe et qu’il indique un conteneur, le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété n’est pas obligatoire. Dans ce cas, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) doit copier l’élément indiqué par le `path` paramètre vers le conteneur indiqué par le `copyPath` paramètre en tant qu’enfant.

- Votre implémentation de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) est chargé pour empêcher une récurrence infinie lorsqu’il y a des liens circulaires et autres. Une exception de fin appropriée doit être levée pour refléter cette condition.

- Votre implémentation de la [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne la valeur true, le [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) méthode comme une vérification supplémentaire pour les modifications du système potentiellement dangereux. Pour plus d’informations sur l’appel de ces méthodes, consultez [renommer les éléments](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Copy-Item

Parfois le `Copy-Item` applet de commande requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneur de Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) gérer ces (méthode) paramètres. Cette méthode récupère les paramètres de l’article sur le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à la `Copy-Item` applet de commande.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Exemple de code

Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Construction du fournisseur PowerShell de Windows

Consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur PowerShell de Windows

Lorsque votre fournisseur de Windows PowerShell a été enregistré avec Windows PowerShell, vous pouvez le tester en exécutant les applets de commande pris en charge sur la ligne de commande. N’oubliez pas que l’exemple suivant utilise une base de données Access fictive.

1. Exécutez le `Get-ChildItem` applet de commande pour récupérer la liste des éléments enfants à partir d’une table Customers dans la base de données Access.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   La sortie suivante s’affiche.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Exécutez le `Get-ChildItem` applet de commande pour récupérer les données d’une table.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   La sortie suivante s’affiche.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Utilisez maintenant le `Get-Item` applet de commande pour récupérer les éléments à la ligne 0 dans la table de données.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   La sortie suivante s’affiche.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Réutiliser `Get-Item` pour récupérer les données pour les éléments dans la ligne 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   La sortie suivante s’affiche.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Utilisez maintenant le `New-Item` applet de commande pour ajouter une ligne à une table existante. Le `Path` paramètre spécifie le chemin d’accès complet à la ligne et doit indiquer un numéro de ligne qui est supérieur au nombre de lignes dans la table existant. Le `Type` paramètre indique « ligne » pour spécifier ce type d’élément à ajouter. Enfin, le `Value` paramètre spécifie une liste délimitée par des virgules des valeurs de colonne pour la ligne.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Vérifiez l’exactitude de la nouvelle opération d’élément comme suit.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   La sortie suivante s’affiche.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Conception de votre fournisseur de PowerShell Windows](./designing-your-windows-powershell-provider.md)

[Implémentation d’un fournisseur d’éléments de PowerShell Windows](./creating-a-windows-powershell-item-provider.md)

[Implémentation d’un fournisseur de PowerShell de Windows de Navigation](./creating-a-windows-powershell-navigation-provider.md)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)