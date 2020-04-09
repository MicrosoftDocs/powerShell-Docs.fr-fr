---
title: Ajout de jeux de paramètres à une applet de commande | Microsoft Docs
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
ms.openlocfilehash: 6e17ff3d8ad3f7b2c511b879c913633f320bf511
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978625"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Ajout de jeux de paramètres à une applet de commande

## <a name="things-to-know-about-parameter-sets"></a>Choses à savoir sur les jeux de paramètres

Windows PowerShell définit un jeu de paramètres sous la forme d’un groupe de paramètres qui fonctionnent ensemble. En regroupant les paramètres d’une applet de commande, vous pouvez créer une applet de commande unique qui peut modifier ses fonctionnalités en fonction du groupe de paramètres que l’utilisateur spécifie.

Un exemple d’applet de commande qui utilise deux jeux de paramètres pour définir des fonctionnalités différentes est l’applet de commande `Get-EventLog` fournie par Windows PowerShell. Cette applet de commande retourne des informations différentes lorsque l’utilisateur spécifie le paramètre `List` ou `LogName`. Si le paramètre `LogName` est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements donné. Si le paramètre `List` est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux eux-mêmes (pas sur les informations d’événement qu’elles contiennent). Dans ce cas, les paramètres `List` et `LogName` identifient deux jeux de paramètres distincts.

Deux points importants à retenir concernant les jeux de paramètres sont que le runtime Windows PowerShell n’utilise qu’un seul jeu de paramètres pour une entrée particulière, et que chaque jeu de paramètres doit avoir au moins un paramètre unique pour ce jeu de paramètres.

Pour illustrer ce dernier point, cette applet de commande Stop-proc utilise trois jeux de paramètres : `ProcessName`, `ProcessId`et `InputObject`. Chacun de ces jeux de paramètres possède un paramètre qui n’est pas dans les autres jeux de paramètres. Les jeux de paramètres peuvent partager d’autres paramètres, mais l’applet de commande utilise les paramètres uniques `ProcessName`, `ProcessId`et `InputObject` pour identifier le jeu de paramètres que le runtime Windows PowerShell doit utiliser.

## <a name="declaring-the-cmdlet-class"></a>Déclaration de la classe d’applet de commande

La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande. Pour cette applet de commande, le verbe de cycle de vie « Stop » est utilisé, car l’applet de commande arrête les processus système. Le nom substantif « proc » est utilisé, car l’applet de commande fonctionne sur les processus. Dans la déclaration ci-dessous, Notez que le verbe d’applet de commande et le nom substantif sont reflétés dans le nom de la classe d’applet de commande.

> [!NOTE]
> Pour plus d’informations sur les noms des verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

Le code suivant est la définition de classe pour cette applet de commande Stop-proc.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Déclaration des paramètres de l’applet de commande

Cette applet de commande définit trois paramètres nécessaires comme entrée pour l’applet de commande (ces paramètres définissent également les jeux de paramètres), ainsi qu’un paramètre `Force` qui gère ce que fait l’applet de commande et un paramètre `PassThru` qui détermine si l’applet de commande envoie un objet de sortie via le pipeline. Par défaut, cette applet de commande ne passe pas un objet via le pipeline. Pour plus d’informations sur ces deux derniers paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Déclaration du paramètre Name

Ce paramètre d’entrée permet à l’utilisateur de spécifier les noms des processus à arrêter. Notez que le mot clé `ParameterSetName` attribut de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le jeu de paramètres `ProcessName` pour ce paramètre.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs" range="44-58":::

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

Notez également que l’alias « ProcessName » est donné à ce paramètre.

### <a name="declaring-the-id-parameter"></a>Déclaration du paramètre ID

Ce paramètre d’entrée permet à l’utilisateur de spécifier les identificateurs des processus à arrêter. Notez que le mot clé `ParameterSetName` attribut de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le jeu de paramètres `ProcessId`.

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

Notez également que l’alias « ProcessId » est donné à ce paramètre.

### <a name="declaring-the-inputobject-parameter"></a>Déclaration du paramètre InputObject

Ce paramètre d’entrée permet à l’utilisateur de spécifier un objet d’entrée qui contient des informations sur les processus à arrêter. Notez que le mot clé `ParameterSetName` attribut de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le jeu de paramètres `InputObject` pour ce paramètre.

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

Bien qu’il ne doive y avoir qu’un seul paramètre pour chaque jeu de paramètres, les paramètres peuvent appartenir à plusieurs jeux de paramètres. Dans ce cas, attribuez au paramètre Shared une déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) pour chaque ensemble auquel appartient le paramètre. Si un paramètre est dans tous les jeux de paramètres, vous ne devez déclarer l’attribut de paramètre qu’une seule fois et vous n’avez pas besoin de spécifier le nom du jeu de paramètres.

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

Chaque applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, il s’agit de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Dans cette applet de commande, la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est remplacée afin que l’applet de commande puisse traiter un nombre quelconque de processus. Il contient une instruction SELECT qui appelle une méthode différente selon le jeu de paramètres spécifié par l’utilisateur.

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

Les méthodes d’assistance appelées par l’instruction SELECT ne sont pas décrites ici, mais vous pouvez voir leur implémentation dans l’exemple de code complet dans la section suivante.

## <a name="code-sample"></a>Exemple de code

Pour obtenir l' C# exemple de code complet, consultez [exemple StopProcessSample04](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, testez-la en l’exécutant sur la ligne de commande. Voici quelques tests qui montrent comment les paramètres `ProcessId` et `InputObject` peuvent être utilisés pour tester leurs jeux de paramètres afin d’arrêter un processus.

- Après avoir démarré Windows PowerShell, exécutez l’applet de commande Stop-proc avec le paramètre `ProcessId` défini pour arrêter un processus en fonction de son identificateur. Dans ce cas, l’applet de commande utilise le jeu de paramètres `ProcessId` pour arrêter le processus.

  ```
  PS> stop-proc -Id 444
  Confirm
  Are you sure you want to perform this action?
  Performing operation "stop-proc" on Target "notepad (444)".
  [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
  ```

- Après avoir démarré Windows PowerShell, exécutez l’applet de commande Stop-proc avec le paramètre `InputObject` défini sur arrêter les processus sur l’objet Notepad récupéré par la commande `Get-Process`.

  ```
  PS> get-process notepad | stop-proc
  Confirm
  Are you sure you want to perform this action?
  Performing operation "stop-proc" on Target "notepad (444)".
  [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
  ```

## <a name="see-also"></a>Voir aussi

[Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)

[Comment créer une applet de commande Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
