---
title: Ajout de paramètres qui traitent l’entrée de ligne de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068808"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Ajout de paramètres qui traitent l’entrée de la ligne de commande

Une source d’entrée pour une applet de commande est la ligne de commande. Cette rubrique décrit comment ajouter un paramètre à la **Get-Process** applet de commande (qui est décrite dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)) afin que l’applet de commande peut traiter l’entrée à partir de l’ordinateur local selon explicite objets passés à l’applet de commande. Le **Get-Process** applet de commande décrite ici récupère des processus basés sur leurs noms, puis affiche des informations sur les processus à l’invite de commande.

Les sections suivantes sont dans cette rubrique :

- [Définition de la classe de l’applet de commande](#Defining-the-Cmdlet-Class)

- [Déclaration de paramètres](#Declaring-Parameters)

- [Prise en charge de la Validation de paramètre](#Supporting-Parameter-Validation)

- [Substitution d’une méthode de traitement des entrées](#Overriding-an-Input-Processing-Method)

- [Exemple de code](#Code-Sample)

- [Définition des Types d’objets et mise en forme](#Defining-Object-Types-and-Formatting)

- [Création de l’applet de commande](#Building-the-Cmdlet)

- [Test de l’applet de commande](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Définition de la classe de l’applet de commande

La première étape de création de l’applet de commande est l’applet de commande d’affectation de noms et la déclaration de la classe .NET Framework qui implémente l’applet de commande. Cette applet de commande récupère les informations de processus, par conséquent, le nom du verbe choisi ici est « Get ». (Presque toute sorte de l’applet de commande qui est capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

Voici la déclaration de classe pour le **Get-Process** applet de commande. Plus d’informations sur cette définition sont fournies dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Déclaration de paramètres

Un paramètre d’applet de commande permet à l’utilisateur à fournir l’entrée à l’applet de commande. Dans l’exemple suivant, **Get-Process** et `Get-Member` sont les noms des applets de commande canalisée en rafale et `MemberType` est un paramètre pour le `Get-Member` applet de commande. Le paramètre a l’argument « property ».

**PS > get-Process ; `get-member` membertype - propriété**

Pour déclarer des paramètres pour une applet de commande, vous devez d’abord définir les propriétés qui représentent les paramètres. Dans le **Get-Process** applet de commande, le seul paramètre est `Name`, qui dans ce cas représente le nom de l’objet de processus de .NET Framework à récupérer. Par conséquent, la classe de l’applet de commande définit une propriété de type chaîne pour accepter un tableau de noms.

Voici la déclaration de paramètre pour le `Name` paramètre de la **Get-Process** applet de commande.

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

Pour informer le runtime de Windows PowerShell que cette propriété est la `Name` paramètre, un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut est ajouté à la définition de propriété. La syntaxe de base pour déclarer cet attribut est `[Parameter()]`.

> [!NOTE]
> Un paramètre doit être explicitement marqué comme public. Paramètres qui ne sont pas marqués comme public par défaut interne et ne sont pas localisés par le runtime de Windows PowerShell.

Cette applet de commande utilise un tableau de chaînes pour la `Name` paramètre. Si possible, votre applet de commande doit également définir un paramètre sous forme de tableau, car cela permet à l’applet de commande accepter plusieurs éléments.

#### <a name="things-to-remember-about-parameter-definitions"></a>Points à retenir sur les définitions de paramètres

- Prédéfinies Windows PowerShell paramètre noms et types de données doivent être réutilisés autant que possible pour vous assurer que votre applet de commande est compatible avec les applets de commande Windows PowerShell. Par exemple, si toutes les applets de commande utilisent prédéfinis `Id` nom de paramètre pour identifier une ressource, l’utilisateur sera facilement comprendre la signification du paramètre, quel que soit l’applet de commande qu’ils utilisent. En fait, les noms de paramètres suivent les mêmes règles que celles utilisées pour les noms de variables dans le common language runtime (CLR). Pour plus d’informations sur le paramètre d’affectation de noms, consultez [noms de paramètre d’applet de commande](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell réserve quelques noms de paramètre pour fournir une expérience utilisateur cohérente. N’utilisez pas ces noms de paramètre : `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, et `OutBuffer`. En outre, les alias suivants de ces noms de paramètres sont réservés : `vb`, `db`, `ea`, `ev`, `ov`, et `ob`.

- `Name` est un nom de paramètre simple et courant recommandé pour une utilisation dans vos applets de commande. Il est préférable de choisir un nom de paramètre, ainsi qu’un nom complex qui est unique pour une applet de commande spécifique et difficiles à mémoriser.

- Les paramètres respectent la casse dans Windows PowerShell, bien que par défaut l’interpréteur de commandes préserve la casse. Respect de la casse des arguments dépend de l’opération de l’applet de commande. Arguments sont passés à un paramètre comme spécifié dans la ligne de commande.

- Pour obtenir des exemples d’autres déclarations de paramètre, consultez [paramètres de l’applet de commande](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Déclarer des paramètres positionnels ou nommés

Une applet de commande doit définir chaque paramètre soit un paramètre positionnel ou nommé. Les deux types de paramètres acceptent des arguments uniques, plusieurs arguments séparés par des virgules et les paramètres de type Boolean. Un paramètre booléen, également appelé un *commutateur*, gère uniquement les paramètres de type Boolean. Le commutateur est utilisé pour déterminer la présence du paramètre. La valeur par défaut recommandée est `false`.

L’exemple **Get-Process** applet de commande définit le `Name` paramètre comme un paramètre de positionnement à la position 0. Cela signifie que le premier argument de l’utilisateur entre dans la ligne de commande est automatiquement inséré pour ce paramètre. Si vous souhaitez définir un paramètre nommé, pour lequel l’utilisateur doit spécifier le nom du paramètre à partir de la ligne de commande, laissez le `Position` mot clé hors de la déclaration d’attribut.

> [!NOTE]
> Sauf si les paramètres doivent être nommés, nous vous recommandons d’apporter les paramètres plus utilisées positionnels afin que les utilisateurs devront pas taper le nom du paramètre.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Déclarer des paramètres comme étant obligatoires ou facultatifs

Une applet de commande doit définir chaque paramètre optionnel ou un paramètre obligatoire. Dans l’exemple **Get-Process** applet de commande, le `Name` paramètre est défini comme étant facultatifs, car le `Mandatory` mot clé n’est pas défini dans la déclaration d’attribut.

## <a name="supporting-parameter-validation"></a>Prise en charge de la Validation de paramètre

L’exemple **Get-Process** applet de commande ajoute un attribut de validation d’entrée, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), à le `Name` paramètre pour activer la validation que le entrée n’est ni `null` ni vide. Cet attribut est un des attributs de validation de fournies par Windows PowerShell. Pour obtenir des exemples d’autres attributs de validation, consultez [validation des entrées de paramètre de](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

Si votre applet de commande consiste à gérer l’entrée de ligne de commande, il doit remplacer la méthodes de traitement d’entrée appropriée. Les méthodes de traitement d’entrée de base sont introduites dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).

Le **Get-Process** applet de commande remplace le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour gérer la `Name` entrée de paramètre fournie par l’utilisateur ou un script. Cette méthode obtient les processus pour chaque nom de processus demandé, ou tous les processus si aucun nom n’est fourni. Notez que dans [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) correspond à la sortie mécanisme pour envoyer la sortie des objets au pipeline. Le deuxième paramètre de cet appel, `enumerateCollection`, est définie sur `true` pour informer le runtime de Windows PowerShell pour énumérer le tableau de sortie d’objets de processus et d’écrire un seul processus à la fois à la ligne de commande.

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

Pour l’ensemble C# exemple de code, consultez [exemple GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide des objets .NET Framework. Par conséquent, une applet de commande devrez peut-être définir son propre type, ou peut-être une applet de commande étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Une fois que vous implémentez une applet de commande, vous devez l’inscrire avec Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande est enregistré avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande. Voici deux façons de tester le code pour l’applet de commande d’exemple. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- À l’invite Windows PowerShell, utilisez la commande suivante pour répertorier le processus Internet Explorer, qui est nommé « IEXPLORE. »

    ```powershell
    PS> get-proc -name iexplore
    ```

La sortie suivante s’affiche.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Pour répertorier les processus Internet Explorer, Outlook et le bloc-notes, nommés « IEXPLORE », « OUTLOOK » et « NOTEPAD », utilisent la commande suivante. S’il existe plusieurs processus, tous d'entre eux sont affichés.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

La sortie suivante s’affiche.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Voir aussi

[Ajout de paramètres d’entrée de Pipeline de processus](./adding-parameters-that-process-pipeline-input.md)

[Création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Informations de référence sur Windows PowerShell](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)
