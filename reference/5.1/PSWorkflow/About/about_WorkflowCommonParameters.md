---
description: Cette rubrique décrit les paramètres qui sont valides pour toutes les commandes de workflow Windows PowerShell. Étant donné que le moteur Windows PowerShell les ajoute aux flux de travail, vous pouvez utiliser ces paramètres sur n’importe quel flux de travail et ils sont automatiquement activés sur les workflows que vous créez.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: 386200475c1dab9735921edd60abbde20ee354c4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207214"
---
# <a name="about-workflowcommonparameters"></a>À propos de WorkflowCommonParameters

## <a name="short-description"></a>DESCRIPTION COURTE

Cette rubrique décrit les paramètres qui sont valides pour toutes les commandes de workflow Windows PowerShell. Étant donné que le moteur Windows PowerShell les ajoute aux flux de travail, vous pouvez utiliser ces paramètres sur n’importe quel flux de travail et ils sont automatiquement activés sur les workflows que vous créez.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les paramètres communs de workflow Windows PowerShell sont un ensemble de paramètres d’applet de commande que vous pouvez utiliser avec tous les flux de travail et activités Windows PowerShell. Elles sont ajoutées par le moteur de workflow Windows PowerShell, et non par l’auteur du flux de travail, et sont automatiquement disponibles sur les workflows et les activités. Toutefois, les workflows imbriqués dans trois niveaux ne prennent pas en charge les paramètres communs, y compris les paramètres communs de Workflow.

Tous les paramètres de flux de travail sont facultatifs et nommés (non positionnels). Ils n’acceptent pas d’entrée du pipeline.

La plupart des paramètres communs de workflow ont un préfixe PS, comme `PSComputerName` et `PSCredential` . Les paramètres de préfixe PS configurent la connexion et l’environnement d’exécution pour les ordinateurs cibles, également appelés « nœuds distants ».

La plupart des paramètres communs de workflow, tels que `PSAllowRedirection` et `AsJob` , ont des noms qui sont similaires aux paramètres utilisés dans la communication à distance Windows PowerShell et les tâches en arrière-plan. Ces paramètres fonctionnent de la même façon que les paramètres de communication à distance et de travail de même nom, ce qui vous permet d’utiliser les connaissances que vous avez développées dans Remoting et les tâches pour gérer les workflows.

Les flux de travail sont introduits dans Windows PowerShell 3,0.

### <a name="parameter-descriptions"></a>DESCRIPTIONS DES PARAMÈTRES

Cette section décrit les paramètres communs du flux de travail.

#### <a name="-asjob-switchparameter"></a>-AsJob \<SwitchParameter\>

Exécute le workflow en tant que tâche de Workflow. La commande de flux de travail retourne immédiatement un objet qui représente un travail parent. La tâche parente contient les tâches enfants qui s’exécutent sur chacun des ordinateurs cibles. Pour gérer la tâche, utilisez les applets de commande Job. Pour obtenir les résultats du travail, utilisez [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job).

#### <a name="-jobname-string"></a>-JobName \<String\>

Spécifie un nom convivial pour la tâche de Workflow. Par défaut, les tâches sont nommées « Job\<n\> », où \<n\> est un nombre ordinal.

Si vous utilisez le paramètre JobName dans une commande de flux de travail, le workflow est exécuté en tant que tâche et la commande Workflow retourne un objet de traitement, même si vous n’incluez pas le `AsJob` paramètre dans la commande.

Pour plus d'informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).

#### <a name="-psallowredirection-switchparameter"></a>-PSAllowRedirection \<SwitchParameter\>

Autorise la redirection de la connexion aux ordinateurs cibles.

Quand vous utilisez le `PSConnectionURI` paramètre, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, Windows PowerShell ne redirige pas les connexions, mais vous pouvez utiliser le `PSAllowRedirection` paramètre pour autoriser la redirection de la connexion à l’ordinateur cible.

Vous pouvez également limiter le nombre de redirections de la connexion en définissant la `MaximumConnectionRedirectionCount` propriété de la `$PSSessionOption` variable de préférence ou la `MaximumConnectionRedirectionCount` propriété de la valeur de `PSSessionOption parameter` . La valeur par défaut est 5. Pour plus d’informations, consultez la description du `PSSessionOption` paramètre et [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

#### <a name="-psapplicationname-string"></a>-PSApplicationName \<String\>

Spécifie le segment de nom d’application de l’URI de connexion utilisé pour se connecter aux ordinateurs cibles. Utilisez ce paramètre pour spécifier le nom de l’application lorsque vous n’utilisez pas le `ConnectionURI` paramètre dans la commande.

La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local. Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN. Cette valeur convient pour la plupart des utilisations. Pour plus d’informations, consultez [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion. La valeur de ce paramètre doit correspondre à la valeur de la `URLPrefix` propriété d’un écouteur sur l’ordinateur distant.

#### <a name="-psauthentication-authenticationmechanism"></a>-PSAuthentication \<AuthenticationMechanism\>

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lors de la connexion aux ordinateurs cibles.

Les valeurs autorisées sont :

- **Par défaut**
- **De base**
- **CredSSP**
- **Digest**
- **Kerberos**
- **Prescrit**
- **NegotiateWithImplicitCredential**

La valeur par défaut est **Default** .

Pour plus d’informations sur les valeurs de ce paramètre, consultez la description de l' `System.Management.Automation.Runspaces.AuthenticationMechanism` énumération dans MSDN.

> [!WARNING]
> L'authentification CredSSP (Credential Security Service Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

#### <a name="-psauthenticationlevel-authenticationlevel"></a>-PSAuthenticationLevel \<AuthenticationLevel\>

Spécifie le niveau d’authentification pour les connexions aux ordinateurs cibles.
La valeur par défaut est **Default** .

Les valeurs autorisées sont :

|Nom |Description |
|---------|---------|
|**Inchangé** | le niveau d'authentification est le même que pour la commande précédente. |
|**Par défaut** | Authentification Windows. |
|**Aucun** | Pas d'authentification COM.   |
|**Connexion** | Authentification COM au niveau de la connexion.|
|**Appeler** | Authentification COM au niveau de l'appel.   |
|**Paquet** | Authentification COM au niveau du paquet.|
|**PacketIntegrity** | Authentification COM au niveau de l'intégrité des paquets.  |
|**PacketPrivacy** | Authentification COM au niveau de la confidentialité des paquets. |

#### <a name="-pscertificatethumbprint-string"></a>-PSCertificateThumbprint \<String\>

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent uniquement être mappés aux comptes d'utilisateurs locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir un certificat, utilisez les [éléments](xref:Microsoft.PowerShell.Management.Get-Item) ou [obtenir-ChildItem] (.. /.. /Microsoft.PowerShell.Management/Get-Childitem.md) dans le lecteur Cert : de Windows PowerShell.

#### <a name="-pscomputername-string"></a>-PSComputerName \<String[]\>

Spécifie la liste des ordinateurs qui sont les nœuds cibles du flux de travail.
Les commandes ou les activités d’un flux de travail sont exécutées sur les ordinateurs spécifiés à l’aide de ce paramètre. La valeur par défaut est l'ordinateur local.

Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules. Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, « localhost » ou un point (.).

Pour inclure l’ordinateur local dans la valeur du `PSComputerName` paramètre, ouvrez Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».

Si ce paramètre est omis de la commande, ou si sa valeur est `$null` ou une chaîne vide, la cible de workflow est l’ordinateur local et la communication à distance Windows PowerShell n’est pas utilisée pour exécuter la commande.

Pour utiliser une adresse IP dans la valeur du `ComputerName` paramètre, la commande doit inclure le `PSCredential` paramètre. En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local. Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez *« comment ajouter un ordinateur à la liste des hôtes approuvés »* dans [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).

#### <a name="-psconfigurationname-string"></a>-PSConfigurationName \<String\>

Spécifie les configurations de session utilisées pour configurer des sessions sur les ordinateurs cibles. Entrez une configuration de session sur les ordinateurs cibles (et non sur l’ordinateur du serveur de flux de travail). La valeur par défaut est `Microsoft.PowerShell.Workflow`.

#### <a name="-psconnectionretrycount-uint"></a>-PSConnectionRetryCount \<UInt\>

Spécifie le nombre maximal de tentatives de connexion à chaque ordinateur cible en cas d’échec de la première tentative de connexion. Entrez un nombre compris entre 1 et 4 294 967 295 (UInt. MaxValue). La valeur par défaut, zéro (0), ne représente aucune nouvelle tentative.

#### <a name="-psconnectionretryintervalsec-uint"></a>-PSConnectionRetryIntervalSec \<UInt\>

Spécifie le délai entre les nouvelles tentatives de connexion en secondes. La valeur par défaut est zéro (0). Ce paramètre est valide uniquement lorsque la valeur de PSConnectionRetryCount est au moins égale à 1.

#### <a name="-psconnectionuri-systemuri"></a>-PSConnectionURI \<System.Uri\>

Spécifie un Uniform Resource Identifier (URI) qui définit le point de terminaison de connexion du flux de travail sur l’ordinateur cible. L’URI doit être complet.

Le format de cette chaîne est le suivant :

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

La valeur par défaut est `http://localhost:5985/WSMAN`.

Si vous ne spécifiez pas de `PSConnectionURI` , vous pouvez utiliser les `PSUseSSL` paramètres,, `PSComputerName` `PSPort` et `PSApplicationName` pour spécifier les `PSConnectionURI` valeurs.

Les valeurs valides pour le segment de transport de l’URI sont **http** et **https** .
Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance Windows PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPS.

#### <a name="-pscredential-pscredential"></a>-PSCredential \<PSCredential\>

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter un flux de travail sur l’ordinateur cible. La valeur par défaut est l’utilisateur actuel. Ce paramètre n’est valide que si le paramètre PSComputerName est inclus dans la commande.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domaine01\utilisateur01 », ou entrez une variable qui contient un `PSCredential` objet, tel que celui retourné par l’applet de commande `Get-Credential` . Si vous entrez uniquement un nom d'utilisateur, vous êtes invité à entrer un mot de passe.

#### <a name="-pselapsedtimeoutsec-uint32"></a>-PSElapsedTimeoutSec \<UInt32\>

Détermine la durée pendant laquelle le flux de travail et toutes les ressources associées sont conservés dans le système. Lorsque le délai d’attente expire, le flux de travail est supprimé, même s’il est toujours en cours de traitement. Entrez une valeur comprise entre 10 et 4 294 967 295. La valeur par défaut, 0 (zéro), signifie qu’il n’y a pas de délai d’attente écoulé.

#### <a name="-psparametercollection-hashtable"></a>-PSParameterCollection \<Hashtable[]\>

Spécifie différentes valeurs de paramètres communs de flux de travail pour différents ordinateurs cibles.

Entrez une liste séparée par des virgules de tables de hachage avec une table de hachage pour chaque ordinateur cible. Dans chaque table de hachage, la première clé est `PSComputerName` et sa valeur est le nom de l’ordinateur cible. Les caractères génériques sont autorisés dans le nom de l’ordinateur. Pour les autres clés de la table de hachage, la clé est le nom du paramètre et la valeur est la valeur du paramètre.

Par exemple :

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

Dans l’exemple ci-dessus, toutes les connexions auront un PSElapsedTimeoutSec par défaut de 20 secondes, à l’exception de SERVEUR01 qui remplace la valeur par défaut en spécifiant son propre délai d’expiration de 10 secondes.

#### <a name="-pspersist-boolean"></a>-PSPersist \<Boolean\>

Ajoute des points de contrôle au workflow, en plus des points de contrôle spécifiés dans le Workflow.

Ce paramètre ne peut pas supprimer les points de contrôle d’un workflow, tels que ceux spécifiés à l’aide du `PSPersist` paramètre commun d’activité, de l' `Checkpoint-Workflow` activité ou de la `$PSPersistPreference` variable.

Un « point de contrôle » ou un « point de persistance » est un instantané de l’état du flux de travail et des données capturées pendant l’exécution du workflow et il est enregistré dans un magasin de persistance sur le disque ou dans une base de données SQL. Le workflow Windows PowerShell utilise les données enregistrées pour reprendre un workflow suspendu ou interrompu à partir du dernier point de persistance, plutôt que de redémarrer le flux de travail.

Valeurs valides :

- ( *Par défaut* ) Si vous omettez ce paramètre, un point de contrôle est ajouté au début et à la fin du flux de travail, en plus des points de contrôle spécifiés dans le Workflow.

- `$True`. Ajoute un point de contrôle au début et à la fin du workflow et un point de contrôle après chaque activité, en plus des points de contrôle spécifiés dans le Workflow.

- `$False`. Aucun point de contrôle n’est ajouté. Les points de contrôle sont pris uniquement lorsqu’ils sont spécifiés dans le flux de travail.

#### <a name="-psport-int32"></a>-PSPort \<Int32\>

Spécifie le port réseau sur les ordinateurs cibles. Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPS).

N’utilisez pas le paramètre PSPort, sauf si vous devez le faire. Le port défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs. Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.

#### <a name="-psprivatemetadata-hashtable"></a>-PSPrivateMetadata \<Hashtable\>

Fournit des informations personnalisées aux tâches de Workflow. Entrez une table de hachage. Les clés et les valeurs sont personnalisées pour chaque flux de travail. Pour plus d’informations sur les métadonnées privées d’un flux de travail, consultez la rubrique d’aide relative au flux de travail.

Ce paramètre n’est pas traité par le moteur de workflow Windows PowerShell.
Au lieu de cela, le moteur transmet directement la table de hachage au flux de travail.

#### <a name="-psrunningtimeoutsec-uint32"></a>-PSRunningTimeoutSec \<UInt32\>

Spécifie la durée d’exécution du flux de travail en secondes, à l’exception de la durée pendant laquelle le flux de travail est interrompu. Si l’exécution du flux de travail n’est pas terminée lorsque le délai expire, le moteur de workflow Windows PowerShell arrête de force l’exécution du flux de travail.

#### <a name="-pssessionoption-pssessionoption"></a>-PSSessionOption \<PSSessionOption\>

Définit des options avancées pour les sessions sur les ordinateurs cibles. Entrez un `PSSessionOption` objet, tel que celui que vous créez à l’aide de l’applet de commande `New-PSSessionOption` .

Les valeurs par défaut pour les options de session sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Dans le cas contraire, la session utilise les valeurs spécifiées dans la configuration de session.

Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez la rubrique d’aide de l’applet de commande `New-PSSessionOption` (.. /.. /Microsoft.PowerShell.Core/New-PSSessionOption.md). Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

#### <a name="-psusessl-switchparameter"></a>-PSUseSSL \<SwitchParameter\>

Utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur cible. Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu Windows PowerShell transmis sur le réseau. UseSSL est une protection supplémentaire qui envoie les données via HTTPS au lieu de HTTP. Si vous utilisez ce paramètre, mais que SSL n'est pas disponible sur le port utilisé pour la commande, celle-ci échoue.

## <a name="see-also"></a>VOIR AUSSI

- [about_ActivityCommonParameters](about_ActivityCommonParameters.md)
- [about_Workflows](about_Workflows.md)
- [Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [New-PSWorkflowExecutionOption](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [New-PSWorkflowSession](xref:PSWorkflow.New-PSWorkflowSession)
