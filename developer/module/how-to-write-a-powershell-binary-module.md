---
title: Comment écrire un Module PowerShell binaire | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856485"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="67262-102">Guide pratique pour écrire un module binaire PowerShell</span><span class="sxs-lookup"><span data-stu-id="67262-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="67262-103">Un module binaire peut être n’importe quel assembly (.dll) qui contient des classes de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="67262-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="67262-104">Par défaut, toutes les applets de commande dans l’assembly sont importées lorsque le module binaire est importé.</span><span class="sxs-lookup"><span data-stu-id="67262-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="67262-105">Toutefois, vous pouvez limiter les applets de commande sont importées en créant un manifeste de module dont le module racine est l’assembly.</span><span class="sxs-lookup"><span data-stu-id="67262-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="67262-106">(Par exemple, la clé de CmdletsToExport du manifeste peut servir à exporter uniquement les applets de commande qui sont nécessaires.) En outre, un module binaire peut contenir des fichiers supplémentaires, une structure de répertoires et autres éléments d’information de gestion utiles qu’une seule applet de commande ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="67262-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="67262-107">La procédure suivante décrit comment créer et installer un module binaire de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67262-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="67262-108">Comment créer et installer un module binaire de PowerShell</span><span class="sxs-lookup"><span data-stu-id="67262-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="67262-109">Créer une solution PowerShell binaire (comme une applet de commande écrite C#), avec les capacités de votre choix et vous assurer qu’elle s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="67262-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="67262-110">À partir du point de vue du code, le cœur d’un module binaire est simplement un assembly de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="67262-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="67262-111">En fait, PowerShell traitent un assembly de l’applet de commande unique en tant que module, en termes de chargement et déchargement, sans aucun effort supplémentaire part du développeur.</span><span class="sxs-lookup"><span data-stu-id="67262-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="67262-112">Pour plus d’informations sur l’écriture d’une applet de commande, consultez [écrire une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="67262-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="67262-113">Si nécessaire, créez le reste de votre solution : (applets de commande supplémentaires, des fichiers XML et ainsi de suite) et les décrire avec un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="67262-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="67262-114">En plus de décrire les assemblys de l’applet de commande dans votre solution, un manifeste de module peut décrire comment vous souhaitez que votre module exportées et importées, quelles applets de commande sera exposée, et ce qui passe des fichiers supplémentaires dans le module.</span><span class="sxs-lookup"><span data-stu-id="67262-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span> <span data-ttu-id="67262-115">Comme indiqué précédemment Toutefois, PowerShell peut traiter une applet de commande binaire comme un module sans aucun effort supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="67262-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span> <span data-ttu-id="67262-116">Par conséquent, un manifeste de module est utile principalement pour la combinaison de plusieurs fichiers dans un package unique, ou pour contrôler explicitement la publication pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="67262-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span> <span data-ttu-id="67262-117">Pour plus d’informations, consultez [comment écrire un manifeste de Module PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span><span class="sxs-lookup"><span data-stu-id="67262-117">For more information, see [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

   <span data-ttu-id="67262-118">Le code suivant est extrêmement simple C# bloc de code qui contient les trois applets de commande dans le même fichier peut être utilisé en tant que module.</span><span class="sxs-lookup"><span data-stu-id="67262-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="67262-119">Empaqueter votre solution et enregistrer le package vers un endroit quelconque dans le chemin d’accès du module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67262-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="67262-120">Le `PSModulePath` variable d’environnement globale décrit les chemins d’accès par défaut que PowerShell utilisera pour localiser votre module.</span><span class="sxs-lookup"><span data-stu-id="67262-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="67262-121">Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="67262-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="67262-122">Si vous n’utilisez pas les chemins d’accès par défaut, vous devez déclarer explicitement l’emplacement de votre module pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="67262-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="67262-123">Veillez à créer un dossier pour enregistrer votre module, vous pouvez avoir besoin du dossier pour stocker plusieurs assemblys et les fichiers de votre solution.</span><span class="sxs-lookup"><span data-stu-id="67262-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="67262-124">Notez que techniquement il est inutile d’installer votre module de n’importe où sur le `PSModulePath` -ce sont simplement les emplacements par défaut qui recherche pour votre module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67262-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="67262-125">Toutefois, il est considéré comme bonne pratique consiste à le faire, sauf si vous avez une bonne raison pour le stockage de votre module vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="67262-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="67262-126">Pour plus d’informations, consultez [installation d’un PowerShell Module](./installing-a-powershell-module.md) et [modifier le chemin d’Installation du Module PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="67262-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="67262-127">Importer le module PowerShell avec un appel à [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="67262-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="67262-128">L’appel à [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) chargera votre module dans la mémoire active.</span><span class="sxs-lookup"><span data-stu-id="67262-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="67262-129">Si vous utilisez PowerShell 3.0 ou version ultérieure, appelant simplement le nom de votre module de code est également importer Pour plus d’informations, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="67262-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="67262-130">Importation des assemblys Snap-in en tant que Modules</span><span class="sxs-lookup"><span data-stu-id="67262-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="67262-131">Applets de commande et les fournisseurs qui existent dans le composant logiciel enfichable dans les assemblys peuvent être chargés en tant que modules binaires.</span><span class="sxs-lookup"><span data-stu-id="67262-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="67262-132">Lorsque les assemblys sont chargés en tant que modules binaires, les applets de commande et les fournisseurs dans le composant logiciel enfichable sont disponibles à l’utilisateur, mais la classe snap-in dans l’assembly est ignorée, et le composant logiciel enfichable n’est pas inscrit.</span><span class="sxs-lookup"><span data-stu-id="67262-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="67262-133">Par conséquent, les applets de commande enfichable fourni par Windows PowerShell ne peut pas détecter le composant logiciel enfichable même si les fournisseurs et applets de commande sont disponibles à la session.</span><span class="sxs-lookup"><span data-stu-id="67262-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="67262-134">En outre, les fichiers de mise en forme ou de types qui sont référencés par le composant logiciel enfichable ne peut pas être importés dans le cadre d’un module binaire.</span><span class="sxs-lookup"><span data-stu-id="67262-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span> <span data-ttu-id="67262-135">Pour importer les fichiers de mise en forme et de types, vous devez créer un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="67262-135">To import the formatting and types files you must create a module manifest.</span></span> <span data-ttu-id="67262-136">Consultez, [comment écrire un manifeste de Module PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span><span class="sxs-lookup"><span data-stu-id="67262-136">See, [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

## <a name="see-also"></a><span data-ttu-id="67262-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67262-137">See Also</span></span>

[<span data-ttu-id="67262-138">Écrire un Module PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="67262-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
