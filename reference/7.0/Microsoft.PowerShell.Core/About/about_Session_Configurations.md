---
description: Décrit les configurations de session qui déterminent les utilisateurs pouvant se connecter à distance à l'ordinateur et les commandes qu'ils peuvent exécuter.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5b59d8fb05ee118f5b2d7b5b859efad9be75814a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206585"
---
# <a name="about-session-configurations"></a>À propos des configurations de session

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les configurations de session qui déterminent les utilisateurs pouvant se connecter à distance à l'ordinateur et les commandes qu'ils peuvent exécuter.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Une configuration de session, également appelée « point de terminaison », est un groupe de paramètres sur l’ordinateur local qui définissent l’environnement des sessions PowerShell qui sont créées lorsque des utilisateurs distants ou locaux se connectent à PowerShell sur l’ordinateur local.

Les administrateurs de l’ordinateur peuvent utiliser des configurations de session pour protéger l’ordinateur et définir des environnements personnalisés pour les utilisateurs qui se connectent à l’ordinateur.

Les administrateurs peuvent également utiliser des configurations de session pour déterminer les autorisations requises pour se connecter à l’ordinateur à distance. Par défaut, seuls les membres du groupe administrateurs sont autorisés à utiliser la configuration de session pour se connecter à distance, mais vous pouvez modifier les paramètres par défaut pour permettre à tous les utilisateurs, ou aux utilisateurs sélectionnés, de se connecter à distance à votre ordinateur.

À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir les éléments d’une configuration de session. Cette fonctionnalité permet de personnaliser facilement les sessions sans écrire de code et de découvrir les propriétés d’une configuration de session. Pour créer un fichier de configuration de session, utilisez l’applet de commande New-PSSessionConfiguration. Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](about_Session_Configuration_Files.md).

Les configurations de session sont une fonctionnalité de la communication à distance PowerShell basée sur les services Web for Management (WS-Management). Ils sont utilisés uniquement lorsque vous utilisez les applets de commande New-PSSession, Invoke-Command ou Enter-PSSession pour vous connecter à un ordinateur distant.

Remarque : pour gérer les configurations de session, démarrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».

À propos des configurations de session

Chaque session PowerShell utilise une configuration de session. Cela comprend les sessions persistantes que vous créez à l’aide des applets de commande New-PSSession ou Enter-PSSession, et les sessions temporaires que PowerShell crée lorsque vous utilisez le paramètre ComputerName d’une applet de commande qui utilise la technologie de communication à distance basée sur WS-Management, comme Invoke-Command.

Les administrateurs peuvent utiliser des configurations de session pour protéger les ressources de l’ordinateur et créer des environnements personnalisés pour les utilisateurs qui se connectent à l’ordinateur. Par exemple, vous pouvez utiliser une configuration de session pour limiter la taille des objets que l’ordinateur reçoit dans la session, pour définir le mode de langue de la session et pour spécifier les applets de commande, fournisseurs et fonctions disponibles dans la session.

En configurant le descripteur de sécurité d’une configuration de session, vous déterminez qui peut utiliser la configuration de session pour se connecter à l’ordinateur.
Les utilisateurs doivent disposer de l’autorisation EXECUTE sur une configuration de session pour pouvoir l’utiliser dans une session. Si un utilisateur ne dispose pas des autorisations nécessaires pour utiliser l’une des configurations de session sur un ordinateur, il ne peut pas se connecter à distance à l’ordinateur.

Par défaut, seuls les administrateurs de l’ordinateur sont autorisés à utiliser les configurations de session par défaut. Toutefois, vous pouvez modifier les descripteurs de sécurité pour autoriser tout le monde, personne ou uniquement les utilisateurs sélectionnés à utiliser les configurations de session sur votre ordinateur.

Configurations de session intégrées

PowerShell 3,0 comprend des configurations de session intégrées nommées Microsoft. PowerShell et Microsoft. PowerShell. Workflow. Sur les ordinateurs exécutant des versions 64 bits de Windows, PowerShell fournit également Microsoft. PowerShell32, une configuration de session 32 bits.

La configuration de session Microsoft. PowerShell est utilisée pour les sessions par défaut, autrement dit, quand une commande permettant de créer une session n’inclut pas le paramètre ConfigurationName de l’applet de commande New-PSSession, Enter-PSSession ou Invoke-Command.

Les descripteurs de sécurité pour les configurations de session par défaut autorisent uniquement les membres du groupe Administrateurs sur l’ordinateur local à les utiliser. Ainsi, seuls les membres du groupe administrateurs peuvent se connecter à l’ordinateur à distance, sauf si vous modifiez les paramètres par défaut.

Vous pouvez modifier les configurations de session par défaut à l’aide de la variable de préférence $PSSessionConfigurationName. Pour plus d'informations, consultez about_Preference_Variables.

Affichage des configurations de session sur l’ordinateur local

Pour récupérer les configurations de session sur votre ordinateur local, utilisez l’applet de commande Get-PSSessionConfiguration.

Par exemple, entrez :

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

L’objet de configuration de session est développé dans PowerShell 3,0 pour afficher les propriétés de la configuration de session configurées à l’aide d’un fichier de configuration de session.

Par exemple, pour afficher toutes les propriétés d’un objet de configuration de session, tapez :

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

Vous pouvez également utiliser le fournisseur WSMan dans PowerShell pour afficher les configurations de session. Le fournisseur WSMan crée un lecteur WSMAN : dans votre session.

Dans le lecteur WSMAN :, les configurations de session se trouvent dans le nœud de plug-in. (Toutes les configurations de session se trouvent dans le nœud de plug-in, mais il existe des éléments dans le nœud de plug-in qui ne sont pas des configurations de session.)

Par exemple, pour afficher les configurations de session sur l’ordinateur local, tapez :

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

Affichage des configurations de session sur un ordinateur distant

Pour afficher les configurations de session sur un ordinateur distant, utilisez l’applet de commande Connect-WSMan pour ajouter une note pour l’ordinateur distant au lecteur WSMAN : sur votre ordinateur local, puis utilisez le lecteur WSMAN : pour afficher les configurations de session.

Par exemple, la commande suivante ajoute un nœud pour l’ordinateur distant SERVEUR01 au lecteur WSMAN : sur l’ordinateur local.

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

Une fois la commande terminée, vous pouvez accéder au nœud de l’ordinateur SERVEUR01 pour afficher les configurations de session.

Par exemple :

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

Modification du descripteur de sécurité d’une configuration de session

Dans Windows Server 2012 et les versions plus récentes de Windows Server, les configurations de session intégrées sont activées par défaut pour les utilisateurs distants. Dans les autres versions prises en charge de Windows, vous devez modifier les descripteurs de sécurité des configurations de session pour autoriser l’accès à distance.

Pour activer l’accès à distance aux configurations de session sur l’ordinateur, utilisez l’applet de commande Enable-PSRemoting. Cette applet de commande crée deux configurations de session :

- avec le nom défini en tant que : « PowerShell ». + « version actuelle de PowerShell »
- avec le nom « PowerShell. 6 », qui n’est pas lié à une version spécifique de PowerShell.

De même, par défaut, seuls les membres du groupe Administrateurs sur l’ordinateur ont l’autorisation EXECUTE sur les configurations de session par défaut, mais vous pouvez modifier les descripteurs de sécurité sur les configurations de session par défaut et sur toutes les configurations de session que vous créez.

Pour accorder à d’autres utilisateurs l’autorisation de se connecter à distance à l’ordinateur, utilisez l’applet de commande Set-PSSessionConfiguration pour ajouter des autorisations « exécuter » pour ces utilisateurs aux descripteurs de sécurité des configurations de session Microsoft. PowerShell et Microsoft. PowerShell32.

Par exemple, la commande suivante ouvre une page de propriétés qui vous permet de modifier le descripteur de sécurité pour la configuration de session Microsoft. PowerShell par défaut.

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

Pour refuser l’autorisation tout le monde à toutes les configurations de session sur l’ordinateur, utilisez l’applet de commande Disable-PSSessionConfiguration. Par exemple, la commande suivante désactive les configurations de session par défaut sur l’ordinateur.

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

Pour empêcher les utilisateurs distants de se connecter à l’ordinateur, mais autoriser les utilisateurs locaux à se connecter, utilisez l’applet de commande Disable-PSRemoting. Disable-PSRemoting ajoute une entrée « Network_Deny_All » à toutes les configurations de session sur l’ordinateur.

```powershell
PS C:> Disable-PSRemoting
```

Pour permettre aux utilisateurs distants d’utiliser toutes les configurations de session sur l’ordinateur, utilisez l’applet de commande Enable-PSRemoting ou Enable-PSSessionConfiguration. Par exemple, la commande suivante active l’accès à distance aux configurations de session intégrées.

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

Pour apporter d’autres modifications au descripteur de sécurité d’une configuration de session, utilisez l’applet de commande Set-PSSessionConfiguration. Utilisez le paramètre SecurityDescriptorSDDL pour envoyer une valeur de chaîne SDDL. Utilisez le paramètre ShowSecurityDescriptorUI pour afficher une feuille de propriétés de l’interface utilisateur qui vous aide à créer un nouveau SDDL.

Par exemple :

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

Création d’une nouvelle configuration de session

Pour créer une nouvelle configuration de session sur l’ordinateur local, utilisez l’applet de commande Register-PSSessionConfiguration. Pour définir la nouvelle configuration de session, vous pouvez utiliser un assembly C#, un script PowerShell et les paramètres de l’applet de commande Register-PSSessionConfiguration.

Par exemple, la commande suivante crée une configuration de session qui est identique à la configuration de session Microsoft. PowerShell, à ceci près qu’elle limite les données reçues d’une commande à distance à 20 mégaoctets (Mo). (La valeur par défaut est 50 Mo).

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

Lorsque vous créez une configuration de session, vous pouvez la gérer à l’aide des autres applets de commande de configuration de session, et elle apparaît dans le lecteur WSMAN :.

Pour plus d’informations, consultez Register-PSSessionConfiguration.

Suppression d’une configuration de session

Pour supprimer une configuration de session de l’ordinateur local, utilisez l’applet de commande Unregister-PSSessionConfiguration. Par exemple, la commande suivante supprime la configuration de session NewConfig de l’ordinateur.

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

Pour plus d’informations, consultez Unregister-PSSessionConfiguration.

Restauration d’une configuration de session

Pour restaurer une configuration de session par défaut qui a été supprimée (désinscrite) accidentellement, utilisez l’applet de commande Enable-PSRemoting.

L’applet de commande Enable-PSRemoting recrée toutes les configurations de sessions par défaut qui n’existent pas sur l’ordinateur. Elle ne remplace pas ou ne modifie pas les valeurs des propriétés des configurations de session existantes.

Pour restaurer les valeurs de propriété d’origine d’une configuration de session par défaut, utilisez la Unregister-PSSessionConfiguration pour supprimer la configuration de session, puis utilisez l’applet de commande Enable-PSRemoting pour la recréer.

Sélection d’une configuration de session

Pour sélectionner une configuration de session particulière pour une session, utilisez le paramètre ConfigurationName de New-PSSession, Enter-PSSession ou Invoke-Command.

Par exemple, cette commande utilise l’applet de commande New-PSSession pour démarrer une session PSSession sur l’ordinateur SERVEUR01. La commande utilise le paramètre ConfigurationName pour sélectionner la configuration WithProfile sur l’ordinateur SERVEUR01.

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

Cette commande ne fonctionnera que si l’utilisateur actuel est autorisé à utiliser la configuration de session WithProfile ou peut fournir les informations d’identification d’un utilisateur disposant des autorisations requises.

Vous pouvez également utiliser la variable de préférence $PSSessionConfigurationName pour modifier la configuration de session par défaut sur l’ordinateur. Pour plus d’informations sur la variable de préférence $PSSessionConfigurationName, consultez about_Preference_Variables.

## <a name="keywords"></a>MOT

about_Endpoints about_SessionConfigurations

## <a name="see-also"></a>VOIR AUSSI

[about_Preference_Variables](about_Preference_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Session_Configuration_Files](about_Session_Configuration_Files.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
