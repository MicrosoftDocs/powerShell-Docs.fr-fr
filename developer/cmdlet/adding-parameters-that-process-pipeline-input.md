---
title: Ajout de paramètres qui traitent l’entrée de Pipeline | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068757"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Ajout de paramètres qui traitent l’entrée du pipeline

Une source d’entrée pour une applet de commande est un objet sur le pipeline qui provient d’une applet de commande en amont. Cette section décrit comment ajouter un paramètre à l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)) afin que l’applet de commande peut traiter les objets pipeline.

Cette applet de commande Get-Process utilise un `Name` paramètre qui accepte les entrées à partir d’un objet de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis, puis affiche des informations sur les processus à la ligne de commande.

Rubriques de cette section sont les suivantes :

- [Définition de la classe de l’applet de commande](#Defining-the-Cmdlet-Class)

- [Définition d’entrée provenant du Pipeline](#Defining-Input-from-the-Pipeline)

- [Substitution d’une méthode de traitement des entrées](#Overriding-an-Input-Processing-Method)

- [Exemple de code](#Code-Sample)

- [Définition des Types d’objets et mise en forme](#Defining-Object-Types-and-Formatting)

- [Création de l’applet de commande](#Building-the-Cmdlet)

- [Test de l’applet de commande](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Définition de la classe de l’applet de commande

La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande. Cette applet de commande récupère des informations de processus, par conséquent, le nom du verbe choisi ici est « Get ». (Presque toute sorte de l’applet de commande qui est capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

Voici la définition de cette applet de commande Get-Process. Informations de cette définition sont fournies dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Définition d’entrée provenant du Pipeline

Cette section décrit comment définir l’entrée du pipeline pour une applet de commande. Cette applet de commande Get-Process définit une propriété qui représente le `Name` paramètre comme décrit dans [ajoutant des paramètres de cette entrée de ligne de commande de processus](./adding-parameters-that-process-command-line-input.md). (Consultez la rubrique appropriée pour des informations générales sur la déclaration de paramètres).

Toutefois, quand une applet de commande doit traiter l’entrée de pipeline, il doit avoir ses paramètres liés aux valeurs d’entrée par le runtime de Windows PowerShell. Pour ce faire, vous devez ajouter le `ValueFromPipeline` mot clé ou d’ajouter le `ValueFromPipelineByProperty` mot clé à la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration de l’attribut. Spécifiez le `ValueFromPipeline` mot clé si l’applet de commande accède à l’objet d’entrée complet. Spécifiez le `ValueFromPipelineByProperty` si l’applet de commande accède à une propriété de l’objet uniquement.

Voici la déclaration de paramètre pour le `Name` paramètre de cette applet de commande Get-Process qui accepte les entrées de pipeline.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

Les ensembles de déclaration précédente le `ValueFromPipeline` mot clé à `true` afin que le runtime Windows PowerShell lier le paramètre à l’objet entrant, si l’objet est le même type que le paramètre, ou si elle peut être forcé au même type. Le `ValueFromPipelineByPropertyName` mot clé est également défini sur `true` afin que le runtime Windows PowerShell recherche l’objet entrant pour un `Name` propriété. Si l’objet entrant a une telle propriété, le runtime crée une liaison le `Name` paramètre à la `Name` propriété de l’objet entrant.

> [!NOTE]
> Le paramètre de la `ValueFromPipeline` mot clé d’attribut d’un paramètre est prioritaire sur le paramètre pour le `ValueFromPipelineByPropertyName` mot clé.

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

Si votre applet de commande consiste à gérer l’entrée de pipeline, il doit remplacer la méthodes de traitement d’entrée appropriée. Les méthodes de traitement d’entrée de base sont introduites dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).

Cette applet de commande Get-Process remplace le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour gérer la `Name` entrée de paramètre fournie par l’utilisateur ou un script. Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni. Notez que dans [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) correspond à la sortie mécanisme pour envoyer la sortie des objets au pipeline. Le deuxième paramètre de cet appel, `enumerateCollection`, est défini sur `true` indiquer au runtime de Windows PowerShell d’énumérer le tableau d’objets de processus et écrire un seul processus à la fois à la ligne de commande.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [GetProcessSample03 exemple](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net. Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec Windows PowerShell, testez-le en l’exécutant sur la ligne de commande. Par exemple, tester le code de l’applet de commande d’exemple. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- À l’invite Windows PowerShell, entrez les commandes suivantes pour récupérer les noms de processus à travers le pipeline.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

La sortie suivante s’affiche.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Entrez les lignes suivantes pour obtenir les objets de processus qui ont un `Name` propriété des processus appelé « IEXPLORE ». Cet exemple utilise le `Get-Process` applet de commande (fourni par Windows PowerShell) en tant qu’une commande en amont pour récupérer les processus Iexplore « a ».

    ```powershell
    PS> get-process iexplore | get-proc
    ```

La sortie suivante s’affiche.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Voir aussi

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Informations de référence sur Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)
