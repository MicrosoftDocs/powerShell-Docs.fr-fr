---
title: Ajout d’alias, le développement des caractères génériques et aux paramètres de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733853"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="90794-102">Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="90794-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="90794-103">Cette section décrit comment ajouter des alias, le développement des caractères génériques, et l’aide des messages vers les paramètres de l’applet de commande Stop-Process (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="90794-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="90794-104">Cette applet de commande Stop-Process tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="90794-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="90794-105">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="90794-105">Defining the Cmdlet</span></span>

<span data-ttu-id="90794-106">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="90794-107">Étant donné que vous écrivez une applet de commande pour modifier le système, il doit être nommé en conséquence.</span><span class="sxs-lookup"><span data-stu-id="90794-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="90794-108">Étant donné que cette applet de commande arrête les processus système, il utilise le verbe « Stop », défini par le [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), avec le nom « Proc » pour indiquer les processus.</span><span class="sxs-lookup"><span data-stu-id="90794-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="90794-109">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="90794-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="90794-110">Le code suivant est la définition de classe pour cette applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="90794-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="90794-111">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="90794-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="90794-112">Votre applet de commande doit définir les paramètres qui modifications du système de prise en charge et les commentaires des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="90794-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="90794-113">L’applet de commande doit définir un `Name` paramètre ou équivalent afin que l’applet de commande sera en mesure de modifier le système par une sorte d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="90794-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="90794-114">En outre, l’applet de commande doit définir le `Force` et `PassThru` paramètres.</span><span class="sxs-lookup"><span data-stu-id="90794-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="90794-115">Pour plus d’informations sur ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="90794-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="90794-116">Définition d’un Alias de paramètre</span><span class="sxs-lookup"><span data-stu-id="90794-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="90794-117">Un alias de paramètre peut être un autre nom ou un nom de court 1-2-lettre ou bien défini pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="90794-118">Dans les deux cas, l’objectif de l’utilisation d’alias est de simplifier l’entrée d’utilisateur à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="90794-119">Windows PowerShell prend en charge les alias de paramètre via la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, qui utilise la syntaxe de déclaration [Alias()].</span><span class="sxs-lookup"><span data-stu-id="90794-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="90794-120">Le code suivant montre comment un alias est ajouté à la `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="90794-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="90794-121">Outre l’utilisation de la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, le runtime Windows PowerShell effectue la correspondance partielle de noms, même si aucun alias ne sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="90794-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="90794-122">Par exemple, si votre applet de commande a un `FileName` paramètre et qui est le seul paramètre qui commence par `F`, l’utilisateur peut entrer `Filename`, `Filenam`, `File`, `Fi`, ou `F` et toujours reconnaître le entrée en tant que le `FileName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="90794-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="90794-123">Création d’une aide pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="90794-123">Creating Help for Parameters</span></span>

<span data-ttu-id="90794-124">Windows PowerShell vous permet de créer une aide pour les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="90794-125">Procédez ainsi pour n’importe quel paramètre utilisé pour les commentaires de modification et l’utilisateur du système.</span><span class="sxs-lookup"><span data-stu-id="90794-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="90794-126">Pour chaque paramètre prendre en charge d’aide, vous pouvez définir le `HelpMessage` attribut mot clé dans le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="90794-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="90794-127">Ce mot clé définit le texte à afficher à l’utilisateur pour obtenir une assistance dans l’aide du paramètre.</span><span class="sxs-lookup"><span data-stu-id="90794-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="90794-128">Vous pouvez également définir le `HelpMessageBaseName` mot clé pour identifier le nom de base d’une ressource à utiliser pour le message.</span><span class="sxs-lookup"><span data-stu-id="90794-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="90794-129">Si vous définissez ce mot clé, vous devez également définir le `HelpMessageResourceId` mot clé pour spécifier l’identificateur de ressource.</span><span class="sxs-lookup"><span data-stu-id="90794-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="90794-130">Le code suivant à partir de cette applet de commande Stop-Process définit le `HelpMessage` attribut mot clé pour le `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="90794-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="90794-131">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="90794-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="90794-132">Votre applet de commande doit substituer une méthode de traitement des entrées, ce sera souvent [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="90794-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="90794-133">Lorsque vous modifiez le système, l’applet de commande doit appeler le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) des méthodes qui permettent de l’utilisateur pour fournir des commentaires avant une modification est apportée.</span><span class="sxs-lookup"><span data-stu-id="90794-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="90794-134">Pour plus d’informations sur ces méthodes, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="90794-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="90794-135">Prise en charge du développement des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="90794-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="90794-136">Pour permettre la sélection de plusieurs objets, votre applet de commande peut utiliser le [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) et [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes pour fournir prise en charge de caractère générique d’extension pour le paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="90794-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="90794-137">Exemples de modèles de caractère générique sont lsa \* \*.txt et [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="90794-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="90794-138">Utiliser le caractère de guillemet inversé (') comme caractère d’échappement lorsque le modèle contient un caractère qui doit être utilisé littéralement.</span><span class="sxs-lookup"><span data-stu-id="90794-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="90794-139">Expansions de caractère générique des noms de fichier et chemin d’accès sont des exemples de scénarios courants où l’applet de commande souhaitez peut-être autoriser la prise en charge pour les entrées de chemin d’accès lors de la sélection de plusieurs objets est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="90794-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="90794-140">Un cas courant est le système de fichiers, dans lequel un utilisateur souhaite voir tous les fichiers qui résident dans le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="90794-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="90794-141">Vous aurez rarement une implémentation du modèle générique personnalisé correspondant.</span><span class="sxs-lookup"><span data-stu-id="90794-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="90794-142">Dans ce cas, votre applet de commande doit prendre en charge la version complète de 1003.2 POSIX, 3,13 spécification pour le développement des caractères génériques ou le sous-ensemble simplifié suivant :</span><span class="sxs-lookup"><span data-stu-id="90794-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="90794-143">**Point d’interrogation ( ?).**</span><span class="sxs-lookup"><span data-stu-id="90794-143">**Question mark (?).**</span></span> <span data-ttu-id="90794-144">Correspond à n’importe quel caractère à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="90794-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="90794-145">**Astérisque (\*).**</span><span class="sxs-lookup"><span data-stu-id="90794-145">**Asterisk (\*).**</span></span> <span data-ttu-id="90794-146">Correspond à zéro ou plusieurs caractères en commençant à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="90794-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="90794-147">**Crochet ouvrant ([]).**</span><span class="sxs-lookup"><span data-stu-id="90794-147">**Open bracket ([).**</span></span> <span data-ttu-id="90794-148">Introduit une expression entre crochets de modèle qui peut contenir des caractères ou une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="90794-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="90794-149">Si une plage est requise, un trait d’union (-) est utilisé pour indiquer la plage.</span><span class="sxs-lookup"><span data-stu-id="90794-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="90794-150">**Crochet fermant (]).**</span><span class="sxs-lookup"><span data-stu-id="90794-150">**Close bracket (]).**</span></span> <span data-ttu-id="90794-151">Met fin à une expression entre crochets de modèle.</span><span class="sxs-lookup"><span data-stu-id="90794-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="90794-152">**Guillemet inversé le caractère d’échappement (').**</span><span class="sxs-lookup"><span data-stu-id="90794-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="90794-153">Indique que le caractère suivant doit être pris littéralement.</span><span class="sxs-lookup"><span data-stu-id="90794-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="90794-154">N’oubliez pas que lorsque vous spécifiez le caractère de guillemet inversé à partir de la ligne de commande (par opposition à spécifier par programmation), le caractère d’échappement de guillemet inversé doit être spécifié deux fois.</span><span class="sxs-lookup"><span data-stu-id="90794-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="90794-155">Pour plus d’informations sur les séquences de caractères génériques, consultez [prenant en charge les caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="90794-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="90794-156">Le code suivant montre comment définir des options des caractères génériques et le modèle de caractère générique utilisé pour résoudre le `Name` paramètre pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="90794-157">Le code suivant montre comment tester si le nom du processus correspond au modèle de caractère générique définie.</span><span class="sxs-lookup"><span data-stu-id="90794-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="90794-158">Notez que, dans ce cas, si le nom du processus ne correspond pas au modèle, l’applet de commande se poursuit sur obtenir le nom du processus suivant.</span><span class="sxs-lookup"><span data-stu-id="90794-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="90794-159">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="90794-159">Code Sample</span></span>

<span data-ttu-id="90794-160">Pour l’ensemble C# exemple de code, consultez [StopProcessSample03 exemple](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="90794-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="90794-161">Définir les Types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="90794-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="90794-162">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="90794-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="90794-163">Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="90794-164">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="90794-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="90794-165">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="90794-165">Building the Cmdlet</span></span>

<span data-ttu-id="90794-166">Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90794-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="90794-167">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="90794-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="90794-168">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="90794-168">Testing the Cmdlet</span></span>

<span data-ttu-id="90794-169">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="90794-170">Testons l’applet de commande Stop-Process exemple.</span><span class="sxs-lookup"><span data-stu-id="90794-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="90794-171">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="90794-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="90794-172">Démarrez Windows PowerShell et utilisez Stop-Process pour arrêter un processus à l’aide de l’alias ProcessName pour le `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="90794-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="90794-173">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="90794-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="90794-174">Ajoutez l’entrée suivante sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="90794-174">Make the following entry on the command line.</span></span> <span data-ttu-id="90794-175">Étant donné que le paramètre de nom est obligatoire, vous êtes invité pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="90794-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="90794-176">Saisie de « ! ? »</span><span class="sxs-lookup"><span data-stu-id="90794-176">Entering "!?"</span></span> <span data-ttu-id="90794-177">Affiche le texte d’aide associé au paramètre.</span><span class="sxs-lookup"><span data-stu-id="90794-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="90794-178">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="90794-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="90794-179">Assurez-vous maintenant l’entrée suivante pour arrêter tous les processus qui correspondent au modèle de caractère générique « \* Remarque\*».</span><span class="sxs-lookup"><span data-stu-id="90794-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="90794-180">Vous êtes invité avant d’arrêter chaque processus qui correspond au modèle.</span><span class="sxs-lookup"><span data-stu-id="90794-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="90794-181">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="90794-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="90794-182">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="90794-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="90794-183">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="90794-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="90794-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90794-184">See Also</span></span>

[<span data-ttu-id="90794-185">Créer une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="90794-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="90794-186">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90794-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="90794-187">[Extension des Types d’objets et mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="90794-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="90794-188">[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="90794-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="90794-189">Prise en charge des caractères génériques dans les paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="90794-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="90794-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="90794-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
