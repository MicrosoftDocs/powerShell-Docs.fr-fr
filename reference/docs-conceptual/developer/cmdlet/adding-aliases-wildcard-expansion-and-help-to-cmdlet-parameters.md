---
title: Ajout d’alias, extension de caractère générique et aide aux paramètres d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415661"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande

Cette section décrit comment ajouter des alias, une extension de caractères génériques et des messages d’aide aux paramètres de l’applet de commande Stop-proc (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)).

Cette applet de commande Stop-proc tente d’arrêter les processus qui sont récupérés à l’aide de l’applet de commande « obtient-proc » (décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande).

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande. Étant donné que vous écrivez une applet de commande pour modifier le système, elle doit être nommée en conséquence. Étant donné que cette applet de commande arrête les processus système, elle utilise le verbe « Stop », défini par la classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , avec le nom « proc » pour indiquer le processus. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

Le code suivant est la définition de classe pour cette applet de commande Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Définition des paramètres pour la modification du système

Votre applet de commande doit définir des paramètres qui prennent en charge les modifications du système et les commentaires des utilisateurs. L’applet de commande doit définir un paramètre `Name` ou un équivalent pour que l’applet de commande puisse modifier le système par une sorte d’identificateur. En outre, l’applet de commande doit définir les paramètres `Force` et `PassThru`. Pour plus d’informations sur ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Définition d’un alias de paramètre

Un alias de paramètre peut être un nom de remplacement ou un nom abrégé à une ou deux lettres bien défini pour un paramètre d’applet de commande. Dans les deux cas, l’objectif de l’utilisation d’alias est de simplifier l’entrée d’utilisateur à partir de la ligne de commande. Windows PowerShell prend en charge les alias de paramètres via l’attribut [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , qui utilise la syntaxe de déclaration [alias ()].

Le code suivant montre comment un alias est ajouté au paramètre `Name`.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Outre l’utilisation de l’attribut [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , le runtime Windows PowerShell effectue une correspondance de nom partielle, même si aucun alias n’est spécifié. Par exemple, si votre applet de commande a un paramètre `FileName` et qu’il s’agit du seul paramètre qui commence par `F`, l’utilisateur peut entrer `Filename`, `Filenam`, `File`, `Fi`ou `F` et toujours reconnaître l’entrée comme paramètre `FileName`.

## <a name="creating-help-for-parameters"></a>Création d’aide pour les paramètres

Windows PowerShell vous permet de créer de l’aide pour les paramètres de l’applet de commande. Procédez ainsi pour tous les paramètres utilisés pour la modification du système et les commentaires des utilisateurs. Pour chaque paramètre permettant de prendre en charge l’aide, vous pouvez définir le mot clé `HelpMessage` attribut dans la déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Ce mot clé définit le texte à afficher à l’utilisateur pour obtenir de l’aide sur l’utilisation du paramètre. Vous pouvez également définir le mot clé `HelpMessageBaseName` pour identifier le nom de base d’une ressource à utiliser pour le message. Si vous définissez ce mot clé, vous devez également définir le mot clé `HelpMessageResourceId` pour spécifier l’identificateur de ressource.

Le code suivant de cette applet de commande Stop-proc définit le mot clé d’attribut `HelpMessage` pour le paramètre `Name`.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

Votre applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de commande. ProcessRecord. Lors de la modification du système, l’applet de commande doit appeler les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) pour permettre à l’utilisateur de fournir des commentaires avant qu’une modification soit apportée. Pour plus d’informations sur ces méthodes, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Extension de caractères génériques prise en charge

Pour permettre la sélection de plusieurs objets, votre applet de commande peut utiliser les classes [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) et [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) pour fournir une prise en charge des caractères génériques pour l’entrée de paramètre. Les exemples de modèles de caractère générique sont LSA *, \*. txt et [a-c]\*. Utilisez le caractère de guillemet (') comme caractère d’échappement lorsque le modèle contient un caractère qui doit être utilisé littéralement.

Les extensions de caractères génériques des noms de fichier et de chemin d’accès sont des exemples de scénarios courants dans lesquels l’applet de commande peut souhaiter prendre en charge les entrées de chemin d’accès lorsque la sélection de plusieurs objets est requise. Un cas courant se trouve dans le système de fichiers, où un utilisateur souhaite voir tous les fichiers résidant dans le dossier actif.

Vous devez avoir besoin d’une implémentation de correspondance de modèle de caractère générique personnalisée uniquement rarement. Dans ce cas, votre applet de commande doit prendre en charge l’intégralité de la spécification POSIX 1003,2, 3,13 pour l’extension de caractères génériques ou le sous-ensemble simplifié suivant :

- **Point d’interrogation ( ?).** Correspond à n’importe quel caractère à l’emplacement spécifié.

- **Astérisque (\*).** Correspond à zéro ou plusieurs caractères en commençant à l’emplacement spécifié.

- **Crochet ouvrant ([).** Introduit une expression de crochet de motif qui peut contenir des caractères ou une plage de caractères. Si une plage est requise, un trait d’Union (-) est utilisé pour indiquer la plage.

- **Crochet fermant (]).** Termine une expression entre crochets.

- **Caractère d’échappement du guillemet (').** Indique que le caractère suivant doit être pris littéralement. Sachez que lorsque vous spécifiez le caractère de guillemets avant à partir de la ligne de commande (au lieu de le spécifier par programmation), le caractère d’échappement du guillemet de retour doit être spécifié deux fois.

> [!NOTE]
> Pour plus d’informations sur les modèles de caractères génériques, consultez [prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md)commande.

Le code suivant montre comment définir des options de caractères génériques et définir le modèle de caractère générique utilisé pour résoudre le paramètre `Name` de cette applet de commande.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Le code suivant montre comment tester si le nom du processus correspond au modèle de caractère générique défini. Notez que, dans ce cas, si le nom du processus ne correspond pas au modèle, l’applet de commande continue à recevoir le nom de processus suivant.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Exemple de code

Pour obtenir l' C# exemple de code complet, consultez [exemple StopProcessSample03](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Définir les types d’objets et la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande. Nous allons tester l’exemple d’applet de commande Stop-proc. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Démarrez Windows PowerShell et utilisez Stop-proc pour arrêter un processus à l’aide de l’alias ProcessName pour le paramètre `Name`.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

La sortie suivante s'affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Effectuez l’entrée suivante sur la ligne de commande. Étant donné que le paramètre Name est obligatoire, vous êtes invité à le faire. Entrée de «  !? » affiche le texte d’aide associé au paramètre.

    ```powershell
    PS> stop-proc
    ```

La sortie suivante s'affiche.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- À présent, effectuez l’entrée suivante pour arrêter tous les processus qui correspondent au modèle de caractère générique « * note\*». Vous êtes invité à arrêter chaque processus correspondant au modèle.

    ```powershell
    PS> stop-proc -Name *note*
    ```

La sortie suivante s'affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

La sortie suivante s'affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

La sortie suivante s'affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Voir aussi

[Créer une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)

[Comment créer une applet de commande Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))

[Prise en charge des caractères génériques dans les paramètres d’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
