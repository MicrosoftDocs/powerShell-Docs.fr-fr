---
title: Création d’une applet de commande sans paramètres | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.openlocfilehash: a14d25660d596ebd12cd7d74b607eab6ac9fd1be
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784382"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Création d’une applet de commande sans paramètre

Cette section décrit comment créer une applet de commande qui récupère des informations à partir de l’ordinateur local sans utiliser de paramètres, puis écrit les informations dans le pipeline. L’applet de commande décrite ici est une applet de commande « obtenir-proc » qui récupère des informations sur les processus de l’ordinateur local, puis affiche ces informations sur la ligne de commande.

> [!NOTE]
> Sachez que lors de l’écriture d’applets de commande, les assemblys de référence de® Windows PowerShell sont téléchargés sur le disque (par défaut, à l’emplacement C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Ils ne sont pas installés dans le global assembly cache (GAC).

## <a name="naming-the-cmdlet"></a>Attribution d’un nom à l’applet de commande

Un nom d’applet de commande se compose d’un verbe qui indique l’action prise par l’applet de commande et d’un nom qui indique les éléments sur lesquels l’applet de commande agit. Étant donné que cet exemple d’applet de commande « obtenir-proc » récupère des objets de processus, il utilise le verbe « obtenir », défini par l’énumération [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) , et le nom « proc » pour indiquer que l’applet de commande fonctionne sur les éléments de processus.

Quand vous nommez des applets de commande, n’utilisez pas les caractères suivants : #, () {} [] &-/\ $;: "' <> &#124;  ? @ ` .

### <a name="choosing-a-noun"></a>Choix d’un nom

Vous devez choisir un nom spécifique. Il est préférable d’utiliser un nom singulier préfixé avec une version abrégée du nom du produit. Un exemple de nom d’applet de commande de ce type est « `Get-SQLServer` ».

### <a name="choosing-a-verb"></a>Choix d’un verbe

Vous devez utiliser un verbe de l’ensemble des noms de verbe d’applet de commande approuvés. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

## <a name="defining-the-cmdlet-class"></a>Définition de la classe cmdlet

Une fois que vous avez choisi un nom d’applet de commande, définissez une classe .NET pour implémenter l’applet de commande. Voici la définition de classe pour cet exemple d’applet de commande-proc :

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Notez que, avant la définition de classe, l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , avec la syntaxe `[Cmdlet(verb, noun, ...)]` , est utilisé pour identifier cette classe en tant qu’applet de commande. Il s’agit du seul attribut requis pour toutes les applets de commande et permet au runtime Windows PowerShell de les appeler correctement. Vous pouvez définir des mots clés d’attribut pour déclarer davantage la classe si nécessaire. Sachez que la déclaration d’attribut pour notre exemple de classe GetProcCommand déclare uniquement les noms de substantif et de verbe pour l’applet de commande « obtenir-proc ».

> [!NOTE]
> Pour toutes les classes d’attributs Windows PowerShell, les mots clés que vous pouvez définir correspondent aux propriétés de la classe d’attributs.

Lorsque vous nommez la classe de l’applet de commande, il est recommandé de refléter le nom de l’applet de commande dans le nom de la classe. Pour ce faire, utilisez la forme « VerbNounCommand » et remplacez « Verb » et « substantif » par le verbe et le substantif utilisés dans le nom de l’applet de commande. Comme indiqué dans la définition de classe précédente, l’applet de commande Sample-proc définit une classe appelée GetProcCommand, qui dérive de la classe de base [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande.

> [!IMPORTANT]
> Si vous souhaitez définir une applet de commande qui accède directement au runtime Windows PowerShell, votre classe .NET doit dériver de la classe de base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Pour plus d’informations sur cette classe, consultez [création d’une applet de commande qui définit des jeux de paramètres](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> La classe d’une applet de commande doit être explicitement marquée comme publique. Les classes qui ne sont pas marquées comme publiques sont par défaut internes et ne sont pas détectées par le runtime Windows PowerShell.

Windows PowerShell utilise l’espace de noms [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) pour ses classes d’applet de commande. Il est recommandé de placer vos classes d’applet de commande dans un espace de noms Commands de votre espace de noms d’API, par exemple, xxx. PS. Commands.

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

La classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande fournit trois méthodes de traitement d’entrée principales, au moins l’une d’entre elles devant être substituée par votre applet de commande. Pour plus d’informations sur la façon dont Windows PowerShell traite les enregistrements, consultez fonctionnement de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

Pour tous les types d’entrée, le runtime Windows PowerShell appelle [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour activer le traitement. Si votre applet de commande doit effectuer un prétraitement ou une configuration, elle peut le faire en substituant cette méthode.

> [!NOTE]
> Windows PowerShell utilise le terme « enregistrement » pour décrire l’ensemble des valeurs de paramètre fournies lors de l’appel d’une applet de commande.

Si votre applet de commande accepte l’entrée de pipeline, elle doit remplacer la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , et éventuellement la méthode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Par exemple, une applet de commande peut substituer les deux méthodes si elle recueille toutes les entrées à l’aide de [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , puis opère sur l’entrée dans son ensemble au lieu d’un élément à la fois, comme le fait l’applet de commande `Sort-Object` .

Si votre applet de commande ne prend pas d’entrée de pipeline, elle doit remplacer la méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . N’oubliez pas que cette méthode est fréquemment utilisée à la place de [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quand l’applet de commande ne peut pas fonctionner sur un élément à la fois, comme c’est le cas pour une applet de commande de tri.

Étant donné que cet exemple d’applet de commande Receive-proc doit recevoir l’entrée de pipeline, elle remplace la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) et utilise les implémentations par défaut pour [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). La substitution [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) récupère les processus et les écrit sur la ligne de commande à l’aide de la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

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

#### <a name="things-to-remember-about-input-processing"></a>Points à retenir au sujet du traitement des entrées

- La source par défaut pour l’entrée est un objet explicite (par exemple, une chaîne) fourni par l’utilisateur sur la ligne de commande. Pour plus d’informations, consultez [création d’une applet de commande pour traiter l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md).

- Une méthode de traitement d’entrée peut également recevoir l’entrée de l’objet de sortie d’une applet de commande en amont sur le pipeline. Pour plus d’informations, consultez [création d’une applet de commande pour traiter l’entrée de pipeline](./adding-parameters-that-process-pipeline-input.md). N’oubliez pas que votre applet de commande peut recevoir l’entrée d’une combinaison de sources de ligne de commande et de pipeline.

- L’applet de commande en aval peut ne pas retourner pendant une longue période, ou pas du tout. Pour cette raison, la méthode de traitement d’entrée dans votre applet de commande ne doit pas contenir de verrous pendant les appels à [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), en particulier les verrous pour lesquels la portée s’étend au-delà de l’instance d’applet de commande.

> [!IMPORTANT]
> Les applets de commande ne doivent jamais appeler [System. Console. WriteLine *](/dotnet/api/System.Console.WriteLine) ou son équivalent.

- Votre applet de commande peut avoir des variables d’objet à nettoyer lorsqu’elle est terminée (par exemple, si elle ouvre un descripteur de fichier dans la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et maintient le handle ouvert pour une utilisation par [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Il est important de se souvenir que le runtime Windows PowerShell n’appelle pas toujours la méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , qui doit effectuer un nettoyage d’objet.

Par exemple, [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) peut ne pas être appelé si l’applet de commande est annulée à mi-chemin ou si une erreur d’arrêt se produit dans n’importe quelle partie de l’applet de commande. Par conséquent, une applet de commande qui requiert le nettoyage d’objets doit implémenter le modèle [System. IDisposable](/dotnet/api/System.IDisposable) complet, y compris le finaliseur, afin que le runtime puisse appeler [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing et [System. IDisposable. dispose *](/dotnet/api/System.IDisposable.Dispose) à la fin du traitement.

## <a name="code-sample"></a>Exemple de code

Pour obtenir l’exemple de code C# complet, consultez [exemple GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande. Le code pour notre applet de commande Sample-proc est petit, mais il utilise toujours le runtime Windows PowerShell et un objet .NET existant, ce qui est suffisant pour le rendre utile. Nous allons le tester pour mieux comprendre ce que peut faire et comment sa sortie peut être utilisée. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Démarrez Windows PowerShell et récupérez les processus en cours d’exécution sur l’ordinateur.

    ```powershell
    get-proc
    ```

    La sortie suivante apparaît.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Assignez une variable aux résultats de l’applet de commande pour faciliter la manipulation.

    ```powershell
    $p=get-proc
    ```

3. Obtient le nombre de processus.

    ```powershell
    $p.length
    ```

    La sortie suivante apparaît.

    ```output
    63
    ```

4. Récupérez un processus spécifique.

    ```powershell
    $p[6]
    ```

    La sortie suivante apparaît.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Obtient l’heure de début de ce processus.

    ```powershell
    $p[6].starttime
    ```

    La sortie suivante apparaît.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Obtenez les processus pour lesquels le nombre de handles est supérieur à 500, puis triez le résultat.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    La sortie suivante apparaît.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Utilisez l' `Get-Member` applet de commande pour répertorier les propriétés disponibles pour chaque processus.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    La sortie suivante apparaît.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Voir aussi

[Création d’une applet de commande pour traiter l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Création d’une applet de commande pour traiter l’entrée de pipeline](./adding-parameters-that-process-pipeline-input.md)

[Comment créer une applet de commande Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Fonctionnement de Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))

[Référence Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applets de commande](./cmdlet-samples.md)
