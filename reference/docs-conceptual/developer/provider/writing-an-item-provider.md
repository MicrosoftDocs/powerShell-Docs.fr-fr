---
ms.date: 09/13/2016
ms.topic: reference
title: Écriture d’un fournisseur d’éléments
description: Écriture d’un fournisseur d’éléments
ms.openlocfilehash: f70c6ee50277988c4e3b7c255dc4548bc30319dd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355202"
---
# <a name="writing-an-item-provider"></a>Écriture d’un fournisseur d’éléments

Cette rubrique explique comment implémenter les méthodes d’un fournisseur Windows PowerShell qui accèdent et manipulent des éléments dans le magasin de données. Pour pouvoir accéder aux éléments, un fournisseur doit dériver de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

Le fournisseur dans les exemples de cette rubrique utilise une base de données Access comme magasin de données. Il existe plusieurs méthodes d’assistance et classes qui sont utilisées pour interagir avec la base de données. Pour obtenir l’exemple complet qui comprend les méthodes d’assistance, consultez [AccessDBProviderSample03](./accessdbprovidersample03.md)

Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implémentation de méthodes d’élément

La classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) expose plusieurs méthodes qui peuvent être utilisées pour accéder aux éléments d’un magasin de données et les manipuler.
Pour obtenir la liste complète de ces méthodes, consultez [méthodes ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods).
Dans cet exemple, nous allons implémenter quatre de ces méthodes.
[System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtient un élément à un chemin d’accès spécifié.
[System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) définit la valeur de l’élément spécifié.
[System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) vérifie si un élément existe dans le chemin d’accès spécifié.
[System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) vérifie un chemin d’accès pour voir s’il est mappé à un emplacement dans le magasin de données.

> [!NOTE]
> Cette rubrique est basée sur les informations contenues dans le Guide de [démarrage rapide du fournisseur Windows PowerShell](./windows-powershell-provider-quickstart.md). Cette rubrique ne couvre pas les concepts de base de la configuration d’un projet de fournisseur, ou la manière d’implémenter les méthodes héritées de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) qui créent et suppriment des lecteurs.

### <a name="declaring-the-provider-class"></a>Déclaration de la classe de fournisseur

Déclarez le fournisseur à dériver de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) et décorez-le à l’aide de [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implémentation de GetItem

[System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) est appelé par le moteur PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) sur votre fournisseur. La méthode retourne l’élément au chemin d’accès spécifié. Dans l’exemple de base de données Access, la méthode vérifie si l’élément est le lecteur lui-même, une table dans la base de données ou une ligne dans la base de données. La méthode envoie l’élément au moteur PowerShell en appelant la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implémentation de SetItem

La méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) est appelée par les appels du moteur PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) . Elle définit la valeur de l’élément au niveau du chemin d’accès spécifié.

Dans l’exemple de base de données Access, il est judicieux de définir la valeur d’un élément uniquement si cet élément est une ligne, de sorte que la méthode lève l' [exception NotSupportedException](/dotnet/api/system.notsupportedexception) lorsque l’élément n’est pas une ligne.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implémentation de ItemExists

La méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) est appelée par le moteur PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) . La méthode détermine s’il existe un élément au chemin d’accès spécifié. Si l’élément existe, la méthode le repasse au moteur PowerShell en appelant [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implémentation de IsValidPath

La méthode [System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) vérifie si le chemin d’accès spécifié est syntaxiquement valide pour le fournisseur actuel. Il ne vérifie pas si un élément existe dans le chemin d’accès.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Étapes suivantes

Un fournisseur réel réel est capable de prendre en charge des éléments qui contiennent d’autres éléments, et de déplacer des éléments d’un chemin d’accès à un autre dans le lecteur. Pour obtenir un exemple de fournisseur qui prend en charge les conteneurs, consultez [écriture d’un fournisseur](./writing-a-container-provider.md)de conteneurs. Pour obtenir un exemple de fournisseur qui prend en charge le déplacement d’éléments, consultez [écriture d’un fournisseur de navigation](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur de conteneur](./writing-a-container-provider.md)

[Écriture d’un fournisseur de navigation](./writing-a-navigation-provider.md)

[Vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md)
