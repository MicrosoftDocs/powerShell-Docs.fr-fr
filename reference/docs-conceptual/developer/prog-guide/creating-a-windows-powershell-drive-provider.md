---
title: Création d’un fournisseur de lecteurs Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366828"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="78c55-102">Création d’un fournisseur de lecteur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78c55-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="78c55-103">Cette rubrique explique comment créer un fournisseur de lecteurs Windows PowerShell qui fournit un moyen d’accéder à un magasin de données via un lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78c55-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="78c55-104">Ce type de fournisseur est également appelé fournisseurs de lecteurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78c55-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="78c55-105">Les lecteurs Windows PowerShell utilisés par le fournisseur permettent de se connecter au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="78c55-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="78c55-106">Le fournisseur de lecteur Windows PowerShell décrit ici permet d’accéder à une base de données Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="78c55-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="78c55-107">Pour ce fournisseur, le lecteur Windows PowerShell représente la base de données (il est possible d’ajouter un nombre quelconque de lecteurs à un fournisseur de lecteur), les conteneurs de niveau supérieur du lecteur représentent les tables de la base de données, et les éléments des conteneurs représentent les lignes dans tables.</span><span class="sxs-lookup"><span data-stu-id="78c55-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="78c55-108">Définition de la classe de fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78c55-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="78c55-109">Votre fournisseur de lecteurs doit définir une classe .NET qui dérive de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="78c55-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="78c55-110">Voici la définition de classe pour ce fournisseur de lecteurs :</span><span class="sxs-lookup"><span data-stu-id="78c55-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="78c55-111">Notez que dans cet exemple, l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) spécifie un nom convivial pour le fournisseur et les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose à Windows Runtime PowerShell pendant le traitement des commandes.</span><span class="sxs-lookup"><span data-stu-id="78c55-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="78c55-112">Les valeurs possibles pour les fonctionnalités du fournisseur sont définies par l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) .</span><span class="sxs-lookup"><span data-stu-id="78c55-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="78c55-113">Ce fournisseur de lecteurs ne prend en charge aucune de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="78c55-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="78c55-114">Définition des fonctionnalités de base</span><span class="sxs-lookup"><span data-stu-id="78c55-114">Defining Base Functionality</span></span>

<span data-ttu-id="78c55-115">Comme décrit dans [concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) dérive de la classe de base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) qui définit les méthodes nécessaires pour initialiser et désinitialiser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="78c55-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="78c55-116">Pour implémenter les fonctionnalités d’ajout d’informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="78c55-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="78c55-117">Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78c55-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="78c55-118">Création d’informations sur l’état du lecteur</span><span class="sxs-lookup"><span data-stu-id="78c55-118">Creating Drive State Information</span></span>

<span data-ttu-id="78c55-119">Tous les fournisseurs Windows PowerShell sont considérés comme sans État, ce qui signifie que le fournisseur de votre lecteur doit créer les informations d’État requises par le runtime Windows PowerShell lorsqu’il appelle votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="78c55-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="78c55-120">Pour ce fournisseur de lecteur, les informations d’État incluent la connexion à la base de données qui est conservée dans le cadre des informations sur le lecteur.</span><span class="sxs-lookup"><span data-stu-id="78c55-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="78c55-121">Voici le code qui montre comment ces informations sont stockées dans l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) qui décrit le lecteur :</span><span class="sxs-lookup"><span data-stu-id="78c55-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="78c55-122">Création d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="78c55-122">Creating a Drive</span></span>

<span data-ttu-id="78c55-123">Pour autoriser le runtime Windows PowerShell à créer un lecteur, le fournisseur de lecteur doit implémenter la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) .</span><span class="sxs-lookup"><span data-stu-id="78c55-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="78c55-124">Le code suivant illustre l’implémentation de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) pour ce fournisseur de lecteurs :</span><span class="sxs-lookup"><span data-stu-id="78c55-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="78c55-125">Votre remplacement de cette méthode doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="78c55-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="78c55-126">Vérifiez que le membre [System. Management. Automation. PSDriveinfo. root \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) existe et qu’une connexion au magasin de données peut être établie.</span><span class="sxs-lookup"><span data-stu-id="78c55-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="78c55-127">Créez un lecteur et renseignez le membre de la connexion, à la prise en charge de l’applet de commande `New-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="78c55-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="78c55-128">Validez l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) pour le lecteur proposé.</span><span class="sxs-lookup"><span data-stu-id="78c55-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="78c55-129">Modifiez l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) qui décrit le lecteur avec les informations de performances ou de fiabilité requises, ou fournissez des données supplémentaires aux appelants à l’aide du lecteur.</span><span class="sxs-lookup"><span data-stu-id="78c55-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="78c55-130">Gérez les échecs à l’aide de la méthode [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) , puis retournez `null`.</span><span class="sxs-lookup"><span data-stu-id="78c55-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="78c55-131">Cette méthode retourne soit les informations de lecteur qui ont été passées à la méthode, soit une version spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="78c55-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="78c55-132">Attachement de paramètres dynamiques à les</span><span class="sxs-lookup"><span data-stu-id="78c55-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="78c55-133">L’applet de commande `New-PSDrive` prise en charge par votre fournisseur de lecteurs peut nécessiter des paramètres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="78c55-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="78c55-134">Pour attacher ces paramètres dynamiques à l’applet de commande, le fournisseur implémente la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="78c55-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="78c55-135">Cette méthode retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .</span><span class="sxs-lookup"><span data-stu-id="78c55-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="78c55-136">Ce fournisseur de lecteurs ne remplace pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="78c55-136">This drive provider does not override this method.</span></span> <span data-ttu-id="78c55-137">Toutefois, le code suivant illustre l’implémentation par défaut de cette méthode :</span><span class="sxs-lookup"><span data-stu-id="78c55-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="78c55-138">Suppression d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="78c55-138">Removing a Drive</span></span>

<span data-ttu-id="78c55-139">Pour fermer la connexion à la base de données, le fournisseur de lecteur doit implémenter la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .</span><span class="sxs-lookup"><span data-stu-id="78c55-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="78c55-140">Cette méthode ferme la connexion au lecteur après le nettoyage des informations spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="78c55-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="78c55-141">Le code suivant illustre l’implémentation de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour ce fournisseur de lecteurs :</span><span class="sxs-lookup"><span data-stu-id="78c55-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="78c55-142">Si le lecteur peut être supprimé, la méthode doit retourner les informations transmises à la méthode par le biais du paramètre `drive`.</span><span class="sxs-lookup"><span data-stu-id="78c55-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="78c55-143">Si le lecteur ne peut pas être supprimé, la méthode doit écrire une exception, puis retourner `null`.</span><span class="sxs-lookup"><span data-stu-id="78c55-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="78c55-144">Si votre fournisseur ne remplace pas cette méthode, l’implémentation par défaut de cette méthode retourne simplement les informations de lecteur passées comme entrée.</span><span class="sxs-lookup"><span data-stu-id="78c55-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="78c55-145">Initialisation des lecteurs par défaut</span><span class="sxs-lookup"><span data-stu-id="78c55-145">Initializing Default Drives</span></span>

<span data-ttu-id="78c55-146">Votre fournisseur de lecteur implémente la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) pour monter des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="78c55-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="78c55-147">Par exemple, le fournisseur de Active Directory peut monter un lecteur pour le contexte d’appellation par défaut si l’ordinateur est joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="78c55-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="78c55-148">Cette méthode retourne une collection d’informations sur les lecteurs initialisés, ou une collection vide.</span><span class="sxs-lookup"><span data-stu-id="78c55-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="78c55-149">L’appel à cette méthode est effectué après que le runtime Windows PowerShell a appelé la méthode [System. Management. Automation. Provider. Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) pour initialiser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="78c55-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="78c55-150">Ce fournisseur de lecteurs ne remplace pas la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) .</span><span class="sxs-lookup"><span data-stu-id="78c55-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="78c55-151">Toutefois, le code suivant montre l’implémentation par défaut, qui retourne une collection de lecteurs vide :</span><span class="sxs-lookup"><span data-stu-id="78c55-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="78c55-152">Points à retenir concernant l’implémentation de InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="78c55-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="78c55-153">Tous les fournisseurs de lecteurs doivent monter un lecteur racine pour aider l’utilisateur à se découvrir.</span><span class="sxs-lookup"><span data-stu-id="78c55-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="78c55-154">Le lecteur racine peut répertorier les emplacements qui servent de racines pour d’autres lecteurs montés.</span><span class="sxs-lookup"><span data-stu-id="78c55-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="78c55-155">Par exemple, le fournisseur de Active Directory peut créer un lecteur qui répertorie les contextes d’attribution de noms trouvés dans les attributs `namingContext` sur l’environnement de système distribué (DSE) racine.</span><span class="sxs-lookup"><span data-stu-id="78c55-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="78c55-156">Cela permet aux utilisateurs de découvrir des points de montage pour d’autres lecteurs.</span><span class="sxs-lookup"><span data-stu-id="78c55-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="78c55-157">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="78c55-157">Code Sample</span></span>

<span data-ttu-id="78c55-158">Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="78c55-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="78c55-159">Test du fournisseur de lecteurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78c55-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="78c55-160">Lorsque votre fournisseur Windows PowerShell a été inscrit auprès de Windows PowerShell, vous pouvez le tester en exécutant les applets de commande prises en charge sur la ligne de commande, y compris les applets de commande rendues disponibles par dérivation.</span><span class="sxs-lookup"><span data-stu-id="78c55-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="78c55-161">Nous allons tester l’exemple de fournisseur de lecteur.</span><span class="sxs-lookup"><span data-stu-id="78c55-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="78c55-162">Exécutez l’applet de commande `Get-PSProvider` pour récupérer la liste des fournisseurs afin de vérifier que le fournisseur de lecteurs AccessDB est présent :</span><span class="sxs-lookup"><span data-stu-id="78c55-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="78c55-163">**@No__t de > PS-1**</span><span class="sxs-lookup"><span data-stu-id="78c55-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="78c55-164">La sortie suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="78c55-164">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="78c55-165">Assurez-vous qu’un nom de serveur de base de données existe pour la base de données en accédant à la partie **sources de données** des **Outils d’administration** du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="78c55-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="78c55-166">Dans la table **DSN utilisateur** , double-cliquez sur **base de données MS Access** et ajoutez le chemin d’accès au lecteur C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="78c55-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="78c55-167">Créez un lecteur à l’aide de l’exemple de fournisseur de lecteur :</span><span class="sxs-lookup"><span data-stu-id="78c55-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="78c55-168">**PS > New-PSDrive-Name MyDB-root c:\ps\northwind.mdb-PSProvider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="78c55-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="78c55-169">La sortie suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="78c55-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="78c55-170">Validez la connexion.</span><span class="sxs-lookup"><span data-stu-id="78c55-170">Validate the connection.</span></span> <span data-ttu-id="78c55-171">Étant donné que la connexion est définie en tant que membre du lecteur, vous pouvez la vérifier à l’aide de l’applet de commande PDDrive.</span><span class="sxs-lookup"><span data-stu-id="78c55-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="78c55-172">L’utilisateur ne peut pas encore interagir avec le fournisseur en tant que lecteur, car le fournisseur a besoin de la fonctionnalité de conteneur pour cette interaction.</span><span class="sxs-lookup"><span data-stu-id="78c55-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="78c55-173">Pour plus d’informations, consultez [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="78c55-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="78c55-174">**> PS (obten-PSDrive MyDB). connexion**</span><span class="sxs-lookup"><span data-stu-id="78c55-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="78c55-175">La sortie suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="78c55-175">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="78c55-176">Retirez le lecteur et quittez l’interpréteur de commandes :</span><span class="sxs-lookup"><span data-stu-id="78c55-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="78c55-177">**Bloc de > PS-Remove-PSDrive MyDB**</span><span class="sxs-lookup"><span data-stu-id="78c55-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="78c55-178">**Sortie de la > PS**</span><span class="sxs-lookup"><span data-stu-id="78c55-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="78c55-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78c55-179">See Also</span></span>

[<span data-ttu-id="78c55-180">Création de fournisseurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78c55-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="78c55-181">Concevoir votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="78c55-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="78c55-182">Création d’un fournisseur Windows PowerShell de base</span><span class="sxs-lookup"><span data-stu-id="78c55-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)