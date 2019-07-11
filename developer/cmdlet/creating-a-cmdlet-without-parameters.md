---
title: Création d’une applet de commande sans paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733971"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="d2bed-102">Création d’une applet de commande sans paramètre</span><span class="sxs-lookup"><span data-stu-id="d2bed-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="d2bed-103">Cette section décrit comment créer une applet de commande qui Récupère des informations à partir de l’ordinateur local sans l’utilisation de paramètres, puis écrit les informations dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d2bed-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="d2bed-104">L’applet de commande décrit ici est une applet de commande Get-Process qui extrait des informations sur les processus de l’ordinateur local, puis affiche ces informations à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="d2bed-105">N’oubliez pas que lors de l’écriture des applets de commande, les assemblys de référence Windows PowerShell® sont téléchargées sur le disque (par défaut dans C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="d2bed-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="d2bed-106">Ils ne sont pas installés dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="d2bed-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="d2bed-107">L’applet de commande d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="d2bed-107">Naming the Cmdlet</span></span>

<span data-ttu-id="d2bed-108">Un nom de l’applet de commande se compose d’un verbe qui indique l’action de l’applet de commande prend et un nom qui indique les éléments de l’applet de commande agit.</span><span class="sxs-lookup"><span data-stu-id="d2bed-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="d2bed-109">Étant donné que cette applet de commande Get-Process exemple récupère des objets de processus, il utilise le verbe « Get », défini par le [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) énumération et le substantif « Proc » pour indiquer que l’applet de commande fonctionne sur les éléments de processus.</span><span class="sxs-lookup"><span data-stu-id="d2bed-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="d2bed-110">Lorsque vous nommez des applets de commande, n’utilisez pas les caractères suivants : #, () {} [] & - / \ $ ; : « ' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="d2bed-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="d2bed-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="d2bed-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="d2bed-112">Choix d’un substantif.</span><span class="sxs-lookup"><span data-stu-id="d2bed-112">Choosing a Noun</span></span>

<span data-ttu-id="d2bed-113">Vous devez choisir un nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="d2bed-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="d2bed-114">Il est préférable d’utiliser un nom au singulier précédé d’une version abrégée du nom du produit.</span><span class="sxs-lookup"><span data-stu-id="d2bed-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="d2bed-115">Un exemple de nom d’applet de commande de ce type est «`Get-SQLServer`».</span><span class="sxs-lookup"><span data-stu-id="d2bed-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="d2bed-116">Choix d’un verbe</span><span class="sxs-lookup"><span data-stu-id="d2bed-116">Choosing a Verb</span></span>

<span data-ttu-id="d2bed-117">Vous devez utiliser un verbe à partir de l’ensemble des noms de verbe approuvé applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="d2bed-118">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d2bed-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="d2bed-119">Définition de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d2bed-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="d2bed-120">Une fois que vous avez choisi un nom de l’applet de commande, définissez une classe .NET pour implémenter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="d2bed-121">Voici la définition de classe pour cette applet de commande Get-Process exemple :</span><span class="sxs-lookup"><span data-stu-id="d2bed-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="d2bed-122">Notez qu’antérieures à la définition de classe, le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut, avec la syntaxe `[Cmdlet(verb, noun, ...)]`, est utilisé pour identifier cette classe comme une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="d2bed-123">Il s’agit du seul attribut requis pour toutes les applets de commande, et il permet au runtime de Windows PowerShell pour les appeler correctement.</span><span class="sxs-lookup"><span data-stu-id="d2bed-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="d2bed-124">Vous pouvez définir des mots clés des attributs pour déclarer plus de la classe si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d2bed-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="d2bed-125">N’oubliez pas que la déclaration d’attribut pour notre exemple de classe GetProcCommand ne déclare que les noms de nom et verbe pour l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="d2bed-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d2bed-126">Pour toutes les classes d’attributs de Windows PowerShell, les mots clés que vous pouvez définir correspondent aux propriétés de la classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="d2bed-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="d2bed-127">Lorsque vous nommez la classe de l’applet de commande, il est conseillé de refléter le nom de l’applet de commande dans le nom de classe.</span><span class="sxs-lookup"><span data-stu-id="d2bed-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="d2bed-128">Pour ce faire, utilisez la forme « VerbNounCommand » et remplacez « Verbe » et « Nom » par le verbe et substantif utilisé dans le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="d2bed-129">Comme indiqué dans la définition de classe précédentes, l’applet de commande Get-Process exemple définit une classe appelée GetProcCommand, qui dérive de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe de base.</span><span class="sxs-lookup"><span data-stu-id="d2bed-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2bed-130">Si vous souhaitez définir une applet de commande qui accède directement à l’exécution de Windows PowerShell, votre classe .NET doit dériver à partir de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe de base.</span><span class="sxs-lookup"><span data-stu-id="d2bed-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="d2bed-131">Pour plus d’informations sur cette classe, consultez [création d’une applet de commande qui définit des jeux de paramètres](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="d2bed-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d2bed-132">La classe pour une applet de commande doit être explicitement marquée comme étant publique.</span><span class="sxs-lookup"><span data-stu-id="d2bed-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="d2bed-133">Les classes qui ne sont pas marqués comme publics seront internes par défaut et seront introuvable par le runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d2bed-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="d2bed-134">Windows PowerShell utilise le [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) espace de noms pour ses classes de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="d2bed-135">Il est recommandé de placer vos classes de l’applet de commande dans un espace de noms de commandes de votre espace de noms API, par exemple, xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="d2bed-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="d2bed-136">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="d2bed-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="d2bed-137">Le [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fournit trois méthodes de traitement d’entrée principal, au moins un d'entre eux doit remplacer votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="d2bed-138">Pour plus d’informations sur la façon dont Windows PowerShell traite les enregistrements, consultez [Windows PowerShell fonctionnement](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d2bed-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="d2bed-139">Pour tous les types d’entrée, l’exécution de Windows PowerShell appelle [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour permettre un traitement.</span><span class="sxs-lookup"><span data-stu-id="d2bed-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="d2bed-140">Si votre applet de commande doit exécuter certaines de prétraitement ou de la configuration, il peut le faire à en substituant cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d2bed-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="d2bed-141">Windows PowerShell utilise le terme « enregistrement » pour décrire le jeu de valeurs de paramètre fournie lors d’une applet de commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="d2bed-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="d2bed-142">Si votre applet de commande accepte les entrées de pipeline, il doit remplacer le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode) et éventuellement le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)(méthode).</span><span class="sxs-lookup"><span data-stu-id="d2bed-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="d2bed-143">Par exemple, une applet de commande peut remplacer les deux méthodes si il rassemble toutes les entrées à l’aide de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) et opère sur l’entrée comme un entier plutôt qu’un seul élément à la fois, comme le `Sort-Object` applet de commande ne.</span><span class="sxs-lookup"><span data-stu-id="d2bed-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="d2bed-144">Si votre applet de commande n’accepte pas d’entrée de pipeline, il doit substituer la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d2bed-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="d2bed-145">N’oubliez pas que cette méthode est fréquemment utilisée à la place de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) lorsque l’applet de commande ne peut pas fonctionner sur un seul élément à la fois, comme c’est le cas pour une applet de commande de tri.</span><span class="sxs-lookup"><span data-stu-id="d2bed-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="d2bed-146">Étant donné que cette applet de commande Get-Process exemple doit recevoir une entrée de pipeline, ce paramètre remplace le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode) et utilise les implémentations par défaut pour [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="d2bed-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="d2bed-147">Le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override récupère les processus et les écrit dans la ligne de commande à l’aide de la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d2bed-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="d2bed-148">Points à retenir sur le traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="d2bed-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="d2bed-149">La source par défaut pour l’entrée est un objet explicit (par exemple, une chaîne) fourni par l’utilisateur sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="d2bed-150">Pour plus d’informations, consultez [création d’une applet de commande pour l’entrée du processus de ligne de commande](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="d2bed-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="d2bed-151">Une méthode de traitement des entrées peuvent également recevoir l’entrée à partir de l’objet de sortie d’une applet de commande en amont sur le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d2bed-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="d2bed-152">Pour plus d’informations, consultez [création d’une applet de commande pour l’entrée de Pipeline de processus](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="d2bed-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="d2bed-153">N’oubliez pas que votre applet de commande peut recevoir l’entrée d’une combinaison de ligne de commande et un pipeline sources.</span><span class="sxs-lookup"><span data-stu-id="d2bed-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="d2bed-154">L’applet de commande en aval ne renvoie pas pendant une longue période, ou pas du tout.</span><span class="sxs-lookup"><span data-stu-id="d2bed-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="d2bed-155">Pour cette raison, l’entrée de méthode dans votre applet de commande de traitement doit contient pas de verrous pendant les appels aux [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), en particulier les verrous dont la portée s’étend au-delà de l’instance de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2bed-156">Applets de commande ne doit jamais appeler [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) ou son équivalent.</span><span class="sxs-lookup"><span data-stu-id="d2bed-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="d2bed-157">Votre applet de commande peut avoir des variables d’objet pour la nettoyer lorsqu’elle est terminée de traitement (par exemple, si elle s’ouvre un descripteur de fichier dans le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode) et conserve le handle ouvrir pour une utilisation par [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="d2bed-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="d2bed-158">Il est important de se rappeler que le runtime Windows PowerShell n’appelle pas toujours le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode), qui doit effectuer un nettoyage de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d2bed-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="d2bed-159">Par exemple, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ne peut pas être appelée si l’applet de commande est annulée à mi-chemin ou si un arrêt de l’erreur se produit dans n’importe quelle partie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="d2bed-160">Par conséquent, une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle, y compris le finaliseur, afin que le runtime peut appeler à la fois [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) et [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="d2bed-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d2bed-161">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="d2bed-161">Code Sample</span></span>

<span data-ttu-id="d2bed-162">Pour l’ensemble C# exemple de code, consultez [exemple GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d2bed-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="d2bed-163">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="d2bed-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="d2bed-164">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d2bed-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="d2bed-165">Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="d2bed-166">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d2bed-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="d2bed-167">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d2bed-167">Building the Cmdlet</span></span>

<span data-ttu-id="d2bed-168">Après l’implémentation d’une applet de commande, vous devez l’inscrire avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d2bed-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="d2bed-169">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d2bed-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="d2bed-170">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d2bed-170">Testing the Cmdlet</span></span>

<span data-ttu-id="d2bed-171">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d2bed-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="d2bed-172">Le code de notre applet de commande Get-Process exemple est petite, mais il utilise toujours le runtime Windows PowerShell et un objet .NET existant, ce qui est suffisant pour rendre utiles.</span><span class="sxs-lookup"><span data-stu-id="d2bed-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="d2bed-173">Nous allons tester pour mieux comprendre ce que Get-Process peut faire et comment sa sortie peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="d2bed-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="d2bed-174">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d2bed-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="d2bed-175">Démarrez Windows PowerShell, et obtient les processus en cours en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d2bed-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="d2bed-176">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d2bed-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="d2bed-177">Attribuez une variable pour les résultats de l’applet de commande pour une manipulation plus facile.</span><span class="sxs-lookup"><span data-stu-id="d2bed-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="d2bed-178">Obtenir le nombre de processus.</span><span class="sxs-lookup"><span data-stu-id="d2bed-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="d2bed-179">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d2bed-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="d2bed-180">Récupérer un processus spécifique.</span><span class="sxs-lookup"><span data-stu-id="d2bed-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="d2bed-181">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d2bed-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="d2bed-182">Obtenir l’heure de début de ce processus.</span><span class="sxs-lookup"><span data-stu-id="d2bed-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="d2bed-183">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d2bed-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="d2bed-184">Obtenir les processus pour lesquels le nombre de handles est supérieur à 500 et trier le résultat.</span><span class="sxs-lookup"><span data-stu-id="d2bed-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="d2bed-185">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d2bed-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="d2bed-186">Utilisez le `Get-Member` applet de commande pour répertorier les propriétés disponibles pour chaque processus.</span><span class="sxs-lookup"><span data-stu-id="d2bed-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="d2bed-187">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d2bed-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="d2bed-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2bed-188">See Also</span></span>

[<span data-ttu-id="d2bed-189">Création d’une applet de commande pour traiter l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="d2bed-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="d2bed-190">Création d’une applet de commande pour traiter l’entrée de Pipeline</span><span class="sxs-lookup"><span data-stu-id="d2bed-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="d2bed-191">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2bed-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="d2bed-192">[Extension des Types d’objets et mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d2bed-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="d2bed-193">[Fonctionnement de Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d2bed-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="d2bed-194">[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d2bed-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="d2bed-195">Référence Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2bed-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="d2bed-196">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d2bed-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)