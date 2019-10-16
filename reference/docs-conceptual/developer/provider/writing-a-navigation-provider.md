---
title: Écriture d’un fournisseur de navigation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359868"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="742ce-102">Écriture d’un fournisseur de navigation</span><span class="sxs-lookup"><span data-stu-id="742ce-102">Writing a navigation provider</span></span>

<span data-ttu-id="742ce-103">Cette rubrique explique comment implémenter les méthodes d’un fournisseur Windows PowerShell qui prennent en charge les conteneurs imbriqués (magasins de données à plusieurs niveaux), les éléments de déplacement et les chemins d’accès relatifs.</span><span class="sxs-lookup"><span data-stu-id="742ce-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="742ce-104">Un fournisseur de navigation doit dériver de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="742ce-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="742ce-105">Le fournisseur dans les exemples de cette rubrique utilise une base de données Access comme magasin de données.</span><span class="sxs-lookup"><span data-stu-id="742ce-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="742ce-106">Il existe plusieurs méthodes d’assistance et classes qui sont utilisées pour interagir avec la base de données.</span><span class="sxs-lookup"><span data-stu-id="742ce-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="742ce-107">Pour obtenir l’exemple complet qui comprend les méthodes d’assistance, consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="742ce-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="742ce-108">Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="742ce-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="742ce-109">Implémentation des méthodes de navigation</span><span class="sxs-lookup"><span data-stu-id="742ce-109">Implementing navigation methods</span></span>

<span data-ttu-id="742ce-110">La classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implémente les méthodes qui prennent en charge les conteneurs imbriqués, les chemins d’accès relatifs et les éléments de déplacement.</span><span class="sxs-lookup"><span data-stu-id="742ce-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="742ce-111">Pour obtenir la liste complète de ces méthodes, consultez [méthodes NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="742ce-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="742ce-112">Cette rubrique est basée sur les informations contenues dans le Guide de [démarrage rapide du fournisseur Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="742ce-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="742ce-113">Cette rubrique ne couvre pas les concepts de base de la configuration d’un projet de fournisseur, ou la manière d’implémenter les méthodes héritées de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) qui créent et suppriment des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="742ce-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="742ce-114">Cette rubrique ne couvre pas non plus comment implémenter des méthodes exposées par les classes [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) ou [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="742ce-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="742ce-115">Pour obtenir un exemple qui montre comment implémenter des applets de commande d’élément, consultez [écriture d’un fournisseur d’éléments](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="742ce-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="742ce-116">Pour obtenir un exemple qui montre comment implémenter des applets de commande de conteneur, consultez [écriture d’un fournisseur de conteneurs](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="742ce-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="742ce-117">Déclaration de la classe de fournisseur</span><span class="sxs-lookup"><span data-stu-id="742ce-117">Declaring the provider class</span></span>

<span data-ttu-id="742ce-118">Déclarez le fournisseur à dériver de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et décorez-le à l’aide de [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="742ce-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="742ce-119">Implémentation de IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="742ce-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="742ce-120">La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. IsItemContainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) vérifie si l’élément au chemin d’accès spécifié est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="742ce-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="742ce-121">Implémentation de GetChildName</span><span class="sxs-lookup"><span data-stu-id="742ce-121">Implementing GetChildName</span></span>

<span data-ttu-id="742ce-122">La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) obtient la propriété de nom de l’élément enfant au niveau du chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="742ce-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="742ce-123">Si l’élément au chemin d’accès spécifié n’est pas un enfant d’un conteneur, cette méthode doit retourner le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="742ce-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="742ce-124">Implémentation de GetParentPath</span><span class="sxs-lookup"><span data-stu-id="742ce-124">Implementing GetParentPath</span></span>

<span data-ttu-id="742ce-125">La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) obtient le chemin d’accès du parent de l’élément au chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="742ce-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="742ce-126">Si l’élément au chemin d’accès spécifié est la racine du magasin de données (il n’a donc pas de parent), cette méthode doit retourner le chemin d’accès racine.</span><span class="sxs-lookup"><span data-stu-id="742ce-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="742ce-127">Implémentation de MakePath</span><span class="sxs-lookup"><span data-stu-id="742ce-127">Implementing MakePath</span></span>

<span data-ttu-id="742ce-128">La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) joint un chemin d’accès parent spécifié et un chemin d’accès enfant spécifié pour créer un chemin d’accès interne au fournisseur (pour plus d’informations sur les types de chemins d’accès que les fournisseurs peuvent prendre en charge, consultez [Vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="742ce-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="742ce-129">Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .</span><span class="sxs-lookup"><span data-stu-id="742ce-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="742ce-130">Implémentation de NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="742ce-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="742ce-131">La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) prend les paramètres `path` et `basepath`, et retourne un chemin d’accès normalisé équivalent au paramètre `path` et relatif au `basepath` paramètre.</span><span class="sxs-lookup"><span data-stu-id="742ce-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="742ce-132">Implémentation de MoveItem</span><span class="sxs-lookup"><span data-stu-id="742ce-132">Implementing MoveItem</span></span>

<span data-ttu-id="742ce-133">La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) déplace un élément du chemin d’accès spécifié vers le chemin d’accès de destination spécifié.</span><span class="sxs-lookup"><span data-stu-id="742ce-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="742ce-134">Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="742ce-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="742ce-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="742ce-135">See Also</span></span>

[<span data-ttu-id="742ce-136">Écriture d’un fournisseur de conteneurs</span><span class="sxs-lookup"><span data-stu-id="742ce-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="742ce-137">Vue d’ensemble du fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="742ce-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)