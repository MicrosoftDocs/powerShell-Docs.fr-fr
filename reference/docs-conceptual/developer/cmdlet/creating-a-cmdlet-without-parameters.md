---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une applet de commande sans paramètre
description: Création d’une applet de commande sans paramètre
ms.openlocfilehash: 5df27ac4c1f6dfcc3e7596d93f8db0f97aae71c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646543"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="66b3f-103">Création d’une applet de commande sans paramètre</span><span class="sxs-lookup"><span data-stu-id="66b3f-103">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="66b3f-104">Cette section décrit comment créer une applet de commande qui récupère des informations à partir de l’ordinateur local sans utiliser de paramètres, puis écrit les informations dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="66b3f-104">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="66b3f-105">L’applet de commande décrite ici est un Get-Proc applet de commande qui récupère des informations sur les processus de l’ordinateur local, puis affiche ces informations sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-105">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="66b3f-106">Sachez que lors de l’écriture d’applets de commande, les assemblys de référence de® Windows PowerShell sont téléchargés sur le disque (par défaut, à l’emplacement C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="66b3f-106">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="66b3f-107">Ils ne sont pas installés dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="66b3f-107">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="66b3f-108">Attribution d’un nom à l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="66b3f-108">Naming the Cmdlet</span></span>

<span data-ttu-id="66b3f-109">Un nom d’applet de commande se compose d’un verbe qui indique l’action prise par l’applet de commande et d’un nom qui indique les éléments sur lesquels l’applet de commande agit.</span><span class="sxs-lookup"><span data-stu-id="66b3f-109">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="66b3f-110">Comme cet exemple Get-Proc applet de commande récupère des objets de processus, il utilise le verbe « obtenir », défini par l’énumération [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) , et le nom « proc » pour indiquer que l’applet de commande fonctionne sur les éléments de processus.</span><span class="sxs-lookup"><span data-stu-id="66b3f-110">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="66b3f-111">Quand vous nommez des applets de commande, n’utilisez pas les caractères suivants : #, () {} [] &-/\ $;: "' <> &#124;  ?</span><span class="sxs-lookup"><span data-stu-id="66b3f-111">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="66b3f-112">@ \` .</span><span class="sxs-lookup"><span data-stu-id="66b3f-112">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="66b3f-113">Choix d’un nom</span><span class="sxs-lookup"><span data-stu-id="66b3f-113">Choosing a Noun</span></span>

<span data-ttu-id="66b3f-114">Vous devez choisir un nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="66b3f-114">You should choose a noun that is specific.</span></span> <span data-ttu-id="66b3f-115">Il est préférable d’utiliser un nom singulier préfixé avec une version abrégée du nom du produit.</span><span class="sxs-lookup"><span data-stu-id="66b3f-115">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="66b3f-116">Un exemple de nom d’applet de commande de ce type est « `Get-SQLServer` ».</span><span class="sxs-lookup"><span data-stu-id="66b3f-116">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="66b3f-117">Choix d’un verbe</span><span class="sxs-lookup"><span data-stu-id="66b3f-117">Choosing a Verb</span></span>

<span data-ttu-id="66b3f-118">Vous devez utiliser un verbe de l’ensemble des noms de verbe d’applet de commande approuvés.</span><span class="sxs-lookup"><span data-stu-id="66b3f-118">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="66b3f-119">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-119">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="66b3f-120">Définition de la classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="66b3f-120">Defining the Cmdlet Class</span></span>

<span data-ttu-id="66b3f-121">Une fois que vous avez choisi un nom d’applet de commande, définissez une classe .NET pour implémenter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-121">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="66b3f-122">Voici la définition de classe pour cet exemple d’applet de commande Get-Proc :</span><span class="sxs-lookup"><span data-stu-id="66b3f-122">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="66b3f-123">Notez que, avant la définition de classe, l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , avec la syntaxe `[Cmdlet(verb, noun, ...)]` , est utilisé pour identifier cette classe en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-123">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="66b3f-124">Il s’agit du seul attribut requis pour toutes les applets de commande et permet au runtime Windows PowerShell de les appeler correctement.</span><span class="sxs-lookup"><span data-stu-id="66b3f-124">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="66b3f-125">Vous pouvez définir des mots clés d’attribut pour déclarer davantage la classe si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="66b3f-125">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="66b3f-126">Sachez que la déclaration d’attribut pour notre exemple de classe GetProcCommand déclare uniquement les noms de substantif et de verbe pour l’applet de commande Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="66b3f-126">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="66b3f-127">Pour toutes les classes d’attributs Windows PowerShell, les mots clés que vous pouvez définir correspondent aux propriétés de la classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="66b3f-127">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="66b3f-128">Lorsque vous nommez la classe de l’applet de commande, il est recommandé de refléter le nom de l’applet de commande dans le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="66b3f-128">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="66b3f-129">Pour ce faire, utilisez la forme « VerbNounCommand » et remplacez « Verb » et « substantif » par le verbe et le substantif utilisés dans le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-129">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="66b3f-130">Comme indiqué dans la définition de classe précédente, l’exemple Get-Proc applet de commande définit une classe appelée GetProcCommand, qui dérive de la classe de base [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-130">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66b3f-131">Si vous souhaitez définir une applet de commande qui accède directement au runtime Windows PowerShell, votre classe .NET doit dériver de la classe de base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="66b3f-131">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="66b3f-132">Pour plus d’informations sur cette classe, consultez [création d’une applet de commande qui définit des jeux de paramètres](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="66b3f-132">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="66b3f-133">La classe d’une applet de commande doit être explicitement marquée comme publique.</span><span class="sxs-lookup"><span data-stu-id="66b3f-133">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="66b3f-134">Les classes qui ne sont pas marquées comme publiques sont par défaut internes et ne sont pas détectées par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66b3f-134">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="66b3f-135">Windows PowerShell utilise l’espace de noms [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) pour ses classes d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-135">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="66b3f-136">Il est recommandé de placer vos classes d’applet de commande dans un espace de noms Commands de votre espace de noms d’API, par exemple, xxx. PS. Commands.</span><span class="sxs-lookup"><span data-stu-id="66b3f-136">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="66b3f-137">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="66b3f-137">Overriding an Input Processing Method</span></span>

<span data-ttu-id="66b3f-138">La classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande fournit trois méthodes de traitement d’entrée principales, au moins l’une d’entre elles devant être substituée par votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-138">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="66b3f-139">Pour plus d’informations sur la façon dont Windows PowerShell traite les enregistrements, consultez fonctionnement de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="66b3f-139">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="66b3f-140">Pour tous les types d’entrée, le runtime Windows PowerShell appelle [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour activer le traitement.</span><span class="sxs-lookup"><span data-stu-id="66b3f-140">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="66b3f-141">Si votre applet de commande doit effectuer un prétraitement ou une configuration, elle peut le faire en substituant cette méthode.</span><span class="sxs-lookup"><span data-stu-id="66b3f-141">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="66b3f-142">Windows PowerShell utilise le terme « enregistrement » pour décrire l’ensemble des valeurs de paramètre fournies lors de l’appel d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-142">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="66b3f-143">Si votre applet de commande accepte l’entrée de pipeline, elle doit remplacer la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , et éventuellement la méthode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="66b3f-143">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="66b3f-144">Par exemple, une applet de commande peut substituer les deux méthodes si elle recueille toutes les entrées à l’aide de [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , puis opère sur l’entrée dans son ensemble au lieu d’un élément à la fois, comme le fait l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="66b3f-144">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="66b3f-145">Si votre applet de commande ne prend pas d’entrée de pipeline, elle doit remplacer la méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="66b3f-145">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="66b3f-146">N’oubliez pas que cette méthode est fréquemment utilisée à la place de [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quand l’applet de commande ne peut pas fonctionner sur un élément à la fois, comme c’est le cas pour une applet de commande de tri.</span><span class="sxs-lookup"><span data-stu-id="66b3f-146">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="66b3f-147">Comme cet exemple Get-Proc applet de commande doit recevoir l’entrée de pipeline, il remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) et utilise les implémentations par défaut pour [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="66b3f-147">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="66b3f-148">La substitution [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) récupère les processus et les écrit sur la ligne de commande à l’aide de la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="66b3f-148">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="66b3f-149">Points à retenir au sujet du traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="66b3f-149">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="66b3f-150">La source par défaut pour l’entrée est un objet explicite (par exemple, une chaîne) fourni par l’utilisateur sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-150">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="66b3f-151">Pour plus d’informations, consultez [création d’une applet de commande pour traiter l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="66b3f-151">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="66b3f-152">Une méthode de traitement d’entrée peut également recevoir l’entrée de l’objet de sortie d’une applet de commande en amont sur le pipeline.</span><span class="sxs-lookup"><span data-stu-id="66b3f-152">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="66b3f-153">Pour plus d’informations, consultez [création d’une applet de commande pour traiter l’entrée de pipeline](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="66b3f-153">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="66b3f-154">N’oubliez pas que votre applet de commande peut recevoir l’entrée d’une combinaison de sources de ligne de commande et de pipeline.</span><span class="sxs-lookup"><span data-stu-id="66b3f-154">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="66b3f-155">L’applet de commande en aval peut ne pas retourner pendant une longue période, ou pas du tout.</span><span class="sxs-lookup"><span data-stu-id="66b3f-155">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="66b3f-156">Pour cette raison, la méthode de traitement d’entrée dans votre applet de commande ne doit pas contenir de verrous pendant les appels à [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), en particulier les verrous pour lesquels la portée s’étend au-delà de l’instance d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-156">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66b3f-157">Les applets de commande ne doivent jamais appeler [System. Console. WriteLine \*](/dotnet/api/System.Console.WriteLine) ou son équivalent.</span><span class="sxs-lookup"><span data-stu-id="66b3f-157">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="66b3f-158">Votre applet de commande peut avoir des variables d’objet à nettoyer lorsqu’elle est terminée (par exemple, si elle ouvre un descripteur de fichier dans la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et maintient le handle ouvert pour une utilisation par [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="66b3f-158">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="66b3f-159">Il est important de se souvenir que le runtime Windows PowerShell n’appelle pas toujours la méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , qui doit effectuer un nettoyage d’objet.</span><span class="sxs-lookup"><span data-stu-id="66b3f-159">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="66b3f-160">Par exemple, [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) peut ne pas être appelé si l’applet de commande est annulée à mi-chemin ou si une erreur d’arrêt se produit dans n’importe quelle partie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-160">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="66b3f-161">Par conséquent, une applet de commande qui requiert le nettoyage d’objets doit implémenter le modèle [System. IDisposable](/dotnet/api/System.IDisposable) complet, y compris le finaliseur, afin que le runtime puisse appeler [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing et [System. IDisposable. dispose \*](/dotnet/api/System.IDisposable.Dispose) à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="66b3f-161">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="66b3f-162">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="66b3f-162">Code Sample</span></span>

<span data-ttu-id="66b3f-163">Pour obtenir l’exemple de code C# complet, consultez [exemple GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="66b3f-163">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="66b3f-164">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="66b3f-164">Defining Object Types and Formatting</span></span>

<span data-ttu-id="66b3f-165">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="66b3f-165">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="66b3f-166">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-166">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="66b3f-167">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="66b3f-167">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="66b3f-168">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="66b3f-168">Building the Cmdlet</span></span>

<span data-ttu-id="66b3f-169">Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66b3f-169">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="66b3f-170">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="66b3f-170">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="66b3f-171">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="66b3f-171">Testing the Cmdlet</span></span>

<span data-ttu-id="66b3f-172">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="66b3f-172">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="66b3f-173">Le code de notre exemple d’applet de commande Get-Proc est petit, mais il utilise toujours le runtime Windows PowerShell et un objet .NET existant, ce qui est suffisant pour le rendre utile.</span><span class="sxs-lookup"><span data-stu-id="66b3f-173">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="66b3f-174">Nous allons le tester pour mieux comprendre ce que Get-Proc pouvez faire et comment sa sortie peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="66b3f-174">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="66b3f-175">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="66b3f-175">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="66b3f-176">Démarrez Windows PowerShell et récupérez les processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="66b3f-176">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="66b3f-177">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="66b3f-177">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="66b3f-178">Assignez une variable aux résultats de l’applet de commande pour faciliter la manipulation.</span><span class="sxs-lookup"><span data-stu-id="66b3f-178">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="66b3f-179">Obtient le nombre de processus.</span><span class="sxs-lookup"><span data-stu-id="66b3f-179">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="66b3f-180">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="66b3f-180">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="66b3f-181">Récupérez un processus spécifique.</span><span class="sxs-lookup"><span data-stu-id="66b3f-181">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="66b3f-182">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="66b3f-182">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="66b3f-183">Obtient l’heure de début de ce processus.</span><span class="sxs-lookup"><span data-stu-id="66b3f-183">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="66b3f-184">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="66b3f-184">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="66b3f-185">Obtenez les processus pour lesquels le nombre de handles est supérieur à 500, puis triez le résultat.</span><span class="sxs-lookup"><span data-stu-id="66b3f-185">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="66b3f-186">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="66b3f-186">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="66b3f-187">Utilisez l' `Get-Member` applet de commande pour répertorier les propriétés disponibles pour chaque processus.</span><span class="sxs-lookup"><span data-stu-id="66b3f-187">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="66b3f-188">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="66b3f-188">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="66b3f-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66b3f-189">See Also</span></span>

[<span data-ttu-id="66b3f-190">Création d’une applet de commande pour traiter l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="66b3f-190">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="66b3f-191">Création d’une applet de commande pour traiter l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="66b3f-191">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="66b3f-192">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b3f-192">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="66b3f-193">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="66b3f-193">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="66b3f-194">[Fonctionnement de Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="66b3f-194">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="66b3f-195">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="66b3f-195">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="66b3f-196">Référence Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b3f-196">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="66b3f-197">Exemples d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="66b3f-197">Cmdlet Samples</span></span>](./cmdlet-samples.md)
