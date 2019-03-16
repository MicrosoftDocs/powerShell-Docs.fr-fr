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
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054915"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="cf865-102">Fournisseur Windows PowerShell - Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="cf865-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="cf865-103">Cette rubrique explique comment créer un fournisseur Windows PowerShell qui a des fonctionnalités de base de la création d’un nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="cf865-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="cf865-104">Pour obtenir des informations générales sur les fournisseurs, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf865-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="cf865-105">Pour obtenir des exemples de fournisseurs de fonctionnalités plus complètes, consultez [exemples de fournisseurs](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf865-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="cf865-106">Écriture d’un fournisseur de base</span><span class="sxs-lookup"><span data-stu-id="cf865-106">Writing a basic provider</span></span>

<span data-ttu-id="cf865-107">Les fonctionnalités de base d’un fournisseur Windows PowerShell consiste à créer et supprimer des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="cf865-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="cf865-108">Dans cet exemple, nous implémentons le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthodes de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="cf865-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="cf865-109">Vous verrez également comment déclarer une classe de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="cf865-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="cf865-110">Lorsque vous écrivez un fournisseur, vous pouvez spécifier par défaut lecteurs de disques qui sont créées automatiquement lorsque le fournisseur est disponible.</span><span class="sxs-lookup"><span data-stu-id="cf865-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="cf865-111">Vous définissez également une méthode pour créer de nouveaux lecteurs qui utilisent ce fournisseur.</span><span class="sxs-lookup"><span data-stu-id="cf865-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="cf865-112">Les exemples fournis dans cette rubrique sont basés sur le [AccessDBProviderSample02](./accessdbprovidersample02.md) exemple, ce qui fait partie d’un exemple plus complet qui représente une base de données Access comme un lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf865-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="cf865-113">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="cf865-113">Setting up the project</span></span>

<span data-ttu-id="cf865-114">Dans Visual Studio, créez un projet de bibliothèque de classes nommé AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="cf865-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="cf865-115">Procédez comme suit pour configurer votre projet afin que Windows PowerShell démarre, et le fournisseur sera chargé dans la session, lorsque vous créez et démarrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="cf865-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="cf865-116">Configurer le projet de fournisseur</span><span class="sxs-lookup"><span data-stu-id="cf865-116">Configure the provider project</span></span>

1. <span data-ttu-id="cf865-117">Ajoutez l’assembly System.Management.Automation en tant que référence à votre projet.</span><span class="sxs-lookup"><span data-stu-id="cf865-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="cf865-118">Cliquez sur **projet > Propriétés de AccessDBProviderSample > déboguer**.</span><span class="sxs-lookup"><span data-stu-id="cf865-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="cf865-119">Dans **démarrer le projet**, cliquez sur **démarrer le programme externe**et accédez à l’exécutable de Windows PowerShell (généralement c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="cf865-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="cf865-120">Sous **Options de démarrage**, entrez ce qui suit dans le **arguments de ligne de commande** zone : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="cf865-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="cf865-121">Déclaration de la classe de fournisseur</span><span class="sxs-lookup"><span data-stu-id="cf865-121">Declaring the provider class</span></span>

<span data-ttu-id="cf865-122">Notre fournisseur dérive le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="cf865-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="cf865-123">La plupart des fournisseurs qui fournissent des fonctionnalités réelles (accéder au et manipuler des éléments, navigation dans le magasin de données et l’obtention et définition du contenu d’éléments) dérivent le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="cf865-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="cf865-124">En plus de spécifier que la classe dérive de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), vous devez décorer avec le [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) comme indiqué dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="cf865-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="cf865-125">Implémentation NewDrive</span><span class="sxs-lookup"><span data-stu-id="cf865-125">Implementing NewDrive</span></span>

<span data-ttu-id="cf865-126">Le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) méthode est appelée par le moteur Windows PowerShell quand un utilisateur appelle le [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)applet de commande en spécifiant le nom de votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="cf865-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="cf865-127">Le paramètre PSDriveInfo est transmis par le moteur Windows PowerShell, et la méthode retourne le nouveau lecteur pour le moteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf865-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="cf865-128">Cette méthode doit être déclarée au sein de la classe créée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="cf865-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="cf865-129">La méthode vérifie d’abord pour vous assurer que l’objet de lecteur et la racine du lecteur qui ont été passés dans existent, retournant `null` si un d’eux n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="cf865-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="cf865-130">Il utilise ensuite un constructeur de la classe interne AccessDBPSDriveInfo pour créer un nouveau lecteur et représente une connexion à la base de données Access, le lecteur.</span><span class="sxs-lookup"><span data-stu-id="cf865-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="cf865-131">Voici la classe interne AccessDBPSDriveInfo qui inclut le constructeur utilisé pour créer un nouveau lecteur et contient les informations d’état pour le lecteur.</span><span class="sxs-lookup"><span data-stu-id="cf865-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="cf865-132">Implémentation RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="cf865-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="cf865-133">Le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthode est appelée par le moteur Windows PowerShell quand un utilisateur appelle le [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cf865-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="cf865-134">La méthode dans ce fournisseur ferme la connexion à la base de données Access.</span><span class="sxs-lookup"><span data-stu-id="cf865-134">The method in this provider closes the connection to the Access database.</span></span>

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