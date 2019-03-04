---
title: Création d’un fournisseur de lecteur PowerShell Windows | Microsoft Docs
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
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855795"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="12f7d-102">Création d’un fournisseur de lecteur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="12f7d-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="12f7d-103">Cette rubrique décrit comment créer un fournisseur de lecteur Windows PowerShell qui fournit un moyen pour accéder à un magasin de données via un lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12f7d-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="12f7d-104">Ce type de fournisseur est également appelé fournisseurs du lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12f7d-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="12f7d-105">Les lecteurs Windows PowerShell utilisées par le fournisseur fournissent les moyens de se connecter au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="12f7d-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="12f7d-106">Le fournisseur du lecteur Windows PowerShell décrit ici fournit l’accès à une base de données Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="12f7d-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="12f7d-107">Pour ce fournisseur, le lecteur Windows PowerShell représente la base de données (il est possible d’ajouter n’importe quel nombre de lecteurs à un fournisseur de lecteur), les conteneurs de niveau supérieur du lecteur représentent les tables dans la base de données et les éléments des conteneurs représentent les lignes dans les tables.</span><span class="sxs-lookup"><span data-stu-id="12f7d-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="12f7d-108">Voici une liste des sections dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="12f7d-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="12f7d-109">Si vous n’êtes pas familiarisé avec l’écriture d’un fournisseur de lecteur Windows PowerShell, lisez ces sections dans l’ordre où ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="12f7d-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="12f7d-110">Toutefois, si vous êtes familiarisé avec l’écriture d’un fournisseur de lecteur, accédez directement aux informations dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="12f7d-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="12f7d-111">Définition de la classe de fournisseur PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="12f7d-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="12f7d-112">Définition des fonctionnalités de Base</span><span class="sxs-lookup"><span data-stu-id="12f7d-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="12f7d-113">Création d’informations sur l’état du lecteur</span><span class="sxs-lookup"><span data-stu-id="12f7d-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="12f7d-114">Création d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="12f7d-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="12f7d-115">Attachement des paramètres dynamiques à NewDrive</span><span class="sxs-lookup"><span data-stu-id="12f7d-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="12f7d-116">Retrait d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="12f7d-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="12f7d-117">L’initialisation par défaut de lecteurs</span><span class="sxs-lookup"><span data-stu-id="12f7d-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="12f7d-118">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="12f7d-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="12f7d-119">Test du fournisseur de lecteur PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="12f7d-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="12f7d-120">Définition de la classe de fournisseur PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="12f7d-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="12f7d-121">Votre fournisseur du lecteur doit définir une classe .NET qui dérive de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base.</span><span class="sxs-lookup"><span data-stu-id="12f7d-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="12f7d-122">Voici la définition de classe pour ce fournisseur de lecteur :</span><span class="sxs-lookup"><span data-stu-id="12f7d-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="12f7d-123">Notez que dans cet exemple, le [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut spécifie un nom convivial pour le fournisseur et les capacités spécifiques de Windows PowerShell qui le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande.</span><span class="sxs-lookup"><span data-stu-id="12f7d-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="12f7d-124">Les valeurs possibles pour les fonctionnalités de fournisseur sont définies par le [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération.</span><span class="sxs-lookup"><span data-stu-id="12f7d-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="12f7d-125">Ce fournisseur de lecteur ne prennent pas en charge ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="12f7d-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="12f7d-126">Définition des fonctionnalités de Base</span><span class="sxs-lookup"><span data-stu-id="12f7d-126">Defining Base Functionality</span></span>

<span data-ttu-id="12f7d-127">Comme décrit dans [fournisseur Design Your Windows PowerShell](./designing-your-windows-powershell-provider.md), le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe dérive de la [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe de base qui définit les méthodes nécessaires pour initialiser et désinitialiser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="12f7d-128">Pour implémenter des fonctionnalités permettant d’ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur de PowerShell Windows base](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="12f7d-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="12f7d-129">Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité est fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12f7d-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="12f7d-130">Création d’informations sur l’état du lecteur</span><span class="sxs-lookup"><span data-stu-id="12f7d-130">Creating Drive State Information</span></span>

<span data-ttu-id="12f7d-131">Tous les fournisseurs Windows PowerShell sont considérées comme sans état, ce qui signifie que votre fournisseur du lecteur doit créer les informations d’état requises par le runtime Windows PowerShell quand il appelle votre fournisseur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="12f7d-132">Pour ce fournisseur du lecteur, les informations d’état incluent la connexion à la base de données est conservée en tant que partie des informations sur le lecteur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="12f7d-133">Voici le code qui montre comment ces informations sont stockées dans le [à savoir System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objet qui décrit le lecteur :</span><span class="sxs-lookup"><span data-stu-id="12f7d-133">Here is code that shows how this information is stored in the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="12f7d-134">Création d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="12f7d-134">Creating a Drive</span></span>

<span data-ttu-id="12f7d-135">Pour permettre au runtime de Windows PowerShell créer un lecteur, le fournisseur du lecteur doit implémenter le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12f7d-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="12f7d-136">Le code suivant montre l’implémentation de la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) méthode pour ce fournisseur de lecteur :</span><span class="sxs-lookup"><span data-stu-id="12f7d-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="12f7d-137">La substitution de cette méthode doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="12f7d-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="12f7d-138">Vérifiez que le [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membre existe et qu’une connexion au magasin de données peut être établie.</span><span class="sxs-lookup"><span data-stu-id="12f7d-138">Verify that the [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="12f7d-139">Créer un lecteur et de remplir le membre de la connexion, à l’appui de la `New-PSDrive` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="12f7d-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="12f7d-140">Valider la [à savoir System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objet pour le lecteur proposé.</span><span class="sxs-lookup"><span data-stu-id="12f7d-140">Validate the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="12f7d-141">Modifier le [à savoir System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) qui décrit le lecteur avec des performances requises ou des informations de la fiabilité de l’objet, ou fournir des données supplémentaires pour les appelants à l’aide du lecteur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-141">Modify the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="12f7d-142">Gérer les défaillances à l’aide de la [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) (méthode) et les renvoyer ensuite `null`.</span><span class="sxs-lookup"><span data-stu-id="12f7d-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="12f7d-143">Cette méthode retourne des informations de lecteur qui a été passées à la méthode ou une version spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="12f7d-144">Attachement des paramètres dynamiques à NewDrive</span><span class="sxs-lookup"><span data-stu-id="12f7d-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="12f7d-145">Le `New-PSDrive` applet de commande pris en charge par votre fournisseur de lecteur peut-être nécessiter des paramètres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="12f7d-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="12f7d-146">Pour attacher ces paramètres dynamiques à l’applet de commande, le fournisseur implémente la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12f7d-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="12f7d-147">Cette méthode retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet.</span><span class="sxs-lookup"><span data-stu-id="12f7d-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="12f7d-148">Ce fournisseur de lecteur ne remplace pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="12f7d-148">This drive provider does not override this method.</span></span> <span data-ttu-id="12f7d-149">Toutefois, le code suivant montre l’implémentation par défaut de cette méthode :</span><span class="sxs-lookup"><span data-stu-id="12f7d-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="12f7d-150">Retrait d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="12f7d-150">Removing a Drive</span></span>

<span data-ttu-id="12f7d-151">Pour fermer la connexion de base de données, le fournisseur du lecteur doit implémenter le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12f7d-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="12f7d-152">Cette méthode ferme la connexion sur le disque après le nettoyage de toutes les informations spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="12f7d-153">Le code suivant montre l’implémentation de la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthode pour ce fournisseur de lecteur :</span><span class="sxs-lookup"><span data-stu-id="12f7d-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="12f7d-154">Si le lecteur peut être supprimé, la méthode doit retourner les informations passées à la méthode via la `drive` paramètre.</span><span class="sxs-lookup"><span data-stu-id="12f7d-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="12f7d-155">Si le lecteur ne peut pas être supprimé, la méthode doit écrire une exception, puis renvoyer `null`.</span><span class="sxs-lookup"><span data-stu-id="12f7d-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="12f7d-156">Si votre fournisseur ne remplace pas cette méthode, l’implémentation par défaut de cette méthode retourne uniquement les informations de lecteur passées en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="12f7d-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="12f7d-157">L’initialisation par défaut de lecteurs</span><span class="sxs-lookup"><span data-stu-id="12f7d-157">Initializing Default Drives</span></span>

<span data-ttu-id="12f7d-158">Votre implémente de fournisseur de lecteur la [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) permet de monter des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="12f7d-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="12f7d-159">Par exemple, le fournisseur Active Directory peut-être monter un disque pour la valeur par défaut de contexte d’appellation si l’ordinateur est joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="12f7d-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="12f7d-160">Cette méthode retourne une collection d’informations de lecteur sur les lecteurs initialisés, ou une collection vide.</span><span class="sxs-lookup"><span data-stu-id="12f7d-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="12f7d-161">L’appel à cette méthode est effectué après les appels de runtime Windows PowerShell le [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode pour initialiser le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="12f7d-162">Ce fournisseur de lecteur ne remplace pas le [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12f7d-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="12f7d-163">Toutefois, le code suivant montre l’implémentation par défaut, qui retourne une collection vide lecteur :</span><span class="sxs-lookup"><span data-stu-id="12f7d-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="12f7d-164">Points à retenir sur l’implémentation InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="12f7d-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="12f7d-165">Tous les fournisseurs de lecteur doivent monter un lecteur racine pour aider l’utilisateur avec la fonctionnalité de découverte.</span><span class="sxs-lookup"><span data-stu-id="12f7d-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="12f7d-166">Le lecteur racine peut répertorier les emplacements qui servent de racines pour les autres lecteurs montés.</span><span class="sxs-lookup"><span data-stu-id="12f7d-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="12f7d-167">Par exemple, le fournisseur Active Directory peut créer un lecteur qui répertorie les contextes d’affectation de noms trouvés dans le `namingContext` attributs sur l’environnement de système distribué (DSE) racine.</span><span class="sxs-lookup"><span data-stu-id="12f7d-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="12f7d-168">Cela permet aux utilisateurs de découvrir les points de montage pour les autres lecteurs.</span><span class="sxs-lookup"><span data-stu-id="12f7d-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="12f7d-169">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="12f7d-169">Code Sample</span></span>

<span data-ttu-id="12f7d-170">Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="12f7d-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="12f7d-171">Test du fournisseur de lecteur PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="12f7d-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="12f7d-172">Lorsque votre fournisseur de Windows PowerShell a été enregistré avec Windows PowerShell, vous pouvez le tester en exécutant les applets de commande pris en charge sur la ligne de commande, y compris les applets de commande mises à disposition par dérivation.</span><span class="sxs-lookup"><span data-stu-id="12f7d-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="12f7d-173">Nous allons tester l’exemple de fournisseur de lecteur.</span><span class="sxs-lookup"><span data-stu-id="12f7d-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="12f7d-174">Exécutez le `Get-PSProvider` applet de commande pour récupérer la liste des fournisseurs pour vous assurer que le fournisseur du lecteur AccessDB est présent :</span><span class="sxs-lookup"><span data-stu-id="12f7d-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="12f7d-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="12f7d-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="12f7d-176">La sortie suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="12f7d-176">The following output appears:</span></span>

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

2. <span data-ttu-id="12f7d-177">Assurez-vous qu’un nom de serveur de base de données (DSN) existe pour la base de données en accédant à la **des Sources de données** partie de la **outils d’administration** du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="12f7d-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="12f7d-178">Dans le **DSN utilisateur** table, double-cliquez sur **base de données MS Access** et ajoutez le chemin d’accès de lecteur C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="12f7d-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="12f7d-179">Créer un nouveau lecteur à l’aide de l’exemple de fournisseur de lecteur :</span><span class="sxs-lookup"><span data-stu-id="12f7d-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="12f7d-180">**PS > Nouveau-psdrive-nom mydb-racine c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="12f7d-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="12f7d-181">La sortie suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="12f7d-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="12f7d-182">Valider la connexion.</span><span class="sxs-lookup"><span data-stu-id="12f7d-182">Validate the connection.</span></span> <span data-ttu-id="12f7d-183">Étant donné que la connexion est définie en tant que membre du lecteur, vous pouvez le vérifier à l’aide de l’applet de commande Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="12f7d-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="12f7d-184">L’utilisateur ne peut pas encore interagir avec le fournisseur en tant que lecteur, comme le fournisseur a besoin de fonctionnalités de conteneur pour cette interaction.</span><span class="sxs-lookup"><span data-stu-id="12f7d-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="12f7d-185">Pour plus d’informations, consultez [création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="12f7d-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="12f7d-186">**PS > (get-psdrive mydb) .connection**</span><span class="sxs-lookup"><span data-stu-id="12f7d-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="12f7d-187">La sortie suivante apparaît :</span><span class="sxs-lookup"><span data-stu-id="12f7d-187">The following output appears:</span></span>

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

5. <span data-ttu-id="12f7d-188">Retirez le lecteur et quitter l’interpréteur de commandes :</span><span class="sxs-lookup"><span data-stu-id="12f7d-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="12f7d-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="12f7d-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="12f7d-190">**PS > Quitter**</span><span class="sxs-lookup"><span data-stu-id="12f7d-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="12f7d-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12f7d-191">See Also</span></span>

[<span data-ttu-id="12f7d-192">Création de fournisseurs de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="12f7d-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="12f7d-193">Concevoir votre fournisseur de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="12f7d-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="12f7d-194">Création d’un fournisseur PowerShell de base Windows</span><span class="sxs-lookup"><span data-stu-id="12f7d-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)