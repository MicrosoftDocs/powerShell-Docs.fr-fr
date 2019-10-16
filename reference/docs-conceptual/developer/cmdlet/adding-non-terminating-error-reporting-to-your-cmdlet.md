---
title: Ajout d’un rapport d’erreurs sans fin d’achèvement à votre applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364608"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Ajout de rapport d’erreurs sans fin d’exécution à votre applet de commande

Les applets de commande peuvent signaler des erreurs qui ne se terminent pas en appelant la méthode [System. Management. Automation. applet de commande. WriteError][] tout en continuant à fonctionner sur l’objet d’entrée actuel ou sur d’autres objets de pipeline entrants.
Cette section explique comment créer une applet de commande qui signale les erreurs qui ne se terminent pas à partir de ses méthodes de traitement d’entrée.

Pour les erreurs qui ne se terminent pas (ainsi que les erreurs de fin), l’applet de commande doit passer un objet [System. Management. Automation. ErrorRecord][] qui identifie l’erreur.
Chaque enregistrement d’erreur est identifié par une chaîne unique appelée « identificateur d’erreur ».
En plus de l’identificateur, la catégorie de chaque erreur est spécifiée par des constantes définies par une énumération [System. Management. Automation. ErrorCategory][] .
L’utilisateur peut afficher les erreurs en fonction de sa catégorie en affectant à la variable `$ErrorView` la valeur « CategoryView ».

Pour plus d’informations sur les enregistrements d’erreurs, consultez la page [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.
Cette applet de commande récupère les informations de processus, le nom du verbe choisi ici est « obtenir ».
(Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](approved-verbs-for-windows-powershell-commands.md)de commande.

Voici la définition de cette applet de commande « obtenir-proc ».
Les détails de cette définition sont donnés dans [création de votre première applet](creating-a-cmdlet-without-parameters.md)de commande.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Définition des paramètres

Si nécessaire, votre applet de commande doit définir des paramètres pour le traitement de l’entrée.
Cette applet de commande obtenir-proc définit un paramètre **Name** comme décrit dans [Ajout de paramètres qui traitent l’entrée de ligne de commande](adding-parameters-that-process-command-line-input.md).

Voici la déclaration de paramètre pour le paramètre **Name** de l’applet de commande « obtenir-proc ».

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>Substitution des méthodes de traitement d’entrée

Toutes les applets de commande doivent remplacer au moins l’une des méthodes de traitement d’entrée fournies par la classe [System. Management. Automation. applet de commande][] de commande.
Ces méthodes sont décrites dans [création de votre première applet](creating-a-cmdlet-without-parameters.md)de commande.

> [!NOTE]
> Votre applet de commande doit gérer chaque enregistrement de la manière la plus indépendante possible.

Cette applet de commande obtenir-proc remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord][] pour gérer le paramètre **Name** de l’entrée fournie par l’utilisateur ou un script.
Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.
Les détails de ce remplacement sont fournis lors de [la création de votre première applet](creating-a-cmdlet-without-parameters.md)de commande.

### <a name="things-to-remember-when-reporting-errors"></a>Points à retenir lors de la création de rapports d’erreurs

L’objet [System. Management. Automation. ErrorRecord][] que l’applet de commande passe lors de l’écriture d’une erreur requiert une exception au niveau de son noyau.
Suivez les instructions .NET lors de la détermination de l’exception à utiliser.
Fondamentalement, si l’erreur est sémantiquement identique à une exception existante, l’applet de commande doit utiliser ou dériver de cette exception.
Dans le cas contraire, elle doit dériver une nouvelle exception ou une nouvelle hiérarchie d’exception directement à partir de la classe [System. exception][] .

Lorsque vous créez des identificateurs d’erreur (accessibles par le biais de la propriété FullyQualifiedErrorId de la classe ErrorRecord), gardez les points suivants à l’esprit.

- Utilisez des chaînes ciblées à des fins de diagnostic afin que, lors de l’inspection de l’identificateur complet, vous puissiez déterminer l’origine de l’erreur et l’origine de l’erreur.

- Un identificateur d’erreur complet bien formé peut être comme suit.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Notez que dans l’exemple précédent, l’identificateur d’erreur (le premier jeton) désigne l’erreur et la partie restante indique l’origine de l’erreur.

- Pour les scénarios plus complexes, l’identificateur d’erreur peut être un jeton séparé par des points qui peut être analysé lors de l’inspection.
  Cela vous permet de créer des branches dans les parties de l’identificateur d’erreur, ainsi que l’identificateur d’erreur et la catégorie d’erreur.

L’applet de commande doit assigner des identificateurs d’erreur spécifiques à différents chemins de code.
Gardez à l’esprit les informations suivantes pour l’affectation des identificateurs d’erreur :

- Un identificateur d’erreur doit rester constant tout au long du cycle de vie des applets de commande.
  Ne modifiez pas la sémantique d’un identificateur d’erreur entre les versions de l’applet de commande.

- Utilisez du texte pour un identificateur d’erreur que tersely correspond à l’erreur signalée.
  N’utilisez pas d’espace blanc ou de ponctuation.

- Demander à votre applet de commande de générer uniquement des identificateurs d’erreur qui sont reproductibles.
  Par exemple, il ne doit pas générer un identificateur qui comprend un identificateur de processus.
  Les identificateurs d’erreur sont utiles à un utilisateur uniquement lorsqu’ils correspondent à des identificateurs qui sont visibles par d’autres utilisateurs rencontrant le même problème.

Les exceptions non gérées ne sont pas interceptées par PowerShell dans les conditions suivantes :

- Si une applet de commande crée un nouveau thread et que le code qui s’exécute dans ce thread lève une exception non gérée, PowerShell n’intercepte pas l’erreur et met fin au processus.

- Si un objet a du code dans son destructeur ou des méthodes dispose qui provoquent une exception non gérée, PowerShell n’intercepte pas l’erreur et met fin au processus.

## <a name="reporting-nonterminating-errors"></a>Signalement d’erreurs qui ne se terminent pas

L’une des méthodes de traitement d’entrée peut signaler une erreur sans fin d’exécution au flux de sortie à l’aide de la méthode [System. Management. Automation. applet de commande. WriteError][] .

Voici un exemple de code de cette applet de commande « obtenir-proc » qui illustre l’appel à [System. Management. Automation. applet de commande. WriteError][] à partir de la substitution de la méthode [System. Management. Automation. applet de commande. ProcessRecord][] .
Dans ce cas, l’appel est effectué si l’applet de commande ne parvient pas à trouver un processus pour un identificateur de processus spécifié.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Points à retenir concernant l’écriture d’erreurs qui ne se terminent pas

Pour une erreur qui ne se termine pas, l’applet de commande doit générer un identificateur d’erreur spécifique pour chaque objet d’entrée spécifique.

Une applet de commande doit souvent modifier l’action PowerShell produite par une erreur qui ne se termine pas.
Pour ce faire, vous devez définir les paramètres `ErrorAction` et `ErrorVariable`.
Si vous définissez le paramètre `ErrorAction`, l’applet de commande présente les options utilisateur [System. Management. Automation. PréférenceAction][]. vous pouvez également influencer directement l’action en définissant la variable `$ErrorActionPreference`.

L’applet de commande peut enregistrer les erreurs sans fin d’utilisation dans une variable à l’aide du paramètre `ErrorVariable`, qui n’est pas affecté par le paramètre de `ErrorAction`.
Les échecs peuvent être ajoutés à une variable d’erreur existante en ajoutant un signe plus (+) au début du nom de la variable.

## <a name="code-sample"></a>Exemple de code

Pour obtenir l' C# exemple de code complet, consultez [exemple GetProcessSample04](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Définir les types d’objets et la mise en forme

PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.
Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.
Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.
Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.
Nous allons tester l’exemple d’applet de commande Sample-proc pour voir s’il signale une erreur :

- Démarrez PowerShell et utilisez l’applet de commande obtenir-proc pour récupérer les processus nommés « TEST ».

    ```powershell
    PS> get-proc -name test
    ```

La sortie suivante s’affiche.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Voir aussi

[Ajout de paramètres qui traitent l’entrée de pipeline](./adding-parameters-that-process-pipeline-input.md)

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)

[Extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Informations de référence sur Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)

[System. exception]: /dotnet/api/System.Exception
[System. Management. Automation. PréférenceAction]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. applet de commande. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. applet de commande. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. applet de commande]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
