---
title: Ajout d’alias, le développement des caractères génériques et aux paramètres de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859325"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande

Cette section décrit comment ajouter des alias, le développement des caractères génériques, et l’aide des messages vers les paramètres de l’applet de commande Stop-Process (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)).

Cette applet de commande Stop-Process tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).

Rubriques de cette section sont les suivantes :

- [Définition de l’applet de commande](#Defining-the-Cmdlet)

- [Définition des paramètres pour la Modification du système](#Defining-Parameters-for-System-Modification)

- [Définition d’un Alias de paramètre](#Defining-a-Parameter-Alias)

- [Création d’une aide pour les paramètres](#Creating-Help-for-Parameters)

- [Substitution d’une méthode de traitement des entrées](#Overriding-an-Input-Processing-Method)

- [Prise en charge du développement des caractères génériques](#Supporting-Wildcard-Expansion)

- [Exemple de code](#Defining-a-Parameter-Alias)

- [Définition des Types d’objets et mise en forme](#Define-Object-Types-and-Formatting)

- [Création de l’applet de commande](#Building-the-Cmdlet)

- [Test de l’applet de commande](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande. Étant donné que vous écrivez une applet de commande pour modifier le système, il doit être nommé en conséquence. Étant donné que cette applet de commande arrête les processus système, il utilise le verbe « Stop », défini par le [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), avec le nom « Proc » pour indiquer les processus. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

Le code suivant est la définition de classe pour cette applet de commande Stop-Process.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Définition des paramètres pour la Modification du système

Votre applet de commande doit définir les paramètres qui modifications du système de prise en charge et les commentaires des utilisateurs. L’applet de commande doit définir un `Name` paramètre ou équivalent afin que l’applet de commande sera en mesure de modifier le système par une sorte d’identificateur. En outre, l’applet de commande doit définir le `Force` et `PassThru` paramètres. Pour plus d’informations sur ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Définition d’un Alias de paramètre

Un alias de paramètre peut être un autre nom ou un nom de court 1-2-lettre ou bien défini pour un paramètre d’applet de commande. Dans les deux cas, l’objectif de l’utilisation d’alias est de simplifier l’entrée d’utilisateur à partir de la ligne de commande. Windows PowerShell prend en charge les alias de paramètre via la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, qui utilise la syntaxe de déclaration [Alias()].

Le code suivant montre comment un alias est ajouté à la `Name` paramètre.

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

Outre l’utilisation de la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, le runtime Windows PowerShell effectue la correspondance partielle de noms, même si aucun alias ne sont spécifiés. Par exemple, si votre applet de commande a un `FileName` paramètre et qui est le seul paramètre qui commence par `F`, l’utilisateur peut entrer `Filename`, `Filenam`, `File`, `Fi`, ou `F` et toujours reconnaître le entrée en tant que le `FileName` paramètre.

## <a name="creating-help-for-parameters"></a>Création d’une aide pour les paramètres

Windows PowerShell vous permet de créer une aide pour les paramètres de l’applet de commande. Procédez ainsi pour n’importe quel paramètre utilisé pour les commentaires de modification et l’utilisateur du système. Pour chaque paramètre prendre en charge d’aide, vous pouvez définir le `HelpMessage` attribut mot clé dans le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration de l’attribut. Ce mot clé définit le texte à afficher à l’utilisateur pour obtenir une assistance dans l’aide du paramètre. Vous pouvez également définir le `HelpMessageBaseName` mot clé pour identifier le nom de base d’une ressource à utiliser pour le message. Si vous définissez ce mot clé, vous devez également définir le `HelpMessageResourceId` mot clé pour spécifier l’identificateur de ressource.

Le code suivant à partir de cette applet de commande Stop-Process définit le `HelpMessage` attribut mot clé pour le `Name` paramètre.

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

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

Votre applet de commande doit substituer une méthode de traitement des entrées, ce sera souvent [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Lorsque vous modifiez le système, l’applet de commande doit appeler le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) des méthodes qui permettent la utilisateur pour fournir des commentaires avant une modification est apportée. Pour plus d’informations sur ces méthodes, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Prise en charge du développement des caractères génériques

Pour permettre la sélection de plusieurs objets, votre applet de commande peut utiliser le [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) et [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes pour fournir prise en charge de caractère générique d’extension pour le paramètre d’entrée. Exemples de modèles de caractère générique sont lsa * \*.txt et [a-c]\*. Utiliser le caractère de guillemet inversé (') comme caractère d’échappement lorsque le modèle contient un caractère qui doit être utilisé littéralement.

Expansions de caractère générique des noms de fichier et chemin d’accès sont des exemples de scénarios courants où l’applet de commande souhaitez peut-être autoriser la prise en charge pour les entrées de chemin d’accès lors de la sélection de plusieurs objets est nécessaire. Un cas courant est le système de fichiers, dans lequel un utilisateur souhaite voir tous les fichiers qui résident dans le dossier actif.

Vous aurez rarement une implémentation du modèle générique personnalisé correspondant. Dans ce cas, votre applet de commande doit prendre en charge la version complète de 1003.2 POSIX, 3,13 spécification pour le développement des caractères génériques ou le sous-ensemble simplifié suivant :

- **Point d’interrogation ( ?).** Correspond à n’importe quel caractère à l’emplacement spécifié.

- **Astérisque (\*).** Correspond à zéro ou plusieurs caractères en commençant à l’emplacement spécifié.

- **Crochet ouvrant ([]).** Introduit une expression entre crochets de modèle qui peut contenir des caractères ou une plage de caractères. Si une plage est requise, un trait d’union (-) est utilisé pour indiquer la plage.

- **Crochet fermant (]).** Met fin à une expression entre crochets de modèle.

- **Guillemet inversé le caractère d’échappement (').** Indique que le caractère suivant doit être pris littéralement. N’oubliez pas que lorsque vous spécifiez le caractère de guillemet inversé à partir de la ligne de commande (par opposition à spécifier par programmation), le caractère d’échappement de guillemet inversé doit être spécifié deux fois.

> [!NOTE]
> Pour plus d’informations sur les séquences de caractères génériques, consultez [prenant en charge les caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Le code suivant montre comment définir des options des caractères génériques et le modèle de caractère générique utilisé pour résoudre le `Name` paramètre pour cette applet de commande.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Le code suivant montre comment tester si le nom du processus correspond au modèle de caractère générique définie. Notez que, dans ce cas, si le nom du processus ne correspond pas au modèle, l’applet de commande se poursuit sur obtenir le nom du processus suivant.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [StopProcessSample03 exemple](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Définir les Types d’objets et la mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net. Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande. Testons l’applet de commande Stop-Process exemple. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Démarrez Windows PowerShell et utilisez Stop-Process pour arrêter un processus à l’aide de l’alias ProcessName pour le `Name` paramètre.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

La sortie suivante s’affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Ajoutez l’entrée suivante sur la ligne de commande. Étant donné que le paramètre de nom est obligatoire, vous êtes invité pour celui-ci. Saisie de « ! ? » Affiche le texte d’aide associé au paramètre.

    ```powershell
    PS> stop-proc
    ```

La sortie suivante s’affiche.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Assurez-vous maintenant l’entrée suivante pour arrêter tous les processus qui correspondent au modèle de caractère générique « * Remarque\*». Vous êtes invité avant d’arrêter chaque processus qui correspond au modèle.

    ```powershell
    PS> stop-proc -Name *note*
    ```

La sortie suivante s’affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

La sortie suivante s’affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

La sortie suivante s’affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Voir aussi

[Créer une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)

[Comment créer une applet de commande Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extension des Types d’objets et mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Prise en charge des caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
