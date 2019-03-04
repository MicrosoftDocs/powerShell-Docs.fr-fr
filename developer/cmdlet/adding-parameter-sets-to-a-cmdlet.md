---
title: Ajout de paramètre de jeux à une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859265"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Ajout de jeux de paramètres à une applet de commande

Cette section décrit comment ajouter des ensembles de paramètre à l’applet de commande Stop-Process (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)). Comme pour les autres Stop-Process applets de commande décrites dans ce Guide du programmeur, cette applet de commande tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).

Rubriques de cette section sont les suivantes :

- [Choses à savoir sur les jeux de paramètres](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Déclaration de la classe de l’applet de commande](#Declaring-the-Cmdlet-Class)

- [Déclarer des paramètres de l’applet de commande](#Declaring-the-Parameters-of-the-Cmdlet)

- [Substitution d’une méthode de traitement des entrées](#Overriding-an-Input-Processing-Method)

- [Exemple de code](#Declaring-the-Parameters-of-the-Cmdlet)

- [Définition des Types d’objets et mise en forme](#Defining-Object-Types-and-Formatting)

- [Création de l’applet de commande](#Building-the-Cmdlet)

- [Test de l’applet de commande](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Choses à savoir sur les jeux de paramètres

Windows PowerShell définit un paramètre défini en tant que groupe de paramètres qui fonctionnent ensemble. En regroupant les paramètres d’applet de commande, vous pouvez créer une applet de commande unique que vous pouvez modifier ses fonctionnalités en fonction de l’utilisateur spécifie de quel groupe de paramètres.

Est un exemple d’une applet de commande qui utilise deux jeux de paramètres pour définir les différentes fonctionnalités du `Get-EventLog` applet de commande qui est fournie par Windows PowerShell. Cette applet de commande renvoie des informations différentes lorsque l’utilisateur spécifie le `List` ou `LogName` paramètre. Si le `LogName` paramètre est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements donné. Si le `List` paramètre est spécifié, l’applet de commande renvoie des informations sur le journal des fichiers (pas les informations d’événements qu’ils contiennent). Dans ce cas, le `List` et `LogName` paramètres identifient deux jeux de paramètres distincts.

Deux points importants à retenir sur les jeux de paramètres est que le runtime Windows PowerShell n'utilise qu’un seul jeu de paramètres pour une entrée donnée, et que chaque jeu de paramètres doit avoir au moins un paramètre qui est unique pour ce jeu de paramètres.

Pour illustrer ce dernier point, cette applet de commande Stop-Process utilise trois jeux de paramètres : `ProcessName`, `ProcessId`, et `InputObject`. Chacun de ces jeux de paramètre a un paramètre qui n’est pas dans les autres jeux de paramètres. Les jeux de paramètres puissent partager des autres paramètres, mais l’applet de commande utilise les paramètres uniques `ProcessName`, `ProcessId`, et `InputObject` pour identifier le jeu de paramètres que le runtime Windows PowerShell doit utiliser.

## <a name="declaring-the-cmdlet-class"></a>Déclaration de la classe de l’applet de commande

La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande. Pour cette applet de commande, le verbe de cycle de vie « Stop » est utilisé, car l’applet de commande arrête les processus système. Le nom de substantif « Proc » est utilisé, car l’applet de commande fonctionne sur les processus. Dans la déclaration ci-dessous, notez que le nom du verbe et substantif applet de commande sont répercutées dans le nom de la classe de l’applet de commande.

> [!NOTE]
> Pour plus d’informations sur les noms de verbe approuvé applet de commande, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

Le code suivant est la définition de classe pour cette applet de commande Stop-Process.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Déclarer des paramètres de l’applet de commande

Cette applet de commande définit trois paramètres nécessaires comme entrée pour l’applet de commande (ces paramètres définissent également les jeux de paramètres), ainsi qu’un `Force` paramètre qui gère ce que fait l’applet de commande et un `PassThru` paramètre qui détermine si l’applet de commande renvoie un objet de sortie dans le pipeline. Par défaut, cette applet de commande ne passe pas d’un objet à travers le pipeline. Pour plus d’informations sur ces deux derniers paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Déclarer le paramètre de nom

Ce paramètre d’entrée permet à l’utilisateur spécifier les noms des processus à arrêter. Notez que le `ParameterSetName` attribut mot clé de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut spécifie le `ProcessName` paramètre défini pour ce paramètre.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Notez également que l’alias « ProcessName » est attribué à ce paramètre.

### <a name="declaring-the-id-parameter"></a>Déclarer le paramètre Id

Ce paramètre d’entrée permet à l’utilisateur spécifier les identificateurs des processus à arrêter. Notez que le `ParameterSetName` attribut mot clé de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut spécifie le `ProcessId` jeu de paramètres.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Notez également que l’alias « ProcessId » est attribué à ce paramètre.

### <a name="declaring-the-inputobject-parameter"></a>Déclarer le paramètre InputObject

Ce paramètre d’entrée permet à l’utilisateur spécifier un objet d’entrée qui contient des informations sur les processus à arrêter. Notez que le `ParameterSetName` attribut mot clé de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut spécifie le `InputObject` paramètre défini pour ce paramètre.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Notez également que ce paramètre n’a pas d’alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Déclaration de paramètres dans plusieurs jeux de paramètres

Bien qu’il doit y avoir un paramètre unique pour chaque jeu de paramètres, les paramètres peuvent appartenir à plus d’un jeu de paramètres. Dans ce cas, donner du paramètre partagé un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration d’attribut pour chaque jeu auquel le paramètre appartient. Si un paramètre est dans tous les jeux de paramètres, vous uniquement obligé de déclarer l’attribut de paramètre qu’une seule fois et n’avez pas besoin de spécifier que le paramètre de nom du jeu.

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

Chaque applet de commande doit remplacer une méthode de traitement des entrées, ce sera souvent le [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode). Dans cette applet de commande, le [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode est remplacée afin que l’applet de commande peut traiter n’importe quel nombre de processus. Il contient une instruction Select qui appelle une autre méthode basée sur le jeu de paramètres, l’utilisateur a spécifié.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

Les méthodes d’assistance appelées par l’instruction Select ne sont pas décrits ici, mais vous pouvez voir leur implémentation dans l’exemple de code complet dans la section suivante.

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [StopProcessSample04 exemple](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET. Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, vous devez l’inscrire avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec Windows PowerShell, testez-le en l’exécutant sur la ligne de commande. Voici quelques tests qui montrent comment la `ProcessId` et `InputObject` paramètres peuvent être utilisés pour tester leurs jeux de paramètres pour arrêter un processus.

- Avec Windows PowerShell de démarrer, exécutez l’applet de commande Stop-Process avec le `ProcessId` paramètre défini pour arrêter un processus en fonction de son identificateur. Dans ce cas, l’applet de commande utilise le `ProcessId` paramètre défini pour arrêter le processus.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Avec Windows PowerShell de démarrer, exécutez l’applet de commande Stop-Process avec le `InputObject` paramètre défini pour arrêter des processus sur l’objet le bloc-notes récupérée par le `Get-Process` commande.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Voir aussi

[Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)

[Comment créer une applet de commande Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
