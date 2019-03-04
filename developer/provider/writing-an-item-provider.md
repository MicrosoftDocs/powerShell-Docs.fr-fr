---
title: Écriture d’un fournisseur d’élément | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: e3289e9336b863b5e0998a2beb29353c82a31f79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856705"
---
# <a name="writing-an-item-provider"></a>Écriture d’un fournisseur d’éléments

Cette rubrique décrit comment implémenter les méthodes d’un fournisseur Windows PowerShell qui accédant et manipulent des éléments dans le magasin de données. Pour être en mesure d’accéder aux éléments, un fournisseur doit dériver de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

Le fournisseur dans les exemples de cette rubrique utilise une base de données Access comme magasin de données. Il existe plusieurs méthodes d’assistance et des classes qui sont utilisées pour interagir avec la base de données. Pour l’exemple complet qui inclut les méthodes d’assistance, consultez [AccessDBProviderSample03](./accessdbprovidersample03.md)

Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implémentation des méthodes de l’élément

Le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe expose plusieurs méthodes qui peuvent être utilisées pour accéder et manipuler les éléments dans un magasin de données. Pour obtenir une liste complète de ces méthodes, consultez [ItemCmdletProvider méthodes](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). Dans cet exemple, nous implémenterons quatre de ces méthodes. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Obtient un élément à un chemin d’accès spécifié. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) définit la valeur de l’élément spécifié. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) vérifie si un élément existe dans le chemin spécifié. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) vérifie un chemin d’accès pour voir s’il est mappé à un emplacement dans le magasin de données.

> [!NOTE]
> Cette rubrique s’appuie sur les informations contenues dans [démarrage rapide de fournisseur Windows PowerShell](./windows-powershell-provider-quickstart.md). Cette rubrique ne couvre pas les principes fondamentaux de la configuration d’un projet de fournisseur, ou comment implémenter les méthodes héritées de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe créer et supprimer des lecteurs.

### <a name="declaring-the-provider-class"></a>Déclaration de la classe de fournisseur

Déclarer au fournisseur de dériver à partir de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe et la décorer avec le [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implémentation GetItem

Le [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) est appelée par le moteur PowerShell lorsqu’un utilisateur appelle le [Microsoft.Powershell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) applet de commande sur votre fournisseur. La méthode retourne l’élément dans le chemin spécifié. Dans l’exemple de base de données Access, la méthode vérifie si l’élément est le lecteur lui-même, une table dans la base de données ou d’une ligne dans la base de données. La méthode envoie l’élément du moteur PowerShell en appelant le [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (méthode).

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

### <a name="implementing-setitem"></a>Implémentation SetItem

Le [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) méthode est appelée par le moteur PowerShell appelle lorsqu’un utilisateur appelle le [Microsoft.Powershell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) applet de commande . Il définit la valeur de l’élément dans le chemin spécifié.

Dans l’exemple de base de données Access, il est judicieux pour définir la valeur d’un élément uniquement si cet élément est une ligne, donc la méthode lève [l’exception NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) lorsque l’élément n’est pas une ligne.

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

### <a name="implementing-itemexists"></a>Implémentation ItemExists

Le [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) méthode est appelée par le moteur PowerShell lorsqu’un utilisateur appelle le [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) applet de commande. La méthode détermine s’il existe un élément dans le chemin spécifié. Si l’élément existe, la méthode transmet au moteur PowerShell en appelant [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

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

### <a name="implementing-isvalidpath"></a>Implémentation IsValidPath

Le [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) méthode vérifie si le chemin d’accès spécifié est syntaxiquement valide pour le fournisseur actuel. Il ne vérifie pas si un élément existe dans le chemin d’accès.

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

Un fournisseur de réels typique est capable de prendre en charge les éléments qui contiennent d’autres éléments et de déplacement d’éléments à partir d’un chemin d’accès vers un autre dans le lecteur. Pour obtenir un exemple d’un fournisseur qui prend en charge des conteneurs, consultez [écriture d’un fournisseur de conteneur](./writing-a-container-provider.md). Pour obtenir un exemple d’un fournisseur qui prend en charge le déplacement des éléments, consultez [écriture d’un fournisseur de navigation](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur de conteneur](./writing-a-container-provider.md)

[Écriture d’un fournisseur de navigation](./writing-a-navigation-provider.md)

[Vue d’ensemble du fournisseur PowerShell Windows](./windows-powershell-provider-overview.md)