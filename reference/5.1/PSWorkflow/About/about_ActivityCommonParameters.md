---
description: Décrit les paramètres que Windows PowerShell workflow ajoute aux activités.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: 93fdcdb9c5afe0b73e843baf2474ec7d3f96a6cf
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387802"
---
# <a name="about-activitycommonparameters"></a>À propos de ActivityCommonParameters

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit les paramètres que Windows PowerShell workflow ajoute aux activités.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le workflow Windows PowerShell ajoute les paramètres communs d’activité aux activités dérivées de la classe de base PSActivity. Cette catégorie comprend l’activité InlineScript et les applets de commande Windows PowerShell qui sont implémentées en tant qu’activités, telles que Get-Process et WinEvent.

Les paramètres communs d’activité ne sont pas valides sur les activités Suspend-Workflow et Checkpoint-Workflow et ne sont pas ajoutés aux applets de commande ou aux expressions que Windows PowerShell Workflow exécute automatiquement dans un bloc de script InlineScript ou une activité similaire. Les paramètres communs d'activités sont disponibles sur l'activité InlineScript, mais pas sur les commandes figurant dans le bloc de script InlineScript.

Plusieurs des paramètres communs d’activité sont également des paramètres communs de flux de travail ou des paramètres communs Windows PowerShell. Les autres paramètres communs d’activité sont spécifiques aux activités.

Pour plus d’informations sur les paramètres communs de workflow, consultez about_WorkflowCommonParameters. Pour plus d’informations sur les paramètres communs de Windows PowerShell, consultez about_CommonParameters.

### <a name="list-of-activity-common-parameters"></a>LISTE DES PARAMÈTRES COMMUNS D’ACTIVITÉ

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a>DESCRIPTIONS DES PARAMÈTRES

Cette section décrit les paramètres communs d’activité.

#### <a name="appendoutput-boolean"></a>AppendOutput \<Boolean\>

La valeur `$True` ajoute la sortie de l’activité à la valeur de la variable.
La valeur n' `$False` a aucun effet. Par défaut, l’attribution d’une valeur à une variable remplace la valeur de la variable.

Par exemple, les commandes suivantes ajoutent un objet processus à l’objet de service dans la `$x` variable.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

Ce paramètre est conçu pour les workflows basés sur XAML. Dans les workflows de script, vous pouvez également utiliser l’opérateur d’assignation + = pour ajouter une sortie à la valeur d’une variable, comme indiqué dans l’exemple suivant.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a>Debug \<SwitchParameter\>

Affiche des détails au niveau du programmeur sur l’opération effectuée par la commande.
Le paramètre de débogage remplace la valeur de la variable $DebugPreference pour la commande actuelle. Ce paramètre fonctionne uniquement lorsque la commande génère des messages de débogage. Ce paramètre est également un paramètre commun Windows PowerShell.

#### <a name="displayname-string"></a>NomComplet \<String\>

Spécifie le nom convivial de l’activité. La valeur DisplayName apparaît dans la barre de progression pendant l’exécution du workflow et dans la valeur de la propriété Progress de la tâche de Workflow. Lorsque le paramètre PSProgressMessage est également inclus dans la commande, le contenu de la barre de progression s’affiche dans \<DisplayName\> : \<PSProgressMessage\> format.

#### <a name="erroraction-actionpreference"></a>ErrorAction \<ActionPreference\>

Détermine la façon dont l’activité répond à une erreur sans fin d’achèvement à partir de la commande. Elle n’a aucun effet sur les erreurs d’arrêt. Ce paramètre fonctionne uniquement lorsque la commande génère une erreur sans fin d’achèvement, telle que celles de l’applet de commande Write-Error. Le paramètre ErrorAction remplace la valeur de la variable $ErrorActionPreference pour la commande actuelle. Ce paramètre est également un paramètre commun Windows PowerShell.

Valeurs valides :

- Pouvoir. Affiche le message d’erreur et poursuit l’exécution de la commande. « Continue » est la valeur par défaut.

- à ignorer. Supprime le message d’erreur et poursuit l’exécution de la commande.
  Contrairement à SilentlyContinue, ignore n’ajoute pas le message d’erreur à la variable automatique $Error. La valeur ignorer est introduite dans Windows PowerShell 3,0.

- Inquire. Affiche le message d’erreur et vous invite à confirmer avant de poursuivre l’exécution. Cette valeur est rarement utilisée.

- Interrompre : Suspend automatiquement une tâche de workflow pour permettre une investigation plus poussée. Après l’examen, le flux de travail peut être repris.

- SilentlyContinue. Supprime le message d’erreur et poursuit l’exécution de la commande.

- Arrêter. Affiche le message d’erreur et arrête l’exécution de la commande.

#### <a name="input-object"></a>Entrée \<Object[]\>

Soumet une collection d’objets à une activité. Il s’agit d’une alternative à la canalisation des objets vers l’activité un à un.

#### <a name="mergeerrortooutput-boolean"></a>MergeErrorToOutput \<Boolean\>

`$True`La valeur ajoute des erreurs au flux de sortie. La valeur n' `$False` a pas d’effet. Utilisez ce paramètre avec les `ForEach -Parallel` Mots clés Parallel et pour collecter les erreurs et la sortie de plusieurs commandes parallèles dans une collection unique.

#### <a name="psactionretrycount-int32"></a>PSActionRetryCount \<Int32\>

Essaie à plusieurs reprises d’exécuter l’activité en cas d’échec de la première tentative. La valeur par défaut 0 n’effectue pas de nouvelle tentative.

#### <a name="psactionretryintervalsec-int32"></a>PSActionRetryIntervalSec \<Int32\>

Détermine l’intervalle entre les actions de nouvelle tentative (en secondes). La valeur par défaut 0 retente l’action immédiatement. Ce paramètre n’est valide que si le paramètre PSActionRetryCount est également utilisé dans la commande.

#### <a name="psactionrunningtimeoutsec-int32"></a>PSActionRunningTimeoutSec \<Int32\>

Détermine la durée pendant laquelle l’activité peut s’exécuter sur chaque ordinateur cible. Si l’activité ne se termine pas avant l’expiration du délai d’attente, le workflow Windows PowerShell génère une erreur de fin et arrête le traitement du workflow sur l’ordinateur cible concerné.

#### <a name="psallowredirection-boolean"></a>PSAllowRedirection \<Boolean\>

La valeur $True permet la redirection de la connexion aux ordinateurs cibles.
La valeur $False n’a aucun effet. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Quand vous utilisez le paramètre PSConnectionURI, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, Windows PowerShell ne redirige pas les connexions, mais vous pouvez utiliser le paramètre PSAllowRedirection avec la valeur $True pour autoriser la redirection de la connexion à l’ordinateur cible.

Vous pouvez également limiter le nombre de redirections de la connexion en définissant la propriété MaximumConnectionRedirectionCount de la `$PSSessionOption` variable de préférence ou la propriété MaximumConnectionRedirectionCount de la valeur du paramètre SSessionOption des applets de commande qui créent une session. La valeur par défaut est 5.

#### <a name="psapplicationname-string"></a>PSApplicationName \<String\>

Spécifie le segment de nom d’application de l’URI de connexion utilisé pour se connecter aux ordinateurs cibles. Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre ConnectionURI dans la commande. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur cible. Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN. Cette valeur convient pour la plupart des utilisations. Pour plus d’informations, consultez [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion. La valeur de ce paramètre doit correspondre à la valeur de la propriété URLPrefix d'un écouteur sur l'ordinateur distant.

#### <a name="psauthentication-authenticationmechanism"></a>PSAuthentication \<AuthenticationMechanism\>

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lors de la connexion aux ordinateurs cibles. Les valeurs valides sont Default, Basic, Credssp, Digest, Kerberos, Negotiate et NegotiateWithImplicitCredential. La valeur par défaut est Default. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Pour plus d’informations sur les valeurs de ce paramètre, consultez la description de l’énumération **System. Management. Automation. instances d’exécution. AuthenticationMechanism** dans le kit de développement logiciel (SDK) PowerShell.

> [!WARNING]
> L'authentification CredSSP (Credential Security Service Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

#### <a name="pscertificatethumbprint-string"></a>PSCertificateThumbprint \<String\>

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action. Entrez l’empreinte numérique du certificat. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent uniquement être mappés aux comptes d'utilisateurs locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir un certificat, utilisez les applets de commande [obtenir-Item](xref:Microsoft.PowerShell.Management.Get-Item) ou [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) dans le lecteur Cert : de Windows PowerShell.

#### <a name="pscomputername-string"></a>PSComputerName \<String[]\>

Spécifie les ordinateurs cibles sur lesquels l’activité s’exécute. La valeur par défaut est l'ordinateur local. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules. Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, « localhost » ou un point (.).

Pour inclure l’ordinateur local dans la valeur du paramètre PSComputerName, ouvrez Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».

Si ce paramètre est omis de la commande, ou si la valeur est $null ou une chaîne vide, la cible de workflow est l’ordinateur local et la communication à distance Windows PowerShell n’est pas utilisée pour exécuter la commande.

Pour utiliser une adresse IP dans la valeur du paramètre ComputerName, la commande doit inclure le paramètre PSCredential. En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local. Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).

#### <a name="psconfigurationname-string"></a>PSConfigurationName \<String\>

Spécifie les configurations de session utilisées pour créer des sessions sur les ordinateurs cibles. Entrez le nom d’une configuration de session sur les ordinateurs cibles (et non sur l’ordinateur qui exécute le Workflow. La valeur par défaut est Microsoft. PowerShell. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

#### <a name="psconnectionretrycount-uint"></a>PSConnectionRetryCount \<UInt\>

Spécifie le nombre maximal de tentatives de connexion à chaque ordinateur cible en cas d’échec de la première tentative de connexion. Entrez un nombre compris entre 1 et 4 294 967 295 (UInt. MaxValue). La valeur par défaut, zéro (0), ne représente aucune nouvelle tentative.
Ce paramètre commun d’activité est également un paramètre commun de Workflow.

#### <a name="psconnectionretryintervalsec-uint"></a>PSConnectionRetryIntervalSec \<UInt\>

Spécifie le délai entre les nouvelles tentatives de connexion en secondes. La valeur par défaut est zéro (0). Ce paramètre est valide uniquement lorsque la valeur de PSConnectionRetryCount est au moins égale à 1. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

#### <a name="psconnectionuri-systemuri"></a>PSConnectionURI \<System.Uri\>

Spécifie un Uniform Resource Identifier (URI) qui définit le point de terminaison de connexion pour l’activité sur l’ordinateur cible. L’URI doit être complet. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Le format de cette chaîne est le suivant :

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

La valeur par défaut est `http://localhost:5985/WSMAN`.

Si vous ne spécifiez pas de PSConnectionURI, vous pouvez utiliser les paramètres PSUseSSL, PSComputerName, PSPort et PSApplicationName pour spécifier les valeurs PSConnectionURI.

Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance Windows PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPS.

#### <a name="pscredential-pscredential"></a>PSCredential \<PSCredential\>

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter l’activité sur l’ordinateur cible. La valeur par défaut est l’utilisateur actuel. Ce paramètre n’est valide que si le paramètre PSComputerName est inclus dans la commande. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domaine01\utilisateur01 », ou entrez une variable qui contient un objet PSCredential, tel que celui retourné par l’applet de commande Get-Credential. Si vous entrez uniquement un nom d'utilisateur, vous êtes invité à entrer un mot de passe.

#### <a name="psdebug-psdatacollectiondebugrecord"></a>PSDebug \<PSDataCollection[DebugRecord]\>

Ajoute des messages de débogage de l’activité à la collection d’enregistrements de débogage spécifiée, au lieu d’écrire les messages de débogage dans la console ou à la valeur de la propriété de débogage de la tâche de flux de travail. Vous pouvez ajouter des messages de débogage de plusieurs activités au même objet de collection d’enregistrements de débogage.

Pour utiliser ce paramètre commun d’activité, utilisez l’applet de commande New-Object pour créer un objet PSDataCollection avec un type DebugRecord et enregistrer l’objet dans une variable. Ensuite, utilisez la variable comme valeur du paramètre PSDebug d’une ou plusieurs activités, comme indiqué dans l’exemple suivant.

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a>PSDisableSerialization \<Boolean\>

Indique à l’activité de retourner les objets « dynamiques » (non sérialisés) au workflow.
Les objets ainsi générés ont des méthodes, ainsi que des propriétés, mais ils ne peuvent pas être enregistrés lorsqu’un point de contrôle est activé.

#### <a name="psdisableserializationpreference-boolean"></a>PSDisableSerializationPreference \<Boolean\>

Applique l’équivalent du paramètre PSDisableSerialization à l’ensemble du workflow, pas seulement à l’activité. L’ajout de ce paramètre n’est généralement pas recommandé, car un workflow qui ne sérialise pas ses objets ne peut pas être repris ou rendu persistant.

Valeurs valides :

- Valeurs En cas d’omission, et que vous n’avez pas ajouté le paramètre PSDisableSerialization à une activité, les objets sont sérialisés.

- `$True`. Indique à toutes les activités au sein d’un workflow de retourner les objets « dynamiques » (non sérialisés). Les objets ainsi générés ont des méthodes, ainsi que des propriétés, mais ils ne peuvent pas être enregistrés lorsqu’un point de contrôle est activé.
- `$False`. Les objets de workflow sont sérialisés.

#### <a name="pserror-psdatacollectionerrorrecord"></a>PSError \<PSDataCollection[ErrorRecord]\>

Ajoute des messages d’erreur de l’activité à la collection d’enregistrements d’erreurs spécifiée, au lieu d’écrire les messages d’erreur dans la console ou à la valeur de la propriété Error de la tâche de Workflow. Vous pouvez ajouter des messages d’erreur de plusieurs activités au même objet de collection d’enregistrements d’erreur.

Pour utiliser ce paramètre commun d’activité, utilisez l' `New-Object` applet de commande pour créer un objet PSDataCollection avec un type ErrorRecord et enregistrer l’objet dans une variable. Ensuite, utilisez la variable comme valeur du paramètre PSError d’une ou plusieurs activités, comme indiqué dans l’exemple suivant.

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a>PSPersist \<Boolean\>

Prend un point de contrôle après l’activité. Ce point de contrôle s’ajoute à tous les points de contrôle spécifiés dans le flux de travail. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Un « point de contrôle » ou un « point de persistance » est un instantané de l’état du flux de travail et des données capturées pendant l’exécution du workflow et il est enregistré dans un magasin de persistance sur le disque. Le workflow Windows PowerShell utilise les données enregistrées pour reprendre un workflow suspendu ou interrompu à partir du dernier point de persistance, plutôt que de redémarrer le flux de travail.

Valeurs valides :

- Valeurs Si vous omettez ce paramètre, aucun point de contrôle n’est ajouté. Les points de contrôle sont pris en fonction des paramètres du flux de travail.

- `$True`. Applique un point de contrôle une fois l’activité terminée.
  Ce point de contrôle s’ajoute à tous les points de contrôle spécifiés dans le flux de travail.

- `$False`. Aucun point de contrôle n’est ajouté. Les points de contrôle sont pris uniquement lorsqu’ils sont spécifiés dans le flux de travail.

#### <a name="psport-int32"></a>PSPort \<Int32\>

Spécifie le port réseau sur les ordinateurs cibles. Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPS). Ce paramètre commun d’activité est également un paramètre commun de Workflow.

N’utilisez pas le paramètre PSPort, sauf si vous devez le faire. Le port défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs. Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.

#### <a name="psprogress-psdatacollectionprogressrecord"></a>PSProgress \<PSDataCollection[ProgressRecord]\>

Ajoute des messages de progression de l’activité à la collection d’enregistrements de progression spécifiée au lieu d’écrire les messages de progression dans la console ou à la valeur de la propriété Progress de la tâche de Workflow. Vous pouvez ajouter des messages de progression de plusieurs activités au même objet de collection d’enregistrements de progression.

#### <a name="psprogressmessage-string"></a>PSProgressMessage \<String\>

Spécifie la description conviviale de l’activité. La valeur PSProgressMessage apparaît dans la barre de progression pendant l’exécution du flux de travail. Lorsque DisplayName est également inclus dans la commande, le contenu de la barre de progression s’affiche dans \<DisplayName\> : \<PSProgressMessage\> format.

Ce paramètre est particulièrement utile pour identifier des activités dans un bloc de script ForEach-Parallel. Sans ce message, les activités de toutes les branches parallèles sont identifiées par le même nom.

#### <a name="psremotingbehavior-remotingbehavior"></a>PSRemotingBehavior \<RemotingBehavior\>

Spécifie la gestion de la communication à distance lorsque l’activité est exécutée sur les ordinateurs cibles.
PowerShell est la valeur par défaut.

Les valeurs autorisées sont :

- Aucun : l’activité n’est pas exécutée sur des ordinateurs distants.

- PowerShell : la communication à distance Windows PowerShell est utilisée pour exécuter l’activité sur les ordinateurs cibles.

- Personnalisé : l’activité prend en charge son propre type de communication à distance. Cette valeur est valide lorsque l’applet de commande qui est implémentée en tant qu’activité définit la valeur de l’attribut RemotingCapability sur SupportedByCommand et que la commande comprend le paramètre ComputerName.

#### <a name="psrequiredmodules-string"></a>PSRequiredModules \<String[]\>

Importe les modules spécifiés avant d’exécuter la commande. Entrez les noms des modules. Les modules doivent être installés sur l’ordinateur cible.

Les modules installés dans un chemin d’accès spécifié dans la variable d’environnement PSModulePath sont automatiquement importés lors de la première utilisation d’une commande dans le module.
Utilisez ce paramètre pour importer des modules qui ne se trouvent pas dans un emplacement PSModulePath.

Étant donné que chaque activité d’un workflow s’exécute dans sa propre session, une commande Import-Module importe un module uniquement dans la session dans laquelle il s’exécute. Elle n’importe pas le module dans des sessions dans lesquelles d’autres activités sont exécutées.

#### <a name="pssessionoption-pssessionoption"></a>PSSessionOption \<PSSessionOption\>

Définit des options avancées pour les sessions sur les ordinateurs cibles. Entrez un objet PSSessionOption, tel que celui que vous créez à l’aide de l’applet de commande New-PSSessionOption. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

Les valeurs par défaut pour les options de session sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Dans le cas contraire, la session utilise les valeurs spécifiées dans la configuration de session.

Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez la rubrique d’aide de l’applet de commande New-PSSessionOption [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

Pour plus d’informations sur la variable de préférence $PSSessionOption, consultez [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

#### <a name="psusessl-boolean"></a>PSUseSSL \<Boolean\>

La valeur $True utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur cible. Par défaut, SSL n'est pas utilisé. La valeur $False n’a aucun effet. Ce paramètre commun d’activité est également un paramètre commun de Workflow.

WS-Management chiffre tout le contenu Windows PowerShell transmis sur le réseau. UseSSL est une protection supplémentaire qui envoie les données via HTTPS au lieu de HTTP. Si vous utilisez ce paramètre, mais que SSL n'est pas disponible sur le port utilisé pour la commande, celle-ci échoue.

#### <a name="psverbose-psdatacollectionverboserecord"></a>PSVerbose \<PSDataCollection[VerboseRecord]\>

Ajoute des messages détaillés de l’activité à la collection d’enregistrements détaillés spécifiée, au lieu d’écrire les messages détaillés dans la console ou à la valeur de la propriété verbose de la tâche de Workflow. Vous pouvez ajouter des messages en clair de plusieurs activités au même objet de collection d’enregistrements en clair.

#### <a name="pswarning-psdatacollectionwarningrecord"></a>PSWarning \<PSDataCollection[WarningRecord]\>

Ajoute des messages d’avertissement de l’activité à la collection d’enregistrements d’avertissements spécifiée au lieu d’écrire les messages d’avertissement dans la console ou à la valeur de la propriété Warning de la tâche de Workflow. Vous pouvez ajouter des messages d’avertissement de plusieurs activités au même objet de collection d’enregistrements d’avertissement.

#### <a name="result"></a>Résultats

Ce paramètre n’est valide que dans les workflows XAML.

#### <a name="usedefaultinput-boolean"></a>UseDefaultInput \<Boolean\>

Accepte toutes les entrées de workflow en tant qu’entrée dans l’activité par valeur.

Par exemple, l’activité Get-Process de l’exemple de workflow suivant utilise le paramètre commun d’activité UseDefaultInput pour obtenir une entrée qui est transmise au workflow. Lorsque vous exécutez le workflow avec l’entrée, cette dernière est utilisée par l’activité.

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a>Verbose \<SwitchParameter\>

Affiche des informations détaillées sur l’opération effectuée par la commande.
Ces informations sont semblables aux informations contenues dans une trace ou dans un journal des transactions.
Le paramètre Verbose remplace la valeur de la variable $VerbosePreference pour la commande actuelle. Ce paramètre fonctionne uniquement lorsque la commande génère un message détaillé. Ce paramètre est également un paramètre commun Windows PowerShell.

#### <a name="warningaction-actionpreference"></a>WarningAction \<ActionPreference\>

Détermine la façon dont l’activité répond à un avertissement. « Continue » est la valeur par défaut. Le paramètre WarningAction remplace la valeur de la variable $WarningPreference pour la commande actuelle. Ce paramètre fonctionne uniquement lorsque la commande génère un message d’avertissement. Ce paramètre est également un paramètre commun Windows PowerShell.

Valeurs valides :

- SilentlyContinue. Supprime le message d’avertissement et poursuit l’exécution de la commande.

- Pouvoir. Affiche le message d’avertissement et poursuit l’exécution de la commande.
  « Continue » est la valeur par défaut.

- Inquire. Affiche le message d’avertissement et vous invite à confirmer l’exécution. Cette valeur est rarement utilisée.

- Arrêter. Affiche le message d’avertissement et arrête l’exécution de la commande.

> [!NOTE]
> Le paramètre WarningAction ne remplace pas la valeur de la variable de préférence $WarningAction lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.

### <a name="examples"></a>EXEMPLES

Les paramètres communs d’activité sont extrêmement utiles. Par exemple, vous pouvez utiliser le paramètre PSComputerName pour exécuter des activités spécifiques sur un sous-ensemble d’ordinateurs cibles.

Vous pouvez également utiliser les paramètres PSConnectionRetryCount et PSConnectionRetryIntervalSec pour ajuster les valeurs de nouvelle tentative pour des activités particulières.

L’exemple suivant montre comment utiliser les paramètres communs d’activité PSComputerName pour exécuter une activité de Get-EventLog uniquement sur des ordinateurs informatiques d’un domaine particulier.

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a>VOIR AUSSI

[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)
