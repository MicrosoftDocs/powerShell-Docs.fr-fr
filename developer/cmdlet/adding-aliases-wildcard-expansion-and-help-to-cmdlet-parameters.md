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
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075254"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="862b0-102">Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="862b0-103">Cette section décrit comment ajouter des alias, le développement des caractères génériques, et l’aide des messages vers les paramètres de l’applet de commande Stop-Process (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="862b0-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="862b0-104">Cette applet de commande Stop-Process tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="862b0-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="862b0-105">Rubriques de cette section sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="862b0-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="862b0-106">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="862b0-107">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="862b0-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="862b0-108">Définition d’un Alias de paramètre</span><span class="sxs-lookup"><span data-stu-id="862b0-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="862b0-109">Création d’une aide pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="862b0-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="862b0-110">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="862b0-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="862b0-111">Prise en charge du développement des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="862b0-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="862b0-112">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="862b0-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="862b0-113">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="862b0-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="862b0-114">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="862b0-115">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="862b0-116">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-116">Defining the Cmdlet</span></span>

<span data-ttu-id="862b0-117">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="862b0-118">Étant donné que vous écrivez une applet de commande pour modifier le système, il doit être nommé en conséquence.</span><span class="sxs-lookup"><span data-stu-id="862b0-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="862b0-119">Étant donné que cette applet de commande arrête les processus système, il utilise le verbe « Stop », défini par le [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), avec le nom « Proc » pour indiquer les processus.</span><span class="sxs-lookup"><span data-stu-id="862b0-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="862b0-120">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="862b0-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="862b0-121">Le code suivant est la définition de classe pour cette applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="862b0-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="862b0-122">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="862b0-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="862b0-123">Votre applet de commande doit définir les paramètres qui modifications du système de prise en charge et les commentaires des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="862b0-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="862b0-124">L’applet de commande doit définir un `Name` paramètre ou équivalent afin que l’applet de commande sera en mesure de modifier le système par une sorte d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="862b0-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="862b0-125">En outre, l’applet de commande doit définir le `Force` et `PassThru` paramètres.</span><span class="sxs-lookup"><span data-stu-id="862b0-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="862b0-126">Pour plus d’informations sur ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="862b0-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="862b0-127">Définition d’un Alias de paramètre</span><span class="sxs-lookup"><span data-stu-id="862b0-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="862b0-128">Un alias de paramètre peut être un autre nom ou un nom de court 1-2-lettre ou bien défini pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="862b0-129">Dans les deux cas, l’objectif de l’utilisation d’alias est de simplifier l’entrée d’utilisateur à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="862b0-130">Windows PowerShell prend en charge les alias de paramètre via la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, qui utilise la syntaxe de déclaration [Alias()].</span><span class="sxs-lookup"><span data-stu-id="862b0-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="862b0-131">Le code suivant montre comment un alias est ajouté à la `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="862b0-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="862b0-132">Outre l’utilisation de la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, le runtime Windows PowerShell effectue la correspondance partielle de noms, même si aucun alias ne sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="862b0-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="862b0-133">Par exemple, si votre applet de commande a un `FileName` paramètre et qui est le seul paramètre qui commence par `F`, l’utilisateur peut entrer `Filename`, `Filenam`, `File`, `Fi`, ou `F` et toujours reconnaître le entrée en tant que le `FileName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="862b0-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="862b0-134">Création d’une aide pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="862b0-134">Creating Help for Parameters</span></span>

<span data-ttu-id="862b0-135">Windows PowerShell vous permet de créer une aide pour les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="862b0-136">Procédez ainsi pour n’importe quel paramètre utilisé pour les commentaires de modification et l’utilisateur du système.</span><span class="sxs-lookup"><span data-stu-id="862b0-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="862b0-137">Pour chaque paramètre prendre en charge d’aide, vous pouvez définir le `HelpMessage` attribut mot clé dans le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="862b0-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="862b0-138">Ce mot clé définit le texte à afficher à l’utilisateur pour obtenir une assistance dans l’aide du paramètre.</span><span class="sxs-lookup"><span data-stu-id="862b0-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="862b0-139">Vous pouvez également définir le `HelpMessageBaseName` mot clé pour identifier le nom de base d’une ressource à utiliser pour le message.</span><span class="sxs-lookup"><span data-stu-id="862b0-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="862b0-140">Si vous définissez ce mot clé, vous devez également définir le `HelpMessageResourceId` mot clé pour spécifier l’identificateur de ressource.</span><span class="sxs-lookup"><span data-stu-id="862b0-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="862b0-141">Le code suivant à partir de cette applet de commande Stop-Process définit le `HelpMessage` attribut mot clé pour le `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="862b0-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="862b0-142">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="862b0-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="862b0-143">Votre applet de commande doit substituer une méthode de traitement des entrées, ce sera souvent [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="862b0-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="862b0-144">Lorsque vous modifiez le système, l’applet de commande doit appeler le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) des méthodes qui permettent de l’utilisateur pour fournir des commentaires avant une modification est apportée.</span><span class="sxs-lookup"><span data-stu-id="862b0-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="862b0-145">Pour plus d’informations sur ces méthodes, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="862b0-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="862b0-146">Prise en charge du développement des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="862b0-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="862b0-147">Pour permettre la sélection de plusieurs objets, votre applet de commande peut utiliser le [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) et [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes pour fournir prise en charge de caractère générique d’extension pour le paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="862b0-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="862b0-148">Exemples de modèles de caractère générique sont lsa \* \*.txt et [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="862b0-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="862b0-149">Utiliser le caractère de guillemet inversé (') comme caractère d’échappement lorsque le modèle contient un caractère qui doit être utilisé littéralement.</span><span class="sxs-lookup"><span data-stu-id="862b0-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="862b0-150">Expansions de caractère générique des noms de fichier et chemin d’accès sont des exemples de scénarios courants où l’applet de commande souhaitez peut-être autoriser la prise en charge pour les entrées de chemin d’accès lors de la sélection de plusieurs objets est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="862b0-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="862b0-151">Un cas courant est le système de fichiers, dans lequel un utilisateur souhaite voir tous les fichiers qui résident dans le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="862b0-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="862b0-152">Vous aurez rarement une implémentation du modèle générique personnalisé correspondant.</span><span class="sxs-lookup"><span data-stu-id="862b0-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="862b0-153">Dans ce cas, votre applet de commande doit prendre en charge la version complète de 1003.2 POSIX, 3,13 spécification pour le développement des caractères génériques ou le sous-ensemble simplifié suivant :</span><span class="sxs-lookup"><span data-stu-id="862b0-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="862b0-154">**Point d’interrogation ( ?).**</span><span class="sxs-lookup"><span data-stu-id="862b0-154">**Question mark (?).**</span></span> <span data-ttu-id="862b0-155">Correspond à n’importe quel caractère à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="862b0-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="862b0-156">**Astérisque (\*).**</span><span class="sxs-lookup"><span data-stu-id="862b0-156">**Asterisk (\*).**</span></span> <span data-ttu-id="862b0-157">Correspond à zéro ou plusieurs caractères en commençant à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="862b0-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="862b0-158">**Crochet ouvrant ([]).**</span><span class="sxs-lookup"><span data-stu-id="862b0-158">**Open bracket ([).**</span></span> <span data-ttu-id="862b0-159">Introduit une expression entre crochets de modèle qui peut contenir des caractères ou une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="862b0-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="862b0-160">Si une plage est requise, un trait d’union (-) est utilisé pour indiquer la plage.</span><span class="sxs-lookup"><span data-stu-id="862b0-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="862b0-161">**Crochet fermant (]).**</span><span class="sxs-lookup"><span data-stu-id="862b0-161">**Close bracket (]).**</span></span> <span data-ttu-id="862b0-162">Met fin à une expression entre crochets de modèle.</span><span class="sxs-lookup"><span data-stu-id="862b0-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="862b0-163">**Guillemet inversé le caractère d’échappement (').**</span><span class="sxs-lookup"><span data-stu-id="862b0-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="862b0-164">Indique que le caractère suivant doit être pris littéralement.</span><span class="sxs-lookup"><span data-stu-id="862b0-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="862b0-165">N’oubliez pas que lorsque vous spécifiez le caractère de guillemet inversé à partir de la ligne de commande (par opposition à spécifier par programmation), le caractère d’échappement de guillemet inversé doit être spécifié deux fois.</span><span class="sxs-lookup"><span data-stu-id="862b0-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="862b0-166">Pour plus d’informations sur les séquences de caractères génériques, consultez [prenant en charge les caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="862b0-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="862b0-167">Le code suivant montre comment définir des options des caractères génériques et le modèle de caractère générique utilisé pour résoudre le `Name` paramètre pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="862b0-168">Le code suivant montre comment tester si le nom du processus correspond au modèle de caractère générique définie.</span><span class="sxs-lookup"><span data-stu-id="862b0-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="862b0-169">Notez que, dans ce cas, si le nom du processus ne correspond pas au modèle, l’applet de commande se poursuit sur obtenir le nom du processus suivant.</span><span class="sxs-lookup"><span data-stu-id="862b0-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="862b0-170">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="862b0-170">Code Sample</span></span>

<span data-ttu-id="862b0-171">Pour l’ensemble C# exemple de code, consultez [StopProcessSample03 exemple](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="862b0-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="862b0-172">Définir les Types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="862b0-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="862b0-173">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="862b0-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="862b0-174">Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="862b0-175">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="862b0-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="862b0-176">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-176">Building the Cmdlet</span></span>

<span data-ttu-id="862b0-177">Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="862b0-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="862b0-178">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="862b0-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="862b0-179">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-179">Testing the Cmdlet</span></span>

<span data-ttu-id="862b0-180">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="862b0-181">Testons l’applet de commande Stop-Process exemple.</span><span class="sxs-lookup"><span data-stu-id="862b0-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="862b0-182">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="862b0-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="862b0-183">Démarrez Windows PowerShell et utilisez Stop-Process pour arrêter un processus à l’aide de l’alias ProcessName pour le `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="862b0-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="862b0-184">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="862b0-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="862b0-185">Ajoutez l’entrée suivante sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="862b0-185">Make the following entry on the command line.</span></span> <span data-ttu-id="862b0-186">Étant donné que le paramètre de nom est obligatoire, vous êtes invité pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="862b0-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="862b0-187">Saisie de « ! ? »</span><span class="sxs-lookup"><span data-stu-id="862b0-187">Entering "!?"</span></span> <span data-ttu-id="862b0-188">Affiche le texte d’aide associé au paramètre.</span><span class="sxs-lookup"><span data-stu-id="862b0-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="862b0-189">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="862b0-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="862b0-190">Assurez-vous maintenant l’entrée suivante pour arrêter tous les processus qui correspondent au modèle de caractère générique « \* Remarque\*».</span><span class="sxs-lookup"><span data-stu-id="862b0-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="862b0-191">Vous êtes invité avant d’arrêter chaque processus qui correspond au modèle.</span><span class="sxs-lookup"><span data-stu-id="862b0-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="862b0-192">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="862b0-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="862b0-193">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="862b0-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="862b0-194">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="862b0-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="862b0-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="862b0-195">See Also</span></span>

[<span data-ttu-id="862b0-196">Créer une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="862b0-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="862b0-197">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="862b0-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="862b0-198">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="862b0-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="862b0-199">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="862b0-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="862b0-200">Prise en charge des caractères génériques dans les paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="862b0-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="862b0-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="862b0-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
