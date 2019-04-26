---
title: Ajout de rapport d’erreurs à votre applet de commande sans terminaison | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068859"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Ajout de rapport d’erreurs sans fin d’exécution à votre applet de commande

Applets de commande peut signaler des erreurs sans fin d’exécution en appelant le [System.Management.Automation.Cmdlet.WriteError][] (méthode) et continuer à opérer sur l’objet d’entrée actuel ou sur entrant autre pipeline d’objets.
Cette section explique comment créer une applet de commande qui signale les erreurs sans fin d’exécution à partir de ses méthodes de traitement d’entrée.

Pour les erreurs sans fin d’exécution (ainsi que des erreurs avec fin d’exécution), l’applet de commande doit passer un [System.Management.Automation.ErrorRecord][] objet identifiant l’erreur.
Chaque enregistrement d’erreur est identifiée par une chaîne unique appelée le « identificateur de l’erreur ».
En plus de l’identificateur de la catégorie de chaque erreur est spécifiée par les constantes définies par un [System.Management.Automation.ErrorCategory][] énumération.
L’utilisateur peut afficher les erreurs en fonction de leur catégorie en définissant le `$ErrorView` variable « CategoryView ».

Pour plus d’informations sur les enregistrements d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.
Cette applet de commande récupère des informations de processus, par conséquent, le nom du verbe choisi ici est « Get ».
(Presque toute sorte de l’applet de commande qui est capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](approved-verbs-for-windows-powershell-commands.md).

Voici la définition de cette applet de commande Get-Process.
Informations de cette définition sont fournies dans [création de votre première applet de commande](creating-a-cmdlet-without-parameters.md).

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

Si nécessaire, votre applet de commande doit définir les paramètres de traitement d’entrée.
Cette applet de commande Get-Process définit un **nom** paramètre comme décrit dans [Ajout de paramètres qui traitent les entrées de ligne de commande](adding-parameters-that-process-command-line-input.md).

Voici la déclaration de paramètre pour le **nom** paramètre de cette applet de commande Get-Process.

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

## <a name="overriding-input-processing-methods"></a>Substitution de méthodes de traitement d’entrée

Toutes les applets de commande doivent substituer au moins un de l’entrée de traitement des méthodes fournies par le [System.Management.Automation.Cmdlet][] classe.
Ces méthodes sont décrites dans [création de votre première applet de commande](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Votre applet de commande doit gérer chaque enregistrement de manière indépendante que possible.

Se substitue à cette applet de commande Get-Process le [System.Management.Automation.Cmdlet.ProcessRecord][] méthode pour gérer la **nom** paramètre pour l’entrée fournie par l’utilisateur ou un script.
Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.
Détails de ce remplacement sont fournis dans [création de votre première applet de commande](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Points à retenir lors du signalement des erreurs

Le [System.Management.Automation.ErrorRecord][] que l’applet de commande passe lors de l’écriture d’une erreur nécessite une exception à la base de l’objet.
Suivez les instructions de .NET lors de la détermination de l’exception à utiliser.
En fait, si l’erreur est sémantiquement identique à une exception existante, l’applet de commande doit utiliser ou dériver de cette exception.
Sinon, elle doit dériver une nouvelle exception ou la hiérarchie des exceptions directement à partir de la [System.Exception][] classe.

Gardez l’esprit ce qui suit lors de la création d’identificateurs d’erreur (accédés via la propriété FullyQualifiedErrorId de la classe ErrorRecord).

- Chaînes d’utilisation qui sont ciblés pour faciliter le diagnostic afin que lors de l’inspection de l’identificateur complet, vous pouvez déterminer l’erreur qui est et où l’erreur provient.

- Un identificateur d’erreur complet correct peut être comme suit.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Notez que dans l’exemple précédent, l’identificateur de l’erreur (le premier jeton) désigne l’erreur et la partie restante indique d'où provenance l’erreur.

- Pour des scénarios plus complexes, l’identificateur de l’erreur peut être un jeton de point séparé qui peut être analysé à l’inspection.
  Cela permet de que vous créer trop de branche sur les parties de l’identificateur de l’erreur, ainsi que la catégorie d’erreur identificateur et d’erreur.

L’applet de commande doit affecter des identificateurs de l’erreur spécifique aux chemins de code différents.
Gardez les informations suivantes à l’esprit pour l’affectation des identificateurs d’erreur :

- Un identificateur de l’erreur doit rester constant tout au long du cycle de vie d’applet de commande.
  Ne modifiez pas la sémantique d’un identificateur de l’erreur entre les versions de l’applet de commande.

- Utilisez le texte d’un identificateur d’erreur tersely correspond à l’erreur signalée.
  N’utilisez pas les espaces blancs ou des signes de ponctuation.

- Avoir votre applet de commande Générer uniquement des identificateurs d’erreur qui sont reproductibles.
  Par exemple, il ne doit pas générer un identificateur qui inclut un identificateur de processus.
  Identificateurs d’erreur sont utiles à un utilisateur uniquement lorsqu’ils correspondent aux identificateurs sont visibles par d’autres utilisateurs rencontrent le même problème.

Exceptions non gérées ne sont pas interceptées par PowerShell dans les conditions suivantes :

- Si une applet de commande crée un nouveau thread et du code en cours d’exécution dans ce thread lève une exception non gérée, PowerShell n’intercepte pas l’erreur et le processus prendra fin.

- Si un objet possède un code qui lève une exception non gérée dans son destructeur ou les méthodes Dispose, PowerShell n’intercepte pas l’erreur et le processus prendra fin.

## <a name="reporting-nonterminating-errors"></a>Rapports d’erreurs sans fin d’exécution

L’un des méthodes de traitement d’entrée peut signaler une erreur sans fin d’exécution pour le flux de sortie à l’aide de la [System.Management.Automation.Cmdlet.WriteError][] (méthode).

Voici un exemple de code à partir de cette applet de commande Get-Process qui illustre l’appel de [System.Management.Automation.Cmdlet.WriteError][] à partir de dans la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord][] (méthode).
Dans ce cas, l’appel est effectué si l’applet de commande ne peut pas trouver un processus pour un identificateur de processus spécifié.

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Points à retenir sur l’écriture des erreurs sans fin d’exécution

Pour une erreur sans fin d’exécution, l’applet de commande doit générer un identificateur de l’erreur spécifique pour chaque objet d’entrée spécifique.

Une applet de commande doit fréquemment modifier l’action PowerShell produite par une erreur sans fin d’exécution.
Il peut le faire en définissant le `ErrorAction` et `ErrorVariable` paramètres.
Si la définition de la `ErrorAction` paramètre, l’applet de commande présente les options utilisateur [System.Management.Automation.ActionPreference][], vous pouvez également directement influencer l’action en définissant le `$ErrorActionPreference` variable.

L’applet de commande peut enregistrer des erreurs sans fin d’exécution dans une variable à l’aide du `ErrorVariable` paramètre, qui n’est pas affectée par la valeur de `ErrorAction`.
Échecs peuvent être ajoutés à une variable d’erreur existant en ajoutant un signe plus (+) devant le nom de variable.

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [GetProcessSample04 exemple](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Définir les Types d’objets et la mise en forme

PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.
Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande.
Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, vous devez l’inscrire avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.
Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.
Testons l’applet de commande Get-Process exemple pour voir si elle signale une erreur :

- Démarrez PowerShell et utilisez l’applet de commande Get-Process pour récupérer les processus nommés « TEST ».

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

[Ajout de paramètres d’entrée de Pipeline de processus](./adding-parameters-that-process-pipeline-input.md)

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Informations de référence sur Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
