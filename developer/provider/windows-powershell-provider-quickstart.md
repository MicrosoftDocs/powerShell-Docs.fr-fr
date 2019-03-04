---
title: Guide de démarrage rapide de Windows PowerShell fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: ab78bcad301215bca9b5324bdb8de863899edec6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862145"
---
# <a name="windows-powershell-provider-quickstart"></a>Fournisseur Windows PowerShell - Démarrage rapide

Cette rubrique explique comment créer un fournisseur Windows PowerShell qui a des fonctionnalités de base de la création d’un nouveau lecteur. Pour obtenir des informations générales sur les fournisseurs, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md). Pour obtenir des exemples de fournisseurs de fonctionnalités plus complètes, consultez [exemples de fournisseurs](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Écriture d’un fournisseur de base

Les fonctionnalités de base d’un fournisseur Windows PowerShell consiste à créer et supprimer des lecteurs. Dans cet exemple, nous implémentons le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthodes de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Vous verrez également comment déclarer une classe de fournisseur.

Lorsque vous écrivez un fournisseur, vous pouvez spécifier par défaut lecteurs de disques qui sont créées automatiquement lorsque le fournisseur est disponible. Vous définissez également une méthode pour créer de nouveaux lecteurs qui utilisent ce fournisseur.

Les exemples fournis dans cette rubrique sont basés sur le [AccessDBProviderSample02](./accessdbprovidersample02.md) exemple, ce qui fait partie d’un exemple plus complet qui représente une base de données Access comme un lecteur Windows PowerShell.

### <a name="setting-up-the-project"></a>Configuration du projet

Dans Visual Studio, créez un projet de bibliothèque de classes nommé AccessDBProviderSample. Procédez comme suit pour configurer votre projet afin que Windows PowerShell démarre, et le fournisseur sera chargé dans la session, lorsque vous créez et démarrez votre projet.

##### <a name="configure-the-provider-project"></a>Configurer le projet de fournisseur

1. Ajoutez l’assembly System.Management.Automation en tant que référence à votre projet.

2. Cliquez sur **projet > Propriétés de AccessDBProviderSample > déboguer**. Dans **démarrer le projet**, cliquez sur **démarrer le programme externe**et accédez à l’exécutable de Windows PowerShell (généralement c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Sous **Options de démarrage**, entrez ce qui suit dans le **arguments de ligne de commande** zone : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Déclaration de la classe de fournisseur

Notre fournisseur dérive le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. La plupart des fournisseurs qui fournissent des fonctionnalités réelles (accéder au et manipuler des éléments, navigation dans le magasin de données et l’obtention et définition du contenu d’éléments) dérivent le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

En plus de spécifier que la classe dérive de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), vous devez décorer avec le [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) comme indiqué dans l’exemple.

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

### <a name="implementing-newdrive"></a>Implémentation NewDrive

Le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) méthode est appelée par le moteur Windows PowerShell quand un utilisateur appelle le [Microsoft.Powershell.Commands.New-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)applet de commande en spécifiant le nom de votre fournisseur. Le paramètre PSDriveInfo est transmis par le moteur Windows PowerShell, et la méthode retourne le nouveau lecteur pour le moteur Windows PowerShell. Cette méthode doit être déclarée au sein de la classe créée ci-dessus.

La méthode vérifie d’abord pour vous assurer que l’objet de lecteur et la racine du lecteur qui ont été passés dans existent, retournant `null` si un d’eux n’est pas le cas. Il utilise ensuite un constructeur de la classe interne AccessDBPSDriveInfo pour créer un nouveau lecteur et représente une connexion à la base de données Access, le lecteur.

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

Voici la classe interne AccessDBPSDriveInfo qui inclut le constructeur utilisé pour créer un nouveau lecteur et contient les informations d’état pour le lecteur.

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

### <a name="implementing-removedrive"></a>Implémentation RemoveDrive

Le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthode est appelée par le moteur Windows PowerShell quand un utilisateur appelle le [Microsoft.Powershell.Commands.Remove-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) applet de commande. La méthode dans ce fournisseur ferme la connexion à la base de données Access.

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