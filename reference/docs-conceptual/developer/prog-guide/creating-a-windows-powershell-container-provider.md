---
title: Création d’un fournisseur de conteneur Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: eec92d526ad78d2351eef6679eaa0df19900715b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978489"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Création d’un fournisseur de conteneur Windows PowerShell

Cette rubrique explique comment créer un fournisseur Windows PowerShell qui peut fonctionner sur des magasins de données multicouches. Pour ce type de banque de données, le niveau supérieur du magasin contient les éléments racine et chaque niveau suivant est désigné sous le terme de nœud d’éléments enfants. En permettant à l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir hiérarchiquement via le magasin de données.

Les fournisseurs qui peuvent travailler sur des magasins de données à plusieurs niveaux sont appelés fournisseurs de conteneurs Windows PowerShell. Toutefois, sachez qu’un fournisseur de conteneurs Windows PowerShell ne peut être utilisé qu’en présence d’éléments dans un conteneur (sans conteneurs imbriqués). S’il existe des conteneurs imbriqués, vous devez implémenter un fournisseur de navigation Windows PowerShell. Pour plus d’informations sur l’implémentation du fournisseur de navigation Windows PowerShell, consultez [création d’un fournisseur de navigation Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (AccessDBSampleProvider04.cs) pour ce fournisseur à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** . Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

Le fournisseur de conteneurs Windows PowerShell décrit ici définit la base de données en tant que conteneur unique, avec les tables et les lignes de la base de données définies en tant qu’éléments du conteneur.

> [!CAUTION]
> N’oubliez pas que cette conception suppose qu’il s’agit d’une base de données qui a un champ avec l’ID de nom et que le type du champ est LongInteger.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Définition d’une classe de fournisseur de conteneurs Windows PowerShell

Un fournisseur de conteneurs Windows PowerShell doit définir une classe .NET qui dérive de la classe de base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Voici la définition de classe pour le fournisseur de conteneurs Windows PowerShell décrit dans cette section.

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

Notez que dans cette définition de classe, l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) comprend deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose au runtime Windows PowerShell pendant le traitement de la commande. Pour ce fournisseur, aucune fonctionnalité spécifique de Windows PowerShell n’est ajoutée.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de base

Comme décrit dans [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) dérive de plusieurs autres classes qui offraient des fonctionnalités de fournisseur différentes. Un fournisseur de conteneurs Windows PowerShell, par conséquent, doit définir toutes les fonctionnalités fournies par ces classes.

Pour implémenter les fonctionnalités d’ajout d’informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md).
Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.

Pour accéder au magasin de données, le fournisseur doit implémenter les méthodes de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Pour manipuler les éléments d’un magasin de données, tels que l’obtention, la définition et l’effacement des éléments, le fournisseur doit implémenter les méthodes fournies par la classe de base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur d’éléments Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Récupération d’éléments enfants

Pour récupérer un élément enfant, le fournisseur de conteneurs Windows PowerShell doit substituer la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour prendre en charge les appels à partir de l’applet de commande `Get-ChildItem`. Cette méthode récupère les éléments enfants dans le magasin de données et les écrit dans le pipeline en tant qu’objets. Si le paramètre `recurse` de l’applet de commande est spécifié, la méthode récupère tous les enfants, quel que soit le niveau auquel ils se trouvent. Si le paramètre `recurse` n’est pas spécifié, la méthode récupère uniquement un seul niveau d’enfants.

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) pour ce fournisseur. Notez que cette méthode récupère les éléments enfants dans toutes les tables de base de données lorsque le chemin d’accès indique la base de données Access et récupère les éléments enfants à partir des lignes de cette table si le chemin d’accès indique une table de données.

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="311-362":::

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Points à retenir concernant l’implémentation de GetChildItems

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Lors de la définition de la classe de fournisseur, un fournisseur de conteneurs Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- L’implémentation de cette méthode doit prendre en compte toute forme d’accès à l’élément qui peut rendre l’élément visible à l’utilisateur. Par exemple, si un utilisateur dispose d’un accès en écriture à un fichier via le fournisseur FileSystem (fourni par Windows PowerShell), mais pas d’accès en lecture, le fichier existe toujours et [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourne `true`. Votre implémentation peut nécessiter la vérification d’un élément parent pour voir si l’enfant peut être énuméré.

- Lors de l’écriture de plusieurs éléments, la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) peut prendre un certain temps. Vous pouvez concevoir votre fournisseur pour écrire les éléments à l’aide de la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) une à la fois. L’utilisation de cette technique permet de présenter les éléments à l’utilisateur dans un flux.

- Votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) est chargée d’empêcher une récurrence infinie lorsqu’il y a des liens circulaires, et ainsi de suite. Une exception d’arrêt appropriée doit être levée pour refléter une telle condition.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande

Parfois, l’applet de commande `Get-ChildItem` qui appelle [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) nécessite des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneurs Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Get-ChildItem`.

Ce fournisseur de conteneurs Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Récupération des noms d’éléments enfants

Pour récupérer les noms des éléments enfants, le fournisseur de conteneurs Windows PowerShell doit substituer la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) pour prendre en charge les appels à partir de l’applet de commande `Get-ChildItem` lorsque son paramètre `Name` est spécifié. Cette méthode récupère les noms des éléments enfants pour le chemin d’accès ou les noms d’éléments enfants spécifiés pour tous les conteneurs si le paramètre `returnAllContainers` de l’applet de commande est spécifié. Un nom enfant est la partie feuille d’un chemin d’accès. Par exemple, le nom enfant pour le chemin d’accès c:\windows\system32\abc.dll est « ABC. dll ». Le nom enfant du répertoire c:\Windows\System32 est « system32 ».

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) pour ce fournisseur. Notez que la méthode récupère les noms des tables si le chemin d’accès spécifié indique la base de données Access (lecteur) et les numéros de ligne si le chemin d’accès indique une table.

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="369-411":::

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Points à retenir concernant l’implémentation de GetChildNames

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Lors de la définition de la classe de fournisseur, un fournisseur de conteneurs Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

  > [!NOTE]
  > Une exception à cette règle se produit lorsque le paramètre `returnAllContainers` de l’applet de commande est spécifié. Dans ce cas, la méthode doit récupérer tout nom enfant pour un conteneur, même s’il ne correspond pas aux valeurs des propriétés [System. Management. Automation. Provider. Cmdletprovider. Filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), System. Management. Automation. Provider. [Cmdletprovider. include](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)* ou [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer les noms des objets qui sont généralement masqués par l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit spécifiée. Si le chemin d’accès spécifié indique un conteneur, la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) n’est pas obligatoire.

- Votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) est chargée d’empêcher une récurrence infinie lorsqu’il y a des liens circulaires, et ainsi de suite. Une exception d’arrêt appropriée doit être levée pour refléter une telle condition.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Attachement de paramètres dynamiques à l’applet de commande (Name) de l’applet de commande

Parfois, l’applet de commande `Get-ChildItem` (avec le paramètre `Name`) requiert des paramètres supplémentaires qui sont spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneurs Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Get-ChildItem`.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Attribution d’un nouveau nom aux éléments

Pour renommer un élément, un fournisseur de conteneurs Windows PowerShell doit substituer la méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) pour prendre en charge les appels à partir de l’applet de commande `Rename-Item`. Cette méthode remplace le nom de l’élément au niveau du chemin d’accès spécifié par le nouveau nom fourni. Le nouveau nom doit toujours être relatif à l’élément parent (conteneur).

Ce fournisseur ne remplace pas la méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) . Toutefois, l’implémentation par défaut est la suivante.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Points à retenir concernant l’implémentation de RenameItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Lors de la définition de la classe de fournisseur, un fournisseur de conteneurs Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- La méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) est destinée uniquement à la modification du nom d’un élément, et non pas aux opérations de déplacement.
  Votre implémentation de la méthode doit écrire une erreur si le paramètre `newName` contient des séparateurs de chemin d’accès ou si elle peut entraîner la modification de son emplacement parent par l’élément.

- Par défaut, les substitutions de cette méthode ne doivent pas renommer les objets, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit spécifiée. Si le chemin d’accès spécifié indique un conteneur, la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) n’est pas obligatoire.

- Votre implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération quand une modification est apportée à l’état du système, par exemple, renommer des fichiers.
  [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte des paramètres de ligne de commande ou des variables de préférence pour déterminer ce qui doit être affiché.

  Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, la méthode [System. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message de confirmation à l’utilisateur afin d’autoriser des commentaires supplémentaires à indiquer si l’opération doit être poursuivie. Un fournisseur doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) pour une vérification supplémentaire des modifications système potentiellement dangereuses.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Rename-Item

Parfois, l’applet de commande `Rename-Item` requiert des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneurs Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) . Cette méthode récupère les paramètres pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Rename-Item`.

Ce fournisseur de conteneurs n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Création de nouveaux éléments

Pour créer de nouveaux éléments, un fournisseur de conteneurs doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) pour prendre en charge les appels à partir de l’applet de commande `New-Item`. Cette méthode crée un élément de données situé dans le chemin d’accès spécifié. Le paramètre `type` de l’applet de commande contient le type défini par le fournisseur pour le nouvel élément. Par exemple, le fournisseur FileSystem utilise un paramètre `type` avec la valeur « file » ou « Directory ». Le paramètre `newItemValue` de l’applet de commande spécifie une valeur spécifique au fournisseur pour le nouvel élément.

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) pour ce fournisseur.

```csharp
protected override void NewItem( string path, string type, object newItemValue )
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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="939-955":::

#### <a name="things-to-remember-about-implementing-newitem"></a>Points à retenir concernant l’implémentation de NewItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- La méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) doit effectuer une comparaison ne respectant pas la casse de la chaîne passée dans le paramètre `type`.
  Elle doit également permettre des correspondances moins ambiguës. Par exemple, pour les types « fichier » et « répertoire », seule la première lettre est nécessaire pour lever l’ambiguïté. Si le paramètre `type` indique un type que votre fournisseur ne peut pas créer, la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) doit écrire une exception ArgumentException avec un message indiquant les types que le fournisseur peut créer.

- Pour le paramètre `newItemValue`, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) est recommandée pour accepter des chaînes au minimum. Elle doit également accepter le type d’objet récupéré par la méthode [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pour le même chemin d’accès. La méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) peut utiliser la méthode [System. Management. Automation. LanguagePrimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) pour convertir les types vers le type souhaité.

- Votre implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne la valeur true, la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) pour effectuer un contrôle supplémentaire des modifications système potentiellement dangereuses.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande New-Item

Parfois, l’applet de commande `New-Item` requiert des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneurs doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) . Cette méthode récupère les paramètres pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `New-Item`.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Suppression d’éléments

Pour supprimer des éléments, le fournisseur Windows PowerShell doit substituer la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) pour prendre en charge les appels à partir de l’applet de commande `Remove-Item`. Cette méthode supprime un élément du magasin de données dans le chemin d’accès spécifié. Si le paramètre `recurse` de l’applet de commande `Remove-Item` a la valeur `true`, la méthode supprime tous les éléments enfants, quel que soit leur niveau. Si le paramètre a la valeur `false`, la méthode supprime un seul élément au chemin d’accès spécifié.

Ce fournisseur ne prend pas en charge la suppression d’éléments. Toutefois, le code suivant est l’implémentation par défaut de [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Points à retenir concernant l’implémentation de RemoveItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. newItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Lors de la définition de la classe de fournisseur, un fournisseur de conteneurs Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas supprimer d’objets, sauf si la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur true. Si le chemin d’accès spécifié indique un conteneur, la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) n’est pas obligatoire.

- Votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) est chargée d’empêcher la récurrence infinie lorsqu’il y a des liens circulaires, et ainsi de suite. Une exception d’arrêt appropriée doit être levée pour refléter une telle condition.

- Votre implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, la méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) pour effectuer un contrôle supplémentaire des modifications système potentiellement dangereuses.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Remove-Item

Parfois, l’applet de commande `Remove-Item` requiert des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneurs doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) pour gérer ces paramètres. Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Remove-Item`.

Ce fournisseur de conteneurs n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Interrogation d’éléments enfants

Pour vérifier si des éléments enfants existent dans le chemin d’accès spécifié, le fournisseur de conteneurs Windows PowerShell doit substituer la méthode [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Cette méthode retourne `true` si l’élément a des enfants, et `false` dans le cas contraire. Pour un chemin d’accès null ou vide, la méthode considère que tous les éléments du magasin de données sont des enfants et retourne `true`.

Voici le remplacement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . S’il existe plus de deux parties de chemin d’accès créées par la méthode d’assistance ChunkPath, la méthode retourne `false`, car seul un conteneur de base de données et un conteneur de table sont définis. Pour plus d’informations sur cette méthode d’assistance, consultez la méthode ChunkPath est décrite dans [création d’un fournisseur d’éléments Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Points à retenir concernant l’implémentation de HasChildItems

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Si le fournisseur de conteneurs expose une racine qui contient des points de montage intéressants, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) doit retourner `true` lorsqu’une chaîne null ou vide est passée pour le chemin d’accès.

## <a name="copying-items"></a>Copie d’éléments

Pour copier des éléments, le fournisseur de conteneurs doit implémenter la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) pour prendre en charge les appels à partir de l’applet de commande `Copy-Item`. Cette méthode copie un élément de données à partir de l’emplacement indiqué par le paramètre `path` de l’applet de commande vers l’emplacement indiqué par le paramètre `copyPath`. Si le paramètre `recurse` est spécifié, la méthode copie tous les sous-conteneurs. Si le paramètre n’est pas spécifié, la méthode copie uniquement un seul niveau d’éléments.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Points à retenir concernant l’implémentation de CopyItem

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Lors de la définition de la classe de fournisseur, un fournisseur de conteneurs Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas copier des objets sur des objets existants, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit définie sur `true`. Par exemple, le fournisseur FileSystem ne copie pas c:\temp\abc.txt sur un fichier c:\ABC.txt existant, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit définie sur `true`. Si le chemin d’accès spécifié dans le paramètre `copyPath` existe et qu’il indique un conteneur, la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) n’est pas obligatoire. Dans ce cas, [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) doit copier l’élément indiqué par le paramètre `path` dans le conteneur indiqué par le paramètre `copyPath` en tant qu’enfant.

- Votre implémentation de [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) est chargée d’empêcher la récurrence infinie lorsqu’il y a des liens circulaires, et ainsi de suite. Une exception d’arrêt appropriée doit être levée pour refléter une telle condition.

- Votre implémentation de la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne la valeur true, la méthode [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) pour effectuer un contrôle supplémentaire des modifications système potentiellement dangereuses. Pour plus d’informations sur l’appel de ces méthodes, consultez [Renommer des éléments](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Copy-Item

Parfois, l’applet de commande `Copy-Item` requiert des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de conteneurs Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) pour gérer ces paramètres. Cette méthode récupère les paramètres pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande `Copy-Item`.

Ce fournisseur n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Exemple de code

Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Génération du fournisseur Windows PowerShell

Découvrez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Lorsque votre fournisseur Windows PowerShell a été inscrit auprès de Windows PowerShell, vous pouvez le tester en exécutant les applets de commande prises en charge sur la ligne de commande. N’oubliez pas que l’exemple de sortie suivant utilise une base de données d’accès fictif.

1. Exécutez l’applet de commande `Get-ChildItem` pour récupérer la liste des éléments enfants d’une table Customers dans la base de données Access.

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

2. Exécutez à nouveau l’applet de commande `Get-ChildItem` pour récupérer les données d’une table.

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

3. À présent, utilisez l’applet de commande `Get-Item` pour récupérer les éléments à la ligne 0 dans la table de données.

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

4. Réutilisez `Get-Item` pour récupérer les données des éléments de la ligne 0.

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

5. À présent, utilisez l’applet de commande `New-Item` pour ajouter une ligne à une table existante. Le paramètre `Path` spécifie le chemin d’accès complet à la ligne et doit indiquer un numéro de ligne qui est supérieur au nombre de lignes existant dans la table. Le paramètre `Type` indique « Row » pour spécifier ce type d’élément à ajouter.
   Enfin, le paramètre `Value` spécifie une liste délimitée par des virgules de valeurs de colonne pour la ligne.

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

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implémentation d’un fournisseur Windows PowerShell d’élément](./creating-a-windows-powershell-item-provider.md)

[Implémentation d’un fournisseur de navigation Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)
