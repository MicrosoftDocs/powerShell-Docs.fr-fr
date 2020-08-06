---
title: Écriture d’un fournisseur de navigation | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2fd27314a2b8547a15dd1bb72aa8f970d40b18cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786779"
---
# <a name="writing-a-navigation-provider"></a>Écriture d’un fournisseur de navigation

Cette rubrique explique comment implémenter les méthodes d’un fournisseur Windows PowerShell qui prennent en charge les conteneurs imbriqués (magasins de données à plusieurs niveaux), les éléments de déplacement et les chemins d’accès relatifs. Un fournisseur de navigation doit dériver de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Le fournisseur dans les exemples de cette rubrique utilise une base de données Access comme magasin de données. Il existe plusieurs méthodes d’assistance et classes qui sont utilisées pour interagir avec la base de données. Pour obtenir l’exemple complet qui comprend les méthodes d’assistance, consultez [AccessDBProviderSample05](./accessdbprovidersample05.md).

Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-navigation-methods"></a>Implémentation des méthodes de navigation

La classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implémente les méthodes qui prennent en charge les conteneurs imbriqués, les chemins d’accès relatifs et les éléments de déplacement. Pour obtenir la liste complète de ces méthodes, consultez [méthodes NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).

> [!NOTE]
> Cette rubrique est basée sur les informations contenues dans le Guide de [démarrage rapide du fournisseur Windows PowerShell](./windows-powershell-provider-quickstart.md). Cette rubrique ne couvre pas les concepts de base de la configuration d’un projet de fournisseur, ou la manière d’implémenter les méthodes héritées de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) qui créent et suppriment des lecteurs. Cette rubrique ne couvre pas non plus comment implémenter des méthodes exposées par les classes [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) ou [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Pour obtenir un exemple qui montre comment implémenter des applets de commande d’élément, consultez [écriture d’un fournisseur d’éléments](./writing-an-item-provider.md). Pour obtenir un exemple qui montre comment implémenter des applets de commande de conteneur, consultez [écriture d’un fournisseur de conteneurs](./writing-a-container-provider.md).

### <a name="declaring-the-provider-class"></a>Déclaration de la classe de fournisseur

Déclarez le fournisseur à dériver de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et décorez-le à l’aide de [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>Implémentation de IsItemContainer

La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) vérifie si l’élément au chemin d’accès spécifié est un conteneur.

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

### <a name="implementing-getchildname"></a>Implémentation de GetChildName

La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) obtient la propriété de nom de l’élément enfant au niveau du chemin d’accès spécifié. Si l’élément au chemin d’accès spécifié n’est pas un enfant d’un conteneur, cette méthode doit retourner le chemin d’accès.

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

### <a name="implementing-getparentpath"></a>Implémentation de GetParentPath

La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) obtient le chemin d’accès du parent de l’élément au chemin d’accès spécifié. Si l’élément au chemin d’accès spécifié est la racine du magasin de données (il n’a donc pas de parent), cette méthode doit retourner le chemin d’accès racine.

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

### <a name="implementing-makepath"></a>Implémentation de MakePath

La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) joint un chemin d’accès parent spécifié et un chemin d’accès enfant spécifié pour créer un chemin d’accès interne au fournisseur (pour plus d’informations sur les types de chemins d’accès que les fournisseurs peuvent prendre en charge, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md). Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .

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

### <a name="implementing-normalizerelativepath"></a>Implémentation de NormalizeRelativePath

La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) prend `path` les `basepath` paramètres et, et retourne un chemin d’accès normalisé équivalent au `path` paramètre et relatif au `basepath` paramètre.

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

### <a name="implementing-moveitem"></a>Implémentation de MoveItem

La méthode [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) déplace un élément du chemin d’accès spécifié vers le chemin d’accès de destination spécifié. Le moteur PowerShell appelle cette méthode lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .

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

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur de conteneur](./writing-a-container-provider.md)

[Vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md)
