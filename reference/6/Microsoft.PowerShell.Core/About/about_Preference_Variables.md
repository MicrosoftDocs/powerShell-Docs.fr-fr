---
description: Variables qui personnalisent le comportement de PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 6f23e016131901ed78b223a4d23dfa12416d970b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206973"
---
# <a name="about-preference-variables"></a>À propos des variables de préférence

## <a name="short-description"></a>Description courte

Variables qui personnalisent le comportement de PowerShell.

## <a name="long-description"></a>Description longue

PowerShell comprend un ensemble de variables qui vous permettent de personnaliser son comportement. Ces variables de préférence fonctionnent comme les options des systèmes basés sur l’interface graphique.

Les variables de préférence affectent l’environnement d’exploitation PowerShell et toutes les commandes exécutées dans l’environnement. Dans de nombreux cas, les applets de commande ont des paramètres que vous pouvez utiliser pour remplacer le comportement de préférence pour une commande spécifique.

Le tableau suivant répertorie les variables de préférence et leurs valeurs par défaut.

|             Variable             |       Valeur par défaut       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | Élevé                      |
| `$DebugPreference`               | SilentlyContinue          |
| `$ErrorActionPreference`         | Continue                  |
| `$ErrorView`                     | NormalView                |
| `$FormatEnumerationLimit`        | 4                         |
| `$InformationPreference`         | SilentlyContinue          |
| `$LogCommandHealthEvent`         | False (non enregistré)        |
| `$LogCommandLifecycleEvent`      | False (non enregistré)        |
| `$LogEngineHealthEvent`          | True (consigné)             |
| `$LogEngineLifecycleEvent`       | True (consigné)             |
| `$LogProviderLifecycleEvent`     | True (consigné)             |
| `$LogProviderHealthEvent`        | True (consigné)             |
| `$MaximumHistoryCount`           | 4096                      |
| `$OFS`                           | (Espace ( `" "` )) |
| `$OutputEncoding`                | **UTF8Encoding** , objet   |
| `$ProgressPreference`            | Continuer                  |
| `$PSDefaultParameterValues`      | (Aucune-table de hachage vide) |
| `$PSEmailServer`                 | (aucune)                    |
| `$PSModuleAutoLoadingPreference` | Tous                       |
| `$PSSessionApplicationName`      | wsman                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | Voir [$PSSessionOption](#pssessionoption) |
| `$Transcript`                    | (aucun)                    |
| `$VerbosePreference`             | SilentlyContinue          |
| `$WarningPreference`             | Continue                  |
| `$WhatIfPreference`              | False                     |

PowerShell comprend les variables d’environnement suivantes qui stockent les préférences de l’utilisateur. Pour plus d’informations sur ces variables d’environnement, consultez [about_Environment_Variables](about_Environment_Variables.md).

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> Les modifications apportées à la variable de préférence prennent effet uniquement dans les scripts et les fonctions si ces scripts ou fonctions sont définis dans la même portée que l’étendue dans laquelle la préférence a été utilisée. Pour plus d’informations, consultez [about_Scopes](about_Scopes.md).

## <a name="working-with-preference-variables"></a>Utilisation des variables de préférence

Ce document décrit chacune des variables de préférence.

Pour afficher la valeur actuelle d’une variable de préférence spécifique, tapez le nom de la variable. Par exemple, la commande suivante affiche la `$ConfirmPreference` valeur de la variable.

```powershell
 $ConfirmPreference
```

```Output
High
```

Pour modifier la valeur d’une variable, utilisez une instruction d’assignation. Par exemple, l’instruction suivante modifie la `$ConfirmPreference` valeur du paramètre en **moyenne** .

```powershell
$ConfirmPreference = "Medium"
```

Les valeurs que vous définissez sont spécifiques à la session PowerShell active. Pour rendre les variables effectives dans toutes les sessions PowerShell, ajoutez-les à votre profil PowerShell. Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).

## <a name="working-remotely"></a>Travailler à distance

Lorsque vous exécutez des commandes sur un ordinateur distant, les commandes à distance sont soumises uniquement aux préférences définies dans le client PowerShell de l’ordinateur distant. Par exemple, lorsque vous exécutez une commande distante, la valeur de la variable de l’ordinateur distant `$DebugPreference` détermine la manière dont PowerShell répond aux messages de débogage.

Pour plus d’informations sur les commandes distantes, consultez [about_Remote](about_Remote.md).

### <a name="confirmpreference"></a>\$ConfirmPreference

Détermine si PowerShell vous invite automatiquement à confirmer l’exécution d’une applet de commande ou d’une fonction.

Les `$ConfirmPreference` valeurs valides de la variable sont **haute** , **moyenne** ou **faible** . Les applets de commande et les fonctions se voient attribuer un risque de **haute** , **moyenne** ou **faible** . Lorsque la valeur de la `$ConfirmPreference` variable est inférieure ou égale au risque affecté à une applet de commande ou à une fonction, PowerShell vous invite automatiquement à confirmer l’exécution de l’applet de commande ou de la fonction.

Si la valeur de la `$ConfirmPreference` variable est **None** , PowerShell ne vous invite jamais automatiquement à exécuter une applet de commande ou une fonction.

Pour modifier le comportement de confirmation pour toutes les applets de commande et fonctions de la session, modifiez la `$ConfirmPreference` valeur de la variable.

Pour remplacer le `$ConfirmPreference` pour une seule commande, utilisez le paramètre **Confirm** d’une applet de commande ou d’une fonction. Pour demander une confirmation, utilisez `-Confirm` . Pour supprimer la confirmation, utilisez `-Confirm:$false` .

Valeurs valides `$ConfirmPreference` :

- **None** : PowerShell n’affiche pas d’invite automatiquement. Pour demander la confirmation d’une commande particulière, utilisez le paramètre **Confirm** de l’applet de commande ou de la fonction.
- **Faible** : PowerShell vous invite à confirmer l’exécution des applets de commande ou des fonctions avec un risque faible, moyen ou élevé.
- **Moyenne** : PowerShell vous invite à confirmer l’exécution des applets de commande ou des fonctions avec un risque moyen ou élevé.
- **Élevé** : PowerShell vous invite à confirmer l’exécution des applets de commande ou des fonctions présentant un risque élevé.

#### <a name="detailed-explanation"></a>Explication détaillée

PowerShell peut vous inviter automatiquement à confirmer l’opération avant d’exécuter une action. Par exemple, quand une applet de commande ou une fonction affecte de manière significative le système pour supprimer des données ou utiliser une quantité importante de ressources système.

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

L’estimation du risque est un attribut de l’applet de commande ou de la fonction appelée **ConfirmImpact** . Les utilisateurs ne peuvent pas le changer.

Les applets de commande et les fonctions qui peuvent présenter un risque pour le système disposent d’un paramètre **Confirm** que vous pouvez utiliser pour demander ou supprimer la confirmation pour une seule commande.

Étant donné que la plupart des applets de commande et des fonctions utilisent la valeur de risque par défaut, **ConfirmImpact** , de **Medium** et que la valeur par défaut de `$ConfirmPreference` est **High** , la confirmation automatique se produit rarement. Toutefois, vous pouvez activer la confirmation automatique en remplaçant la valeur de par `$ConfirmPreference` **moyenne** ou **faible** .

#### <a name="examples"></a>Exemples

Cet exemple montre l’effet de la `$ConfirmPreference` valeur par défaut de la variable **High** . La valeur **élevée** confirme uniquement les applets de commande et les fonctions à haut risque. Étant donné que la plupart des applets de commande et des fonctions sont à risque moyen, elles ne sont pas confirmées automatiquement et `Remove-Item` suppriment le fichier. `-Confirm`L’ajout de à la commande invite l’utilisateur à confirmer.

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

Utilisez `-Confirm` pour demander une confirmation.

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

L’exemple suivant montre l’effet de la modification de la valeur de `$ConfirmPreference` en **moyenne** . Étant donné que la plupart des applets de commande et des fonctions sont à risque moyen, elles sont confirmées automatiquement. Pour supprimer l’invite de confirmation pour une seule commande, utilisez le paramètre **Confirm** avec la valeur `$false` .

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a>\$Variable DebugPreference

Détermine la manière dont PowerShell répond aux messages de débogage générés par un script, une applet de commande ou un fournisseur, ou par une `Write-Debug` commande sur la ligne de commande.

Certaines applets de commande affichent des messages de débogage, qui sont généralement des messages techniques destinés aux programmeurs et aux professionnels du support technique. Par défaut, les messages de débogage ne sont pas affichés, mais vous pouvez afficher les messages de débogage en modifiant la valeur de `$DebugPreference` .

Vous pouvez utiliser le paramètre Common de **débogage** d’une applet de commande pour afficher ou masquer les messages de débogage d’une commande spécifique. Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).

Les valeurs valides sont les suivantes :

- **Arrêter** : affiche le message de débogage et arrête l’exécution. Écrit une erreur dans la console.
- **Rechercher** : affiche le message de débogage et vous demande si vous souhaitez continuer. L’ajout du paramètre common **Debug** à une commande, lorsque la commande est configurée pour générer un message de débogage, remplace la valeur de la `$DebugPreference` variable par **inquire** .
- **Continuer** : affiche le message de débogage et poursuit l’exécution.
- **SilentlyContinue** : (valeur par défaut) aucun effet. Le message de débogage n’est pas affiché et l’exécution se poursuit sans interruption.

#### <a name="examples"></a>Exemples

Les exemples suivants illustrent l’effet de la modification des valeurs de `$DebugPreference` lorsqu’une `Write-Debug` commande est entrée sur la ligne de commande.
La modification affecte tous les messages de débogage, y compris les messages générés par les applets de commande et les scripts. Les exemples montrent le paramètre de **débogage** , qui affiche ou masque les messages de débogage associés à une commande unique.

Cet exemple montre l’effet de la `$DebugPreference` valeur par défaut de la variable, **SilentlyContinue** . Par défaut, le `Write-Debug` message de débogage de l’applet de commande n’est pas affiché et le traitement continue. Lorsque le paramètre de **débogage** est utilisé, il se substitue à la préférence pour une seule commande. Le message de débogage s’affiche.

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

Cet exemple montre l’effet de `$DebugPreference` avec la valeur **continue** . Le message de débogage s’affiche et la commande continue à traiter.

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

Cet exemple utilise le paramètre **Debug** avec la valeur `$false` pour supprimer le message d’une seule commande. Le message de débogage n’est pas affiché.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

Cet exemple montre l’effet de la `$DebugPreference` définition de la valeur d' **arrêt** . Le message de débogage s’affiche et la commande est arrêtée.

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

Cet exemple utilise le paramètre **Debug** avec la valeur `$false` pour supprimer le message d’une seule commande. Le message de débogage n’est pas affiché et le traitement n’est pas arrêté.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

Cet exemple montre l’effet de la `$DebugPreference` définition de la valeur de **recherche** . Le message de débogage s’affiche et l’utilisateur est invité à confirmer l’intervention.

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

Cet exemple utilise le paramètre **Debug** avec la valeur `$false` pour supprimer le message d’une seule commande. Le message de débogage n’est pas affiché et le traitement continue.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a>\$ErrorActionPreference

Détermine la manière dont PowerShell répond à une erreur sans fin d’exécution, une erreur qui n’arrête pas le traitement de l’applet de commande. Par exemple, sur la ligne de commande ou dans un script, une applet de commande ou un fournisseur, comme les erreurs générées par l’applet de commande `Write-Error` .

Vous pouvez utiliser le paramètre commun **ErrorAction** d’une applet de commande pour remplacer la préférence pour une commande spécifique.

Les valeurs valides sont les suivantes :

- **Continuer** : (valeur par défaut) affiche le message d’erreur et poursuit l’exécution.
- **Ignorer** : supprime le message d’erreur et poursuit l’exécution de la commande. La valeur **Ignorer** est destinée à une utilisation par commande, et non à une utilisation en tant que préférence enregistrée. L’option **ignore** n’est pas une valeur valide pour la `$ErrorActionPreference` variable.
- **Rechercher** : affiche le message d’erreur et vous demande si vous souhaitez continuer.
- **SilentlyContinue** : aucun effet. Le message d’erreur ne s’affiche pas et l’exécution se poursuit sans interruption.
- **Arrêter** : affiche le message d’erreur et arrête l’exécution. En plus de l’erreur générée, la valeur d' **arrêt** génère un objet ActionPreferenceStopException dans le flux d’erreurs.
  flux
- **Suspend** : suspend automatiquement une tâche de workflow pour permettre une investigation plus poussée. Après l’examen, le flux de travail peut être repris. La valeur de **suspension** est destinée à une utilisation par commande, et non à une utilisation en tant que préférence enregistrée. **Suspend** n’est pas une valeur valide pour la `$ErrorActionPreference` variable.

`$ErrorActionPreference` et le paramètre **ErrorAction** n’affectent pas la manière dont PowerShell répond aux erreurs de fin qui arrêtent le traitement des applets de commande. Pour plus d’informations sur le paramètre commun **ErrorAction** , consultez [about_CommonParameters](about_CommonParameters.md).

#### <a name="examples"></a>Exemples

Ces exemples illustrent l’effet des différentes valeurs de la `$ErrorActionPreference` variable. Le paramètre **ErrorAction** est utilisé pour remplacer la `$ErrorActionPreference` valeur.

Cet exemple montre la `$ErrorActionPreference` valeur par défaut, **continue** . Une erreur sans fin d’achèvement est générée. Le message s’affiche et le traitement continue.

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error -Message  'Test Error' ; Write-Host 'Hello World' : Test Error
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

Hello World
```

Cet exemple montre la `$ErrorActionPreference` valeur par défaut, **inquire** . Une erreur est générée et une invite d’action s’affiche.

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

Cet exemple montre l' `$ErrorActionPreference` ensemble de **SilentlyContinue** .
Le message d’erreur est supprimé.

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

Cet exemple montre le `$ErrorActionPreference` jeu à **arrêter** . Il montre également l’objet supplémentaire généré pour la `$Error` variable.

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

The running command stopped because the preference variable "ErrorActionPreference"
or common parameter is set to Stop: Test Error

Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

### <a name="errorview"></a>\$ErrorView

Détermine le format d’affichage des messages d’erreur dans PowerShell.

Les valeurs valides sont les suivantes :

- **NormalView** : (par défaut) vue détaillée conçue pour la plupart des utilisateurs. Se compose d’une description de l’erreur et du nom de l’objet impliqué dans l’erreur.
- **CategoryView** : vue succincte structurée conçue pour les environnements de production. au format suivant :

  {Category} : ({NomCible} : {TargetType}) : [{Activity}], {Reason}

Pour plus d’informations sur les champs dans **CategoryView** , consultez classe [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) .

#### <a name="examples"></a>Exemples

Cet exemple montre comment une erreur s’affiche lorsque la valeur de `$ErrorView` est la valeur par défaut, **NormalView** . `Get-ChildItem` est utilisé pour rechercher un fichier inexistant.

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

Cet exemple montre comment la même erreur s’affiche lorsque la valeur de `$ErrorView` est remplacée par **CategoryView** .

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

Cet exemple montre que la valeur de `$ErrorView` affecte uniquement l’affichage des erreurs. Elle ne modifie pas la structure de l’objet d’erreur stocké dans la `$Error` variable automatique. Pour plus d’informations sur la `$Error` variable automatique, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

La commande suivante prend l’objet **ErrorRecord** associé à l’erreur la plus récente dans le tableau d’erreurs, **élément 0** , et met en forme toutes les propriétés de l’objet d’erreur dans une liste.

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a>\$FormatEnumerationLimit

Détermine le nombre d’éléments énumérés inclus dans un affichage. Cette variable n’affecte pas les objets sous-jacents, mais uniquement l’affichage. Lorsque la valeur de `$FormatEnumerationLimit` est inférieure au nombre d’éléments énumérés, PowerShell ajoute des points de suspension ( `...` ) pour indiquer les éléments qui ne sont pas affichés.

**Valeurs valides** : entiers ( `Int32` )

**Valeur par défaut** : 4

#### <a name="examples"></a>Exemples

Cet exemple montre comment utiliser la `$FormatEnumerationLimit` variable pour améliorer l’affichage des éléments énumérés.

Dans cet exemple, la commande génère une table qui répertorie tous les services en cours d’exécution sur l’ordinateur en deux groupes : un pour les services **en cours d’exécution** et un pour les services **arrêtés** . Elle utilise une `Get-Service` commande pour obtenir tous les services, puis envoie les résultats via le pipeline à l' `Group-Object` applet de commande, qui regroupe les résultats selon l’état du service.

Le résultat est une table qui répertorie l’État dans la colonne **nom** et les processus dans la colonne **groupe** . Pour modifier les étiquettes de colonne, utilisez une table de hachage, consultez [about_Hash_Tables](about_Hash_Tables.md). Pour plus d’informations, consultez les exemples dans [format-table](xref:Microsoft.PowerShell.Utility.Format-Table).

Recherchez la valeur actuelle de `$FormatEnumerationLimit` .

```powershell
$FormatEnumerationLimit
```

```Output
4
```

Répertorie tous les services regroupés par **État** . Il existe un maximum de quatre services répertoriés dans la colonne **groupe** pour chaque État, car `$FormatEnumerationLimit` a la valeur **4** .

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

Pour augmenter le nombre d’éléments figurant dans la liste, augmentez la valeur de `$FormatEnumerationLimit` à **1000** . Utilisez `Get-Service` et `Group-Object` pour afficher les services.

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

Utilisez `Format-Table` avec le paramètre **Wrap** pour afficher la liste des services.

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a>\$InformationPreference

La `$InformationPreference` variable vous permet de définir les préférences de flux d’informations que vous souhaitez afficher aux utilisateurs. Plus précisément, les messages d’information que vous avez ajoutés aux commandes ou aux scripts en ajoutant l’applet de commande [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information) . Si le paramètre **InformationAction** est utilisé, sa valeur remplace la valeur de la `$InformationPreference` variable. `Write-Information` a été introduit dans PowerShell 5,0.

Les valeurs valides sont les suivantes :

- **Arrêter** : arrête une commande ou un script à une occurrence de la `Write-Information` commande.
- **Rechercher** : affiche le message d’information que vous spécifiez dans une `Write-Information` commande, puis vous demande si vous souhaitez continuer.
- **Continuer** : affiche le message d’information et poursuit son exécution.
- L' **interruption** n’est disponible que pour les flux de travail qui ne sont pas pris en charge dans PowerShell 6 et les versions ultérieures.
- **SilentlyContinue** : (valeur par défaut) aucun effet. Les messages d’information ne sont pas affichés et le script se poursuit sans interruption.

### <a name="logevent"></a>\$Log * (événement)

Les variables de préférence d' **événement log *** déterminent les types d’événements qui sont écrits dans le journal des événements PowerShell dans observateur d’événements. Par défaut, seuls les événements du moteur et du fournisseur sont journalisés. Toutefois, vous pouvez utiliser les variables de préférence d' **événement log *** pour personnaliser votre journal, comme la journalisation des événements sur les commandes.

Les variables de préférence d' **événement log *** sont les suivantes :

- `$LogCommandHealthEvent`: Journalise les erreurs et les exceptions dans l’initialisation et le traitement des commandes. La valeur par défaut est `$false` (non enregistré).
- `$LogCommandLifecycleEvent`: Journalise le démarrage et l’arrêt des commandes et des pipelines de commande et des exceptions de sécurité dans la découverte des commandes. La valeur par défaut est `$false` (non enregistré).
- `$LogEngineHealthEvent`: Journalise les erreurs et les échecs des sessions. La valeur par défaut est `$true` (journalisée).
- `$LogEngineLifecycleEvent`: Journalise l’ouverture et la fermeture des sessions. La valeur par défaut est `$true` (journalisée).
- `$LogProviderHealthEvent`: Journalise des erreurs de fournisseur, telles que des erreurs de lecture et d’écriture, des erreurs de recherche et des erreurs d’appel. La valeur par défaut est `$true` (journalisée).
- `$LogProviderLifecycleEvent`: Enregistre l’ajout et la suppression des fournisseurs PowerShell. La valeur par défaut est `$true` (journalisée). Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](about_Providers.md).

Pour activer un **événement log *** , tapez la variable avec la valeur `$true` , par exemple :

```powershell
$LogCommandLifeCycleEvent = $true
```

Pour désactiver un type d’événement, tapez la variable avec la valeur `$false` , par exemple :

```powershell
$LogCommandLifeCycleEvent = $false
```

Les événements que vous activez sont effectifs uniquement pour la console PowerShell actuelle. Pour appliquer la configuration à toutes les consoles, enregistrez les paramètres de la variable dans votre profil PowerShell. Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).

### <a name="maximumhistorycount"></a>\$MaximumHistoryCount

Détermine le nombre de commandes enregistrées dans l’historique des commandes pour la session active.

**Valeurs valides** : 1-32768 ( `Int32` )

**Valeur par défaut** : 4096

Pour déterminer le nombre de commandes actuellement enregistrées dans l’historique de commande, tapez :

```powershell
(Get-History).Count
```

Pour afficher les commandes enregistrées dans votre historique de session, utilisez l’applet de commande `Get-History` . Pour plus d’informations, consultez [about_History](about_History.md).

### <a name="ofs"></a>\$OFS

Le séparateur de champ de sortie (OFS) spécifie le caractère qui sépare les éléments d’un tableau qui est converti en chaîne.

**Valeurs valides** : n’importe quelle chaîne.

**Valeur par défaut** : espace

Par défaut, la `$OFS` variable n’existe pas et le séparateur de fichier de sortie est un espace, mais vous pouvez ajouter cette variable et la définir sur n’importe quelle chaîne. Vous pouvez modifier la valeur de `$OFS` dans votre session, en tapant `$OFS="<value>"` .

> [!NOTE]
> Si vous prévoyez la valeur par défaut d’un espace ( `" "` ) dans votre script, module ou sortie de configuration, veillez à ce que la `$OFS` valeur par défaut n’ait pas été modifiée ailleurs dans votre code.

#### <a name="examples"></a>Exemples

Cet exemple montre qu’un espace est utilisé pour séparer les valeurs lorsqu’un tableau est converti en chaîne. Dans ce cas, un tableau d’entiers est stocké dans une variable, puis la variable est convertie en chaîne.

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

Pour modifier le séparateur, ajoutez la `$OFS` variable en lui assignant une valeur.
La variable doit être nommée `$OFS` .

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

Pour restaurer le comportement par défaut, vous pouvez assigner un espace ( `" "` ) à la valeur de `$OFS` ou supprimer la variable. Les commandes suivantes suppriment la variable, puis vérifient que le séparateur est un espace.

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a>\$OutputEncoding

Détermine la méthode d’encodage de caractères que PowerShell utilise lorsqu’il envoie du texte à d’autres applications.

Par exemple, si une application retourne des chaînes Unicode à PowerShell, vous devrez peut-être modifier la valeur en **UnicodeEncoding** pour envoyer correctement les caractères.

Les valeurs valides sont les suivantes : objets dérivés d’une classe d’encodage, tels que **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** et **UnicodeEncoding** .

**Default** : objet UTF8Encoding (System. Text. UTF8Encoding)

#### <a name="examples"></a>Exemples

Cet exemple montre comment rendre la commande Windows **findstr.exe** fonctionner dans PowerShell sur un ordinateur localisé pour une langue qui utilise des caractères Unicode, tels que le chinois.

La première commande recherche la valeur de `$OutputEncoding` . Étant donné que la valeur est un objet d’encodage, Affichez uniquement sa propriété **EncodingName** .

```powershell
$OutputEncoding.EncodingName
```

Dans cet exemple, une commande **findstr.exe** est utilisée pour rechercher deux caractères chinois présents dans le `Test.txt` fichier. Quand cette commande **findstr.exe** est exécutée dans l’invite de commandes Windows ( **cmd.exe** ), **findstr.exe** recherche les caractères dans le fichier texte. Toutefois, lorsque vous exécutez la même commande **findstr.exe** dans PowerShell, les caractères ne sont pas trouvés, car PowerShell les envoie à **findstr.exe** en texte ASCII, et non en texte Unicode.

```powershell
findstr <Unicode-characters>
```

Pour que la commande fonctionne dans PowerShell, définissez la valeur de la `$OutputEncoding` propriété **OutputEncoding** de la console, en fonction des paramètres régionaux sélectionnés pour Windows. Étant donné que **OutputEncoding** est une propriété statique de la console, utilisez le double signe deux-points ( `::` ) dans la commande.

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

Après la modification de l’encodage, la commande **findstr.exe** recherche les caractères Unicode.

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a>\$ProgressPreference

Détermine la manière dont PowerShell répond aux mises à jour de progression générées par un script, une applet de commande ou un fournisseur, comme les barres de progression générées par l’applet [de commande Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) .
L' `Write-Progress` applet de commande crée des barres de progression qui indiquent l’état d’une commande.

Les valeurs valides sont les suivantes :

- **Stop** : n’affiche pas la barre de progression. Au lieu de cela, il affiche un message d’erreur et arrête l’exécution.
- **Rechercher** : n’affiche pas la barre de progression. Demande l’autorisation de continuer. Si vous répondez avec `Y` ou `A` , la barre de progression s’affiche.
- **Continuer** : (valeur par défaut) affiche la barre de progression et poursuit l’exécution.
- **SilentlyContinue** : exécute la commande, mais n’affiche pas la barre de progression.

### <a name="psemailserver"></a>\$PSEmailServer

Spécifie le serveur de messagerie par défaut qui est utilisé pour envoyer des messages électroniques. Cette variable de préférence est utilisée par les cmdlets qui envoient des messages électroniques, tels que l’applet de commande [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) .

### <a name="psdefaultparametervalues"></a>\$PSDefaultParameterValues

Spécifie les valeurs par défaut des paramètres des applets de commande et des fonctions avancées.
La valeur de `$PSDefaultParameterValues` est une table de hachage où la clé se compose du nom de l’applet de commande et du nom du paramètre séparés par un signe deux-points ( `:` ). La valeur est une valeur par défaut personnalisée que vous spécifiez.

`$PSDefaultParameterValues` a été introduit dans PowerShell 3,0.

Pour plus d’informations sur cette variable de préférence, consultez [about_Parameters_Default_Values](about_Parameters_Default_Values.md).

### <a name="psmoduleautoloadingpreference"></a>\$PSModuleAutoloadingPreference

Active et désactive l’importation automatique de modules dans la session. **All** est la valeur par défaut. Quelle que soit la valeur de la variable, vous pouvez utiliser [import-module](xref:Microsoft.PowerShell.Core.Import-Module) pour importer un module.

Les valeurs autorisées sont :

- **Tous : les** modules sont importés automatiquement à la première utilisation. Pour importer un module, récupérez ou utilisez une commande quelconque dans le module. Par exemple, utilisez `Get-Command`.
- **ModuleQualified** : les modules sont importés automatiquement uniquement lorsqu’un utilisateur utilise le nom qualifié du module d’une commande dans le module. Par exemple, si l’utilisateur tape `MyModule\MyCommand` , PowerShell importe le module **MyModule** .
- **Aucun** : l’importation automatique des modules est désactivée dans la session. Pour importer un module, utilisez l' `Import-Module` applet de commande.

Pour plus d’informations sur l’importation automatique de modules, consultez [about_Modules](about_Modules.md).

### <a name="pssessionapplicationname"></a>\$PSSessionApplicationName

Spécifie le nom d’application par défaut pour une commande à distance qui utilise la technologie Web Services for Management (WS-Management). Pour plus d’informations, consultez [à propos de Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).

Le nom d’application par défaut du système est `WSMAN` , mais vous pouvez utiliser cette variable de préférence pour modifier la valeur par défaut.

Le nom de l’application est le dernier nœud d’un URI de connexion. Par exemple, le nom de l’application dans l’exemple d’URI suivant est `WSMAN` .

`http://Server01:8080/WSMAN`

Le nom de l’application par défaut est utilisé lorsque la commande distante ne spécifie pas un URI de connexion ou un nom d’application.

Le service **WinRM** utilise le nom de l’application pour sélectionner un écouteur afin de traiter la demande de connexion. La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d’un écouteur sur l’ordinateur distant.

Pour remplacer la valeur système par défaut et la valeur de cette variable, et sélectionner un autre nom d’application pour une session particulière, utilisez les paramètres **ConnectionUri** ou **applicationName** des applets de commande [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)ou [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .

La `$PSSessionApplicationName` variable de préférence est définie sur l’ordinateur local, mais elle spécifie un écouteur sur l’ordinateur distant. Si le nom d’application que vous spécifiez n’existe pas sur l’ordinateur distant, la commande d’établissement de la session échoue.

### <a name="pssessionconfigurationname"></a>\$PSSessionConfigurationName

Spécifie la configuration de session par défaut utilisée pour les **sessions PSSession** créés dans la session active.

Cette variable de préférence est définie sur l’ordinateur local, mais elle spécifie une configuration de session qui se trouve sur l’ordinateur distant.

La valeur de la `$PSSessionConfigurationName` variable est un URI de ressource complet.

La valeur par défaut `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indique la configuration de session **Microsoft. PowerShell** sur l’ordinateur distant.

Si vous spécifiez uniquement un nom de configuration, l’URI de schéma suivant est ajouté :

`http://schemas.microsoft.com/PowerShell/`

Vous pouvez remplacer la valeur par défaut et sélectionner une autre configuration de session pour une session particulière à l’aide du paramètre **ConfigurationName** des `New-PSSession` applets de commande, `Enter-PSSession` ou `Invoke-Command` .

Vous pouvez modifier la valeur de cette variable à tout moment. Dans ce cas, n’oubliez pas que la configuration de session que vous sélectionnez doit exister sur l’ordinateur distant. Si ce n’est pas le cas, la commande permettant de créer une session qui utilise la configuration de session échoue.

Cette variable de préférence ne détermine pas les configurations de sessions locales utilisées lorsque les utilisateurs distants créent une session qui se connecte à cet ordinateur.
Toutefois, vous pouvez utiliser les autorisations pour les configurations de session locale pour déterminer les utilisateurs qui peuvent les utiliser.

### <a name="pssessionoption"></a>\$PSSessionOption

Établit les valeurs par défaut pour les options utilisateur avancées dans une session à distance.
Ces préférences de l’option remplacent les valeurs par défaut du système pour les options de session.

La `$PSSessionOption` variable contient un objet **PSSessionOption** . Pour plus d’informations, consultez [System. Management. Automation. Remoting. PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).
Chaque propriété de l’objet représente une option de session. Par exemple, la propriété **NoCompression** active la compression des données pendant la session.

Par défaut, la `$PSSessionOption` variable contient un objet **PSSessionOption** avec les valeurs par défaut pour toutes les options, comme indiqué ci-dessous.

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

Pour obtenir une description de ces options et des informations supplémentaires, consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption). Pour plus d’informations sur les commandes et les sessions à distance, consultez [about_Remote](about_Remote.md) et [about_PSSessions](about_PSSessions.md).

Pour modifier la valeur de la `$PSSessionOption` variable de préférence, utilisez l' `New-PSSessionOption` applet de commande pour créer un objet **PSSessionOption** avec les valeurs d’option que vous préférez. Enregistrez la sortie dans une variable appelée `$PSSessionOption` .

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

Pour utiliser la `$PSSessionOption` variable de préférence dans chaque session PowerShell, ajoutez une `New-PSSessionOption` commande qui crée la `$PSSessionOption` variable à votre profil PowerShell. Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).

Vous pouvez définir des options personnalisées pour une session à distance particulière. Les options que vous définissez prévalent sur les valeurs par défaut du système et sur la valeur de la `$PSSessionOption` variable de préférence.

Pour définir des options de session personnalisées, utilisez l' `New-PSSessionOption` applet de commande pour créer un objet **PSSessionOption** . Ensuite, utilisez l’objet **PSSessionOption** comme valeur du paramètre **SessionOption** dans les applets de commande qui créent une session, telles que `New-PSSession` , `Enter-PSSession` et `Invoke-Command` .

### <a name="transcript"></a>$Transcript

Utilisé par `Start-Transcript` pour spécifier le nom et l’emplacement du fichier de transcription. Si vous ne spécifiez pas de valeur pour le paramètre **path** , `Start-Transcript` utilise le chemin d’accès dans la valeur de la `$Transcript` variable globale. Si vous n’avez pas créé cette variable, `Start-Transcript` stocke les transcriptions dans le `$Home\My Documents` répertoire sous forme de `\PowerShell_transcript.<time-stamp>.txt` fichiers.

### <a name="verbosepreference"></a>\$VerbosePreference

Détermine la manière dont PowerShell répond aux messages détaillés générés par un script, une applet de commande ou un fournisseur, tels que les messages générés par l’applet de commande [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) .
Les messages détaillés décrivent les actions effectuées pour exécuter une commande.

Par défaut, les messages détaillés ne sont pas affichés, mais vous pouvez modifier ce comportement en modifiant la valeur de `$VerbosePreference` .

Vous pouvez utiliser le paramètre commun **Verbose** d’une applet de commande pour afficher ou masquer les messages détaillés pour une commande spécifique. Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).

Les valeurs valides sont les suivantes :

- **Arrêter** : affiche le message détaillé et un message d’erreur, puis arrête l’exécution.
- **Rechercher** : affiche le message détaillé, puis affiche une invite vous demandant si vous souhaitez continuer.
- **Continuer** : affiche le message détaillé, puis poursuit l’exécution.
- **SilentlyContinue** : (par défaut) n’affiche pas le message détaillé. Continue l’exécution.

#### <a name="examples"></a>Exemples

Ces exemples illustrent l’effet des différentes valeurs de `$VerbosePreference` et le paramètre **Verbose** pour remplacer la valeur de préférence.

Cet exemple montre l’effet de la valeur **SilentlyContinue** , qui est la valeur par défaut. La commande utilise le paramètre **message** , mais n’écrit pas de message dans la console PowerShell.

```powershell
Write-Verbose -Message "Verbose message test."
```

Lorsque le paramètre **Verbose** est utilisé, le message est écrit.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

Cet exemple montre l’effet de la valeur **continue** . La `$VerbosePreference` variable est définie pour **Continuer** et le message s’affiche.

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

Cet exemple utilise le paramètre **Verbose** avec une valeur de `$false` qui remplace la valeur **continue** . Le message n’est pas affiché.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

Cet exemple montre l’effet de la valeur d' **arrêt** . La `$VerbosePreference` variable est définie sur **Stop** et le message s’affiche. La commande est arrêtée.

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

Cet exemple utilise le paramètre **Verbose** avec une valeur de `$false` qui remplace la valeur d' **arrêt** . Le message n’est pas affiché.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

Cet exemple montre l’effet de la valeur de **recherche** . La `$VerbosePreference` variable est définie sur **inquire** . Le message s’affiche et l’utilisateur est invité à confirmer l’intervention.

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

Cet exemple utilise le paramètre **Verbose** avec une valeur de `$false` qui remplace la valeur de **recherche** . L’utilisateur n’est pas invité et le message n’est pas affiché.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a>\$WarningPreference

Détermine la manière dont PowerShell répond aux messages d’avertissement générés par un script, une applet de commande ou un fournisseur, tels que les messages générés par l’applet de commande [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) .

Par défaut, les messages d’avertissement s’affichent et l’exécution se poursuit, mais vous pouvez modifier ce comportement en modifiant la valeur de `$WarningPreference` .

Vous pouvez utiliser le paramètre commun **WarningAction** d’une applet de commande pour déterminer comment PowerShell répond aux avertissements d’une commande particulière. Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).

Les valeurs valides sont les suivantes :

- **Arrêter** : affiche le message d’avertissement et un message d’erreur, puis arrête l’exécution.
- **Rechercher** : affiche le message d’avertissement, puis demande l’autorisation de continuer.
- **Continuer** : (valeur par défaut) affiche le message d’avertissement, puis continue l’exécution.
- **SilentlyContinue** : n’affiche pas le message d’avertissement. Continue l’exécution.

#### <a name="examples"></a>Exemples

Ces exemples illustrent l’effet des différentes valeurs de `$WarningPreference` .
Le paramètre **WarningAction** remplace la valeur de préférence.

Cet exemple montre l’effet de la valeur par défaut, **continue** .

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

Cet exemple utilise le paramètre **WarningAction** avec la valeur **SilentlyContinue** pour supprimer l’avertissement. Le message n’est pas affiché.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

Cet exemple remplace la `$WarningPreference` variable par la valeur **SilentlyContinue** . Le message n’est pas affiché.

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

Cet exemple utilise le paramètre **WarningAction** pour s’arrêter lorsqu’un avertissement est généré.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

Cet exemple remplace la `$WarningPreference` variable par la valeur de **recherche** . L’utilisateur est invité à confirmer l’intervention.

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

Cet exemple utilise le paramètre **WarningAction** avec la valeur **SilentlyContinue** . La commande continue de s’exécuter et aucun message n’est affiché.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

Cet exemple modifie la `$WarningPreference` valeur en **Stop** .

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

Cet exemple utilise **WarningAction** avec la valeur **Inquiry** . Lorsqu’un avertissement se produit, l’utilisateur est invité à entrer un message.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a>\$WhatIfPreference quand vous

Détermine si **WhatIf** est activé automatiquement pour chaque commande qui le prend en charge. Lorsque **WhatIf** est activé, l’applet de commande signale l’effet attendu de la commande, mais n’exécute pas la commande.

Les valeurs valides sont les suivantes :

- **False** ( **0** , non activé) : (valeur par défaut) **WhatIf** n’est pas activé automatiquement. Pour l’activer manuellement, utilisez le paramètre **WhatIf** de l’applet de commande.
- **True** ( **1** , activé) : **WhatIf** est activé automatiquement sur toute commande qui le prend en charge. Les utilisateurs peuvent utiliser le paramètre **WhatIf** avec la valeur **false** pour le désactiver manuellement, par exemple `-WhatIf:$false` .

#### <a name="examples"></a>Exemples

Ces exemples illustrent l’effet des différentes valeurs de `$WhatIfPreference` .
Ils montrent comment utiliser le paramètre **WhatIf** pour remplacer la valeur de préférence pour une commande spécifique.

Cet exemple montre l’effet de la `$WhatIfPreference` variable définie sur la valeur par défaut, **false** . Utilisez `Get-ChildItem` pour vérifier que le fichier existe.
`Remove-Item` supprime le fichier. Une fois le fichier supprimé, vous pouvez vérifier la suppression avec `Get-ChildItem` .

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

Cet exemple montre l’effet de l’utilisation du paramètre **WhatIf** lorsque la valeur de `$WhatIfPreference` est **false** .

Vérifiez que le fichier existe.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

Utilisez le paramètre **WhatIf** pour déterminer le résultat de la tentative de suppression du fichier.

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

Vérifiez que le fichier n’a pas été supprimé.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

Cet exemple montre l’effet de la `$WhatIfPreference` variable définie sur la valeur **true** . Lorsque vous utilisez `Remove-Item` pour supprimer un fichier, le chemin d’accès du fichier est affiché, mais le fichier n’est pas supprimé.

Tentative de suppression d’un fichier. Un message s’affiche à propos de ce qui se passe si `Remove-Item` a été exécuté, mais le fichier n’est pas supprimé.

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

Utilisez `Get-ChildItem` pour vérifier que le fichier n’a pas été supprimé.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

Cet exemple montre comment supprimer un fichier lorsque la valeur de `$WhatIfPreference` est **true** . Elle utilise le paramètre **WhatIf** avec la valeur `$false` . Utilisez `Get-ChildItem` pour vérifier que le fichier a été supprimé.

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

Voici quelques exemples de l’applet de commande `Get-Process` qui ne prend pas en charge **WhatIf** et `Stop-Process` qui prend en charge **WhatIf** . La `$WhatIfPreference` valeur de la variable est **true** .

`Get-Process` ne prend pas en charge **WhatIf** . Lorsque la commande est exécutée, elle affiche le processus **WINWORD** .

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

`Stop-Process` prend en charge **WhatIf** . Le processus **WINWORD** n’est pas arrêté.

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

Vous pouvez remplacer le comportement `Stop-Process` **WhatIf** en utilisant le paramètre **WhatIf** avec la valeur `$false` . Le processus **WINWORD** est arrêté.

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

Pour vérifier que le processus **WINWORD** a été arrêté, utilisez `Get-Process` .

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_CommonParameters](about_CommonParameters.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Variables](about_Variables.md)
