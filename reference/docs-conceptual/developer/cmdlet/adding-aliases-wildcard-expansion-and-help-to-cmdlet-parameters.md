---
ms.date: 09/13/2016
ms.topic: reference
title: Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande
description: Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande
ms.openlocfilehash: f0f07796370b4613b1ca0ad17b16c6598bfa438d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660629"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="42e17-103">Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="42e17-103">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="42e17-104">Cette section décrit comment ajouter des alias, une extension de caractères génériques et des messages d’aide aux paramètres de l’applet de commande Stop-Proc (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="42e17-104">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="42e17-105">Cette applet de commande Stop-Proc tente d’arrêter les processus qui sont récupérés à l’aide de l’applet de commande Get-Proc (décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande).</span><span class="sxs-lookup"><span data-stu-id="42e17-105">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="42e17-106">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="42e17-106">Defining the Cmdlet</span></span>

<span data-ttu-id="42e17-107">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="42e17-108">Étant donné que vous écrivez une applet de commande pour modifier le système, elle doit être nommée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="42e17-108">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="42e17-109">Étant donné que cette applet de commande arrête les processus système, elle utilise le verbe « Stop », défini par la classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , avec le nom « proc » pour indiquer le processus.</span><span class="sxs-lookup"><span data-stu-id="42e17-109">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="42e17-110">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-110">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="42e17-111">Le code suivant est la définition de classe pour cette applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="42e17-111">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="42e17-112">Définition des paramètres pour la modification du système</span><span class="sxs-lookup"><span data-stu-id="42e17-112">Defining Parameters for System Modification</span></span>

<span data-ttu-id="42e17-113">Votre applet de commande doit définir des paramètres qui prennent en charge les modifications du système et les commentaires des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="42e17-113">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="42e17-114">L’applet de commande doit définir un `Name` paramètre ou un équivalent pour que l’applet de commande puisse modifier le système par une sorte d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="42e17-114">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="42e17-115">En outre, l’applet de commande doit définir les `Force` `PassThru` paramètres et.</span><span class="sxs-lookup"><span data-stu-id="42e17-115">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="42e17-116">Pour plus d’informations sur ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="42e17-116">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="42e17-117">Définition d’un alias de paramètre</span><span class="sxs-lookup"><span data-stu-id="42e17-117">Defining a Parameter Alias</span></span>

<span data-ttu-id="42e17-118">Un alias de paramètre peut être un nom de remplacement ou un nom abrégé à une ou deux lettres bien défini pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-118">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="42e17-119">Dans les deux cas, l’objectif de l’utilisation d’alias est de simplifier l’entrée d’utilisateur à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-119">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="42e17-120">Windows PowerShell prend en charge les alias de paramètres via l’attribut [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , qui utilise la syntaxe de déclaration [alias ()].</span><span class="sxs-lookup"><span data-stu-id="42e17-120">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="42e17-121">Le code suivant montre comment un alias est ajouté au `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-121">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="42e17-122">Outre l’utilisation de l’attribut [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , le runtime Windows PowerShell effectue une correspondance de nom partielle, même si aucun alias n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="42e17-122">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="42e17-123">Par exemple, si votre applet de commande a un `FileName` paramètre et qu’il s’agit du seul paramètre qui commence par `F` , l’utilisateur peut entrer `Filename` , `Filenam` ,, `File` `Fi` ou `F` et toujours reconnaître l’entrée comme `FileName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-123">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="42e17-124">Création d’aide pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="42e17-124">Creating Help for Parameters</span></span>

<span data-ttu-id="42e17-125">Windows PowerShell vous permet de créer de l’aide pour les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-125">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="42e17-126">Procédez ainsi pour tous les paramètres utilisés pour la modification du système et les commentaires des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="42e17-126">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="42e17-127">Pour chaque paramètre permettant de prendre en charge l’aide, vous pouvez définir le `HelpMessage` mot clé attribute dans la déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="42e17-127">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="42e17-128">Ce mot clé définit le texte à afficher à l’utilisateur pour obtenir de l’aide sur l’utilisation du paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-128">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="42e17-129">Vous pouvez également définir le `HelpMessageBaseName` mot clé pour identifier le nom de base d’une ressource à utiliser pour le message.</span><span class="sxs-lookup"><span data-stu-id="42e17-129">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="42e17-130">Si vous définissez ce mot clé, vous devez également définir le `HelpMessageResourceId` mot clé pour spécifier l’identificateur de ressource.</span><span class="sxs-lookup"><span data-stu-id="42e17-130">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="42e17-131">Le code suivant de cette applet de commande Stop-Proc définit le `HelpMessage` mot clé d’attribut pour le `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-131">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="42e17-132">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="42e17-132">Overriding an Input Processing Method</span></span>

<span data-ttu-id="42e17-133">Votre applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de commande. ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="42e17-133">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="42e17-134">Lors de la modification du système, l’applet de commande doit appeler les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) pour permettre à l’utilisateur de fournir des commentaires avant qu’une modification soit apportée.</span><span class="sxs-lookup"><span data-stu-id="42e17-134">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="42e17-135">Pour plus d’informations sur ces méthodes, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="42e17-135">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="42e17-136">Extension de caractères génériques prise en charge</span><span class="sxs-lookup"><span data-stu-id="42e17-136">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="42e17-137">Pour permettre la sélection de plusieurs objets, votre applet de commande peut utiliser les classes [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) et [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) pour fournir une prise en charge des caractères génériques pour l’entrée de paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-137">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="42e17-138">LSA \*, \* . txt et [a-c] sont des exemples de modèles de caractères génériques \* .</span><span class="sxs-lookup"><span data-stu-id="42e17-138">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="42e17-139">Utilisez le caractère de guillemet (') comme caractère d’échappement lorsque le modèle contient un caractère qui doit être utilisé littéralement.</span><span class="sxs-lookup"><span data-stu-id="42e17-139">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="42e17-140">Les extensions de caractères génériques des noms de fichier et de chemin d’accès sont des exemples de scénarios courants dans lesquels l’applet de commande peut souhaiter prendre en charge les entrées de chemin d’accès lorsque la sélection de plusieurs objets est requise.</span><span class="sxs-lookup"><span data-stu-id="42e17-140">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="42e17-141">Un cas courant se trouve dans le système de fichiers, où un utilisateur souhaite voir tous les fichiers résidant dans le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="42e17-141">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="42e17-142">Vous devez avoir besoin d’une implémentation de correspondance de modèle de caractère générique personnalisée uniquement rarement.</span><span class="sxs-lookup"><span data-stu-id="42e17-142">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="42e17-143">Dans ce cas, votre applet de commande doit prendre en charge l’intégralité de la spécification POSIX 1003,2, 3,13 pour l’extension de caractères génériques ou le sous-ensemble simplifié suivant :</span><span class="sxs-lookup"><span data-stu-id="42e17-143">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="42e17-144">**Point d’interrogation ( ?).**</span><span class="sxs-lookup"><span data-stu-id="42e17-144">**Question mark (?).**</span></span> <span data-ttu-id="42e17-145">Correspond à n’importe quel caractère à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="42e17-145">Matches any character at the specified location.</span></span>

- <span data-ttu-id="42e17-146">**Astérisque ( \* ).**</span><span class="sxs-lookup"><span data-stu-id="42e17-146">**Asterisk (\*).**</span></span> <span data-ttu-id="42e17-147">Correspond à zéro ou plusieurs caractères en commençant à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="42e17-147">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="42e17-148">**Crochet ouvrant ([).**</span><span class="sxs-lookup"><span data-stu-id="42e17-148">**Open bracket ([).**</span></span> <span data-ttu-id="42e17-149">Introduit une expression de crochet de motif qui peut contenir des caractères ou une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="42e17-149">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="42e17-150">Si une plage est requise, un trait d’Union (-) est utilisé pour indiquer la plage.</span><span class="sxs-lookup"><span data-stu-id="42e17-150">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="42e17-151">**Crochet fermant (]).**</span><span class="sxs-lookup"><span data-stu-id="42e17-151">**Close bracket (]).**</span></span> <span data-ttu-id="42e17-152">Termine une expression entre crochets.</span><span class="sxs-lookup"><span data-stu-id="42e17-152">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="42e17-153">**Caractère d’échappement du guillemet (').**</span><span class="sxs-lookup"><span data-stu-id="42e17-153">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="42e17-154">Indique que le caractère suivant doit être pris littéralement.</span><span class="sxs-lookup"><span data-stu-id="42e17-154">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="42e17-155">Sachez que lorsque vous spécifiez le caractère de guillemets avant à partir de la ligne de commande (au lieu de le spécifier par programmation), le caractère d’échappement du guillemet de retour doit être spécifié deux fois.</span><span class="sxs-lookup"><span data-stu-id="42e17-155">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="42e17-156">Pour plus d’informations sur les modèles de caractères génériques, consultez [prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md)commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-156">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="42e17-157">Le code suivant montre comment définir des options de caractères génériques et définir le modèle de caractère générique utilisé pour résoudre le `Name` paramètre pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-157">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="42e17-158">Le code suivant montre comment tester si le nom du processus correspond au modèle de caractère générique défini.</span><span class="sxs-lookup"><span data-stu-id="42e17-158">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="42e17-159">Notez que, dans ce cas, si le nom du processus ne correspond pas au modèle, l’applet de commande continue à recevoir le nom de processus suivant.</span><span class="sxs-lookup"><span data-stu-id="42e17-159">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="42e17-160">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="42e17-160">Code Sample</span></span>

<span data-ttu-id="42e17-161">Pour obtenir l’exemple de code C# complet, consultez [exemple StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="42e17-161">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="42e17-162">Définir les types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="42e17-162">Define Object Types and Formatting</span></span>

<span data-ttu-id="42e17-163">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="42e17-163">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="42e17-164">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-164">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="42e17-165">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="42e17-165">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="42e17-166">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="42e17-166">Building the Cmdlet</span></span>

<span data-ttu-id="42e17-167">Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42e17-167">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="42e17-168">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="42e17-168">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="42e17-169">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="42e17-169">Testing the Cmdlet</span></span>

<span data-ttu-id="42e17-170">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-170">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="42e17-171">Nous allons tester l’exemple d’applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="42e17-171">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="42e17-172">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="42e17-172">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="42e17-173">Démarrez Windows PowerShell et utilisez Stop-Proc pour arrêter un processus à l’aide de l’alias ProcessName pour le `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-173">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    <span data-ttu-id="42e17-174">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="42e17-174">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="42e17-175">Effectuez l’entrée suivante sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="42e17-175">Make the following entry on the command line.</span></span> <span data-ttu-id="42e17-176">Étant donné que le paramètre Name est obligatoire, vous êtes invité à le faire.</span><span class="sxs-lookup"><span data-stu-id="42e17-176">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="42e17-177">Entrée de «  !? »</span><span class="sxs-lookup"><span data-stu-id="42e17-177">Entering "!?"</span></span> <span data-ttu-id="42e17-178">affiche le texte d’aide associé au paramètre.</span><span class="sxs-lookup"><span data-stu-id="42e17-178">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="42e17-179">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="42e17-179">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="42e17-180">À présent, effectuez l’entrée suivante pour arrêter tous les processus qui correspondent au modèle de caractère générique « \* Remarque \* ».</span><span class="sxs-lookup"><span data-stu-id="42e17-180">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="42e17-181">Vous êtes invité à arrêter chaque processus correspondant au modèle.</span><span class="sxs-lookup"><span data-stu-id="42e17-181">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

    <span data-ttu-id="42e17-182">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="42e17-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    <span data-ttu-id="42e17-183">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="42e17-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    <span data-ttu-id="42e17-184">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="42e17-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="42e17-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42e17-185">See Also</span></span>

[<span data-ttu-id="42e17-186">Créer une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="42e17-186">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="42e17-187">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42e17-187">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="42e17-188">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="42e17-188">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="42e17-189">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="42e17-189">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="42e17-190">Prise en charge des caractères génériques dans les paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="42e17-190">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="42e17-191">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="42e17-191">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
