---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202969"
---
# New-PSWorkflowSession

## SYNOPSIS
Crée une session de workflow.

## SYNTAX

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## Description

L' `New-PSWorkflowSession` applet de commande crée une session gérée par l’utilisateur ( **PSSession** ) qui est spécialement conçue pour exécuter des workflows Windows PowerShell. Elle utilise la configuration de session Microsoft.PowerShell.Workflow, qui inclut les scripts, les fichiers de type et de mise en forme, ainsi que les options requises pour les workflows.

Vous pouvez utiliser `New-PSWorkflowSession` ou son alias, `nwsn` .

Vous pouvez également ajouter des paramètres communs de workflow à cette commande. Pour plus d’informations sur les paramètres communs de workflow, consultez [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : créer une session de workflow sur un ordinateur distant

Cet exemple crée la session **workflowtests** sur l’ordinateur distant ServerNode01.

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

La valeur du paramètre **SessionOption** est une `New-PSSessionOption` commande qui définit le mode de mise en mémoire tampon de sortie dans la session à **supprimer** .

### Exemple 2 : créer des sessions de workflow sur plusieurs ordinateurs distants

Cet exemple crée des sessions de workflow sur les ordinateurs ServerNode01 et Server12. La commande utilise le paramètre **Credential** à exécuter avec les autorisations de l'administrateur de domaine.

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

La commande utilise le paramètre **ThrottleLimit** pour augmenter le seuil de limitation par commande à 150.
Cette valeur est prioritaire sur la limite de limitation par défaut de 100 qui est définie dans la configuration de session **Microsoft. PowerShell. Workflow** .

## PARAMETERS

### -ApplicationName

Spécifie le segment de nom d'application de l'URI de connexion.

La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local. Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN. Cette valeur convient pour la plupart des utilisations. Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.
La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.
Les valeurs valides pour ce paramètre sont :

- Default
- Basic
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez l' `Get-Item` applet `Get-ChildItem` de commande ou l’applet de commande dans le lecteur Cert : de Windows PowerShell.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Crée une connexion persistante ( **PSSession** ) sur l’ordinateur spécifié. Si vous entrez plusieurs noms d’ordinateur, Windows PowerShell crée plusieurs **sessions PSSession** , une pour chaque ordinateur. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.). Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'utilisateur, le nom de domaine complet est obligatoire. Vous pouvez également diriger un nom d’ordinateur, entre guillemets, vers `New-PSWorkflowSession` .

Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** . En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local. Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel. Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com , ou entrez un objet **PSCredential** , tel que celui retourné par l' `Get-Credential` applet de commande.

Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage. Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs. Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.

Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur. Pour créer une session de bouclage, ne spécifiez pas le paramètre **ComputerName** ou affectez-lui la valeur dot, localhost ou le nom de l’ordinateur local.

Par défaut, les sessions de bouclage sont créées avec un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.

Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage. Si vous spécifiez le paramètre **EnableNetworkAccess** lorsque vous créez une session sur un ordinateur distant, la commande se déroule correctement, mais le paramètre est ignoré.

Vous pouvez également autoriser l'accès à distance dans une session de bouclage à l'aide de la valeur **CredSSP** du paramètre **Authentication** , qui délègue les informations d'identification de session à d'autres ordinateurs.

Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, celles créées à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée. Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs. Pour plus d'informations, consultez l'applet de commande `Disconnect-PSSession`.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un nom convivial pour la session de workflow. Vous pouvez utiliser le nom avec d’autres applets de commande, telles que `Get-PSSession` et `Enter-PSSession` . Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion. Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPs).

Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port. Utilisez les commandes suivantes pour configurer l'écouteur :

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé. Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Spécifie les options avancées pour la session. Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l’applet de commande `New-PSSessionOption` .

Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session. Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session. Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).

Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .
Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut de la configuration de session **Microsoft. PowerShellWorkflow** , 100, est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur distant. Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu Windows PowerShell transmis sur le réseau. Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.

Si vous spécifiez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. instances d’exécution. PSSession [], System. String

Vous pouvez diriger une session ou un nom d’ordinateur vers cette applet de commande.

## SORTIES

### System. Management. Automation. instances d’exécution. PSSession

## REMARQUES

Une `New-PSWorkflowSession` commande est équivalente à la commande suivante :

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## LIENS CONNEXES

[Disconnect-PSSession](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSTransportOption](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[Register-PSSessionConfiguration](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
