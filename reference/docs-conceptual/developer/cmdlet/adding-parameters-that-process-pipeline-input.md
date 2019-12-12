---
title: Ajout de paramètres qui traitent l’entrée de pipeline | Microsoft Docs
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
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364598"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Ajout de paramètres qui traitent l’entrée du pipeline

Une source d’entrée pour une applet de commande est un objet sur le pipeline qui provient d’une applet de commande en amont. Cette section décrit comment ajouter un paramètre à l’applet de commande « obtenir-proc » (décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande) afin que l’applet de commande puisse traiter les objets de pipeline.

Cette applet de commande Accept-proc utilise un paramètre `Name` qui accepte l’entrée d’un objet pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis affiche des informations sur les processus sur la ligne de commande.

## <a name="defining-the-cmdlet-class"></a>Définition de la classe cmdlet

La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande. Cette applet de commande récupère les informations de processus, le nom du verbe choisi ici est « obtenir ». (Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

Voici la définition de cette applet de commande « obtenir-proc ». Les détails de cette définition sont donnés dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Définition de l’entrée à partir du pipeline

Cette section décrit comment définir une entrée à partir du pipeline pour une applet de commande. Cette applet de commande obtenir-proc définit une propriété qui représente le paramètre `Name` comme décrit dans [Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md). (Pour obtenir des informations générales sur la déclaration des paramètres, consultez la rubrique.)

Toutefois, lorsqu’une applet de commande doit traiter l’entrée de pipeline, elle doit avoir ses paramètres liés aux valeurs d’entrée par le runtime Windows PowerShell. Pour ce faire, vous devez ajouter le mot clé `ValueFromPipeline` ou ajouter le mot clé `ValueFromPipelineByProperty` à la déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Spécifiez le mot clé `ValueFromPipeline` si l’applet de commande accède à l’objet d’entrée complet. Spécifiez le `ValueFromPipelineByProperty` si l’applet de commande accède uniquement à une propriété de l’objet.

Voici la déclaration de paramètre pour le paramètre `Name` de cette applet de commande Accept-proc qui accepte l’entrée de pipeline.

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

La déclaration précédente définit le mot clé `ValueFromPipeline` sur `true` afin que le runtime Windows PowerShell lie le paramètre à l’objet entrant si l’objet est du même type que le paramètre, ou s’il peut être forcé au même type. Le mot clé `ValueFromPipelineByPropertyName` est également défini sur `true` afin que le runtime Windows PowerShell vérifie l’objet entrant pour une propriété `Name`. Si l’objet entrant possède une telle propriété, le runtime lie le paramètre `Name` à la propriété `Name` de l’objet entrant.

> [!NOTE]
> La valeur du mot clé d’attribut `ValueFromPipeline` pour un paramètre est prioritaire sur le paramètre du mot clé `ValueFromPipelineByPropertyName`.

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

Si votre applet de commande doit gérer l’entrée de pipeline, elle doit remplacer les méthodes de traitement d’entrée appropriées. Les méthodes de traitement d’entrée de base sont introduites lors de la [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.

Cette applet de commande obtenir-proc remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour gérer le `Name` entrée de paramètre fournie par l’utilisateur ou un script. Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni. Notez que dans [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) est le mécanisme de sortie permettant d’envoyer des objets de sortie au pipeline. Le deuxième paramètre de cet appel, `enumerateCollection`, est défini sur `true` pour indiquer au runtime Windows PowerShell d’énumérer le tableau d’objets de processus et d’écrire un processus à la fois sur la ligne de commande.

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

Pour obtenir l' C# exemple de code complet, consultez [exemple GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell via un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, testez-la en l’exécutant sur la ligne de commande. Par exemple, testez le code de l’applet de commande Sample. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- À l’invite Windows PowerShell, entrez les commandes suivantes pour récupérer les noms de processus via le pipeline.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

La sortie suivante s'affiche.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Entrez les lignes suivantes pour obtenir les objets processus qui ont une propriété `Name` à partir des processus appelés « IEXPLORE ». Cet exemple utilise l’applet de commande `Get-Process` (fournie par Windows PowerShell) en tant que commande amont pour récupérer les processus « IEXPLORE ».

    ```powershell
    PS> get-process iexplore | get-proc
    ```

La sortie suivante s'affiche.

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

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))

[Informations de référence sur Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)
