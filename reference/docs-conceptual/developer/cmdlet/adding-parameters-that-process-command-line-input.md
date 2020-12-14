---
ms.date: 09/13/2016
ms.topic: reference
title: Ajout de paramètres qui traitent l’entrée de la ligne de commande
description: Ajout de paramètres qui traitent l’entrée de la ligne de commande
ms.openlocfilehash: f20469d366330aa787fbc16e4f0a76e67fc7c6db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354607"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Ajout de paramètres qui traitent l’entrée de la ligne de commande

Une source d’entrée pour une applet de commande est la ligne de commande. Cette rubrique explique comment ajouter un paramètre à l’applet de commande `Get-Proc` (qui est décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande) afin que l’applet de commande puisse traiter l’entrée de l’ordinateur local en fonction d’objets explicites passés à l’applet de commande. L' `Get-Proc` applet de commande décrite ici récupère les processus en fonction de leurs noms, puis affiche des informations sur les processus à partir d’une invite de commandes.

## <a name="defining-the-cmdlet-class"></a>Définition de la classe cmdlet

La première étape de la création des applets de commande consiste à nommer l’applet de commande et la déclaration de la classe .NET Framework qui implémente l’applet de commande. Cette applet de commande récupère les informations sur le processus. le nom du verbe choisi ici est « obtenir ». (Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

Voici la déclaration de classe pour l' `Get-Proc` applet de commande. Des informations détaillées sur cette définition sont fournies dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Déclarer des paramètres

Un paramètre d’applet de commande permet à l’utilisateur de fournir une entrée à l’applet de commande. Dans l’exemple suivant, `Get-Proc` et `Get-Member` sont les noms des applets de commande canalisées, et `MemberType` est un paramètre de l’applet de commande `Get-Member` . Le paramètre a l’argument « Property ».

**Bloc de> PS-proc ; `get-member` -MemberType, propriété**

Pour déclarer des paramètres pour une applet de commande, vous devez d’abord définir les propriétés qui représentent les paramètres. Dans l' `Get-Proc` applet de commande, le seul paramètre est `Name` , qui, dans ce cas, représente le nom de l’objet de processus .NET Framework à récupérer. Par conséquent, la classe d’applet de commande définit une propriété de type chaîne pour accepter un tableau de noms.

Voici la déclaration de paramètre pour le `Name` paramètre de l' `Get-Proc` applet de commande.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Pour informer le runtime Windows PowerShell que cette propriété est le `Name` paramètre, un attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) est ajouté à la définition de propriété. La syntaxe de base pour déclarer cet attribut est `[Parameter()]` .

> [!NOTE]
> Un paramètre doit être explicitement marqué comme public. Les paramètres qui ne sont pas marqués comme étant des paramètres par défaut publics et internes sont introuvables par le runtime Windows PowerShell.

Cette applet de commande utilise un tableau de chaînes pour le `Name` paramètre. Si possible, votre applet de commande doit également définir un paramètre en tant que tableau, car cela permet à l’applet de commande d’accepter plusieurs éléments.

#### <a name="things-to-remember-about-parameter-definitions"></a>Points à retenir sur les définitions de paramètres

- Les noms de paramètres et les types de données Windows PowerShell prédéfinis doivent être réutilisés autant que possible pour garantir la compatibilité de votre applet de commande avec les applets de commande Windows PowerShell. Par exemple, si toutes les applets de commande utilisent le `Id` nom de paramètre prédéfini pour identifier une ressource, l’utilisateur peut facilement comprendre la signification du paramètre, quelle que soit l’applet de commande qu’il utilise. Fondamentalement, les noms de paramètres suivent les mêmes règles que celles utilisées pour les noms de variables dans le common language runtime (CLR). Pour plus d’informations sur la dénomination des paramètres, consultez [noms des paramètres](/previous-versions/ms714468(v=vs.85))de l’applet de commande.

- Windows PowerShell réserve quelques noms de paramètres pour fournir une expérience utilisateur cohérente. N’utilisez pas ces noms de paramètres : `WhatIf` , `Confirm` , `Verbose` , `Debug` , `Warn` , `ErrorAction` , `ErrorVariable` , `OutVariable` et `OutBuffer` . En outre, les alias suivants pour ces noms de paramètres sont réservés : `vb` , `db` ,,, `ea` `ev` `ov` et `ob` .

- `Name` est un nom de paramètre simple et commun, recommandé pour une utilisation dans vos applets de commande. Il est préférable de choisir un nom de paramètre comme celui-ci plutôt qu’un nom complexe propre à une applet de commande spécifique et difficile à retenir.

- Les paramètres ne sont pas sensibles à la casse dans Windows PowerShell, bien que l’interpréteur de commandes conserve par défaut la casse. Le respect de la casse des arguments dépend du fonctionnement de l’applet de commande. Les arguments sont passés à un paramètre comme spécifié sur la ligne de commande.

- Pour obtenir des exemples d’autres déclarations de paramètres, consultez [paramètres d’applet](./cmdlet-parameters.md)de commande.

## <a name="declaring-parameters-as-positional-or-named"></a>Déclarer des paramètres en tant que positionnels ou nommés

Une applet de commande doit définir chaque paramètre en tant que paramètre positionnel ou nommé. Les deux types de paramètres acceptent des arguments uniques, plusieurs arguments séparés par des virgules et des paramètres booléens. Un paramètre booléen, également appelé *commutateur*, gère uniquement les paramètres booléens. Le commutateur est utilisé pour déterminer la présence du paramètre. La valeur par défaut recommandée est `false` .

L’exemple `Get-Proc` d’applet de commande définit le `Name` paramètre en tant que paramètre positionnel avec la position
0. Cela signifie que le premier argument entré par l’utilisateur sur la ligne de commande est automatiquement inséré pour ce paramètre. Si vous souhaitez définir un paramètre nommé, pour lequel l’utilisateur doit spécifier le nom de paramètre à partir de la ligne de commande, laissez le `Position` mot clé en dehors de la déclaration d’attribut.

> [!NOTE]
> À moins que les paramètres ne soient nommés, nous vous recommandons de définir la position des paramètres les plus utilisés de manière à ce que les utilisateurs n’aient pas à taper le nom du paramètre.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Déclarer des paramètres comme obligatoires ou facultatifs

Une applet de commande doit définir chaque paramètre en tant que paramètre facultatif ou obligatoire. Dans l’exemple d’applet de commande `Get-Proc` , le `Name` paramètre est défini sur facultatif, car le `Mandatory` mot clé n’est pas défini dans la déclaration d’attribut.

## <a name="supporting-parameter-validation"></a>Prise en charge de la validation des paramètres

L’exemple d’applet de commande `Get-Proc` ajoute un attribut de validation d’entrée, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), au `Name` paramètre pour permettre la validation que l’entrée n’est ni `null` ni vide. Cet attribut est l’un des nombreux attributs de validation fournis par Windows PowerShell. Pour obtenir des exemples d’autres attributs de validation, consultez [validation des entrées de paramètres](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

Si votre applet de commande doit gérer l’entrée de ligne de commande, elle doit remplacer les méthodes de traitement d’entrée appropriées. Les méthodes de traitement d’entrée de base sont introduites lors de la [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.

L' `Get-Proc` applet de commande remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour gérer l' `Name` entrée de paramètre fournie par l’utilisateur ou un script. Cette méthode obtient les processus pour chaque nom de processus demandé, ou tous les processus si aucun nom n’est fourni. Notez que dans [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [System. Management. Automation. applet de commande. WriteObject% 28System. Object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) est le mécanisme de sortie permettant d’envoyer des objets de sortie au pipeline. Le deuxième paramètre de cet appel, `enumerateCollection` , est défini sur `true` pour indiquer à l’exécution de Windows PowerShell d’énumérer le tableau de sortie des objets de processus et d’écrire un processus à la fois sur la ligne de commande.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Exemple de code

Pour obtenir l’exemple de code C# complet, consultez [exemple GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET Framework. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou une applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après avoir implémenté une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande est inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande. Voici deux façons de tester le code de l’applet de commande Sample. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- À l’invite de commandes Windows PowerShell, utilisez la commande suivante pour répertorier le processus Internet Explorer, qui est nommé « IEXPLORE ».

  ```powershell
  get-proc -name iexplore
  ```

  La sortie suivante apparaît.

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- Pour répertorier les processus Internet Explorer, Outlook et bloc-notes nommés « IEXPLORE », « OUTLOOK » et « NOTEPAD », utilisez la commande suivante. S’il existe plusieurs processus, ils sont tous affichés.

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  La sortie suivante apparaît.

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a>Voir aussi

[Ajout de paramètres qui traitent l’entrée du pipeline](./adding-parameters-that-process-pipeline-input.md)

[Création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)

[Extension des types d’objets et de la mise en forme](/previous-versions/ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))

[Référence Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applets de commande](./cmdlet-samples.md)
