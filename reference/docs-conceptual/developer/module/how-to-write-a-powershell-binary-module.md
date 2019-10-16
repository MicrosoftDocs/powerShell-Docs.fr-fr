---
title: Comment écrire un module binaire PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367118"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="b079a-102">Guide pratique pour écrire un module binaire PowerShell</span><span class="sxs-lookup"><span data-stu-id="b079a-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="b079a-103">Un module binaire peut être n’importe quel assembly (. dll) qui contient des classes d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b079a-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="b079a-104">Par défaut, toutes les applets de commande de l’assembly sont importées lors de l’importation du module binaire.</span><span class="sxs-lookup"><span data-stu-id="b079a-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="b079a-105">Toutefois, vous pouvez restreindre les applets de commande importées en créant un manifeste de module dont le module racine est l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b079a-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="b079a-106">(Par exemple, la clé CmdletsToExport du manifeste peut être utilisée pour exporter uniquement les applets de commande nécessaires.) En outre, un module binaire peut contenir des fichiers supplémentaires, une structure de répertoires et d’autres éléments d’informations de gestion utiles qu’une applet de commande unique ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="b079a-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="b079a-107">La procédure suivante décrit comment créer et installer un module binaire PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b079a-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="b079a-108">Comment créer et installer un module binaire PowerShell</span><span class="sxs-lookup"><span data-stu-id="b079a-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="b079a-109">Créez une solution PowerShell binaire (telle qu’une applet de commande C#écrite dans), avec les fonctionnalités dont vous avez besoin et assurez-vous qu’elle s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="b079a-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="b079a-110">Du point de vue du code, le cœur d’un module binaire est simplement un assembly d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b079a-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="b079a-111">En fait, PowerShell traitera un assembly d’applet de commande unique comme un module, en termes de chargement et de déchargement, sans effort supplémentaire de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="b079a-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="b079a-112">Pour plus d’informations sur l’écriture d’une applet de commande, consultez [écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="b079a-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="b079a-113">Si nécessaire, créez le reste de votre solution : (applets de commande supplémentaires, fichiers XML, etc.) et décrivez-les à l’aide d’un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="b079a-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="b079a-114">En plus de décrire les assemblys d’applet de commande dans votre solution, un manifeste de module peut décrire comment vous souhaitez exporter et importer votre module, les applets de commande exposées et les fichiers supplémentaires qui seront insérés dans le module.</span><span class="sxs-lookup"><span data-stu-id="b079a-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="b079a-115">Comme indiqué précédemment, PowerShell peut traiter une applet de commande binaire comme un module sans effort supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b079a-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="b079a-116">Par conséquent, un manifeste de module est utile principalement pour la combinaison de plusieurs fichiers dans un package unique, ou pour le contrôle explicite de la publication pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="b079a-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="b079a-117">Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b079a-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="b079a-118">Le code suivant est un bloc de C# code extrêmement simple qui contient trois applets de commande dans le même fichier qui peuvent être utilisées en tant que module.</span><span class="sxs-lookup"><span data-stu-id="b079a-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="b079a-119">Empaquetez votre solution et enregistrez le package dans un chemin d’accès au module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b079a-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="b079a-120">La variable d’environnement global `PSModulePath` décrit les chemins d’accès par défaut que PowerShell utilisera pour localiser votre module.</span><span class="sxs-lookup"><span data-stu-id="b079a-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="b079a-121">Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="b079a-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="b079a-122">Si vous n’utilisez pas les chemins d’accès par défaut, vous devrez indiquer explicitement l’emplacement de votre module lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="b079a-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="b079a-123">Veillez à créer un dossier pour enregistrer votre module dans, car vous aurez peut-être besoin du dossier pour stocker plusieurs assemblys et fichiers pour votre solution.</span><span class="sxs-lookup"><span data-stu-id="b079a-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="b079a-124">Notez que techniquement, vous n’avez pas besoin d’installer votre module n’importe où sur le `PSModulePath` : il s’agit simplement des emplacements par défaut que PowerShell recherchera pour votre module.</span><span class="sxs-lookup"><span data-stu-id="b079a-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="b079a-125">Toutefois, il est recommandé de le faire, sauf si vous avez une bonne raison de stocker votre module ailleurs.</span><span class="sxs-lookup"><span data-stu-id="b079a-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="b079a-126">Pour plus d’informations, consultez [installation d’un module PowerShell](./installing-a-powershell-module.md) et [modification du chemin d’installation du module PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="b079a-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="b079a-127">Importez votre module dans PowerShell avec un appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="b079a-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="b079a-128">L’appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) chargera votre module dans la mémoire active.</span><span class="sxs-lookup"><span data-stu-id="b079a-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="b079a-129">Si vous utilisez PowerShell 3,0 et versions ultérieures, il vous suffit d’appeler le nom de votre module dans le code pour l’importer également. Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="b079a-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="b079a-130">Importation d’assemblys de composant logiciel enfichable en tant que modules</span><span class="sxs-lookup"><span data-stu-id="b079a-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="b079a-131">Les applets de commande et les fournisseurs qui existent dans les assemblys de composant logiciel enfichable peuvent être chargés en tant que modules binaires.</span><span class="sxs-lookup"><span data-stu-id="b079a-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="b079a-132">Lorsque les assemblys du composant logiciel enfichable sont chargés en tant que modules binaires, les applets de commande et les fournisseurs du composant logiciel enfichable sont disponibles pour l’utilisateur, mais la classe de composant logiciel enfichable de l’assembly est ignorée et le composant logiciel enfichable n’est pas inscrit.</span><span class="sxs-lookup"><span data-stu-id="b079a-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="b079a-133">Par conséquent, les applets de commande du composant logiciel enfichable fournies par Windows PowerShell ne peuvent pas détecter le composant logiciel enfichable, même si les applets de commande et les fournisseurs sont disponibles pour la session.</span><span class="sxs-lookup"><span data-stu-id="b079a-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="b079a-134">En outre, les fichiers de mise en forme ou de types référencés par le composant logiciel enfichable ne peuvent pas être importés dans le cadre d’un module binaire.</span><span class="sxs-lookup"><span data-stu-id="b079a-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="b079a-135">Pour importer les fichiers de mise en forme et de types, vous devez créer un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="b079a-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="b079a-136">Consultez [Comment écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b079a-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b079a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b079a-137">See Also</span></span>

[<span data-ttu-id="b079a-138">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b079a-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
