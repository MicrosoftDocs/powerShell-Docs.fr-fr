---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour écrire un module binaire PowerShell
description: Guide pratique pour écrire un module binaire PowerShell
ms.openlocfilehash: 1d5cea474ac418f78cc782360b7c23b7614d6669
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663073"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="c3b6b-103">Guide pratique pour écrire un module binaire PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3b6b-103">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="c3b6b-104">Un module binaire peut être n’importe quel assembly (. dll) qui contient des classes d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-104">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="c3b6b-105">Par défaut, toutes les applets de commande de l’assembly sont importées lors de l’importation du module binaire.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-105">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="c3b6b-106">Toutefois, vous pouvez restreindre les applets de commande importées en créant un manifeste de module dont le module racine est l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-106">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="c3b6b-107">(Par exemple, la clé CmdletsToExport du manifeste peut être utilisée pour exporter uniquement les applets de commande nécessaires.) En outre, un module binaire peut contenir des fichiers supplémentaires, une structure de répertoires et d’autres éléments d’informations de gestion utiles qu’une applet de commande unique ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-107">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="c3b6b-108">La procédure suivante décrit comment créer et installer un module binaire PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-108">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="c3b6b-109">Comment créer et installer un module binaire PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3b6b-109">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="c3b6b-110">Créez une solution PowerShell binaire (telle qu’une applet de commande écrite en C#), avec les fonctionnalités dont vous avez besoin et assurez-vous qu’elle s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-110">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="c3b6b-111">Du point de vue du code, le cœur d’un module binaire est simplement un assembly d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-111">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="c3b6b-112">En fait, PowerShell traitera un assembly d’applet de commande unique comme un module, en termes de chargement et de déchargement, sans effort supplémentaire de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-112">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="c3b6b-113">Pour plus d’informations sur l’écriture d’une applet de commande, consultez [écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="c3b6b-113">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="c3b6b-114">Si nécessaire, créez le reste de votre solution : (applets de commande supplémentaires, fichiers XML, etc.) et décrivez-les à l’aide d’un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-114">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="c3b6b-115">En plus de décrire les assemblys d’applet de commande dans votre solution, un manifeste de module peut décrire comment vous souhaitez exporter et importer votre module, les applets de commande exposées et les fichiers supplémentaires qui seront insérés dans le module.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-115">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="c3b6b-116">Comme indiqué précédemment, PowerShell peut traiter une applet de commande binaire comme un module sans effort supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-116">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="c3b6b-117">Par conséquent, un manifeste de module est utile principalement pour la combinaison de plusieurs fichiers dans un package unique, ou pour le contrôle explicite de la publication pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-117">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="c3b6b-118">Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="c3b6b-118">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="c3b6b-119">Le code suivant est un bloc de code C# extrêmement simple qui contient trois applets de commande dans le même fichier qui peuvent être utilisées en tant que module.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-119">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="c3b6b-120">Empaquetez votre solution et enregistrez le package dans un chemin d’accès au module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-120">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="c3b6b-121">La `PSModulePath` variable d’environnement globale décrit les chemins d’accès par défaut que PowerShell utilisera pour localiser votre module.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-121">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="c3b6b-122">Par exemple, un chemin d’accès commun pour enregistrer un module sur un système est `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` .</span><span class="sxs-lookup"><span data-stu-id="c3b6b-122">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="c3b6b-123">Si vous n’utilisez pas les chemins d’accès par défaut, vous devrez indiquer explicitement l’emplacement de votre module lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-123">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="c3b6b-124">Veillez à créer un dossier pour enregistrer votre module dans, car vous aurez peut-être besoin du dossier pour stocker plusieurs assemblys et fichiers pour votre solution.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-124">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="c3b6b-125">Notez que techniquement, vous n’avez pas besoin d’installer votre module à l’emplacement de votre choix `PSModulePath` : il s’agit simplement des emplacements par défaut que PowerShell recherchera pour votre module.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-125">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="c3b6b-126">Toutefois, il est recommandé de le faire, sauf si vous avez une bonne raison de stocker votre module ailleurs.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-126">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="c3b6b-127">Pour plus d’informations, consultez [installation d’un module PowerShell](./installing-a-powershell-module.md) et [modification du chemin d’installation du module PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="c3b6b-127">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="c3b6b-128">Importez votre module dans PowerShell avec un appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="c3b6b-128">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="c3b6b-129">L’appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) chargera votre module dans la mémoire active.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-129">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="c3b6b-130">Si vous utilisez PowerShell 3,0 et versions ultérieures, il vous suffit d’appeler le nom de votre module dans le code pour l’importer également. Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="c3b6b-130">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="c3b6b-131">Importation d’assemblys de composant logiciel enfichable en tant que modules</span><span class="sxs-lookup"><span data-stu-id="c3b6b-131">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="c3b6b-132">Les applets de commande et les fournisseurs qui existent dans les assemblys de composant logiciel enfichable peuvent être chargés en tant que modules binaires.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-132">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="c3b6b-133">Lorsque les assemblys du composant logiciel enfichable sont chargés en tant que modules binaires, les applets de commande et les fournisseurs du composant logiciel enfichable sont disponibles pour l’utilisateur, mais la classe de composant logiciel enfichable de l’assembly est ignorée et le composant logiciel enfichable n’est pas inscrit.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-133">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="c3b6b-134">Par conséquent, les applets de commande du composant logiciel enfichable fournies par Windows PowerShell ne peuvent pas détecter le composant logiciel enfichable, même si les applets de commande et les fournisseurs sont disponibles pour la session.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-134">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="c3b6b-135">En outre, les fichiers de mise en forme ou de types référencés par le composant logiciel enfichable ne peuvent pas être importés dans le cadre d’un module binaire.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-135">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="c3b6b-136">Pour importer les fichiers de mise en forme et de types, vous devez créer un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="c3b6b-136">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="c3b6b-137">Consultez [Comment écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="c3b6b-137">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3b6b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3b6b-138">See Also</span></span>

[<span data-ttu-id="c3b6b-139">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3b6b-139">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
