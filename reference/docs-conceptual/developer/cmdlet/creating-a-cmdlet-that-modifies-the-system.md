---
title: Création d’une applet de commande qui modifie le système | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.openlocfilehash: 03ffe0c9c02dcdeb2dd24f81014b2013ae169aa4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782172"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Création d’une applet de commande qui modifie le système

Parfois, une applet de commande doit modifier l’état d’exécution du système, et pas seulement l’état du runtime Windows PowerShell. Dans ce cas, l’applet de commande doit permettre à l’utilisateur de confirmer si la modification doit être apportée ou non.

Pour prendre en charge la confirmation, une applet de commande doit faire deux choses.

- Déclarez que l’applet de commande prend en charge la confirmation quand vous spécifiez l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) en définissant le mot clé SupportsShouldProcess sur `true` .

- Appelez [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pendant l’exécution de l’applet de commande (comme indiqué dans l’exemple suivant).

En prenant en charge la confirmation, une applet de commande expose les `Confirm` `WhatIf` paramètres et fournis par Windows PowerShell, ainsi que les instructions de développement des applets de commande (pour plus d’informations sur les instructions de développement des applets de commande, consultez [instructions de développement d’applets](./cmdlet-development-guidelines.md)de commande).

## <a name="changing-the-system"></a>Modification du système

L’acte de « modification du système » fait référence à toute applet de commande qui modifie potentiellement l’état du système en dehors de Windows PowerShell. Par exemple, l’arrêt d’un processus, l’activation ou la désactivation d’un compte d’utilisateur, ou l’ajout d’une ligne à une table de base de données sont toutes des modifications apportées au système qui doivent être confirmées. En revanche, les opérations qui lisent les données ou établissent des connexions temporaires ne modifient pas le système et ne nécessitent généralement pas de confirmation. La confirmation n’est pas non plus nécessaire pour les actions dont l’effet est limité à dans le runtime Windows PowerShell, tel que `set-variable` . Les applets de commande qui peuvent ou ne peuvent pas effectuer de modification permanente doivent déclarer `SupportsShouldProcess` et appeler [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uniquement si elles sont sur le lieu d’effectuer une modification permanente.

> [!NOTE]
> La confirmation ShouldProcess s’applique uniquement aux applets de commande. Si une commande ou un script modifie l’état d’exécution d’un système en appelant directement des méthodes ou des propriétés .NET, ou en appelant des applications en dehors de Windows PowerShell, cette forme de confirmation n’est pas disponible.

## <a name="the-stopproc-cmdlet"></a>Applet de commande StopProc

Cette rubrique décrit une applet de commande Stop-proc qui tente d’arrêter les processus qui sont récupérés à l’aide de l’applet de commande « obtenir-proc » (décrite dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande).

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande. Étant donné que vous écrivez une applet de commande pour modifier le système, elle doit être nommée en conséquence. Cette applet de commande arrête les processus système. par conséquent, le nom du verbe choisi ici est « Stop », défini par la classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , avec le nom « proc » pour indiquer que l’applet de commande arrête les processus. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

Voici la définition de classe pour cette applet de commande Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Sachez que dans la Déclaration [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , le `SupportsShouldProcess` mot clé d’attribut a la valeur `true` pour permettre à l’applet de commande d’effectuer des appels à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Si ce mot clé n’est pas défini, les `Confirm` `WhatIf` paramètres et ne sont pas disponibles pour l’utilisateur.

### <a name="extremely-destructive-actions"></a>Actions extrêmement destructrices

Certaines opérations sont extrêmement destructrices, telles que le reformatage d’une partition de disque dur active. Dans ce cas, l’applet de commande doit être définie `ConfirmImpact`  =  `ConfirmImpact.High` lors de la déclaration de l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Ce paramètre force l’applet de commande à demander la confirmation de l’utilisateur même si l’utilisateur n’a pas spécifié le `Confirm` paramètre. Toutefois, les développeurs d’applets de commande doivent éviter de les utiliser `ConfirmImpact` pour les opérations qui sont simplement potentiellement destructrices, telles que la suppression d’un compte d’utilisateur. N’oubliez pas que si `ConfirmImpact` a la valeur [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.

De même, certaines opérations ont peu de chances d’être destructrices, bien qu’elles modifient en théorie l’état d’exécution d’un système en dehors de Windows PowerShell. Ces applets de commande peuvent `ConfirmImpact` être définies sur [System. Management. Automation. ConfirmImpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Cela permet de contourner les demandes de confirmation lorsque l’utilisateur a demandé à confirmer uniquement les opérations à impact moyen et à impact élevé.

## <a name="defining-parameters-for-system-modification"></a>Définition des paramètres pour la modification du système

Cette section décrit comment définir les paramètres de l’applet de commande, y compris ceux qui sont nécessaires pour prendre en charge la modification du système. Consultez [Ajout de paramètres qui traitent l’entrée de la ligne de](./adding-parameters-that-process-command-line-input.md) commande si vous avez besoin d’informations générales sur la définition des paramètres.

L’applet de commande Stop-proc définit trois paramètres : `Name` , `Force` et `PassThru` .

Le `Name` paramètre correspond à la `Name` propriété de l’objet de traitement d’entrée. Sachez que le `Name` paramètre de cet exemple est obligatoire, car l’applet de commande échouera s’il n’a pas de processus nommé à arrêter.

Le `Force` paramètre permet à l’utilisateur de substituer des appels à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)de commande. ShouldContinue. En fait, toute applet de commande qui appelle [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doit avoir un `Force` paramètre de sorte que lorsque `Force` est spécifié, l’applet de commande ignore l’appel à [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et poursuit l’opération. N’oubliez pas que cela n’affecte pas les appels à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)de commande. ShouldProcess.

Le `PassThru` paramètre permet à l’utilisateur d’indiquer si l’applet de commande passe un objet de sortie via le pipeline, dans ce cas, après l’arrêt d’un processus. N’oubliez pas que ce paramètre est lié à l’applet de commande elle-même et non à une propriété de l’objet d’entrée.

Voici la déclaration du paramètre pour l’applet de commande Stop-proc.

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

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

L’applet de commande doit remplacer une méthode de traitement d’entrée. Le code suivant illustre la substitution [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilisée dans l’exemple d’applet de commande Stop-proc. Pour chaque nom de processus demandé, cette méthode garantit que le processus n’est pas un processus spécial, tente d’arrêter le processus, puis envoie un objet de sortie si le `PassThru` paramètre est spécifié.

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

La méthode de traitement d’entrée de votre applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour confirmer l’exécution d’une opération avant qu’une modification (par exemple, la suppression de fichiers) soit apportée à l’état d’exécution du système. Cela permet au runtime Windows PowerShell de fournir les comportements « WhatIf » et « Confirm » corrects dans l’interpréteur de commandes.

> [!NOTE]
> Si une applet de commande indique qu’elle prend en charge doit traiter et ne parvient pas à effectuer l’appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l’utilisateur peut modifier le système de manière inattendue.

L’appel à [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte des paramètres de ligne de commande ou des variables de préférence pour déterminer ce qui doit être affiché à l’utilisateur.

L’exemple suivant montre l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) dans l’exemple d’applet de commande Stop-proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Appel de la méthode ShouldContinue

L’appel à la méthode [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) envoie un message secondaire à l’utilisateur. Cet appel est effectué après l’appel à [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourne `true` et si le `Force` paramètre n’a pas la valeur `true` . L’utilisateur peut ensuite fournir des commentaires pour indiquer si l’opération doit être poursuivie. Votre applet de commande appelle [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en guise de vérification supplémentaire des modifications système potentiellement dangereuses ou lorsque vous souhaitez fournir des options Oui-à-tout et non-tout à l’utilisateur.

L’exemple suivant illustre l’appel à [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) dans l’exemple d’applet de commande Stop-proc.

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

## <a name="stopping-input-processing"></a>Arrêt du traitement des entrées

La méthode de traitement d’entrée d’une applet de commande qui effectue des modifications du système doit permettre d’arrêter le traitement des entrées. Dans le cas de cette applet de commande Stop-proc, un appel est effectué à partir de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) vers la méthode [System. Diagnostics. Process. Kill *](/dotnet/api/System.Diagnostics.Process.Kill) . Étant donné que le `PassThru` paramètre a la valeur `true` , [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) appelle également [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) pour envoyer l’objet processus au pipeline.

## <a name="code-sample"></a>Exemple de code

Pour obtenir l’exemple de code C# complet, consultez [exemple StopProcessSample01](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande. Voici plusieurs tests qui testent l’applet de commande Stop-proc. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Démarrez Windows PowerShell et utilisez l’applet de commande Stop-proc pour arrêter le traitement, comme indiqué ci-dessous. Étant donné que l’applet de commande spécifie le `Name` paramètre comme obligatoire, l’applet de commande interroge le paramètre.

    ```powershell
    PS> stop-proc
    ```

    La sortie suivante apparaît.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Nous allons maintenant utiliser l’applet de commande pour arrêter le processus nommé « NOTEPAD ». L’applet de commande vous demande de confirmer l’action.

    ```powershell
    PS> stop-proc -Name notepad
    ```

    La sortie suivante apparaît.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Utilisez Stop-proc comme indiqué pour arrêter le processus critique nommé « WINLOGON ». Vous êtes invité à effectuer cette action, qui entraîne le redémarrage du système d’exploitation.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    La sortie suivante apparaît.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Essayons maintenant d’arrêter le processus WINLOGON sans recevoir d’avertissement. N’oubliez pas que cette entrée de commande utilise le `Force` paramètre pour remplacer l’avertissement.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    La sortie suivante apparaît.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Voir aussi

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Exemples d’applets de commande](./cmdlet-samples.md)
