---
title: Écriture d’un fournisseur d’éléments | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1df30e7af1b534756f797b9b5d4e29b689cbc782
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786762"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="f56ae-102">Écriture d’un fournisseur d’éléments</span><span class="sxs-lookup"><span data-stu-id="f56ae-102">Writing an item provider</span></span>

<span data-ttu-id="f56ae-103">Cette rubrique explique comment implémenter les méthodes d’un fournisseur Windows PowerShell qui accèdent et manipulent des éléments dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="f56ae-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="f56ae-104">Pour pouvoir accéder aux éléments, un fournisseur doit dériver de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="f56ae-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="f56ae-105">Le fournisseur dans les exemples de cette rubrique utilise une base de données Access comme magasin de données.</span><span class="sxs-lookup"><span data-stu-id="f56ae-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="f56ae-106">Il existe plusieurs méthodes d’assistance et classes qui sont utilisées pour interagir avec la base de données.</span><span class="sxs-lookup"><span data-stu-id="f56ae-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="f56ae-107">Pour obtenir l’exemple complet qui comprend les méthodes d’assistance, consultez [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="f56ae-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="f56ae-108">Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f56ae-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="f56ae-109">Implémentation de méthodes d’élément</span><span class="sxs-lookup"><span data-stu-id="f56ae-109">Implementing item methods</span></span>

<span data-ttu-id="f56ae-110">La classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) expose plusieurs méthodes qui peuvent être utilisées pour accéder aux éléments d’un magasin de données et les manipuler.</span><span class="sxs-lookup"><span data-stu-id="f56ae-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="f56ae-111">Pour obtenir la liste complète de ces méthodes, consultez [méthodes ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="f56ae-111">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span></span> <span data-ttu-id="f56ae-112">Dans cet exemple, nous allons implémenter quatre de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="f56ae-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="f56ae-113">[System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtient un élément à un chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="f56ae-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="f56ae-114">[System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) définit la valeur de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="f56ae-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="f56ae-115">[System. Management. Automation. Provider. Itemcmdletprovider. itemExists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) vérifie si un élément existe dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="f56ae-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="f56ae-116">[System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) vérifie un chemin d’accès pour voir s’il est mappé à un emplacement dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="f56ae-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="f56ae-117">Cette rubrique est basée sur les informations contenues dans le Guide de [démarrage rapide du fournisseur Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="f56ae-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="f56ae-118">Cette rubrique ne couvre pas les concepts de base de la configuration d’un projet de fournisseur, ou la manière d’implémenter les méthodes héritées de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) qui créent et suppriment des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="f56ae-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="f56ae-119">Déclaration de la classe de fournisseur</span><span class="sxs-lookup"><span data-stu-id="f56ae-119">Declaring the provider class</span></span>

<span data-ttu-id="f56ae-120">Déclarez le fournisseur à dériver de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) et décorez-le à l’aide de [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="f56ae-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="f56ae-121">Implémentation de GetItem</span><span class="sxs-lookup"><span data-stu-id="f56ae-121">Implementing GetItem</span></span>

<span data-ttu-id="f56ae-122">[System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) est appelé par le moteur PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) sur votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="f56ae-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="f56ae-123">La méthode retourne l’élément au chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="f56ae-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="f56ae-124">Dans l’exemple de base de données Access, la méthode vérifie si l’élément est le lecteur lui-même, une table dans la base de données ou une ligne dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="f56ae-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="f56ae-125">La méthode envoie l’élément au moteur PowerShell en appelant la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .</span><span class="sxs-lookup"><span data-stu-id="f56ae-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="f56ae-126">Implémentation de SetItem</span><span class="sxs-lookup"><span data-stu-id="f56ae-126">Implementing SetItem</span></span>

<span data-ttu-id="f56ae-127">La méthode [System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) est appelée par les appels du moteur PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="f56ae-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="f56ae-128">Elle définit la valeur de l’élément au niveau du chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="f56ae-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="f56ae-129">Dans l’exemple de base de données Access, il est judicieux de définir la valeur d’un élément uniquement si cet élément est une ligne, de sorte que la méthode lève l' [exception NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) lorsque l’élément n’est pas une ligne.</span><span class="sxs-lookup"><span data-stu-id="f56ae-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="f56ae-130">Implémentation de ItemExists</span><span class="sxs-lookup"><span data-stu-id="f56ae-130">Implementing ItemExists</span></span>

<span data-ttu-id="f56ae-131">La méthode [System. Management. Automation. Provider. Itemcmdletprovider. itemExists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) est appelée par le moteur PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) .</span><span class="sxs-lookup"><span data-stu-id="f56ae-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="f56ae-132">La méthode détermine s’il existe un élément au chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="f56ae-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="f56ae-133">Si l’élément existe, la méthode le repasse au moteur PowerShell en appelant [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="f56ae-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="f56ae-134">Implémentation de IsValidPath</span><span class="sxs-lookup"><span data-stu-id="f56ae-134">Implementing IsValidPath</span></span>

<span data-ttu-id="f56ae-135">La méthode [System. Management. Automation. Provider. Itemcmdletprovider. IsValidPath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) vérifie si le chemin d’accès spécifié est syntaxiquement valide pour le fournisseur actuel.</span><span class="sxs-lookup"><span data-stu-id="f56ae-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="f56ae-136">Il ne vérifie pas si un élément existe dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f56ae-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="f56ae-137">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f56ae-137">Next steps</span></span>

<span data-ttu-id="f56ae-138">Un fournisseur réel réel est capable de prendre en charge des éléments qui contiennent d’autres éléments, et de déplacer des éléments d’un chemin d’accès à un autre dans le lecteur.</span><span class="sxs-lookup"><span data-stu-id="f56ae-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="f56ae-139">Pour obtenir un exemple de fournisseur qui prend en charge les conteneurs, consultez [écriture d’un fournisseur](./writing-a-container-provider.md)de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f56ae-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="f56ae-140">Pour obtenir un exemple de fournisseur qui prend en charge le déplacement d’éléments, consultez [écriture d’un fournisseur de navigation](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f56ae-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f56ae-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f56ae-141">See Also</span></span>

[<span data-ttu-id="f56ae-142">Écriture d’un fournisseur de conteneur</span><span class="sxs-lookup"><span data-stu-id="f56ae-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="f56ae-143">Écriture d’un fournisseur de navigation</span><span class="sxs-lookup"><span data-stu-id="f56ae-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="f56ae-144">Vue d’ensemble du fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f56ae-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
