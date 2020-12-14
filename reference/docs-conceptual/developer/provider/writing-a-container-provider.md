---
ms.date: 09/13/2016
ms.topic: reference
title: Écriture d’un fournisseur de conteneur
description: Écriture d’un fournisseur de conteneur
ms.openlocfilehash: 17ec3e11258ee77a8e569df1af3a0e9bcd9798b6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354930"
---
# <a name="writing-a-container-provider"></a><span data-ttu-id="a2d86-103">Écriture d’un fournisseur de conteneur</span><span class="sxs-lookup"><span data-stu-id="a2d86-103">Writing a container provider</span></span>

<span data-ttu-id="a2d86-104">Cette rubrique explique comment implémenter les méthodes d’un fournisseur Windows PowerShell qui prennent en charge des éléments qui contiennent d’autres éléments, tels que des dossiers dans le fournisseur de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a2d86-104">This topic describes how to implement the methods of a Windows PowerShell provider that support items that contain other items, such as folders in the file system provider.</span></span> <span data-ttu-id="a2d86-105">Pour pouvoir prendre en charge les conteneurs, un fournisseur doit dériver de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-105">To be able to support containers, a provider must derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

<span data-ttu-id="a2d86-106">Le fournisseur dans les exemples de cette rubrique utilise une base de données Access comme magasin de données.</span><span class="sxs-lookup"><span data-stu-id="a2d86-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="a2d86-107">Il existe plusieurs méthodes d’assistance et classes qui sont utilisées pour interagir avec la base de données.</span><span class="sxs-lookup"><span data-stu-id="a2d86-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="a2d86-108">Pour obtenir l’exemple complet qui comprend les méthodes d’assistance, consultez [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a2d86-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>

<span data-ttu-id="a2d86-109">Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2d86-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-container-methods"></a><span data-ttu-id="a2d86-110">Implémentation des méthodes de conteneur</span><span class="sxs-lookup"><span data-stu-id="a2d86-110">Implementing container methods</span></span>

<span data-ttu-id="a2d86-111">La classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) implémente les méthodes qui prennent en charge les conteneurs, et créent, copient et suppriment des éléments.</span><span class="sxs-lookup"><span data-stu-id="a2d86-111">The [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class implements methods that support containers, and create, copy, and remove items.</span></span> <span data-ttu-id="a2d86-112">Pour obtenir la liste complète de ces méthodes, consultez [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider#methods).</span><span class="sxs-lookup"><span data-stu-id="a2d86-112">For a complete list of these methods, see [System.Management.Automation.Provider.ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="a2d86-113">Cette rubrique est basée sur les informations contenues dans le Guide de [démarrage rapide du fournisseur Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="a2d86-113">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="a2d86-114">Cette rubrique ne couvre pas les concepts de base de la configuration d’un projet de fournisseur, ou la manière d’implémenter les méthodes héritées de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) qui créent et suppriment des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="a2d86-114">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="a2d86-115">Cette rubrique ne couvre pas non plus comment implémenter des méthodes exposées par la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-115">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="a2d86-116">Pour obtenir un exemple qui montre comment implémenter des applets de commande d’élément, consultez [écriture d’un fournisseur d’éléments](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a2d86-116">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="a2d86-117">Déclaration de la classe de fournisseur</span><span class="sxs-lookup"><span data-stu-id="a2d86-117">Declaring the provider class</span></span>

<span data-ttu-id="a2d86-118">Déclarez le fournisseur à dériver de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) et décorez-le à l’aide de [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="a2d86-118">Declare the provider to derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a><span data-ttu-id="a2d86-119">Implémentation de GetChildItems</span><span class="sxs-lookup"><span data-stu-id="a2d86-119">Implementing GetChildItems</span></span>

<span data-ttu-id="a2d86-120">Le moteur PowerShell appelle la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) quand un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-120">The PowerShell engine calls the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method when a user calls the [Microsoft.PowerShell.Commands.GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) cmdlet.</span></span> <span data-ttu-id="a2d86-121">Cette méthode obtient les éléments qui sont les enfants de l’élément au chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="a2d86-121">This method gets the items that are the children of the item at the specified path.</span></span>

<span data-ttu-id="a2d86-122">Dans l’exemple de base de données Access, le comportement de la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) dépend du type de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="a2d86-122">In the Access database example, the behavior of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method depends on the type of the specified item.</span></span> <span data-ttu-id="a2d86-123">Si l’élément est le lecteur, les enfants sont des tables et la méthode retourne l’ensemble des tables de la base de données.</span><span class="sxs-lookup"><span data-stu-id="a2d86-123">If the item is the drive, then the children are tables, and the method returns the set of tables from the database.</span></span> <span data-ttu-id="a2d86-124">Si l’élément spécifié est une table, les enfants sont les lignes de cette table.</span><span class="sxs-lookup"><span data-stu-id="a2d86-124">If the specified item is a table, then the children are the rows of that table.</span></span> <span data-ttu-id="a2d86-125">Si l’élément est une ligne, il n’a pas d’enfants et la méthode retourne cette ligne uniquement.</span><span class="sxs-lookup"><span data-stu-id="a2d86-125">If the item is a row, then it has no children, and the method returns that row only.</span></span> <span data-ttu-id="a2d86-126">Tous les éléments enfants sont renvoyés au moteur PowerShell par la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-126">All child items are sent back to the PowerShell engine by the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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
       }
```

### <a name="implementing-getchildnames"></a><span data-ttu-id="a2d86-127">Implémentation de GetChildNames</span><span class="sxs-lookup"><span data-stu-id="a2d86-127">Implementing GetChildNames</span></span>

<span data-ttu-id="a2d86-128">La méthode [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) est semblable à la méthode [System. Management. Automation. Provider. Containercmdletprovider. GetChildItems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) , sauf qu’elle retourne uniquement la propriété Name des éléments, et non les éléments eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="a2d86-128">The [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method is similar to the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method, except that it returns only the name property of the items, and not the items themselves.</span></span>

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
       }
```

### <a name="implementing-newitem"></a><span data-ttu-id="a2d86-129">Implémentation de NewItem</span><span class="sxs-lookup"><span data-stu-id="a2d86-129">Implementing NewItem</span></span>

<span data-ttu-id="a2d86-130">La méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) crée un élément du type spécifié dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="a2d86-130">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method creates a new item of the specified type at the specified path.</span></span> <span data-ttu-id="a2d86-131">Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-131">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) cmdlet.</span></span>

<span data-ttu-id="a2d86-132">Dans cet exemple, la méthode implémente la logique pour déterminer que le chemin d’accès et le type correspondent.</span><span class="sxs-lookup"><span data-stu-id="a2d86-132">In this example, the method implements logic to determine that the path and type match.</span></span> <span data-ttu-id="a2d86-133">Autrement dit, seule une table peut être créée directement sous le lecteur (la base de données), et seule une ligne peut être créée sous une table.</span><span class="sxs-lookup"><span data-stu-id="a2d86-133">That is, only a table can be created directly under the drive (the database), and only a row can be created under a table.</span></span> <span data-ttu-id="a2d86-134">Si le chemin d’accès et le type d’élément spécifiés ne correspondent pas de cette manière, la méthode lève une exception.</span><span class="sxs-lookup"><span data-stu-id="a2d86-134">If the specified path and item type don't match in this way, the method throws an exception.</span></span>

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a><span data-ttu-id="a2d86-135">Implémentation de CopyItem</span><span class="sxs-lookup"><span data-stu-id="a2d86-135">Implementing CopyItem</span></span>

<span data-ttu-id="a2d86-136">[System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copie l’élément spécifié dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="a2d86-136">The [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copies the specified item to the specified path.</span></span> <span data-ttu-id="a2d86-137">Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-137">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) cmdlet.</span></span> <span data-ttu-id="a2d86-138">Cette méthode peut également être récursive, en copiant tous les éléments enfants en plus de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2d86-138">This method can also be recursive, copying all of the items children in addition to the item itself.</span></span>

<span data-ttu-id="a2d86-139">À l’instar de la méthode [System. Management. Automation. Provider. Containercmdletprovider. newItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) , cette méthode exécute une logique pour s’assurer que l’élément spécifié est du type correct pour le chemin d’accès vers lequel il est copié.</span><span class="sxs-lookup"><span data-stu-id="a2d86-139">Similarly to the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method, this method performs logic to make sure that the specified item is of the correct type for the path to which it is being copied.</span></span> <span data-ttu-id="a2d86-140">Par exemple, si le chemin d’accès de destination est une table, l’élément à copier doit être une ligne.</span><span class="sxs-lookup"><span data-stu-id="a2d86-140">For example, if the destination path is a table, the item to be copied must be a row.</span></span>

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a><span data-ttu-id="a2d86-141">Implémentation de RemoveItem</span><span class="sxs-lookup"><span data-stu-id="a2d86-141">Implementing RemoveItem</span></span>

<span data-ttu-id="a2d86-142">La méthode [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) supprime l’élément au niveau du chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="a2d86-142">The [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method removes the item at the specified path.</span></span> <span data-ttu-id="a2d86-143">Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="a2d86-143">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) cmdlet.</span></span>

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a><span data-ttu-id="a2d86-144">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a2d86-144">Next steps</span></span>

<span data-ttu-id="a2d86-145">Un fournisseur réel réel peut déplacer des éléments d’un chemin d’accès à un autre dans le lecteur.</span><span class="sxs-lookup"><span data-stu-id="a2d86-145">A typical real-world provider is capable of moving items from one path to another within the drive.</span></span>
<span data-ttu-id="a2d86-146">Pour obtenir un exemple de fournisseur qui prend en charge le déplacement d’éléments, consultez [écriture d’un fournisseur de navigation](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a2d86-146">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2d86-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2d86-147">See Also</span></span>

[<span data-ttu-id="a2d86-148">Écriture d’un fournisseur de navigation</span><span class="sxs-lookup"><span data-stu-id="a2d86-148">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="a2d86-149">Vue d’ensemble du fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2d86-149">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
