---
ms.date: 09/13/2016
ms.topic: reference
title: Fournisseur Windows PowerShell - Démarrage rapide
description: Fournisseur Windows PowerShell - Démarrage rapide
ms.openlocfilehash: f0fe0ad60e9d10efd505cda60af995c597226b92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664338"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="24a29-103">Fournisseur Windows PowerShell - Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="24a29-103">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="24a29-104">Cette rubrique explique comment créer un fournisseur Windows PowerShell qui dispose des fonctionnalités de base de la création d’un nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="24a29-104">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="24a29-105">Pour obtenir des informations générales sur les fournisseurs, consultez [vue d’ensemble du fournisseur Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="24a29-105">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="24a29-106">Pour obtenir des exemples de fournisseurs avec une fonctionnalité plus complète, consultez [exemples](./provider-samples.md)de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="24a29-106">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="24a29-107">Écriture d’un fournisseur de base</span><span class="sxs-lookup"><span data-stu-id="24a29-107">Writing a basic provider</span></span>

<span data-ttu-id="24a29-108">La fonctionnalité la plus basique d’un fournisseur Windows PowerShell consiste à créer et à supprimer des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="24a29-108">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="24a29-109">Dans cet exemple, nous implémentons les méthodes [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="24a29-109">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="24a29-110">Vous verrez également comment déclarer une classe de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="24a29-110">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="24a29-111">Lorsque vous écrivez un fournisseur, vous pouvez spécifier les lecteurs de lecteurs par défaut qui sont créés automatiquement lorsque le fournisseur est disponible.</span><span class="sxs-lookup"><span data-stu-id="24a29-111">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="24a29-112">Vous définissez également une méthode pour créer de nouveaux lecteurs qui utilisent ce fournisseur.</span><span class="sxs-lookup"><span data-stu-id="24a29-112">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="24a29-113">Les exemples fournis dans cette rubrique sont basés sur l’exemple [AccessDBProviderSample02](./accessdbprovidersample02.md) , qui fait partie d’un exemple plus complet qui représente une base de données Access en tant que lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24a29-113">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="24a29-114">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="24a29-114">Setting up the project</span></span>

<span data-ttu-id="24a29-115">Dans Visual Studio, créez un projet de bibliothèque de classes nommé AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="24a29-115">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="24a29-116">Effectuez les étapes suivantes pour configurer votre projet afin que Windows PowerShell démarre, et le fournisseur sera chargé dans la session, lorsque vous générerez et démarrerez votre projet.</span><span class="sxs-lookup"><span data-stu-id="24a29-116">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="24a29-117">Configurer le projet de fournisseur</span><span class="sxs-lookup"><span data-stu-id="24a29-117">Configure the provider project</span></span>

1. <span data-ttu-id="24a29-118">Ajoutez l’assembly System. Management. Automation en tant que référence à votre projet.</span><span class="sxs-lookup"><span data-stu-id="24a29-118">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="24a29-119">Cliquez sur **projet > propriétés AccessDBProviderSample > débogage**.</span><span class="sxs-lookup"><span data-stu-id="24a29-119">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="24a29-120">Dans **Démarrer le projet**, cliquez sur **Démarrer le programme externe**, puis accédez à l’exécutable Windows PowerShell (généralement c:\Windows\system32\WindowsPowerShell\v1.0 \\.powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="24a29-120">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="24a29-121">Sous **options de démarrage**, entrez ce qui suit dans la zone **arguments de ligne de commande** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="24a29-121">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="24a29-122">Déclaration de la classe de fournisseur</span><span class="sxs-lookup"><span data-stu-id="24a29-122">Declaring the provider class</span></span>

<span data-ttu-id="24a29-123">Notre fournisseur est dérivé de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="24a29-123">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="24a29-124">La plupart des fournisseurs qui fournissent des fonctionnalités réelles (accès et manipulation d’éléments, navigation dans le magasin de données et obtention et définition du contenu d’éléments) dérivent de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="24a29-124">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="24a29-125">En plus de spécifier que la classe dérive de [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), vous devez la décorer avec [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) , comme indiqué dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="24a29-125">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="24a29-126">Implémentation de les</span><span class="sxs-lookup"><span data-stu-id="24a29-126">Implementing NewDrive</span></span>

<span data-ttu-id="24a29-127">La méthode [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) est appelée par le moteur Windows PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) en spécifiant le nom de votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="24a29-127">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="24a29-128">Le paramètre PSDriveInfo est passé par le moteur Windows PowerShell et la méthode retourne le nouveau lecteur au moteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24a29-128">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="24a29-129">Cette méthode doit être déclarée dans la classe créée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="24a29-129">This method must be declared within the class created above.</span></span>

<span data-ttu-id="24a29-130">La méthode commence par vérifier que l’objet lecteur et la racine du lecteur qui ont été transmis existent, en retournant `null` si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="24a29-130">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="24a29-131">Il utilise ensuite un constructeur de la classe interne AccessDBPSDriveInfo pour créer un nouveau lecteur et une connexion à la base de données Access que le lecteur représente.</span><span class="sxs-lookup"><span data-stu-id="24a29-131">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="24a29-132">Voici la classe interne AccessDBPSDriveInfo qui inclut le constructeur utilisé pour créer un nouveau lecteur et contient les informations d’État du lecteur.</span><span class="sxs-lookup"><span data-stu-id="24a29-132">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="24a29-133">Implémentation de RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="24a29-133">Implementing RemoveDrive</span></span>

<span data-ttu-id="24a29-134">La méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) est appelée par le moteur Windows PowerShell lorsqu’un utilisateur appelle l’applet de [commande Microsoft. PowerShell. Commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) .</span><span class="sxs-lookup"><span data-stu-id="24a29-134">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="24a29-135">La méthode de ce fournisseur ferme la connexion à la base de données Access.</span><span class="sxs-lookup"><span data-stu-id="24a29-135">The method in this provider closes the connection to the Access database.</span></span>

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
