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
# <a name="creating-a-cmdlet-without-parameters"></a>Création d’une applet de commande sans paramètre

Cette section décrit comment créer une applet de commande qui Récupère des informations à partir de l’ordinateur local sans l’utilisation de paramètres, puis écrit les informations dans le pipeline. L’applet de commande décrit ici est une applet de commande Get-Process qui extrait des informations sur les processus de l’ordinateur local, puis affiche ces informations à la ligne de commande.

> [!NOTE]
> N’oubliez pas que lors de l’écriture des applets de commande, les assemblys de référence Windows PowerShell® sont téléchargées sur le disque (par défaut dans C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Ils ne sont pas installés dans le Global Assembly Cache (GAC).

## <a name="naming-the-cmdlet"></a>L’applet de commande d’affectation de noms

Un nom de l’applet de commande se compose d’un verbe qui indique l’action de l’applet de commande prend et un nom qui indique les éléments de l’applet de commande agit. Étant donné que cette applet de commande Get-Process exemple récupère des objets de processus, il utilise le verbe « Get », défini par le [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) énumération et le substantif « Proc » pour indiquer que l’applet de commande fonctionne sur les éléments de processus.

Lorsque vous nommez des applets de commande, n’utilisez pas les caractères suivants : #, () {} [] & - / \ $ ; : « ' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Choix d’un substantif.

Vous devez choisir un nom spécifique. Il est préférable d’utiliser un nom au singulier précédé d’une version abrégée du nom du produit. Un exemple de nom d’applet de commande de ce type est «`Get-SQLServer`».

### <a name="choosing-a-verb"></a>Choix d’un verbe

Vous devez utiliser un verbe à partir de l’ensemble des noms de verbe approuvé applet de commande. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Définition de la classe de l’applet de commande

Une fois que vous avez choisi un nom de l’applet de commande, définissez une classe .NET pour implémenter l’applet de commande. Voici la définition de classe pour cette applet de commande Get-Process exemple :

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Notez qu’antérieures à la définition de classe, le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut, avec la syntaxe `[Cmdlet(verb, noun, ...)]`, est utilisé pour identifier cette classe comme une applet de commande. Il s’agit du seul attribut requis pour toutes les applets de commande, et il permet au runtime de Windows PowerShell pour les appeler correctement. Vous pouvez définir des mots clés des attributs pour déclarer plus de la classe si nécessaire. N’oubliez pas que la déclaration d’attribut pour notre exemple de classe GetProcCommand ne déclare que les noms de nom et verbe pour l’applet de commande Get-Process.

> [!NOTE]
> Pour toutes les classes d’attributs de Windows PowerShell, les mots clés que vous pouvez définir correspondent aux propriétés de la classe d’attributs.

Lorsque vous nommez la classe de l’applet de commande, il est conseillé de refléter le nom de l’applet de commande dans le nom de classe. Pour ce faire, utilisez la forme « VerbNounCommand » et remplacez « Verbe » et « Nom » par le verbe et substantif utilisé dans le nom de l’applet de commande. Comme indiqué dans la définition de classe précédentes, l’applet de commande Get-Process exemple définit une classe appelée GetProcCommand, qui dérive de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe de base.

> [!IMPORTANT]
> Si vous souhaitez définir une applet de commande qui accède directement à l’exécution de Windows PowerShell, votre classe .NET doit dériver à partir de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe de base. Pour plus d’informations sur cette classe, consultez [création d’une applet de commande qui définit des jeux de paramètres](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> La classe pour une applet de commande doit être explicitement marquée comme étant publique. Les classes qui ne sont pas marqués comme publics seront internes par défaut et seront introuvable par le runtime de Windows PowerShell.

Windows PowerShell utilise le [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) espace de noms pour ses classes de l’applet de commande. Il est recommandé de placer vos classes de l’applet de commande dans un espace de noms de commandes de votre espace de noms API, par exemple, xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

Le [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fournit trois méthodes de traitement d’entrée principal, au moins un d'entre eux doit remplacer votre applet de commande. Pour plus d’informations sur la façon dont Windows PowerShell traite les enregistrements, consultez [Windows PowerShell fonctionnement](/previous-versions//ms714658(v=vs.85)).

Pour tous les types d’entrée, l’exécution de Windows PowerShell appelle [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour permettre un traitement. Si votre applet de commande doit exécuter certaines de prétraitement ou de la configuration, il peut le faire à en substituant cette méthode.

> [!NOTE]
> Windows PowerShell utilise le terme « enregistrement » pour décrire le jeu de valeurs de paramètre fournie lors d’une applet de commande est appelée.

Si votre applet de commande accepte les entrées de pipeline, il doit remplacer le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode) et éventuellement le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)(méthode). Par exemple, une applet de commande peut remplacer les deux méthodes si il rassemble toutes les entrées à l’aide de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) et opère sur l’entrée comme un entier plutôt qu’un seul élément à la fois, comme le `Sort-Object` applet de commande ne.

Si votre applet de commande n’accepte pas d’entrée de pipeline, il doit substituer la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode). N’oubliez pas que cette méthode est fréquemment utilisée à la place de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) lorsque l’applet de commande ne peut pas fonctionner sur un seul élément à la fois, comme c’est le cas pour une applet de commande de tri.

Étant donné que cette applet de commande Get-Process exemple doit recevoir une entrée de pipeline, ce paramètre remplace le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode) et utilise les implémentations par défaut pour [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override récupère les processus et les écrit dans la ligne de commande à l’aide de la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode).

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

#### <a name="things-to-remember-about-input-processing"></a>Points à retenir sur le traitement d’entrée

- La source par défaut pour l’entrée est un objet explicit (par exemple, une chaîne) fourni par l’utilisateur sur la ligne de commande. Pour plus d’informations, consultez [création d’une applet de commande pour l’entrée du processus de ligne de commande](./adding-parameters-that-process-command-line-input.md).

- Une méthode de traitement des entrées peuvent également recevoir l’entrée à partir de l’objet de sortie d’une applet de commande en amont sur le pipeline. Pour plus d’informations, consultez [création d’une applet de commande pour l’entrée de Pipeline de processus](./adding-parameters-that-process-pipeline-input.md). N’oubliez pas que votre applet de commande peut recevoir l’entrée d’une combinaison de ligne de commande et un pipeline sources.

- L’applet de commande en aval ne renvoie pas pendant une longue période, ou pas du tout. Pour cette raison, l’entrée de méthode dans votre applet de commande de traitement doit contient pas de verrous pendant les appels aux [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), en particulier les verrous dont la portée s’étend au-delà de l’instance de l’applet de commande.

> [!IMPORTANT]
> Applets de commande ne doit jamais appeler [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) ou son équivalent.

- Votre applet de commande peut avoir des variables d’objet pour la nettoyer lorsqu’elle est terminée de traitement (par exemple, si elle s’ouvre un descripteur de fichier dans le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode) et conserve le handle ouvrir pour une utilisation par [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Il est important de se rappeler que le runtime Windows PowerShell n’appelle pas toujours le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode), qui doit effectuer un nettoyage de l’objet.

Par exemple, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ne peut pas être appelée si l’applet de commande est annulée à mi-chemin ou si un arrêt de l’erreur se produit dans n’importe quelle partie de l’applet de commande. Par conséquent, une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle, y compris le finaliseur, afin que le runtime peut appeler à la fois [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) et [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) à la fin du traitement.

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [exemple GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET. Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, vous devez l’inscrire avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande. Le code de notre applet de commande Get-Process exemple est petite, mais il utilise toujours le runtime Windows PowerShell et un objet .NET existant, ce qui est suffisant pour rendre utiles. Nous allons tester pour mieux comprendre ce que Get-Process peut faire et comment sa sortie peut être utilisée. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Démarrez Windows PowerShell, et obtient les processus en cours en cours d’exécution sur l’ordinateur.

    ```powershell
    get-proc
    ```

    La sortie suivante s’affiche.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Attribuez une variable pour les résultats de l’applet de commande pour une manipulation plus facile.

    ```powershell
    $p=get-proc
    ```

3. Obtenir le nombre de processus.

    ```powershell
    $p.length
    ```

    La sortie suivante s’affiche.

    ```output
    63
    ```

4. Récupérer un processus spécifique.

    ```powershell
    $p[6]
    ```

    La sortie suivante s’affiche.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Obtenir l’heure de début de ce processus.

    ```powershell
    $p[6].starttime
    ```

    La sortie suivante s’affiche.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Obtenir les processus pour lesquels le nombre de handles est supérieur à 500 et trier le résultat.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    La sortie suivante s’affiche.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Utilisez le `Get-Member` applet de commande pour répertorier les propriétés disponibles pour chaque processus.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    La sortie suivante s’affiche.

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

[Création d’une applet de commande pour traiter l’entrée de Pipeline](./adding-parameters-that-process-pipeline-input.md)

[Comment créer une applet de commande Windows PowerShell](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extension des Types d’objets et mise en forme](/previous-versions//ms714665(v=vs.85))

[Fonctionnement de Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85))

[Référence Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)