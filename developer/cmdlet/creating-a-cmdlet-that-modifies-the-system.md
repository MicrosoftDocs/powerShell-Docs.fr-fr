---
title: Création d’une applet de commande qui modifie le système | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301403"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Création d’une applet de commande qui modifie le système

Parfois, une applet de commande doit modifier l’état en cours d’exécution du système, pas seulement l’état de l’exécution de Windows PowerShell. Dans ce cas, l’applet de commande doit autoriser l’utilisateur une possibilité de vérifier s’il faut apporter la modification.

Pour prendre en charge de confirmation une applet de commande doit faire deux choses.

- Déclarer que l’applet de commande prend en charge la confirmation lorsque vous spécifiez le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut en définissant le mot-clé SupportsShouldProcess sur `true`.

- Appelez [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pendant l’exécution de l’applet de commande (comme indiqué dans l’exemple suivant).

En prenant en charge la confirmation, une applet de commande expose le `Confirm` et `WhatIf` paramètres qui sont fournies par Windows PowerShell et également répond aux exigences de développement pour les applets de commande (pour plus d’informations sur les directives de développement d’applet de commande, consultez [ Directives de développement d’applet de commande](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Modification du système

Le fait de « modification du système » fait référence à une applet de commande qui potentiellement modifie l’état du système en dehors de Windows PowerShell. Par exemple, l’arrêt d’un processus, l’activation ou la désactivation d’un compte d’utilisateur ou ajouter une ligne à une table de base de données sont toutes les modifications apportées au système qui doit être confirmé. En revanche, les opérations de lire les données ou établissent des connexions temporaires ne modifiez pas le système et ne nécessitent généralement pas de confirmation. Confirmation n’est pas également nécessaire pour les actions dont l’effet est limitée au sein du runtime Windows PowerShell, comme `set-variable`. Applets de commande qui peut ou peut ne pas faire une modification permanente doit déclarer `SupportsShouldProcess` et appelez [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uniquement s’ils sont sur le point d’apporter une modification permanente.

> [!NOTE]
> Confirmation de ShouldProcess s’applique uniquement aux applets de commande. Si une commande ou un script modifie l’état en cours d’exécution d’un système en appelant directement des propriétés ou méthodes .NET, ou en appelant des applications en dehors de Windows PowerShell, il se peut que cette forme de confirmation ne sera pas disponible.

## <a name="the-stopproc-cmdlet"></a>L’applet de commande StopProc

Cette rubrique décrit une applet de commande Stop-Process qui tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande. Étant donné que vous écrivez une applet de commande pour modifier le système, il doit être nommé en conséquence. Cette applet de commande s’arrête système traite, par conséquent, le nom du verbe choisi ici est « Stop », défini par le [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), avec le nom « Proc » pour indiquer que l’applet de commande arrête le processus. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

Voici la définition de classe pour cette applet de commande Stop-Process.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

N’oubliez pas que, dans le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) déclaration, le `SupportsShouldProcess` mot clé d’attribut est défini sur `true` pour activer l’applet de commande effectuer des appels à [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Sans ce jeu de mot clé, le `Confirm` et `WhatIf` paramètres ne seront pas disponibles à l’utilisateur.

### <a name="extremely-destructive-actions"></a>Actions extrêmement destructeur

Certaines opérations sont extrêmement destructeur, telles que le reformatage d’une partition de disque dur actif. Dans ces cas, l’applet de commande doit définir `ConfirmImpact`  =  `ConfirmImpact.High` lorsque vous déclarez le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut. Ce paramètre force l’applet de commande pour demander la confirmation utilisateur même lorsque l’utilisateur n’a pas spécifié le `Confirm` paramètre. Toutefois, les développeurs d’applet de commande doivent éviter un abus de `ConfirmImpact` pour les opérations qui sont simplement potentiellement destructrices, telles que la suppression d’un compte d’utilisateur. Rappelez-vous que si `ConfirmImpact` a la valeur [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **haute**.

De même, certaines opérations sont peu de chances d’être destructive, bien qu’elles modifient en théorie l’état en cours d’exécution d’un système en dehors de Windows PowerShell. Ces applets de commande peut définir `ConfirmImpact` à [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Cela permettra d’ignorer les demandes de confirmation où l’utilisateur a demandé de confirmer les opérations uniquement moyenne impact et à fort impact.

## <a name="defining-parameters-for-system-modification"></a>Définition des paramètres pour la Modification du système

Cette section décrit comment définir les paramètres de l’applet de commande, y compris ceux qui sont nécessaires pour la modification d’un système de prise en charge. Consultez [ajoutant des paramètres de cette entrée de ligne de commande de processus](./adding-parameters-that-process-command-line-input.md) si vous avez besoin des informations générales sur la définition des paramètres.

L’applet de commande Stop-Process définit trois paramètres : `Name`, `Force`, et `PassThru`.

Le `Name` paramètre correspond à la `Name` propriété de l’objet d’entrée du processus. N’oubliez pas que le `Name` paramètre dans cet exemple est obligatoire, comme l’applet de commande échouera si elle n’a pas d’un processus nommé à arrêter.

Le `Force` paramètre permet à l’utilisateur à remplacer les appels à [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). En fait, une applet de commande qui appelle [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doit avoir un `Force` paramètre afin que lorsque `Force` est spécifié, l’applet de commande ignore l’appel à [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et poursuit l’opération. N’oubliez pas que cela n’affecte pas les appels à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Le `PassThru` paramètre permet à l’utilisateur indiquer si l’applet de commande passe un objet de sortie via le pipeline, dans ce cas, une fois un processus est arrêté. N’oubliez pas que ce paramètre est lié à l’applet de commande lui-même plutôt qu’à une propriété de l’objet d’entrée.

Voici la déclaration de paramètre pour l’applet de commande Stop-Process.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

L’applet de commande doit substituer une méthode de traitement des entrées. Le code suivant illustre la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilisé dans l’applet de commande Stop-Process exemple de remplacement. Pour chaque demandé de nom de processus, cette méthode garantit que le processus n’est pas un processus spécial, qu’il tente d’arrêter le processus et qu’il envoie ensuite un objet de sortie si la `PassThru` est précisé.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>Appel de la méthode ShouldProcess

L’entrée de traitement de la méthode de votre applet de commande doit appeler le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour confirmer l’exécution d’une opération avant une modification (par exemple, une suppression de fichiers) est apportée à l’état en cours d’exécution (méthode) du système. Cela permet l’exécution de Windows PowerShell pour fournir le comportement correct de « WhatIf » et « Confirmer » au sein de l’interpréteur de commandes.

> [!NOTE]
> Si une applet de commande indique qu’il prend en charge doit traiter et ne parvient pas à rendre le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appeler, l’utilisateur peut modifier le système de manière inattendue.

L’appel à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell en prenant en compte les paramètres de ligne de commande ou les variables de préférence pour déterminer ce qui doit être affiché à l’utilisateur.

L’exemple suivant illustre l’appel à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) à partir de la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode dans l’exemple L’applet de commande Stop-Process.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Appel de la méthode ShouldContinue

L’appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode envoie un message secondaire à l’utilisateur. Cet appel est effectué après l’appel à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourne `true` et si le `Force` paramètre n’a pas été défini `true`. L’utilisateur peut ensuite fournir des commentaires pour indiquer si l’opération doit être poursuivie. Vos appels de l’applet de commande [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) une vérification supplémentaire pour les modifications du système potentiellement dangereux ou lorsque vous souhaitez fournir des options Oui à tous et non à tous à l’utilisateur.

L’exemple suivant illustre l’appel à [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) à partir de la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode dans l’exemple L’applet de commande Stop-Process.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Arrêt de traitement d’entrée

L’entrée de méthode d’une applet de commande qui effectue des modifications de système de traitement doit fournir un moyen de l’arrêt du traitement d’entrée. Dans le cas de cette applet de commande Stop-Process, un appel est effectué à partir de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode à la [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) (méthode). Étant donné que le `PassThru` paramètre est défini sur `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) appelle également [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) à envoyer l’objet processus au pipeline.

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [StopProcessSample01 exemple](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net. Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande. Voici plusieurs tests qui testent l’applet de commande Stop-Process. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Démarrez Windows PowerShell et utilisez l’applet de commande Stop-Process pour arrêter le traitement comme indiqué ci-dessous. Étant donné que l’applet de commande spécifie le `Name` paramètre comme étant obligatoire, les requêtes de l’applet de commande pour le paramètre.

    ```powershell
    PS> stop-proc
    ```

La sortie suivante s’affiche.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Maintenant nous allons utiliser l’applet de commande pour arrêter le processus nommé « NOTEPAD ». L’applet de commande vous invite à confirmer l’action.

    ```powershell
    PS> stop-proc -Name notepad
    ```

La sortie suivante s’affiche.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Comme indiqué, utilisez Stop-Process pour arrêter le processus critique nommé « WINLOGON ». Vous êtes invité et un avertissement d’exécution de cette action, car elle entraîne le redémarrage du système d’exploitation.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

La sortie suivante s’affiche.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Nous allons maintenant essayez d’arrêter le processus WINLOGON sans recevoir d’avertissement. N’oubliez pas que cette entrée de la commande utilise le `Force` paramètre pour remplacer l’avertissement.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

La sortie suivante s’affiche.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Voir aussi

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Extension des Types d’objets et mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Exemples d’applet de commande](./cmdlet-samples.md)