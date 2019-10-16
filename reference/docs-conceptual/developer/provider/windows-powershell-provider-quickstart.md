---
title: Guide de démarrage rapide du fournisseur Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359918"
---
# <a name="windows-powershell-provider-quickstart"></a>Fournisseur Windows PowerShell - Démarrage rapide

Cette rubrique explique comment créer un fournisseur Windows PowerShell qui dispose des fonctionnalités de base de la création d’un nouveau lecteur. Pour obtenir des informations générales sur les fournisseurs, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md). Pour obtenir des exemples de fournisseurs avec une fonctionnalité plus complète, consultez [exemples](./provider-samples.md)de fournisseurs.

## <a name="writing-a-basic-provider"></a>Écriture d’un fournisseur de base

La fonctionnalité la plus basique d’un fournisseur Windows PowerShell consiste à créer et à supprimer des lecteurs. Dans cet exemple, nous implémentons les méthodes [System. Management. Automation. Provider. Drivecmdletprovider. les *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) de la [ Classe System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Vous verrez également comment déclarer une classe de fournisseur.

Lorsque vous écrivez un fournisseur, vous pouvez spécifier les lecteurs de lecteurs par défaut qui sont créés automatiquement lorsque le fournisseur est disponible. Vous définissez également une méthode pour créer de nouveaux lecteurs qui utilisent ce fournisseur.

Les exemples fournis dans cette rubrique sont basés sur l’exemple [AccessDBProviderSample02](./accessdbprovidersample02.md) , qui fait partie d’un exemple plus complet qui représente une base de données Access en tant que lecteur Windows PowerShell.

### <a name="setting-up-the-project"></a>Configuration du projet

Dans Visual Studio, créez un projet de bibliothèque de classes nommé AccessDBProviderSample. Effectuez les étapes suivantes pour configurer votre projet afin que Windows PowerShell démarre, et le fournisseur sera chargé dans la session, lorsque vous générerez et démarrerez votre projet.

##### <a name="configure-the-provider-project"></a>Configurer le projet de fournisseur

1. Ajoutez l’assembly System. Management. Automation en tant que référence à votre projet.

2. Cliquez sur **projet > propriétés AccessDBProviderSample > débogage**. Dans **Démarrer le projet**, cliquez sur **Démarrer le programme externe**, puis accédez à l’exécutable Windows PowerShell (généralement c:\windows\system32\windowspowershell\ v1.0\\.powershell.exe).

3. Sous **options de démarrage**, entrez ce qui suit dans la zone **arguments de ligne de commande** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Déclaration de la classe de fournisseur

Notre fournisseur est dérivé de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . La plupart des fournisseurs qui fournissent des fonctionnalités réelles (accès et manipulation d’éléments, navigation dans le magasin de données et obtention et définition du contenu d’éléments) dérivent de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

En plus de spécifier que la classe dérive de [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), vous devez la décorer avec [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) , comme indiqué dans l’exemple. .

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>Implémentation de les

La méthode [System. Management. Automation. Provider. Drivecmdletprovider. les *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) est appelée par le moteur Windows PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) en spécifiant le nom de votre moteur. Le paramètre PSDriveInfo est passé par le moteur Windows PowerShell et la méthode retourne le nouveau lecteur au moteur Windows PowerShell. Cette méthode doit être déclarée dans la classe créée ci-dessus.

La méthode commence par vérifier que l’objet lecteur et la racine du lecteur qui ont été transmis existent, en retournant `null` si l’un ou l’autre ne le fait pas. Il utilise ensuite un constructeur de la classe interne AccessDBPSDriveInfo pour créer un nouveau lecteur et une connexion à la base de données Access que le lecteur représente.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

Voici la classe interne AccessDBPSDriveInfo qui inclut le constructeur utilisé pour créer un nouveau lecteur et contient les informations d’État du lecteur.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>Implémentation de RemoveDrive

La méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) est appelée par le moteur Windows PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) . La méthode de ce fournisseur ferme la connexion à la base de données Access.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```